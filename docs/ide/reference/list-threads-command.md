---
title: Afficher les threads, commande
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.listthreads
helpviewer_keywords:
- ListThreads command
- list threads command
- Debug.ListThreads command
ms.assetid: 34b665c0-d46f-4c1a-a066-b678eba5ac54
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: aa44556be7c20c52d44ec83da1ba9d4972b4542d
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31947428"
---
# <a name="list-threads-command"></a>Afficher les threads, commande
Affiche une liste des threads du programme en cours.

## <a name="syntax"></a>Syntaxe

```
Debug.ListThreads [index]
```

## <a name="arguments"></a>Arguments
 `index`

 Facultative. Sélectionne un thread par son index pour en faire le thread actuel.

## <a name="remarks"></a>Notes
 Une fois spécifié, l’argument `index` marque le thread indiqué comme étant le thread actuel. Un astérisque (*) est affiché dans la liste en regard du thread actuel.

## <a name="example"></a>Exemple

```
>Debug.ListThreads
```

## <a name="see-also"></a>Voir aussi

- [Afficher la pile des appels, commande](../../ide/reference/list-call-stack-command.md)
- [Afficher le code machine, commande](../../ide/reference/list-disassembly-command.md)
- [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Commande, fenêtre](../../ide/reference/command-window.md)
- [Rechercher/Commande, zone](../../ide/find-command-box.md)
- [Alias de commandes Visual Studio](../../ide/reference/visual-studio-command-aliases.md)