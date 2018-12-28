---
title: Dépannage des Solutions SharePoint | Microsoft Docs
ms.custom: ''
ms.date: 02/22/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- Microsoft.VisualStudio.Tools.SharePoint.Errors.Debugging
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, troubleshooting
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 103595772c5597eadb251e1d21befba88df2c9d2
ms.sourcegitcommit: f6dd17b0864419083d0a1bf54910023045526437
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/27/2018
ms.locfileid: "53803199"
---
# <a name="troubleshoot-sharepoint-solutions"></a>Résoudre les problèmes des solutions SharePoint
  Les alertes ou les problèmes suivants peuvent se produire lorsque vous déboguez des solutions SharePoint à l’aide de la [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] débogueur. Pour plus d’informations, consultez [débogage de Solutions de flux de travail 2007 SharePoint](https://msdn.microsoft.com/3a5392f3-66f3-48be-956e-02de23fa6247).

## <a name="token-restrictions-in-sandboxed-visual-web-parts"></a>Restrictions des jetons dans les composants WebPart visuels bac à sable
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
 Message d’erreur « Caractères non valides ».

### <a name="resolution"></a>Résolution
 Pour les noms de projets et d'éléments de projet SharePoint, utilisez uniquement les caractères suivants :

- Caractères ASCII alphanumériques

- Espace

- Point (.)

- Virgule ()

- Trait de soulignement (_)

- Tiret (-)

- Barre oblique inverse (\\)

  Lorsqu’un projet est empaqueté, une règle de validation vérifie que la propriété du chemin d’accès de déploiement de chaque fichier déployé contient uniquement ces caractères valides.

## <a name="errors-when-creating-custom-fields"></a>Erreurs lors de la création de champs personnalisés
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

 Comme le montre l’exemple suivant, une référence de champ dans un type de contenu doit être définie en utilisant le format d’élément vide (\<FieldRef / >), ne pas à l’aide des éléments de début/fin (\<FieldRef >\</FieldRef >) :

```xml
<FieldRef ID="{5744d18c-305e-4632-8bd1-09d134f4830d}"
    Name="PatientName"
    DisplayName="Patient Name"
    Required="TRUE"/>
```

 En cas de problème avec le code XML source pour le champ, par exemple s'il est incorrect ou si le fichier XML n'est pas valide, l'erreur d'analyse "Impossible d'analyser le fichier" du fichier survient.

## <a name="new-non-english-site-definitions-do-not-appear-in-site-creation-page-after-deployment"></a>Nouvelles définitions de site non anglaises n’apparaissent pas dans la page de création de site après le déploiement
 Une fois que vous créez et déployez une définition de site à l’aide d’une version non anglaise de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] (autrement dit, une version avec des paramètres régionaux [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] autres que 1033), le **personnalisations de SharePoint** onglet n’apparaît pas dans le **Sélection du modèle** boîte et le nouveau modèle de site n’apparaît pas dans le **nouveau SharePoint Site** page.

### <a name="error-message"></a>Message d'erreur
 Aucun.

### <a name="resolution"></a>Résolution
 Ce problème se produit en raison d’une valeur incorrecte dans le **chemin d’accès** fichier de propriété pour la configuration de définition de site webtemp, telles que *webtemp_SiteDefinitionProject1.xml*. Dans le **chemin d’accès** propriété pour le fichier webtemp, situé sous le **emplacement de déploiement**, remplacez 1033 par les paramètres régionaux appropriés [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)]. Par exemple, pour utiliser un paramètre régional japonais modifier la valeur par 1041. Pour plus d’informations, consultez [ID de paramètres régionaux assignés par Microsoft](http://go.microsoft.com/fwlink/?LinkID=165561).

## <a name="error-appears-when-a-workflow-project-is-deployed-on-a-clean-system"></a>Erreur s’affiche lorsqu’un projet de flux de travail est déployé sur un système propre
 Ce problème se produit si vous déployez un projet de flux de travail dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] sur un système propre. Un système propre est un ordinateur avec une nouvelle installation de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] et SharePoint, sans aucun projet de flux de travail déployé.

### <a name="error-message"></a>Message d'erreur
 Impossible de trouver la liste SharePoint : Historique de flux de travail.

### <a name="resolution"></a>Résolution
 Cette erreur se produit en raison d’une liste d’historique de flux de travail manquante. Étant donné que l’environnement de développement est un système propre, aucun flux de travail n’est déployées et la liste d’historique de flux de travail n’existe pas encore. Pour résoudre ce problème, rouvrez l’Assistant flux de travail, ce qui provoque la liste d’historique de flux de travail à créer.

##### <a name="to-reenter-the-workflow-wizard"></a>Pour entrer de nouveau l’Assistant flux de travail

1.  Dans **l’Explorateur de solutions**, choisissez le nœud de flux de travail.

2.  Dans le **propriétés** fenêtre, cliquez sur le bouton points de suspension (...) sur n’importe quelle propriété qui a un bouton de sélection.

## <a name="user-must-refresh-application-page-in-browser-while-debugging-to-view-updated-image"></a>Utilisateur doit actualiser la page d’application dans un navigateur pendant le débogage pour afficher l’image mise à jour
 Si vous déboguez une solution SharePoint qui contient une page d’application avec un contrôle qui affiche une image, tel qu’un [!INCLUDE[TLA2#tla_html](../sharepoint/includes/tla2sharptla-html-md.md)] contrôle d’Image, vous devez actualiser la page dans le navigateur pour afficher toutes les modifications qui ont été apportées à l’image.

## <a name="error-the-site-location-is-not-valid"></a>Erreur : L’emplacement du site n’est pas valide
 Ce problème peut se produire si [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] n’est pas installé. Il peut également se produire si vous n’avez pas l’accès administrateur au site SharePoint Web qui est spécifié dans le **Assistant Personnalisation de SharePoint**.

### <a name="error-message"></a>Message d'erreur

-   Emplacement du site SharePoint n’est pas valide.

### <a name="resolution"></a>Résolution

-   Installez [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)].

-   Assurez-vous d’avoir un accès administrateur au site Web de SharePoint. Pour plus d’informations, consultez le [!INCLUDE[TLA2#tla_office](../sharepoint/includes/tla2sharptla-office-md.md)] article en ligne [affecter ou supprimer des administrateurs d’applications de service dans SharePoint Server](https://docs.microsoft.com/sharepoint/administration/assign-or-remove-administrators-of-service-applications).

## <a name="site-deletion-web-event-does-not-occur-in-event-receiver-project"></a>Événement de web site suppression ne se produit pas dans le projet de récepteur d’événements
 Lorsque vous créez un projet de récepteur d’événements et vous sélectionnez certains événements Web tels que « un site est en cours de suppression », l’événement se produit jamais.

### <a name="error-message"></a>Message d'erreur
 Aucun.

### <a name="resolution"></a>Résolution
 Ce problème se produit car l’étendue de fonctionnalité doit être « Site » pour gérer les événements au niveau du site, mais l’étendue de fonctionnalité par défaut pour les projets de récepteur d’événement est « Web ». Les événements Web affectés sont :

- Un site est en cours de suppression (WebDeleting)

- Un site a été supprimé (WebDeleted)

- Un site est en cours de déplacement (WebMoving)

- Un site a été déplacé (WebMoved)

  Pour résoudre le problème, modifiez l’étendue de la fonctionnalité du récepteur d’événements, comme suit.

##### <a name="to-change-the-feature-scope-of-the-event-receiver"></a>Pour modifier l’étendue de fonctionnalité du récepteur d’événements

1.  Dans **l’Explorateur de solutions**, ouvrez le récepteur d’événements *.feature* de fichiers dans le **Concepteur de fonctionnalités** en double-cliquant sur le fichier ou en ouvrant le menu contextuel, puis en choisissant **Open**.

2.  Cliquez sur la flèche à côté **étendue**, puis choisissez **Site** dans la liste qui s’affiche.

## <a name="deployment-error-appears-after-the-name-of-an-identifier-in-a-business-data-connectivity-model-project-is-changed"></a>Erreur de déploiement apparaît une fois que le nom d’un identificateur dans un projet de modèle de connectivité de données métier est modifié
 Ce problème se produit si vous modifiez le nom d’identificateur d’une entité dans un modèle de connectivité de données métiers (BDC) et que vous essayez ensuite de déployer la solution.

### <a name="error-messages"></a>Messages d’erreur

-   \<*nom du modèle*> comporte les erreurs d’activation de Type de contenu externe suivantes...

-   L’objet IMetadataObject portant le nom '\<*nom_modèle*>' a une valeur dans le champ 'name' est dupliquée...

### <a name="resolution"></a>Résolution
 Pour résoudre ce problème, supprimez le modèle manuellement, puis redéployez la solution.  Vous pouvez supprimer le modèle à l’aide des outils suivants :

-   Administration centrale de SharePoint 2010. Pour plus d’informations, consultez [gestion des modèles BDC](http://go.microsoft.com/fwlink/?LinkID=181472) sur le site Web Microsoft TechNet.

-   Windows PowerShell. Vous pouvez supprimer le modèle en tapant cette commande à l’invite de commandes : **Remove-SPBusinessDataCatalogModel**. Pour plus d’informations, consultez [applets de commande générales (SharePoint Server 2010)](http://go.microsoft.com/fwlink/?LinkID=182375) sur le site Web Microsoft TechNet.

## <a name="an-error-appears-when-you-try-to-view-a-visual-web-part-in-sharepoint"></a>Une erreur s’affiche lorsque vous essayez d’afficher un composant visual WebPart dans SharePoint
 Ce problème se produit lorsque le **chemin d’accès** propriété du contrôle utilisateur ne commence pas par la chaîne « CONTROLTEMPLATES\\».

### <a name="error-messages"></a>Messages d’erreur

-   Le fichier ' /_CONTROLTEMPLATES/*\<nom_projet >*/*\<nom du composant WebPart >*/*\<contrôle utilisateur nom >*.ascx' n’existe pas.

-   Erreur de serveur dans l’Application '/'.

### <a name="resolution"></a>Résolution

##### <a name="to-resolve-this-issue"></a>Pour résoudre ce problème

1.  Dans **l’Explorateur de solutions**, choisissez le fichier de contrôle utilisateur, dont l’extension est *.ascx*.

2.  Dans la barre de menus, choisissez **vue** > **fenêtre Propriétés**.

3.  Dans le **propriétés** fenêtre, développez le **emplacement de déploiement** nœud.

4.  Vérifiez que la valeur de la **chemin d’accès** propriété commence par la chaîne « CONTROLTEMPLATES\\».

## <a name="error-appears-when-an-imported-reusable-workflow-that-contains-a-task-form-field-is-run"></a>Erreur apparaît quand un flux de travail réutilisable importé qui contient un champ de formulaire de tâche est exécutée.
 Ce problème se produit si vous importez un flux de travail qui contient un formulaire de tâche qui a un champ, puis exécutez le nouveau flux de travail sur le même système à partir duquel vous l’avez importée.

### <a name="error-message"></a>Message d'erreur
 Erreur lors de l’étape de déploiement « Activer les fonctionnalités » : Le champ avec l’Id [*Guid*] défini dans la fonctionnalité [*Guid*] a été trouvé dans la collection de sites actuelle ou dans un sous-site.

### <a name="resolution"></a>Résolution
 Cette erreur est le résultat de collisions d’ID de champ qui se produisent, car le flux de travail réutilisable importation de projet dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ne modifie pas le champ de formulaire de tâche ID. Si vous déployez un flux de travail importé sur le même serveur qui contient le flux de travail d’origine, des collisions d’ID champ se produisent.

 Pour résoudre ce problème, utilisez la fonctionnalité Rechercher et remplacer pour modifier la valeur de l’attribut ID de champ dans tous les fichiers de flux de travail importé.

## <a name="error-appears-when-a-renamed-imported-list-instance-is-run"></a>Erreur s’affiche lors de l’importation un renommé liste instance est exécutée
 Ce problème se produit si vous renommez une instance de liste importée et exécutez [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

### <a name="error-message"></a>Message d'erreur
 Erreur de build : Erreur lors de l’étape de déploiement « Activer les fonctionnalités » : Le fichier Template\Features\\[*importer le projet*<em>fonctionnalité</em>*nom*] \Files\Lists\\[*ancien* <em>nom de la liste</em>] \Schema.xml n’existe pas.

### <a name="resolution"></a>Résolution
 Lorsque vous importez une instance de liste, un attribut nommé CustomSchema est ajouté au fichier Elements.xml de l’instance de liste. Le fichier Elements.XML inclut le chemin d’accès d’un fichier schema.xml personnalisé pour l’instance de liste. Lorsque vous renommez l’instance de liste dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], modifie le chemin d’accès de déploiement pour le fichier schema.xml personnalisé, mais la valeur de chemin d’accès de l’attribut CustomSchema n’est pas mis à jour. Par conséquent, l’instance de liste ne peut pas trouver le *schema.xml* fichier dans l’ancien chemin d’accès spécifié par l’attribut CustomSchema lorsque la fonctionnalité est activée.

 Pour résoudre ce problème, mettez à jour le chemin d’accès de l’emplacement de déploiement de la *schema.xml* fichier dans l’attribut CustomSchema.

## <a name="sharepoint-debugging-session-terminated-by-iis"></a>SharePoint s’est arrêtée par IIS de session de débogage
 Ce problème se produit si vous définissez un point d’arrêt dans un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] solution SharePoint, choisissez le **F5** clé pour l’exécuter, puis il restera à un point d’arrêt plu de 90 secondes.

### <a name="error-message"></a>Message d'erreur
 Le processus de serveur Web en cours de débogage a été arrêté par Internet Information Services (IIS). Pour éviter que cette situation ne se présente, configurez les paramètres Ping du pool d'applications dans IIS. Consultez l’aide pour plus d’informations.

### <a name="resolution"></a>Résolution
 Par défaut, le pool d’applications IIS attend 90 secondes pour une application de répondre avant la fermeture de l’application. Ce processus est appelé « ping » de l’application. Pour résoudre ce problème, vous pouvez augmenter le délai d’attente ou désactiver l’application effectuant un test ping entièrement.

##### <a name="to-access-the-iis-app-pool-settings"></a>Accéder aux paramètres de pool d’application IIS

1.  Ouvrez le gestionnaire des services Internet (IIS).

2.  Dans le **connexions** volet, développez le nœud du serveur SharePoint, puis choisissez le **Pools d’applications** nœud.

3.  Sur le **Pools d’applications** page, choisissez le pool d’applications SharePoint (généralement « SharePoint - 80 »), puis, dans le **Actions** volet, choisissez le **paramètres avancés** lien.

4.  Pour augmenter le temps d’attente avant le délai d’attente IIS, modifiez la valeur de **le temps de réponse Maximum Ping (secondes)** à une valeur qui est supérieure à 90 secondes.

5.  Pour désactiver IIS exécutant la commande ping, définissez **Ping activé** à **False**.

## <a name="auto-retract-leaves-orphaned-list-instance-in-sharepoint"></a>Retrait automatique laisse instance de liste orpheline dans SharePoint
 Ce problème se produit si vous effectuez les étapes suivantes.

1.  Créer une définition de liste qui a une instance de liste dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2.  Choisissez le **F5** clé pour exécuter la solution.

3.  Arrêter le débogage, ou fermez le site SharePoint.

4.  Rouvrez le site SharePoint et ouvrez l’instance de liste.

### <a name="error-message"></a>Message d'erreur
 Erreur de serveur dans l’Application '/'.

### <a name="resolution"></a>Résolution
 Cela se produit, car une fois que vous fermez une session de débogage d’une solution SharePoint, le retrait automatique fonctionnalité permet de retirer la solution. Le retrait supprime la définition de liste SharePoint, mais ne supprime pas l’instance de la liste. La définition de liste sous-jacente est requise par l’instance de liste.

 Pour résoudre ce problème, déployez la solution, sur la barre de menus, choisissez **Build** > **déployer**. (Ne pas déboguer la solution en choisissant le **F5** clé.) Ensuite, supprimez l’instance de liste dans SharePoint.

## <a name="original-sharepoint-solution-is-replaced-by-an-exported-version"></a>Solution SharePoint d’origine est remplacée par une version exportée
 Si vous exportez une solution SharePoint, importez la solution dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]et ensuite déployer la solution vers le même site à partir duquel il a été exporté, la solution SharePoint d’origine est remplacée. Ce problème ne se produit pas si vous déployez la solution sur un serveur qui n’a pas de la solution d’origine est activée sur ce dernier.

### <a name="error-message"></a>Message d'erreur
 Aucun.

### <a name="resolution"></a>Résolution
 Pour éviter le remplacement d’une solution sur le site à partir duquel il a été exporté, modifier les GUID de SolutionID et les ID de fonctionnalité de toutes les fonctions importées dans le [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projet.

## <a name="error-appears-when-debugging-starts"></a>Erreur s’affiche au démarrage du débogage
 Lorsque vous commencez à déboguer une solution SharePoint dans Visual Studio, vous obtenez une erreur indiquant que Visual Studio n'a pas pu charger le fichier de configuration Web.config parce que la clé spécifiée n'était pas présente dans le dictionnaire.

### <a name="error-message"></a>Message d'erreur
 N’a pas pu charger le fichier de configuration Web.config. Vérifiez le fichier pour tous les éléments XML mal formés et réessayez. L'erreur suivante s'est produite : La clé donnée n’était pas présente dans le dictionnaire.

### <a name="resolution"></a>Résolution
 Pour résoudre ce problème, assurez-vous que la valeur de la propriété URL du site du projet SharePoint dans Visual Studio correspond à l'URL attribuée à la zone par défaut pour les mappages des accès de substitution de l'application Web. L'utilisation d'une autre zone, telle que l'Intranet, pour l'URL ne résout pas l'erreur. La propriété URL du site du projet et l'URL de la zone par défaut doivent être identiques. Pour accéder aux mappages des accès de substitution, ouvrez l’utilitaire d’Administration centrale de SharePoint 2010, choisissez le **gestion des applications** lien, puis, sous **Applications Web**, choisissez le  **Configurer les mappages des accès de substitution** lien. Pour plus d’informations, consultez [créer des zones pour les applications Web](http://go.microsoft.com/fwlink/?LinkId=192274).

## <a name="see-also"></a>Voir aussi

- [Résoudre les problèmes de déploiement et empaquetage de SharePoint](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md)
- [Générer et déboguer des solutions SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)
- [Débogage dans Visual Studio](../debugger/debugging-in-visual-studio.md)