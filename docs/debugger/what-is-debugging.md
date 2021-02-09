---
title: Qu’est-ce que le débogage ?
description: Comprendre ce que cela signifie pour déboguer une application
ms.custom: debug-experiment
ms.date: 10/17/2018
ms.topic: conceptual
helpviewer_keywords:
- debugger
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3435b7a270d89dc38f5ff10a1350418a24f91c0a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99883933"
---
# <a name="what-is-debugging"></a>Qu’est-ce que le débogage ?

Le débogueur Visual Studio est un outil puissant. Avant de montrer comment l’utiliser, nous souhaitons parler de certains termes tels que le *débogueur*, le *débogage* et le *mode débogage*. De cette façon, lorsque nous parlons plus tard de la recherche et de la résolution des bogues, nous parlerons de la même chose.

## <a name="debugger-vs-debugging"></a>Débogueur et débogage

Le terme *débogage* peut signifier un grand nombre de choses différentes, mais la plupart du fait, cela implique de supprimer les bogues de votre code. À présent, il existe de nombreuses façons de procéder. Par exemple, vous pouvez déboguer en analysant votre code pour rechercher des fautes de frappe, ou à l’aide d’un analyseur de code. Vous pouvez déboguer du code à l’aide d’un profileur de performances. Vous pouvez également déboguer à l’aide d’un *débogueur*.

Un débogueur est un outil de développement très spécialisé qui s’attache à votre application en cours d’exécution et vous permet d’inspecter votre code. Dans la documentation de débogage de Visual Studio, c’est généralement ce que nous voulons dire quand nous disons « débogage ».

## <a name="debug-mode-vs-running-your-app"></a>Mode débogage et exécution de votre application

Quand vous exécutez votre application dans Visual Studio pour la première fois, vous pouvez la démarrer en appuyant sur le bouton fléché vert ![Démarrer le débogage](../debugger/media/dbg-tour-start-debugging.png "Démarrer le débogage") dans la barre d’outils (ou **F5**). Par défaut, la valeur de **débogage** apparaît dans la liste déroulante à gauche. Si vous ne connaissez pas Visual Studio, cela peut vous donner l’impression que le débogage de votre application s’effectue avec l’exécution de votre application, ce qu’elle fait, mais il s’agit fondamentalement de deux tâches très différentes.

![Sélectionner une version Debug](../debugger/media/what-is-debugging-debug-build.png)

Une valeur de **débogage** indique une configuration de débogage. Quand vous démarrez l’application (en appuyant sur la flèche verte ou **F5**) dans une configuration de débogage, vous démarrez l’application en *mode débogage*, ce qui signifie que vous exécutez votre application avec un débogueur attaché. Cela permet d’obtenir un jeu complet de fonctionnalités de débogage que vous pouvez utiliser pour identifier les bogues dans votre application.

Si vous avez un projet ouvert, choisissez le sélecteur de liste déroulante où il indique **Déboguer** , puis choisissez **version Release** à la place.

![Sélectionner une version Release](../debugger/media/what-is-debugging-release-build.png)

Lorsque vous changez ce paramètre, vous modifiez votre projet d’une configuration de débogage à une configuration Release. Les projets Visual Studio ont des configurations Release et Debug distinctes pour votre programme. Vous générez la version Debug pour le débogage et la version Release pour la distribution de la version finale. Une version Release est optimisée pour les performances, mais une version Debug est préférable au débogage.

## <a name="when-to-use-a-debugger"></a>Quand utiliser un débogueur

Le débogueur est un outil essentiel pour rechercher et corriger les bogues dans vos applications. Toutefois, le contexte est roi et il est important de tirer parti de tous les outils de votre jetable pour vous aider à éliminer rapidement les bogues ou les erreurs. Parfois, le bon « outil » peut être une meilleure pratique de codage. En apprenant quand utiliser le débogueur ou un autre outil, vous apprendrez également comment utiliser le débogueur plus efficacement.

## <a name="next-steps"></a>Étapes suivantes

Dans cet article, vous avez découvert quelques concepts généraux liés au débogage. Ensuite, vous pouvez commencer à apprendre à déboguer avec Visual Studio et à écrire du code avec moins de bogues. Les articles suivants présentent des exemples de code C#, mais les concepts s’appliquent à tous les langages pris en charge par Visual Studio.

> [!div class="nextstepaction"]
> [Débogage pour grands débutants](../debugger/debugging-absolute-beginners.md)

> [!div class="nextstepaction"]
> [Techniques et outils de débogage](../debugger/write-better-code-with-visual-studio.md)
