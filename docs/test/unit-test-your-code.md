---
title: Tests unitaires dans Visual Studio
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, unit tests
- unit tests, verifying code with
- testing code, automated tests
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: bc69869e8f1cd60bad1f30f6ee9c37ca5d2821bd
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/20/2018
ms.locfileid: "39179214"
---
# <a name="unit-test-your-code"></a>Tests unitaires de votre code

Les tests unitaires offrent aux développeurs et aux testeurs un moyen rapide de rechercher des erreurs de logique dans les méthodes des classes des projets C#, Visual Basic et C++.

Les outils de test unitaire incluent :

* **Explorateur de tests**&mdash; vous pouvez exécuter des tests unitaires et voir leurs résultats dans **l’Explorateur de tests**. Vous pouvez utiliser n’importe quel framework de tests unitaires, y compris un framework tiers, qui a un adaptateur pour **l’Explorateur de tests**.

* **Framework de tests unitaires Microsoft pour le code managé**&mdash; le framework de tests unitaires Microsoft pour le code managé est installé avec Visual Studio et fournit un framework pour tester le code .NET.

* **Infrastructure de tests unitaires Microsoft pour C++**&mdash; le framework de tests unitaires Microsoft pour C++ est installé dans le cadre de la charge de travail **Développement Desktop en C++**. Il fournit un framework pour tester du code natif. Les frameworks Google Test, Boost.Test et CTest sont également inclus, et des adaptateurs tiers sont disponibles pour d’autres frameworks de test. Pour plus d’informations, consultez [Écriture de tests unitaires pour C/C++](../test/writing-unit-tests-for-c-cpp.md).

* **Outils de couverture du code**&mdash; vous pouvez déterminer la quantité de code du produit que vos tests unitaires passent en revue en utilisant une seule commande dans l’Explorateur de tests.

* **Framework d’isolement Microsoft Fakes**&mdash; le framework d’isolement Microsoft Fakes peut créer des classes et des méthodes de remplacement pour le code de production et le code système qui créent des dépendances dans le code testé. En implémentant les délégués substituts d'une fonction, vous contrôlez le comportement et la sortie de l'objet de dépendance.

Vous pouvez également utiliser [IntelliTest](../test/generate-unit-tests-for-your-code-with-intellitest.md) pour explorer votre code .NET et générer des données de test et une suite de tests unitaires. Pour chaque instruction dans le code, une entrée de test est générée pour exécuter cette instruction. Une analyse de cas est effectuée pour chaque branche conditionnelle dans le code.

## <a name="key-tasks"></a>Tâches clés

Utilisez les rubriques suivantes pour mieux comprendre et créer les tests unitaires :

|Tâches|Rubriques associées|
|-----------|-----------------------|
|**Démarrages rapides et procédures pas-à-pas :** consultez les rubriques suivantes pour apprendre à effectuer des tests unitaires dans Visual Studio avec des exemples de code.|-   [Procédure pas à pas : création et exécution de tests unitaires pour le code managé](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md)<br />-   [Démarrage rapide : développement piloté par les tests avec l’Explorateur de tests](../test/quick-start-test-driven-development-with-test-explorer.md)<br />-   [Ajout de tests unitaires à des applications C++ existantes](../test/unit-testing-existing-cpp-applications-with-test-explorer.md)|
|**Tests unitaires avec l’Explorateur de tests :** découvrez comment l’Explorateur de tests vous permet de créer des tests unitaires plus productifs et plus efficaces.|-   [Concepts de base des tests unitaires](../test/unit-test-basics.md)<br />-   [Créer un projet de test unitaire](../test/create-a-unit-test-project.md)<br />-   [Exécuter des tests unitaires avec l’Explorateur de tests](../test/run-unit-tests-with-test-explorer.md)<br />-   [Installer des frameworks de tests unitaires tiers](../test/install-third-party-unit-test-frameworks.md)|
|**Effectuer des tests unitaires sur du code managé :**|-   [Écriture de tests unitaires pour le .NET Framework à l’aide du framework de tests unitaires Microsoft pour le code managé](../test/writing-unit-tests-for-the-dotnet-framework-with-the-microsoft-unit-test-framework-for-managed-code.md)|
|**Effectuer des tests unitaires sur du code C++**|-   [Écriture de tests unitaires pour C/C++ à l’aide du framework de tests unitaires Microsoft pour C++](../test/writing-unit-tests-for-c-cpp-with-the-microsoft-unit-testing-framework-for-cpp.md)|
|**Isolation des tests unitaires**|-   [Isolation du code testé avec Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md)|
|**Utiliser la couverture du code pour identifier la proportion du code de votre projet qui est testée :** découvrez plus d’informations sur la fonctionnalité de couverture du code des outils de test de Visual Studio.|-   [Utilisation de la couverture du code pour déterminer la quantité de code testé](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)|
|**Effectuer une analyse des contraintes et des performances avec des tests de charge :** vous pouvez créer un test de charge et lui ajouter vos tests unitaires pour isoler les problèmes de contraintes et de performances de votre application.|-   [Tests de charge (VSTS et TFS)](/vsts/load-test/)|
|**Définir des niveaux de qualité :** vous pouvez créer des niveaux de qualité pour que les tests soient exécutés avant que le code ne soit archivé, de façon à garantir la qualité du code.|-   [Stratégies d’archivage (VSTS)](/vsts/tfvc/add-check-policies)|
|**Définir les options de test :** par exemple, vous pouvez spécifier l’emplacement de stockage des résultats des tests.|[Configurer des tests unitaires à l’aide d’un fichier .runsettings](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)|

## <a name="api-reference-documentation"></a>Documentation de référence des API

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting> décrit l’espace de noms UnitTesting, qui fournit des attributs, des exceptions, des assertions et d’autres classes qui prennent en charge les tests unitaires.
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Web> décrit l’espace de noms UnitTesting.Web, qui étend l’espace de noms UnitTesting en assurant la prise en charge des tests unitaires pour ASP.NET et les services web.

## <a name="see-also"></a>Voir aussi

- [Améliorer la qualité du code](../test/improve-code-quality.md)
