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
ms.openlocfilehash: c18d825ae61dd80ab7b72e1e14c7dc3412582317
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33704471"
---
# <a name="set-radix-command"></a>Définir la base, commande
Définit ou retourne la base numérique utilisée pour afficher les valeurs entières.

## <a name="syntax"></a>Syntaxe

```cmd
Debug.SetRadix [10 | 16 | hex | dec]
```

## <a name="arguments"></a>Arguments
 `10` ou `16` ou `hex` ou `dec`

 Facultative. Indique un nombre décimal (10 ou dec) ou hexadécimal (16 ou hex). Si l’argument est omis, la valeur actuelle de la base est retournée.

## <a name="example"></a>Exemple
 Cet exemple configure l’environnement pour afficher les valeurs entières au format hexadécimal.

```cmd
>Debug.SetRadix hex
```

## <a name="see-also"></a>Voir aussi

- [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Commande, fenêtre](../../ide/reference/command-window.md)
- [Rechercher/Commande, zone](../../ide/find-command-box.md)
- [Alias de commandes Visual Studio](../../ide/reference/visual-studio-command-aliases.md)