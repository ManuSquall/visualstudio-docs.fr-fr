---
title: Guide pratique pour afficher une liste d’éléments séparés par des virgules | Microsoft Docs
description: Découvrez comment utiliser MSBuild pour afficher une liste d’éléments séparés par des virgules, ou pour spécifier d’autres chaînes de séparation pour une liste d’éléments.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, separating items with semicolons
- MSBuild, formatting item collections
ms.assetid: 3cae844c-7c6d-4144-82dc-efad10ba458f
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3ac0295b2d6f4300fa29c893d61616977ad44b87
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99914421"
---
# <a name="how-to-display-an-item-list-separated-with-commas"></a>Guide pratique pour afficher une liste d’éléments séparés par des virgules

Quand vous travaillez avec des listes d’éléments dans Microsoft Build Engine (MSBuild), il est parfois utile d’afficher le contenu de ces listes d’éléments d’une manière facile à lire. Vous pouvez également avoir une tâche qui accepte une liste d’éléments séparés par une chaîne de séparation particulière. Dans ces deux cas, vous pouvez spécifier une chaîne de séparation pour la liste d’éléments.

## <a name="separate-items-in-a-list-with-commas"></a>Séparer des éléments d’une liste à l’aide de virgules

Par défaut, MSBuild utilise des points-virgules pour séparer les éléments d’une liste. Par exemple, imaginez un élément `Message` avec la valeur suivante :

`<Message Text="This is my list of TXT files: @(TXTFile)"/>`

Lorsque la `@(TXTFile)` liste d’éléments contient les éléments *App1.txt*, *App2.txt* et *App3.txt*, le message est :

`This is my list of TXT files: App1.txt;App2.txt;App3.txt`

Si vous souhaitez modifier le comportement par défaut, vous pouvez spécifier votre propre séparateur. La syntaxe à utiliser pour spécifier un séparateur d’éléments de liste est la suivante :

`@(ItemListName, '<separator>')`

Le séparateur peut être un caractère unique ou une chaîne, et doit être compris entre guillemets simples.

#### <a name="to-insert-a-comma-and-a-space-between-items"></a>Pour insérer une virgule et un espace entre les éléments

- Utilisez une notation d’éléments semblable à celle-ci :

    `@(TXTFile, ', ')`

## <a name="example"></a>Exemple

Dans cet exemple, la tâche [Exec](../msbuild/exec-task.md) exécute l’outil findstr pour rechercher des chaînes de texte spécifiées dans le fichier *Phrases.txt*. Dans la commande Findstr, les chaînes de recherche littérales sont indiquées par le commutateur **-c :** , donc le séparateur `-c:` d’éléments est inséré entre les éléments de la liste d’éléments `@(Phrase)` .

Pour cet exemple, la commande équivalente de ligne de commande est la suivante :

`findstr /i /c:hello /c:world /c:msbuild phrases.txt`

```xml
<Project DefaultTargets = "Find"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >

    <ItemGroup>
        <Phrase Include="hello"/>
        <Phrase Include="world"/>
        <Phrase Include="msbuild"/>
    </ItemGroup>

    <Target Name = "Find">
        <!-- Find some strings in a file -->
        <Exec Command="findstr /i /c:@(Phrase, ' /c:') phrases.txt"/>
    </Target>
</Project>
```

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur MSBuild](../msbuild/msbuild-reference.md)
- [Éléments](../msbuild/msbuild-items.md)
