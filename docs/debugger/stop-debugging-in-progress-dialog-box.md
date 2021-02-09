---
title: Arrêter le débogage en cours, boîte de dialogue | Microsoft Docs
description: Explorez la boîte de dialogue arrêter le débogage en cours, qui apparaît lorsque le débogueur tente d’arrêter une session de débogage, mais l’arrêt de la session prend du temps.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ae8cb1935a5f88335411d5284f32267a9a65e4da
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99904969"
---
# <a name="stop-debugging-in-progress-dialog-box"></a>Arrêt du débogage en cours (boîte de dialogue)
Cette boîte de dialogue s'affiche lorsque le débogueur tente d'arrêter une session de débogage, mais que l'arrêt de la session prend du temps. L'arrêt d'une session de débogage est généralement très rapide et cette boîte de dialogue ne s'affiche pas. Cependant, il arrive que l'opération prenne du temps pour détacher tous les processus débogués. Si l'arrêt de la session dépasse quelques secondes (ou si une erreur de détachement se produit), cette boîte de dialogue apparaît. Si cela se produit fréquemment, cela peut être dû à un problème interne et vous pouvez contacter le Support Technique Microsoft.

 Vous pouvez attendre le détachement des processus et la disparition de cette boîte de dialogue, ou utiliser le bouton **Arrêter maintenant** pour forcer l’arrêt immédiat.

 **Arrêter maintenant** Cliquez sur ce bouton pour mettre fin immédiatement à la session de débogage. L’utilisation de **Stop Now** se termine plutôt que le détachement des processus en cours de débogage. Si vous déboguez des processus système, l’arrêt de ces processus avec **Arrêter maintenant** peut entraîner des effets inattendus et indésirables.

## <a name="see-also"></a>Voir aussi
- [Sécurité du débogueur](../debugger/debugger-security.md)
- [Détachement de programmes](/previous-versions/visualstudio/visual-studio-2010/x1thkxez(v=vs.100))