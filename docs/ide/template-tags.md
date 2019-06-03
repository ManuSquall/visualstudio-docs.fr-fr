---
title: Ajouter ou modifier des balises sur des modèles de projet
ms.date: 04/30/2019
author: minsa110
ms.author: somin
manager: jillfra
ms.topic: reference
helpviewer_keywords:
- item templates, updating
- Visual Studio templates, updating
- project templates, updating
- updating templates [Visual Studio]
- template tagging, updating
- template tags, updating
ms.openlocfilehash: 4a5113fa7f420d58892e2737ec9196422486490e
ms.sourcegitcommit: cd21b38eefdea2cdefb53e68e7a30b868e78dd6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/22/2019
ms.locfileid: "66038625"
---
# <a name="add-tags-to-project-templates"></a>Ajouter des balises à des modèles de projet

À compter de [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/) version 16.1 préversion 2, vous pouvez ajouter des balises de langage, de plateforme et de type de projet à vos modèles de projet. Les balises sont utilisées à deux emplacements dans la boîte de dialogue Nouveau projet :

- Les balises s’affichent sous la description du modèle

   ![Modèle de projet avec des balises dans la boîte de dialogue Nouveau projet](media/npd-item-with-template-tags.png)

- Les balises permettent de filtrer un modèle et d’y effectuer des recherches

   ![Recherche et filtrage dans la boîte de dialogue Nouveau projet](media/npd-search-and-filter.png)

Vous pouvez ajouter des balises en mettant à jour le fichier XML *.vstemplate* à l’aide des balises de modèle intégrées à Visual Studio ou en créant des balises de modèle personnalisées. Les balises de modèle s’affichent uniquement dans la boîte de dialogue Nouveau projet de Visual Studio 2019. Elles n’affectent pas le rendu du modèle dans les versions précédentes de Visual Studio.

## <a name="add-or-edit-tags"></a>Ajouter ou modifier des balises

Vous pouvez ajouter ou modifier des balises dans le fichier XML *.vstemplate* de votre modèle de projet lorsque vous :

* [Créez un modèle de projet](/visualstudio/ide/how-to-create-project-templates) en utilisant l’Assistant Exportation de modèle

* [Mettez à jour des modèles de projet existants](/visualstudio/ide/how-to-update-existing-templates)

* [Créez un modèle de projet VSIX](/visualstudio/extensibility/getting-started-with-the-vsix-project-template)

## <a name="syntax"></a>Syntaxe

```xml
<LanguageTag> Language Name </LanguageTag>
<PlatformTag> Platform Name </PlatformTag>
<ProjectTypeTag> Project Type </ProjectTypeTag>
```

## <a name="attributes"></a>Attributs

Les attributs suivants sont facultatifs et destinés aux utilisateurs expérimentés.

|Attribut|Description|
|---------------|-----------------|
|`Package`|Un GUID qui spécifie l’ID du package Visual Studio.|
|`ID`|Spécifie l’ID de la ressource Visual Studio.|

Syntaxe :

```xml
<LanguageTag Package="{PackageID}" ID="ResourceID" />
<PlatformTag Package="{PackageID}" ID="ResourceID" />
<ProjectTypeTag Package="{PackageID}" ID="ResourceID" />
```

## <a name="elements"></a>Éléments

### <a name="child-elements"></a>Éléments enfants

Aucun.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|(Requis) Définit la catégorie du modèle et comment il s’affiche dans la boîte de dialogue **Nouveau projet** ou **Ajouter un nouvel élément**.|

## <a name="text-value"></a>Valeur texte

Une valeur texte est requise, sauf si les attributs `Package` et `ID` sont utilisés.

Le texte indique le nom du modèle.

## <a name="built-in-tags"></a>Balises intégrées

Visual Studio propose une liste de balises intégrées qui, lorsqu’elles sont ajoutées, affichent une ressource localisée. Voici une liste des balises intégrées et leurs valeurs correspondantes entre parenthèses.

| Langue | Plateforme | Type de projet |
| -- | -- | -- |
| C++ (`cpp`) | Android (`android`) | Cloud (`cloud`) |
| C# (`csharp`) | Azure (`azure`) | Console (`console`) |
| F# (`fsharp`) | iOS (`ios`) | Desktop (`desktop`) |
| Java (`java`) | Linux (`linux`) | Extensions (`extension`) |
| JavaScript (`javascript`) | macOS (`macos`) | Jeux (`games`) |
| Python (`python`) | tvOS (`tvos`) | IoT (`iot`) |
| Langage de requête (`querylanguage`) | Windows (`windows`) | Bibliothèque (`library`) |
| TypeScript (`typescript`) | Xbox (`xbox`) | Machine Learning (`machinelearning`) |
| Visual Basic (`visualbasic`) | | Mobile (`mobile`) |
| | | Office (`office`) |
| | | Autres (`other`) |
| | | Service (`service`) |
| | | Test (`test`) |
| | | UWP (`uwp`) |
| | | Web (`web`) |

## <a name="example"></a>Exemple

L’exemple suivant montre les métadonnées d’un modèle de projet pour une application Visual C#.

```xml
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic template</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <LanguageTag>C#</LanguageTag>
        <PlatformTag>windows</PlatformTag>
        <PlatformTag>linux</PlatformTag>
        <PlatformTag>My Platform</PlatformTag>
        <ProjectTypeTag>console</ProjectTypeTag>
        <ProjectTypeTag>desktop</ProjectTypeTag>
    </TemplateData>
    <TemplateContent>
        <Project File="MyTemplate.csproj">
            <ProjectItem>Form1.cs<ProjectItem>
            <ProjectItem>Form1.Designer.cs</ProjectItem>
            <ProjectItem>Program.cs</ProjectItem>
            <ProjectItem>Properties\AssemblyInfo.cs</ProjectItem>
            <ProjectItem>Properties\Resources.resx</ProjectItem>
            <ProjectItem>Properties\Resources.Designer.cs</ProjectItem>
            <ProjectItem>Properties\Settings.settings</ProjectItem>
            <ProjectItem>Properties\Settings.Designer.cs</ProjectItem>
        </Project>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur les schémas de modèles Visual Studio](/visualstudio/extensibility/visual-studio-template-schema-reference)
- [Création de modèles de projets et d’éléments](/visualstudio/ide/creating-project-and-item-templates)
- [Personnaliser des modèles de projet et d’élément](/visualstudio/ide/customizing-project-and-item-templates)
- [Bien démarrer avec le modèle de projet VSIX](/visualstudio/extensibility/getting-started-with-the-vsix-project-template)