---
title: Évaluer l'instruction, commande
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.evaluatestatement
helpviewer_keywords:
- Debug.EvaluateStatement command
- Evaluate Statement command
ms.assetid: 032039bc-9477-4f93-9b9d-66d4be0e90f4
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0c2ec882bb2fdc9d0f3b74a0552c85a7b286617c
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="evaluate-statement-command"></a>Évaluer l'instruction, commande
Évalue et affiche l’instruction donnée.

## <a name="syntax"></a>Syntaxe

```
Debug.EvaluateStatement text
```

## <a name="arguments"></a>Arguments
 `text` (obligatoire). Instruction à évaluer.

## <a name="remarks"></a>Notes
 La fenêtre utilisée pour entrer la commande **EvaluateStatement** détermine si un signe égal (=) est interprété comme un opérateur de comparaison ou comme un opérateur d’assignation.

 Dans la fenêtre **Commande**, un signe égal (=) est interprété comme un opérateur de comparaison. Ainsi, si les valeurs des variables `a` et `b` sont différentes, la commande

```
>Debug.EvaluateStatement(a=b)
```

 retourne la valeur `false`.

 Dans la fenêtre **Exécution**, en revanche, un signe égal (=) est interprété comme un opérateur d’assignation. Ainsi, la commande

```
>Debug.EvaluateStatement(a=b)
```

 assigne à la variable `a` la valeur de variable `b`.

## <a name="example"></a>Exemple

```
>Debug.EvaluateStatement(a+b)
```

## <a name="see-also"></a>Voir aussi

- [Imprimer, commande](../../ide/reference/print-command.md)
- [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Commande, fenêtre](../../ide/reference/command-window.md)
- [Rechercher/Commande, zone](../../ide/find-command-box.md)
- [Alias de commandes Visual Studio](../../ide/reference/visual-studio-command-aliases.md)