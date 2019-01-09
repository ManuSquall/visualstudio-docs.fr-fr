---
title: Définir le processus actuel
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
helpviewer_keywords:
- Debug.SetCurrentProcess command
- Set Current Process command
ms.assetid: 1e016ebd-aadd-411f-a606-03bf69d3f8aa
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0c01c399dc76d1b328443edef27edd9a921b1b9c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53855281"
---
# <a name="set-current-process"></a>Définir le processus actuel
Définit le processus spécifié comme processus actif dans le débogueur.

## <a name="syntax"></a>Syntaxe

```cmd
Debug.SetCurrentProcess index
```

## <a name="arguments"></a>Arguments
 `index`

 Obligatoire. Index du processus.

## <a name="remarks"></a>Notes
 Pendant le débogage, vous pouvez attacher plusieurs processus à la fois, mais seul l’un d’entre eux est actif dans le débogueur à un moment donné. Vous pouvez utiliser la commande `SetCurrentProcess` pour définir le processus actif.

## <a name="example"></a>Exemple

```cmd
>Debug.SetCurrentProcess 1
```

## <a name="see-also"></a>Voir aussi

- [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Commande, fenêtre](../../ide/reference/command-window.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)