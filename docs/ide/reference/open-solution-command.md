---
title: Ouvrir une solution, commande
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- file.opensolution
helpviewer_keywords:
- Open Solution command
- File.OpenSolution command
ms.assetid: 61de76c8-69d7-4cdb-b605-e132f45d05d9
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 652305e6d5d360169645e7801e788b39b8982400
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="open-solution-command"></a>Ouvrir une solution, commande
Ouvre une solution existante, en fermant toutes les autres solutions ouvertes.

## <a name="syntax"></a>Syntaxe

```
File.OpenSolution filename
```

## <a name="arguments"></a>Arguments
 `Filename`

 Obligatoire. Chemin complet et nom de fichier de la solution à ouvrir.

 La syntaxe de l’argument `filename` nécessite que les chemins contenant des espaces utilisent des guillemets.

## <a name="remarks"></a>Notes
 La saisie semi-automatique tente de deviner le chemin et le nom de fichier à mesure que vous tapez.

## <a name="example"></a>Exemple
 Cet exemple ouvre la solution Test1.sln.

```
>File.OpenSolution "c:\MySolutions\Test1\Test1.sln"
```

## <a name="see-also"></a>Voir aussi

- [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Commande, fenêtre](../../ide/reference/command-window.md)
- [Rechercher/Commande, zone](../../ide/find-command-box.md)
- [Alias de commandes Visual Studio](../../ide/reference/visual-studio-command-aliases.md)