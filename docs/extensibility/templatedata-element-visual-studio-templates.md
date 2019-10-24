---
title: Élément TemplateData (modèles Visual Studio) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#TemplateData
helpviewer_keywords:
- TemplateData element [Visual Studio project templates]
ms.assetid: db17ec9b-bfdf-46b1-bbe7-5ccc140056e2
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b122857a4d916379c070e923ed0753b01287f08b
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72718852"
---
# <a name="templatedata-element-visual-studio-templates"></a>TemplateData, élément (modèles Visual Studio)
Définit la catégorie du modèle et comment il s’affiche dans la boîte de dialogue **Nouveau projet** ou **Ajouter un nouvel élément** .

 \<VSTemplate > \<TemplateData >

## <a name="syntax"></a>Syntaxe

```
<TemplateData>
    <Name> ... </Name>
    <Description> ... </Description>
    <Icon> ... </Icon>
    <ProjectType> ... </ProjectType>
    ...
</TemplateData>
```

## <a name="attributes-and-elements"></a>Attributs et éléments
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.

### <a name="attributes"></a>Attributs
 Aucun(e).

### <a name="child-elements"></a>Éléments enfants

| Élément | Description |
| - | - |
| [Nom](../extensibility/name-element-visual-studio-templates.md) | Élément requis.<br /><br /> Spécifie le nom du modèle tel qu’il apparaît dans la boîte de dialogue **nouveau projet** ou **Ajouter un nouvel élément** . |
| [Description](../extensibility/description-element-visual-studio-templates.md) | Élément requis.<br /><br /> Spécifie la description du modèle telle qu’elle apparaît dans la boîte de dialogue **nouveau projet** ou **Ajouter un nouvel élément** . |
| [Icône](../extensibility/icon-element-visual-studio-templates.md) | Élément requis.<br /><br /> Spécifie le chemin d’accès et le nom du fichier image qui sert d’icône, qui apparaît dans la boîte de dialogue **nouveau projet** ou **Ajouter un nouvel élément** , pour le modèle. |
| [ProjectType](../extensibility/projecttype-element-visual-studio-templates.md) | Élément requis.<br /><br /> Classe le modèle de projet de manière à ce qu’il apparaisse sous le groupe spécifié dans la boîte de dialogue **nouveau projet** . |
| [ProjectSubType](../extensibility/projectsubtype-element-visual-studio-templates.md) | Élément facultatif.<br /><br /> Classe le modèle de projet afin qu’il apparaisse sous la sous-catégorie spécifiée dans la boîte de dialogue **nouveau projet** . |
| [TemplateID](../extensibility/templateid-element-visual-studio-templates.md) | Élément facultatif.<br /><br /> Spécifie l’ID du modèle. |
| [TemplateGroupID](../extensibility/templategroupid-element-visual-studio-templates.md) | Élément facultatif.<br /><br /> Spécifie l’ID de groupe de modèles. |
| [SortOrder](../extensibility/sortorder-element-visual-studio-templates.md) | Élément facultatif.<br /><br /> Spécifie une valeur qui est utilisée pour réorganiser le modèle, parmi d’autres modèles de la même catégorie, tel qu’il apparaît dans la boîte de dialogue **nouveau projet** ou **Ajouter un nouvel élément** . |
| [CreateNewFolder](../extensibility/createnewfolder-element-visual-studio-templates.md) | Élément facultatif.<br /><br /> Spécifie si un dossier conteneur est créé lors de l’instanciation du projet. |
| [DefaultName](../extensibility/defaultname-element-visual-studio-templates.md) | Élément facultatif.<br /><br /> Spécifie le nom que le système de projet Visual Studio va générer pour le projet ou l’élément lors de sa création. |
| [ProvideDefaultName](../extensibility/providedefaultname-element-visual-studio-templates.md) | Élément facultatif.<br /><br /> Spécifie si le système de projet Visual Studio doit générer le nom par défaut d’un projet ou d’un élément lors de sa création. |
| [PromptForSaveOnCreation](../extensibility/promptforsaveoncreation-element-visual-studio-templates.md) | Élément facultatif.<br /><br /> Spécifie si le projet peut être créé en tant que projet temporaire (Visual Studio 2017 uniquement). |
| [EnableLocationBrowseButton](../extensibility/enablelocationbrowsebutton-element-visual-studio-templates.md) | Élément facultatif.<br /><br /> Spécifie si le bouton **Parcourir** est disponible dans la boîte de dialogue **nouveau projet** , afin que les utilisateurs puissent facilement modifier le répertoire par défaut où un nouveau projet est enregistré. |
| [Masquer](../extensibility/hidden-element-visual-studio-templates.md) | Élément facultatif.<br /><br /> Spécifie si le modèle s’affiche dans la boîte de dialogue **nouveau projet** ou **Ajouter un nouvel élément** . |
| [NumberOfParentCategoriesToRollUp](../extensibility/numberofparentcategoriestorollup-visual-studio-templates.md) | Élément facultatif.<br /><br /> Spécifie le nombre de catégories parentes qui afficheront le modèle dans la boîte de dialogue **nouveau projet** . |
| [LocationFieldMRUPrefix](../extensibility/locationfieldmruprefix-element-visual-studio-templates.md) | Élément facultatif. |
| [LocationField](../extensibility/locationfield-element-visual-studio-project-templates.md) | Élément facultatif.<br /><br /> Spécifie si la zone de texte **emplacement** dans la boîte de dialogue **nouveau projet** est activée, désactivée ou masquée pour le modèle de projet. |
| [RequiredFrameworkVersion](../extensibility/requiredframeworkversion-element-visual-studio-templates.md) | Élément facultatif.<br /><br /> Utilisez cet élément si le modèle prend uniquement en charge une version minimale spécifique et, le cas échéant, les versions ultérieures du .NET Framework. |
| [SupportsMasterPage](../extensibility/supportsmasterpage-element-visual-studio-templates.md) | Élément facultatif.<br /><br /> Spécifie si le modèle prend en charge une page maître pour les projets Web. |
| [SupportsCodeSeparation](../extensibility/supportscodeseparation-element-visual-studio-templates.md) | Élément facultatif.<br /><br /> Spécifie si le modèle prend en charge la séparation de code, ou le modèle de page code-behind, pour les projets Web. |
| [SupportsLanguageDropDown](../extensibility/supportslanguagedropdown-element-visual-studio-templates.md) | Élément facultatif.<br /><br /> Spécifie si le modèle est identique pour plusieurs langues et si l’option **langue** est disponible dans la boîte de dialogue **nouveau projet** . |
| [TargetPlatformName](../extensibility/targetplatformname-element-visual-studio-templates.md) | Élément facultatif.<br /><br /> Spécifie la plateforme ciblée par le modèle de projet. Cet élément spécifie qu’un modèle de projet est utilisé pour créer des [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] des applications. |

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Lit](../extensibility/vstemplate-element-visual-studio-templates.md)|Élément requis.<br /><br /> Contient toutes les métadonnées pour le modèle de projet, le modèle d’élément ou le starter kit.|

## <a name="remarks"></a>Notes
 `TemplateData` est un élément obligatoire.

 Si vous n’incluez pas d’élément facultatif, la valeur par défaut de cet élément est utilisée.

## <a name="example"></a>Exemple
 L’exemple suivant montre les métadonnées d’un modèle de projet pour une application [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)].

```
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic starter kit</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
    </TemplateData>
    <TemplateContent>
        <Project File="MyStarterKit.csproj">
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
- [Référence du schéma de modèle Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Création de modèles de projet et d’élément](../ide/creating-project-and-item-templates.md)