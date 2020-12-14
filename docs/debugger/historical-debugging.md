---
title: Débogage d’historique | Microsoft Docs
description: Dépannez une application en inspectant son état à mesure que vous progressez vers l’avant et vers l’arrière dans son exécution. IntelliTrace collecte les informations pour cette fonctionnalité.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 7cc5ddf2-2f7c-4f83-b7ca-58e92e9bfdd2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 38166f777153206ad4b862ac473226aecdff4147
ms.sourcegitcommit: 40d758f779d42c66cb02ae7face8a62763a8662b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2020
ms.locfileid: "97398543"
---
# <a name="historical-debugging-c-visual-basic-c"></a>Débogage d’historique (C#, Visual Basic, C++)

Le débogage d'historique est un mode de débogage qui repose sur les informations recueillies par IntelliTrace. Il vous permet de parcourir l'exécution de votre application et d'inspecter son état.

 Vous pouvez utiliser IntelliTrace dans Visual Studio Enterprise Edition (mais pas dans les éditions Professional ou Community).

## <a name="why-use-historical-debugging"></a>Pourquoi utiliser le débogage d’historique ?

 La définition de points d'arrêt pour rechercher des bogues peut être assez aléatoire. Vous définissez un point d'arrêt proche de l'endroit dans votre code où vous pensez que se trouve le bogue, puis vous exécutez l'application dans le débogueur en espérant que votre point d'arrêt soit atteint et que l'endroit où l'exécution s'arrête puisse révéler la source du bogue. Si ce n’est pas le cas, vous devez essayer de définir un point d’arrêt autre part dans le code puis réexécuter le débogueur, en réexécutant vos étapes de façon répétée jusqu’à ce que vous puissiez identifier le problème.

 ![définition d’un point d’arrêt](../debugger/media/breakpointprocesa.png "BreakpointProcesa")

 Vous pouvez utiliser IntelliTrace et le débogage d’historique pour parcourir votre application et inspecter son état (pile des appels et variables locales) sans avoir à définir des points d’arrêt, à redémarrer le débogage et à répéter les étapes de test. Vous pouvez gagner beaucoup de temps, en particulier quand le bogue se trouve loin dans un scénario de test dont l'exécution est  très longue.

## <a name="how-do-i-start-using-historical-debugging"></a>Comment utiliser le débogage d’historique ?

IntelliTrace est activé par défaut. Il vous suffit de choisir les événements et les appels de fonction qui vous intéressent, et de déterminer si vous souhaitez afficher des instantanés de l’état complet de votre application. Pour plus d’informations sur l’identification de ce que vous voulez rechercher, consultez [Fonctionnalités d’IntelliTrace](../debugger/intellitrace-features.md). La prise en charge des fonctionnalités varie selon la langue et le type d’application.

- Pour afficher les instantanés avec le débogage d’historique, consultez [inspecter les États d’application précédents à l’aide d’IntelliTrace](../debugger/view-historical-application-state.md)
- Pour savoir comment inspecter des variables et parcourir le code, consultez [inspecter votre application avec le débogage d’historique](../debugger/historical-debugging-inspect-app.md)
- Pour en savoir plus sur le débogage avec des événements IntelliTrace, consultez [procédure pas à pas : utilisation d’IntelliTrace](../debugger/walkthrough-using-intellitrace.md).