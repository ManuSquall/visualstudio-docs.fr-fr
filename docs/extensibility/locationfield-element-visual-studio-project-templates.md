---
title: LocationField, élément (modèles de projet Visual Studio)
titleSuffix: ''
description: En savoir plus sur l’élément LocationField et sur la façon dont il spécifie si la zone de texte emplacement de la boîte de dialogue Nouveau projet est activée, désactivée ou masquée pour le modèle de projet.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#LocationField
helpviewer_keywords:
- LocationField element [Visual Studio project templates]
ms.assetid: 6aaaa155-6ce0-4f7f-aa50-8d63d7a7c992
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: cbd0d6ee6ede29be35437125f614512ff3bbeab3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99915177"
---
# <a name="locationfield-element-visual-studio-project-templates"></a>Élément LocationField (modèles de projet Visual Studio)
Spécifie si la zone de texte **emplacement** dans la boîte de dialogue **nouveau projet** est activée, désactivée ou masquée pour le modèle de projet.

 \<VSTemplate> \<TemplateData>
 \<LocationField>

## <a name="syntax"></a>Syntaxe

```
<LocationField> Enabled/Disabled/Hidden </LocationField>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Élément requis.<br /><br /> Classe le modèle dans une catégorie et définit la manière dont il s’affiche dans le **nouveau projet**.|

## <a name="text-value"></a>Valeur texte
 Une valeur texte est requise.

 Les valeurs de texte valides sont :

- `Enabled`, qui spécifie que la zone **emplacement** de la boîte de dialogue **nouveau projet** est activée.

- `Disabled`, qui spécifie que la zone **emplacement** de la boîte de dialogue **nouveau projet** est désactivée.

- `Hidden`, qui spécifie que la zone **emplacement** de la boîte de dialogue **nouveau projet** est masquée.

## <a name="remarks"></a>Notes
 La valeur par défaut est `Enabled`.

 La zone de texte **emplacement** dans la boîte de dialogue **nouveau projet** permet aux utilisateurs de modifier le répertoire par défaut dans lequel les nouveaux projets sont enregistrés.

 La valeur spécifiée dans l' `Location` élément est honorée uniquement par la boîte de dialogue si le système de projet sous-jacent le prend en charge.

## <a name="example"></a>Exemple
 L'exemple suivant illustre les métadonnées d'un modèle [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)].

```
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic template</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <LocationField>Disabled</LocationField>
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
- [Référence du schéma de modèle Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Création de modèles de projet et d’élément](../ide/creating-project-and-item-templates.md)
