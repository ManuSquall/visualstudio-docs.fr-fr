---
title: Définir la base, commande | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.setradix
helpviewer_keywords:
- Set Radix command
- Debug.SetRadix command
ms.assetid: 6ffd1554-7530-4da4-b5f5-e276a5034f3b
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 050cbe6e639f4177694d9af3ecbc0b768065b7d9
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665416"
---
# <a name="set-radix-command"></a>Définir la base, commande
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Définit ou retourne la base numérique utilisée pour afficher les valeurs entières.

## <a name="syntax"></a>Syntaxe

```
Debug.SetRadix [10 | 16 | hex | dec]
```

## <a name="arguments"></a>Arguments
 `10` ou `16` ou `hex` ou `dec` facultatif. Indique un nombre décimal (10 ou dec) ou hexadécimal (16 ou hex). Si l’argument est omis, la valeur actuelle de la base est retournée.

## <a name="example"></a>Exemples
 Cet exemple configure l’environnement pour afficher les valeurs entières au format hexadécimal.

```
>Debug.SetRadix hex
```

## <a name="see-also"></a>Voir aussi
 [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md) [fenêtre commande](../../ide/reference/command-window.md) [Rechercher/zone de commande](../../ide/find-command-box.md) [alias de commandes Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
