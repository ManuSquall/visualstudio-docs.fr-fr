---
title: Élément ItemGroup (MSBuild) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ItemGroup
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ItemGroup element [MSBuild]
- <ItemGroup> element [MSBuild]
ms.assetid: aac894e3-a9f1-4bbc-a796-6ef07001f35b
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a62b4df06d1c180a6a6d62b0231dce1136fb8059
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85288973"
---
# <a name="itemgroup-element-msbuild"></a>ItemGroup, élément (MSBuild)

Contient un ensemble d’éléments [Item](../msbuild/item-element-msbuild.md) définis par l’utilisateur. Chaque élément utilisé dans un projet MSBuild doit être spécifié en tant qu’enfant d’un `ItemGroup` élément.

\<Project>
\<ItemGroup>

## <a name="syntax"></a>Syntax

```xml
<ItemGroup Condition="'String A' == 'String B'"
           Label="Label">
    <Item1>... </Item1>
    <Item2>... </Item2>
</ItemGroup>
```

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.

### <a name="attributes"></a>Attributs

|Attribut|Description|
|---------------|-----------------|
|`Condition`|Attribut facultatif. Condition à évaluer. Pour plus d’informations, consultez l’article [Conditions (Conditions MSBuild)](../msbuild/msbuild-conditions.md).|
|`Label`|Attribut facultatif. Identifie le `ItemGroup`. |

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[Item](../msbuild/item-element-msbuild.md)|Définit les entrées du processus de génération. Un élément `ItemGroup` peut ne contenir aucun élément `Item` ou en contenir plusieurs.|

### <a name="parent-elements"></a>Éléments parents

| Élément | Description |
| - | - |
| [Projet](../msbuild/project-element-msbuild.md) | Élément racine requis d’un fichier projet MSBuild. |
| [Cible](../msbuild/target-element-msbuild.md) | Depuis .NET Framework 3.5, l’élément `ItemGroup` peut apparaître dans un élément `Target`. Pour plus d’informations, consultez l’article [Targets (Cibles MSBuild)](../msbuild/msbuild-targets.md). |

## <a name="example"></a>Exemple

L’exemple de code suivant illustre les collections d’éléments définis par l’utilisateur `Res` et `CodeFiles` déclarés dans un élément `ItemGroup`. Chacun des éléments de la collection d’éléments `Res` contient un élément [ItemMetadata](../msbuild/itemmetadata-element-msbuild.md) enfant défini par l’utilisateur.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <ItemGroup>
        <Res Include = "Strings.fr.resources" >
            <Culture>fr</Culture>
        </Res>
        <Res Include = "Dialogs.fr.resources" >
            <Culture>fr</Culture>
        </Res>

        <CodeFiles Include="**\*.cs" Exclude="**\generated\*.cs" />
        <CodeFiles Include="..\..\Resources\Constants.cs" />
    </ItemGroup>
...
</Project>
```

Dans un fichier projet simple, vous utilisez normalement un seul `ItemGroup` élément, mais vous pouvez également utiliser plusieurs `ItemGroup` éléments. Quand plusieurs `ItemGroup` éléments sont utilisés, les éléments sont combinés en un seul `ItemGroup` . Par exemple, certains éléments peuvent être inclus `ItemGroup` dans un élément distinct qui est défini dans un fichier importé.

ItemGroup enfants peut avoir des conditions appliquées à l’aide de l' `Condition` attribut. Dans ce cas, les éléments sont ajoutés uniquement à la liste d’éléments si la condition est satisfaite. Voir les [Conditions MSBuild](msbuild-conditions.md)

L' `Label` attribut est utilisé dans certains systèmes de génération comme un moyen de contrôler les comportements de génération. Vous pouvez l’utiliser uniquement dans les déclarations, comme un moyen de créer des scripts MSBuild plus compréhensibles, ou en tant que paramètre de contrôle pour affecter des actions de génération.

## <a name="see-also"></a>Voir aussi

- [Référence du schéma de fichier projet](../msbuild/msbuild-project-file-schema-reference.md)
- [Éléments](../msbuild/msbuild-items.md)
- [Éléments communs des projets MSBuild](../msbuild/common-msbuild-project-items.md)
