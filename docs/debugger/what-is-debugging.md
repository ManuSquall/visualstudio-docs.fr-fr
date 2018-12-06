---
title: Qu’est-ce que le débogage ?
description: Comprendre ce que cela signifie pour déboguer une application
ms.custom: debug-experiments
ms.date: 10/17/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- debugger
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8f0aa6cbe09f902ef69e1fd5cb3a2d9712cabf28
ms.sourcegitcommit: d7f232a7596420e40ff8051d42cdf90203af4a74
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52821446"
---
# <a name="what-is-debugging"></a>Qu’est-ce que le débogage ?

Le débogueur Visual Studio est un outil puissant. Avant de vous montrer comment l’utiliser, nous voulons parler de certains termes tels que *débogueur*, *débogage*, et *mode débogage*. De cette façon, lorsque nous parlerons plus tard recherche et correction des bogues, nous parlerons de la même chose.

## <a name="debugger-vs-debugging"></a>Débogueur et débogage

Le terme *débogage* peut signifier beaucoup de choses, mais plus littéralement, cela signifie que la suppression des bogues à partir de votre code. Maintenant, il existe de nombreuses manières de procéder. Par exemple, vous pouvez déboguer en analysant votre code à la recherche de frappe, ou à l’aide d’un analyseur de code. Vous pouvez déboguer le code à l’aide d’un profileur de performances. Ou, vous pouvez déboguer en utilisant un *débogueur*.

Un débogueur est un outil de développement très spécialisée qui s’attache à votre application en cours d’exécution et vous permet d’inspecter votre code. Dans la documentation relative au débogage pour Visual Studio, il s’agit en général, ce que nous entendons lorsque nous disons « débogage ».

## <a name="debug-mode-vs-running-your-app"></a>Déboguer en mode et l’exécution de votre application

Lorsque vous exécutez votre application dans Visual Studio pour la première fois, vous pouvez le démarrer en appuyant sur le bouton fléché vert ![démarrer le débogage](../debugger/media/dbg-tour-start-debugging.png "démarrer le débogage") dans la barre d’outils (ou **F5**). Par défaut, le **déboguer** valeur apparaît dans la liste déroulante à gauche. Si vous débutez avec Visual Studio, cela peut exposer l’impression que le débogage de votre application a quelque chose à faire avec exécutant votre application--qu’elle ne les--mais il s’agit fondamentalement de deux tâches très différentes.

![Sélectionnez une version Debug](../debugger/media/what-is-debugging-debug-build.png)

Un **déboguer** valeur indique une configuration debug. Lorsque vous démarrez l’application (appuyez sur la flèche verte ou **F5**) dans une configuration debug, vous démarrez l’application dans *mode débogage*, ce qui signifie que vous exécutez votre application avec un débogueur attaché. Ainsi, un ensemble complet de fonctionnalités que vous pouvez utiliser pour aider à trouver des bogues dans votre application de débogage.

Si vous avez un projet ouvert, choisissez le sélecteur de liste déroulante intitulée **déboguer** et choisissez **version** à la place.

![Sélectionnez une version Release](../debugger/media/what-is-debugging-release-build.png)

Lorsque vous basculez ce paramètre, vous modifiez votre projet à partir d’une configuration debug à une configuration release. Les projets Visual Studio ont des configurations Release et Debug distinctes pour votre programme. Vous générez la version debug pour le débogage et la version release pour la distribution de la version finale. Une version Release est optimisée pour les performances, mais une version debug est préférable pour le débogage.

## <a name="when-to-use-a-debugger"></a>Quand utiliser un débogueur

Le débogueur est un outil essentiel pour rechercher et corriger les bogues dans vos applications. Toutefois, contexte est roi et il est important de tirer parti de tous les outils à votre élément jetable pour vous aider à éliminer rapidement les bogues ou des erreurs. Parfois, le droit « tool » peut être une méthode de codage mieux. En apprenant quand utiliser le débogueur et un autre outil, vous allez également apprendre à utiliser le débogueur plus efficacement. Si vous savez déjà que vous deviez en savoir plus sur le débogueur, consultez [débogage pour les débutants](../debugger/debugging-absolute-beginners.md). Sinon, suivez le lien dans **étapes suivantes**.

## <a name="next-steps"></a>Étapes suivantes

Dans cet article, vous avez découvert quelques concepts généraux liés au débogage. Ensuite, vous pouvez démarrer le débogage avec Visual Studio et comment écrire du code avec moins de bogues d’apprentissage. L’article suivant montre C# exemples de code, mais les concepts s’appliquent à tous les langages pris en charge par Visual Studio.

> [!div class="nextstepaction"]
> [Corriger les bogues en écrivant un meilleur code C#](../debugger/write-better-code-with-visual-studio.md)
