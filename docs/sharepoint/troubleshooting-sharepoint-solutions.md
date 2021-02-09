---
title: Résolution des problèmes des solutions SharePoint | Microsoft Docs
description: Consultez les problèmes ou alertes susceptibles de se produire lorsque vous déboguez des solutions SharePoint à l’aide du débogueur Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/22/2017
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
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: c6b0e031e96d2543ae0bb109f243824125f431a3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99892292"
---
# <a name="troubleshoot-sharepoint-solutions"></a>Résoudre les problèmes des solutions SharePoint
  Les problèmes ou alertes suivants peuvent se produire lorsque vous déboguez des solutions SharePoint à l’aide du [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] débogueur. Pour plus d’informations, consultez [débogage de solutions de flux de travail SharePoint 2007](/previous-versions/bb386166(v=vs.100)).

## <a name="token-restrictions-in-sandboxed-visual-web-parts"></a>Restrictions de jeton dans les composants Visual Web part sandbox
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

## <a name="character-restrictions-in-names-of-projects-and-project-items"></a>Restrictions de caractères dans les noms de projets et d’éléments de projet
 Les noms de projets et d'éléments de projet peuvent contenir uniquement des caractères qui sont valides dans un chemin de déploiement dans SharePoint 2010. Aucun autre caractère n’est autorisé.

### <a name="error-message"></a>Message d’erreur
 Message d’erreur « caractères non valides ».

### <a name="resolution"></a>Résolution
 Pour les noms de projets et d'éléments de projet SharePoint, utilisez uniquement les caractères suivants :

- Caractères ASCII alphanumériques

- Espace

- Point (.)

- Virgule (,)

- Trait de soulignement (_)

- Tiret (-)

- Barre oblique inverse (\\)

  Lorsqu'un projet est empaqueté, une règle de validation vérifie que la propriété du chemin d'accès de déploiement de chaque fichier déployé contient uniquement ces caractères valides.

## <a name="errors-when-creating-custom-fields"></a>Erreurs lors de la création de champs personnalisés
 Dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], les champs personnalisés sont définis dans XML. Des erreurs peuvent survenir si un champ n'est pas défini, ni référencé à l'aide d'un format spécifique.

### <a name="error-message"></a>Message d’erreur
 Message d’erreur « caractères non valides » au moment de l’empaquetage.

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

 Comme le montre l’exemple suivant, une référence de champ dans un type de contenu doit être définie à l’aide du format d’élément vide ( \<FieldRef /> ), et non à l’aide d’éléments start/end ( \<FieldRef> \</FieldRef> ) :

```xml
<FieldRef ID="{5744d18c-305e-4632-8bd1-09d134f4830d}"
    Name="PatientName"
    DisplayName="Patient Name"
    Required="TRUE"/>
```

 En cas de problème avec le code XML source pour le champ, par exemple s'il est incorrect ou si le fichier XML n'est pas valide, l'erreur d'analyse "Impossible d'analyser le fichier" du fichier survient.

## <a name="new-non-english-site-definitions-do-not-appear-in-site-creation-page-after-deployment"></a>Les nouvelles définitions de site non anglaises n’apparaissent pas dans la page de création de site après le déploiement
 Une fois que vous avez créé et déployé une définition de site à l’aide d’une version non anglaise de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] (autrement dit, une version avec des paramètres régionaux [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] autres que 1033), l’onglet **personnalisations de SharePoint** ne s’affiche pas dans la zone de **sélection du modèle** et le nouveau modèle de site n’apparaît pas dans la page **nouveau site SharePoint** .

### <a name="error-message"></a>Message d’erreur
 Aucun.

### <a name="resolution"></a>Résolution
 Ce problème se produit en raison d’une valeur incorrecte dans la propriété **path** du fichier de configuration de la définition de site WebTemp, par exemple *webtemp_SiteDefinitionProject1.xml*. Dans la propriété **chemin d’accès** du fichier WebTemp, situé sous l’emplacement de **déploiement**, remplacez 1033 par les paramètres régionaux appropriés [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] . Par exemple, pour utiliser des paramètres régionaux japonais, remplacez la valeur par 1041. Pour plus d'informations, consultez [Locale IDs Assigned by Microsoft (en anglais)](/openspecs/windows_protocols/ms-lcid/a9eac961-e77d-41a6-90a5-ce1a8b0cdb9c).

## <a name="error-appears-when-a-workflow-project-is-deployed-on-a-clean-system"></a>Une erreur s’affiche lorsqu’un projet de workflow est déployé sur un système propre
 Ce problème se produit si vous déployez un projet de flux de travail dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] sur un système propre. Un système propre est un ordinateur avec une nouvelle installation de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] et SharePoint, sans aucun projet de flux de travail déployé.

### <a name="error-message"></a>Message d’erreur
 Impossible de trouver la liste SharePoint : historique du flux de travail.

### <a name="resolution"></a>Résolution
 Cette erreur se produit en raison d’une liste d’historique de flux de travail manquante. Étant donné que l’environnement de développement est un système propre, aucun flux de travail n’est déployé et la liste d’historique du flux de travail n’existe pas encore. Pour résoudre ce problème, rouvrez l’Assistant flux de travail, ce qui entraîne la création de la liste historique du flux de travail.

##### <a name="to-reenter-the-workflow-wizard"></a>Pour entrer de nouveau dans l’Assistant flux de travail

1. Dans **Explorateur de solutions**, choisissez le nœud flux de travail.

2. Dans la fenêtre **Propriétés** , choisissez le bouton représentant des points de suspension (...) sur toute propriété qui contient un bouton de sélection.

## <a name="user-must-refresh-application-page-in-browser-while-debugging-to-view-updated-image"></a>L’utilisateur doit actualiser la page d’application dans le navigateur pendant le débogage pour afficher l’image mise à jour
 Si vous déboguez une solution SharePoint qui contient une page d’application avec un contrôle qui affiche une image, tel qu’un [!INCLUDE[TLA2#tla_html](../sharepoint/includes/tla2sharptla-html-md.md)] contrôle image, vous devez actualiser la page dans le navigateur pour afficher les modifications apportées à l’image.

## <a name="error-the-site-location-is-not-valid"></a>Erreur : l’emplacement du site n’est pas valide
 Ce problème peut se produire si [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] n’est pas installé. Cela peut également se produire si vous n’avez pas d’accès administrateur au site Web SharePoint qui est spécifié dans l' **Assistant Personnalisation de SharePoint**.

### <a name="error-message"></a>Message d’erreur

- L’emplacement du site SharePoint n’est pas valide.

### <a name="resolution"></a>Résolution

- Installez [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)].

- Vérifiez que vous disposez d’un accès administrateur au site Web SharePoint. Pour plus d’informations, consultez l' [!INCLUDE[TLA2#tla_office](../sharepoint/includes/tla2sharptla-office-md.md)] article en ligne [affecter ou supprimer des administrateurs d’applications de service dans SharePoint Server](/sharepoint/administration/assign-or-remove-administrators-of-service-applications).

## <a name="site-deletion-web-event-does-not-occur-in-event-receiver-project"></a>L’événement Web de suppression de site ne se produit pas dans le projet de récepteur d’événements
 Lorsque vous créez un projet de récepteur d’événements et que vous sélectionnez certains événements Web tels que « un site est en cours de suppression », l’événement ne se produit jamais.

### <a name="error-message"></a>Message d’erreur
 Aucun.

### <a name="resolution"></a>Résolution
 Ce problème se produit car l’étendue de la fonctionnalité doit être « site » pour gérer les événements au niveau du site, mais l’étendue des fonctionnalités par défaut pour les projets de récepteur d’événements est « Web ». Les événements Web affectés sont les suivants :

- Un site est en cours de suppression (Websuppression)

- Un site a été supprimé (suppression de websupprimée)

- Un site est en cours de déplacement (webmove)

- Un site a été déplacé (Web déplacé)

  Pour résoudre le problème, modifiez l’étendue de la fonctionnalité du récepteur d’événements, comme suit.

##### <a name="to-change-the-feature-scope-of-the-event-receiver"></a>Pour modifier l’étendue des fonctionnalités du récepteur d’événements

1. Dans **Explorateur de solutions**, ouvrez le fichier *. Feature* du récepteur d’événements dans le **Concepteur de fonctionnalités** en double-cliquant sur le fichier ou en ouvrant le menu contextuel, puis en choisissant **ouvrir**.

2. Choisissez la flèche en regard de **étendue**, puis choisissez **site** dans la liste qui s’affiche.

## <a name="deployment-error-appears-after-the-name-of-an-identifier-in-a-business-data-connectivity-model-project-is-changed"></a>Une erreur de déploiement s’affiche après la modification du nom d’un identificateur dans un projet de modèle de connectivité de données métiers
 Ce problème se produit si vous modifiez le nom de l’identificateur d’une entité dans un modèle de connectivité de données métiers (BDC), puis que vous essayez de déployer la solution.

### <a name="error-messages"></a>Messages d’erreur

- \<*model name*> contient les erreurs d’activation de type de contenu externe suivantes...

- Le IMetadataObject avec le nom « \<*model name*> » a une valeur dans le champ « Name » qui est dupliqué...

### <a name="resolution"></a>Résolution
 Pour résoudre ce problème, supprimez le modèle manuellement, puis déployez de nouveau la solution.  Vous pouvez supprimer le modèle à l’aide de l’un des outils suivants :

- Administration centrale de SharePoint 2010. Pour plus d’informations, consultez [gestion des modèles BDC](/previous-versions/office/sharepoint-server-2010/ee524073(v=office.14)#delete-a-bdc-model) sur le site Web Microsoft TechNet.

- Windows PowerShell. Vous pouvez supprimer le modèle en tapant la commande suivante à l’invite de commandes : **Remove-SPBusinessDataCatalogModel**. Pour plus d’informations, consultez [applets de commande générales (SharePoint Server 2010)](/powershell/module/sharepoint-server) sur le site Web Microsoft TechNet.

## <a name="an-error-appears-when-you-try-to-view-a-visual-web-part-in-sharepoint"></a>Une erreur s’affiche lorsque vous essayez d’afficher un composant Visual Web part dans SharePoint
 Ce problème se produit lorsque la propriété **path** du contrôle utilisateur ne commence pas par la chaîne « CONTROLTEMPLATES \\ ».

### <a name="error-messages"></a>Messages d’erreur

- Le fichier'/_controltemplates/ *\<project name>* / *\<Web Part name>* / *\<user control name>* . ascx’n’existe pas.

- Erreur de serveur dans l’application « / ».

### <a name="resolution"></a>Résolution

##### <a name="to-resolve-this-issue"></a>Pour résoudre ce problème

1. Dans **Explorateur de solutions**, choisissez le fichier de contrôle utilisateur, dont l’extension de nom de fichier est *. ascx*.

2. Dans la barre de menus, choisissez **Afficher** la  >  **fenêtre Propriétés**.

3. Dans la fenêtre **Propriétés** , développez le nœud **emplacement de déploiement** .

4. Vérifiez que la valeur de la propriété **path** commence par la chaîne « CONTROLTEMPLATES \\ ».

## <a name="error-appears-when-an-imported-reusable-workflow-that-contains-a-task-form-field-is-run"></a>Une erreur s’affiche lors de l’exécution d’un flux de travail réutilisable importé qui contient un champ de formulaire de tâche
 Ce problème se produit si vous importez un flux de travail qui contient un formulaire de tâche contenant un champ, puis exécutez le nouveau flux de travail sur le même système que celui à partir duquel vous l’avez importé.

### <a name="error-message"></a>Message d’erreur
 Une erreur s’est produite lors de l’étape de déploiement « activation des fonctionnalités » : le champ avec l’ID [*GUID*] défini dans la fonctionnalité [*GUID*] a été trouvé dans la collection de sites actuelle ou dans un sous-site.

### <a name="resolution"></a>Résolution
 Cette erreur est le résultat des collisions d’ID de champ qui se produisent parce que le projet importer le flux de travail réutilisable dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ne modifie pas les ID des champs de formulaire de tâche. Si vous déployez un flux de travail importé sur le serveur qui contient le flux de travail d’origine, des collisions d’ID de champ se produisent.

 Pour résoudre ce problème, utilisez la fonctionnalité Rechercher et remplacer pour modifier la valeur de l’attribut ID de champ dans tous les fichiers de flux de travail importés.

## <a name="error-appears-when-a-renamed-imported-list-instance-is-run"></a>Une erreur s’affiche lors de l’exécution d’une instance de liste importée renommée
 Ce problème se produit si vous renommez une instance de liste importée, puis que vous l’exécutez dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

### <a name="error-message"></a>Message d’erreur
 Erreur de build : une erreur s’est produite lors de l’étape de déploiement’activer les fonctionnalités' : le fichier Template\Features \\ [*Import Project*<em>Feature</em>*Name*] \Files\Lists \\ [*Old*<em>List Name</em>] \Schema.xml n’existe pas.

### <a name="resolution"></a>Résolution
 Lorsque vous importez une instance de liste, un attribut nommé CustomSchema est ajouté au fichier Elements.xml de l’instance de liste. Elements.xml comprend le chemin d’accès d’une schema.xml personnalisée pour l’instance de liste. Lorsque vous renommez l’instance de liste dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , le chemin de déploiement de l' schema.xml personnalisé change, mais la valeur de chemin d’accès de l’attribut CustomSchema n’est pas mise à jour. Par conséquent, l’instance de liste ne peut pas trouver le fichier *schema.xml* dans l’ancien chemin d’accès spécifié par l’attribut CustomSchema lorsque la fonctionnalité est activée.

 Pour résoudre ce problème, mettez à jour le chemin d’accès de l’emplacement de déploiement du fichier *schema.xml* dans l’attribut CustomSchema.

## <a name="sharepoint-debugging-session-terminated-by-iis"></a>Session de débogage SharePoint terminée par IIS
 Ce problème se produit si vous définissez un point d’arrêt dans une solution SharePoint, que vous appuyez sur [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] la touche **F5** pour l’exécuter, puis que vous restez à un point d’arrêt d’une durée supérieure à 90 secondes.

### <a name="error-message"></a>Message d’erreur
 Le processus de serveur Web qui était en cours de débogage a été arrêté par Internet Information Services (IIS). Pour éviter que cette situation ne se présente, configurez les paramètres Ping du pool d'applications dans IIS. Pour plus d’informations, consultez l’aide.

### <a name="resolution"></a>Résolution
 Par défaut, le pool d’applications IIS attend 90 secondes qu’une application réponde avant de fermer l’application. Ce processus est appelé « test ping » de l’application. Pour résoudre ce problème, vous pouvez augmenter le délai d’attente ou désactiver complètement l’exécution de la commande ping de l’application.

##### <a name="to-access-the-iis-app-pool-settings"></a>Pour accéder aux paramètres du pool d’applications IIS

1. Ouvrez le Gestionnaire des services IIS.

2. Dans le volet **connexions** , développez le nœud serveur SharePoint, puis choisissez le nœud **pools d’applications** .

3. Dans la page **pools d’applications** , choisissez le pool d’applications SharePoint (généralement « sharepoint-80 »), puis, dans le volet **actions** , choisissez le lien **Paramètres avancés** .

4. Pour augmenter le délai d’attente avant l’expiration du délai d’attente IIS, remplacez la valeur du **temps de réponse maximal ping (secondes)** par une valeur supérieure à 90 secondes.

5. Pour désactiver la commande ping IIS, attribuez la valeur **false** à **ping activé** .

## <a name="auto-retract-leaves-orphaned-list-instance-in-sharepoint"></a>Le retrait automatique laisse l’instance de liste orpheline dans SharePoint
 Ce problème se produit si vous effectuez les étapes suivantes.

1. Créez une définition de liste avec une instance de liste dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

2. Appuyez sur la touche **F5** pour exécuter la solution.

3. Arrêtez le débogage ou fermez le site SharePoint.

4. Rouvrez le site SharePoint et ouvrez l’instance de liste.

### <a name="error-message"></a>Message d’erreur
 Erreur de serveur dans l’application « / ».

### <a name="resolution"></a>Résolution
 Cela se produit car une fois que vous avez fermé une session de débogage d’une solution SharePoint, la fonctionnalité de retrait automatique rétracte la solution. La rétractation supprime la définition de liste de SharePoint, mais ne supprime pas l’instance de la liste. La définition de liste sous-jacente est requise par l’instance de liste.

 Pour résoudre ce problème, déployez la solution en cliquant sur la barre de menus, puis sur **générer**  >  **déployer**. (Ne déboguez pas la solution en choisissant la touche **F5** .) Ensuite, supprimez l’instance de liste dans SharePoint.

## <a name="original-sharepoint-solution-is-replaced-by-an-exported-version"></a>La solution SharePoint d’origine est remplacée par une version exportée
 Si vous exportez une solution SharePoint, importez la solution dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , puis déployez la solution sur le même site que celui à partir duquel elle a été exportée, la solution SharePoint d’origine est remplacée. Ce problème ne se produit pas si vous déployez la solution sur un serveur sur lequel la solution d’origine n’est pas activée.

### <a name="error-message"></a>Message d’erreur
 Aucun.

### <a name="resolution"></a>Résolution
 Pour éviter de remplacer une solution sur le site à partir duquel elle a été exportée, modifiez les GUID de SolutionID et les ID de fonctionnalités de toutes les fonctionnalités importées dans le [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projet.

## <a name="error-appears-when-debugging-starts"></a>Une erreur s’affiche au démarrage du débogage
 Lorsque vous commencez à déboguer une solution SharePoint dans Visual Studio, vous obtenez une erreur indiquant que Visual Studio n'a pas pu charger le fichier de configuration Web.config parce que la clé spécifiée n'était pas présente dans le dictionnaire.

### <a name="error-message"></a>Message d’erreur
 Impossible de charger le fichier de configuration Web.config. Vérifiez les éléments XML incorrects dans le fichier, puis réessayez. L’erreur suivante s’est produite : la clé donnée n’était pas présente dans le dictionnaire.

### <a name="resolution"></a>Résolution
 Pour résoudre ce problème, assurez-vous que la valeur de la propriété URL du site du projet SharePoint dans Visual Studio correspond à l'URL attribuée à la zone par défaut pour les mappages des accès de substitution de l'application Web. L'utilisation d'une autre zone, telle que l'Intranet, pour l'URL ne résout pas l'erreur. La propriété URL du site du projet et l'URL de la zone par défaut doivent être identiques. Pour accéder aux mappages des accès de substitution, ouvrez l’utilitaire d’administration centrale de SharePoint 2010, choisissez le lien **gestion des applications** , puis, sous **applications Web**, choisissez le lien **configurer les mappages des accès de substitution** . Pour plus d’informations, consultez [créer des zones pour des applications Web](/previous-versions/office/sharepoint-2007-products-and-technologies/cc263087(v=office.12)).

## <a name="see-also"></a>Voir aussi

- [Résoudre les problèmes d’empaquetage et de déploiement SharePoint](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md)
- [Générer et déboguer des solutions SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)
- [Débogage dans Visual Studio](../debugger/debugger-feature-tour.md)