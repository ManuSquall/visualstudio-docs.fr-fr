---
title: 'Procédure pas à pas : Création d’un élément de projet d’Action personnalisé avec un modèle d’élément, partie 1 | Documents Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project items, creating custom templates
- SharePoint project items, defining your own types
- project items [SharePoint development in Visual Studio], defining your own types
- SharePoint development in Visual Studio, defining new project item types
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e690d18bae72b59234f2f90cbcf903b9941df7d6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1"></a>Procédure pas à pas : création d'un élément de projet d'action personnalisé avec un modèle d'élément, première partie
  Vous pouvez étendre le système de projet SharePoint dans Visual Studio en créant des types d’éléments de votre propre projet. Dans cette procédure pas à pas, vous allez créer un élément de projet qui peut être ajouté à un projet SharePoint pour créer une action personnalisée sur un site SharePoint. L’action personnalisée ajoute un élément de menu pour le **Actions du Site** menu du site SharePoint.  
  
 Cette procédure pas à pas décrit les tâches suivantes :  
  
-   Création d’une extension Visual Studio qui définit un nouveau type d’élément de projet SharePoint pour une action personnalisée. Le nouveau type d’élément de projet implémente plusieurs fonctionnalités personnalisées :  
  
    -   Un menu contextuel qui sert de point de départ pour d’autres tâches relatives à l’élément de projet, comme l’affichage d’un concepteur pour l’action personnalisée dans Visual Studio.  
  
    -   Code qui s’exécute lorsqu’un développeur modifie certaines propriétés de l’élément de projet et le projet qui le contient.  
  
    -   Une icône personnalisée qui s’affiche en regard de l’élément de projet dans **l’Explorateur de solutions**.  
  
-   Création d’un modèle d’élément Visual Studio pour l’élément de projet.  
  
-   Création d’un package d’Extension Visual Studio (VSIX) pour déployer le modèle d’élément de projet et l’assembly d’extension.  
  
-   Débogage et test de l’élément de projet.  
  
 Il s’agit d’une procédure pas à pas autonome. Après avoir terminé cette procédure pas à pas, vous pouvez améliorer l’élément de projet en ajoutant un Assistant pour le modèle d’élément. Pour plus d’informations, consultez [procédure pas à pas : création d’un élément de projet d’Action personnalisé avec un modèle d’élément, partie 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md).  
  
> [!NOTE]  
>  Vous pouvez télécharger un exemple qui contient les projets remplis, de code et d’autres fichiers pour cette procédure pas à pas à l’emplacement suivant : [ http://go.microsoft.com/fwlink/?LinkId=191369 ](http://go.microsoft.com/fwlink/?LinkId=191369).  
  
## <a name="prerequisites"></a>Prérequis  
 Vous devez disposer des composants suivants sur l’ordinateur de développement pour terminer cette procédure pas à pas :  
  
-   Éditions prises en charge de Microsoft Windows, SharePoint et Visual Studio. Pour plus d’informations, consultez [configuration requise pour le développement de Solutions SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]. Cette procédure pas à pas utilise le **projet VSIX** modèle dans le Kit de développement pour créer un package VSIX pour déployer l’élément de projet. Pour plus d’informations, consultez [extension des outils SharePoint dans Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
 Connaissance des concepts suivants s’avère utile, mais n’est pas requis pour terminer la procédure pas à pas :  
  
-   Actions personnalisées dans SharePoint. Pour plus d’informations, consultez [Action personnalisée](http://go.microsoft.com/fwlink/?LinkId=177800).  
  
-   Modèles d’élément dans Visual Studio. Pour plus d’informations, consultez [Création de modèles de projet et d’élément](/visualstudio/ide/creating-project-and-item-templates).  
  
## <a name="creating-the-projects"></a>Création des projets  
 Pour effectuer cette procédure pas à pas, vous devez créer trois projets :  
  
-   Un projet VSIX. Ce projet crée le package VSIX pour déployer l’élément de projet SharePoint.  
  
-   Un projet de modèle d’élément. Ce projet crée un modèle d’élément qui peut être utilisé pour ajouter l’élément de projet SharePoint à un projet SharePoint.  
  
-   Un projet de bibliothèque de classes. Ce projet implémente une extension Visual Studio qui définit le comportement de l’élément de projet SharePoint.  
  
 Démarrer la procédure pas à pas en créant les projets.  
  
#### <a name="to-create-the-vsix-project"></a>Pour créer le projet VSIX  
  
1.  Démarrez [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Dans la barre de menus, sélectionnez **Fichier**, **Nouveau**, **Projet**.  
  
3.  Dans la liste en haut de la **nouveau projet** boîte de dialogue zone, assurez-vous que **.NET Framework 4.5** est sélectionnée.  
  
4.  Dans le **nouveau projet** boîte de dialogue, développez le **Visual C#** ou **Visual Basic** nœuds, puis choisissez le **extensibilité** nœud.  
  
    > [!NOTE]  
    >  Le **extensibilité** nœud est disponible uniquement si vous installez le Kit de développement logiciel Visual Studio. Pour plus d’informations, consultez la section conditions préalables plus haut dans cette rubrique.  
  
5.  Choisissez le **projet VSIX** modèle.  
  
6.  Dans le **nom** , entrez **ÉlémentProjetActionPersonnalisée**, puis choisissez le **OK** bouton.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Ajoute le **ÉlémentProjetActionPersonnalisée** projet **l’Explorateur de solutions**.  
  
#### <a name="to-create-the-item-template-project"></a>Pour créer le projet de modèle d’élément  
  
1.  Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour le nœud de solution, choisissez **ajouter**, puis choisissez **nouveau projet**.  
  
2.  Dans la liste en haut de la **nouveau projet** boîte de dialogue zone, assurez-vous que **.NET Framework 4.5** est sélectionnée.  
  
3.  Dans le **nouveau projet** boîte de dialogue, développez le **Visual C#** ou **Visual Basic** nœuds, puis choisissez le **extensibilité** nœud.  
  
4.  Dans la liste des modèles de projet, choisissez la **modèle d’élément c#** ou **modèle d’élément Visual Basic** modèle.  
  
5.  Dans le **nom** , entrez **ItemTemplate**, puis choisissez le **OK** bouton.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Ajoute le **ItemTemplate** projet à la solution.  
  
#### <a name="to-create-the-extension-project"></a>Pour créer le projet d’extension  
  
1.  Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour le nœud de solution, choisissez **ajouter**, puis choisissez **nouveau projet**.  
  
2.  Dans la liste en haut de la **nouveau projet** boîte de dialogue zone, assurez-vous que **.NET Framework 4.5** est sélectionnée.  
  
3.  Dans le **nouveau projet** boîte de dialogue, développez le **Visual C#** ou **Visual Basic** nœuds, choisissez le **Windows** nœud, puis choisissez le  **Bibliothèque de classes** modèle de projet.  
  
4.  Dans le **nom** , entrez **ProjectItemDefinition**, puis choisissez le **OK** bouton.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Ajoute le **ProjectItemDefinition** projet à la solution et ouvre le fichier de code Class1 par défaut.  
  
5.  Supprime le fichier de code Class1 du projet.  
  
## <a name="configuring-the-extension-project"></a>Configuration du projet d’Extension  
 Avant d’écrire de code pour définir le type d’élément de projet SharePoint, vous devez ajouter des fichiers de code et des références d’assembly au projet d’extension.  
  
#### <a name="to-configure-the-project"></a>Pour configurer le projet  
  
1.  Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour le **ProjectItemDefinition** de projet, choisissez **ajouter**, puis choisissez **un nouvel élément**.  
  
2.  Dans la liste des éléments de projet, choisissez **fichier de Code**.  
  
3.  Dans le **nom** , entrez le nom **CustomAction** avec les extension de nom de fichier, puis choisissez le **ajouter** bouton.  
  
4.  Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour le **ProjectItemDefinition** de projet, puis choisissez **ajouter une référence**.  
  
5.  Dans le **Gestionnaire de références - ProjectItemDefinition** boîte de dialogue, choisissez le **assemblys** nœud, puis choisissez le **Framework** nœud.  
  
6.  Sélectionnez la case à cocher en regard de chacun des assemblys suivants :  
  
    -   System.ComponentModel.Composition  
  
    -   System.Windows.Forms  
  
7.  Choisissez le **Extensions** nœud, sélectionnez la case à cocher en regard de l’assembly Microsoft.VisualStudio.Sharepoint, puis choisissez le **OK** bouton.  
  
## <a name="defining-the-new-sharepoint-project-item-type"></a>Définir le nouveau Type d’élément de projet SharePoint  
 Créez une classe qui implémente le <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> interface pour définir le comportement du nouveau type d’élément de projet. Implémentez cette interface chaque fois que vous souhaitez définir un nouveau type d’élément de projet.  
  
#### <a name="to-define-the-new-sharepoint-project-item-type"></a>Pour définir le nouveau type d’élément de projet SharePoint  
  
1.  Dans le projet ProjectItemDefinition, ouvrez le fichier de code CustomAction.  
  
2.  Remplacez le code dans ce fichier par le code suivant.  
  
     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#1](../sharepoint/codesnippet/CSharp/customactionprojectitem/projectitemtypedefinition/customaction.cs#1)]
     [!code-vb[SPExtensibility.ProjectItem.CustomAction#1](../sharepoint/codesnippet/VisualBasic/customactionprojectitem/projectitemdefinition/customaction.vb#1)]  
  
## <a name="creating-an-icon-for-the-project-item-in-solution-explorer"></a>Création d’une icône pour l’élément de projet dans l’Explorateur de solutions  
 Lorsque vous créez un élément de projet SharePoint personnalisé, vous pouvez associer une image (icône ou bitmap) avec l’élément de projet. Cette image s’affiche en regard de l’élément de projet dans **l’Explorateur de solutions**.  
  
 Dans la procédure suivante, vous créez une icône pour l’élément de projet et incorporez l’icône dans l’assembly d’extension. Cette icône est référencée par la <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemIconAttribute> de la `CustomActionProjectItemTypeProvider` classe que vous avez créé précédemment.  
  
#### <a name="to-create-a-custom-icon-for-the-project-item"></a>Pour créer une icône personnalisée pour l’élément de projet  
  
1.  Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour le **ProjectItemDefinition** de projet, choisissez **ajouter**, puis choisissez **un nouvel élément...** .  
  
2.  Dans la liste des éléments de projet, choisissez la **fichier d’icône** élément.  
  
    > [!NOTE]  
    >  Dans les projets Visual Basic, vous devez choisir le **général** nœud pour afficher les **fichier d’icône** élément.  
  
3.  Dans le **nom** , entrez **CustomAction_SolutionExplorer.ico**, puis choisissez le **ajouter** bouton.  
  
     La nouvelle icône s’ouvre dans le **Éditeur d’images**.  
  
4.  Modifier la version de 16 x 16 du fichier icône afin qu’il ait une conception, vous pouvez reconnaître et puis enregistrez le fichier d’icône.  
  
5.  Dans **l’Explorateur de solutions**, choisissez **CustomAction_SolutionExplorer.ico**.  
  
6.  Dans le **propriétés** fenêtre, cliquez sur la flèche à côté du **Action de génération** propriété.  
  
7.  Dans la liste qui s’affiche, choisissez **ressource incorporée**.  
  
## <a name="checkpoint"></a>Point de contrôle  
 À ce stade dans la procédure pas à pas, l’intégralité du code de l’élément de projet est maintenant dans le projet. Générez le projet pour vérifier qu’elle est compilée sans erreur.  
  
#### <a name="to-build-your-project"></a>Pour générer votre projet  
  
1.  Ouvrez le menu contextuel pour le **ProjectItemDefinition** de projet et choisissez **Build**.  
  
## <a name="creating-a-visual-studio-item-template"></a>Création d’un modèle d’élément Visual Studio  
 Pour activer d’autres développeurs d’utiliser votre élément de projet, vous devez créer un modèle de projet ou un modèle d’élément. Les développeurs utilisent ces modèles dans Visual Studio pour créer une instance de votre élément de projet en créant un nouveau projet, ou en ajoutant un élément à un projet existant. Pour cette procédure pas à pas, utilisez le projet ItemTemplate pour configurer votre élément de projet.  
  
#### <a name="to-create-the-item-template"></a>Pour créer le modèle d’élément  
  
1.  Supprimer le fichier de code Class1 du projet ItemTemplate.  
  
2.  Dans le projet ItemTemplate, ouvrez le fichier ItemTemplate.vstemplate.  
  
3.  Remplacez le contenu du fichier par le code XML suivant, puis enregistrez et fermez le fichier.  
  
    > [!NOTE]  
    >  Le code XML suivant est pour un modèle d’élément Visual c#. Si vous créez un modèle d’élément Visual Basic, remplacez la valeur de la `ProjectType` élément avec `VisualBasic`.  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?>  
    <VSTemplate Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" Type="Item">  
      <TemplateData>  
        <DefaultName>CustomAction</DefaultName>  
        <Name>Custom Action</Name>  
        <Description>SharePoint Custom Action by Contoso</Description>  
        <ProjectType>CSharp</ProjectType>  
        <SortOrder>1000</SortOrder>  
        <Icon>ItemTemplate.ico</Icon>  
        <ProvideDefaultName>true</ProvideDefaultName>  
      </TemplateData>  
      <TemplateContent>  
        <ProjectItem ReplaceParameters="true" TargetFileName="$fileinputname$\Elements.xml">Elements.xml</ProjectItem>  
        <ProjectItem ReplaceParameters="true" TargetFileName="$fileinputname$\SharePointProjectItem.spdata">CustomAction.spdata</ProjectItem>  
      </TemplateContent>  
    </VSTemplate>  
    ```  
  
     Ce fichier définit le contenu et le comportement du modèle d’élément. Pour plus d’informations sur le contenu de ce fichier, consultez [référence de schéma de modèle Visual Studio](/visualstudio/extensibility/visual-studio-template-schema-reference).  
  
4.  Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour le **ItemTemplate** de projet, choisissez **ajouter**, puis choisissez **un nouvel élément**.  
  
5.  Dans le **ajouter un nouvel élément** boîte de dialogue, choisissez le **fichier texte** modèle.  
  
6.  Dans le **nom** , entrez **CustomAction.spdata**, puis choisissez le **ajouter** bouton.  
  
7.  Ajoutez le code XML suivant au fichier CustomAction.spdata, puis enregistrez et fermez le fichier.  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?>  
    <ProjectItem Type="Contoso.CustomAction" DefaultFile="Elements.xml"   
     xmlns="http://schemas.microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel">  
      <Files>  
        <ProjectItemFile Source="Elements.xml" Target="$fileinputname$\" Type="ElementManifest" />  
      </Files>  
    </ProjectItem>  
    ```  
  
     Ce fichier contient des informations sur les fichiers qui sont contenus par l’élément de projet. Le `Type` attribut de la `ProjectItem` élément doit être défini sur la même chaîne est passée à la <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute> sur la définition d’élément de projet (la `CustomActionProjectItemTypeProvider` classe que vous avez créé précédemment dans cette procédure pas à pas). Pour plus d’informations sur le contenu des fichiers .spdata, consultez [SharePoint Project Item Schema Reference](../sharepoint/sharepoint-project-item-schema-reference.md).  
  
8.  Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour le **ItemTemplate** de projet, choisissez **ajouter**, puis choisissez **un nouvel élément**.  
  
9. Dans le **ajouter un nouvel élément** boîte de dialogue, choisissez le **fichier XML** modèle.  
  
10. Dans le **nom** , entrez **Elements.xml**, puis choisissez le **ajouter** bouton.  
  
11. Remplacez le contenu du fichier Elements.xml par le code XML suivant, puis enregistrez et fermez le fichier.  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>  
    <Elements Id="$guid8$" xmlns="http://schemas.microsoft.com/sharepoint/">  
      <CustomAction Id="Replace this with a GUID or some other unique string"  
                    GroupId="SiteActions"  
                    Location="Microsoft.SharePoint.StandardMenu"  
                    Sequence="1000"  
                    Title="Replace this with your title"  
                    Description="Replace this with your description" >  
        <UrlAction Url="~site/Lists/Tasks/AllItems.aspx"/>  
      </CustomAction>  
    </Elements>  
    ```  
  
     Ce fichier définit une action personnalisée par défaut qui crée un élément de menu sur le **Actions du Site** menu du site SharePoint. Lorsqu’un utilisateur choisit l’élément de menu, l’URL spécifiée dans le `UrlAction` élément s’ouvre dans le navigateur web. Pour plus d’informations sur les éléments XML que vous pouvez utiliser pour définir une action personnalisée, consultez [définitions d’actions personnalisées](http://go.microsoft.com/fwlink/?LinkId=177801).  
  
12. Si vous le souhaitez, ouvrez le fichier ItemTemplate.ico et modifiez-le afin qu’il ait une conception que vous pouvez identifier. Cette icône s’affichera en regard de l’élément de projet dans le **ajouter un nouvel élément** boîte de dialogue.  
  
13. Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour le **ItemTemplate** de projet, puis choisissez **décharger le projet**.  
  
14. Ouvrez le menu contextuel pour le **ItemTemplate** à nouveau de projet, puis choisissez **Modifier ItemTemplate.csproj** ou **Modifier ItemTemplate.vbproj**.  
  
15. Recherchez les éléments suivants `VSTemplate` élément dans le fichier projet.  
  
    ```  
    <VSTemplate Include="ItemTemplate.vstemplate">  
    ```  
  
16. Remplacez ceci `VSTemplate` élément avec le code XML suivant, puis enregistrez et fermez le fichier.  
  
    ```  
    <VSTemplate Include="ItemTemplate.vstemplate">  
      <OutputSubPath>SharePoint\SharePoint14</OutputSubPath>  
    </VSTemplate>  
    ```  
  
     Le `OutputSubPath` élément spécifie des dossiers supplémentaires dans le chemin d’accès sous lequel le modèle d’élément est créé lorsque vous générez le projet. Les dossiers spécifiés ici garantissent que le modèle d’élément sera disponible uniquement lorsque vous ouvrez des clients le **ajouter un nouvel élément** boîte de dialogue, développez le **SharePoint** nœud, puis choisissez le **2010**  nœud.  
  
17. Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour le **ItemTemplate** de projet, puis choisissez **recharger le projet**.  
  
## <a name="creating-a-vsix-package-to-deploy-the-project-item"></a>Création d’un Package VSIX pour déployer l’élément de projet  
 Pour déployer l’extension, utilisez le projet VSIX dans votre solution pour créer un package VSIX. Tout d’abord, configurez le package VSIX en modifiant le fichier source.extension.vsixmanifest qui est inclus dans le projet VSIX. Ensuite, créez le package VSIX en générant la solution.  
  
#### <a name="to-configure-and-create-the-vsix-package"></a>Pour configurer et créer le package VSIX  
  
1.  Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour le **source.extension.vsixmanifest** de fichiers dans le projet ÉlémentProjetActionPersonnalisée, puis choisissez **ouvrir**.  
  
     Visual Studio ouvre le fichier dans l’éditeur de manifeste. Le fichier source.extension.vsixmanifest est la base du fichier extension.vsixmanifest qui nécessitent de tous les packages VSIX. Pour plus d’informations sur ce fichier, consultez [une Extension de schéma 1.0 référence VSIX](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).  
  
2.  Dans le **Product Name** , entrez **élément de projet d’Action personnalisée**.  
  
3.  Dans le **auteur** , entrez **Contoso**.  
  
4.  Dans le **Description** , entrez **élément de projet SharePoint qui représente une action personnalisée**.  
  
5.  Sur le **actifs** , choisir le **nouveau** bouton.  
  
     Le **ajouter un nouveau composant** boîte de dialogue s’affiche.  
  
6.  Dans le **Type** , choisissez **Microsoft.VisualStudio.ItemTemplate**.  
  
    > [!NOTE]  
    >  Cette valeur correspond à la `ItemTemplate` élément dans le fichier extension.vsixmanifest. Cet élément identifie le sous-dossier du package VSIX qui contient le modèle d’élément de projet. Pour plus d’informations, consultez [ItemTemplate, élément (schéma VSX)](http://msdn.microsoft.com/en-us/1d489e54-c1c5-4f96-a510-6c2640867ff0).  
  
7.  Dans le **Source** , choisissez **un projet dans la solution actuelle**.  
  
8.  Dans le **projet** , choisissez **ItemTemplate**, puis choisissez le **OK** bouton.  
  
9. Dans le **actifs** , choisir le **nouveau** bouton Nouveau.  
  
     Le **ajouter un nouveau composant** boîte de dialogue s’affiche.  
  
10. Dans le **Type** , choisissez **Microsoft.VisualStudio.MefComponent**.  
  
    > [!NOTE]  
    >  Cette valeur correspond à la `MefComponent` élément dans le fichier extension.vsixmanifest. Cet élément spécifie le nom d’un assembly d’extension dans le package VSIX. Pour plus d’informations, consultez [MEFComponent, élément (schéma VSX)](http://msdn.microsoft.com/en-us/8a813141-8b73-44c9-b80b-ca85bbac9551).  
  
11. Dans le **Source** , choisissez **un projet dans la solution actuelle**.  
  
12. Dans le **projet** , choisissez **ProjectItemDefinition**.  
  
13. Sélectionnez le bouton **OK** .  
  
14. Dans la barre de menus, choisissez **générer**, **générer la Solution**, puis assurez-vous que le projet se compile sans erreur.  
  
15. Assurez-vous que le dossier de sortie de génération pour le projet ÉlémentProjetActionPersonnalisée contienne le fichier ÉlémentProjetActionPersonnalisée.VSIX.  
  
     Par défaut, le dossier de sortie est le... dossier \bin\debug sous le dossier qui contient le projet ÉlémentProjetActionPersonnalisée.  
  
## <a name="testing-the-project-item"></a>Test de l’élément de projet  
 Vous êtes maintenant prêt à tester l’élément de projet. Commencez à déboguer la solution CustomActionProjectItem dans l’instance expérimentale de Visual Studio. Ensuite, testez le **Action personnalisée** élément de projet dans un projet SharePoint dans l’instance expérimentale de Visual Studio. Enfin, générez et exécutez le projet SharePoint pour vérifier que l’action personnalisée fonctionne comme prévu.  
  
#### <a name="to-start-debugging-the-solution"></a>Pour démarrer le débogage de la solution  
  
1.  Redémarrez Visual Studio avec des informations d’identification d’administration et ouvrez la solution CustomActionProjectItem.  
  
2.  Ouvrez le fichier de code CustomAction et puis ajoutez un point d’arrêt à la première ligne de code dans le `InitializeType` (méthode).  
  
3.  Choisissez le **F5** touche pour démarrer le débogage.  
  
     Visual Studio installe l’extension %UserProfile%\AppData\Local\Microsoft\VisualStudio\10.0Exp\Extensions\Contoso\Custom Item\1.0 de projet d’Action et démarre une instance expérimentale de Visual Studio. Vous allez tester l’élément de projet dans cette instance de Visual Studio.  
  
#### <a name="to-test-the-project-item-in-visual-studio"></a>Pour tester l’élément de projet dans Visual Studio  
  
1.  Dans l’instance expérimentale de Visual Studio, dans la barre de menus, choisissez **fichier**, **nouveau**, **projet**.  
  
2.  Développez **Visual C#** ou **Visual Basic** (selon le langage qui prend en charge de votre modèle d’élément), développez **SharePoint**, puis choisissez le **2010**  nœud.  
  
3.  Dans la liste des modèles de projet, choisissez **projet SharePoint 2010**.  
  
4.  Dans le **nom** , entrez **TestActionPersonnalisée**, puis choisissez le **OK** bouton.  
  
5.  Dans le **Assistant Personnalisation de SharePoint**, entrez l’URL du site que vous souhaitez utiliser pour le débogage, puis choisissez le **Terminer** bouton.  
  
6.  Dans **l’Explorateur de solutions**, ouvrez le menu contextuel du nœud de projet, choisissez **ajouter**, puis choisissez **un nouvel élément**.  
  
7.  Dans le **ajouter un nouvel élément** boîte de dialogue, choisissez le **2010** nœud sous la **SharePoint** nœud.  
  
     Vérifiez que le **Action personnalisée** élément apparaît dans la liste des éléments de projet.  
  
8.  Choisissez le **Action personnalisée** d’élément, puis choisissez le **ajouter** bouton.  
  
     Visual Studio ajoute un élément nommé **CustomAction1** à votre projet et l’ouvre le fichier Elements.xml de fichiers dans l’éditeur.  
  
9. Vérifiez que le code dans l’autre instance de Visual Studio s’arrête au point d’arrêt défini précédemment dans le `InitializeType` (méthode).  
  
10. Choisissez le **F5** touche pour continuer à déboguer le projet.  
  
11. Dans l’instance expérimentale de Visual Studio, dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour le **CustomAction1** nœud, puis choisissez **mode concepteur d’actions personnalisées**.  
  
12. Vérifiez qu’une boîte de message s’affiche, puis choisissez le **OK** bouton.  
  
     Vous pouvez utiliser ce menu contextuel pour fournir des options supplémentaires ou des commandes pour les développeurs, comme l’affichage d’un concepteur pour l’action personnalisée.  
  
13. Dans la barre de menus, choisissez **vue**, **sortie**.  
  
     Le **sortie** fenêtre s’ouvre.  
  
14. Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour le **CustomAction1** d’élément, puis remplacez son nom par **MyCustomAction**.  
  
     Dans le **sortie** fenêtre, un message de confirmation s’affiche. Ce message est écrit par le <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemNameChanged> Gestionnaire d’événements que vous avez définie dans la `CustomActionProjectItemTypeProvider` classe. Vous pouvez gérer cet événement et autres événements d’élément de projet pour implémenter un comportement personnalisé lorsque le développeur modifie l’élément de projet.  
  
#### <a name="to-test-the-custom-action-in-sharepoint"></a>Pour tester l’action personnalisée dans SharePoint  
  
1.  Dans l’instance expérimentale de Visual Studio, ouvrez le fichier Elements.xml qui est un enfant de la **MyCustomAction** élément de projet.  
  
2.  Dans le fichier Elements.xml, apportez les modifications suivantes, puis enregistrez le fichier :  
  
    -   Dans le `CustomAction` élément, définissez la `Id` d’attribut à un GUID ou une autre chaîne unique comme le montre l’exemple suivant :  
  
        ```  
        Id="cd85f6a7-af2e-44ab-885a-0c795b52121a"  
        ```  
  
    -   Dans le `CustomAction` élément, définissez la `Title` attribut comme le montre l’exemple suivant :  
  
        ```  
        Title="SharePoint Developer Center"  
        ```  
  
    -   Dans le `CustomAction` élément, définissez la `Description` attribut comme le montre l’exemple suivant :  
  
        ```  
        Description="Opens the SharePoint Developer Center Web site."  
        ```  
  
    -   Dans le `UrlAction` élément, définissez la `Url` attribut comme le montre l’exemple suivant :  
  
        ```  
        Url="http://msdn.microsoft.com/sharepoint/default.aspx"  
        ```  
  
3.  Appuyez sur la touche F5.  
  
     L’action personnalisée est packagée et déployée sur le site SharePoint qui est spécifié dans le **URL du Site** propriété du projet. Le navigateur web s’ouvre à la page par défaut de ce site.  
  
    > [!NOTE]  
    >  Si le **le débogage de Script est désactivé** boîte de dialogue apparaît, choisissez le **Oui** pour continuer à déboguer le projet.  
  
4.  Sur le **Actions du Site** menu, choisissez **centre de développement SharePoint**, vérifiez que le navigateur s’ouvre le site Web http://msdn.microsoft.com/sharepoint/default.aspx, puis fermez le navigateur web.  
  
## <a name="cleaning-up-the-development-computer"></a>Nettoyage de l’ordinateur de développement  
 Une fois que vous avez terminé le test de l’élément de projet, supprimez le modèle d’élément de projet à partir de l’instance expérimentale de Visual Studio.  
  
#### <a name="to-clean-up-the-development-computer"></a>Pour nettoyer l’ordinateur de développement  
  
1.  Dans l’instance expérimentale de Visual Studio, dans la barre de menus, choisissez **outils**, **Extensions et mises à jour**.  
  
     La boîte de dialogue **Extensions et mises à jour** s’ouvre.  
  
2.  Dans la liste des extensions, choisissez **élément de projet d’Action personnalisée**, puis choisissez le **désinstallation** bouton.  
  
3.  Dans la boîte de dialogue qui s’affiche, choisissez le **Oui** pour confirmer que vous voulez désinstaller l’extension.  
  
4.  Choisissez le **redémarrer maintenant** bouton pour terminer la désinstallation.  
  
5.  Fermez l’instance expérimentale de Visual Studio et l’instance dans laquelle la solution ÉlémentProjetActionPersonnalisée est ouverte.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Après avoir terminé cette procédure pas à pas, vous pouvez ajouter un Assistant pour le modèle d’élément. Lorsqu’un utilisateur ajoute un élément de projet d’Action personnalisée à un projet SharePoint, l’Assistant collecte des informations sur l’action (par exemple, son emplacement et l’URL à atteindre lorsque l’action est choisie) et ajoute ces informations dans le fichier Elements.xml dans le nouvel élément de projet. Pour plus d’informations, consultez [procédure pas à pas : création d’un élément de projet d’Action personnalisé avec un modèle d’élément, partie 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Procédure pas à pas : Création d’un élément de projet d’Action personnalisé avec un modèle d’élément, partie 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)   
 [Définition des Types d’éléments de projet SharePoint personnalisé](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Création de modèles d’élément et les modèles de projet pour les éléments de projet SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)   
 [L’utilisation du Service de projet SharePoint](../sharepoint/using-the-sharepoint-project-service.md)   
 [Référence du schéma de modèle Visual Studio](/visualstudio/extensibility/visual-studio-template-schema-reference)   
 [Éditeur d’images pour les icônes](/cpp/windows/image-editor-for-icons)   
 [Création d’une icône ou une autre Image &#40;Éditeur d’images pour les icônes&#41;](/cpp/windows/creating-an-icon-or-other-image-image-editor-for-icons)  
  
  