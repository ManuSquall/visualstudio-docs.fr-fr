---
title: Élément EnableEditOfLocationField (modèles Visual Studio)
description: En savoir plus sur l’élément EnableEditOfLocationField et sur la façon dont il spécifie si l’utilisateur peut modifier le champ d’emplacement.
titleSuffix: ''
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- EnableEditOfLocationField (Visual Studio project templates)
ms.assetid: 51a91963-8a3f-4741-928e-bc90c11473bb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 46af48bf8bf9f128103767be1aa5fa64968e68f5
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94671296"
---
# <a name="enableeditoflocationfield-element-visual-studio-templates"></a>Élément EnableEditOfLocationField (modèles Visual Studio)
Spécifie si l’utilisateur peut modifier le champ d’emplacement.

 \<VSTemplate> \<TemplateData>
 \<EnableEditOfLocationField>

## <a name="syntax"></a>Syntaxe

```
<EnableEditOfLocationField> true/false </EnableEditOfLocationField>
```

## <a name="attributes-and-elements"></a>Attributs et éléments
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.

### <a name="attributes"></a>Attributs
 Aucun

### <a name="child-elements"></a>Éléments enfants
 Aucun

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Élément requis.<br /><br /> Définit la catégorie du modèle et comment il s’affiche dans la boîte de dialogue **Nouveau projet** ou **Ajouter un nouvel élément** .|

## <a name="text-value"></a>Valeur texte
 Une valeur texte est requise.

 Le texte doit être `true` ou `false` , indiquant si l’utilisateur peut modifier la zone de texte **emplacement** dans la boîte de dialogue **nouveau projet** .

## <a name="remarks"></a>Remarques
 `EnableEditOfLocationField` est un élément facultatif. La valeur par défaut est `true` , ce qui permet à l’utilisateur de modifier la valeur de la zone de texte **emplacement** dans la boîte de dialogue **nouveau projet** .

 Dans la boîte de dialogue **nouveau projet** , la zone de texte **emplacement** spécifie le répertoire dans lequel un nouveau projet est enregistré.

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
        <EnableEditOfLocationField>false</EnableEditOfLocationField>
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
