---
title: Élément NumberOfParentCategoriesToRollUp (modèles)
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#NumberOfParentCategoriesToRollUp
helpviewer_keywords:
- NumberOfParentCategoriesToRollUp element [Visual Studio Templates]
- <NumberOfParentCategoriesToRollUp> element [Visual Studio Templates]
ms.assetid: 6f9d36f5-ae23-4a92-8132-b11799e2c21a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6d53467e01b9485917f90a570d65a932b55baab4
ms.sourcegitcommit: 13ab9a5ab039b070b9cd9251d0b83dd216477203
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66177642"
---
# <a name="numberofparentcategoriestorollup-element-visual-studio-templates"></a>Élément NumberOfParentCategoriesToRollUp (modèles Visual Studio)
Spécifie le nombre de catégories parentes qui afficheront le modèle dans le **nouveau projet** boîte de dialogue.

 \<VSTemplate> \<TemplateData> \<NumberOfParentCategoriesToRollUp>

## <a name="syntax"></a>Syntaxe

```xml
<NumberOfParentCategoriesToRollUp>
1
</NumberOfParentCategoriesToRollUp>
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
 Un `integer` valeur est requise.

 Cette valeur spécifie le nombre de catégories parentes qui afficheront le modèle dans le **nouveau projet** boîte de dialogue.

## <a name="remarks"></a>Notes
 `NumberOfParentCategoriesToRollUp` est un élément facultatif.

## <a name="example"></a>Exemple
 Cet exemple illustre les métadonnées d’un [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] application de Windows. Si un modèle avec ces métadonnées est placé deux niveaux de dossiers sous le niveau supérieur [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] nœud, le modèle s’affiche dans le nœud de niveau supérieur dans le **nouveau projet** boîte de dialogue. Si le `NumberOfParentCategoriesToRollUp` n’est pas défini, le modèle apparaît seulement dans le nœud dans lequel il se trouve physiquement.

```xml
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic starter kit</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <NumberOfParentCategoriesToRollUp>2</NumberOfParentCategoriesToRollUp>
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
- [Informations de référence sur les schémas de modèles Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Création de modèles de projets et d’éléments](../ide/creating-project-and-item-templates.md)
