---
title: Surveiller les activités DQS | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
f1_keywords:
- sql12.dqs.administration.activitymonitoring.f1
helpviewer_keywords:
- monitoring activity
- activity monitoring
ms.assetid: 1d4c76f3-0d7b-498e-b792-4db4a0349814
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 860842ee5c6c946e6631abac23b229ca67d86334
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "65484132"
---
# <a name="monitor-dqs-activities"></a>Surveiller les activités DQS
  Cette rubrique décrit comment surveiller de manière centralisée les activités suivantes dans [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) : découverte des connaissances, gestion des domaines, stratégie de correspondance, nettoyage des données, correspondance de données et nettoyage SSIS.  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="LimitationsRestrictions"></a> Limitations et restrictions  
 Seuls les utilisateurs avec le rôle dqs_administrator sur la base de données DQS_Main peuvent terminer une activité ou arrêter un processus dans une activité.  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Autorisations  
  
-   Vous devez disposer du rôle dqs_kb_editor ou dqs_kb_operator sur la base de données DQS_MAIN pour afficher les activités DQS.  
  
-   Vous devez disposer du rôle dqs_administrator sur la base de données DQS_MAIN pour terminer une activité ou arrêter un processus dans une activité en plus d'afficher les activités DQS.  
  
##  <a name="View"></a>Afficher les activités DQS  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)][Exécutez l’Application Data Quality client](../../2014/data-quality-services/run-the-data-quality-client-application.md).  
  
2.  Dans l'écran d'accueil [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] , cliquez sur **Analyse des activités**. L'écran de surveillance de l'activité s'affiche.  
  
     ![Écran Analyse des activités](../../2014/data-quality-services/media/dqs-activitymonitoring.gif "Écran Analyse des activités")  
  
3.  L'écran de surveillance affiche des informations sur chaque activité d'une grille d'activité. La grille d'activité affiche les informations suivantes sur chaque activité DQS :  
  
    |Information|Description|  
    |-----------------|-----------------|  
    |**IDENTIFI**|Valeur entière. Numéro d'activité unique généré par le système pour l'analyse des activités.|  
    |**Nom**|Nom de la base de connaissances ou du projet de qualité des données utilisé pour cette activité.|  
    |**Est actif**|Indique si l'activité est actuellement active ou non. Il peut avoir les valeurs suivantes :<br /><br /> **Actif**: l’activité est en cours d’exécution.<br /><br /> **Terminé**: l’activité est terminée.<br /><br /> **Terminé**: l’activité a été arrêtée à l’aide de l’écran de surveillance de l’activité par l’administrateur DQS ou l’activité a été annulée par l’utilisateur lors de son [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]exécution dans le domaine de fonctionnalité respectif dans.|  
    |**Type**|Indique le type d'activité. Les types d'activités suivants font l'objet d'une surveillance : **Gestion des connaissances**, **Projet DQ**et **Nettoyage SSIS**.|  
    |**Sous-type**|Indique le flux de travail spécifique exécuté pour un type d'activité.<br /><br /> Un type d'activité **Gestion des connaissances** peut avoir les sous-types ou flux de travail suivants : **Découverte des connaissances**, **Gestion de l'arborescence du domaine**et **Stratégie de correspondance**.<br /><br /> Un type d'activité **Projet DQ** peut avoir les sous-types ou flux de travail suivants : **Nettoyage** et **Correspondance**.<br /><br /> Un type d'activité **Nettoyage SSIS** peut avoir uniquement un sous-type ou flux de travail **Nettoyage** .|  
    |**État actuel**|Indique l'état actuel d'une activité. L'état d'une activité est déterminé par le dernier processus de calcul. Il peut avoir les valeurs suivantes :<br /><br /> **En cours d’exécution**: le processus de calcul est en cours d’exécution.<br /><br /> Opération **réussie**: avant l’exécution d’un processus de calcul, l’État est défini sur opération **réussie**. Là encore, une fois que le processus de calcul a été exécuté avec succès, l'état est défini sur **Opération réussie**.<br /><br /> **Échec**: le processus de calcul a échoué.<br /><br /> **Arrêté**: le processus de calcul a été arrêté.<br /><br /> <br /><br /> Remarque : il peut y avoir plusieurs processus de calcul dans une activité, tels que l’exécution de plusieurs fois le processus de découverte (au sein de l’activité de découverte des connaissances). Par conséquent, l'état peut changer plusieurs fois pendant la durée de vie d'une activité.|  
    |**DQKB**|Nom de la base de connaissances utilisée pour l'activité.|  
    |**Utilisateur**|Le nom de l'utilisateur qui a démarré l'activité, ou du dernier utilisateur qui a travaillé sur l'activité (au cas où il ne s'agirait pas des deux mêmes personnes).|  
    |**Heure de début de l’activité**|Date et heure du début de l'activité|  
    |**Temps écoulé**|Temps qui s'est écoulé depuis le début de l'activité. Affiché en notation HH:MM:SS.|  
    |**Fin de l’activité**|Date et heure de fin de l'activité.|  
  
##  <a name="Filter"></a>Filtrer les informations sur l’activité DQS  
 Vous pouvez utiliser le volet de filtre (**Filtrer par**, **Valeur**, **Date de début**et **À ce jour**) dans l'écran de surveillance de l'activité pour filtrer et afficher les activités requises sur certains critères. Pour filtrer les enregistrements d'activité :  
  
1.  Choisissez le critère de filtrage : si vous souhaitez filtrer les enregistrements d'activité en fonction d'une valeur de l'une des colonnes de la grille des activités (fondée sur les valeurs), d'une plage de dates, ou des deux.  
  
    1.  **Filtrage basé sur les valeurs**: sélectionnez un critère de filtre dans la liste **Filtrer par** , puis sélectionnez la valeur appropriée pour le filtrage dans la liste **valeur** . Lors de la sélection d'une option dans la liste **Filtrer par** , la liste **Valeur** est mise à jour avec les valeurs possibles. Vous pouvez effectuer un filtrage selon les champs suivants dans les enregistrements d'activité : **Est activé**, **Type**, **Sous-type**, **État actuel**, **BCQD**et **Utilisateur**.  
  
    2.  **Filtrage basé sur une plage de dates**: sélection des dates appropriées dans les contrôles **de date de** date et **d'** échéance. Par défaut, la date affichée dans **Date de début** se situe deux jours avant la date actuelle, tandis que la date affichée dans **Jusqu'à ce jour** correspond à la date actuelle. Le filtrage n'est pas basé sur les dates de *début* et de *fin* , mais sur la plage. Cela signifie que chaque activité qui s'exécutait pendant la plage de dates sélectionnée est affichée.  
  
2.  Cliquez sur l'icône d' **Actualiser la liste des activités** pour appliquer le filtrage, et afficher les activités filtrées DQS uniquement.  
  
##  <a name="ActivityDetails"></a>Afficher les détails de l’activité DQS  
 Vous pouvez afficher les informations détaillées d'une activité DQS, telles que les étapes d'activité et des informations du Générateur de profils, dans l'écran d'analyse d'activité. Pour ce faire :  
  
1.  Sélectionnez une activité DQS dans la grille des activités (dans le volet supérieur).  
  
2.  Le volet inférieur affiche les détails de l'activité sélectionnée sous les 2 onglets suivants :  
  
    -   **Étapes**de l’activité : affiche une grille des processus de calcul (étapes d’activité) associés à l’activité sélectionnée. Il peut y avoir plusieurs étapes d’activité affichées pour une activité sous cet onglet. Cela peut se produire si la même étape d’activité dans l’activité a été exécutée plusieurs fois par l’utilisateur. Par exemple, l'étape d'activité a été arrêtée et démarrée à nouveau. La grille figurant sous cet onglet affiche les informations suivantes pour étape associée à l'activité : **Type**, **État actuel**, **Heure de début**, **Temps écoulé**et **Heure de fin**.  
  
    -   **Profiler**: affiche les informations de profilage pour les activités en cours et historiques. Pour les activités courantes, les informations sont partielles mais cohérentes. Les informations de profilage d'une activité sont exportées vers un fichier Excel lorsque vous exportez les détails d'activité correspondants dans un fichier Excel. Les informations sont disponibles dans les feuilles de **Générateur de profils - source** et de **Générateur de profils - champs** dans le fichier Excel exporté.  
  
##  <a name="Export"></a>Exporter les détails de l’activité DQS  
 Vous pouvez exporter les propriétés d'activité, les processus d'activité, et les informations de profilage d'une activité de l'écran d'analyse vers un fichier Excel. Pour ce faire :  
  
1.  Sélectionnez une activité dans la grille des activités (dans le volet supérieur).  
  
2.  Cliquez sur l'icône d' **Exporter l'activité sélectionnée dans Excel** . Ou bien, cliquez avec le bouton droit sur n'importe quelle activité de la grille, puis cliquez sur **Exporter l'activité** dans le menu contextuel.  
  
3.  Vous êtes invité à spécifier un nom et un emplacement pour le fichier Excel à enregistrer. Le fichier Excel exporté contient les feuilles suivantes :  
  
    |Nom de la feuille|Description|  
    |----------------|-----------------|  
    |Activité|Contient des informations (colonnes) sur l'activité comme dans la grille des activités.|  
    |Processus|Contient des informations (colonnes) sur les processus de l'activité comme dans l'onglet **Étapes de l'activité** .|  
    |Générateur de profils - source|Pour le sous-type **Nettoyage** , contient les informations suivantes sur l'activité : enregistrements, enregistrements corrects, enregistrements corrigés et enregistrements non valides.<br /><br /> Pour les sous-types **Découverte des connaissances**, **Gestion de l'arborescence du domaine**, **Stratégie de correspondance**et **Correspondance** , contient les informations suivantes sur l'activité : enregistrements, valeurs totales, nouvelles valeurs, valeurs uniques et nouvelles valeurs uniques.|  
    |Générateur de profils - champs|Pour les sous-types **Nettoyage** et **Nettoyage SSIS** , contient les informations suivantes sur l'activité : champ, domaine, valeurs corrigées, valeurs suggérées, achèvement et précision.<br /><br /> Pour les sous-types **Découverte des connaissances**, **Gestion de l'arborescence du domaine**, **Stratégie de correspondance**et **Correspondance** , contient les informations suivantes sur l'activité : champ, domaine, nouveau, unique, valide dans le domaine, et achèvement.|  
  
##  <a name="Terminate"></a>Terminer une activité DQS  
 Les administrateurs DQS (rôle dqs_administrator) peuvent terminer une activité (active) en cours d'exécution qui n'est pas du type **Nettoyage SSIS**. La fin d'une activité arrête tous les processus en cours d'exécution dans l'activité et supprime tout ce qui est lié à cette activité. Il est impossible d’annuler cette opération. Terminer une activité dans l'écran de surveillance de l'activité est équivalent à annuler l'activité correspondante en cliquant sur **Annuler** lors de l'exécution dans la zone fonctionnelle de [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]. Pour terminer une activité :  
  
1.  Sélectionnez une activité en cours d'exécution dans la grille des activités (volet supérieur).  
  
2.  Cliquez sur l'icône **Terminer l'activité sélectionnée** . Ou bien, cliquez avec le bouton droit sur n'importe quelle activité de la grille, puis cliquez sur **Terminer l'activité** dans le menu contextuel.  
  
3.  Un message s'affiche pour confirmer votre action. Cliquez sur **Oui**.  
  
##  <a name="Stop"></a>Arrêter un processus dans l’activité DQS  
 Les administrateurs DQS (rôle dqs_administrator) peuvent arrêter un processus (activé) en cours d'exécution dans une activité qui n'est pas du type **Nettoyage SSIS**. L'arrêt d'un processus dans l'écran de surveillance de l'activité est équivalent à arrêter le processus dans l'activité correspondante de la zone fonctionnelle de [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]. Par exemple, arrêt du processus de nettoyage assisté par ordinateur dans une activité de nettoyage, ou arrêt du processus correspondant dans une activité correspondante. Un processus arrêté ne peut pas être redémarré depuis l'écran de surveillance des activités. Vous devrez redémarrer le processus depuis la zone fonctionnelle correspondante dans [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]. Dans ce cas, une ligne supplémentaire est ajoutée à la grille des processus sous l’onglet étapes de l' **activité** . L’état du processus arrêté continue à s’afficher **arrêté**. Pour arrêter un processus :  
  
1.  Sélectionnez un processus en cours d’exécution dans la grille des détails de l'activité (volet inférieur).  
  
2.  Cliquez sur l'icône **Arrêter le processus sélectionné** . Ou bien, cliquez avec le bouton droit sur le processus dans la grille des détails de l'activité, puis cliquez sur **Arrêter le processus** dans le menu contextuel.  
  
3.  Un message s'affiche pour confirmer votre action. Cliquez sur **Oui**.  
  
  
