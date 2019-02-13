---
title: -Diff (devenv.exe)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- Devenv, /Diff switch
- /Diff Devenv switch
- Diff Devenv switch
ms.assetid: 5377fedb-632a-4e86-a947-7c11c86451e7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c2e69435a319a9730af846a912cb3f90a12d4ac8
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55918467"
---
# <a name="diff-devenvexe"></a>/Diff (devenv.exe)

Compare deux fichiers. Les différences sont affichées dans une fenêtre spéciale de Visual Studio.

## <a name="syntax"></a>Syntaxe

```shell
devenv /Diff SourceFile TargetFile [SourceDisplayName [TargetDisplayName]]
```

## <a name="arguments"></a>Arguments

- *SourceFile*

  Obligatoire. Chemin complet et nom du premier fichier à comparer.

- *TargetFile*

  Obligatoire. Chemin complet et nom du second fichier à comparer.

- *SourceDisplayName*

  Optionnel. Nom d’affichage du premier fichier.

- *TargetDisplayName*

  Optionnel. Nom d’affichage du deuxième fichier.

## <a name="remarks"></a>Notes

S’il y a déjà une instance de l’environnement IDE ouverte, la comparaison de fichiers s’affiche dans un onglet de cet environnement.

## <a name="example"></a>Exemple

Le premier exemple compare deux fichiers sans modifier leur nom d’affichage. Le second exemple compare les fichiers en modifiant les deux noms d’affichage. Le troisième et le quatrième exemples comparent deux fichiers, mais appliquent un alias soit au premier, soit au second.

```shell
devenv /diff File1.txt File2.txt

devenv /diff File1.txt File2.txt FirstAlias "Second Alias"

devenv /diff File1.txt File2.txt "File One"

devenv /diff File1.txt File2.txt "" FileTwo
```

## <a name="see-also"></a>Voir aussi

- [Commutateurs de ligne de commande Devenv](../../ide/reference/devenv-command-line-switches.md)
