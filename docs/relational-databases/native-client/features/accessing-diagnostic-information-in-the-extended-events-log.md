---
title: Accès aux informations de diagnostic dans le journal des événements étendus | Microsoft Docs
ms.date: 03/14/2017
ms.reviewer: ''
ms.prod: sql
ms.technology: native-client
ms.topic: reference
ms.assetid: aaa180c2-5e1a-4534-a125-507c647186ab
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: a60a54d930f87ebe054d3d414b31049fd26a4a2a
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68103428"
---
# <a name="accessing-diagnostic-information-in-the-extended-events-log"></a>Accès aux informations de diagnostic dans le journal des événements étendus
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  À compter de [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)], [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client et les données de suivi d’accès ([suivi d’accès aux données](https://go.microsoft.com/fwlink/?LinkId=125805)) ont été mis à jour pour le rendre plus facile d’obtenir des informations de diagnostic des échecs de connexion à partir de l’anneau de connectivité informations de performances mémoire tampon et d’applications dans le journal des événements étendus.  
  
 Pour plus d’informations sur la lecture du journal des événements étendus, consultez [Afficher des données de session d’événements](https://msdn.microsoft.com/library/ac742a01-2a95-42c7-b65e-ad565020dc49).  
  
> [!NOTE]  
>  Cette fonctionnalité n'est conçue qu'à des fins de dépannage et de diagnostic et peut ne pas convenir à des fins d'audit ou de sécurité.  
  
## <a name="remarks"></a>Notes  
 Pour les opérations de connexion, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client envoie un ID de connexion client. Si la connexion échoue, vous pouvez accéder à la mémoire tampon en anneau de connectivité ([Résolution des problèmes de connectivité dans SQL Server 2008 avec la mémoire tampon en anneau de connectivité](https://go.microsoft.com/fwlink/?LinkId=207752)) et rechercher le champ **ClientConnectionID** pour obtenir les informations de diagnostic sur l’échec de connexion. Les ID de connexion du client sont enregistrés dans la mémoire tampon en anneau uniquement en cas d'erreur. (Si une connexion échoue avant d'envoyer le paquet de préconnexion, un ID de connexion client ne sera pas généré.) L'ID de connexion client est un GUID à 16 octets. Vous pouvez également rechercher l’ID de connexion client dans la cible de sortie d’événements étendus, si l’action **client_connection_id** est ajoutée aux événements dans une session d’événements étendus. Vous pouvez activer le traçage de l’accès aux données et réexécuter la commande de connexion, puis observer le champ **ClientConnectionID** dans la trace d’accès aux données pour une opération ayant échoué, si vous avez besoin d’une aide supplémentaire pour le diagnostic.  
  
 Si vous utilisez ODBC dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client et une connexion aboutit, vous pouvez obtenir le client ID de connexion à l’aide de la **SQL_COPT_SS_CLIENT_CONNECTION_ID** attribut avec [SQLGetConnectAttr](../../../relational-databases/native-client-odbc-api/sqlgetconnectattr.md).  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client envoie également un ID d'activité spécifique à un thread. L'ID d'activité est capturé dans les sessions d'événements étendus si les sessions sont démarrées alors que l'option TRACK_CAUSAILITY est activée. En cas de problèmes de performance avec une connexion active, vous pouvez obtenir l’ID d’activité de la trace d’accès aux données du client (champ **ActivityID**), puis le localiser dans la sortie d’événements étendus. L'ID d'activité dans les événements étendus est un GUID à 16 octets (différent du GUID de l'ID de connexion client) ajouté avec un numéro de séquence de quatre octets. Le numéro séquentiel représente l'ordre d'une demande dans un thread et indique l'ordre relatif du traitement par lot et des instructions RPC pour le thread. **ActivityID** est éventuellement envoyé pour les instructions par lots SQL et les demandes RPC quand le traçage de l’accès aux données est activé et que le 18ème bit dans le mot de configuration de traçage est activé.  
  
 Voici un exemple qui utilise [!INCLUDE[tsql](../../../includes/tsql-md.md)] pour démarrer une session d'événements étendus qui sera stockée dans une mémoire tampon en anneau et enregistrera l'ID d'activité envoyé d'un client sur des opérations de traitement par lot et RPC.  
  
```  
create event session MySession on server   
add event connectivity_ring_buffer_recorded,   
add event sql_statement_starting (action (client_connection_id)),   
add event sql_statement_completed (action (client_connection_id)),   
add event rpc_starting (action (client_connection_id)),   
add event rpc_completed (action (client_connection_id))  
add target ring_buffer with (track_causality=on)  
  
```  
  
## <a name="control-file"></a>Fichier de contrôle  
 Dans [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)], le contenu du fichier de commandes SQL Server Native Client (ctrl.guid.snac11) est :  
  
```  
{8B98D3F2-3CC6-0B9C-6651-9649CCE5C752}  0x00000000  0   MSDADIAG.ETW  
{2DA81B52-908E-7DB6-EF81-76856BB47C4F}  0xFFFFFFFF  0   SQLNCLI11.1  
```  
  
## <a name="mof-file"></a>Fichier MOF  
 Dans [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)], le contenu du fichier MOF de SQL Server Native Client est :  
  
```  
#pragma classflags("forceupdate")  
#pragma namespace ("\\\\.\\Root\\WMI")  
  
/////////////////////////////////////////////////////////////////////////////  
//  
//  MSDADIAG.ETW  
  
[  
 dynamic: ToInstance,  
 Description("MSDADIAG.ETW"),  
 Guid("{8B98D3F2-3CC6-0B9C-6651-9649CCE5C752}"),  
 locale("MS\\0x409")  
]  
class Bid2Etw_MSDADIAG_ETW : EventTrace  
{  
};  
  
[  
 dynamic: ToInstance,  
 Description("MSDADIAG.ETW"),  
 Guid("{8B98D3F3-3CC6-0B9C-6651-9649CCE5C752}"),  
 DisplayName("msdadiag"),  
 locale("MS\\0x409")  
]  
class Bid2Etw_MSDADIAG_ETW_Trace : Bid2Etw_MSDADIAG_ETW  
{  
};  
  
[  
 dynamic: ToInstance,  
 Description("MSDADIAG.ETW formatted output (A)"),  
 EventType(17),  
 EventTypeName("TextA"),  
 locale("MS\\0x409")  
]  
class Bid2Etw_MSDADIAG_ETW_Trace_TextA : Bid2Etw_MSDADIAG_ETW_Trace  
{  
    [  
     WmiDataId(1),  
     Description("Module ID"),  
     read  
    ]  
    uint32 ModID;  
  
    [  
     WmiDataId(2),  
     Description("Text StringA"),  
     extension("RString"),  
     read  
    ]  
    object msgStr;  
};  
  
[  
 dynamic: ToInstance,  
 Description("MSDADIAG.ETW formatted output (W)"),  
 EventType(18),  
 EventTypeName("TextW"),  
 locale("MS\\0x409")  
]  
class Bid2Etw_MSDADIAG_ETW_Trace_TextW : Bid2Etw_MSDADIAG_ETW_Trace  
{  
    [  
     WmiDataId(1),  
     Description("Module ID"),  
     read  
    ]  
    uint32 ModID;  
  
    [  
     WmiDataId(2),  
     Description("Text StringW"),  
     extension("RWString"),  
     read  
    ]  
    object msgStr;  
};  
  
/////////////////////////////////////////////////////////////////////////////  
//  
//  SQLNCLI11.1  
  
[  
 dynamic: ToInstance,  
 Description("SQLNCLI11.1"),  
 Guid("{2DA81B52-908E-7DB6-EF81-76856BB47C4F}"),  
 locale("MS\\0x409")  
]  
class Bid2Etw_SQLNCLI11_1 : EventTrace  
{  
};  
  
[  
 dynamic: ToInstance,  
 Description("SQLNCLI11.1"),  
 Guid("{2DA81B53-908E-7DB6-EF81-76856BB47C4F}"),  
 DisplayName("SQLNCLI11.1"),  
 locale("MS\\0x409")  
]  
class Bid2Etw_SQLNCLI11_1_Trace : Bid2Etw_SQLNCLI11_1  
{  
};  
  
[  
 dynamic: ToInstance,  
 Description("SQLNCLI11.1 formatted output (A)"),  
 EventType(17),  
 EventTypeName("TextA"),  
 locale("MS\\0x409")  
]  
class Bid2Etw_SQLNCLI11_1_Trace_TextA : Bid2Etw_SQLNCLI11_1_Trace  
{  
    [  
     WmiDataId(1),  
     Description("Module ID"),  
     read  
    ]  
    uint32 ModID;  
  
    [  
     WmiDataId(2),  
     Description("Text StringA"),  
     extension("RString"),  
     read  
    ]  
    object msgStr;  
};  
  
[  
 dynamic: ToInstance,  
 Description("SQLNCLI11.1 formatted output (W)"),  
 EventType(18),  
 EventTypeName("TextW"),  
 locale("MS\\0x409")  
]  
class Bid2Etw_SQLNCLI11_1_Trace_TextW : Bid2Etw_SQLNCLI11_1_Trace  
{  
    [  
     WmiDataId(1),  
     Description("Module ID"),  
     read  
    ]  
    uint32 ModID;  
  
    [  
     WmiDataId(2),  
     Description("Text StringW"),  
     extension("RWString"),  
     read  
    ]  
    object msgStr;  
};  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des erreurs et des messages](../../../relational-databases/native-client-odbc-error-messages/handling-errors-and-messages.md)  
  
  
