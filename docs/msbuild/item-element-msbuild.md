---
title: Item, élément (MSBuild) | Microsoft Docs
description: Découvrez comment MSBuild utilise l’élément Item pour contenir un élément défini par l’utilisateur et ses métadonnées. Chaque élément doit être un enfant d’un élément ItemGroup.
ms.custom: SEO-VS-2020
ms.date: 03/13/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Item Element [MSBuild]
- <Item> Element [MSBuild]
ms.assetid: dcef5f91-0613-4bfc-8ee9-d7004bb6d3a9
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 59a0660bb78e966150a6ef8d17dc24512a901a26
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99913947"
---
# <a name="item-element-msbuild"></a>Item, élément (MSBuild)

Contient un élément défini par l'utilisateur et ses métadonnées. Chaque élément utilisé dans un projet MSBuild doit être spécifié en tant qu’enfant d’un `ItemGroup` élément.

\<Project>
\<ItemGroup>
\<Item>

## <a name="syntax"></a>Syntaxe

```xml
<Item Include="*.cs"
        Exclude="MyFile.cs"
        Condition="'String A'=='String B'">
    <ItemMetadata1>...</ItemMetadata1>
    <ItemMetadata2>...</ItemMetadata2>
</Item>
```

## <a name="specify-metadata-as-attributes"></a>Spécifier des métadonnées en tant qu’attributs

Dans MSBuild version 15.1 ou ultérieure, toutes les métadonnées dont le nom n’entre pas en conflit avec la liste actuelle des attributs peuvent éventuellement être exprimées en tant qu’attribut.

Par exemple, pour spécifier une liste de packages NuGet, vous utiliseriez normalement une syntaxe similaire à la suivante.

```xml
<ItemGroup>
  <PackageReference Include="Newtonsoft.Json">
    <Version>9.0.1-beta1<Version>
  </PackageReference>
</ItemGroup>
```

À présent, toutefois, vous pouvez passer les métadonnées `Version` en tant qu’attribut, comme dans la syntaxe suivante :

```xml
<ItemGroup>
  <PackageReference Include="Newtonsoft.Json" Version="9.0.1-beta1" />
</ItemGroup>
```

## <a name="attributes-and-elements"></a>Attributs et éléments

 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.

### <a name="attributes"></a>Attributs

|Attribut|Description|
|---------------|-----------------|
|`Include`|Attribut facultatif.<br /><br /> Fichier ou caractère générique à inclure dans la liste des éléments.|
|`Exclude`|Attribut facultatif.<br /><br /> Fichier ou caractère générique à exclure de la liste des éléments.|
|`Condition`|Attribut facultatif.<br /><br /> Condition à évaluer. Pour plus d’informations, consultez l’article [Conditions (Conditions MSBuild)](../msbuild/msbuild-conditions.md).|
|`Remove`|Attribut facultatif.<br /><br /> Fichier ou caractère générique à supprimer de la liste des éléments.<br /><br />|
|`KeepDuplicates`|Attribut facultatif.<br /><br /> Spécifie si un élément doit être ajouté au groupe cible s'il s'agit d'une copie exacte d'un élément existant. Si les éléments source et cible ont les mêmes valeurs `Include` mais des métadonnées différentes, l'élément est ajouté même si `KeepDuplicates` est défini sur `false`. Pour plus d’informations, consultez l’article [Éléments MSBuild](../msbuild/msbuild-items.md).<br /><br /> Cet attribut n'est valide que s'il est spécifié pour un élément d'un `ItemGroup` présent dans un `Target`.|
|`KeepMetadata`|Attribut facultatif.<br /><br /> Métadonnées des éléments sources à ajouter aux éléments cibles. Seules les métadonnées dont les noms sont spécifiés dans la liste délimitée par des points-virgules sont transférées depuis un élément source vers un élément cible. Pour plus d’informations, consultez l’article [Éléments MSBuild](../msbuild/msbuild-items.md).<br /><br /> Cet attribut n'est valide que s'il est spécifié pour un élément d'un `ItemGroup` présent dans un `Target`.|
|`RemoveMetadata`|Attribut facultatif.<br /><br /> Métadonnées des éléments sources à ne pas transférer aux éléments cibles. Toutes les métadonnées sont transférées depuis un élément source vers un élément cible, à l'exception des métadonnées dont le nom figure dans la liste de noms délimitée par des points-virgules. Pour plus d’informations, consultez l’article [Éléments MSBuild](../msbuild/msbuild-items.md).<br /><br /> Cet attribut n'est valide que s'il est spécifié pour un élément d'un `ItemGroup` présent dans un `Target`.|
|`Update`|Attribut facultatif. (Disponible uniquement pour les projets .NET Core dans Visual Studio versions 2017 ou ultérieures).<br /><br /> Vous permet de modifier les métadonnées d’un élément ; généralement utilisé pour remplacer les métadonnées par défaut d’éléments spécifiques après qu’un groupe d’éléments est spécifié au niveau initial (par exemple, avec un caractère générique).<br /><br /> Cet attribut est valide seulement s’il est spécifié pour un élément d’un `ItemGroup` qui n’est pas présent dans un `Target`.|

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[ItemMetadata,](../msbuild/itemmetadata-element-msbuild.md)|Clé de métadonnées d'élément définie par l'utilisateur, qui contient la valeur des métadonnées de l'élément. Un élément peut ne contenir aucun élément `ItemMetadata` ou en contenir plusieurs.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[ItemGroup](../msbuild/itemgroup-element-msbuild.md)|Élément grouping pour d’autres éléments.|

## <a name="remarks"></a>Remarques

Les éléments `Item` définissent les entrées du système de génération et sont regroupés en collections d'éléments, selon leur nom de collection défini par l'utilisateur. Ces collections d’éléments peuvent être utilisées comme paramètres des [tâches](../msbuild/msbuild-tasks.md), lesquelles utilisent les éléments d’une collection pour exécuter les étapes du processus de génération. Pour plus d’informations, consultez l’article [Éléments MSBuild](../msbuild/msbuild-items.md).

L’utilisation de la notation @ ( \<myType> ) permet d’étendre une collection d’éléments de type \<myType> dans une liste de chaînes délimitées par des points-virgules, et de la passer à un paramètre. Si le paramètre est de type `string`, la valeur du paramètre correspond à la liste des éléments séparés par des points-virgules. Si le paramètre est un tableau de chaînes (`string[]`), chaque élément est inséré dans le tableau selon l'emplacement des points-virgules. Si le paramètre de tâche est de type <xref:Microsoft.Build.Framework.ITaskItem>`[]`, la valeur correspond au contenu de la collection d'éléments et à toutes les métadonnées associées. Pour délimiter chaque élément à l’aide d’un caractère autre que le point-virgule, utilisez la syntaxe @(\<myType>, '\<separator>').

Le moteur MSBuild peut évaluer des caractères génériques tels que `*` et `?` et des caractères génériques récursifs, tels que */ \* \* / \* . cs*. Pour plus d’informations, consultez l’article [Éléments MSBuild](../msbuild/msbuild-items.md).

## <a name="examples"></a>Exemples

L'exemple de code suivant montre comment déclarer deux éléments de type `CSFile`. Le second élément déclaré contient les métadonnées dans lesquelles `MyMetadata` a la valeur `HelloWorld`.

```xml
<ItemGroup>
    <CSFile Include="engine.cs; form.cs" />
    <CSFile Include="main.cs" >
        <MyMetadata>HelloWorld</MyMetadata>
    </CSFile>
</ItemGroup>
```

L’exemple de code suivant montre comment utiliser l’attribut `Update` pour modifier les métadonnées dans un fichier appelé *somefile.cs* fourni par le biais d’un glob. (Disponible uniquement pour les projets .NET Core dans Visual Studio versions 2017 ou ultérieures).

```xml
<ItemGroup>
    <Compile Update="somefile.cs">  // or Update="*.designer.cs"
        <MetadataKey>MetadataValue</MetadataKey>
    </Compile>
</ItemGroup>
```

## <a name="see-also"></a>Voir aussi

- [Éléments](../msbuild/msbuild-items.md)
- [Éléments communs des projets MSBuild](../msbuild/common-msbuild-project-items.md)
- [MSBuild (propriétés)](../msbuild/msbuild-properties.md)
- [Référence du schéma de fichier projet](../msbuild/msbuild-project-file-schema-reference.md)
