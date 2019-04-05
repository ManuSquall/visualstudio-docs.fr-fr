---
title: Outils de test pour développeurs
ms.date: 05/02/2017
ms.topic: conceptual
helpviewer_keywords:
- unit testing, create unit tests
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a1cc43bfeb66792d2d8ff5a736d957740f62c5ff
ms.sourcegitcommit: 489aca71046fb6e4aafd0a4509cd7dc149d707b1
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2019
ms.locfileid: "58416204"
---
# <a name="developer-testing-tools-scenarios-and-capabilities"></a>Outils de test pour les développeurs, scénarios et fonctions

Maintenez l’intégrité du code avec des tests unitaires. Visual Studio offre aux développeurs un large éventail de techniques et d’outils puissants permettant de tester les applications.

## <a name="avoid-regressions-and-achieve-code-coverage-with-intellitest"></a>Éviter les régressions et obtenir la couverture du code avec IntelliTest

Dans les suites de tests unitaires classiques, chaque cas de test représente un scénario d’utilisation exemplaire et les assertions expriment la relation entre l’entrée et la sortie.  La vérification de quelques scénarios de ce type peut très bien être suffisante, mais les développeurs expérimentés savent que les bogues se cachent même dans du code soigneusement testé quand des entrées correctes, mais non testées, provoquent des réponses incorrectes.

Améliorez la couverture et évitez les régressions avec IntelliTest. IntelliTest réduit considérablement l’effort de création et de maintenance de tests unitaires pour le code nouveau ou existant.

![IntelliTest en action](media/devtest-intellitest.png)

* [Introduction à IntelliTest avec Visual Studio](http://download.microsoft.com/download/6/2/B/62B60ECE-B9DC-4E8A-A97C-EA261BFB935E/Docs/Introduction%20to%20IntelliTest%20with%20Visual%20Studio%20Enterprise%202015.docx)
* [IntelliTest – One Test to rule them all](https://devblogs.microsoft.com/devops/intellitest-one-test-to-rule-them-all/)
* [Vidéos IntelliTest](https://channel9.msdn.com/Series/Test-Tools-in-Visual-Studio)
* [Bien démarrer avec IntelliTest](generate-unit-tests-for-your-code-with-intellitest.md)
* [Manuel de référence IntelliTest](intellitest-manual/index.md)

## <a name="user-interface-testing-with-coded-ui-and-selenium"></a>Tests codés de l’interface utilisateur et avec Selenium

Testez votre interface utilisateur avec les meilleurs tests de l’interface utilisateur ou ceux qui ont été approuvés par la communauté. Les tests codés de l’interface utilisateur fournissent un moyen de créer des tests entièrement automatisés pour valider les fonctionnalités et le comportement de l’interface utilisateur de votre application. Ils peuvent automatiser les tests de l’interface utilisateur avec différentes technologies, notamment les applications UWP en XAML, les applications de navigateur et les applications SharePoint.

Que vous choisissiez les meilleurs tests codés de l’interface utilisateur ou des tests de l’interface utilisateur basés sur un navigateur générique avec Selenium, Visual Studio fournit tous les outils dont vous avez besoin.

![Tests codés de l’interface utilisateur](media/devtest-codeduitest.png)

* [Utiliser l’automatisation de l’interface utilisateur pour tester votre code](use-ui-automation-to-test-your-code.md)
* [Bien démarrer avec la création, la modification et la gestion d’un test codé de l’interface utilisateur](walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md)
* [Tester des applications UWP avec des tests codés de l’interface utilisateur](test-uwp-app-with-coded-ui-test.md)
* [Introduction aux tests codés de l’interface utilisateur avec Visual Studio Enterprise (laboratoire)](http://download.microsoft.com/download/6/2/B/62B60ECE-B9DC-4E8A-A97C-EA261BFB935E/Docs/Introduction%20to%20Coded%20UI%20Tests%20with%20Visual%20Studio%20Enterprise%202015.docx)

## <a name="effective-unit-testing-with-visual-studio-code-coverage"></a>Tests unitaires efficaces avec couverture du code Visual Studio

Pour déterminer la proportion de code de votre projet qui est réellement testée par des tests codés, par exemple des tests unitaires, recourez à la fonctionnalité de couverture du code de Visual Studio. Pour apporter une protection efficace contre les bogues, les tests doivent traiter ou « couvrir » une proportion importante de votre code.

L’analyse de couverture du code peut être appliquée à du code managé et non managé (natif).

Vous pouvez avoir recours à la couverture du code lorsque vous exécutez des méthodes de test à l'aide de l'Explorateur de tests. La table des résultats affiche le pourcentage de code exécuté dans chaque assembly, classe et méthode. En outre, l'éditeur de code source vous indique quel code a été testé.

* [Utiliser la couverture du code pour déterminer la quantité de code testé](using-code-coverage-to-determine-how-much-code-is-being-tested.md)
* [Tests unitaires, couverture du code et analyse des clones de code avec Visual Studio (laboratoire)](http://download.microsoft.com/download/6/2/B/62B60ECE-B9DC-4E8A-A97C-EA261BFB935E/Docs/Unit%20Testing,%20Code%20Coverage%20and%20Code%20Clone%20Analysis%20with%20Visual%20Studio%202015.docx)
* [Personnaliser l’analyse de la couverture du code](customizing-code-coverage-analysis.md)

## <a name="test-explorer"></a>Explorateur de tests

**L’Explorateur de tests** permet aux développeurs de créer, de gérer et d’exécuter des tests unitaires.

![Explorateur de tests Visual Studio](media/devtest-testexplorer.png)

* [Bien démarrer avec les tests unitaires](unit-test-your-code.md)
* [Exécuter des tests unitaires avec l’Explorateur de tests](run-unit-tests-with-test-explorer.md)
* [Questions fréquentes (FAQ) sur l’Explorateur de tests](test-explorer-faq.md)
* [Installer des frameworks de tests unitaires tiers](install-third-party-unit-test-frameworks.md)

Visual Studio est également extensible et accepte les adaptateurs de tests unitaires tiers comme NUnit et xUnit.net. En outre, la fonctionnalité de clonage de code va de pair avec des logiciels de haute qualité en vous aidant à identifier les blocs de code sémantiquement similaires qui peuvent faire l’objet d’une refactorisation ou de correctifs de bogues courants.

![Intégration de tests tiers](media/devtest-thirdparty.png)

## <a name="see-also"></a>Voir aussi

* [Bien démarrer avec les tests unitaires](getting-started-with-unit-testing.md)
* [Accélérer l’exécution des tests unitaires dans Team Foundation Server](https://devblogs.microsoft.com/devops/speeding-up-unit-test-execution-in-tfs/)
* [Exécution de tests unitaires contextuelle et en parallèle](https://devblogs.microsoft.com/devops/parallel-and-context-sensitive-test-execution-with-visual-studio-2015-update-1/)
* [Tests unitaires, couverture du code et analyse des clones de code avec Visual Studio (laboratoire)](http://download.microsoft.com/download/6/2/B/62B60ECE-B9DC-4E8A-A97C-EA261BFB935E/Docs/Unit%20Testing,%20Code%20Coverage%20and%20Code%20Clone%20Analysis%20with%20Visual%20Studio%202015.docx)
* [Écriture de tests unitaires pour C/C++](writing-unit-tests-for-c-cpp.md)
