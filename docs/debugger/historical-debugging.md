---
title: "Débogage d’historique | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7cc5ddf2-2f7c-4f83-b7ca-58e92e9bfdd2
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6507ce8544c2dc3bc9085cbcab70a87f04176c17
ms.sourcegitcommit: fb751e41929f031d1a9247bc7c8727312539ad35
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2017
---
# <a name="historical-debugging"></a>Débogage d’historique
Le débogage d'historique est un mode de débogage qui repose sur les informations recueillies par IntelliTrace. Il vous permet de parcourir l'exécution de votre application et d'inspecter son état.  
  
 Vous pouvez utiliser IntelliTrace dans Visual Studio Enterprise Edition (mais pas dans les éditions Professional ou Community).  
  
## <a name="why-use-historical-debugging"></a>Pourquoi utiliser le débogage d’historique ?  
 La définition de points d'arrêt pour rechercher des bogues peut être assez aléatoire. Vous définissez un point d'arrêt proche de l'endroit dans votre code où vous pensez que se trouve le bogue, puis vous exécutez l'application dans le débogueur en espérant que votre point d'arrêt soit atteint et que l'endroit où l'exécution s'arrête puisse révéler la source du bogue. Si ce n’est pas le cas, vous devrez, essayez de définir un point d’arrêt vers un autre emplacement dans le code et réexécuter le débogueur, l’exécution de vos étapes de test plusieurs fois jusqu'à ce que vous trouviez le problème.  
  
 ![définir un point d’arrêt](../debugger/media/breakpointprocesa.png "BreakpointProcesa")  
  
 Vous pouvez utiliser IntelliTrace et le débogage d’historique à parcourir dans votre application et inspecter son état (pile des appels et les variables locales) sans avoir à définir des points d’arrêt, redémarrez le débogage et répétez les étapes de test. Vous pouvez gagner beaucoup de temps, en particulier quand le bogue se trouve loin dans un scénario de test dont l'exécution est  très longue.  
  
## <a name="how-do-i-start-using-historical-debugging"></a>Comment démarrer à l’aide du débogage d’historique ?  
 IntelliTrace est activé par défaut. Il vous est décider des événements et les appels de fonction sont dignes d’intérêt pour vous, et si vous souhaitez afficher des instantanés de l’état de votre application complète. Pour plus d’informations sur la définition de ce que vous voulez rechercher, consultez [des fonctionnalités IntelliTrace](../debugger/intellitrace-features.md).  

 - Pour afficher des instantanés avec le débogage d’historique, consultez [afficher des instantanés à l’aide d’IntelliTrace étape différée](../debugger/how-to-use-intellitrace-step-back.md)
 - Pour savoir comment inspecter des variables et parcourir le code, consultez [Inspecter votre application avec débogage d’historique](../debugger/historical-debugging-inspect-app.md)
 - Pour en savoir plus sur le débogage avec les événements IntelliTrace, consultez [procédure pas à pas : à l’aide de IntelliTrace](../debugger/walkthrough-using-intellitrace.md).