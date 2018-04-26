---
title: Définir la base, commande
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.setradix
helpviewer_keywords:
- Set Radix command
- Debug.SetRadix command
ms.assetid: 6ffd1554-7530-4da4-b5f5-e276a5034f3b
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f23e2492a183dcae2e2b3cb87e39b08f66a7c2ae
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="set-radix-command"></a>Définir la base, commande
Définit ou retourne la base numérique utilisée pour afficher les valeurs entières.

## <a name="syntax"></a>Syntaxe

```
Debug.SetRadix [10 | 16 | hex | dec]
```

## <a name="arguments"></a>Arguments
 `10` ou `16` ou `hex` ou `dec`

 Facultative. Indique un nombre décimal (10 ou dec) ou hexadécimal (16 ou hex). Si l’argument est omis, la valeur actuelle de la base est retournée.

## <a name="example"></a>Exemple
 Cet exemple configure l’environnement pour afficher les valeurs entières au format hexadécimal.

```
>Debug.SetRadix hex
```

## <a name="see-also"></a>Voir aussi

- [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Commande, fenêtre](../../ide/reference/command-window.md)
- [Rechercher/Commande, zone](../../ide/find-command-box.md)
- [Alias de commandes Visual Studio](../../ide/reference/visual-studio-command-aliases.md)