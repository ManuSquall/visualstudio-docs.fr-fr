---
title: Basculer le point d'arrêt, commande
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.togglebreakpoint
helpviewer_keywords:
- ToggleBreakpoint command
- Debug.ToggleBreakPoint command
- Toggle Breakpoint command
ms.assetid: d50dfadb-ce79-4d5e-9c09-1cfddd57876d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 14f4d60bcbf7c7f394d62cc881c78ef9aa51e545
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31946804"
---
# <a name="toggle-breakpoint-command"></a>Basculer le point d'arrêt, commande
Active ou désactive le point d’arrêt, en fonction de son état actuel, à l’emplacement actuel dans le fichier.

## <a name="syntax"></a>Syntaxe

```
Debug.ToggleBreakpoint [text]
```

## <a name="arguments"></a>Arguments
 `text` (facultatif). Si l’argument text est spécifié, la ligne est marquée en tant que point d’arrêt nommé. Sinon, la ligne est marquée en tant que point d’arrêt non nommé, ce qui revient à appuyer sur la touche F9.

## <a name="example"></a>Exemple
 L’exemple suivant bascule le point d’arrêt actuel.

```
>Debug.ToggleBreakpoint
```

## <a name="see-also"></a>Voir aussi

- [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Commande, fenêtre](../../ide/reference/command-window.md)
- [Rechercher/Commande, zone](../../ide/find-command-box.md)
- [Alias de commandes Visual Studio](../../ide/reference/visual-studio-command-aliases.md)