---
title: Arrêter le débogage en cours, boîte de dialogue | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.debug.stopnow
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
helpviewer_keywords:
- Stop Debugging in Progress dialog box
ms.assetid: ed7ef49d-e25f-4a4d-9396-9bc7b4143117
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3beefe16f8883eb64d7d0a2641cabf9eb1f702fa
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72729655"
---
# <a name="stop-debugging-in-progress-dialog-box"></a>Arrêt du débogage en cours (boîte de dialogue)
Cette boîte de dialogue s'affiche lorsque le débogueur tente d'arrêter une session de débogage, mais que l'arrêt de la session prend du temps. L'arrêt d'une session de débogage est généralement très rapide et cette boîte de dialogue ne s'affiche pas. Cependant, il arrive que l'opération prenne du temps pour détacher tous les processus débogués. Si l'arrêt de la session dépasse quelques secondes (ou si une erreur de détachement se produit), cette boîte de dialogue apparaît. Si cela se produit fréquemment, cela peut être dû à un problème interne et vous pouvez contacter le Support Technique Microsoft.

 Vous pouvez attendre le détachement des processus et la disparition de cette boîte de dialogue, ou utiliser le bouton **Arrêter maintenant** pour forcer l’arrêt immédiat.

 **Arrêter maintenant** Cliquez sur ce bouton pour mettre fin immédiatement à la session de débogage. L’utilisation de **Stop Now** se termine plutôt que le détachement des processus en cours de débogage. Si vous déboguez des processus système, l’arrêt de ces processus avec **Arrêter maintenant** peut entraîner des effets inattendus et indésirables.

## <a name="see-also"></a>Voir aussi
- [Sécurité du débogueur](../debugger/debugger-security.md)
- [Détachement de programmes](/previous-versions/visualstudio/visual-studio-2010/x1thkxez(v=vs.100))