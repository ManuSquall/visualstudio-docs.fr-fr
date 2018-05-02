---
title: -Diff
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
ms.assetid: 5377fedb-632a-4e86-a947-7c11c86451e7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 81c70c238a4503fbd05249ef6522cf020c00221c
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="diff"></a>/Diff
Compare deux fichiers. Les différences sont affichées dans une fenêtre spéciale de Visual Studio.

## <a name="syntax"></a>Syntaxe

```
devenv /Diff SourceFile, TargetFile, [SourceDisplayName],[TargetDisplayName]
```

## <a name="arguments"></a>Arguments
 `SourceFile`

 Obligatoire. Chemin complet et nom du premier fichier à comparer.

 `TargetFile`

 Obligatoire. Chemin complet et nom du deuxième fichier à comparer.

 `SourceDisplayName`

 Facultative. Nom d’affichage du premier fichier.

 `TargetDisplayName`

 Facultative. Nom d’affichage du deuxième fichier.