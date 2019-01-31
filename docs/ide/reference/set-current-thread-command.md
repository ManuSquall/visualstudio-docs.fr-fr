---
title: Définir le thread en cours, commande
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- debug.setcurrentthread
helpviewer_keywords:
- Set Current Thread command
- Debug.SetCurrentThread command
ms.assetid: 9917ed1d-6c30-4d94-b2f0-69acce74f1b2
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dcfbceba1cc9d0b24c135a8ce25fbd2f3d367f55
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54924134"
---
# <a name="set-current-thread-command"></a>Définir le thread en cours, commande
Définit le thread spécifié comme thread actuel.

## <a name="syntax"></a>Syntaxe

```
Debug.SetCurrentThread index
```

## <a name="arguments"></a>Arguments
 `index`

 Obligatoire. Sélectionne un thread par son index.

## <a name="example"></a>Exemple

```
>Debug.SetCurrentThread 1
```

## <a name="see-also"></a>Voir aussi

- [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Commande, fenêtre](../../ide/reference/command-window.md)
- [Rechercher/Commande, zone](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)