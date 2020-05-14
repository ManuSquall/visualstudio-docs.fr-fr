---
title: Élément TemplateData (Modèles de studio visuel) Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#TemplateData
helpviewer_keywords:
- TemplateData element [Visual Studio project templates]
ms.assetid: db17ec9b-bfdf-46b1-bbe7-5ccc140056e2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f3ce0226286e8cc4623b66c043eb7bd376597118
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699190"
---
# <a name="templatedata-element-visual-studio-templates"></a>TemplateData, élément (modèles Visual Studio)
Définit la catégorie du modèle et comment il s’affiche dans la boîte de dialogue **Nouveau projet** ou **Ajouter un nouvel élément** .

 \<VSTemplate> \<TemplateData>

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
 Aucun.

### <a name="child-elements"></a>Éléments enfants

| Élément | Description |
| - | - |
| [Nom](../extensibility/name-element-visual-studio-templates.md) | Élément requis.<br /><br /> Spécifie le nom du modèle tel qu’il apparaît dans le **nouveau projet** ou la boîte de dialogue Add **New Item.** |
| [Description](../extensibility/description-element-visual-studio-templates.md) | Élément requis.<br /><br /> Spécifie la description du modèle tel qu’il apparaît dans le **nouveau projet** ou la boîte de dialogue Add **New Item.** |
| [Icône](../extensibility/icon-element-visual-studio-templates.md) | Élément requis.<br /><br /> Spécifie le chemin et le nom de fichier du fichier d’image qui sert d’icône, qui apparaît soit dans le **nouveau projet** ou la boîte de dialogue **Add New Item,** pour le modèle. |
| [ProjectType](../extensibility/projecttype-element-visual-studio-templates.md) | Élément requis.<br /><br /> Catégorise le modèle de projet de sorte qu’il apparaisse sous le groupe spécifié dans la boîte de dialogue **du nouveau projet.** |
| [ProjectSubType](../extensibility/projectsubtype-element-visual-studio-templates.md) | Élément facultatif.<br /><br /> Classifie le modèle de projet de sorte qu’il apparaisse sous la sous-catégorie spécifiée dans la boîte de dialogue **du nouveau projet.** |
| [TemplateID](../extensibility/templateid-element-visual-studio-templates.md) | Élément facultatif.<br /><br /> Spécifie l’ID du modèle. |
| [TemplateGroupID](../extensibility/templategroupid-element-visual-studio-templates.md) | Élément facultatif.<br /><br /> Spécifie l’ID de groupe de modèle. |
| [SortOrder](../extensibility/sortorder-element-visual-studio-templates.md) | Élément facultatif.<br /><br /> Spécifie une valeur qui est utilisée pour arranger le modèle, entre autres modèles dans la même catégorie, comme il apparaît dans le **nouveau projet** ou ajouter la boîte de dialogue **Nouvel Élément.** |
| [CreateNewFolder](../extensibility/createnewfolder-element-visual-studio-templates.md) | Élément facultatif.<br /><br /> Précise si un dossier contenant est créé sur l’instantanéisation du projet. |
| [Nom par défaut](../extensibility/defaultname-element-visual-studio-templates.md) | Élément facultatif.<br /><br /> Spécifie le nom que le système de projet Visual Studio générera pour le projet ou l’élément lorsqu’il sera créé. |
| [ProvideDefaultName](../extensibility/providedefaultname-element-visual-studio-templates.md) | Élément facultatif.<br /><br /> Précise si le système de projet Visual Studio générera le nom par défaut d’un projet ou d’un élément lorsqu’il sera créé. |
| [PromptForSaveOnCreation](../extensibility/promptforsaveoncreation-element-visual-studio-templates.md) | Élément facultatif.<br /><br /> Précise si le projet peut être créé comme un projet temporaire (Visual Studio 2017 seulement). |
| [EnableLocationBrowseButton](../extensibility/enablelocationbrowsebutton-element-visual-studio-templates.md) | Élément facultatif.<br /><br /> Précise si le bouton **Browse** est disponible dans la boîte de dialogue **Du nouveau projet,** afin que les utilisateurs puissent facilement modifier l’annuaire par défaut où un nouveau projet est enregistré. |
| [Cachés](../extensibility/hidden-element-visual-studio-templates.md) | Élément facultatif.<br /><br /> Précise si le modèle apparaît dans le **nouveau projet** ou ajouter la boîte de dialogue **Nouvel Élément.** |
| [NumberOfParentCategoriesToRollUp](../extensibility/numberofparentcategoriestorollup-visual-studio-templates.md) | Élément facultatif.<br /><br /> Spécifie le nombre de catégories de parents qui afficheront le modèle dans la boîte de dialogue **du nouveau projet.** |
| [LocationFieldMRUPrefix](../extensibility/locationfieldmruprefix-element-visual-studio-templates.md) | Élément facultatif. |
| [LocationField](../extensibility/locationfield-element-visual-studio-project-templates.md) | Élément facultatif.<br /><br /> Précise si la boîte de texte **de localisation** de la boîte de dialogue Du **nouveau projet** est activée, désactivée ou cachée pour le modèle de projet. |
| [RequiredFrameworkVersion](../extensibility/requiredframeworkversion-element-visual-studio-templates.md) | Élément facultatif.<br /><br /> Utilisez cet élément si le modèle ne prend en charge qu’une version minimale spécifique, et des versions ultérieures, le cas échéant, du cadre .NET. |
| [SupportsMasterPage](../extensibility/supportsmasterpage-element-visual-studio-templates.md) | Élément facultatif.<br /><br /> Précise si le modèle prend en charge une page maîtresse pour les projets Web. |
| [SupportsCodeSeparation](../extensibility/supportscodeseparation-element-visual-studio-templates.md) | Élément facultatif.<br /><br /> Précise si le modèle prend en charge la séparation du code, ou le modèle de page de code-derrière, pour les projets Web. |
| [SupportsLanguageDropDown](../extensibility/supportslanguagedropdown-element-visual-studio-templates.md) | Élément facultatif.<br /><br /> Précise si le modèle est identique pour plusieurs langues, et si **l’option langue** est disponible à partir de la boîte de dialogue **du nouveau projet.** |
| [TargetPlatformName](../extensibility/targetplatformname-element-visual-studio-templates.md) | Élément facultatif.<br /><br /> Spécifie la plateforme ciblée par le modèle de projet. Cet élément précise qu’un modèle de [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] projet est utilisé pour créer des applications. |

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[VSTemplate](../extensibility/vstemplate-element-visual-studio-templates.md)|Élément requis.<br /><br /> Contient toutes les métadonnées pour le modèle de projet, le modèle d’élément ou le kit de démarrage.|

## <a name="remarks"></a>Notes
 `TemplateData`est un élément nécessaire.

 Si vous n’incluez pas un élément facultatif, la valeur par défaut de cet élément est utilisée.

## <a name="example"></a>Exemple
 L’exemple suivant montre les métadonnées [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] d’un modèle de projet pour une application.

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
