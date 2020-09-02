---
title: Évaluer l’instruction, commande | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.evaluatestatement
helpviewer_keywords:
- Debug.EvaluateStatement command
- Evaluate Statement command
ms.assetid: 032039bc-9477-4f93-9b9d-66d4be0e90f4
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6e2db8596c1c16f5c9fb54a8c7c867b06e997b7b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657709"
---
# <a name="evaluate-statement-command"></a>Évaluer l'instruction, commande
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Évalue et affiche l’instruction donnée.

## <a name="syntax"></a>Syntaxe

```
Debug.EvaluateStatement text
```

## <a name="arguments"></a>Arguments
 `text` Obligatoire. Instruction à évaluer.

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

## <a name="example"></a> Exemple

```
>Debug.EvaluateStatement(a+b)
```

## <a name="see-also"></a>Voir aussi
 [Commande d’impression commande](../../ide/reference/print-command.md) [Visual Studio](../../ide/reference/visual-studio-commands.md) [fenêtre commande](../../ide/reference/command-window.md) [Rechercher/zone](../../ide/find-command-box.md) de commandes [Visual Studio alias de commandes Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
