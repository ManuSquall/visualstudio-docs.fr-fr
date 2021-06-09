---
title: Outils de test
description: Découvrez comment les outils de test de Visual Studio peuvent vous aider et votre équipe à développer et maintenir des niveaux élevés d’excellence du code.
ms.custom: SEO-VS-2020
ms.date: 03/16/2018
ms.topic: conceptual
helpviewer_keywords:
- testing tools [Visual Studio]
- unit tests [Visual Studio]
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: e2224ffc1776a15453d1382872c2d3f5a9e86c3c
ms.sourcegitcommit: 01a411cd7ae3488b7b979a947bca92fd296a98e9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2021
ms.locfileid: "111760950"
---
# <a name="first-look-at-testing-tools-in-visual-studio"></a>Examinez d’abord les outils de test dans Visual Studio

Les outils de test de Visual Studio peuvent vous aider vous et votre équipe à développer et à maintenir du code avec des standards élevés d’excellence.

> [!NOTE]
> Les tests unitaires sont disponibles dans toutes les éditions de Visual Studio. D’autres outils de test, tels que Live Unit Testing et IntelliTest, sont uniquement disponibles dans l’édition Visual Studio Enterprise. Pour plus d’informations sur les éditions, consultez le [comparatif des IDE Visual Studio](https://visualstudio.microsoft.com/vs/compare/).

## <a name="test-explorer"></a>Explorateur de tests

La fenêtre **Explorateur de tests** permet aux développeurs de créer, gérer et exécuter des tests unitaires. Vous pouvez utiliser l'infrastructure de test unitaire Microsoft ou une des infrastructures tierces et ouvertes.

::: moniker range="vs-2017"
![Explorateur de tests Visual Studio](media/devtest-testexplorer.png)
::: moniker-end

::: moniker range=">=vs-2019"
![Explorateur de tests Visual Studio 16.2](media/vs-2019/test-explorer-16-2.PNG)
::: moniker-end

* [Bien démarrer avec les tests unitaires](unit-test-your-code.md)
* [Exécuter des tests unitaires avec l'Explorateur de tests](run-unit-tests-with-test-explorer.md)
* [Questions fréquentes (FAQ) sur l’Explorateur de tests](test-explorer-faq.md)
* [Installer des frameworks de tests unitaires tierces](install-third-party-unit-test-frameworks.md)

Visual Studio est également extensible et accepte les adaptateurs de tests unitaires tiers comme NUnit et xUnit.net. En outre, la fonctionnalité de clonage de code va de pair avec des logiciels de haute qualité en vous aidant à identifier les blocs de code sémantiquement similaires qui peuvent faire l’objet d’une refactorisation ou de correctifs de bogues courants.

![Intégration de tests tiers](media/devtest-thirdparty.png)

## <a name="live-unit-testing"></a>Live Unit Testing

[Live Unit Testing](../test/live-unit-testing.md) exécute automatiquement des tests unitaires en arrière-plan et affiche les résultats de test et de couverture du code sous forme graphique dans l’éditeur de code Visual Studio.

> [!NOTE]
> Live Unit testing est uniquement disponible dans l’édition Enterprise et n’est pris en charge que pour le code .NET.

## <a name="intellitest"></a>IntelliTest

IntelliTest génère automatiquement des tests unitaires et des données de test pour votre code managé. IntelliTest améliore la couverture et réduit considérablement l’effort de création et de maintenance de tests unitaires pour du code nouveau ou existant.

![IntelliTest en action](media/devtest-intellitest.png)

> [!NOTE]
> IntelliTest est disponible uniquement dans l’édition Enterprise. Il est pris en charge pour le code C# qui cible le .NET Framework. .NET Core et .NET Standard ne sont pas pris en charge actuellement.

* [Générer des tests unitaires pour votre code avec IntelliTest](generate-unit-tests-for-your-code-with-intellitest.md)
* [IntelliTest – One Test to rule them all](https://devblogs.microsoft.com/devops/intellitest-one-test-to-rule-them-all/)
* [Manuel de référence IntelliTest](intellitest-manual/index.md)

## <a name="code-coverage"></a>Couverture du code

La [couverture du code](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md) détermine la proportion de code de votre projet qui sera réellement testée par les tests codés, comme des tests unitaires. Pour apporter une protection efficace contre les bogues, vos tests doivent s’effectuer sur ou « couvrir » une proportion importante de votre code.

> [!NOTE]
> La couverture du code est disponible uniquement dans l’édition Enterprise.

L’analyse de couverture du code peut être appliquée à du code managé et non managé (natif).

Vous pouvez avoir recours à la couverture du code lorsque vous exécutez des méthodes de test à l'aide de l'Explorateur de tests. La table des résultats affiche le pourcentage de code exécuté dans chaque assembly, classe et méthode. En outre, l'éditeur de code source vous indique quel code a été testé.

* [Utiliser la couverture du code pour déterminer la quantité de code testé](using-code-coverage-to-determine-how-much-code-is-being-tested.md)
* [Tests unitaires, couverture du code et analyse des clones de code avec Visual Studio (laboratoire)](https://azuredevopslabs.com/labs/devopsserver/liveunittesting)
* [Personnaliser l’analyse de la couverture du code](customizing-code-coverage-analysis.md)

## <a name="microsoft-fakes"></a>Microsoft Fakes

[Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md) vous permet d’isoler le code que vous testez en remplaçant d’autres parties de l’application par des stubs ou des shims.

> [!NOTE]
> Les substituts Microsoft sont disponibles uniquement dans l’édition Enterprise et ne sont pris en charge que pour le code .NET.

## <a name="user-interface-testing-with-coded-ui-and-selenium"></a>Tests codés de l’interface utilisateur et avec Selenium

Les tests codés de l’interface utilisateur fournissent un moyen de créer des tests entièrement automatisés pour valider les fonctionnalités et le comportement de l’interface utilisateur de votre application. Ils peuvent automatiser les tests de l’interface utilisateur avec différentes technologies, notamment les applications UWP en XAML, les applications de navigateur et les applications SharePoint.

> [!NOTE]
> L’interface utilisateur codée est une fonctionnalité déconseillée.

Que vous choisissiez les meilleurs tests codés de l’interface utilisateur ou des tests de l’interface utilisateur basés sur un navigateur générique avec Selenium, Visual Studio fournit tous les outils dont vous avez besoin.

![Tests codés de l’interface utilisateur](media/devtest-codeduitest.png)

* [Utiliser UI Automation pour tester votre code](use-ui-automation-to-test-your-code.md)
* [Prise en main de la création, de la modification et de la maintenance d’un test codé de l’interface utilisateur](walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md)
* [Tester des applications UWP avec des tests codés de l’interface utilisateur](test-uwp-app-with-coded-ui-test.md)
* [Introduction aux tests codés de l’interface utilisateur avec Visual Studio Enterprise (laboratoire)](https://azuredevopslabs.com/labs/tfs/codedui)

## <a name="related-scenarios"></a>Scénarios connexes

* [Tests exploratoires et manuels (Azure Test Plans)](/azure/devops/test/index?view=vsts&preserve-view=true)
* [Tests de charge (Azure Test Plans)](/azure/devops/test/load-test/index?view=vsts&preserve-view=true)
* [Tests continus (Azure Test Plans)](/azure/devops/pipelines/test/getting-started-with-continuous-testing?view=vsts&preserve-view=true)
* [Outils d’analyse du code](../code-quality/code-analysis-for-managed-code-overview.md)
