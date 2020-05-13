---
title: EmplacementField Element (Visual Studio Project Templates) Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#LocationField
helpviewer_keywords:
- LocationField element [Visual Studio project templates]
ms.assetid: 6aaaa155-6ce0-4f7f-aa50-8d63d7a7c992
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d993e84bec41486ef4dce6ad98c61f23ab2a46bd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702883"
---
# <a name="locationfield-element-visual-studio-project-templates"></a>Élément LocationField (modèles de projet Visual Studio)
Précise si la boîte de texte **de localisation** de la boîte de dialogue du **nouveau projet** est activée, désactivée ou cachée pour le modèle de projet.

 \<VSTemplate> \<TemplateData> \<LocationField>

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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Élément requis.<br /><br /> Catégorise le modèle et définit la façon dont il s’affiche dans le **nouveau projet**.|

## <a name="text-value"></a>Valeur texte
 Une valeur texte est requise.

 Les valeurs de texte valides sont les :

- `Enabled`, qui précise que la boîte de **localisation** de la boîte de dialogue **du nouveau projet** est activée.

- `Disabled`, qui précise que la boîte de **localisation** de la boîte de dialogue **du nouveau projet** est désactivée.

- `Hidden`, qui précise que la boîte de **localisation** de la boîte de dialogue **du nouveau projet** est cachée.

## <a name="remarks"></a>Notes
 La valeur par défaut est `Enabled`.

 La boîte de texte **de localisation** dans la boîte de dialogue **New Project** permet aux utilisateurs de modifier l’annuaire par défaut dans lequel de nouveaux projets sont sauvegardés.

 La valeur spécifiée dans l’élément `Location` n’est honorée que par la boîte de dialogue si le système de projet sous-jacent le prend en charge.

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
- [Référence de schéma de modèle de studio visuel](../extensibility/visual-studio-template-schema-reference.md)
- [Création de modèles de projets et d’objets](../ide/creating-project-and-item-templates.md)
