---
title: "Dépannage des Solutions SharePoint | Documents Microsoft"
ms.custom: 
ms.date: 02/22/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: Microsoft.VisualStudio.Tools.SharePoint.Errors.Debugging
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords: SharePoint development in Visual Studio, troubleshooting
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 6f03f8fd1fd5609f93d4fae22a7a694e61b1c80c
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2018
---
# <a name="troubleshooting-sharepoint-solutions"></a>Dépannage des solutions SharePoint
  Les alertes ou les problèmes suivants peuvent se produire lorsque vous déboguez des solutions SharePoint à l’aide de la [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] débogueur. Pour plus d’informations, consultez [débogage de Solutions de flux de travail SharePoint 2007](http://msdn.microsoft.com/en-us/3a5392f3-66f3-48be-956e-02de23fa6247).
  
## <a name="token-restrictions-in-sandboxed-visual-web-parts"></a>Restrictions des jetons dans les composants Visual WebPart en bac à sable  
 Les composants Visual WebPart de solutions bac à sable ne peuvent pas traiter les jetons standard, tels que $SPUrl, que le runtime SharePoint prend en charge. Par conséquent, l'URL n'est pas résolue et vous ne pouvez pas avoir d'aperçu du contenu en mode Design du concepteur de composants Visual WebPart si vous y faites référence directement dans un élément de script, tel que dans l'exemple suivant :  
  
```xml  
<script src="<% $SPUrl:~site/SiteAssets/ListOperations.js %>"></script>  
```  
  
 Pour contourner cette limitation et résoudre le jeton, faites-y référence à l'aide des littéraux :  
  
```xml  
<asp:literal ID="Literal1" runat="server" Text="<script src='" />  
<asp:literal ID="Literal2" runat="server" Text="<% $SPUrl:~site/SiteAssets/ListOperations.js %>" />  
<asp:literal ID="Literal3" runat="server" Text="' type='text/javascript' ></script>" />  
```  
  
## <a name="character-restrictions-in-names-of-projects-and-project-items"></a>Restrictions de caractères dans les noms de projets et éléments de projet  
 Les noms de projets et d’éléments de projet peuvent contenir uniquement des caractères qui sont valides dans un chemin de déploiement dans SharePoint 2010. Aucun autre caractère n’est pas autorisés.  
  
### <a name="error-message"></a>Message d'erreur  
 Message d’erreur « Caractères non valide ».  
  
### <a name="resolution"></a>Résolution  
 Pour les noms de projets et d'éléments de projet SharePoint, utilisez uniquement les caractères suivants :  
  
-   Caractères ASCII alphanumériques  
  
-   Espace  
  
-   Point (.)  
  
-   Virgule ()  
  
-   Trait de soulignement (_)  
  
-   Tiret (-)  
  
-   Barre oblique inverse (\\)  
  
 Lorsqu’un projet est empaqueté, une règle de validation vérifie que la propriété du chemin d’accès de déploiement de chaque fichier déployé contient uniquement ces caractères valides.  
  
## <a name="errors-when-creating-custom-fields"></a>Erreur lors de la création de champs personnalisés  
 Dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], les champs personnalisés sont définis dans XML. Des erreurs peuvent survenir si un champ n'est pas défini, ni référencé à l'aide d'un format spécifique.  
  
### <a name="error-message"></a>Message d'erreur  
 Message d’erreur « Caractères non valides » au moment de l’empaquetage.  
  
### <a name="resolution"></a>Résolution  
 L'ID d'une définition de champ doit être un GUID délimité par des accolades, comme dans l'exemple suivant :  
  
```xml  
<Field ID="{5744d18c-305e-4632-8bd1-09d134f4830d}"   
    Type="Note"   
    Name="PatientName"   
    DisplayName="Patient Name"   
    Group="A Custom Group">  
</Field>.  
```  
  
 Comme le montre l’exemple suivant, une référence de champ dans un type de contenu doit être définie en utilisant le format d’élément vide (\<FieldRef / >), ne pas à l’aide des éléments de début et de fin (\<FieldRef >\</FieldRef >) :  
  
```xml  
<FieldRef ID="{5744d18c-305e-4632-8bd1-09d134f4830d}"   
    Name="PatientName"   
    DisplayName="Patient Name"   
    Required="TRUE"/>  
```  
  
 En cas de problème avec le code XML source pour le champ, par exemple s'il est incorrect ou si le fichier XML n'est pas valide, l'erreur d'analyse "Impossible d'analyser le fichier" du fichier survient.  
  
## <a name="new-non-english-site-definitions-do-not-appear-in-site-creation-page-after-deployment"></a>Les nouvelles définitions de Site Non anglaises n’apparaissent pas dans la Page de création de Site après le déploiement  
 Une fois que vous créez et déployez une définition de site à l’aide d’une version non anglaise de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] (autrement dit, une version avec les paramètres régionaux [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] autres que 1033), le **personnalisations de SharePoint** onglet n’apparaît pas dans le **Sélection du modèle** zone et le nouveau modèle de site n’apparaît pas dans le **nouveau SharePoint Site** page.  
  
### <a name="error-message"></a>Message d'erreur  
 Aucun.  
  
### <a name="resolution"></a>Résolution  
 Ce problème se produit en raison d’une valeur incorrecte dans le **chemin d’accès** propriété pour le fichier de configuration de la définition de site webtemp, tel que webtemp_SiteDefinitionProject1.xml. Dans le **chemin d’accès** propriété pour le fichier webtemp, situé sous le **emplacement de déploiement**, remplacez 1033 par les paramètres régionaux appropriés [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)]. Par exemple, pour utiliser un paramètre régional japonais modifier la valeur par 1041. Pour plus d’informations, consultez [ID de paramètres régionaux assignés par Microsoft](http://go.microsoft.com/fwlink/?LinkID=165561) sur le site Web MSDN.  
  
## <a name="error-appears-when-a-workflow-project-is-deployed-on-a-clean-system"></a>Erreur s’affiche lorsqu’un projet de flux de travail est déployé sur un système propre  
 Ce problème se produit si vous déployez un projet de flux de travail dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] sur un système propre. Un système propre est un ordinateur avec une nouvelle installation de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] et SharePoint, sans aucun projet de flux de travail déployé.  
  
### <a name="error-message"></a>Message d'erreur  
 Impossible de trouver la liste SharePoint : historique de flux de travail.  
  
### <a name="resolution"></a>Résolution  
 Cette erreur se produit en raison d’une liste d’historique de flux de travail manquante. Étant donné que l’environnement de développement est un système propre, aucun flux de travail n’est déployés et l’historique de flux de travail n’existe pas encore. Pour résoudre ce problème, rouvrez l’Assistant flux de travail, ce qui entraîne l’historique de flux de travail à créer.  
  
##### <a name="to-reenter-the-workflow-wizard"></a>Pour entrer de nouveau l’Assistant flux de travail  
  
1.  Dans **l’Explorateur de solutions**, choisissez le nœud du flux de travail.  
  
2.  Dans le **propriétés** fenêtre, cliquez sur le bouton de sélection (...) sur n’importe quelle propriété qui a un bouton de sélection.  
  
## <a name="user-must-refresh-application-page-in-browser-while-debugging-to-view-updated-image"></a>Utilisateur doit actualiser la Page Application dans le navigateur pendant le débogage en mode de mise à jour Image  
 Si vous déboguez une solution SharePoint qui contient une page d’application avec un contrôle qui affiche une image, tel qu’un [!INCLUDE[TLA2#tla_html](../sharepoint/includes/tla2sharptla-html-md.md)] contrôle Image, vous devez actualiser la page dans le navigateur pour afficher toutes les modifications qui ont été apportées à l’image.  
  
## <a name="error-the-site-location-is-not-valid"></a>Erreur : L’emplacement du Site n’est pas valide  
 Ce problème peut se produire si [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] n’est pas installé. Il peut également se produire si vous n’avez pas d’accès administrateur sur le site SharePoint Web qui est spécifié dans le **Assistant Personnalisation de SharePoint**.  
  
### <a name="error-message"></a>Message d'erreur  
  
-   Emplacement du site SharePoint n’est pas valide.  
  
### <a name="resolution"></a>Résolution  
  
-   Installez [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)].  
  
-   Assurez-vous d’avoir un accès administrateur sur le site SharePoint Web. Pour plus d’informations, consultez la [!INCLUDE[TLA2#tla_office](../sharepoint/includes/tla2sharptla-office-md.md)] l’article en ligne [accorder l’accès au site du portail](http://go.microsoft.com/fwlink/?LinkId=98310).  
  
## <a name="site-deletion-web-event-does-not-occur-in-event-receiver-project"></a>Événement de Web site suppression ne se produit pas dans le projet de récepteur d’événements  
 Lorsque vous créez un projet de récepteur d’événements et que vous sélectionnez certains événements Web tels que « un site est en cours de suppression », l’événement se produit jamais.  
  
### <a name="error-message"></a>Message d'erreur  
 Aucun.  
  
### <a name="resolution"></a>Résolution  
 Ce problème se produit parce que l’étendue de la fonctionnalité doit être « Site » pour gérer les événements au niveau du site, mais l’étendue de la fonctionnalité par défaut pour les projets de récepteur d’événements est « Web ». Les événements Web affectés sont :  
  
-   Un site est supprimé (WebDeleting)  
  
-   Un site a été supprimé (WebDeleted)  
  
-   Un site est en cours déplacement (WebMoving)  
  
-   Un site a été déplacé (WebMoved)  
  
 Pour résoudre le problème, modifiez l’étendue de la fonctionnalité du récepteur d’événements, comme suit.  
  
##### <a name="to-change-the-feature-scope-of-the-event-receiver"></a>Pour modifier l’étendue de la fonctionnalité du récepteur d’événements  
  
1.  Dans **l’Explorateur de solutions**, ouvrez le fichier de .feature du récepteur d’événements dans le **Concepteur de fonctionnalités** en double-cliquant sur le fichier ou en ouvrant le menu contextuel, puis en choisissant **ouvrir**.  
  
2.  Cliquez sur la flèche à côté **étendue**, puis choisissez **Site** dans la liste qui s’affiche.  
  
## <a name="deployment-error-appears-after-the-name-of-an-identifier-in-a-business-data-connectivity-model-project-is-changed"></a>Erreur de déploiement s’affiche après la modification du nom d’un identificateur dans un projet de modèle de connectivité de données métier  
 Ce problème se produit si vous modifiez le nom d’identificateur d’une entité dans un modèle de connectivité de données métiers (BDC) et que vous essayez ensuite de déployer la solution.  
  
### <a name="error-messages"></a>messages d'erreur  
  
-   \<*nom du modèle*> comporte les erreurs d’activation de Type de contenu externe suivantes...  
  
-   L’objet IMetadataObject portant le nom '\<*nom_modèle*>' a une valeur dans le champ 'name' est dupliquée...  
  
### <a name="resolution"></a>Résolution  
 Pour résoudre ce problème, supprimez le modèle manuellement, puis redéployez la solution.  Vous pouvez supprimer le modèle à l’aide des outils suivants :  
  
-   Administration centrale de SharePoint 2010. Pour plus d’informations, consultez [gérer les modèles BDC](http://go.microsoft.com/fwlink/?LinkID=181472) sur le site Web Microsoft TechNet.  
  
-   Windows PowerShell. Vous pouvez supprimer le modèle en tapant cette commande à l’invite de commandes : **Remove-SPBusinessDataCatalogModel**. Pour plus d’informations, consultez [applets de commande générales (SharePoint Server 2010)](http://go.microsoft.com/fwlink/?LinkID=182375) sur le site Web Microsoft TechNet.  
  
## <a name="an-error-appears-when-you-try-to-view-a-visual-web-part-in-sharepoint"></a>Une erreur s’affiche lorsque vous essayez d’afficher un composant Visual Web Part dans SharePoint  
 Ce problème se produit lorsque le **chemin d’accès** propriété du contrôle utilisateur ne commence pas par la chaîne « CONTROLTEMPLATES\\».  
  
### <a name="error-messages"></a>messages d'erreur  
  
-   Le fichier ' /_CONTROLTEMPLATES/*\<nom du projet >*/*\<nom du composant WebPart >*/*\<contrôle utilisateur nom >*.ascx » n’existe pas.  
  
-   Erreur de serveur dans l’Application '/'.  
  
### <a name="resolution"></a>Résolution  
  
##### <a name="to-resolve-this-issue"></a>Pour résoudre ce problème  
  
1.  Dans **l’Explorateur de solutions**, choisissez le fichier de contrôle utilisateur, dont l’extension est .ascx.  
  
2.  Dans la barre de menus, choisissez **vue**, **fenêtre Propriétés**.  
  
3.  Dans le **propriétés** fenêtre, développez le **emplacement de déploiement** nœud.  
  
4.  Vérifiez que la valeur de la **chemin d’accès** propriété commence par la chaîne « CONTROLTEMPLATES\\».  
  
## <a name="error-appears-when-an-imported-reusable-workflow-that-contains-a-task-form-field-is-run"></a>Erreur apparaît lorsqu’un flux de travail réutilisable importé qui contient un champ de formulaire de tâche est exécutée.  
 Ce problème se produit si vous importez un flux de travail qui contient un formulaire de tâche qui a un champ, puis exécutez le nouveau flux de travail sur le même système à partir de laquelle vous l’avez importé.  
  
### <a name="error-message"></a>Message d'erreur  
 Une erreur s’est produite à l’étape de déploiement « Activer les fonctionnalités » : le champ avec l’Id [*Guid*] défini dans la fonctionnalité [*Guid*] a été trouvé dans la collection de sites actuelle ou dans un sous-site.  
  
### <a name="resolution"></a>Résolution  
 Cette erreur est le résultat de collisions d’ID de champ qui se produisent parce que le flux de travail réutilisable importation de projet dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ne modifie pas le champ ID de tâche. Si vous déployez un flux de travail importé sur le même serveur qui contient le flux de travail d’origine, des collisions d’ID de champ se produisent.  
  
 Pour résoudre ce problème, utilisez la fonctionnalité Rechercher et remplacer pour modifier la valeur de l’attribut ID de champ dans tous les fichiers de flux de travail importé.  
  
## <a name="error-appears-when-a-renamed-imported-list-instance-is-run"></a>Erreur s’affiche lorsque importée renommée Instance de liste est exécuté.  
 Ce problème se produit si vous renommez une instance de liste importée et exécutez [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
### <a name="error-message"></a>Message d'erreur  
 Erreur de build : une erreur s’est produite à l’étape de déploiement « Activer les fonctionnalités » : le fichier Template\Features\\[*importer le projet**fonctionnalité**nom*] \Files\Lists \\[*ancien**nom de la liste*] \Schema.xml n’existe pas.  
  
### <a name="resolution"></a>Résolution  
 Lorsque vous importez une instance de liste, un attribut nommé CustomSchema est ajouté au fichier Elements.xml de l’instance de liste. Le fichier Elements.XML inclut le chemin d’accès d’un fichier schema.xml personnalisé pour l’instance de liste. Lorsque vous renommez l’instance de liste dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], le chemin d’accès de déploiement pour le fichier schema.xml personnalisé change, mais la valeur de chemin d’accès de l’attribut CustomSchema n’est pas mis à jour. Par conséquent, l’instance de liste ne peut pas trouver le fichier schema.xml dans l’ancien chemin d’accès spécifié par l’attribut CustomSchema lorsque la fonctionnalité est activée.  
  
 Pour résoudre ce problème, mettez à jour le chemin d’accès de l’emplacement de déploiement du fichier schema.xml dans l’attribut CustomSchema.  
  
## <a name="sharepoint-debugging-session-terminated-by-iis"></a>SharePoint interrompue par IIS de Session de débogage  
 Ce problème se produit si vous définissez un point d’arrêt dans un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] solution SharePoint, choisissez la touche F5 pour l’exécuter, puis il restera à un point d’arrêt pendant plu de 90 secondes.  
  
### <a name="error-message"></a>Message d'erreur  
 Le processus de serveur Web qui était en cours de débogage a été arrêté par Internet Information Services (IIS). Pour éviter que cette situation ne se présente, configurez les paramètres Ping du pool d'applications dans IIS. Consultez l’aide pour plus d’informations.  
  
### <a name="resolution"></a>Résolution  
 Par défaut, le pool d’applications IIS attend pendant 90 secondes pour une application de répondre avant la fermeture de l’application. Ce processus est appelé « ping » de l’application. Pour résoudre ce problème, vous pouvez augmenter le délai d’attente ou désactivation de l’application de test ping entièrement.  
  
##### <a name="to-access-the-iis-app-pool-settings"></a>Pour accéder aux paramètres de pool d’application IIS  
  
1.  Ouvrez le gestionnaire des services Internet (IIS).  
  
2.  Dans le **connexions** volet, développez le nœud du serveur SharePoint, puis choisissez le **Pools d’applications** nœud.  
  
3.  Sur le **Pools d’applications** page, choisissez le pool d’applications SharePoint (en général « SharePoint – 80 »), puis, dans le **Actions** volet, choisissez la **paramètres avancés** lien.  
  
4.  Pour augmenter le temps d’attente avant le délai d’IIS, modifiez la valeur de **le temps de réponse Maximum Ping (secondes)** à une valeur qui est supérieure à 90 secondes.  
  
5.  Pour désactiver IIS exécutant la commande ping, définissez **Ping activé** à **False**.  
  
## <a name="auto-retract-leaves-orphaned-list-instance-in-sharepoint"></a>Instance de liste orpheline retrait automatique laisse dans SharePoint  
 Ce problème se produit si vous procédez comme suit.  
  
1.  Créer une définition de liste qui a une instance de liste dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Sélectionnez la touche F5 pour exécuter la solution.  
  
3.  Arrêter le débogage, ou fermez le site SharePoint.  
  
4.  Rouvrez le site SharePoint et ouvrez l’instance de liste.  
  
### <a name="error-message"></a>Message d'erreur  
 Erreur de serveur dans l’Application '/'.  
  
### <a name="resolution"></a>Résolution  
 Cela se produit, car une fois que vous fermez une session de débogage d’une solution SharePoint, le retrait automatique fonctionnalité permet de retirer la solution. Le retrait supprime la définition de liste SharePoint, mais ne supprime pas l’instance de la liste. La définition de la liste sous-jacente est requise par l’instance de liste.  
  
 Pour résoudre ce problème, déployez la solution, sur la barre de menus, en choisissant **générer**, **déployer**. (Ne déboguez pas la solution en choisissant la touche F5.) Ensuite, supprimez l’instance de liste dans SharePoint.  
  
## <a name="original-sharepoint-solution-is-replaced-by-an-exported-version"></a>La SharePoint Solution d’origine est remplacée par une Version exportée  
 Si vous exportez une solution SharePoint, importez la solution dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]et ensuite déployer la solution sur le même site à partir duquel il a été exporté, la solution SharePoint d’origine est remplacée. Ce problème ne se produit pas si vous déployez la solution sur un serveur qui ne dispose pas de la solution d’origine est activée sur ce dernier.  
  
### <a name="error-message"></a>Message d'erreur  
 Aucun.  
  
### <a name="resolution"></a>Résolution  
 Pour éviter le remplacement d’une solution sur le site à partir duquel il a été exporté, modifiez les GUID de SolutionID et les ID de fonctionnalité de toutes les fonctionnalités importées dans le [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projet.  
  
## <a name="error-appears-when-debugging-starts"></a>Une erreur survient lors du démarrage du débogage  
 Lorsque vous commencez à déboguer une solution SharePoint dans Visual Studio, vous obtenez une erreur indiquant que Visual Studio n'a pas pu charger le fichier de configuration Web.config parce que la clé spécifiée n'était pas présente dans le dictionnaire.  
  
### <a name="error-message"></a>Message d'erreur  
 Impossible de charger pas le fichier de configuration Web.config. Vérifiez le fichier pour tous les éléments XML mal formés et réessayez. L’erreur suivante s’est produite : la clé donnée était absente du dictionnaire.  
  
### <a name="resolution"></a>Résolution  
 Pour résoudre ce problème, assurez-vous que la valeur de la propriété URL du site du projet SharePoint dans Visual Studio correspond à l'URL attribuée à la zone par défaut pour les mappages des accès de substitution de l'application Web. L'utilisation d'une autre zone, telle que l'Intranet, pour l'URL ne résout pas l'erreur. La propriété URL du site du projet et l'URL de la zone par défaut doivent être identiques. Pour accéder aux mappages des accès de substitution, ouvrez l’utilitaire d’Administration centrale de SharePoint 2010, choisissez le **gestion des applications** lien, puis, sous **Applications Web**, choisissez le  **Configurer les mappages des accès de substitution** lien. Pour plus d’informations, consultez [créer des zones pour les applications Web](http://go.microsoft.com/fwlink/?LinkId=192274).  
  
## <a name="see-also"></a>Voir aussi  
 [Résolution des problèmes d’empaquetage de SharePoint et de déploiement](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md)   
 [Génération et débogage de solutions SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)   
 [Débogage dans Visual Studio](/visualstudio/debugger/debugging-in-visual-studio)  
  
  
