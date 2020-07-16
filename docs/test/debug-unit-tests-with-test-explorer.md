---
title: Déboguer des tests unitaires avec l’Explorateur de tests
description: Découvrez comment déboguer des tests unitaires avec l’Explorateur de tests dans Visual Studio.
ms.date: 07/14/2020
ms.topic: how-to
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2def56c6a3860ce0476f448f87bdde25c7970807
ms.sourcegitcommit: a77158415da04e9bb8b33c332f6cca8f14c08f8c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2020
ms.locfileid: "86393528"
---
# <a name="debug-and-analyze-unit-tests-with-test-explorer"></a>Déboguer et analyser des tests unitaires avec l’Explorateur de tests

Vous pouvez utiliser l'Explorateur de tests pour démarrer une session de débogage de vos tests. L’exécution pas à pas de votre code avec le débogueur Visual Studio vous conduit de manière transparente à des allers et retours entre les tests unitaires et le projet testé. Pour démarrer le débogage :

1. Dans l’éditeur Visual Studio, définissez un point d’arrêt dans une ou plusieurs méthodes de test que vous souhaitez déboguer.

    > [!NOTE]
    > Comme les méthodes de test peuvent s’exécuter dans n’importe quel ordre, définissez les points d’arrêt dans toutes les méthodes de test que vous souhaitez déboguer.

::: moniker range="vs-2017"
2. Dans l’Explorateur de tests, sélectionnez la ou les méthodes de test, puis choisissez **déboguer les tests sélectionnés** dans le menu contextuel.
::: moniker-end
::: moniker range=">=vs-2019"
2. Dans l’Explorateur de tests, sélectionnez la ou les méthodes de test, puis choisissez **Déboguer** dans le menu contextuel.

   ![Détails de l'exécution de tests](../test/media/vs-2019/test-explorer-debug.png)
::: moniker-end

   Pour plus d’informations sur le débogueur, consultez [Déboguer dans Visual Studio](../debugger/debugger-feature-tour.md).

## <a name="diagnose-test-method-performance-issues"></a>Diagnostiquer les problèmes de performances de méthode de test

::: moniker range="vs-2017"
Pour diagnostiquer la lenteur d’une méthode de test, sélectionnez-la dans l’Explorateur de tests, puis choisissez **Profiler le test sélectionné** dans le menu contextuel. Consultez [rapport de profilage par instrumentation](../profiling/understanding-instrumentation-data-values.md?view=vs-2017).
::: moniker-end

::: moniker range=">=vs-2019"
Pour diagnostiquer la lenteur d’une méthode de test, sélectionnez la méthode dans l’Explorateur de tests, puis choisissez **Profil** dans le menu contextuel (clic droit). Consultez [rapport de profilage par instrumentation](../profiling/understanding-instrumentation-data-values.md?view=vs-2017).
::: moniker-end

> [!NOTE]
> Cette fonctionnalité n’est actuellement pas prise en charge pour .NET Core.

## <a name="see-also"></a>Voir aussi

- [Test unitaire de votre code](../test/unit-test-your-code.md)
- [Exécuter des tests unitaires avec l'Explorateur de tests](../test/run-unit-tests-with-test-explorer.md)
- [Questions fréquentes (FAQ) sur l’Explorateur de tests](test-explorer-faq.md)
