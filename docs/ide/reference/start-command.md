---
title: Démarrer, commande
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.start
helpviewer_keywords:
- Start command
- Debug.Start command
ms.assetid: dc4e4aa2-b0ab-4e00-92db-6dc3058ddc21
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 946c4e39b48d15352ef5fa8ae240fb3fe9da5b9b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72645233"
---
# <a name="start-command"></a>Démarrer, commande
Commence le débogage du projet de démarrage.

## <a name="syntax"></a>Syntaxe

```cmd
Debug.Start [address]
```

## <a name="arguments"></a>Arguments
`address`

Optionnel. Adresse à laquelle le programme suspend son exécution, semblable à un point d’arrêt dans le code source. Cet argument est valide uniquement en mode débogage.

## <a name="remarks"></a>Notes
Quand elle est exécutée, la commande **Start** effectue une opération RunToCursor vers l’adresse spécifiée.

## <a name="example"></a>Exemple
Cet exemple démarre le débogueur et ignore toute exception qui peut se produire.

```cmd
>Debug.Start
```

## <a name="see-also"></a>Voir aussi

- [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Commande, fenêtre](../../ide/reference/command-window.md)
- [Rechercher/Commande, zone](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)