---
title: ProjectType Element (Visual Studio Templates) Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectType
helpviewer_keywords:
- ProjectType element [Visual Studio project templates]
ms.assetid: ccf9d83f-c7f3-49c7-a31f-e1f22bec004c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d794bd5e81e77a892b5a3be38ff73ab805582dd7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701807"
---
# <a name="projecttype-element-visual-studio-templates"></a>Élément ProjectType (modèles Visual Studio)
Catégorise le modèle de projet de sorte qu’il apparaisse sous le groupe spécifié dans la **boîte de** dialogue New Project ou Ajouter de nouveaux **éléments.**

> [!WARNING]
> Les modèles de projet sont pris en charge pour le CMD à partir de Visual Studio 2012. Ils ne sont pas pris en charge pour le C dans Visual Studio 2010 et les versions précédentes.

 \<VSTemplate> \<TemplateData> \<ProjectType>

## <a name="syntax"></a>Syntaxe

```xml
<ProjectType> CSharp/VisualBasic/VC/Web </ProjectType>
```

## <a name="attributes-and-elements"></a>Attributs et éléments
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.

### <a name="attributes"></a>Attributs
 Aucun.

### <a name="child-elements"></a>Éléments enfants
 Aucun.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Définit la catégorie du modèle et comment il s’affiche dans la boîte de dialogue **Nouveau projet** ou **Ajouter un nouvel élément** .|

## <a name="text-value"></a>Valeur texte
 Une valeur texte est requise.

 Cette valeur spécifie le type de projet que le modèle créera et doit contenir l’une des valeurs suivantes :

- `CSharp`: Spécifie que [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] le modèle crée un projet ou un élément.

- `VisualBasic`: Spécifie que [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] le modèle crée un projet ou un élément.

- `Web`: Spécifie que le modèle crée un projet Web ou un élément. Si `ProjectType` l’élément contient cette valeur, la langue du projet ou de l’élément est définie dans [l’élément ProjectSubType (Visual Studio Templates)](../extensibility/projectsubtype-element-visual-studio-templates.md).

## <a name="remarks"></a>Notes
 `ProjectType` est un élément enfant obligatoire de `TemplateData`.

 La valeur `ProjectType` de l’élément spécifie où le modèle est situé dans la boîte de dialogue **Du nouveau projet** ou ajouter un nouvel **élément.** Par exemple, un `ProjectType` modèle `CSharp` d’une valeur de apparaît sous le nœud **Visual C dans** la boîte de dialogue du nouveau **projet.**

 Un sous-type de modèle peut être spécifié à l’aide de [l’élément ProjectSubType.](../extensibility/projectsubtype-element-visual-studio-templates.md)

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
- [Référence de schéma de modèle de studio visuel](../extensibility/visual-studio-template-schema-reference.md)
- [Créer des modèles de projet et d’élément](../ide/creating-project-and-item-templates.md)
- [Élément ProjectSubType (modèles Visual Studio)](../extensibility/projectsubtype-element-visual-studio-templates.md)
