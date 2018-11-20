---
title: Arrêter le débogage dans la boîte de dialogue de progression | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: 2dba046c57e7b3990b3bf31994da699bed1e6442
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51792279"
---
# <a name="stop-debugging-in-progress-dialog-box"></a>Arrêt du débogage en cours (boîte de dialogue)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cette boîte de dialogue s'affiche lorsque le débogueur tente d'arrêter une session de débogage, mais que l'arrêt de la session prend du temps. L'arrêt d'une session de débogage est généralement très rapide et cette boîte de dialogue ne s'affiche pas. Cependant, il arrive que l'opération prenne du temps pour détacher tous les processus débogués. Si l'arrêt de la session dépasse quelques secondes (ou si une erreur de détachement se produit), cette boîte de dialogue apparaît. Si cela se produit fréquemment, cela peut être dû à un problème interne et vous pouvez contacter le Support Technique Microsoft.  
  
 Vous pouvez attendre les détachement des processus et la boîte de dialogue disparaît, ou utiliser le **arrêter maintenant** bouton pour forcer l’arrêt immédiat.  
  
 **Arrêter maintenant**  
 Cliquez sur le bouton pour terminer immédiatement la session de débogage. À l’aide de **arrêter maintenant**prendra fin, plutôt que de détacher les processus en cours de débogage. Si vous déboguez un processus système, arrêt de ces processus avec **arrêter maintenant** peut avoir des effets inattendus et indésirables.  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurité du débogueur](../debugger/debugger-security.md)   
 [Détachement de programmes](http://msdn.microsoft.com/en-us/f2c756c2-8079-474b-94c2-01c19a141a01)



