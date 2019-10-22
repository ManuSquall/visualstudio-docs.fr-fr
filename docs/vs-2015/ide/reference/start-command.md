---
title: Démarrer, commande | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.start
helpviewer_keywords:
- Start command
- Debug.Start command
ms.assetid: dc4e4aa2-b0ab-4e00-92db-6dc3058ddc21
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a216e053a08662da5da04206c780fb4455e9ec09
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663495"
---
# <a name="start-command"></a>Démarrer, commande
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Commence le débogage du projet de démarrage.

## <a name="syntax"></a>Syntaxe

```
Debug.Start [address]
```

## <a name="arguments"></a>Arguments
 `address` Facultatif. Adresse à laquelle le programme suspend son exécution, semblable à un point d’arrêt dans le code source. Cet argument est valide uniquement en mode débogage.

## <a name="remarks"></a>Remarques
 Quand elle est exécutée, la commande **Start** effectue une opération RunToCursor vers l’adresse spécifiée.

## <a name="example"></a>Exemples
 Cet exemple démarre le débogueur et ignore toute exception qui peut se produire.

```
>Debug.Start
```

## <a name="see-also"></a>Voir aussi
 [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md) [fenêtre commande](../../ide/reference/command-window.md) [Rechercher/zone de commande](../../ide/find-command-box.md) [alias de commandes Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
