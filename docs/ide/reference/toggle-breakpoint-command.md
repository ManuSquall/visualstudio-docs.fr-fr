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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5d393890e6166b4a4ef53c9520a556e9a9edd64d
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75597319"
---
# <a name="toggle-breakpoint-command"></a>Basculer le point d'arrêt, commande
Active ou désactive le point d’arrêt, en fonction de son état actuel, à l’emplacement actuel dans le fichier.

## <a name="syntax"></a>Syntaxe

```
Debug.ToggleBreakpoint [text]
```

## <a name="arguments"></a>Arguments

`text`\
Option facultative. Si l’argument text est spécifié, la ligne est marquée en tant que point d’arrêt nommé. Sinon, la ligne est marquée en tant que point d’arrêt non nommé, ce qui revient à appuyer sur la touche F9.

## <a name="example"></a>Exemple
L’exemple suivant bascule le point d’arrêt actuel.

```
>Debug.ToggleBreakpoint
```

## <a name="see-also"></a>Voir aussi

- [Visual Studio, commandes](../../ide/reference/visual-studio-commands.md)
- [Fenêtre Commande](../../ide/reference/command-window.md)
- [Rechercher/Commande, zone](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
