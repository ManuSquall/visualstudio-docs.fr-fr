---
title: EnableLocationBrowseButton, élément (modèles Visual Studio)
titleSuffix: ''
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
ms.openlocfilehash: 1b04152864b77c33e3821e4e1ba415cc4fa9f502
ms.sourcegitcommit: 2a201c93ed526b0f7e5848657500f1111b08ac2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2020
ms.locfileid: "89742995"
---
# <a name="enablelocationbrowsebutton-element-visual-studio-templates"></a>Élément EnableLocationBrowseButton (modèles Visual Studio)
Spécifie si le bouton **Parcourir** est disponible dans la boîte de dialogue **nouveau projet** , afin que les utilisateurs puissent facilement modifier le répertoire par défaut où un nouveau projet est enregistré.

 \<VSTemplate> \<TemplateData>
 \<EnableLocationBrowseButton>

## <a name="syntax"></a>Syntaxe

```xml
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

 Le texte doit être `true` ou `false` , indiquant s’il faut ou non afficher le bouton **Parcourir** dans la boîte de dialogue **nouveau projet** .

## <a name="remarks"></a>Notes
 `EnableLocationBrowseButton` est un élément facultatif. La valeur par défaut est `true` , qui affiche le bouton **Parcourir** dans la boîte de dialogue **nouveau projet** .

 Dans la boîte de dialogue **nouveau projet** , la zone de texte **emplacement** spécifie le répertoire dans lequel un nouveau projet est enregistré. Le bouton **Parcourir** vous permet de modifier ce répertoire en affichant la boîte de dialogue **emplacement du projet** , qui vous permet de naviguer facilement vers un autre répertoire disponible à partir de votre ordinateur, puis de le choisir comme répertoire dans lequel le nouveau projet est enregistré.

## <a name="example"></a>Exemple
 L’exemple suivant illustre les métadonnées d’une [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] application Windows.

```xml
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
- [Référence du schéma de modèle Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Création de modèles de projet et d’élément](../ide/creating-project-and-item-templates.md)
