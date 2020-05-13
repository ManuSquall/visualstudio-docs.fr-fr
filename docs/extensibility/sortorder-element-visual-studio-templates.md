---
title: SortOrder Element (Visual Studio Templates) Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#SortOrder
helpviewer_keywords:
- SortOrder element [Visual Studio Templates]
- <SortOrder> element [Visual Studio Templates]
ms.assetid: 151932c1-f08a-4f78-a8d0-bd2f32211a9c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 935d00335a21d3e129e79ce351e554ea93787447
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699959"
---
# <a name="sortorder-element-visual-studio-templates"></a>SortOrder, élément (modèles Visual Studio)
Spécifie une valeur qui est utilisée pour arranger le modèle, entre autres modèles dans la même catégorie, comme il apparaît dans le **nouveau projet** ou ajouter la boîte de dialogue **Nouvel Élément.**

 \<VSTemplate> \<TemplateData> \<SortOrder>

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

 Un `integer` qui représente la valeur de commande de tri.

## <a name="remarks"></a>Notes
 `SortOrder` est un élément facultatif. La valeur par défaut est de 100, et toutes les valeurs doivent être multiples de 10.

 L’élément `SortOrder` est ignoré pour les modèles créés par l’utilisateur. Tous les modèles créés par l’utilisateur sont triés par ordre alphabétique.

 Les modèles qui ont des valeurs d’ordre de tri faible apparaissent dans le **nouveau projet** ou la boîte de dialogue de nouvel **élément d’addition** avant les modèles qui ont des valeurs élevées de commande de tri.

## <a name="example"></a>Exemple
 L’exemple suivant illustre les métadonnées d’un modèle de classe standard. [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]

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

 Dans cet exemple, l’élément `SortOrder` est relativement élevé. Il est probable [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] que d’autres `SortOrder` modèles `290` d’éléments auront une valeur inférieure à celle et apparaîtront avant ce modèle dans la boîte de dialogue **Du nouvel élément.**

## <a name="see-also"></a>Voir aussi
- [Référence du schéma de modèle Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Création de modèles de projet et d’élément](../ide/creating-project-and-item-templates.md)
