---
title: 'Procédure pas à pas : Création d’un élément de projet de colonne de Site avec un modèle de projet, partie 1 | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project items, defining your own types
- project items [SharePoint development in Visual Studio], defining your own types
- SharePoint projects, creating custom templates
- SharePoint development in Visual Studio, defining new project item types
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: f6c683166eb2192a32e1d829800abed16db43e0c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53832149"
---
# <a name="walkthrough-create-a-site-column-project-item-with-a-project-template-part-1"></a>Procédure pas à pas : Créer un élément de projet de colonne de site avec un modèle de projet, partie 1
  Les projets SharePoint sont des conteneurs pour un ou plusieurs éléments de projet SharePoint. Vous pouvez étendre le système de projet SharePoint dans Visual Studio en créant vos propres types d’éléments de projet SharePoint et associez-les avec un modèle de projet. Dans cette procédure pas à pas, vous allez définir un type d’élément de projet pour la création d’une colonne de site, puis vous allez créer un modèle de projet qui peut être utilisé pour créer un nouveau projet qui contient un élément de projet de colonne de site.

 Cette procédure pas à pas décrit les tâches suivantes :

- Création d’une extension Visual Studio qui définit un nouveau type d’élément de projet SharePoint pour une colonne de site. Le type d’élément de projet inclut une propriété personnalisée simple qui s’affiche dans le **propriétés** fenêtre.

- Création d’un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] modèle de projet pour l’élément de projet.

- Création d’un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] package d’Extension (VSIX) pour déployer le modèle de projet et l’assembly d’extension.

- Débogage et test de l’élément de projet.

  Il s’agit d’une procédure pas à pas autonome. Après avoir terminé cette procédure pas à pas, vous pouvez améliorer l’élément de projet en ajoutant un Assistant pour le modèle de projet. Pour plus d’informations, consultez [Procédure pas à pas : Créer un élément de projet de colonne de site avec un modèle de projet, partie 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md).

> [!NOTE]
> Pour une série d’exemples de workflows, consultez [exemples de flux de travail SharePoint](https://docs.microsoft.com/sharepoint/dev/general-development/sharepoint-workflow-samples).

## <a name="prerequisites"></a>Prérequis
 Vous avez besoin des composants suivants sur l’ordinateur de développement pour effectuer cette procédure pas à pas :

- Prise en charge des éditions de Microsoft Windows, SharePoint et [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

- [!include[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]. Cette procédure pas à pas utilise le **projet VSIX** modèle dans le Kit de développement logiciel pour créer un package VSIX pour déployer l’élément de projet. Pour plus d’informations, consultez [étendre les outils SharePoint dans Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).

  Connaissance du concept suivant est utile, mais pas obligatoire, pour suivre la procédure pas à pas :

- Colonnes de site dans SharePoint. Pour plus d’informations, consultez [colonnes](http://go.microsoft.com/fwlink/?LinkId=183547).

- Modèles de projet dans Visual Studio. Pour plus d’informations, consultez [Création de modèles de projet et d’élément](../ide/creating-project-and-item-templates.md).

## <a name="create-the-projects"></a>Créer les projets
 Pour effectuer cette procédure pas à pas, vous devez créer trois projets :

- Un projet VSIX. Ce projet crée le package VSIX pour déployer l’élément de projet de colonne de site et le modèle de projet.

- Un projet de modèle de projet. Ce projet crée un modèle de projet qui peut être utilisé pour créer un nouveau projet SharePoint qui contient l’élément de projet de colonne de site.

- Un projet de bibliothèque de classes. Ce projet qui implémente une extension Visual Studio qui définit le comportement de l’élément de projet de colonne de site.

  Démarrer la procédure pas à pas en créant les projets.

#### <a name="to-create-the-vsix-project"></a>Pour créer le projet VSIX

1.  Démarrez [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2.  Dans la barre de menus, choisissez **Fichier** > **Nouveau** > **Projet**.

3.  En haut de la **nouveau projet** boîte de dialogue zone, assurez-vous que l’option **.NET Framework 4.5** est choisi dans la liste des versions du .NET Framework.

4.  Développez le **Visual Basic** ou **Visual C#** nœuds, puis choisissez le **extensibilité** nœud.

    > [!NOTE]
    >  Le **extensibilité** nœud est disponible uniquement si vous installez le SDK Visual Studio. Pour plus d’informations, consultez la section conditions préalables plus haut dans cette rubrique.

5.  Dans la liste des modèles de projet, choisissez **projet VSIX**.

6.  Dans le **nom** , entrez **SiteColumnProjectItem**, puis choisissez le **OK** bouton.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Ajoute le **SiteColumnProjectItem** projet **l’Explorateur de solutions**.

#### <a name="to-create-the-project-template-project"></a>Pour créer le projet de modèle de projet

1.  Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour le nœud de solution, choisissez **ajouter**, puis choisissez **nouveau projet**.

2.  En haut de la **nouveau projet** boîte de dialogue zone, assurez-vous que l’option **.NET Framework 4.5** est choisi dans la liste des versions du .NET Framework.

3.  Développez le **Visual C#** ou **Visual Basic** nœud, puis choisissez le **extensibilité** nœud.

4.  Dans la liste des modèles de projet, choisissez le **le modèle de projet c#** ou **modèle de projet Visual Basic** modèle.

5.  Dans le **nom** , entrez **SiteColumnProjectTemplate**, puis choisissez le **OK** bouton.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Ajoute le **SiteColumnProjectTemplate** projet à la solution.

6.  Supprimer le fichier de code Class1 du projet.

7.  Si vous avez créé un projet Visual Basic, vous devez également supprimer les fichiers suivants à partir du projet :

    -   *MyApplication.Designer.vb*

    -   MyApplication.myapp

    -   *Resources.Designer.vb*

    -   *Resources.resx*

    -   *Settings.Designer.vb*

    -   Settings.Settings

#### <a name="to-create-the-extension-project"></a>Pour créer le projet d’extension

1.  Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour le nœud de solution, choisissez **ajouter**, puis choisissez **nouveau projet**.

2.  En haut de la **nouveau projet** boîte de dialogue zone, assurez-vous que l’option **.NET Framework 4.5** est choisi dans la liste des versions du .NET Framework.

3.  Développez le **Visual C#** ou **Visual Basic** nœuds, choisissez le **Windows** nœud, puis choisissez le **bibliothèque de classes** modèle.

4.  Dans le **nom** , entrez **ProjectItemTypeDefinition** , puis choisissez le **OK** bouton.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Ajoute le **ProjectItemTypeDefinition** projet à la solution et ouvre le fichier de code Class1 par défaut.

5.  Supprimer le fichier de code Class1 du projet.

## <a name="configure-the-extension-project"></a>Configurer le projet d’extension
 Ajouter des fichiers de code et des références d’assembly pour configurer le projet d’extension.

#### <a name="to-configure-the-project"></a>Pour configurer le projet

1.  Dans le projet ProjectItemTypeDefinition, ajoutez un fichier de code nommé **SiteColumnProjectItemTypeProvider**.

2.  Dans la barre de menus, choisissez **Projet** > **Ajouter une référence**.

3.  Dans le **Gestionnaire de références - ProjectItemTypeDefinition** boîte de dialogue, développez le **assemblys** nœud, choisissez le **Framework** nœud, puis sélectionnez le Case à cocher System.ComponentModel.Composition.

4.  Choisissez le **Extensions** nœud, sélectionnez la case à cocher en regard de l’assembly Microsoft.VisualStudio.SharePoint, puis choisissez le **OK** bouton.

## <a name="define-the-new-sharepoint-project-item-type"></a>Définir le nouveau type d’élément de projet SharePoint
 Créez une classe qui implémente le <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> interface pour définir le comportement du nouveau type d’élément de projet. Implémentez cette interface chaque fois que vous souhaitez définir un nouveau type d’élément de projet.

#### <a name="to-define-the-new-sharepoint-project-item-type"></a>Pour définir le nouveau type d’élément de projet SharePoint

1.  Dans le **SiteColumnProjectItemTypeProvider** fichier de code, remplacez le code par défaut par le code suivant, puis enregistrez le fichier.

     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#1](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projectitemtypedefinition/sitecolumnprojectitemtypeprovider.cs#1)]
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#1](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projectitemtypedefinition/sitecolumnprojectitemtypeprovider.vb#1)]

## <a name="create-a-visual-studio-project-template"></a>Créer un modèle de projet Visual Studio
 En créant un modèle de projet, vous activez d’autres développeurs à créer des projets SharePoint qui contiennent des éléments de projet colonne de site. Un modèle de projet SharePoint inclut des fichiers qui sont requis pour tous les projets dans Visual Studio, telles que *.csproj* ou *.vbproj* et *.vstemplate* fichiers et les fichiers sont spécifiques aux projets SharePoint. Pour plus d’informations, consultez [créer des modèles de projet pour les éléments de projet SharePoint et de modèles d’élément](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).

 Dans cette procédure, vous créez un projet SharePoint vide pour générer les fichiers qui sont spécifiques aux projets SharePoint. Vous ajoutez ensuite ces fichiers au projet SiteColumnProjectTemplate afin qu’ils soient inclus dans le modèle qui est généré à partir de ce projet. Vous configurez également le fichier de projet SiteColumnProjectTemplate pour spécifier où le modèle de projet s’affiche dans le **nouveau projet** boîte de dialogue.

#### <a name="to-create-the-files-for-the-project-template"></a>Pour créer les fichiers du modèle de projet

1. Démarrez une deuxième instance de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] en tant qu’administrateur.

2. Créez un projet SharePoint 2010 nommé **BaseSharePointProject**.

   > [!IMPORTANT]
   >  Dans le **Assistant Personnalisation de SharePoint**, ne sélectionnez pas le **déployer en tant que solution de batterie** case d’option.

3. Ajouter un élément vide au projet, puis nommez l’élément **Field1**.

4. Enregistrez le projet, puis fermez la deuxième instance de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

5. Dans l’instance de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] qui contient la solution SiteColumnProjectItem est ouverte, dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour le **SiteColumnProjectTemplate** nœud de projet, choisissez  **Ajouter**, puis choisissez **élément existant**.

6. Dans le **ajouter un élément existant** boîte de dialogue, ouvrez la liste des extensions de fichier, puis choisissez **tous les fichiers (\*.\*)** .

7. Dans le répertoire qui contient le projet BaseSharePointProject, sélectionnez le fichier key.snk, puis choisissez le **ajouter** bouton.

   > [!NOTE]
   >  Dans cette procédure pas à pas, le modèle de projet que vous créez utilise le même fichier key.snk pour signer chaque projet est créé en utilisant le modèle. Pour savoir comment développer cet exemple pour créer un fichier key.snk différents pour chaque instance de projet, consultez [procédure pas à pas : Créer un élément de projet de colonne de site avec un modèle de projet, partie 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md).

8. Répétez les étapes 5 à 8 pour ajouter les fichiers suivants à partir des sous-dossiers dans le dossier BaseSharePointProject spécifiés :

   - *\Field1\Elements.Xml*

   - *\Field1\SharePointProjectItem.spdata*

   - *\Features\Feature1\Feature1.Feature*

   - *\Features\Feature1\Feature1.Template.Xml*

   - *\Package\Package.package*

   - *\Package\Package.Template.Xml*

     Ajoutez ces fichiers directement dans le projet SiteColumnProjectTemplate ; ne pas recréer les sous-dossiers Field1, de fonctionnalités ou de Package dans le projet. Pour plus d’informations sur ces fichiers, consultez [créer des modèles de projet pour les éléments de projet SharePoint et de modèles d’élément](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).

#### <a name="to-configure-how-developers-discover-the-project-template-in-the-new-project-dialog-box"></a>Pour configurer la façon dont les développeurs découvrent le modèle de projet dans la boîte de dialogue Nouveau projet

1.  Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour le **SiteColumnProjectTemplate** nœud de projet, puis choisissez **décharger le projet**. Si vous êtes invité à enregistrer les modifications à tous les fichiers, choisissez le **Oui** bouton.

2.  Ouvrez le menu contextuel pour le **SiteColumnProjectTemplate** nœud à nouveau, puis choisissez **Modifier SiteColumnProjectTemplate.csproj** ou **Modifier SiteColumnProjectTemplate.vbproj**.

3.  Dans le fichier projet, recherchez ce qui suit `VSTemplate` élément.

    ```xml
    <VSTemplate Include="SiteColumnProjectTemplate.vstemplate">
    ```

4.  Remplacez cet élément par le code XML suivant.

    ```xml
    <VSTemplate Include="SiteColumnProjectTemplate.vstemplate">
      <OutputSubPath>SharePoint\SharePoint14</OutputSubPath>
    </VSTemplate>
    ```

     Le `OutputSubPath` élément spécifie des dossiers supplémentaires dans le chemin d’accès sous lequel le modèle de projet est créé lorsque vous générez le projet. Les dossiers spécifiés ici garantissent que le modèle de projet seront disponible uniquement lorsque les clients Ouvrir le **nouveau projet** boîte de dialogue, développez le **SharePoint** nœud, puis choisissez le **2010**  nœud.

5.  Enregistrez et fermez le fichier.

6.  Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour le **SiteColumnProjectTemplate** de projet, puis choisissez **recharger le projet**.

## <a name="edit-the-project-template-files"></a>Modifier les fichiers de modèle de projet
 Dans le projet SiteColumnProjectTemplate, modifiez les fichiers suivants pour définir le comportement du modèle de projet :

- *AssemblyInfo.cs* ou *AssemblyInfo.vb*

- *Elements.Xml*

- *SharePointProjectItem.spdata*

- *Feature1.Feature*

- *Package*

- *SiteColumnProjectTemplate.vstemplate*

- *ProjectTemplate.csproj* ou *ProjectTemplate.vbproj*

  Dans les procédures suivantes, vous allez ajouter des paramètres remplaçables à certains de ces fichiers. Un paramètre remplaçable est un jeton qui commence et se termine par le caractère de signe dollar ($). Lorsqu’un utilisateur utilise ce modèle de projet pour créer un projet, Visual Studio remplace automatiquement ces paramètres dans le nouveau projet avec des valeurs spécifiques. Pour plus d’informations, consultez [paramètres remplaçables](../sharepoint/replaceable-parameters.md).

#### <a name="to-edit-the-assemblyinfocs-or-assemblyinfovb-file"></a>Pour modifier le fichier AssemblyInfo.cs ou AssemblyInfo.vb

1.  Dans le projet SiteColumnProjectTemplate, ouvrez le *AssemblyInfo.cs* ou *AssemblyInfo.vb* fichier, puis ajoutez l’instruction suivante au début de celui-ci :

    ```vb
    Imports System.Security
    ```

    ```csharp
    using System.Security;
    ```

     Lorsque le **Solution bac à sable** propriété d’un projet SharePoint est définie sur **True**, Visual Studio ajoute le <xref:System.Security.AllowPartiallyTrustedCallersAttribute> au fichier de code AssemblyInfo. Toutefois, n’importe pas le fichier de code AssemblyInfo dans le modèle de projet la <xref:System.Security> espace de noms par défaut. Vous devez ajouter cette **à l’aide de** ou **importations** instruction afin d’éviter les erreurs de compilation.

2.  Enregistrez et fermez le fichier.

#### <a name="to-edit-the-elementsxml-file"></a>Pour modifier le fichier Elements.xml

1.  Dans le projet SiteColumnProjectTemplate, remplacez le contenu de la *Elements.xml* fichier avec le code XML suivant.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <Elements xmlns="http://schemas.microsoft.com/sharepoint/">
      <Field ID="{$guid5$}"
          Name="$safeprojectname$"
          DisplayName="$projectname$"
          Type="Text"
          Group="Custom Columns">
      </Field>
    </Elements>
    ```

     Le nouveau code XML ajoute un `Field` élément qui définit le nom de la colonne de site, son type de base et le groupe dans lequel la colonne de site dans la galerie. Pour plus d’informations sur le contenu de ce fichier, consultez [schéma de définition du champ](http://go.microsoft.com/fwlink/?LinkId=184290).

2.  Enregistrez et fermez le fichier.

#### <a name="to-edit-the-sharepointprojectitemspdata-file"></a>Pour modifier le fichier SharePointProjectItem.spdata

1. Dans le projet SiteColumnProjectTemplate, remplacez le contenu de la *SharePointProjectItem.spdata* fichier avec le code XML suivant.

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <ProjectItem Type="Contoso.SiteColumn" DefaultFile="Elements.xml"
                xmlns="http://schemas.microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel">
     <Files>
       <ProjectItemFile Source="Elements.xml" Target="$safeprojectname$\" Type="ElementManifest" />
     </Files>
   </ProjectItem>
   ```

    Le nouveau code XML apporte les modifications suivantes au fichier :

   - Modifications du `Type` attribut de la `ProjectItem` élément à la même chaîne est passée à la <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute> sur la définition d’élément de projet (le `SiteColumnProjectItemTypeProvider` classe que vous avez créé précédemment dans cette procédure pas à pas).

   - Supprime le `SupportedTrustLevels` et `SupportedDeploymentScopes` attributs à partir de la `ProjectItem` élément. Ces valeurs d’attribut sont inutiles, car les niveaux de confiance et les portées de déploiement sont spécifiées dans la `SiteColumnProjectItemTypeProvider` classe dans le projet ProjectItemTypeDefinition.

     Pour plus d’informations sur le contenu de *.spdata* de fichiers, consultez [référence de schéma élément de projet SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md).

2. Enregistrez et fermez le fichier.

#### <a name="to-edit-the-feature1feature-file"></a>Pour modifier le fichier Feature1.feature

1. Dans le projet SiteColumnProjectTemplate, remplacez le contenu de la *Feature1.feature* fichier avec le code XML suivant.

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <feature xmlns:dm0="http://schemas.microsoft.com/VisualStudio/2008/DslTools/Core" dslVersion="1.0.0.0" Id="$guid4$" featureId="$guid4$"
            imageUrl="" solutionId="00000000-0000-0000-0000-000000000000" title="Site Column Feature1" version=""
            deploymentPath="$SharePoint.Project.FileNameWithoutExtension$_$SharePoint.Feature.FileNameWithoutExtension$"
            xmlns="http://schemas.microsoft.com/VisualStudio/2008/SharePointTools/FeatureModel">
     <projectItems>
       <projectItemReference itemId="$guid2$" />
     </projectItems>
   </feature>
   ```

    Le nouveau code XML apporte les modifications suivantes au fichier :

   - Modifie les valeurs de la `Id` et `featureId` les attributs de la `feature` élément à `$guid4$`.

   - Modifie les valeurs de la `itemId` attribut de la `projectItemReference` élément à `$guid2$`.

     Pour plus d’informations sur *.feature* de fichiers, consultez [créer des modèles de projet pour les éléments de projet SharePoint et de modèles d’élément](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).

2. Enregistrez et fermez le fichier.

#### <a name="to-edit-the-packagepackage-file"></a>Pour modifier le fichier de package

1. Dans le projet SiteColumnProjectTemplate, remplacez le contenu de la *package* fichier avec le code XML suivant.

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <package xmlns:dm0="http://schemas.microsoft.com/VisualStudio/2008/DslTools/Core" dslVersion="1.0.0.0"
            Id="$guid3$" solutionId="$guid3$" resetWebServer="false" name="$safeprojectname$"
            xmlns="http://schemas.microsoft.com/VisualStudio/2008/SharePointTools/PackageModel">
     <features>
       <featureReference itemId="$guid4$" />
     </features>
   </package>
   ```

    Le nouveau code XML apporte les modifications suivantes au fichier :

   - Modifie les valeurs de la `Id` et `solutionId` les attributs de la `package` élément à `$guid3$`.

   - Modifie les valeurs de la `itemId` attribut de la `featureReference` élément à `$guid4$`.

     Pour plus d’informations sur *.package* de fichiers, consultez [créer des modèles de projet pour les éléments de projet SharePoint et de modèles d’élément](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).

2. Enregistrez et fermez le fichier.

#### <a name="to-edit-the-sitecolumnprojecttemplatevstemplate-file"></a>Pour modifier le fichier sitecolumnprojecttemplate.vstemplate

1. Dans le projet SiteColumnProjectTemplate, remplacez le contenu du fichier SiteColumnProjectTemplate.vstemplate avec l’une des sections suivantes de XML.

   -   Si vous créez un modèle de projet Visual c#, utilisez le code XML suivant.

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
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

   -   Si vous créez un modèle de projet Visual Basic, utilisez le code XML suivant.

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
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

    Le nouveau code XML apporte les modifications suivantes au fichier :

   - Définit le `Name` élément sur la valeur **colonne de Site**. (Ce nom apparaît dans le **nouveau projet** boîte de dialogue).

   - Ajoute `ProjectItem` éléments pour chaque filethat d’inclus dans chaque instance de projet.

   - Utilise l’espace de noms »<http://schemas.microsoft.com/developer/vstemplate/2005>«. Autres fichiers de projet en cours d’utilisation de cette solution le »<http://schemas.microsoft.com/developer/msbuild/2003>« espace de noms. Par conséquent, les messages d’avertissement schéma XML seront générées, mais vous pouvez les ignorer dans cette procédure pas à pas.

     Pour plus d’informations sur le contenu de *.vstemplate* de fichiers, consultez [référence de schéma de modèle Visual Studio](/visualstudio/extensibility/visual-studio-template-schema-reference).

2. Enregistrez et fermez le fichier.

#### <a name="to-edit-the-projecttemplatecsproj-or-projecttemplatevbproj-file"></a>Pour modifier le fichier projecttemplate.csproj ou projecttemplate.vbproj

1.  Dans le projet SiteColumnProjectTemplate, remplacez le contenu de la *ProjectTemplate.csproj* fichier ou *ProjectTemplate.vbproj* fichier avec l’une des sections suivantes de XML.

    -   Si vous créez un modèle de projet Visual c#, utilisez le code XML suivant.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
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

    1.  Si vous créez un modèle de projet Visual Basic, utilisez le code XML suivant.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
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

     Le nouveau code XML apporte les modifications suivantes au fichier :

    -   Utilise le `TargetFrameworkVersion` élément pour spécifier le .NET Framework 3.5, non 4.5.

    -   Ajoute `SignAssembly` et `AssemblyOriginatorKeyFile` éléments à signer la sortie du projet.

    -   Ajoute `Reference` éléments pour l’assembly fait référence à cette utilisation de projets SharePoint.

    -   Ajoute des éléments pour chaque fichier par défaut dans le projet, tel que *Elements.xml* et *SharePointProjectItem.spdata*.

2.  Enregistrez et fermez le fichier.

## <a name="create-a-vsix-package-to-deploy-the-project-template"></a>Créer un package VSIX pour déployer le modèle de projet
 Pour déployer l’extension, utilisez le projet VSIX dans le **SiteColumnProjectItem** solution pour créer un package VSIX. Tout d’abord, configurez le package VSIX en modifiant le fichier source.extension.vsixmanifest qui est inclus dans le projet VSIX. Ensuite, créez le package VSIX en générant la solution.

#### <a name="to-configure-and-create-the-vsix-package"></a>Pour configurer et créer le package VSIX

1.  Dans **l’Explorateur de solutions**, dans le **SiteColumnProjectItem** projet d’équipe, ouvrez le fichier source.extension.vsixmanifest dans l’éditeur de manifeste.

     Le fichier source.extension.vsixmanifest est la base du fichier extension.vsixmanifest qui nécessitent de tous les packages VSIX. Pour plus d’informations sur ce fichier, consultez [VSIX Extension schéma 1.0 référence](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).

2.  Dans le **Product Name** , entrez **colonne de Site**.

3.  Dans le **auteur** , entrez **Contoso**.

4.  Dans le **Description** , entrez **un projet SharePoint pour la création de colonnes de site**.

5.  Choisissez le **actifs** onglet, puis choisissez le **New** bouton.

     Le **ajouter un nouveau composant** boîte de dialogue s’ouvre.

6.  Dans le **Type** , choisissez **Microsoft.VisualStudio.ProjectTemplate**.

    > [!NOTE]
    >  Cette valeur correspond à la `ProjectTemplate` élément dans le fichier extension.vsixmanifest. Cet élément identifie le sous-dossier dans le package VSIX qui contient le modèle de projet. Pour plus d’informations, consultez [ProjectTemplate, élément (schéma VSX)](/previous-versions/visualstudio/visual-studio-2010/dd393735\(v\=vs.100\)).

7.  Dans le **Source** , choisissez **un projet dans la solution actuelle**.

8.  Dans le **projet** liste, puis choisissez **SiteColumnProjectTemplate**, puis choisissez le **OK** bouton.

9. Choisissez le **New** bouton à nouveau.

     Le **ajouter un nouveau composant** boîte de dialogue s’ouvre.

10. Dans le **Type** , choisissez **Microsoft.VisualStudio.MefComponent**.

    > [!NOTE]
    >  Cette valeur correspond à la `MefComponent` élément dans le fichier extension.vsixmanifest. Cet élément spécifie le nom d’un assembly d’extension dans le package VSIX. Pour plus d’informations, consultez [MEFComponent, élément (schéma VSX)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\)).

11. Dans le **Source** , choisissez **un projet dans la solution actuelle**.

12. Dans le **projet** , choisissez **ProjectItemTypeDefinition**, puis choisissez le **OK** bouton.

13. Dans la barre de menus, choisissez **Build** > **générer la Solution**, puis assurez-vous que le projet se compile sans erreur.

## <a name="test-the-project-template"></a>Le modèle de projet de test
 Vous êtes maintenant prêt à tester le modèle de projet. Tout d’abord, démarrez le débogage de la solution SiteColumnProjectItem dans l’instance expérimentale de Visual Studio. Ensuite, testez la **colonne de Site** projet dans l’instance expérimentale de Visual Studio. Enfin, générez et exécutez le projet SharePoint pour vérifier que la colonne de site fonctionne comme prévu.

#### <a name="to-start-debugging-the-solution"></a>Pour démarrer le débogage de la solution

1.  Redémarrez Visual Studio en tant qu’administrateur et ouvrez la solution SiteColumnProjectItem.

2.

3.  Dans le fichier de code SiteColumnProjectItemTypeProvider, ajoutez un point d’arrêt à la première ligne de code dans le `InitializeType` (méthode), puis choisissez le **F5** touche pour démarrer le débogage.

     Visual Studio installe l’extension %UserProfile%\AppData\Local\Microsoft\VisualStudio\10.0Exp\Extensions\Contoso\Site Column\1.0 et démarre une instance expérimentale de Visual Studio. Vous allez tester l’élément de projet dans cette instance de Visual Studio.

#### <a name="to-test-the-project-in-visual-studio"></a>Pour tester le projet dans Visual Studio

1.  Dans l’instance expérimentale de Visual Studio, dans la barre de menus, choisissez **fichier** > **New** > **projet**.

2.  Développez le **Visual C#** ou **Visual Basic** nœud (selon le langage qui prend en charge de votre modèle de projet), développez le **SharePoint** nœud, puis choisissez le **2010** nœud.

3.  Dans la liste des modèles de projet, choisissez le **colonne de Site** modèle.

4.  Dans le **nom** , entrez **SiteColumnTest** , puis choisissez le **OK** bouton.

     Dans **l’Explorateur de solutions**, un nouveau projet s’affiche avec un élément de projet nommé **Field1**.

5.  Vérifiez que le code dans l’autre instance de Visual Studio s’arrête au point d’arrêt que vous avez défini précédemment dans le `InitializeType` (méthode), puis choisissez le **F5** touche pour continuer à déboguer le projet.

6.  Dans **l’Explorateur de solutions**, choisissez le **Field1** nœud, puis choisissez le **F4** clé.

     Le **propriétés** fenêtre s’ouvre.

7.  Dans la liste des propriétés, vérifiez que la propriété **exemple de propriété** s’affiche.

#### <a name="to-test-the-site-column-in-sharepoint"></a>Pour tester la colonne de site dans SharePoint

1.  Dans **l’Explorateur de solutions**, choisissez le **SiteColumnTest** nœud.

2.  Dans le **propriétés** fenêtre, dans la zone de texte située en regard du **URL du Site** propriété, entrez **http://localhost**.

     Cette étape spécifie le site SharePoint local sur l’ordinateur de développement que vous souhaitez utiliser pour le débogage.

    > [!NOTE]
    >  Le **URL du Site** propriété est vide par défaut, car le modèle de projet colonne de Site ne fournit pas un Assistant pour collecter cette valeur lorsque le projet est créé. Pour savoir comment ajouter un Assistant qui vous demande le développeur pour cette valeur, puis configure cette propriété dans le nouveau projet, consultez [procédure pas à pas : Créer un élément de projet de colonne de site avec un modèle de projet, partie 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md).

3.  Choisissez la touche **F5**.

     La colonne de site est empaquetée et déployée vers le site SharePoint qui est spécifié dans le **URL du Site** propriété du projet. Le navigateur web s’ouvre à la page par défaut de ce site.

    > [!NOTE]
    >  Si le **le débogage de Script est désactivé** boîte de dialogue s’affiche, choisissez le **Oui** pour continuer à déboguer le projet.

4.  Sur le **Actions du Site** menu, choisissez **paramètres du Site**.

5.  Sur le **paramètres du Site** page, sous la **galeries** , choisissez le **colonnes de Site** lien.

6.  Dans la liste des colonnes de site, vérifiez qu’un **colonnes personnalisées** groupe contient une colonne nommée **SiteColumnTest**.

7.  Fermez le navigateur web.

## <a name="clean-up-the-development-computer"></a>Nettoyer l’ordinateur de développement
 Une fois que vous avez terminé le test du projet, supprimez le modèle de projet à partir de l’instance expérimentale de Visual Studio.

#### <a name="to-clean-up-the-development-computer"></a>Pour nettoyer l’ordinateur de développement

1.  Dans l’instance expérimentale de Visual Studio, dans la barre de menus, choisissez **outils** > **Extensions et mises à jour**.

     La boîte de dialogue **Extensions et mises à jour** s’ouvre.

2.  Dans la liste des extensions, choisissez le **colonne de Site** extension, puis choisissez le **désinstallation** bouton.

3.  Dans la boîte de dialogue qui s’affiche, choisissez le **Oui** pour confirmer que vous souhaitez désinstaller l’extension.

4.  Choisissez le **fermer** bouton pour terminer la désinstallation.

5.  Fermez les deux instances de Visual Studio (l’instance expérimentale et l’instance de Visual Studio dans laquelle la solution SiteColumnProjectItem est ouverte).

## <a name="next-steps"></a>Étapes suivantes
 Après avoir terminé cette procédure pas à pas, vous pouvez ajouter un Assistant pour le modèle de projet. Lorsqu’un utilisateur crée un projet colonne de Site, l’Assistant demande à l’utilisateur pour l’URL du site à utiliser pour le débogage et si la nouvelle solution est sable et l’Assistant configure le nouveau projet avec ces informations. Également, l’Assistant recueille des informations sur la colonne (par exemple, le type de base et le groupe dans lequel répertorier la colonne dans la galerie des colonnes de site) et ajoute ces informations pour le *Elements.xml* fichier dans le nouveau projet. Pour plus d’informations, consultez [Procédure pas à pas : Créer un élément de projet de colonne de site avec un modèle de projet, partie 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md).

## <a name="see-also"></a>Voir aussi

- [Procédure pas à pas : Créer un élément de projet de colonne de site avec un modèle de projet, partie 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)
- [Définir les types d’éléments de projet SharePoint personnalisés](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [Créer des modèles d’élément et les modèles de projet pour les éléments de projet SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)
- [Enregistrer les données dans les extensions du système de projet SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)
- [Associer des données personnalisées avec les extensions d’outils SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)