---
title: "Proc&#233;dure pas &#224; pas&#160;: cr&#233;ation d&#39;un &#233;l&#233;ment de projet Colonne de site avec un mod&#232;le de projet, premi&#232;re&#160;partie"
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
  - "éléments de projet SharePoint, définition de vos propres types"
  - "éléments de projet (développement SharePoint dans Visual Studio), définition de vos propres types"
  - "projets SharePoint, création de modèles personnalisés"
  - "développement SharePoint dans Visual Studio, définition de nouveaux types d’éléments de projet"
ms.assetid: b53d48d7-cbf2-45c2-9537-06a6819be397
caps.latest.revision: 60
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 59
---
# Proc&#233;dure pas &#224; pas&#160;: cr&#233;ation d&#39;un &#233;l&#233;ment de projet Colonne de site avec un mod&#232;le de projet, premi&#232;re&#160;partie
  Les projets SharePoint sont des conteneurs pour un ou plusieurs éléments de projet SharePoint.  Étendez le système de projet SharePoint dans Visual Studio en créant vos propres types d'éléments de projet SharePoint, puis en les associant à un modèle de projet.  Dans cette procédure pas à pas, vous allez définir un type d'élément de projet pour créer une colonne de site, puis vous créerez un modèle de projet qui pourra être utilisé pour créer un projet contenant un élément de projet de la colonne de site.  
  
 Cette procédure pas à pas présente les tâches suivantes :  
  
-   Création d'une extension Visual Studio qui définit un nouveau type d'élément de projet SharePoint pour une colonne de site.  Le type d'élément de projet comprend une propriété personnalisée simple qui s'affiche dans la fenêtre **Propriétés**.  
  
-   Création d'un modèle de projet pour l'élément de projet dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
-   Génération d'un package VSIX \([!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Extension\) pour déployer le modèle de projet et l'assembly d'extension.  
  
-   Débogage et test de l'élément de projet.  
  
 Il s'agit d'une procédure pas à pas autonome.  Après avoir exécuté cette procédure pas à pas, vous pouvez améliorer l'élément de projet en ajoutant un Assistant au modèle de projet.  Pour plus d'informations, consultez [Procédure pas à pas : création d'un élément de projet Colonne de site avec un modèle de projet, deuxième partie](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md).  
  
> [!NOTE]  
>  Téléchargez un exemple qui contient les projets terminés, du code et d'autres fichiers pour cette procédure pas à pas depuis l'emplacement suivant : [http:\/\/go.microsoft.com\/fwlink\/?LinkId\=191369](http://go.microsoft.com/fwlink/?LinkId=191369).  
  
## Composants requis  
 Vous avez besoin des composants suivants sur l'ordinateur de développement pour terminer cette procédure pas à pas :  
  
-   Éditions de Microsoft Windows, SharePoint et [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] prises en charge.  Pour plus d'informations, consultez [Configuration requise pour développer des solutions SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)].  Cette procédure pas à pas utilise le modèle **Projet VSIX** du Kit de développement logiciel \(SDK\) pour créer un package VSIX afin de déployer l'élément de projet.  Pour plus d'informations, consultez [Extending the SharePoint Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
 Une connaissance du concept suivant est utile, mais pas obligatoire, pour effectuer cette procédure pas à pas :  
  
-   Colonnes de site dans SharePoint.  Pour plus d’informations, consultez [Colonnes](http://go.microsoft.com/fwlink/?LinkId=183547).  
  
-   Modèles de projet dans Visual Studio.  Pour plus d'informations, consultez [Création de modèles de projets et d'éléments personnalisés dans Visual Studio](../ide/creating-project-and-item-templates.md).  
  
## Création du projet  
 Pour exécuter cette procédure pas à pas, vous devez créer trois projets :  
  
-   Un projet VSIX.  Ce projet crée le package VSIX pour déployer l'élément de projet de la colonne de site et le modèle de projet.  
  
-   Un projet de modèle de projet.  Ce projet crée un modèle de projet pouvant être utilisé pour créer un projet SharePoint qui contient l'élément de projet de la colonne de site.  
  
-   Un projet de bibliothèque de classes.  Ce projet implémente une extension Visual Studio qui définit le comportement de l'élément de projet de la colonne de site.  
  
 Démarrez la procédure pas à pas en créant les projets.  
  
#### Pour créer le projet VSIX  
  
1.  Démarrez [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Dans la barre de menus, sélectionnez **Fichier**, **Nouveau**, **Projet**.  
  
3.  En haut de la boîte de dialogue **Nouveau projet**, vérifiez que **.NET Framework 4.5** est sélectionné dans la liste des versions du .NET Framework.  
  
4.  Développez les nœuds **Visual Basic** ou **Visual C\#**, puis choisissez le nœud **Extensibilité**.  
  
    > [!NOTE]  
    >  Le nœud **Extensibilité** est disponible uniquement si vous installez le Kit de développement logiciel de Visual Studio.  Pour plus d'informations, consultez la section des composants requis plus haut dans cette rubrique.  
  
5.  Dans la liste de modèles de projets, choisissez **Projet VSIX**.  
  
6.  Dans la zone de texte **Nom**, entrez **SiteColumnProjectItem**, puis choisissez le bouton **OK**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ajoute le projet **SiteColumnProjectItem** à l'**Explorateur de solutions**.  
  
#### Pour créer le projet de modèle de projet  
  
1.  Dans **l'Explorateur de solutions**, ouvrez le menu contextuel du nœud de votre solution, choisissez **Ajouter**, puis choisissez **Nouveau Projet**.  
  
    > [!NOTE]  
    >  Dans les projets Visual Basic, le nœud de la solution s'affiche dans l'**Explorateur de solutions** à condition d'avoir activé la case à cocher **Toujours afficher la solution** dans la [NIB: General, Projects and Solutions, Options Dialog Box](http://msdn.microsoft.com/fr-fr/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca).  
  
2.  En haut de la boîte de dialogue **Nouveau projet**, vérifiez que **.NET Framework 4.5** est sélectionné dans la liste des versions du .NET Framework.  
  
3.  Développez les nœuds **Visual C\#** ou **Visual Basic**, puis choisissez le nœud **Extensibilité**.  
  
4.  Dans la liste des modèles de projet, sélectionnez les modèles **Modèle de projet C\#** ou **Modèle de projet Visual Basic**.  
  
5.  Dans la zone de texte **Nom**, entrez **SiteColumnProjectTemplate**, puis choisissez le bouton **OK**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ajoute le projet **SiteColumnProjectTemplate** à la solution.  
  
6.  Supprimez le fichier de code Class1 du projet.  
  
7.  Si vous avez créé un projet Visual Basic, supprimez également les fichiers suivants du projet :  
  
    -   MyApplication.Designer.vb  
  
    -   MyApplication.myapp  
  
    -   Resources.Designer.vb  
  
    -   Resources.resx  
  
    -   Settings.Designer.vb  
  
    -   Settings.settings  
  
#### Pour créer le projet d'extension  
  
1.  Dans **l'Explorateur de solutions**, ouvrez le menu contextuel du nœud de votre solution, choisissez **Ajouter**, puis choisissez **Nouveau Projet**.  
  
2.  En haut de la boîte de dialogue **Nouveau projet**, vérifiez que **.NET Framework 4.5** est sélectionné dans la liste des versions du .NET Framework.  
  
3.  Développez les nœuds **Visual C\#** ou **Visual Basic**, choisissez le nœud **Windows**, puis choisissez le modèle **Bibliothèque de classes**.  
  
4.  Dans la zone de texte **Nom**, entrez **ProjectItemTypeDefinition**, puis choisissez le bouton **OK**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ajoute le projet **ProjectItemTypeDefinition** à la solution et ouvre le fichier de code Class1 par défaut.  
  
5.  Supprimez le fichier de code Class1 du projet.  
  
## Configuration du projet d'extension  
 Ajoutez des fichiers de code et des références d'assembly pour configurer le projet d'extension.  
  
#### Pour configurer le projet  
  
1.  Dans le projet de ProjectItemTypeDefinition, ajoutez un nouveau fichier de code appelé **SiteColumnProjectItemTypeProvider**.  
  
2.  Dans la barre de menus, choisissez **Projet**, **Ajouter une référence**.  
  
3.  Dans la boîte de dialogue **Gestionnaire de références \- ProjectItemTypeDefinition**, développez le nœud **Assemblys**, choisissez le nœud **Framework**, puis cochez la case System.ComponentModel.Composition.  
  
4.  Sélectionnez le nœud **Extensions**, activez la case à cocher à côté de l'assembly Microsoft.VisualStudio.SharePoint, puis cliquez sur le bouton **OK**.  
  
## Définition du nouveau type d'élément de projet SharePoint  
 Créez une classe qui implémente l'interface <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> pour définir le comportement du nouveau type d'élément de projet.  Implémentez cette interface chaque fois que vous souhaitez définir un nouveau type d'élément de projet.  
  
#### Pour définir le nouveau type d'élément de projet SharePoint  
  
1.  Dans le fichier de code de **SiteColumnProjectItemTypeProvider**, remplacez le code par défaut par le code suivant, puis enregistrez le fichier.  
  
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#1](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/cs/projectitemtypedefinition/sitecolumnprojectitemtypeprovider.cs#1)]
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/vb/projectitemtypedefinition/sitecolumnprojectitemtypeprovider.vb#1)]  
  
## Création d'un modèle de projet Visual Studio  
 En créant un modèle de projet, vous permettez à d'autres développeurs de créer des projets SharePoint qui contiennent des éléments de projet qui sont des colonnes de site.  Un modèle de projet SharePoint se compose de fichiers requis pour tous les projets dans Visual Studio, tels que les fichiers .csproj ou .vbproj et .vstemplate, et de fichiers spécifiques aux projets SharePoint.  Pour plus d'informations, consultez [Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
 Dans cette procédure, vous créez un projet SharePoint vide pour générer des fichiers spécifiques aux projets SharePoint.  Vous ajoutez ensuite ces fichiers au projet SiteColumnProjectTemplate pour qu'ils soient inclus dans le modèle généré à partir de ce projet.  Configurez également le fichier projet SiteColumnProjectTemplate pour spécifier l'emplacement où le modèle de projet s'affiche dans la boîte de dialogue **Ajouter un nouveau projet**.  
  
#### Pour créer les fichiers pour le modèle de projet  
  
1.  Démarrez une deuxième instance de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] avec des privilèges administrateur.  
  
2.  Créez un projet SharePoint 2010 vide nommé **BaseSharePointProject**.  
  
    > [!IMPORTANT]  
    >  Ne sélectionnez pas l'option **Déployer en tant que solution de batterie** dans l' **Assistant de Personnalisation SharePoint**.  
  
3.  Ajoutez un élément vide au projet, puis nommez l'élément **Field1**.  
  
4.  Enregistrez le projet, puis fermez la deuxième instance de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
5.  Dans l'instance de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] avec la solution SiteColumnProjectItem ouverte, dans **Explorateur de solutions**, ouvrez le menu contextuel du nœud de projet **SiteColumnProjectTemplate**, sélectionnez **Ajouter**, puis choisissez **Élément existant**.  
  
6.  Dans la boîte de dialogue **Ajouter un élément existant**, cliquez sur la liste déroulante des extensions de fichier et sélectionnez **Tous les fichiers \(\*.\*\)**.  
  
7.  Dans le répertoire qui contient le projet BaseSharePointProject, sélectionnez le fichier key.snk, puis choisissez le bouton **Ajouter**.  
  
    > [!NOTE]  
    >  Dans cette procédure pas à pas, le modèle de projet que vous créez utilise le même fichier key.snk pour signer chaque projet créé à l'aide du modèle.  Pour savoir comment développer cet exemple pour créer un nouveau fichier key.snk pour chaque instance de projet, consultez [Procédure pas à pas : création d'un élément de projet Colonne de site avec un modèle de projet, deuxième partie](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md).  
  
8.  Répétez les étapes 5 à 8 pour ajouter les fichiers suivants des sous\-dossiers spécifiés dans le dossier BaseSharePointProject :  
  
    -   \\Field1\\Elements.xml  
  
    -   \\Field1\\SharePointProjectItem.spdata  
  
    -   \\Features\\Feature1\\Feature1.feature  
  
    -   \\Features\\Feature1\\Feature1.Template.xml  
  
    -   \\Package\\Package.package  
  
    -   \\Package\\Package.Template.xml  
  
     Ajoutez ces fichiers directement dans le projet SiteColumnProjectTemplate ; ne recréez pas les sous\-dossiers Field1, Features ou Package dans le projet.  Pour plus d'informations sur ces fichiers, consultez [Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
#### Pour configurer la manière dont les développeurs découvrent le modèle de projet dans la boîte de dialogue Ajouter un nouveau projet  
  
1.  Dans **Explorateur de solutions**, ouvrez le menu contextuel du nœud de projet **SiteColumnProjectTemplate**, et choisissez **Décharger projet**.  Si vous êtes invité à enregistrer vos modifications dans un des fichiers, cliquez sur **Oui**.  
  
2.  Ouvrez le menu contextuel du nœud **SiteColumnProjectTemplate**, puis cliquez sur **Modifier SiteColumnProjectTemplate.csproj** ou **Modifier SiteColumnProjectTemplate.vbproj**.  
  
3.  Localisez l'élément `VSTemplate` suivant dans le fichier projet.  
  
    ```  
    <VSTemplate Include="SiteColumnProjectTemplate.vstemplate">  
    ```  
  
4.  Remplacez cet élément par le code XML suivant :  
  
    ```  
    <VSTemplate Include="SiteColumnProjectTemplate.vstemplate">  
      <OutputSubPath>SharePoint\SharePoint14</OutputSubPath>  
    </VSTemplate>  
    ```  
  
     L'élément `OutputSubPath` spécifie des dossiers supplémentaires dans le chemin d'accès où le modèle de projet est créé lorsque vous générez le projet.  Les fichiers spécifiés ici garantissent que le modèle de projet sera disponible quand les utilisateurs utiliseront la boîte de dialogue **Nouveau Projet**, développeront le nœud **SharePoint** et choisiront le nœud **2010**.  
  
5.  Enregistrez et fermez le fichier.  
  
6.  Dans l' **Explorateur de solutions**, ouvrez le menu contextuel du projet **SiteColumnProjectTemplate** et choisissez **Recharger le projet**.  
  
## Modification des fichiers du modèle de projet  
 Modifiez les fichiers suivants dans le projet SiteColumnProjectTemplate pour définir le comportement du modèle de projet :  
  
-   AssemblyInfo.cs ou AssemblyInfo.vb  
  
-   Elements.xml  
  
-   SharePointProjectItem.spdata  
  
-   Feature1.feature  
  
-   Package.package  
  
-   SiteColumnProjectTemplate.vstemplate  
  
-   ProjectTemplate.csproj ou ProjectTemplate.vbproj  
  
 Dans les procédures suivantes, vous allez ajouter à certains de ces fichiers des paramètres remplaçables.  Un paramètre remplaçable est un jeton qui commence et se termine par le signe dollar \($\).  Lorsqu'un utilisateur utilise ce modèle de projet pour créer un projet, Visual Studio remplace automatiquement ces paramètres dans le nouveau projet par des valeurs spécifiques.  Pour plus d'informations, consultez [Paramètres remplaçables](../sharepoint/replaceable-parameters.md).  
  
#### Pour modifier le fichier AssemblyInfo.cs ou AssemblyInfo.vb  
  
1.  Dans le projet SiteColumnProjectTemplate, ouvrez le fichier AssemblyInfo.cs ou AssemblyInfo.vb, puis ajoutez l'instruction suivante à son début :  
  
    ```vb  
    Imports System.Security  
    ```  
  
    ```csharp  
    using System.Security;  
    ```  
  
     Lorsque la propriété **Sandboxed Solution** d'un projet SharePoint a la valeur **True**, Visual Studio ajoute l'attribut <xref:System.Security.AllowPartiallyTrustedCallersAttribute> au fichier de code AssemblyInfo.  Toutefois, le fichier de code AssemblyInfo dans le modèle de projet n'importe pas l'espace de noms <xref:System.Security> par défaut.  Vous devez ajouter cette instruction **using** ou **Imports** pour éviter les erreurs de compilation.  
  
2.  Enregistrez et fermez le fichier.  
  
#### Pour modifier le fichier Elements.xml  
  
1.  Dans le projet SiteColumnProjectTemplate, remplacez le contenu du fichier Elements.xml par le code XML suivant.  
  
    ```  
  
    <Elements xmlns="http://schemas.microsoft.com/sharepoint/">  
      <Field ID="{$guid5$}"   
          Name="$safeprojectname$"   
          DisplayName="$projectname$"   
          Type="Text"   
          Group="Custom Columns">  
      </Field>  
    </Elements>  
    ```  
  
     Le nouveau XML ajoute un élément `Field` qui définit le nom de la colonne de site, son type de base et le groupe dans lequel la colonne de site peut être répertoriée dans la galerie.  Pour plus d'informations sur le contenu du fichier, voir [Schéma de définition de champ](http://go.microsoft.com/fwlink/?LinkId=184290).  
  
2.  Enregistrez et fermez le fichier.  
  
#### Pour modifier le fichier SharePointProjectItem.spdata  
  
1.  Dans le projet SiteColumnProjectTemplate, remplacez le contenu du fichier SharePointProjectItem.spdata par le code XML suivant.  
  
    ```  
  
    <ProjectItem Type="Contoso.SiteColumn" DefaultFile="Elements.xml"   
                 xmlns="http://schemas.microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel">  
      <Files>  
        <ProjectItemFile Source="Elements.xml" Target="$safeprojectname$\" Type="ElementManifest" />  
      </Files>   
    </ProjectItem>  
    ```  
  
     Le nouveau XML apporte les modifications suivantes au fichier :  
  
    -   Remplace l'attribut `Type` de l'élément `ProjectItem` par la même chaîne transmise au <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute> de la définition d'élément de projet \(classe `SiteColumnProjectItemTypeProvider` que vous avez créée précédemment dans cette procédure\).  
  
    -   Supprime les attributs `SupportedTrustLevels` et `SupportedDeploymentScopes` de l'élément `ProjectItem`.  Ces valeurs d'attribut sont inutiles, étant donné que les niveaux de confiance et portées de déploiement sont spécifiés dans la classe `SiteColumnProjectItemTypeProvider` dans le projet ProjectItemTypeDefinition.  
  
     Pour plus d'informations sur le contenu des fichiers .spdata, consultez [SharePoint Project Item Schema Reference](../sharepoint/sharepoint-project-item-schema-reference.md).  
  
2.  Enregistrez et fermez le fichier.  
  
#### Pour modifier le fichier Feature1.feature  
  
1.  Dans le projet SiteColumnProjectTemplate, remplacez le contenu du fichier Feature1.feature par le code XML suivant.  
  
    ```  
  
    <feature xmlns:dm0="http://schemas.microsoft.com/VisualStudio/2008/DslTools/Core" dslVersion="1.0.0.0" Id="$guid4$" featureId="$guid4$"   
             imageUrl="" solutionId="00000000-0000-0000-0000-000000000000" title="Site Column Feature1" version=""  
             deploymentPath="$SharePoint.Project.FileNameWithoutExtension$_$SharePoint.Feature.FileNameWithoutExtension$"  
             xmlns="http://schemas.microsoft.com/VisualStudio/2008/SharePointTools/FeatureModel">  
      <projectItems>  
        <projectItemReference itemId="$guid2$" />  
      </projectItems>  
    </feature>  
    ```  
  
     Le nouveau XML apporte les modifications suivantes au fichier :  
  
    -   Remplace les valeurs des attributs `Id` et `featureId` de l'élément `feature` par `$guid4$`.  
  
    -   Remplace les valeurs de l'attribut `itemId` de l'élément `projectItemReference` par `$guid2$`.  
  
     Pour plus d'informations sur les fichiers .feature, consultez [Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
2.  Enregistrez et fermez le fichier.  
  
#### Pour modifier le fichier Package.package  
  
1.  Dans le projet SiteColumnProjectTemplate, remplacez le contenu du fichier Package.package par le code XML suivant.  
  
    ```  
  
    <package xmlns:dm0="http://schemas.microsoft.com/VisualStudio/2008/DslTools/Core" dslVersion="1.0.0.0"   
             Id="$guid3$" solutionId="$guid3$" resetWebServer="false" name="$safeprojectname$"   
             xmlns="http://schemas.microsoft.com/VisualStudio/2008/SharePointTools/PackageModel">  
      <features>  
        <featureReference itemId="$guid4$" />  
      </features>  
    </package>  
    ```  
  
     Le nouveau XML apporte les modifications suivantes au fichier :  
  
    -   Remplace les valeurs des attributs `Id` et `solutionId` de l'élément `package` par `$guid3$`.  
  
    -   Remplace les valeurs de l'attribut `itemId` de l'élément `featureReference` par `$guid4$`.  
  
     Pour plus d'informations sur les fichiers .package, consultez [Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
2.  Enregistrez et fermez le fichier.  
  
#### Pour modifier le fichier SiteColumnProjectTemplate.vstemplate  
  
1.  Dans le projet SiteColumnProjectTemplate, remplacez le contenu du fichier SiteColumnProjectTemplate.vstemplate par l'une des sections XML suivantes.  
  
    -   Si vous créez un modèle de projet Visual C\#, utilisez la syntaxe XML suivante.  
  
    ```  
  
    <VSTemplate Version="3.0.0" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" Type="Project">  
      <TemplateData>  
        <Name>Site Column</Name>  
        <Description>Creates a new site column in SharePoint</Description>  
        <FrameworkVersion>3.5</FrameworkVersion>  
        <ProjectType>CSharp</ProjectType>  
        <CreateNewFolder>true</CreateNewFolder>  
        <CreateInPlace>true</CreateInPlace>  
        <ProvideDefaultName>true</ProvideDefaultName>  
        <DefaultName>SiteColumn</DefaultName>  
        <LocationField>Enabled</LocationField>  
        <EnableLocationBrowseButton>true</EnableLocationBrowseButton>  
        <PromptForSaveOnCreation>true</PromptForSaveOnCreation>  
        <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>  
        <Icon>SiteColumnProjectTemplate.ico</Icon>  
        <SortOrder>1000</SortOrder>  
      </TemplateData>  
      <TemplateContent>  
        <Project TargetFileName="SharePointProject1.csproj" File="ProjectTemplate.csproj" ReplaceParameters="true">  
          <ProjectItem ReplaceParameters="true" TargetFileName="Properties\AssemblyInfo.cs">AssemblyInfo.cs</ProjectItem>  
          <ProjectItem ReplaceParameters="true" TargetFileName="Features\Feature1\Feature1.feature">Feature1.feature</ProjectItem>  
          <ProjectItem ReplaceParameters="true" TargetFileName="Features\Feature1\Feature1.Template.xml">Feature1.template.xml</ProjectItem>  
          <ProjectItem ReplaceParameters="true" TargetFileName="Package\Package.package">Package.package</ProjectItem>  
          <ProjectItem ReplaceParameters="true" TargetFileName="Package\Package.Template.xml">Package.Template.xml</ProjectItem>  
          <ProjectItem ReplaceParameters="true" TargetFileName="Field1\SharePointProjectItem.spdata">SharePointProjectItem.spdata</ProjectItem>  
          <ProjectItem ReplaceParameters="true" TargetFileName="Field1\Elements.xml" OpenInEditor="true">Elements.xml</ProjectItem>  
          <ProjectItem ReplaceParameters="false" TargetFileName="key.snk">key.snk</ProjectItem>  
        </Project>  
      </TemplateContent>  
    </VSTemplate>  
    ```  
  
    -   Si vous créez un modèle de projet Visual Basic, utilisez le XML suivant.  
  
    ```  
  
    <VSTemplate Version="3.0.0" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" Type="Project">  
      <TemplateData>  
        <Name>Site Column</Name>  
        <Description>Creates a new site column in SharePoint</Description>  
        <FrameworkVersion>3.5</FrameworkVersion>  
        <ProjectType>VisualBasic</ProjectType>  
        <CreateNewFolder>true</CreateNewFolder>  
        <CreateInPlace>true</CreateInPlace>  
        <ProvideDefaultName>true</ProvideDefaultName>  
        <DefaultName>SiteColumn</DefaultName>  
        <LocationField>Enabled</LocationField>  
        <EnableLocationBrowseButton>true</EnableLocationBrowseButton>  
        <PromptForSaveOnCreation>true</PromptForSaveOnCreation>  
        <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>  
        <Icon>SiteColumnProjectTemplate.ico</Icon>  
        <SortOrder>1000</SortOrder>  
      </TemplateData>  
      <TemplateContent>  
        <Project TargetFileName="SharePointProject1.vbproj" File="ProjectTemplate.vbproj" ReplaceParameters="true">  
          <ProjectItem ReplaceParameters="true" TargetFileName="My Project\AssemblyInfo.vb">AssemblyInfo.vb</ProjectItem>  
          <ProjectItem ReplaceParameters="true" TargetFileName="Features\Feature1\Feature1.feature">Feature1.feature</ProjectItem>  
          <ProjectItem ReplaceParameters="true" TargetFileName="Features\Feature1\Feature1.Template.xml">Feature1.template.xml</ProjectItem>  
          <ProjectItem ReplaceParameters="true" TargetFileName="Package\Package.package">Package.package</ProjectItem>  
          <ProjectItem ReplaceParameters="true" TargetFileName="Package\Package.Template.xml">Package.Template.xml</ProjectItem>  
          <ProjectItem ReplaceParameters="true" TargetFileName="Field1\SharePointProjectItem.spdata">SharePointProjectItem.spdata</ProjectItem>  
          <ProjectItem ReplaceParameters="true" TargetFileName="Field1\Elements.xml" OpenInEditor="true">Elements.xml</ProjectItem>  
          <ProjectItem ReplaceParameters="false" TargetFileName="key.snk">key.snk</ProjectItem>  
        </Project>  
      </TemplateContent>  
    </VSTemplate>  
    ```  
  
     Le nouveau XML apporte les modifications suivantes au fichier :  
  
    -   Définit l'élément `Name` à la valeur **Colonne de site**. \(Ce nom apparaît dans la boîte de dialogue **Nouveau projet** \).  
  
    -   Ajoute les éléments `ProjectItem` pour chacun des fichiers inclus dans chaque instance de projet.  
  
    -   Utilise l'espace de noms « http:\/\/schemas.microsoft.com\/developer\/vstemplate\/2005 ».  D'autres fichiers projet dans cette solution utilisent l'espace de noms « http:\/\/schemas.microsoft.com\/developer\/msbuild\/2003 ».  Par conséquent, des messages d'avertissement de schéma XML sont générés, mais il est possible de les ignorer dans cette procédure.  
  
     Pour plus d'informations sur le contenu des fichiers .vstemplate, consultez [Référence du schéma de modèle Visual Studio](../extensibility/visual-studio-template-schema-reference.md).  
  
2.  Enregistrez et fermez le fichier.  
  
#### Pour modifier le fichier de ProjectTemplate.csproj ou ProjectTemplate.vbproj  
  
1.  Dans le projet SiteColumnProjectTemplate, remplacez le contenu du fichier ProjectTemplate.csproj ou du fichier ProjectTemplate.vbproj par l'une des sections XML suivantes.  
  
    -   Si vous créez un modèle de projet Visual C\#, utilisez la syntaxe XML suivante.  
  
    ```  
  
    <Project ToolsVersion="4.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
      <PropertyGroup>  
        <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>  
        <Platform Condition=" '$(Platform)' == '' ">AnyCPU</Platform>  
        <SchemaVersion>2.0</SchemaVersion>  
        <ProjectGuid>{$guid1$}</ProjectGuid>  
        <OutputType>Library</OutputType>  
        <AppDesignerFolder>Properties</AppDesignerFolder>  
        <RootNamespace>$safeprojectname$</RootNamespace>  
        <AssemblyName>$safeprojectname$</AssemblyName>  
        <TargetFrameworkVersion>v3.5</TargetFrameworkVersion>  
        <FileAlignment>512</FileAlignment>  
        <ProjectTypeGuids>{BB1F664B-9266-4fd6-B973-E1E44974B511};{14822709-B5A1-4724-98CA-57A101D1B079};{FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}</ProjectTypeGuids>  
      </PropertyGroup>  
      <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">  
        <DebugSymbols>true</DebugSymbols>  
        <DebugType>full</DebugType>  
        <Optimize>false</Optimize>  
        <OutputPath>bin\Debug\</OutputPath>  
        <DefineConstants>DEBUG;TRACE</DefineConstants>  
        <ErrorReport>prompt</ErrorReport>  
        <WarningLevel>4</WarningLevel>  
        <UseVSHostingProcess>false</UseVSHostingProcess>  
      </PropertyGroup>  
      <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Release|AnyCPU' ">  
        <DebugType>pdbonly</DebugType>  
        <Optimize>true</Optimize>  
        <OutputPath>bin\Release\</OutputPath>  
        <DefineConstants>TRACE</DefineConstants>  
        <ErrorReport>prompt</ErrorReport>  
        <WarningLevel>4</WarningLevel>  
      </PropertyGroup>  
      <PropertyGroup>  
        <SignAssembly>true</SignAssembly>  
        <AssemblyOriginatorKeyFile>key.snk</AssemblyOriginatorKeyFile>  
      </PropertyGroup>  
      <ItemGroup>  
        <Reference Include="System" />  
        <Reference Include="System.Core" />  
        <Reference Include="System.Data" />  
        <Reference Include="System.Data.DataSetExtensions" />  
        <Reference Include="System.Web" />  
        <Reference Include="System.Xml" />  
        <Reference Include="System.Xml.Linq" />  
        <Reference Include="Microsoft.SharePoint" />  
        <Reference Include="Microsoft.SharePoint.Security" />  
      </ItemGroup>  
      <ItemGroup>  
        <Compile Include="Properties\AssemblyInfo.cs" />  
      </ItemGroup>  
      <ItemGroup>  
        <None Include="Field1\SharePointProjectItem.spdata">  
          <SharePointProjectItemId>{$guid2$}</SharePointProjectItemId>  
        </None>  
        <None Include="Field1\Elements.xml" />  
      </ItemGroup>  
      <ItemGroup>  
        <None Include="key.snk" />  
        <None Include="Package\Package.package">  
          <PackageId>{$guid3$}</PackageId>  
        </None>  
        <None Include="Package\Package.Template.xml">  
          <DependentUpon>Package.package</DependentUpon>  
        </None>  
        <None Include="Features\Feature1\Feature1.feature">  
          <FeatureId>{$guid4$}</FeatureId>  
        </None>  
        <None Include="Features\Feature1\Feature1.Template.xml">  
          <DependentUpon>Feature1.feature</DependentUpon>  
        </None>  
      </ItemGroup>  
      <Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />  
      <Import Project="$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v10.0\SharePointTools\Microsoft.VisualStudio.SharePoint.targets" />  
    </Project>  
    ```  
  
    1.  Si vous créez un modèle de projet Visual Basic, utilisez le XML suivant.  
  
    ```  
  
    <Project ToolsVersion="4.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
      <PropertyGroup>  
        <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>  
        <Platform Condition=" '$(Platform)' == '' ">AnyCPU</Platform>  
        <ProductVersion>  
        </ProductVersion>  
        <SchemaVersion>  
        </SchemaVersion>  
        <ProjectGuid>{$guid1$}</ProjectGuid>  
        <OutputType>Library</OutputType>  
        <RootNamespace>$safeprojectname$</RootNamespace>  
        <AssemblyName>$safeprojectname$</AssemblyName>  
        <TargetFrameworkVersion>v3.5</TargetFrameworkVersion>  
        <FileAlignment>512</FileAlignment>  
        <ProjectTypeGuids>{BB1F664B-9266-4fd6-B973-E1E44974B511};{D59BE175-2ED0-4C54-BE3D-CDAA9F3214C8};{F184B08F-C81C-45F6-A57F-5ABD9991F28F}</ProjectTypeGuids>  
        <OptionExplicit>On</OptionExplicit>  
        <OptionCompare>Binary</OptionCompare>  
        <OptionStrict>Off</OptionStrict>  
        <OptionInfer>On</OptionInfer>  
      </PropertyGroup>  
      <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">  
        <DebugSymbols>true</DebugSymbols>  
        <DebugType>full</DebugType>  
        <DefineDebug>true</DefineDebug>  
        <DefineTrace>true</DefineTrace>  
        <OutputPath>bin\Debug\</OutputPath>  
        <WarningLevel>4</WarningLevel>  
        <UseVSHostingProcess>false</UseVSHostingProcess>  
      </PropertyGroup>  
      <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Release|AnyCPU' ">  
        <DebugType>pdbonly</DebugType>  
        <DefineDebug>false</DefineDebug>  
        <DefineTrace>true</DefineTrace>  
        <Optimize>true</Optimize>  
        <OutputPath>bin\Release\</OutputPath>  
        <UseVSHostingProcess>false</UseVSHostingProcess>  
      </PropertyGroup>  
      <PropertyGroup>  
        <SignAssembly>true</SignAssembly>  
        <AssemblyOriginatorKeyFile>key.snk</AssemblyOriginatorKeyFile>  
      </PropertyGroup>  
      <ItemGroup>  
        <Reference Include="System" />  
        <Reference Include="System.Core" />  
        <Reference Include="System.Data" />  
        <Reference Include="System.Data.DataSetExtensions" />  
        <Reference Include="System.Xml" />  
        <Reference Include="System.Xml.Linq" />  
        <Reference Include="Microsoft.SharePoint" />  
        <Reference Include="Microsoft.SharePoint.Security" />  
      </ItemGroup>  
      <ItemGroup>  
        <Import Include="Microsoft.VisualBasic" />  
        <Import Include="System" />  
        <Import Include="System.Collections" />  
        <Import Include="System.Collections.Generic" />  
        <Import Include="System.Data" />  
        <Import Include="System.Diagnostics" />  
        <Import Include="System.Linq" />  
        <Import Include="System.Xml.Linq" />  
        <Import Include="Microsoft.SharePoint" />  
        <Import Include="Microsoft.SharePoint.Security" />  
      </ItemGroup>  
      <ItemGroup>  
        <Compile Include="My Project\AssemblyInfo.vb" />  
      </ItemGroup>  
      <ItemGroup>  
        <AppDesigner Include="My Project\" />  
      </ItemGroup>  
      <ItemGroup>  
        <None Include="Features\Feature1\Feature1.feature">  
          <FeatureId>{$guid4$}</FeatureId>  
        </None>  
        <None Include="Field1\SharePointProjectItem.spdata">  
          <SharePointProjectItemId>{$guid2$}</SharePointProjectItemId>  
        </None>  
        <None Include="key.snk" />  
        <None Include="Package\Package.package">  
          <PackageId>{$guid3$}</PackageId>  
        </None>  
        <None Include="Package\Package.Template.xml">  
          <DependentUpon>Package.package</DependentUpon>  
        </None>  
      </ItemGroup>  
      <ItemGroup>  
        <None Include="Features\Feature1\Feature1.Template.xml">  
          <DependentUpon>Feature1.feature</DependentUpon>  
        </None>  
        <None Include="Field1\Elements.xml" />  
      </ItemGroup>  
      <Import Project="$(MSBuildToolsPath)\Microsoft.VisualBasic.targets" />  
      <Import Project="$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v10.0\SharePointTools\Microsoft.VisualStudio.SharePoint.targets" />  
    </Project>  
    ```  
  
     Le nouveau XML apporte les modifications suivantes au fichier :  
  
    -   Utilise l'élément `TargetFrameworkVersion` pour spécifier le .NET Framework 3.5 à la place de 4.5.  
  
    -   Ajoute les éléments `SignAssembly` et `AssemblyOriginatorKeyFile` pour signer la sortie de projet.  
  
    -   Ajoute de nouveaux éléments `Reference` pour les références d'assembly utilisées par les projets SharePoint.  
  
    -   Ajoute de nouveaux éléments pour chacun des fichiers par défaut du projet, notamment Elements.xml et SharePointProjectItem.spdata.  
  
2.  Enregistrez et fermez le fichier.  
  
## Création d'un package VSIX pour déployer le modèle de projet  
 Pour déployer l'extension, utilisez le projet VSIX dans la solution **SiteColumnProjectItem** pour créer un package VSIX.  En premier lieu, configurez le package VSIX en modifiant le fichier source.extension.vsixmanifest qui est inclus dans le projet VSIX.  Ensuite, créez le package VSIX en générant la solution.  
  
#### Pour configurer et créer le package VSIX  
  
1.  Dans l' **Explorateur de solutions**, dans le projet **SiteColumnProjectItem**, ouvrez le fichier manifeste source.extension.vsixmanifest dans l'éditeur de manifeste.  
  
     Le fichier source.extension.vsixmanifest est la base du fichier extension.vsixmanifest requis par tous les packages VSIX.  Pour plus d'informations sur ce fichier, consultez [Référence de schéma d'extensions VSIX](http://msdn.microsoft.com/fr-fr/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).  
  
2.  Dans la zone **Nom du produit**, entrez **Colonne de site**.  
  
3.  Dans la zone **Auteur**, tapez **Contoso**.  
  
4.  Dans la zone **Description**, tapez **Un projet SharePoint pour la création de colonnes de site**.  
  
5.  Sélectionnez l'onglet **Composants**, puis choisissez le bouton **Nouveau**.  
  
     La boîte de dialogue **Ajouter un nouveau composant** s'ouvre.  
  
6.  Dans la liste **Type**, choisissez **Microsoft.VisualStudio.ProjectTemplate**.  
  
    > [!NOTE]  
    >  Cette valeur correspond à l'élément `ProjectTemplate` dans le fichier extension.vsixmanifest.  Cet élément identifie le sous\-dossier du package VSIX qui contient le modèle de projet.  Pour plus d'informations, consultez [NIB: ProjectTemplate Element \(VSX Schema\)](http://msdn.microsoft.com/fr-fr/87add64c-9dcd-495f-8815-209dab182cb1).  
  
7.  Dans la liste **Source**, choisissez **Un projet dans la solution actuelle**.  
  
8.  Dans la liste **Projet**, choisissez **SiteColumnProjectTemplate**, puis le bouton **OK**.  
  
9. Sélectionnez le bouton **Nouveau** à nouveau.  
  
     La boîte de dialogue **Ajouter un nouveau composant** s'ouvre.  
  
10. Dans la liste **Type**, choisissez **Microsoft.VisualStudio.MefComponent**.  
  
    > [!NOTE]  
    >  Cette valeur correspond à l'élément `MefComponent` dans le fichier extension.vsixmanifest.  Cet élément spécifie le nom d'un assembly d'extension dans le package VSIX.  Pour plus d'informations, consultez [NIB: MEFComponent Element \(VSX Schema\)](http://msdn.microsoft.com/fr-fr/8a813141-8b73-44c9-b80b-ca85bbac9551).  
  
11. Dans la liste **Source**, choisissez **Un projet dans la solution actuelle**.  
  
12. Dans la liste **Projet**, choisissez **ProjectItemTypeDefinition**, puis le bouton **OK**.  
  
13. Dans la barre de menus, sélectionnez **Générer**, **Générer la solution**, puis vérifiez que les projet se compilent sans erreurs.  
  
## Test du modèle de projet  
 Vous êtes maintenant prêt à tester le modèle de projet.  Commencez à déboguer la solution SiteColumnProjectItem dans l'instance expérimentale de Visual Studio.  Testez ensuite le projet **Colonne de site** dans l'instance expérimentale de Visual Studio.  Enfin, générez et exécutez le projet SharePoint pour vous assurer que la colonne de site fonctionne comme prévu.  
  
#### Pour commencer à déboguer la solution  
  
1.  Redémarrez Visual Studio avec les privilèges d'administrateur et ouvrez la solution SiteColumnProjectItem.  
  
2.  Dans le fichier de code SiteColumnProjectItemTypeProvider, ajoutez un point d'arrêt sur la première ligne de code dans la méthode `InitializeType`, puis appuyez sur la touche **F5** pour démarrer le débogage.  
  
     Visual Studio installe l'extension sous %UserProfile%\\AppData\\Local\\Microsoft\\VisualStudio\\10.0Exp\\Extensions\\Contoso\\Site Column\\1.0 et démarre une instance expérimentale de Visual Studio.  Vous testerez l'élément de projet dans cette instance de Visual Studio.  
  
#### Pour tester le projet dans Visual Studio  
  
1.  Dans l'instance expérimentale de Visual Studio, dans la barre de menu, sélectionnez **Fichier**, **Nouveau**, puis cliquez sur **Projet**.  
  
2.  Développez **Visual C\#** ou **Visual Basic** \(selon le langage pris en charge par votre modèle de projet\), développez **SharePoint**, puis cliquez sur **2010**.  
  
3.  Dans la liste des modèles de projet, choisissez le modèle **Colonne de site**.  
  
4.  Dans la zone de texte **Nom**, entrez **SiteColumnTest**, puis choisissez le bouton **OK**.  
  
     Un nouveau projet s'affiche dans l' **Explorateur de solutions** avec un élément de projet nommé **Field1**.  
  
5.  Vérifiez que le code dans l'autre instance de Visual Studio s'arrête au point d'arrêt que vous avez défini précédemment dans la méthode `InitializeType`, puis appuyez sur **F5** pour continuer à déboguer le projet.  
  
6.  Dans **Explorateur de solutions**, choisissez le nœud **Field1**, puis appuyez sur la touche **F4**.  
  
     Cela a pour effet d'ouvrir la fenêtre **Propriétés**.  
  
7.  Vérifiez si la propriété **Exemple de propriété** figure dans la liste des propriétés.  
  
#### Pour tester la colonne de site dans SharePoint  
  
1.  Dans l' **Explorateur de solutions**, sélectionnez le nœud **SiteColumnTest**.  
  
2.  Dans la fenêtre **Propriétés**,dans la zone de texte en regard de la propriété **URL du site** tapez **http:\/\/localhost**.  
  
     Cela spécifie le site SharePoint local sur l'ordinateur de développement que vous souhaitez utiliser pour le débogage.  
  
    > [!NOTE]  
    >  La propriété **URL du site** est vide par défaut parce que le modèle de projet Colonne de site ne fournit pas d'Assistant pour collecter cette valeur lorsque le projet est créé.  Pour en savoir plus sur l'ajout d'un Assistant qui invite le développeur à spécifier cette valeur, puis configure cette propriété dans le nouveau projet, consultez [Procédure pas à pas : création d'un élément de projet Colonne de site avec un modèle de projet, deuxième partie](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md).  
  
3.  Choisissez la touche **F5**.  
  
     La colonne de site est empaquetée et déployée sur le site SharePoint spécifié par la propriété **URL de site** du projet.  Le navigateur Web s'ouvre à la page par défaut de ce site.  
  
    > [!NOTE]  
    >  Si la boîte de dialogue **Le débogage de script est désactivé** s'affiche, cliquez sur **Oui** pour continuer à déboguer le projet.  
  
4.  Dans le menu **Actions de site**, cliquez sur **Paramètres du site**.  
  
5.  Sous la section **Galeries** de la page **Paramètres du site**, cliquez sur le lien **Colonnes de site**.  
  
6.  Dans la liste des colonnes de site, vérifiez qu'il existe un groupe **Colonnes personnalisées** qui contient une colonne nommée **SiteColumnTest**.  
  
7.  Fermez le navigateur Web.  
  
## Nettoyage de l'ordinateur de développement  
 Une fois le test du projet terminé, supprimez le modèle de projet de l'instance expérimentale de Visual Studio.  
  
#### Pour nettoyer l'ordinateur de développement  
  
1.  Dans l'instance expérimentale de Visual Studio, dans la barre de menu, cliquez sur **Outils**, **Extensions et mises à jour**.  
  
     La boîte de dialogue **Extensions et mises à jour** s'ouvre.  
  
2.  Dans la liste d'extensions, choisissez l'extension **Colonne de site**, puis choisissez le bouton **Désinstaller**.  
  
3.  Dans la boîte de dialogue qui s'affiche, cliquez sur **Oui** pour confirmer que vous voulez désinstaller l'extension.  
  
4.  Cliquez sur le bouton **Fermer** pour terminer la désinstallation.  
  
5.  Fermez les deux instances de Visual Studio \(l'instance expérimentale et l'instance de Visual Studio dans laquelle la solution SiteColumnProjectItem est ouverte\).  
  
## Étapes suivantes  
 Après avoir terminé cette procédure pas à pas, vous pouvez ajouter un Assistant au modèle de projet.  Lorsqu'un utilisateur crée un projet Colonne de site, l'Assistant invite l'utilisateur à indiquer l'URL du site à utiliser pour le débogage et lui demande si la nouvelle solution est un bac à sable \(sandbox\), puis l'Assistant configure le projet avec ces informations.  L'Assistant collecte également des informations sur la colonne \(par exemple le type de base et le groupe dans lequel la colonne peut être répertoriée dans la galerie des colonnes de site\) et ajoute ces informations dans le fichier Elements.xml du nouveau projet.  Pour plus d'informations, consultez [Procédure pas à pas : création d'un élément de projet Colonne de site avec un modèle de projet, deuxième partie](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md).  
  
## Voir aussi  
 [Procédure pas à pas : création d'un élément de projet Colonne de site avec un modèle de projet, deuxième partie](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)   
 [Defining Custom SharePoint Project Item Types](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)   
 [Saving Data in Extensions of the SharePoint Project System](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)   
 [Associating Custom Data with SharePoint Tools Extensions](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)  
  
  