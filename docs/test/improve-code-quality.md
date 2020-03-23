---
title: Outils de test
ms.date: 03/16/2018
ms.topic: conceptual
helpviewer_keywords:
- testing tools [Visual Studio]
- unit tests [Visual Studio]
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: e6dd0f0df6dde5c1f3553ab86374e71dfef82384
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75594362"
---
# <a name="testing-tools-in-visual-studio"></a>Outils de test dans Visual Studio

Les outils de test de Visual Studio peuvent vous aider vous et votre équipe à développer et à maintenir du code avec des standards élevés d’excellence.

> [!NOTE]
> Les tests unitaires sont disponibles dans toutes les éditions de Visual Studio. D’autres outils de test, comme Live Unit Testing, IntelliTest et les tests codés de l’interface utilisateur, sont disponibles seulement dans l’édition Visual Studio Enterprise. Pour plus d’informations sur les éditions, consultez le [comparatif des IDE Visual Studio](https://visualstudio.microsoft.com/vs/compare/).

## <a name="test-explorer"></a>Explorateur de tests

La fenêtre **Explorateur de tests** permet aux développeurs de créer, gérer et exécuter des tests unitaires. Vous pouvez utiliser l'infrastructure de test unitaire Microsoft ou une des infrastructures tierces et ouvertes.

::: moniker range="vs-2017"
![Explorateur de tests Visual Studio](media/devtest-testexplorer.png)
::: moniker-end

::: moniker range="vs-2019"
![Explorateur de tests Visual Studio 16.2](media/vs-2019/test-explorer-16-2.PNG)
::: moniker-end

* [Bien démarrer avec les tests unitaires](unit-test-your-code.md)
* [Exécuter des tests unitaires avec Test Explorer](run-unit-tests-with-test-explorer.md)
* [Questions fréquentes (FAQ) sur l’Explorateur de tests](test-explorer-faq.md)
* [Installer des frameworks de tests unitaires tiers](install-third-party-unit-test-frameworks.md)

Visual Studio est également extensible et accepte les adaptateurs de tests unitaires tiers comme NUnit et xUnit.net. En outre, la fonctionnalité de clonage de code va de pair avec des logiciels de haute qualité en vous aidant à identifier les blocs de code sémantiquement similaires qui peuvent faire l’objet d’une refactorisation ou de correctifs de bogues courants.

![Intégration de tests tiers](media/devtest-thirdparty.png)

## <a name="live-unit-testing"></a>Live Unit Testing

[Live Unit Testing](../test/live-unit-testing.md) exécute automatiquement des tests unitaires en arrière-plan et affiche les résultats de test et de couverture du code sous forme graphique dans l’éditeur de code Visual Studio.

## <a name="intellitest"></a>IntelliTest

IntelliTest génère automatiquement des tests unitaires et des données de test pour votre code managé. IntelliTest améliore la couverture et réduit considérablement l’effort de création et de maintenance de tests unitaires pour du code nouveau ou existant.

![IntelliTest en action](media/devtest-intellitest.png)

* [Générer des tests unitaires pour votre code avec IntelliTest](generate-unit-tests-for-your-code-with-intellitest.md)
* [IntelliTest – One Test to rule them all](https://devblogs.microsoft.com/devops/intellitest-one-test-to-rule-them-all/)
* [Manuel de référence IntelliTest](intellitest-manual/index.md)

## <a name="code-coverage"></a>Couverture du code

La [couverture du code](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md) détermine la proportion de code de votre projet qui sera réellement testée par les tests codés, comme des tests unitaires. Pour apporter une protection efficace contre les bogues, vos tests doivent s’effectuer sur ou « couvrir » une proportion importante de votre code.

L’analyse de couverture du code peut être appliquée à du code managé et non managé (natif).

Vous pouvez avoir recours à la couverture du code lorsque vous exécutez des méthodes de test à l'aide de l'Explorateur de tests. La table des résultats affiche le pourcentage de code exécuté dans chaque assembly, classe et méthode. En outre, l'éditeur de code source vous indique quel code a été testé.

* [Utiliser la couverture du code pour déterminer la quantité de code testée](using-code-coverage-to-determine-how-much-code-is-being-tested.md)
* [Tests unitaires, couverture du code et analyse des clones de code avec Visual Studio (laboratoire)](https://www.boost.org/doc/libs/1_71_0/libs/test/doc/html/index.html)
* [Personnaliser l’analyse de la couverture du code](customizing-code-coverage-analysis.md)

## <a name="microsoft-fakes"></a>Microsoft Fakes

[Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md) vous permet d’isoler le code que vous testez en remplaçant d’autres parties de l’application par des stubs ou des shims.

## <a name="user-interface-testing-with-coded-ui-and-selenium"></a>Tests codés de l’interface utilisateur et avec Selenium

Les tests codés de l’interface utilisateur fournissent un moyen de créer des tests entièrement automatisés pour valider les fonctionnalités et le comportement de l’interface utilisateur de votre application. Ils peuvent automatiser les tests de l’interface utilisateur avec différentes technologies, notamment les applications UWP en XAML, les applications de navigateur et les applications SharePoint.

Que vous choisissiez les meilleurs tests codés de l’interface utilisateur ou des tests de l’interface utilisateur basés sur un navigateur générique avec Selenium, Visual Studio fournit tous les outils dont vous avez besoin.

![Tests codés de l’interface utilisateur](media/devtest-codeduitest.png)

* [Utilisez l’automatisation de l’interface utilisateur pour tester votre code](use-ui-automation-to-test-your-code.md)
* [Commencer à créer, modifier et maintenir un test d’interface utilisateur codé](walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md)
* [Testez les applications UWP avec des tests d’interface utilisateur codés](test-uwp-app-with-coded-ui-test.md)
* [Introduction aux tests codés de l’interface utilisateur avec Visual Studio Enterprise (laboratoire)](https://www.boost.org/doc/libs/1_71_0/libs/test/doc/html/index.html)

## <a name="load-testing"></a>Test de charge

[Le test de charge](../test/quickstart-create-a-load-test-project.md) simule la charge sur une application de serveur en exécutant des tests unitaires et des tests de performance Web.

## <a name="related-scenarios"></a>Scénarios connexes

* [Tests exploratoires et manuels (Azure Test Plans)](/azure/devops/test/index?view=vsts)
* [Tests de charge (Azure Test Plans)](/azure/devops/test/load-test/index?view=vsts)
* [Tests continus (Azure Test Plans)](/azure/devops/pipelines/test/getting-started-with-continuous-testing?view=vsts)
* [Outils d’analyse du code](../code-quality/code-analysis-for-managed-code-overview.md)
