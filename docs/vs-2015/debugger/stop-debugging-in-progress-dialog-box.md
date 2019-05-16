---
title: Arrêter le débogage dans la boîte de dialogue de progression | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.stopnow
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- SQL
- VB
- CSharp
- C++
helpviewer_keywords:
- Stop Debugging in Progress dialog box
ms.assetid: ed7ef49d-e25f-4a4d-9396-9bc7b4143117
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4fc4b72987be726ab06aeb92a0e3eec2a338949e
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65684945"
---
# <a name="stop-debugging-in-progress-dialog-box"></a>Arrêt du débogage en cours (boîte de dialogue)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cette boîte de dialogue s'affiche lorsque le débogueur tente d'arrêter une session de débogage, mais que l'arrêt de la session prend du temps. L'arrêt d'une session de débogage est généralement très rapide et cette boîte de dialogue ne s'affiche pas. Cependant, il arrive que l'opération prenne du temps pour détacher tous les processus débogués. Si l'arrêt de la session dépasse quelques secondes (ou si une erreur de détachement se produit), cette boîte de dialogue apparaît. Si cela se produit fréquemment, cela peut être dû à un problème interne et vous pouvez contacter le Support Technique Microsoft.  
  
 Vous pouvez attendre le détachement des processus et la disparition de cette boîte de dialogue, ou utiliser le bouton **Arrêter maintenant** pour forcer l’arrêt immédiat.  
  
 **Arrêter maintenant**  
 Cliquez sur le bouton pour terminer immédiatement la session de débogage. À l’aide de **arrêter maintenant**prendra fin, plutôt que de détacher les processus en cours de débogage. Si vous déboguez des processus système, l’arrêt de ces processus avec **Arrêter maintenant** peut entraîner des effets inattendus et indésirables.  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurité du débogueur](../debugger/debugger-security.md)   
 [Détachement de programmes](https://msdn.microsoft.com/f2c756c2-8079-474b-94c2-01c19a141a01)
