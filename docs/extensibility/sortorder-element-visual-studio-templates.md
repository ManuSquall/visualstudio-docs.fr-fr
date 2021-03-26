---
title: SortOrder, élément (modèles Visual Studio) | Microsoft Docs
description: En savoir plus sur l’élément SortOrder et sur la manière dont il spécifie une valeur utilisée pour réorganiser le modèle tel qu’il apparaît dans la boîte de dialogue Nouveau projet ou ajouter un nouvel élément.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#SortOrder
helpviewer_keywords:
- SortOrder element [Visual Studio Templates]
- <SortOrder> element [Visual Studio Templates]
ms.assetid: 151932c1-f08a-4f78-a8d0-bd2f32211a9c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a195e3801ce505d2c1f069c07ff4457e1c1042b3
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105073792"
---
# <a name="sortorder-element-visual-studio-templates"></a>SortOrder, élément (modèles Visual Studio)
Spécifie une valeur qui est utilisée pour réorganiser le modèle, parmi d’autres modèles de la même catégorie, tel qu’il apparaît dans la boîte de dialogue **nouveau projet** ou **Ajouter un nouvel élément** .

 \<VSTemplate> \<TemplateData>
 \<SortOrder>

## <a name="syntax"></a>Syntaxe

```
<SortOrder> ... </SortOrder>
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

 `integer`Qui représente la valeur d’ordre de tri.

## <a name="remarks"></a>Notes
 `SortOrder` est un élément facultatif. La valeur par défaut est 100, et toutes les valeurs doivent être des multiples de 10.

 L' `SortOrder` élément est ignoré pour les modèles créés par l’utilisateur. Tous les modèles créés par l’utilisateur sont triés par ordre alphabétique.

 Les modèles qui ont des valeurs d’ordre de tri faible s’affichent dans la boîte de dialogue **nouveau projet** ou **nouvel élément Ajouter** avant les modèles qui ont des valeurs d’ordre de tri élevées.

## <a name="example"></a>Exemple
 L’exemple suivant illustre les métadonnées pour un [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] modèle de classe standard.

```
<VSTemplate Type="Item" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>MyClass</Name>
        <Description>My custom C# class template.</Description>
        <Icon>Icon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <SortOrder>290</SortOrder>
        <DefaultName>MyClass</DefaultName>
    </TemplateData>
    <TemplateContent>
        <ProjectItem>MyClass.cs</ProjectItem>
    </TemplateContent>
</VSTemplate>
```

 Dans cet exemple, l' `SortOrder` élément est relativement élevé. Il est probable que [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] d’autres modèles d’élément auront une `SortOrder` valeur inférieure à `290` et apparaîtront avant ce modèle dans la boîte de dialogue **nouvel élément** .

## <a name="see-also"></a>Voir aussi
- [Référence du schéma de modèle Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Création de modèles de projet et d’élément](../ide/creating-project-and-item-templates.md)
