---
title: Créer, modifier ou supprimer des abonnements pilotés par les données | Microsoft Docs
description: Dans cet article, vous allez découvrir comment créer, modifier et supprimer un abonnement piloté par les données. Vous verrez également quelques conseils sur la définition d’une requête pour récupérer des informations d’abonnement.
ms.date: 06/12/2019
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: subscriptions
ms.topic: conceptual
helpviewer_keywords:
- query-based subscriptions [Reporting Services]
- queries [Reporting Services], data-driven subscriptions
- subscriptions [Reporting Services], data-driven
- data-driven subscriptions
ms.assetid: 0ba2093e-9393-4eb6-af06-9da10988cfaf
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 3d38d44537589ff4b58a41b6b89960b262783e06
ms.sourcegitcommit: c6a2efe551e37883c1749bdd9e3c06eb54ccedc9
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80742203"
---
# <a name="create-modify-and-delete-data-driven-subscriptions"></a>Créer, modifier ou supprimer des abonnements pilotés par les données
  Un abonnement piloté par les données est un abonnement qui a recours à une requête pour obtenir les valeurs de données qui seront utilisées dans le traitement de l'abonnement au moment de l'exécution. Lorsque l'abonnement est déclenché, une requête est traitée pour récupérer des informations récentes sur les destinataires, les options de remise de rapport, les formats de rendu et les valeurs de paramètre. Les résultats de la requête sont combinées à la définition de l'abonnement pour créer un abonnement dynamique utilisant les données que vous avez conservées dans une base de données employés, une base de données clients ou dans toute autre base de données contenant des informations utilisables comme données d'abonnés.  
  
 Pour créer un abonnement piloté par les données ou modifier un abonnement existant, utilisez la page **Gérer** > **Abonnements** dans le portail web. La page **Abonnements** vous guide tout au long du processus de création ou de modification d'un abonnement. Pour accéder à un abonnement après qu'il a été créé, utilisez la page **Mes abonnements** et la liste Abonnements d'un rapport. Pour savoir comment créer un abonnement piloté par les données, consultez [Créer un abonnement piloté par les données &#40;didacticiel SSRS&#41;](../../reporting-services/create-a-data-driven-subscription-ssrs-tutorial.md).  
  
 Contenu de cet article :  
  
-   [Gestion et suppression d'un abonnement piloté par les données](#bkmk_manage_and_delete)  
  
-   [Création et modification d'un abonnement piloté par les données](#bkmk_create_and_modify)  
  
-   [Définition d'une requête qui extrait les informations d'abonnement](#bkmk_define_query)  
  
-   [Exécution de l'abonnement](#bkmk_run_subscription)  
  
##  <a name="managing-and-deleting-a-data-driven-subscription"></a><a name="bkmk_manage_and_delete"></a> Gestion et suppression d'un abonnement piloté par les données  
 Un abonnement piloté par les données en cours d'exécution ne peut pas être arrêté ou supprimé via le portail web. Par conséquent, il est préférable d'utiliser une planification partagée pour déclencher l'abonnement piloté par les données. Si vous voulez empêcher temporairement l'exécution d'un abonnement, vous pouvez suspendre la planification qui le déclenche. Pour plus d’informations, consultez [Créer et gérer des abonnements pour les serveurs de rapports en mode natif](../../reporting-services/subscriptions/create-and-manage-subscriptions-for-native-mode-report-servers.md).  
  
 Pour supprimer un abonnement piloté par les données, cochez la case en regard du rapport sur la page **Abonnements**, puis sélectionnez **Supprimer**.  
  
 Pour obtenir des instructions sur l’annulation d’un abonnement piloté par les données, consultez [Gérer un processus en cours d’exécution](../../reporting-services/subscriptions/manage-a-running-process.md).  
  
##  <a name="creating-and-modifying-a-data-driven-subscription"></a><a name="bkmk_create_and_modify"></a> Création et modification d'un abonnement piloté par les données  
 Pour créer un abonnement piloté par les données, sélectionnez un rapport qui utilise des informations d'identification stockées ou aucune information d'identification. Lorsque vous créez l'abonnement piloté par les données, nous vous conseillons d'utiliser une convention d'affectation de noms pour le champ de description, afin de pouvoir différencier facilement les abonnements standard des abonnements pilotés par les données.  
  
### <a name="to-create-a-data-driven-subscription-native-mode"></a>Pour créer un abonnement piloté par les données (mode natif)  
  
1. Dans le portail web, accédez au dossier contenant le rapport, cliquez avec le bouton droit sur le rapport, puis sélectionnez **Gérer** dans le menu déroulant.  
  
2. Sélectionnez l'onglet **Abonnements** .  
  
3. Sélectionnez **+ Nouvel abonnement** dans la page **Abonnements**.  
  
### <a name="to-create-a-data-driven-subscription-sharepoint-mode"></a>Pour créer un abonnement piloté par les données (mode SharePoint)  
  
1. Dans la bibliothèque de documents SharePoint, pointez sur le rapport, ouvrez le menu d'options et cliquez sur **Gérer les abonnements**.  
  
2. Cliquez sur **Ajouter un abonnement piloté par les données**.  
  
### <a name="to-modify-an-existing-data-driven-subscription-native-mode"></a>Pour modifier un abonnement piloté par les données existant (mode natif)  
  
1. Dans le portail web, accédez au dossier contenant le rapport, cliquez avec le bouton droit sur le rapport, puis sélectionnez **Gérer** dans le menu déroulant.  
  
2. Sélectionnez l'onglet **Abonnements** .  
  
3. Cochez la case en regard de l’abonnement que vous souhaitez modifier, puis sélectionnez **Modifier**. Les abonnements pilotés par les données ont la valeur « Piloté par les données » dans la colonne **Type**.  
  
### <a name="to-modify-an-existing-data-driven-subscription-sharepoint-mode"></a>Pour modifier un abonnement piloté par les données existant (mode SharePoint)  
  
1.  Dans la bibliothèque de documents SharePoint, pointez sur le rapport, ouvrez le menu d'options et cliquez sur **Gérer les abonnements**.  
  
2.  Sélectionnez l’abonnement que vous souhaitez modifier.  
  
    > [!NOTE]  
    > Vous pouvez modifier n'importe quelle valeur déjà spécifiée. Toutes les valeurs sont présentées comme elles ont été créées, à l'exception du mot de passe qui est utilisé pour accéder à la banque de données des abonnés. Vous devez retaper le mot de passe chaque fois que vous modifiez des valeurs dans la deuxième page ou dans les pages suivantes.  
  
  Avant de créer un abonnement piloté par les données, assurez-vous que les conditions suivantes sont remplies :  
  
-   **Conditions requises liées au rapport**. Le rapport doit utiliser des informations d'identification stockées ou ne pas en utiliser du tout pour être en mesure d'extraire les données au moment de l'exécution. Vous ne pouvez pas vous abonner à un rapport qui utilise des informations d'identification déléguées ou empruntées pour vous connecter à une source de données externe ; les informations d'identification de l'utilisateur qui crée ou possède l'abonnement ne seront pas disponibles lorsque l'abonnement sera traité. Les informations d'identification stockées peuvent être un compte Windows ou un compte d'utilisateur de base de données. Pour plus d’informations, consultez [Spécifier des informations d’identification et de connexion pour les sources de données de rapport](../../reporting-services/report-data/specify-credential-and-connection-information-for-report-data-sources.md).  
  
     Vous ne pouvez pas vous abonner à un rapport du Générateur de rapports qui utilise un modèle comme source de données si le modèle contient des paramètres de sécurité de l'élément de modèle. Seuls les rapports qui utilisent la sécurité de l'élément de modèle sont inclus dans cette restriction.  
  
     Vous ne pouvez pas créer un abonnement piloté par les données pour un rapport qui contient l'expression `User!UserID` .  
  
-   **Conditions requises liées aux données**. Vous devez posséder une source de données externe et accessible contenant des données d'abonnés.  
  
-   **Conditions requises liées à l'utilisateur**. L'auteur de l'abonnement doit être autorisé à « Gérer les rapports » et « Gérer tous les abonnements ». Pour plus d’informations sur les autorisations d’exécution de tâches au niveau élément, consultez [Tâches et autorisations](../../reporting-services/security/tasks-and-permissions.md). L'auteur doit également posséder les informations d'identification requises pour accéder à la source de données externe qui contient les données des abonnés.  
  
##  <a name="defining-a-query-that-retrieves-subscription-information"></a><a name="bkmk_define_query"></a> Définition d'une requête qui extrait les informations d'abonnement  
 Un abonnement piloté par les données doit spécifier une requête ou une commande qui permet d'extraire les données des abonnés. La requête doit produire une ligne pour chaque abonné. Si vous utilisez l'extension de remise par messagerie électronique, la requête doit retourner un alias de messagerie pour chaque abonné. Le nombre de remises effectuées est basé sur le nombre de lignes retournées par la requête. Si le jeu de lignes contient 10 000 lignes, l'abonnement remet 10 000 rapports.  
  
 Si l'exécution de la requête est trop longue, vous pouvez augmenter la valeur du délai d'expiration pour permettre un temps de traitement supplémentaire.  
  
 Pour cette étape, la requête doit être validée avant que vous continuiez. La validation ne traite pas la requête mais retourne la liste de toutes les colonnes qui se trouvent dans l'ensemble de lignes, ce qui vous permet de référencer les colonnes lors de sélections ultérieures. Si la validation de la requête échoue, il vous est impossible de continuer. Une requête n'est pas validée si sa syntaxe est incorrecte ou si la connexion à la source de données n'est pas valide. Utilisez le bouton **Précédent** pour effectuer les corrections qui s'imposent sur la source de données.  
  
##  <a name="running-the-subscription"></a><a name="bkmk_run_subscription"></a> Exécution de l'abonnement  
 Vous devez indiquer les conditions du traitement de l'abonnement. Vous pouvez spécifier une planification ou déclencher l'abonnement de façon à ce qu'il coïncide avec la mise à jour de l'instantané d'exécution de rapport. Le traitement des abonnements pilotés par les données est identique au traitement des abonnements standard.  
  
## <a name="see-also"></a>Voir aussi  
 [Créer et gérer des abonnements pour les serveurs de rapports en mode natif](../../reporting-services/subscriptions/create-and-manage-subscriptions-for-native-mode-report-servers.md)   
 [Abonnements et remise &#40;Reporting Services&#41;](../../reporting-services/subscriptions/subscriptions-and-delivery-reporting-services.md)   
 [Le portail web d’un serveur de rapports (Mode natif SSRS)](../../reporting-services/web-portal-ssrs-native-mode.md)   
 [Créer et gérer des abonnements pour les serveurs de rapports en mode natif](create-and-manage-subscriptions-for-native-mode-report-servers.md)   
 [Utilisation des abonnements (portail web)](../../reporting-services/working-with-subscriptions-web-portal.md) [Utiliser Mes abonnements (serveur de rapports en mode natif)](../../reporting-services/subscriptions/use-my-subscriptions-native-mode-report-server.md)  
 