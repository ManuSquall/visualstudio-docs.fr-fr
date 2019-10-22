---
title: Outils de test
ms.date: 03/16/2018
ms.topic: conceptual
helpviewer_keywords:
- testing tools [Visual Studio]
- unit tests [Visual Studio]
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
author: jillre
ms.openlocfilehash: b68793e512cdb367375cc9f27d61ae5a85e4f078
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72653280"
---
# <a name="testing-tools-in-visual-studio"></a>Outils de test dans Visual Studio

Les outils de test de Visual Studio peuvent vous aider vous et votre équipe à développer et à maintenir du code avec des standards élevés d’excellence.

> [!NOTE]
> Les tests unitaires sont disponibles dans toutes les éditions de Visual Studio. D’autres outils de test, comme Live Unit Testing, IntelliTest et les tests codés de l’interface utilisateur, sont disponibles seulement dans l’édition Visual Studio Enterprise. Pour plus d’informations sur les éditions, consultez le [comparatif des IDE Visual Studio](https://visualstudio.microsoft.com/vs/compare/).

## <a name="test-explorer"></a>Explorateur de tests

La fenêtre **Explorateur de tests** permet aux développeurs de créer, gérer et exécuter des tests unitaires. Vous pouvez utiliser le framework de tests unitaires Microsoft ou un des frameworks tiers et ouverts.

::: moniker range="vs-2017"
![Explorateur de tests Visual Studio](media/devtest-testexplorer.png)
::: moniker-end

::: moniker range="vs-2019"
![Explorateur de tests Visual Studio 16.2](media/vs-2019/test-explorer-16-2.PNG)
::: moniker-end

* [Bien démarrer avec les tests unitaires](unit-test-your-code.md)
* [Exécuter des tests unitaires avec l’Explorateur de tests](run-unit-tests-with-test-explorer.md)
* [Questions fréquentes (FAQ) sur l’Explorateur de tests](test-explorer-faq.md)
* [Installer des infrastructures de tests unitaires tierces](install-third-party-unit-test-frameworks.md)

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

* [Utiliser la couverture du code pour déterminer la quantité de code testé](using-code-coverage-to-determine-how-much-code-is-being-tested.md)
* [Tests unitaires, couverture du code et analyse des clones de code avec Visual Studio (laboratoire)](http://download.microsoft.com/download/6/2/B/62B60ECE-B9DC-4E8A-A97C-EA261BFB935E/Docs/Unit%20Testing,%20Code%20Coverage%20and%20Code%20Clone%20Analysis%20with%20Visual%20Studio%202015.docx)
* [Personnaliser l’analyse de la couverture du code](customizing-code-coverage-analysis.md)

## <a name="microsoft-fakes"></a>Microsoft Fakes

[Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md) vous permet d’isoler le code que vous testez en remplaçant d’autres parties de l’application par des stubs ou des shims.

## <a name="user-interface-testing-with-coded-ui-and-selenium"></a>Tests codés de l’interface utilisateur et avec Selenium

Les tests codés de l’interface utilisateur fournissent un moyen de créer des tests entièrement automatisés pour valider les fonctionnalités et le comportement de l’interface utilisateur de votre application. Ils peuvent automatiser les tests de l’interface utilisateur avec différentes technologies, notamment les applications UWP en XAML, les applications de navigateur et les applications SharePoint.

Que vous choisissiez les meilleurs tests codés de l’interface utilisateur ou des tests de l’interface utilisateur basés sur un navigateur générique avec Selenium, Visual Studio fournit tous les outils dont vous avez besoin.

![Tests codés de l’interface utilisateur](media/devtest-codeduitest.png)

* [Utiliser l’automatisation de l’interface utilisateur pour tester votre code](use-ui-automation-to-test-your-code.md)
* [Bien démarrer avec la création, la modification et la gestion d’un test codé de l’interface utilisateur](walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md)
* [Tester des applications UWP avec des tests codés de l’interface utilisateur](test-uwp-app-with-coded-ui-test.md)
* [Introduction aux tests codés de l’interface utilisateur avec Visual Studio Enterprise (laboratoire)](http://download.microsoft.com/download/6/2/B/62B60ECE-B9DC-4E8A-A97C-EA261BFB935E/Docs/Introduction%20to%20Coded%20UI%20Tests%20with%20Visual%20Studio%20Enterprise%202015.docx)

## <a name="load-testing"></a>Test de charge

Les [tests de charge](../test/quickstart-create-a-load-test-project.md) simulent la charge sur une application serveur en exécutant des tests unitaires et des tests de performances web.

## <a name="related-scenarios"></a>Scénarios connexes

* [Tests exploratoires et manuels (Azure Test Plans)](/azure/devops/test/index?view=vsts)
* [Tests de charge (Azure Test Plans)](/azure/devops/test/load-test/index?view=vsts)
* [Tests continus (Azure Test Plans)](/azure/devops/pipelines/test/getting-started-with-continuous-testing?view=vsts)
* [Outils d’analyse du code](../code-quality/code-analysis-for-managed-code-overview.md)
