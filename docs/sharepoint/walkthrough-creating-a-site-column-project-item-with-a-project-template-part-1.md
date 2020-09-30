---
title: Créer un élément de projet colonne de site avec un modèle de projet, partie 1
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project items, defining your own types
- project items [SharePoint development in Visual Studio], defining your own types
- SharePoint projects, creating custom templates
- SharePoint development in Visual Studio, defining new project item types
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a740d96fb6ae846188fc4fa457c5baeb7b5e907d
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91585548"
---
# <a name="walkthrough-create-a-site-column-project-item-with-a-project-template-part-1"></a>Procédure pas à pas : création d’un élément de projet colonne de site avec un modèle de projet, partie 1
  Les projets SharePoint sont des conteneurs pour un ou plusieurs éléments de projet SharePoint. Vous pouvez étendre le système de projet SharePoint dans Visual Studio en créant vos propres types d’éléments de projet SharePoint, puis en les associant à un modèle de projet. Dans cette procédure pas à pas, vous allez définir un type d’élément de projet pour la création d’une colonne de site, puis vous allez créer un modèle de projet qui peut être utilisé pour créer un projet qui contient un élément de projet de colonne de site.

 Cette procédure pas à pas décrit les tâches suivantes :

- Création d’une extension Visual Studio qui définit un nouveau type d’élément de projet SharePoint pour une colonne de site. Le type d’élément de projet comprend une propriété personnalisée simple qui s’affiche dans la fenêtre **Propriétés** .

- Création d’un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] modèle de projet pour l’élément de projet.

- Génération [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] d’un package d’extension (VSIX) pour déployer le modèle de projet et l’assembly d’extension.

- Débogage et test de l’élément de projet.

  Il s’agit d’une procédure pas à pas autonome. Après avoir effectué cette procédure pas à pas, vous pouvez améliorer l’élément de projet en ajoutant un assistant au modèle de projet. Pour plus d’informations, consultez [procédure pas à pas : création d’un élément de projet colonne de site avec un modèle de projet, partie 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md).

> [!NOTE]
> Pour obtenir une série d’exemples de flux de travail, consultez [exemples de flux](/sharepoint/dev/general-development/sharepoint-workflow-samples)de travail SharePoint.

## <a name="prerequisites"></a>Prérequis
 Pour effectuer cette procédure pas à pas, vous avez besoin des composants suivants sur l’ordinateur de développement :

- Éditions prises en charge de Microsoft Windows, SharePoint et [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

- L’[!include[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]opérateur Cette procédure pas à pas utilise le modèle de **projet VSIX** dans le kit de développement logiciel (SDK) pour créer un package VSIX afin de déployer l’élément de projet. Pour plus d’informations, consultez [étendre les outils SharePoint dans Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).

  La connaissance du concept suivant est utile, mais pas obligatoire, pour effectuer la procédure pas à pas :

- Colonnes de site dans SharePoint. Pour plus d’informations, consultez [colonnes](/previous-versions/office/developer/sharepoint-2010/ms196085(v=office.14)).

- Modèles de projet dans Visual Studio. Pour plus d’informations, consultez [Création de modèles de projet et d’élément](../ide/creating-project-and-item-templates.md).

## <a name="create-the-projects"></a>Créer les projets
 Pour effectuer cette procédure pas à pas, vous devez créer trois projets :

- Projet VSIX. Ce projet crée le package VSIX pour déployer l’élément de projet colonne de site et le modèle de projet.

- Projet de modèle de projet. Ce projet crée un modèle de projet qui peut être utilisé pour créer un projet SharePoint qui contient l’élément de projet colonne de site.

- Projet de bibliothèque de classes. Ce projet qui implémente une extension Visual Studio qui définit le comportement de l’élément de projet colonne de site.

  Démarrez la procédure pas à pas en créant les projets.

#### <a name="to-create-the-vsix-project"></a>Pour créer le projet VSIX

1. Démarrez [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. Dans la barre de menus, choisissez **fichier**  >  **nouveau**  >  **projet**.

3. En haut de la boîte de dialogue **nouveau projet** , assurez-vous que **.NET Framework 4,5** est choisi dans la liste des versions du .NET Framework.

4. Développez les nœuds **Visual Basic** ou **Visual C#** , puis choisissez le nœud **extensibilité** .

    > [!NOTE]
    > Le nœud **extensibilité** est disponible uniquement si vous installez le kit de développement logiciel (SDK) Visual Studio. Pour plus d’informations, consultez la section conditions préalables, plus haut dans cette rubrique.

5. Dans la liste des modèles de projet, choisissez **projet VSIX**.

6. Dans la zone **nom** , entrez **SiteColumnProjectItem**, puis choisissez le bouton **OK** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Ajoute le projet **SiteColumnProjectItem** à **Explorateur de solutions**.

#### <a name="to-create-the-project-template-project"></a>Pour créer le projet de modèle de projet

1. Dans **Explorateur de solutions**, ouvrez le menu contextuel du nœud solution, choisissez **Ajouter**, puis **nouveau projet**.

2. En haut de la boîte de dialogue **nouveau projet** , assurez-vous que **.NET Framework 4,5** est choisi dans la liste des versions du .NET Framework.

3. Développez le nœud **Visual C#** ou **Visual Basic** , puis choisissez le nœud **extensibilité** .

4. Dans la liste des modèles de projet, choisissez le modèle de **projet C#** ou Visual Basic modèle de **modèle de projet** .

5. Dans la zone **nom** , entrez **SiteColumnProjectTemplate**, puis choisissez le bouton **OK** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Ajoute le projet **SiteColumnProjectTemplate** à la solution.

6. Supprimez le fichier de code Class1 du projet.

7. Si vous avez créé un projet Visual Basic, supprimez également les fichiers suivants du projet :

    - *MyApplication. Designer. vb*

    - MyApplication. MyApp

    - *Resources. Designer. vb*

    - *Resources. resx*

    - *Settings. Designer. vb*

    - Paramètres. Settings

#### <a name="to-create-the-extension-project"></a>Pour créer le projet d’extension

1. Dans **Explorateur de solutions**, ouvrez le menu contextuel du nœud solution, choisissez **Ajouter**, puis **nouveau projet**.

2. En haut de la boîte de dialogue **nouveau projet** , assurez-vous que **.NET Framework 4,5** est choisi dans la liste des versions du .NET Framework.

3. Développez les nœuds **Visual C#** ou **Visual Basic** , choisissez le nœud **Windows** , puis choisissez le modèle **bibliothèque de classes** .

4. Dans la zone **nom** , entrez **projectItemTypeDefinition** , puis choisissez le bouton **OK** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Ajoute le projet **projectItemTypeDefinition** à la solution et ouvre le fichier de code Class1 par défaut.

5. Supprimez le fichier de code Class1 du projet.

## <a name="configure-the-extension-project"></a>Configurer le projet d’extension
 Ajoutez des fichiers de code et des références d’assembly pour configurer le projet d’extension.

#### <a name="to-configure-the-project"></a>Pour configurer le projet

1. Dans le projet ProjectItemTypeDefinition, ajoutez un fichier de code nommé **SiteColumnProjectItemTypeProvider**.

2. Dans la barre de menus, choisissez **projet**  >  **Ajouter une référence**.

3. Dans la boîte de dialogue **Gestionnaire de références-projectItemTypeDefinition** , développez le nœud **assemblys** , choisissez le nœud **Framework** , puis activez la case à cocher System. ComponentModel. composition.

4. Choisissez le nœud **Extensions** , activez la case à cocher en regard de l’assembly Microsoft. VisualStudio. SharePoint, puis choisissez le bouton **OK** .

## <a name="define-the-new-sharepoint-project-item-type"></a>Définir le nouveau type d’élément de projet SharePoint
 Créez une classe qui implémente l' <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> interface pour définir le comportement du nouveau type d’élément de projet. Implémentez cette interface chaque fois que vous souhaitez définir un nouveau type d’élément de projet.

#### <a name="to-define-the-new-sharepoint-project-item-type"></a>Pour définir le nouveau type d’élément de projet SharePoint

1. Dans le fichier de code **SiteColumnProjectItemTypeProvider** , remplacez le code par défaut par le code suivant, puis enregistrez le fichier.

     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#1](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projectitemtypedefinition/sitecolumnprojectitemtypeprovider.cs#1)]
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#1](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projectitemtypedefinition/sitecolumnprojectitemtypeprovider.vb#1)]

## <a name="create-a-visual-studio-project-template"></a>Créer un modèle de projet Visual Studio
 En créant un modèle de projet, vous permettez à d’autres développeurs de créer des projets SharePoint qui contiennent des éléments de projet de colonne de site. Un modèle de projet SharePoint comprend des fichiers qui sont requis pour tous les projets dans Visual Studio, tels que les fichiers. *csproj* ou *. vbproj* et *. vstemplate* , ainsi que les fichiers spécifiques aux projets SharePoint. Pour plus d’informations, consultez [créer des modèles d’élément et des modèles de projet pour les éléments de projet SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).

 Dans cette procédure, vous créez un projet SharePoint vide pour générer les fichiers qui sont spécifiques aux projets SharePoint. Vous ajoutez ensuite ces fichiers au projet SiteColumnProjectTemplate afin qu’ils soient inclus dans le modèle généré à partir de ce projet. Vous configurez également le fichier projet SiteColumnProjectTemplate pour spécifier l’emplacement où le modèle de projet s’affiche dans la boîte de dialogue **nouveau projet** .

#### <a name="to-create-the-files-for-the-project-template"></a>Pour créer les fichiers pour le modèle de projet

1. Démarrez une deuxième instance de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] avec les informations d’identification d’administration.

2. Créez un projet SharePoint 2010 nommé **BaseSharePointProject**.

   > [!IMPORTANT]
   > Dans l' **Assistant Personnalisation de SharePoint**, ne sélectionnez pas la case **d’option déployer en tant que solution de batterie** .

3. Ajoutez un élément élément vide au projet, puis nommez l’élément **champ1**.

4. Enregistrez le projet, puis fermez la deuxième instance de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

5. Dans l’instance de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] qui a la solution SiteColumnProjectItem ouverte, dans **Explorateur de solutions**, ouvrez le menu contextuel du nœud de projet **SiteColumnProjectTemplate** , choisissez **Ajouter**, puis **élément existant**.

6. Dans la boîte de dialogue **Ajouter un élément existant** , ouvrez la liste des extensions de fichier, puis choisissez **tous les fichiers ( \* . \* )**.

7. Dans le répertoire qui contient le projet BaseSharePointProject, sélectionnez le fichier Key. snk, puis cliquez sur le bouton **Ajouter** .

   > [!NOTE]
   > Dans cette procédure pas à pas, le modèle de projet que vous créez utilise le même fichier Key. snk pour signer chaque projet créé à l’aide du modèle. Pour savoir comment développer cet exemple afin de créer un fichier. snk de clé pour chaque instance de projet, consultez [procédure pas à pas : création d’un élément de projet colonne de site avec un modèle de projet, deuxième partie](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md).

8. Répétez les étapes 5-8 pour ajouter les fichiers suivants à partir des sous-dossiers spécifiés dans le répertoire BaseSharePointProject :

   - *\Field1\Elements.xml*

   - *\Field1\SharePointProjectItem.spdata*

   - *\Features\Feature1\Feature1.feature*

   - *\Features\Feature1\Feature1.Template.xml*

   - *\Package\Package.package*

   - *\Package\Package.Template.xml*

     Ajoutez ces fichiers directement au projet SiteColumnProjectTemplate. ne recréez pas les sous-dossiers champ1, fonctionnalités ou packages dans le projet. Pour plus d’informations sur ces fichiers, consultez [créer des modèles d’élément et des modèles de projet pour les éléments de projet SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).

#### <a name="to-configure-how-developers-discover-the-project-template-in-the-new-project-dialog-box"></a>Pour configurer la façon dont les développeurs découvrent le modèle de projet dans la boîte de dialogue Nouveau projet

1. Dans **Explorateur de solutions**, ouvrez le menu contextuel du nœud de projet **SiteColumnProjectTemplate** , puis choisissez **décharger le projet**. Si vous êtes invité à enregistrer les modifications apportées à un fichier, choisissez le bouton **Oui** .

2. Ouvrez à nouveau le menu contextuel du nœud **SiteColumnProjectTemplate** , puis choisissez **modifier SiteColumnProjectTemplate. csproj** ou **modifier SiteColumnProjectTemplate. vbproj**.

3. Dans le fichier projet, recherchez l' `VSTemplate` élément suivant.

    ```xml
    <VSTemplate Include="SiteColumnProjectTemplate.vstemplate">
    ```

4. Remplacez cet élément par le code XML suivant.

    ```xml
    <VSTemplate Include="SiteColumnProjectTemplate.vstemplate">
      <OutputSubPath>SharePoint\SharePoint14</OutputSubPath>
    </VSTemplate>
    ```

     L' `OutputSubPath` élément spécifie des dossiers supplémentaires dans le chemin d’accès sous lequel le modèle de projet est créé lorsque vous générez le projet. Les dossiers spécifiés ici garantissent que le modèle de projet sera disponible uniquement lorsque les clients ouvriront la boîte **de dialogue Nouveau projet** , développez le nœud **SharePoint** , puis choisissez le nœud **2010** .

5. Enregistrez et fermez le fichier.

6. Dans **Explorateur de solutions**, ouvrez le menu contextuel du projet **SiteColumnProjectTemplate** , puis choisissez **recharger le projet**.

## <a name="edit-the-project-template-files"></a>Modifier les fichiers de modèle de projet
 Dans le projet SiteColumnProjectTemplate, modifiez les fichiers suivants pour définir le comportement du modèle de projet :

- *AssemblyInfo.cs* ou *AssemblyInfo. vb*

- *Elements.xml*

- *SharePointProjectItem. les données*

- *Feature1. Feature*

- *Package. Package*

- *SiteColumnProjectTemplate. vstemplate*

- *ProjectTemplate. csproj* ou *ProjectTemplate. vbproj*

  Dans les procédures suivantes, vous allez ajouter des paramètres remplaçables à certains de ces fichiers. Un paramètre remplaçable est un jeton qui commence et se termine par le caractère dollar ($). Quand un utilisateur utilise ce modèle de projet pour créer un projet, Visual Studio remplace automatiquement ces paramètres dans le nouveau projet par des valeurs spécifiques. Pour plus d’informations, consultez [paramètres remplaçables](../sharepoint/replaceable-parameters.md).

#### <a name="to-edit-the-assemblyinfocs-or-assemblyinfovb-file"></a>Pour modifier le fichier AssemblyInfo.cs ou AssemblyInfo. vb

1. Dans le projet SiteColumnProjectTemplate, ouvrez le fichier *AssemblyInfo.cs* ou *AssemblyInfo. vb* , puis ajoutez l’instruction suivante en haut de celui-ci :

    ```vb
    Imports System.Security
    ```

    ```csharp
    using System.Security;
    ```

     Lorsque la propriété de la **solution bac à sable (sandbox)** d’un projet SharePoint a la valeur **true**, Visual Studio ajoute le <xref:System.Security.AllowPartiallyTrustedCallersAttribute> au fichier de code AssemblyInfo. Toutefois, le fichier de code AssemblyInfo dans le modèle de projet n’importe pas l' <xref:System.Security> espace de noms par défaut. Vous devez l’ajouter à **l’aide de l'** instruction ou **Imports** pour éviter les erreurs de compilation.

2. Enregistrez et fermez le fichier.

#### <a name="to-edit-the-elementsxml-file"></a>Pour modifier le fichier Elements.xml

1. Dans le projet SiteColumnProjectTemplate, remplacez le contenu du fichier *Elements.xml* par le code XML suivant.

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

     Le nouveau XML ajoute un `Field` élément qui définit le nom de la colonne de site, son type de base et le groupe dans lequel répertorier la colonne de site dans la Galerie. Pour plus d’informations sur le contenu de ce fichier, consultez [schéma de définition de champ](/previous-versions/office/developer/sharepoint-2010/ms196289(v=office.14)).

2. Enregistrez et fermez le fichier.

#### <a name="to-edit-the-sharepointprojectitemspdata-file"></a>Pour modifier le fichier SharePointProjectItem. resdata

1. Dans le projet SiteColumnProjectTemplate, remplacez le contenu du fichier *SharePointProjectItem. didata* par le code XML suivant.

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

   - Affecte `Type` à l’attribut de l' `ProjectItem` élément la même chaîne que celle qui est passée au <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute> sur la définition de l’élément de projet (la `SiteColumnProjectItemTypeProvider` classe que vous avez créée précédemment dans cette procédure pas à pas).

   - Supprime les `SupportedTrustLevels` `SupportedDeploymentScopes` attributs et de l' `ProjectItem` élément. Ces valeurs d’attribut ne sont pas nécessaires, car les niveaux de confiance et les étendues de déploiement sont spécifiés dans la `SiteColumnProjectItemTypeProvider` classe du projet projectItemTypeDefinition.

     Pour plus d’informations sur le contenu des fichiers *. resdonnées* , consultez [Référence du schéma d’élément de projet SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md).

2. Enregistrez et fermez le fichier.

#### <a name="to-edit-the-feature1feature-file"></a>Pour modifier le fichier Feature1. Feature

1. Dans le projet SiteColumnProjectTemplate, remplacez le contenu du fichier *Feature1. Feature* par le code XML suivant.

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

   - Remplace les valeurs des `Id` attributs et `featureId` de l' `feature` élément par `$guid4$` .

   - Remplace les valeurs de l' `itemId` attribut de l' `projectItemReference` élément par `$guid2$` .

     Pour plus d’informations sur les fichiers *. Feature* , consultez [créer des modèles d’élément et des modèles de projet pour les éléments de projet SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).

2. Enregistrez et fermez le fichier.

#### <a name="to-edit-the-packagepackage-file"></a>Pour modifier le fichier Package. Package

1. Dans le projet SiteColumnProjectTemplate, remplacez le contenu du fichier *Package. Package* par le code XML suivant.

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

   - Remplace les valeurs des `Id` attributs et `solutionId` de l' `package` élément par `$guid3$` .

   - Remplace les valeurs de l' `itemId` attribut de l' `featureReference` élément par `$guid4$` .

     Pour plus d’informations sur les fichiers *. Package* , consultez [créer des modèles d’élément et des modèles de projet pour les éléments de projet SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).

2. Enregistrez et fermez le fichier.

#### <a name="to-edit-the-sitecolumnprojecttemplatevstemplate-file"></a>Pour modifier le fichier SiteColumnProjectTemplate. vstemplate

1. Dans le projet SiteColumnProjectTemplate, remplacez le contenu du fichier SiteColumnProjectTemplate. vstemplate par l’une des sections suivantes de XML.

   - Si vous créez un modèle de projet Visual C#, utilisez le code XML suivant.

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

   - Si vous créez un modèle de projet Visual Basic, utilisez le code XML suivant.

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

   - Définit l' `Name` élément sur la **colonne de site**de valeur. (Ce nom apparaît dans la boîte de dialogue **nouveau projet** ).

   - Ajoute `ProjectItem` des éléments pour chaque filethat inclus dans chaque instance de projet.

   - Utilise l’espace de noms `http://schemas.microsoft.com/developer/vstemplate/2005` . Les autres fichiers projet de cette solution utilisent l' `http://schemas.microsoft.com/developer/msbuild/2003` espace de noms. Par conséquent, les messages d’avertissement de schéma XML sont générés, mais vous pouvez les ignorer dans cette procédure pas à pas.

     Pour plus d’informations sur le contenu des fichiers *. vstemplate* , consultez [Référence du schéma de modèle Visual Studio](../extensibility/visual-studio-template-schema-reference.md).

2. Enregistrez et fermez le fichier.

#### <a name="to-edit-the-projecttemplatecsproj-or-projecttemplatevbproj-file"></a>Pour modifier le fichier ProjectTemplate. csproj ou ProjectTemplate. vbproj

1. Dans le projet SiteColumnProjectTemplate, remplacez le contenu du fichier *ProjectTemplate. csproj* ou du fichier *ProjectTemplate. vbproj* par l’une des sections suivantes de XML.

    - Si vous créez un modèle de projet Visual C#, utilisez le code XML suivant.

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

    1. Si vous créez un modèle de projet Visual Basic, utilisez le code XML suivant.

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

    - Utilise l' `TargetFrameworkVersion` élément pour spécifier le .NET Framework 3,5, et non 4,5.

    - Ajoute `SignAssembly` des `AssemblyOriginatorKeyFile` éléments et pour signer la sortie du projet.

    - Ajoute `Reference` des éléments pour les références d’assembly que les projets SharePoint utilisent.

    - Ajoute des éléments pour chaque fichier par défaut dans le projet, par exemple *Elements.xml* et *SharePointProjectItem. resdonnées*.

2. Enregistrez et fermez le fichier.

## <a name="create-a-vsix-package-to-deploy-the-project-template"></a>Créer un package VSIX pour déployer le modèle de projet
 Pour déployer l’extension, utilisez le projet VSIX dans la solution **SiteColumnProjectItem** pour créer un package VSIX. Tout d’abord, configurez le package VSIX en modifiant le fichier source. extension. vsixmanifest qui est inclus dans le projet VSIX. Ensuite, créez le package VSIX en générant la solution.

#### <a name="to-configure-and-create-the-vsix-package"></a>Pour configurer et créer le package VSIX

1. Dans **Explorateur de solutions**, dans le projet **SiteColumnProjectItem** , ouvrez le fichier source. extension. vsixmanifest dans l’éditeur de manifeste.

     Le fichier source. extension. vsixmanifest est la base du fichier extension. vsixmanifest requis par tous les packages VSIX. Pour plus d’informations sur ce fichier, consultez [Référence du schéma d’extension VSIX 1,0](/previous-versions/dd393700(v=vs.110)).

2. Dans la zone **nom du produit** , entrez colonne de **site**.

3. Dans la zone **auteur** , entrez **contoso**.

4. Dans la zone **Description** , entrez **un projet SharePoint pour la création de colonnes de site**.

5. Sélectionnez l’onglet **ressources** , puis cliquez sur le bouton **nouveau** .

     La boîte de dialogue **Ajouter un nouvel élément** multimédia s’ouvre.

6. Dans la liste **type** , choisissez **Microsoft. VisualStudio. ProjectTemplate**.

    > [!NOTE]
    > Cette valeur correspond à l' `ProjectTemplate` élément dans le fichier extension. vsixmanifest. Cet élément identifie le sous-dossier du package VSIX qui contient le modèle de projet. Pour plus d’informations, consultez l' [élément ProjectTemplate (schéma VSX)](/previous-versions/visualstudio/visual-studio-2010/dd393735\(v\=vs.100\)).

7. Dans la liste **source** , choisissez **un projet dans la solution actuelle**.

8. Dans la liste **projet** , choisissez **SiteColumnProjectTemplate**, puis le bouton **OK** .

9. Cliquez à nouveau sur le bouton **nouveau** .

     La boîte de dialogue **Ajouter un nouvel élément** multimédia s’ouvre.

10. Dans la liste **type** , choisissez **Microsoft. VisualStudio. MEFComponent**.

    > [!NOTE]
    > Cette valeur correspond à l' `MefComponent` élément dans le fichier extension. vsixmanifest. Cet élément spécifie le nom d’un assembly d’extension dans le package VSIX. Pour plus d’informations, consultez [MefComponent, élément (schéma VSX)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\)).

11. Dans la liste **source** , choisissez **un projet dans la solution actuelle**.

12. Dans la liste **projet** , choisissez **projectItemTypeDefinition**, puis cliquez sur le bouton **OK** .

13. Dans la barre de menus, choisissez **générer**  >  **générer la solution**, puis assurez-vous que le projet se compile sans erreur.

## <a name="test-the-project-template"></a>Tester le modèle de projet
 Vous êtes maintenant prêt à tester le modèle de projet. Tout d’abord, commencez à déboguer la solution SiteColumnProjectItem dans l’instance expérimentale de Visual Studio. Ensuite, testez le projet de **colonne de site** dans l’instance expérimentale de Visual Studio. Enfin, générez et exécutez le projet SharePoint pour vérifier que la colonne de site fonctionne comme prévu.

#### <a name="to-start-debugging-the-solution"></a>Pour démarrer le débogage de la solution

1. Redémarrez Visual Studio avec les informations d’identification d’administration, puis ouvrez la solution SiteColumnProjectItem.

2. Dans le fichier de code SiteColumnProjectItemTypeProvider, ajoutez un point d’arrêt à la première ligne de code dans la méthode, puis appuyez sur `InitializeType` la touche **F5** pour démarrer le débogage.

     Visual Studio installe l’extension sur%UserProfile%\AppData\Local\Microsoft\VisualStudio\10.0Exp\Extensions\Contoso\Site Column\1.0 et démarre une instance expérimentale de Visual Studio. Vous allez tester l’élément de projet dans cette instance de Visual Studio.

#### <a name="to-test-the-project-in-visual-studio"></a>Pour tester le projet dans Visual Studio

1. Dans l’instance expérimentale de Visual Studio, dans la barre de menus, choisissez **fichier**  >  **nouveau**  >  **projet**.

2. Développez le nœud **Visual C#** ou **Visual Basic** (selon la langue prise en charge par votre modèle de projet), développez le nœud **SharePoint** , puis choisissez le nœud **2010** .

3. Dans la liste des modèles de projet, choisissez le modèle **colonne de site** .

4. Dans la zone **nom** , entrez **SiteColumnTest** , puis choisissez le bouton **OK** .

     Dans **Explorateur de solutions**, un nouveau projet s’affiche avec un élément de projet nommé **champ1**.

5. Vérifiez que le code de l’autre instance de Visual Studio s’arrête sur le point d’arrêt que vous avez défini précédemment dans la méthode, puis appuyez sur `InitializeType` la touche **F5** pour continuer à déboguer le projet.

6. Dans **Explorateur de solutions**, choisissez le nœud **champ1** , puis appuyez sur la touche **F4** .

     La fenêtre **Propriétés** apparaît.

7. Dans la liste Propriétés, vérifiez que la **propriété exemple** de propriété s’affiche.

#### <a name="to-test-the-site-column-in-sharepoint"></a>Pour tester la colonne de site dans SharePoint

1. Dans **Explorateur de solutions**, choisissez le nœud **SiteColumnTest** .

2. Dans la fenêtre **Propriétés** , dans la zone de texte située en regard de la propriété **URL du site** , entrez **http://localhost** .

     Cette étape spécifie le site SharePoint local sur l’ordinateur de développement que vous souhaitez utiliser pour le débogage.

    > [!NOTE]
    > La propriété **URL du site** est vide par défaut, car le modèle de projet colonne de site ne fournit pas d’Assistant permettant de collecter cette valeur lors de la création du projet. Pour savoir comment ajouter un assistant qui demande au développeur de cette valeur, puis configure cette propriété dans le nouveau projet, consultez [procédure pas à pas : création d’un élément de projet colonne de site avec un modèle de projet, deuxième partie](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md).

3. Choisissez la touche **F5**.

     La colonne de site est empaquetée et déployée sur le site SharePoint spécifié dans la propriété **URL du site** du projet. Le navigateur Web s’ouvre sur la page par défaut de ce site.

    > [!NOTE]
    > Si la boîte de dialogue **débogage de script désactivé** s’affiche, choisissez le bouton **Oui** pour continuer à déboguer le projet.

4. Dans le menu **actions du site** , choisissez Paramètres du **site**.

5. Sur la page **paramètres du site** , sous la liste **galeries** , choisissez le lien colonnes de **site** .

6. Dans la liste des colonnes de site, vérifiez qu’un groupe de **colonnes personnalisé** contient une colonne nommée **SiteColumnTest**.

7. Fermez le navigateur web.

## <a name="clean-up-the-development-computer"></a>Nettoyer l’ordinateur de développement
 Une fois que vous avez fini de tester le projet, supprimez le modèle de projet de l’instance expérimentale de Visual Studio.

#### <a name="to-clean-up-the-development-computer"></a>Pour nettoyer l’ordinateur de développement

1. Dans l’instance expérimentale de Visual Studio, dans la barre de menus, choisissez **Outils**  >  **extensions et mises à jour**.

     La boîte de dialogue **Extensions et mises à jour** s’ouvre.

2. Dans la liste des extensions, choisissez l’extension de **colonne de site** , puis cliquez sur le bouton **désinstaller** .

3. Dans la boîte de dialogue qui s’affiche, choisissez le bouton **Oui** pour confirmer que vous souhaitez désinstaller l’extension.

4. Cliquez sur le bouton **Fermer** pour terminer la désinstallation.

5. Fermez les deux instances de Visual Studio (l’instance expérimentale et l’instance de Visual Studio dans laquelle la solution SiteColumnProjectItem est ouverte).

## <a name="next-steps"></a>Étapes suivantes
 Après avoir effectué cette procédure pas à pas, vous pouvez ajouter un assistant au modèle de projet. Lorsqu’un utilisateur crée un projet de colonne de site, l’Assistant demande à l’utilisateur l’URL du site à utiliser pour le débogage et indique si la nouvelle solution est bac à sable (sandbox) et si l’Assistant Configure le nouveau projet avec ces informations. L’Assistant collecte également des informations sur la colonne (telles que le type de base et le groupe dans lequel répertorier la colonne dans la Galerie de colonnes de site) et ajoute ces informations au fichier *Elements.xml* dans le nouveau projet. Pour plus d’informations, consultez [procédure pas à pas : création d’un élément de projet colonne de site avec un modèle de projet, partie 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md).

## <a name="see-also"></a>Voir aussi

- [Procédure pas à pas : création d’un élément de projet colonne de site avec un modèle de projet, partie 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)
- [Définir des types d’éléments de projet SharePoint personnalisés](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [Créer des modèles d’élément et des modèles de projet pour les éléments de projet SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)
- [Enregistrer des données dans les extensions du système de projet SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)
- [Associer des données personnalisées à des extensions d’outils SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)