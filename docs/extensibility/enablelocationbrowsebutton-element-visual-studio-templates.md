---
title: EnableLocationBrowseButton Element (Visual Studio Templates) Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#EnableLocationBrowseButton
helpviewer_keywords:
- EnableLocationBrowseButton [Visual Studio project templates]
ms.assetid: a12d10d8-af49-482a-af77-e084fd07a47d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 263157d5c6fefc208f28caa55475ba329a0d230f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711989"
---
# <a name="enablelocationbrowsebutton-element-visual-studio-templates"></a>Élément EnableLocationBrowseButton (modèles Visual Studio)
Précise si le bouton **Browse** est disponible dans la boîte de dialogue **Du nouveau projet,** afin que les utilisateurs puissent facilement modifier l’annuaire par défaut où un nouveau projet est enregistré.

 \<VSTemplate> \<TemplateData> \<EnableLocationBrowseButton>

## <a name="syntax"></a>Syntaxe

```
<EnableLocationBrowseButton> true/false </EnableLocationBrowseButton>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Élément requis.<br /><br /> Définit la catégorie du modèle et comment il s’affiche dans la boîte de dialogue **Nouveau projet** ou **Ajouter un nouvel élément** .|

## <a name="text-value"></a>Valeur texte
 Une valeur texte est requise.

 Le texte doit `true` `false`être soit ou , indiquant si oui ou non d’afficher le bouton **Parcourir** sur la boîte de dialogue **Du nouveau projet.**

## <a name="remarks"></a>Notes
 `EnableLocationBrowseButton` est un élément facultatif. La valeur `true`par défaut est , qui affiche le bouton **Parcourir** dans la boîte de dialogue **New Project.**

 Dans la boîte de dialogue **New Project,** la boîte de texte **De localisation** spécifie l’annuaire où un nouveau projet est sauvegardé. Le bouton **Parcourir** vous aide à modifier ce répertoire en affichant la boîte de dialogue **Project Location,** qui vous permet de naviguer facilement vers un répertoire différent qui est disponible à partir de votre ordinateur, puis de le choisir comme répertoire où le nouveau projet est enregistré.

## <a name="example"></a>Exemple
 L’exemple suivant illustre les métadonnées d’une [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] application Windows.

```
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic starter kit</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <EnableLocationBrowseButton>false</EnableLocationBrowseButton>
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
- [Création de modèles de projets et d’objets](../ide/creating-project-and-item-templates.md)
