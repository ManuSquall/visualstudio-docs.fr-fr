---
title: Élément ItemMetadata (MSBuild) | Microsoft Docs
description: En savoir plus sur l’élément MSBuild ItemMetadata,, qui contient une clé de métadonnées d’élément définie par l’utilisateur qui a la valeur de métadonnées.
ms.custom: SEO-VS-2020
ms.date: 03/13/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ItemMetadata Element [MSBuild]
- <ItemMetadata> Element [MSBuild]
ms.assetid: e3db5122-202d-43a9-b2f4-3e0ec4ed3d08
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: aba274068d8cba4f22526fdefac36d6c75f9f1e2
ms.sourcegitcommit: f1d47655974a2f08e69704a9a0c46cb007e51589
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/28/2020
ms.locfileid: "92903593"
---
# <a name="itemmetadata-element-msbuild"></a>ItemMetadata, élément (MSBuild)

Contient une clé de métadonnées d’élément définie par l’utilisateur, qui contient la valeur des métadonnées de l’élément. Un élément peut comporter un nombre quelconque de paires clé-valeur de métadonnées.

 \<Project> \<ItemGroup>
 \<Item>

## <a name="syntax"></a>Syntaxe

```xml
<ItemMetadataName> Item Metadata value</ItemMetadataName>
```

## <a name="attributes-and-elements"></a>Attributs et éléments

 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.

### <a name="attributes"></a>Attributs

|Attribut|Description|
|---------------|-----------------|
|`Condition`|Attribut facultatif.<br /><br /> Condition à évaluer. Pour plus d’informations, consultez l’article [Conditions (Conditions MSBuild)](../msbuild/msbuild-conditions.md).|

### <a name="child-elements"></a>Éléments enfants

 Aucun.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Item](../msbuild/item-element-msbuild.md)|Élément défini par l’utilisateur qui définit les entrées pour le processus de génération.|

## <a name="text-value"></a>Valeur texte

 Une valeur texte est facultative.

 Ce texte spécifie la valeur des métadonnées de l’élément (texte ou XML).

## <a name="example"></a>Exemple

 L’exemple de code ci-après indique comment ajouter des métadonnées `Culture` avec la valeur `fr` à l’élément `CSFile`.

```xml
<ItemGroup>
    <CSFile Include="main.cs" >
        <Culture>fr</Culture>
    </CSFile>
</ItemGroup>
```

## <a name="see-also"></a>Voir aussi

- [Référence du schéma de fichier projet](../msbuild/msbuild-project-file-schema-reference.md)
- [Éléments](../msbuild/msbuild-items.md)
