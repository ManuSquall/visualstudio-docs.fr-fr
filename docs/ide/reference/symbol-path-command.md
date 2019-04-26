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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 23a7a59ca23dc444bcdc714ade2fce5bedb87e8c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62945126"
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

## <a name="remarks"></a>Remarques
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