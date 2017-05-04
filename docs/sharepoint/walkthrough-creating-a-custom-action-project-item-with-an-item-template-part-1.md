---
title: "Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 1 | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "SharePoint project items, creating custom templates"
  - "SharePoint project items, defining your own types"
  - "project items [SharePoint development in Visual Studio], defining your own types"
  - "SharePoint development in Visual Studio, defining new project item types"
ms.assetid: 41ed9c1c-4239-4d80-934b-975fde744288
caps.latest.revision: 152
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 151
---
# Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 1
  Etendez le système de projet SharePoint dans Visual Studio en créant vos propres types d'élément de projet.  Au cours de cette procédure, vous aurez l'occasion de créer un élément de projet prévu pour être inséré dans un projet SharePoint dans le but de créer une action personnalisée sur un site SharePoint.  L'action personnalisée ajoute un élément de menu au menu **Actions du site** du site SharePoint.  
  
 Cette procédure pas à pas présente les tâches suivantes :  
  
-   Création d'une extension Visual Studio qui définit un nouveau type d'élément de projet SharePoint pour une action personnalisée.  Le nouveau type d'élément de projet implémente plusieurs fonctionnalités personnalisées :  
  
    -   Menu contextuel très pratique pour commencer à définir des tâches supplémentaires ayant trait à l'élément de projet \(affichage d'un concepteur pour l'action personnalisée dans Visual Studio, par exemple\).  
  
    -   Code exécuté lorsqu'un développeur modifie certaines propriétés de l'élément de projet et le projet dans lequel il figure.  
  
    -   Une icône personnalisée qui s'affiche en regard de l'élément de projet dans l'**Explorateur de solutions**.  
  
-   Création d'un modèle d'élément Visual Studio pour l'élément de projet.  
  
-   Génération d'un package VSIX \(Visual Studio Extension\) pour déployer le modèle d'élément de projet et l'assembly d'extension.  
  
-   Débogage et test de l'élément de projet.  
  
 Il s'agit d'une procédure pas à pas autonome.  Après avoir exécuté cette procédure pas à pas, vous pouvez améliorer l'élément de projet en ajoutant un Assistant au modèle d'élément.  Pour plus d'informations, consultez [Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md).  
  
> [!NOTE]  
>  Téléchargez un exemple qui contient les projets terminés, du code et d'autres fichiers pour cette procédure pas à pas depuis l'emplacement suivant :  [http:\/\/go.microsoft.com\/fwlink\/?LinkId\=191369](http://go.microsoft.com/fwlink/?LinkId=191369).  
  
## Composants requis  
 Vous avez besoin des composants suivants sur l'ordinateur de développement pour terminer cette procédure pas à pas :  
  
-   Éditions de Microsoft Windows, SharePoint et Visual Studio prises en charge.  Pour plus d'informations, consultez [Configuration requise pour développer des solutions SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)].  Cette procédure pas à pas utilise le modèle **Projet VSIX** du Kit de développement logiciel \(SDK\) pour créer un package VSIX afin de déployer l'élément de projet.  Pour plus d'informations, consultez [Extending the SharePoint Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
 Une connaissance des concepts suivants est utile, mais pas obligatoire, pour effectuer cette procédure pas à pas :  
  
-   Actions personnalisées dans SharePoint.  Pour plus d'informations, consultez [Actions personnalisées](http://go.microsoft.com/fwlink/?LinkId=177800).  
  
-   Modèles d'élément dans Visual Studio.  Pour plus d'informations, consultez [Création de modèles de projets et d'éléments personnalisés dans Visual Studio](../ide/creating-project-and-item-templates.md).  
  
## Création du projet  
 Pour exécuter cette procédure pas à pas, vous devez créer trois projets :  
  
-   Un projet VSIX.  Ce projet crée le package VSIX permettant de déployer l'élément de projet SharePoint.  
  
-   Un projet de modèle d'élément.  Ce projet crée un modèle d'élément qui permet d'ajouter l'élément de projet SharePoint à un projet SharePoint.  
  
-   Un projet de bibliothèque de classes.  Ce projet implémente une extension Visual Studio qui définit le comportement de l'élément de projet SharePoint.  
  
 Démarrez la procédure pas à pas en créant les projets.  
  
#### Pour créer le projet VSIX  
  
1.  Démarrez [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Dans la barre de menus, sélectionnez **Fichier**, **Nouveau**, **Projet**.  
  
3.  Dans la liste située en haut de la boîte de dialogue **Nouveau projet**, vérifiez que **.NET Framework 4.5** est sélectionné.  
  
4.  Dans la boîte de dialogue **Nouveau projet**, développez les nœuds **Visual C\#** ou **Visual Basic**, puis sélectionnez le nœud **Extensibilité**.  
  
    > [!NOTE]  
    >  Le nœud **Extensibilité** est disponible uniquement si vous installez le Kit de développement logiciel de Visual Studio 2010.  Pour plus d'informations, consultez la section des composants requis plus haut dans cette rubrique.  
  
5.  Choisissez le modèle **VSIX Project**.  
  
6.  Dans la zone de texte **Nom**, entrez **CustomActionProjectItem**, puis cliquez sur le bouton **OK**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ajoute le projet **ÉlémentProjetActionPersonnalisée** à l'**Explorateur de solutions**.  
  
#### Pour créer le projet de modèle d'élément  
  
1.  Dans **l'Explorateur de solutions**, ouvrez le menu contextuel du nœud de votre solution, choisissez **Ajouter**, puis choisissez **Nouveau Projet**.  
  
    > [!NOTE]  
    >  Dans les projets Visual Basic, le nœud de la solution s'affiche dans l'**Explorateur de solutions** à condition d'avoir activé la case à cocher **Toujours afficher la solution** dans la [NIB: General, Projects and Solutions, Options Dialog Box](http://msdn.microsoft.com/fr-fr/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca).  
  
2.  Dans la liste située en haut de la boîte de dialogue **Nouveau projet**, vérifiez que **.NET Framework 4.5** est sélectionné.  
  
3.  Dans la boîte de dialogue **Nouveau projet**, développez les nœuds **Visual C\#** ou **Visual Basic**, puis sélectionnez le nœud **Extensibilité**.  
  
4.  Dans la liste de modèles de projet, choisissez **Modèle d'élément C\#** ou **Modèle d'élément Visual Basic**.  
  
5.  Dans la zone de texte **Nom**, entrez **ItemTemplate**, puis cliquez sur le bouton **OK**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ajoute le projet **ItemTemplate** à la solution.  
  
#### Pour créer le projet d'extension  
  
1.  Dans **l'Explorateur de solutions**, ouvrez le menu contextuel du nœud de votre solution, choisissez **Ajouter**, puis choisissez **Nouveau Projet**.  
  
2.  Dans la liste située en haut de la boîte de dialogue **Nouveau projet**, vérifiez que **.NET Framework 4.5** est sélectionné.  
  
3.  Dans la boîte de dialogue **Nouveau projet**, développez le nœud **Visual C\#** ou **Visual Basic**, choisissez le nœud **Windows**, puis sélectionnez le modèle de projet **Bibliothèque de classes**.  
  
4.  Dans la zone de texte **Nom**, entrez **ProjectItemDefinition**, puis cliquez sur le bouton **OK**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ajoute le projet **ProjectItemDefinition** à la solution et ouvre le fichier de code Class1 par défaut.  
  
5.  Supprimez le fichier de code Class1 du projet.  
  
## Configuration du projet d'extension  
 Avant d'écrire le code pour définir le type d'élément de projet SharePoint, vous devez ajouter des fichiers de code et des références d'assembly au projet d'extension.  
  
#### Pour configurer le projet  
  
1.  Dans **l'Explorateur de solutions**, ouvrez le menu contextuel du projet **ProjectItemDefinition**, choisissez **Ajouter**, puis **Nouvel élément**.  
  
2.  Dans la liste d'éléments de projet, sélectionnez sur **Fichier de code**.  
  
3.  Dans la zone **Nom**, entrez le nom **CustomAction** avec l'extension de nom de fichier appropriée, puis cliquez sur le bouton **Ajouter**.  
  
4.  Dans **l'Explorateur de solutions**, ouvrez le menu contextuel du projet **ProjectItemDefinition**, puis choisissez **Ajouter une référence**.  
  
5.  Dans la boîte de dialogue **Gestionnaire de référence – ProjectItemDefinition**, choisissez le nœud **Assemblys**, puis choisissez **Framework**.  
  
6.  Activez la case à cocher à côté de chacun des assemblys suivants :  
  
    -   System.ComponentModel.Composition  
  
    -   System.Windows.Forms  
  
7.  Sélectionnez le nœud **Extensions**, activez la case à cocher à côté de l'assembly de Microsoft.VisualStudio.Sharepoint, puis cliquez sur le bouton **OK**.  
  
## Définition du nouveau type d'élément de projet SharePoint  
 Créez une classe qui implémente l'interface <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> pour définir le comportement du nouveau type d'élément de projet.  Implémentez cette interface chaque fois que vous souhaitez définir un nouveau type d'élément de projet.  
  
#### Pour définir le nouveau type d'élément de projet SharePoint  
  
1.  Dans le projet ProjectItemDefinition, ouvrez le fichier de code CustomAction.  
  
2.  Remplacez le code de ce fichier par le code suivant.  
  
     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#1](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitem.customaction/cs/projectitemtypedefinition/customaction.cs#1)]
     [!code-vb[SPExtensibility.ProjectItem.CustomAction#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitem.customaction/vb/projectitemdefinition/customaction.vb#1)]  
  
## Création d'une icône pour l'élément de projet dans l'Explorateur de solutions  
 Lorsque vous créez un élément de projet SharePoint personnalisé, vous pouvez associer une image \(icône ou fichier bitmap\) à l'élément de projet.  Cette image s'affiche en regard de l'élément de projet dans l'**Explorateur de solutions**.  
  
 Dans la procédure suivante, vous aurez l'occasion de créer une icône pour l'élément de projet et d'incorporer l'icône dans l'assembly d'extension.  Cette icône est référencée par l'attribut <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemIconAttribute> de la classe `CustomActionProjectItemTypeProvider` que vous avez créée précédemment.  
  
#### Pour créer une icône personnalisée pour l'élément de projet  
  
1.  Dans **l'Explorateur de solutions**, ouvrez le menu contextuel du projet **ProjectItemDefinition**, choisissez **Ajouter**, et enfin **Nouvel élément...**.  
  
2.  Dans la liste d'éléments du projet, sélectionnez l'élément **Fichier d'icône**.  
  
    > [!NOTE]  
    >  Dans les projets Visual Basic, vous devez choisir le nœud **Général** pour afficher l'élément **Fichier d'icône**.  
  
3.  Dans la zone de texte **Nom**, entrez **CustomAction\_SolutionExplorer.ico**, puis cliquez sur le bouton **Ajouter**.  
  
     La nouvelle icône s'ouvre dans l'**Éditeur d'images**.  
  
4.  Modifiez la version 16x16 du fichier icône de manière à reconnaître son design, puis enregistrez le fichier icône.  
  
5.  Dans **l'Explorateur de solutions**, cliquez sur **CustomAction\_SolutionExplorer.ico**.  
  
6.  Dans la fenêtre **Propriétés**, choisissez la flèche à côté de la propriété **Action de génération**.  
  
7.  Dans la liste qui apparaît, choisissez **Ressource incorporée**.  
  
## Point de contrôle  
 À ce stade de la procédure, l'intégralité du code de l'élément de projet fait désormais partie du projet.  Générez le projet afin de vérifier qu'il est compilé sans erreur.  
  
#### Pour générer votre projet  
  
1.  Ouvrez le menu contextuel du projet **Propriétés** puis sélectionnez **Générer**.  
  
## Création d'un modèle d'élément Visual Studio  
 Pour donner à d'autres développeurs la possibilité d'utiliser votre élément de projet, vous devez créer un modèle de projet ou un modèle d'élément.  Les développeurs utilisent ces modèles dans Visual Studio pour créer une instance de votre élément de projet en élaborant un nouveau projet ou en ajoutant un élément à un projet existant.  Pour cette procédure pas à pas, utilisez le projet ItemTemplate pour configurer votre élément de projet.  
  
#### Pour créer le modèle d'élément  
  
1.  Supprimez le fichier de code Class1 du projet ItemTemplate.  
  
2.  Dans le projet ItemTemplate, ouvrez le fichier ItemTemplate.vstemplate.  
  
3.  Remplacez le contenu du fichier par le code XML ci\-dessous, puis enregistrez et fermez le fichier.  
  
    > [!NOTE]  
    >  Le code XML ci\-dessous correspond à un modèle d'élément Visual C\#.  Si vous créez un modèle d'élément Visual Basic, remplacez la valeur de l'élément `ProjectType` par `VisualBasic`.  
  
    ```  
  
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
  
     Ce fichier définit le contenu et le comportement du modèle d'élément.  Pour en savoir plus sur le contenu de ce fichier, consultez [Référence du schéma de modèle Visual Studio](../extensibility/visual-studio-template-schema-reference.md).  
  
4.  Dans **l'Explorateur de solutions**, ouvrez le menu contextuel du projet **ItemTemplate**, choisissez **Ajouter**, puis **Nouvel élément**.  
  
5.  Dans la boîte de dialogue **Ajouter un nouvel élément**, choisissez le modèle **Fichier texte**.  
  
6.  Dans la zone de texte **Nom**, entrez **CustomAction.spdata**, puis cliquez sur le bouton **Ajouter**.  
  
7.  Ajoutez le code XML suivant au fichier CustomAction.spdata, puis enregistrez et fermez le fichier.  
  
    ```  
  
    <ProjectItem Type="Contoso.CustomAction" DefaultFile="Elements.xml"   
     xmlns="http://schemas.microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel">  
      <Files>  
        <ProjectItemFile Source="Elements.xml" Target="$fileinputname$\" Type="ElementManifest" />  
      </Files>  
    </ProjectItem>  
    ```  
  
     Ce fichier contient des informations relatives aux fichiers contenus dans l'élément de projet.  La chaîne affectée à l'attribut `Type` de l'élément `ProjectItem` doit être identique à celle transmise au <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute> de la définition d'élément de projet \(classe `CustomActionProjectItemTypeProvider` que vous avez créée précédemment dans cette procédure\).  Pour plus d'informations sur le contenu des fichiers .spdata, consultez [SharePoint Project Item Schema Reference](../sharepoint/sharepoint-project-item-schema-reference.md).  
  
8.  Dans **l'Explorateur de solutions**, ouvrez le menu contextuel du projet **ItemTemplate**, choisissez **Ajouter**, puis **Nouvel élément**.  
  
9. Dans la boîte de dialogue **Ajouter un nouvel élément** sélectionnez le modèle **Fichier XML**.  
  
10. Dans la zone de texte **Nom**, entrez **Elements.xml**, puis cliquez sur le bouton **Ajouter**.  
  
11. Remplacez le contenu du fichier Elements.xml par le code XML suivant, puis enregistrez et fermez le fichier.  
  
    ```  
  
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
  
     Ce fichier définit une action personnalisée par défaut qui crée un élément de menu dans le menu **Actions du site** du site SharePoint.  Lorsqu'un utilisateur clique sur l'élément de menu, l'URL spécifiée dans l'élément `UrlAction` s'ouvre dans le navigateur web.  Pour plus d'informations sur les éléments XML que vous pouvez utiliser pour définir une action personnalisée, consultez [Définitions d'actions personnalisées](http://go.microsoft.com/fwlink/?LinkId=177801).  
  
12. Vous pouvez éventuellement ouvrir le fichier ItemTemplate.ico et le modifier de façon à ce que sa conception soit reconnaissable.  Cette icône s'affichera en regard de l'élément de projet dans la boîte de dialogue **Ajouter un nouvel élément**.  
  
13. Dans **l'Explorateur de solutions**, ouvrez le menu contextuel de votre projet **ItemTemplate** puis sélectionnez **Décharger le projet**.  
  
14. Ouvrez à nouveau le menu contextuel du projet de **ItemTemplate**, puis sélectionnez **Modifier ItemTemplate.csproj** ou **Modifier ItemTemplate.vbproj**.  
  
15. Localisez l'élément `VSTemplate` suivant dans le fichier projet.  
  
    ```  
    <VSTemplate Include="ItemTemplate.vstemplate">  
    ```  
  
16. Remplacez cet élément `VSTemplate` par le code XML ci\-dessous, puis enregistrez et fermez le fichier.  
  
    ```  
    <VSTemplate Include="ItemTemplate.vstemplate">  
      <OutputSubPath>SharePoint\SharePoint14</OutputSubPath>  
    </VSTemplate>  
    ```  
  
     L'élément `OutputSubPath` spécifie des dossiers supplémentaires dans le chemin d'accès où le modèle d'élément est créé lorsque vous générez le projet.  Le fichier spécifié ici s'assure que le modèle d'élément sera disponible uniquement lorsque les clients ouvrent la boite de dialogue **Ajouter un nouvel élément**, développe le noeud **SharePoint**, puis choisit **2010**.  
  
17. Dans **l'Explorateur de solutions**, ouvrez le menu contextuel de votre projet **ItemTemplate** puis sélectionnez **Recharger le projet**.  
  
## Création d'un package VSIX pour déployer l'élément de projet  
 Pour déployer l'extension, utilisez le projet VSIX inclus dans votre solution pour créer un package VSIX.  En premier lieu, configurez le package VSIX en modifiant le fichier source.extension.vsixmanifest qui est inclus dans le projet VSIX.  Ensuite, créez le package VSIX en générant la solution.  
  
#### Pour configurer et créer le package VSIX  
  
1.  Dans **l'Explorateur de solutions**, ouvrez le menu contextuel du fichier **source.extension.vsixmanifest** dans le projet CustomActionProjectItem, puis cliquez sur **Ouvrir**.  
  
     Visual Studio ouvre le fichier dans l'éditeur de manifeste.  Le fichier source.extension.vsixmanifest est la base du fichier extension.vsixmanifest requis par tous les packages VSIX.  Pour plus d'informations sur ce fichier, consultez [Référence de schéma d'extensions VSIX](http://msdn.microsoft.com/fr-fr/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).  
  
2.  Dans la zone **Nom du produit**, tapez **Élément de projet d'action personnalisée**.  
  
3.  Dans la zone **Auteur**, tapez **Contoso**.  
  
4.  Dans la zone **Description**, tapez **Un élément de projet SharePoint qui représente une action personnalisée**.  
  
5.  Dans l'onglet **Atouts**, choisissez le bouton **Nouveau**.  
  
     La boîte de dialogue **Ajouter un nouveau atout** s'affiche.  
  
6.  Dans la liste **Type**, choisissez **Microsoft.VisualStudio.ItemTemplate**.  
  
    > [!NOTE]  
    >  Cette valeur correspond à l'élément `ItemTemplate` dans le fichier extension.vsixmanifest.  Cet élément identifie le sous\-dossier du package VSIX qui contient le modèle d'élément de projet.  Pour plus d'informations, consultez [NIB: ItemTemplate Element \(VSX Schema\)](http://msdn.microsoft.com/fr-fr/1d489e54-c1c5-4f96-a510-6c2640867ff0).  
  
7.  Dans la liste **Source**, choisissez **Un projet dans la solution actuelle**.  
  
8.  Dans la liste **Projet**, choisissez **ItemTemplate**, puis cliquez sur le bouton **OK**.  
  
9. Dans l'onglet **Atouts**, cliquez à nouveau sur le bouton **Nouveau**.  
  
     La boîte de dialogue **Ajouter un nouveau atout** s'affiche.  
  
10. Dans la liste **Type**, choisissez **Microsoft.VisualStudio.MefComponent**.  
  
    > [!NOTE]  
    >  Cette valeur correspond à l'élément `MefComponent` dans le fichier extension.vsixmanifest.  Cet élément spécifie le nom d'un assembly d'extension dans le package VSIX.  Pour plus d'informations, consultez [NIB: MEFComponent Element \(VSX Schema\)](http://msdn.microsoft.com/fr-fr/8a813141-8b73-44c9-b80b-ca85bbac9551).  
  
11. Dans la liste **Source**, choisissez **Un projet dans la solution actuelle**.  
  
12. Dans la liste **Projet**, choisissez **ProjectItemDefinition**.  
  
13. Cliquez sur le bouton **OK**.  
  
14. Dans la barre de menus, sélectionnez **Générer**, **Générer la solution**, puis vérifiez que les projet se compilent sans erreurs.  
  
15. Assurez\-vous que le dossier de sortie de la génération pour le projet CustomActionProjectItem contient le fichier CustomActionProjectItem.vsix.  
  
     Par défaut, le dossier de sortie de la génération est le dossier ..\\bin\\Debug dans le dossier qui contient le projet CustomActionProjectItem.  
  
## Test de l'élément de projet  
 Vous êtes maintenant prêt à tester l'élément de projet.  Commencez à déboguer la solution CustomActionProjectItem dans l'instance expérimentale de Visual Studio.  Testez ensuite l'élément de projet **Action personnalisée** dans un projet SharePoint de l'instance expérimentale de Visual Studio.  Enfin, générez et exécutez le projet SharePoint pour vous assurer que l'action personnalisée fonctionne comme prévu.  
  
#### Pour commencer à déboguer la solution  
  
1.  Redémarrez Visual Studio avec les droits d'administrateur puis ouvrez la solution CustomActionProjectItem.  
  
2.  Ouvrez le fichier de code CustomAction puis ajoutez un point d'arrêt au niveau de la première ligne de code dans la méthode `InitializeType`.  
  
3.  Appuyez sur la touche **F5** pour démarrer le débogage.  
  
     Visual Studio installe l'extension sous %UserProfile%\\AppData\\Local\\Microsoft\\VisualStudio\\10.0Exp\\Extensions\\Contoso\\Élément de projet d'action personnalisée\\1.0 et démarre une instance expérimentale de Visual Studio.  Vous testerez l'élément de projet dans cette instance de Visual Studio.  
  
#### Pour tester l'élément de projet dans Visual Studio  
  
1.  Dans l'instance expérimentale de Visual Studio, dans la barre de menu, sélectionnez **Fichier**, **Nouveau**, puis cliquez sur **Projet**.  
  
2.  Développez **Visual C\#** ou **Visual Basic** \(selon le langage pris en charge par votre modèle d'élément\), développez **SharePoint**, puis cliquez sur **2010**.  
  
3.  Dans la liste des modèles de projet, cliquez sur **SharePoint 2010**.  
  
4.  Dans la zone de texte **Nom**, entrez **CustomActionTest**, puis choisissez le bouton **OK**.  
  
5.  Dans **l'Assistant Personnalisation de SharePoint**, saisissez l'URL du site que vous souhaitez utiliser pour le débogage, puis cliquez sur **Terminer**.  
  
6.  Dans **l'Explorateur de solutions**, ouvrez le menu contextuel du projet, cliquez sur **Ajouter**, puis sur **Nouvel élément**.  
  
7.  Dans la boîte de dialogue **Ajouter un nouvel élément**, cliquez sur **2010** sous **SharePoint**.  
  
     Vérifiez que l'élément **Action personnalisée** s'affiche dans la liste des éléments de projet.  
  
8.  Sélectionnez l'élément **Action personnalisée**, puis choisissez le bouton **Ajouter**.  
  
     Visual Studio ajoute un nouvel élément nommé **CustomAction1** à votre projet et ouvre le fichier Elements.xml dans l'éditeur.  
  
9. Assurez\-vous que le code dans l'autre instance de Visual Studio s'arrête au niveau du point d'arrêt que vous avez défini précédemment dans la méthode `InitializeType`.  
  
10. Sélectionnez la clé **F5** pour continuer à déboguer le projet.  
  
11. Dans l'instance expérimentale de Visual Studio, dans **l'Explorateur de solutions**, ouvrez le menu contextuel pour la **CustomAction1**, puis cliquez sur **Afficher le Concepteur d'actions personnalisées**.  
  
12. Assurez\-vous qu'une boîte de message apparaît, puis cliquez sur **OK**.  
  
     Vous pouvez utiliser ce menu contextuel pour proposer des options ou des commandes supplémentaires aux développeurs \(en leur permettant, par exemple, d'afficher un concepteur pour l'action personnalisée\).  
  
13. Dans la barre de menu, sélectionnez **Afficher**, **Sortie**.  
  
     La fenêtre **Sortie** s'ouvre.  
  
14. Dans **Explorateur de solutions**, ouvrez le menu contextuel de l'élément **CustomAction1**, puis remplacez son nom par **MyCustomAction**.  
  
     Dans la fenêtre **Sortie**, un message de confirmation apparaît.  Ce message est écrit par le gestionnaire d'événements <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemNameChanged> que vous avez défini dans la classe `CustomActionProjectItemTypeProvider`.  Vous pouvez gérer cet événement et d'autres événements d'élément de projet dans le but de prévoir un comportement personnalisé lorsque le développeur modifie l'élément de projet.  
  
#### Pour tester l'action personnalisée dans SharePoint  
  
1.  Dans l'instance expérimentale de Visual Studio, ouvrez le fichier Elements.xml qui est un enfant de l'élément de projet **MyCustomAction**.  
  
2.  Dans le fichier Elements.xml, apportez les modifications suivantes, puis enregistrez le fichier :  
  
    -   Dans l'élément `CustomAction`, définissez l'attribut `Id` à un GUID ou une autre chaîne unique comme l'illustre l'exemple suivant :  
  
        ```  
        Id="cd85f6a7-af2e-44ab-885a-0c795b52121a"  
        ```  
  
    -   Dans l'élément `CustomAction`, définissez l'attribut `Title` comme montré dans l'exemple ci\-dessous.  
  
        ```  
        Title="SharePoint Developer Center"  
        ```  
  
    -   Dans l'élément `CustomAction`, définissez l'attribut `Description` comme montré dans l'exemple ci\-dessous.  
  
        ```  
        Description="Opens the SharePoint Developer Center Web site."  
        ```  
  
    -   Dans l'élément `UrlAction`, définissez l'attribut `Url` comme montré dans l'exemple ci\-dessous.  
  
        ```  
        Url="http://msdn.microsoft.com/sharepoint/default.aspx"  
        ```  
  
3.  Sélectionnez la touche F5.  
  
     L'action personnalisée est empaquetée et déployée sur le site SharePoint spécifié dans la propriété **URL de site** du projet.  Le navigateur Web s'ouvre à la page par défaut de ce site.  
  
    > [!NOTE]  
    >  Si la boîte de dialogue **Le débogage de script est désactivé** s'affiche, cliquez sur **Oui** pour continuer à déboguer le projet.  
  
4.  Dans le menu **Actions du site**, choisissez **Centre de développement SharePoint**, vérifiez que le navigateur ouvre le site Web http:\/\/msdn.microsoft.com\/sharepoint\/default.aspx, puis fermez le navigateur Web.  
  
## Nettoyage de l'ordinateur de développement  
 Une fois le test de l'élément de projet terminé, supprimez le modèle d'élément de projet de l'instance expérimentale de Visual Studio.  
  
#### Pour nettoyer l'ordinateur de développement  
  
1.  Dans l'instance expérimentale de Visual Studio, dans la barre de menu, cliquez sur **Outils**, **Extensions et mises à jour**.  
  
     La boîte de dialogue **Extensions et mises à jour** s'ouvre.  
  
2.  Dans la liste d'extensions, cliquez sur **Élément de projet d'action personnalisée**, puis sur **Désinstaller**.  
  
3.  Dans la boîte de dialogue qui s'affiche, cliquez sur **Oui** pour confirmer que vous voulez désinstaller l'extension.  
  
4.  Cliquez sur le bouton **Redémarrer maintenant** pour terminer l'installation.  
  
5.  Fermez les deux instances de Visual Studio \(l'instance expérimentale et l'instance de Visual Studio dans laquelle la solution CustomActionProjectItem est ouverte\).  
  
## Étapes suivantes  
 Après avoir terminé cette procédure pas à pas, vous pouvez ajouter un Assistant au modèle d'élément.  Lorsqu'un utilisateur ajoute un élément de projet Action personnalisée à un projet SharePoint, l'Assistant collecte les informations relatives à l'action \(telles que son emplacement et l'URL à atteindre lorsqu'elle fait l'objet d'un clic\) et les ajoute au fichier Elements.xml dans le nouvel élément de projet.  Pour plus d'informations, consultez [Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md).  
  
## Voir aussi  
 [Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)   
 [Defining Custom SharePoint Project Item Types](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)   
 [Using the SharePoint Project Service](../sharepoint/using-the-sharepoint-project-service.md)   
 [Référence du schéma de modèle Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Image Editor for Icons](/visual-cpp/windows/image-editor-for-icons)   
 [Creating an Icon or Other Image &#40;Image Editor for Icons&#41;](/visual-cpp/windows/creating-an-icon-or-other-image-image-editor-for-icons)  
  
  