---
title: Débogage d’historique | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 7cc5ddf2-2f7c-4f83-b7ca-58e92e9bfdd2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e44e62997cac1060047de03253880bbf577935da
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60075321"
---
# <a name="historical-debugging-c-visual-basic-c"></a>Débogage d’historique (C#, Visual Basic, C++)

Le débogage d'historique est un mode de débogage qui repose sur les informations recueillies par IntelliTrace. Il vous permet de parcourir l'exécution de votre application et d'inspecter son état.

 Vous pouvez utiliser IntelliTrace dans Visual Studio Enterprise Edition (mais pas dans les éditions Professional ou Community).

## <a name="why-use-historical-debugging"></a>Pourquoi utiliser le débogage d’historique ?

 La définition de points d'arrêt pour rechercher des bogues peut être assez aléatoire. Vous définissez un point d'arrêt proche de l'endroit dans votre code où vous pensez que se trouve le bogue, puis vous exécutez l'application dans le débogueur en espérant que votre point d'arrêt soit atteint et que l'endroit où l'exécution s'arrête puisse révéler la source du bogue. Si ce n’est pas le cas, vous devez essayer de définir un point d’arrêt autre part dans le code puis réexécuter le débogueur, en réexécutant vos étapes de façon répétée jusqu’à ce que vous puissiez identifier le problème.

 ![définir un point d’arrêt](../debugger/media/breakpointprocesa.png "BreakpointProcesa")

 Vous pouvez utiliser IntelliTrace et le débogage d’historique pour parcourir votre application et inspecter son état (pile des appels et variables locales) sans avoir à définir des points d’arrêt, à redémarrer le débogage et à répéter les étapes de test. Vous pouvez gagner beaucoup de temps, en particulier quand le bogue se trouve loin dans un scénario de test dont l'exécution est  très longue.

## <a name="how-do-i-start-using-historical-debugging"></a>Comment utiliser le débogage d’historique ?

IntelliTrace est activé par défaut. Il vous suffit est de déterminer les événements et les appels de fonction présentent un intérêt pour vous, et si vous souhaitez afficher les captures instantanées de votre état complet des applications. Pour plus d’informations sur l’identification de ce que vous voulez rechercher, consultez [Fonctionnalités d’IntelliTrace](../debugger/intellitrace-features.md). Prise en charge de la fonctionnalité varie selon la langue et application type.

- Pour afficher des captures instantanées avec le débogage d’historique, consultez [Inspecter les États d’application précédent à l’aide d’IntelliTrace](../debugger/view-historical-application-state.md)
- Pour savoir comment inspecter des variables et parcourir le code, consultez [Inspecter votre application avec le débogage d’historique](../debugger/historical-debugging-inspect-app.md)
- Pour en savoir plus sur le débogage avec des événements IntelliTrace, consultez [procédure pas à pas : À l’aide d’IntelliTrace](../debugger/walkthrough-using-intellitrace.md).