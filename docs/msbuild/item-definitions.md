---
title: Définitions d’éléments | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- msbuild, item definitions
ms.assetid: 8e3dc223-f9e5-4974-aa0e-5dc7967419cb
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 18d6a2a30af4fb29a8d9e924c44c1570ff1efe29
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "77633705"
---
# <a name="item-definitions"></a>Définitions d’éléments

MSBuild 2,0 active la déclaration statique d’éléments dans les fichiers projet à l’aide de l’élément [ItemGroup](../msbuild/itemgroup-element-msbuild.md) . Les métadonnées ne peuvent cependant être ajoutées qu’au niveau de l’élément, même si elles sont identiques pour tous les éléments. À compter de MSBuild 3,5, un élément de projet nommé [ItemDefinitionGroup](../msbuild/itemdefinitiongroup-element-msbuild.md) se limite à cette limitation. *ItemDefinitionGroup* vous permet de définir un ensemble de définitions d’élément, qui ajoutent des valeurs de métadonnées par défaut à tous les éléments dans le type d’élément nommé.

L’élément *ItemDefinitionGroup* apparaît immédiatement après l’élément [Project](../msbuild/project-element-msbuild.md) du fichier projet. Les définitions d’élément offrent les fonctionnalités suivantes :

- Vous pouvez définir des métadonnées par défaut globales pour les éléments en dehors d’une cible. Autrement dit, les mêmes métadonnées s’appliquent à tous les éléments du type spécifié.

- Les types d’éléments peuvent avoir plusieurs définitions. Quand des spécifications de métadonnées supplémentaires sont ajoutées au type, la dernière spécification est prioritaire. \(Les métadonnées suivent le même ordre d’importation que celui des propriétés.\)

- Les métadonnées peuvent être additionnées. Par exemple, les valeurs CDefines sont cumulées conditionnellement, en fonction des propriétés qui sont définies. Par exemple : `MT;STD_CALL;DEBUG;UNICODE`.

- Les métadonnées peuvent être supprimées.

- Des conditions peuvent être utilisées pour contrôler l’inclusion de métadonnées.

## <a name="item-metadata-default-values"></a>Valeurs par défaut des métadonnées d’éléments

Les métadonnées d’éléments qui sont définies dans un ItemDefinitionGroup sont simplement une déclaration de métadonnées par défaut. Les métadonnées ne s’applique pas sauf si vous définissez un élément qui utilise un ItemGroup pour contenir les valeurs des métadonnées.

> [!NOTE]
> Dans la plupart des exemples de cette rubrique, un élément ItemDefinitionGroup est montré mais sa définition ItemGroup correspondante est omise par souci de clarté.

Les métadonnées explicitement définies dans un ItemGroup sont prioritaires sur les métadonnées dans ItemDefinitionGroup. Les métadonnées dans ItemDefinitionGroup sont appliquées uniquement pour les métadonnées non définies dans un ItemGroup. Par exemple :

```xml
<ItemDefinitionGroup>
    <i>
        <m>m1</m>
        <n>n1</n>
    </i>
</ItemDefinitionGroup>
<ItemGroup>
    <i Include="a">
        <o>o1</o>
        <n>n2</n>
    </i>
</ItemGroup>
```

Dans cet exemple, les métadonnées par défaut « m » sont appliquées à l’élément « i », car les métadonnées « m » ne sont pas explicitement définies par l’élément « i ». Cependant, les métadonnées par défaut « n » ne sont pas appliquées à l’élément « i », car les métadonnées « n » sont déjà définies par l’élément « i ».

> [!NOTE]
> Les noms de paramètre et d’élément XML respectent la casse. Les noms des métadonnées d’élément et des éléments\/propriétés ne respectent pas la casse. Par conséquent, les éléments ItemDefinitionGroup ayant des noms qui diffèrent uniquement par la casse doivent être traités comme le même ItemGroup.

## <a name="value-sources"></a>Sources des valeurs

Les valeurs pour les métadonnées définies dans un ItemDefinitionGroup peuvent provenir de nombreuses sources différentes, comme suit :

- Propriété PropertyGroup

- Élément d’un ItemDefinitionGroup

- Transformation d’élément sur un élément ItemDefinitionGroup

- Variable d’environnement

- Propriété globale (de la ligne de commande *MSBuild.exe*)

- Propriété réservée

- Métadonnées bien connues sur un élément d’un ItemDefinitionGroup

- Section CDATA \<\!\[CDATA\[anything here is not parsed\]\]\>

> [!NOTE]
> Les métadonnées d’élément d’un ItemGroup ne sont pas utiles dans une déclaration de métadonnées ItemDefinitionGroup, car les éléments ItemDefinitionGroup sont traités avant les éléments ItemGroup.

## <a name="additive-and-multiple-definitions"></a>Définitions additives et multiples

Quand vous ajoutez des définitions ou que vous utilisez plusieurs ItemDefinitionGroup, gardez à l’esprit que :

- Une spécification de métadonnées supplémentaires est ajoutée au type.

- La dernière spécification est prioritaire.

Quand vous avez plusieurs ItemDefinitionGroup, chaque spécification ultérieure ajoute ses métadonnées à la définition précédente. Par exemple :

```xml
<ItemDefinitionGroup>
    <i>
        <m>m1</m>
        <n>n1</n>
    </i>
</ItemDefinitionGroup>
<ItemDefinitionGroup>
    <i>
        <o>o1</o>
    </i>
</ItemDefinitionGroup>
```

Dans cet exemple, les métadonnées « o » sont ajoutées à « m » et à « n ».

En outre, les valeurs des métadonnées définies précédemment peuvent également être ajoutées. Par exemple :

```xml
<ItemDefinitionGroup>
    <i>
        <m>m1</m>
    </i>
</ItemDefinitionGroup>
<ItemDefinitionGroup>
    <i>
        <m>%(m);m2</m>
    </i>
</ItemDefinitionGroup>
```

Dans cet exemple, la valeur précédemment définie pour les métadonnées « m » \(m1\) est ajoutée à la nouvelle valeur \(m2\), de sorte que la valeur finale est « m1;m2 ».

> [!NOTE]
> Ceci peut également se produire dans le même ItemDefinitionGroup.

Quand vous remplacez les métadonnées définies précédemment, la dernière spécification est prioritaire. Dans l’exemple suivant, la valeur finale des métadonnées « m » passe de « m1 » « m1a ».

```xml
<ItemDefinitionGroup>
    <i>
        <m>m1</m>
    </i>
</ItemDefinitionGroup>
<ItemDefinitionGroup>
    <i>
        <m>m1a</m>
    </i>
</ItemDefinitionGroup>
```

## <a name="use-conditions-in-an-itemdefinitiongroup"></a>Utiliser des conditions dans un ItemDefinitionGroup

Vous pouvez utiliser des conditions dans un ItemDefinitionGroup pour contrôler l’inclusion des métadonnées. Par exemple :

```xml
<ItemDefinitionGroup Condition="'$(Configuration)'=='Debug'">
    <i>
        <m>m1</m>
    </i>
</ItemDefinitionGroup>
```

Dans ce cas, les métadonnées par défaut « m1 » sur l’élément « i » sont incluses seulement si la valeur de la propriété « Configuration » est « Debug ».

> [!NOTE]
> Seules les références de métadonnées locales sont prises en charge dans les conditions.

Les références aux métadonnées définies dans un ItemDefinitionGroup antérieur sont locales à l’élément, et non pas au groupe de définitions. Autrement dit, l’étendue des références est spécifique aux éléments. Par exemple :

```xml
<ItemDefinitionGroup>
    <test>
        <yes>1</yes>
    </test>
    <i>
        <m>m0</m>
        <m Condition="'%(test.yes)'=='1'">m1</m>
    </i>
</ItemDefinitionGroup>

```

Dans l’exemple ci-dessus, l’élément « i » référence l’élément « test » dans sa condition. Cette condition ne sera jamais vraie car MSBuild interprète une référence aux métadonnées d’un autre élément dans un ItemDefinitionGroup comme une chaîne vide. Par conséquent, « m » est défini sur « m0 ».

```xml
  <ItemDefinitionGroup>
    <i>
      <m>m0</m>
      <yes>1</yes>
      <m Condition="'%(i.yes)'=='1'">m1</m>
    </i>
  </ItemDefinitionGroup>

```

Dans l’exemple ci-dessus, « m » est défini sur la valeur « m1 », car la condition référence la valeur des métadonnées « i » pour l’élément « yes ».

## <a name="override-and-delete-metadata"></a>Remplacer et supprimer des métadonnées

Les métadonnées définies dans un élément ItemDefinitionGroup peuvent être substituées dans un élément ItemDefinitionGroup ultérieur en affectant à la valeur de métadonnées une autre valeur. Vous pouvez aussi supprimer un élément de métadonnées en lui attribuant une valeur vide. Par exemple :

```xml
<ItemDefinitionGroup>
    <i>
        <m>m1</m>
    </i>
</ItemDefinitionGroup>
<ItemDefinitionGroup>
    <i>
        <m></m>
    </i>
</ItemDefinitionGroup>
```

L’élément « i » contient encore les métadonnées « m », mais sa valeur est maintenant vide.

## <a name="scope-of-metadata"></a>Étendue des métadonnées

Les ItemDefinitionGroup ont une étendue globale sur les propriétés définies et globales là où elles sont définies. Les définitions de métadonnées par défaut dans un ItemDefinitionGroup peuvent se référencer elles-mêmes. Par exemple, ce qui suit utilise une référence de métadonnées simple :

```xml
<ItemDefinitionGroup>
    <i>
        <m>m1</m>
        <m>%(m);m2</m>
    </i>
</ItemDefinitionGroup>
```

Une référence de métadonnées qualifiée peut également être utilisée :

```xml
<ItemDefinitionGroup>
    <i>
        <m>m1</m>
        <m>%(i.m);m2</m>
    </i>
</ItemDefinitionGroup>
```

L’exemple suivant n’est cependant pas valide :

```xml
<ItemDefinitionGroup>
    <i>
        <m>m1</m>
        <m>@(x)</m>
    </i>
</ItemDefinitionGroup>
```

À compter de MSBuild 3,5, ItemGroup enfants peut également être auto-référentielle. Par exemple :

```xml
<ItemGroup>
    <item Include="a">
        <m>m1</m>
        <m>%(m);m2</m>
    </item>
</ItemGroup>
```

## <a name="see-also"></a>Voir aussi

- [Traitement par lot](../msbuild/msbuild-batching.md)
