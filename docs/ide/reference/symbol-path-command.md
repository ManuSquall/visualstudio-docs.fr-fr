---
title: Chemin d’accès aux symboles, commande
description: En savoir plus sur la commande Symbol Path et la façon dont elle définit la liste des répertoires pour que le débogueur recherche des symboles.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.symbolpath
helpviewer_keywords:
- symbol path command
- Debug.SymbolPath command
- SymbolPath command
ms.assetid: b697ef2d-3f5d-40df-b113-7068a5bec0d4
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bd3268f3c40736f85a18b35e33c6cc78c96d6c88
ms.sourcegitcommit: 2cf87f79762906ccaa133a7645aa4c77a0bed7da
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2020
ms.locfileid: "96616445"
---
# <a name="symbol-path-command"></a>Chemin d’accès aux symboles, commande
Définit la liste des répertoires où le débogueur recherche des symboles.

## <a name="syntax"></a>Syntaxe

```
Debug.SymbolPath pathname1;pathname2;... pathnameN
```

## <a name="arguments"></a>Arguments
`pathname`

facultatif. Liste de chemins délimités par des points-virgules dans laquelle le débogueur doit rechercher des symboles.

## <a name="remarks"></a>Remarques
Si aucun `pathname` n’est spécifié, la commande répertorie les chemins des symboles actuels.

## <a name="example-1"></a>Exemple 1
Cet exemple ajoute deux chemins à la liste des répertoires de symboles.

```
Debug.SymbolPath C:\Symbol Path 1;C:\Symbol Path 2
```

## <a name="example-2"></a>Exemple 2
Cet exemple affiche une liste de chemins des symboles actuels délimités par des points-virgules.

```
Debug.SymbolPath
```

## <a name="see-also"></a>Voir aussi

- [Fenêtre commande](../../ide/reference/command-window.md)
- [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)
