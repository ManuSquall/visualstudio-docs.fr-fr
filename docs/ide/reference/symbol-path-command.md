---
title: Chemin d’accès aux symboles, commande
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.symbolpath
helpviewer_keywords:
- symbol path command
- Debug.SymbolPath command
- SymbolPath command
ms.assetid: b697ef2d-3f5d-40df-b113-7068a5bec0d4
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d7a2e4c789f4bd2637cd4da79d66071cc94d697f
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72748595"
---
# <a name="symbol-path-command"></a>Chemin d’accès aux symboles, commande
Définit la liste des répertoires où le débogueur recherche des symboles.

## <a name="syntax"></a>Syntaxe

```
Debug.SymbolPath pathname1;pathname2;... pathnameN
```

## <a name="arguments"></a>Arguments
`pathname`

Optionnel. Liste de chemins délimités par des points-virgules dans laquelle le débogueur doit rechercher des symboles.

## <a name="remarks"></a>Notes
Si aucun `pathname` n’est spécifié, la commande répertorie les chemins des symboles actuels.

## <a name="example"></a>Exemple
Cet exemple ajoute deux chemins à la liste des répertoires de symboles.

```
Debug.SymbolPath C:\Symbol Path 1;C:\Symbol Path 2
```

## <a name="example"></a>Exemple
Cet exemple affiche une liste de chemins des symboles actuels délimités par des points-virgules.

```
Debug.SymbolPath
```

## <a name="see-also"></a>Voir aussi

- [Commande, fenêtre](../../ide/reference/command-window.md)
- [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)