---
title: Basculer le point d'arrêt, commande
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.togglebreakpoint
helpviewer_keywords:
- ToggleBreakpoint command
- Debug.ToggleBreakPoint command
- Toggle Breakpoint command
ms.assetid: d50dfadb-ce79-4d5e-9c09-1cfddd57876d
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d72ec4717a7669fd5b4d489b8324f2e0b25c57c0
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72644707"
---
# <a name="toggle-breakpoint-command"></a>Basculer le point d'arrêt, commande
Active ou désactive le point d’arrêt, en fonction de son état actuel, à l’emplacement actuel dans le fichier.

## <a name="syntax"></a>Syntaxe

```
Debug.ToggleBreakpoint [text]
```

## <a name="arguments"></a>Arguments

`text`\
Optionnel. Si l’argument text est spécifié, la ligne est marquée en tant que point d’arrêt nommé. Sinon, la ligne est marquée en tant que point d’arrêt non nommé, ce qui revient à appuyer sur la touche F9.

## <a name="example"></a>Exemple
L’exemple suivant bascule le point d’arrêt actuel.

```
>Debug.ToggleBreakpoint
```

## <a name="see-also"></a>Voir aussi

- [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Commande, fenêtre](../../ide/reference/command-window.md)
- [Rechercher/Commande, zone](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)