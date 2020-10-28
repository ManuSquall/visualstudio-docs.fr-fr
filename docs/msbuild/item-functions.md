---
title: Fonctions d’élément | Microsoft Docs
description: Découvrez comment le code MSBuild dans les tâches et les cibles peut appeler des fonctions d’élément pour obtenir des informations sur les éléments du projet.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- msbuild, Item functions
ms.assetid: 5e6df3cc-2db8-4cbd-8fdd-3ffd03ac0876
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 94b94ef7b17633ab78f7eb91f61dd67ea2c8021d
ms.sourcegitcommit: f1d47655974a2f08e69704a9a0c46cb007e51589
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/28/2020
ms.locfileid: "92904636"
---
# <a name="item-functions"></a>fonctions d'élément

Le code des tâches et des cibles peut appeler des fonctions d’élément pour obtenir des informations sur les éléments du projet (dans MSBuild 4,0 et versions ultérieures). Ces fonctions simplifient l’obtention d’éléments distincts et sont plus rapides que l’itération dans les éléments.

## <a name="string-item-functions"></a>Fonctions d’élément de type chaîne

Vous pouvez utiliser des méthodes et des propriétés de chaîne dans le .NET Framework pour manipuler n’importe quelle valeur d’élément. Pour les méthodes <xref:System.String>, spécifiez le nom de la méthode. Pour les propriétés <xref:System.String>, spécifiez le nom de la propriété après « get_ ».

Pour les éléments qui ont plusieurs chaînes, la méthode ou la propriété de chaîne s’exécute sur chaque chaîne.

L’exemple suivant montre comment utiliser ces méthodes d’élément de type chaîne.

```xml
<ItemGroup>
    <theItem Include="andromeda;tadpole;cartwheel" />
</ItemGroup>

<Target Name = "go">
    <Message Text="IndexOf  @(theItem->IndexOf('r'))" />
    <Message Text="Replace  @(theItem->Replace('tadpole', 'pinwheel'))" />
    <Message Text="Length   @(theItem->get_Length())" />
    <Message Text="Chars    @(theItem->get_Chars(2))" />
</Target>

  <!--
  Output:
    IndexOf  3;-1;2
    Replace  andromeda;pinwheel;cartwheel
    Length   9;7;9
    Chars    d;d;r
  -->
```

## <a name="intrinsic-item-functions"></a>Fonctions d’élément intrinsèques

Le tableau ci-dessous liste les fonctions intrinsèques disponibles pour les éléments.

|Fonction| Exemple|Description|
|--------------|-------------|-----------------|
|`Count`|`@(MyItem->Count())`|Retourne le nombre d’éléments.|
|`DirectoryName`|`@(MyItem->DirectoryName())`|Retourne l’équivalent de `Path.DirectoryName` pour chaque élément.|
|`Distinct`|`@(MyItem->Distinct())`|Retourne les éléments qui ont des valeurs `Include` distinctes. Les métadonnées sont ignorées. La comparaison ne respecte pas la casse.|
|`DistinctWithCase`|`@(MyItem->DistinctWithCase())`|Retourne les éléments qui ont des valeurs `itemspec` distinctes. Les métadonnées sont ignorées. La comparaison respecte la casse.|
|`Reverse`|`@(MyItem->Reverse())`|Retourne les éléments en ordre inverse.|
|`AnyHaveMetadataValue`|`@(MyItem->AnyHaveMetadataValue("MetadataName", "MetadataValue"))`|Retourne un `boolean` pour indiquer si un élément a le nom et la valeur des métadonnées fournies. La comparaison ne respecte pas la casse.|
|`ClearMetadata`|`@(MyItem->ClearMetadata())`|Retourne les éléments avec leurs métadonnées effacées. Seul `itemspec` est conservé.|
|`HasMetadata`|`@(MyItem->HasMetadata("MetadataName"))`|Retourne les éléments qui ont le nom des métadonnées fourni. La comparaison ne respecte pas la casse.|
|`Metadata`|`@(MyItem->Metadata("MetadataName"))`|Retourne les valeurs des métadonnées qui ont le nom des métadonnées.|
|`WithMetadataValue`|`@(MyItem->WithMetadataValue("MetadataName", "MetadataValue"))`|Retourne les éléments qui ont le nom et la valeur des métadonnées fournis. La comparaison ne respecte pas la casse.|

L’exemple suivant montre comment utiliser des fonctions d’élément intrinsèques.

```xml
<ItemGroup>
    <TheItem Include="first">
        <Plant>geranium</Plant>
    </TheItem>
    <TheItem Include="second">
        <Plant>algae</Plant>
    </TheItem>
    <TheItem Include="third">
        <Plant>geranium</Plant>
    </TheItem>
</ItemGroup>

<Target Name="go">
    <Message Text="MetaData:    @(TheItem->Metadata('Plant'))" />
    <Message Text="HasMetadata: @(theItem->HasMetadata('Plant'))" />
    <Message Text="WithMetadataValue: @(TheItem->WithMetadataValue('Plant', 'geranium'))" />
    <Message Text=" " />
    <Message Text="Count:   @(theItem->Count())" />
    <Message Text="Reverse: @(theItem->Reverse())" />
</Target>

  <!--
  Output:
    MetaData:    geranium;algae;geranium
    HasMetadata: first;second;third
    WithMetadataValue: first;third

    Count:   3
    Reverse: third;second;first
  -->
```

## <a name="msbuild-condition-functions"></a>Fonctions de condition MSBuild

Les fonctions `Exists` et ne `HasTrailingSlash` sont pas des fonctions d’élément. Elles peuvent être utilisées avec l' `Condition` attribut. Consultez les [Conditions MSBuild](msbuild-conditions.md).

## <a name="see-also"></a>Voir aussi

- [Éléments](../msbuild/msbuild-items.md)
