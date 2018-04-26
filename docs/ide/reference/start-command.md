---
title: Démarrer, commande
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.start
helpviewer_keywords:
- Start command
- Debug.Start command
ms.assetid: dc4e4aa2-b0ab-4e00-92db-6dc3058ddc21
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c1e5ade7d02882633504ac5615ee751b2533adde
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="start-command"></a>Démarrer, commande
Commence le débogage du projet de démarrage.

## <a name="syntax"></a>Syntaxe

```
Debug.Start [address]
```

## <a name="arguments"></a>Arguments
 `address`

 Facultative. Adresse à laquelle le programme suspend son exécution, semblable à un point d’arrêt dans le code source. Cet argument est valide uniquement en mode débogage.

## <a name="remarks"></a>Notes
 Quand elle est exécutée, la commande **Start** effectue une opération RunToCursor vers l’adresse spécifiée.

## <a name="example"></a>Exemple
 Cet exemple démarre le débogueur et ignore toute exception qui peut se produire.

```
>Debug.Start
```

## <a name="see-also"></a>Voir aussi

- [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Commande, fenêtre](../../ide/reference/command-window.md)
- [Rechercher/Commande, zone](../../ide/find-command-box.md)
- [Alias de commandes Visual Studio](../../ide/reference/visual-studio-command-aliases.md)