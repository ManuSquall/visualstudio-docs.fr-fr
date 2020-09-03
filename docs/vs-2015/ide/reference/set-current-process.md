---
title: Définir le processus actuel | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Debug.SetCurrentProcess command
- Set Current Process command
ms.assetid: 1e016ebd-aadd-411f-a606-03bf69d3f8aa
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c362d3f5dda5015e91ac88dd8f0abd60a185ba72
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72665463"
---
# <a name="set-current-process"></a>Définir le processus actuel
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Définit le processus spécifié comme processus actif dans le débogueur.

## <a name="syntax"></a>Syntaxe

```
Debug.SetCurrentProcess index
```

## <a name="arguments"></a>Arguments
 `index` Obligatoire. Index du processus.

## <a name="remarks"></a>Notes
 Pendant le débogage, vous pouvez attacher plusieurs processus à la fois, mais seul l’un d’entre eux est actif dans le débogueur à un moment donné. Vous pouvez utiliser la commande `SetCurrentProcess` pour définir le processus actif.

## <a name="example"></a> Exemple

```
>Debug.SetCurrentProcess 1
```

## <a name="see-also"></a>Voir aussi
 Fenêtres de commandes de la [fenêtre commande](../../ide/reference/command-window.md) [Visual](../../ide/reference/visual-studio-commands.md) Studio [alias de commandes Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
