---
title: SortOrder, élément (modèles Visual Studio) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#SortOrder
helpviewer_keywords:
- SortOrder element [Visual Studio Templates]
- <SortOrder> element [Visual Studio Templates]
ms.assetid: 151932c1-f08a-4f78-a8d0-bd2f32211a9c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2875bcb4583c1d2ec47a935d1a8bb4f0de109a92
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72719924"
---
# <a name="sortorder-element-visual-studio-templates"></a>SortOrder, élément (modèles Visual Studio)
Spécifie une valeur qui est utilisée pour réorganiser le modèle, parmi d’autres modèles de la même catégorie, tel qu’il apparaît dans la boîte de dialogue **nouveau projet** ou **Ajouter un nouvel élément** .

 \<VSTemplate > \<TemplateData > \<SortOrder >

## <a name="syntax"></a>Syntaxe

```
<SortOrder> ... </SortOrder>
```

## <a name="attributes-and-elements"></a>Attributs et éléments
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.

### <a name="attributes"></a>Attributs
 Aucun(e).

### <a name="child-elements"></a>Éléments enfants
 Aucun(e).

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Élément requis.<br /><br /> Définit la catégorie du modèle et comment il s’affiche dans la boîte de dialogue **Nouveau projet** ou **Ajouter un nouvel élément** .|

## <a name="text-value"></a>Valeur texte
 Une valeur texte est requise.

 @No__t_0 qui représente la valeur d’ordre de tri.

## <a name="remarks"></a>Notes
 `SortOrder` est un élément facultatif. La valeur par défaut est 100, et toutes les valeurs doivent être des multiples de 10.

 L’élément `SortOrder` est ignoré pour les modèles créés par l’utilisateur. Tous les modèles créés par l’utilisateur sont triés par ordre alphabétique.

 Les modèles qui ont des valeurs d’ordre de tri faible s’affichent dans la boîte de dialogue **nouveau projet** ou **nouvel élément Ajouter** avant les modèles qui ont des valeurs d’ordre de tri élevées.

## <a name="example"></a>Exemple
 L’exemple suivant illustre les métadonnées pour un modèle de classe [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] standard.

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

 Dans cet exemple, l’élément `SortOrder` est relativement élevé. Il est probable que d’autres modèles d’élément de [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] auront une valeur de `SortOrder` inférieure à `290` et apparaîtront avant ce modèle dans la boîte de dialogue **nouvel élément** .

## <a name="see-also"></a>Voir aussi
- [Référence du schéma de modèle Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Création de modèles de projet et d’élément](../ide/creating-project-and-item-templates.md)