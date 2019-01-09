---
title: -Diff
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
ms.assetid: 5377fedb-632a-4e86-a947-7c11c86451e7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cf58c25611fd52c6e8db8e8210101e1c80153275
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53844536"
---
# <a name="diff"></a>/Diff
Compare deux fichiers. Les différences sont affichées dans une fenêtre spéciale de Visual Studio.

## <a name="syntax"></a>Syntaxe

```cmd
devenv /Diff SourceFile, TargetFile, [SourceDisplayName],[TargetDisplayName]
```

## <a name="arguments"></a>Arguments
 `SourceFile`

 Obligatoire. Chemin complet et nom du premier fichier à comparer.

 `TargetFile`

 Obligatoire. Chemin complet et nom du deuxième fichier à comparer.

 `SourceDisplayName`

 Optionnel. Nom d’affichage du premier fichier.

 `TargetDisplayName`

 Optionnel. Nom d’affichage du deuxième fichier.