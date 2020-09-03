---
title: Tests unitaires
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, unit tests
- unit tests, verifying code with
- testing code, automated tests
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: ffe383d2195feb6689954a8ec858b196bae8c06a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75565992"
---
# <a name="unit-test-your-code"></a>Tests unitaires de votre code

Les tests unitaires offrent aux développeurs et aux testeurs un moyen rapide de rechercher des erreurs de logique dans les méthodes des classes des projets C#, Visual Basic et C++.

Les outils de test unitaire incluent :

* **Explorateur** &mdash; de tests Exécutez des tests unitaires et consultez leurs résultats dans l' **Explorateur de tests**. Vous pouvez utiliser n’importe quel framework de tests unitaires, y compris un framework tiers, qui a un adaptateur pour **l’Explorateur de tests**.

* **Infrastructure de tests unitaires Microsoft pour le code managé** &mdash; L’infrastructure de tests unitaires Microsoft pour le code managé est installée avec Visual Studio et fournit une infrastructure pour tester le code .NET.

* **Infrastructure de tests unitaires Microsoft pour C++** &mdash; L’infrastructure de tests unitaires Microsoft pour C++ est installée dans le cadre de la charge de travail **développement Desktop avec c++** . Il fournit un framework pour tester du code natif. Les frameworks Google Test, Boost.Test et CTest sont également inclus, et des adaptateurs tiers sont disponibles pour d’autres frameworks de test. Pour plus d’informations, consultez [Écrire des tests unitaires pour C/C++](../test/writing-unit-tests-for-c-cpp.md).

* Outils de couverture **du code** &mdash; Vous pouvez déterminer la quantité de code de produit que vos tests unitaires exercent à partir d’une commande de l’Explorateur de tests.

* **Microsoft** a fictif l’infrastructure &mdash; d’isolation L’infrastructure d’isolation Microsoft simule peut créer des classes et des méthodes de substitution pour la production et le code système qui créent des dépendances dans le code testé. En implémentant les délégués substituts d'une fonction, vous contrôlez le comportement et la sortie de l'objet de dépendance.

Vous pouvez également utiliser [IntelliTest](../test/generate-unit-tests-for-your-code-with-intellitest.md) pour explorer votre code .NET et générer des données de test et une suite de tests unitaires. Pour chaque instruction dans le code, une entrée de test est générée pour exécuter cette instruction. Une analyse de cas est effectuée pour chaque branche conditionnelle dans le code.

## <a name="key-tasks"></a>Tâches clés

Utilisez les articles suivants pour comprendre et créer des tests unitaires :

|Tâches|Rubriques associées|
|-|-----------------------|
|**Démarrages rapides et procédures pas à pas :** En savoir plus sur les tests unitaires dans Visual Studio à partir d’exemples de code.|- [Procédure pas à pas : créer et exécuter des tests unitaires pour le code managé](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md)<br />- [Démarrage rapide : développement piloté par les tests avec l’Explorateur de tests](../test/quick-start-test-driven-development-with-test-explorer.md)<br />- [Comment : ajouter des tests unitaires à des applications C++](../test/how-to-use-microsoft-test-framework-for-cpp.md)|
|**Tests unitaires avec l’Explorateur de tests :** découvrez comment l’Explorateur de tests vous permet de créer des tests unitaires plus productifs et plus efficaces.|- [Concepts de base des tests unitaires](../test/unit-test-basics.md)<br />- [Créer un projet de test unitaire](../test/create-a-unit-test-project.md)<br />- [Exécuter des tests unitaires avec l’Explorateur de tests](../test/run-unit-tests-with-test-explorer.md)<br />- [Installer des infrastructures de tests unitaires tierces](../test/install-third-party-unit-test-frameworks.md)|
|**Test unitaire de code C++**|- [Écrire des tests unitaires pour C/C++](../test/writing-unit-tests-for-c-cpp.md)|
|**Isolation des tests unitaires**|- [Isoler le code testé avec les substituts Microsoft](../test/isolating-code-under-test-with-microsoft-fakes.md)|
|**Utiliser la couverture du code pour identifier la proportion du code de votre projet qui est testée :** découvrez plus d’informations sur la fonctionnalité de couverture du code des outils de test de Visual Studio.|- [Utiliser la couverture du code pour déterminer la quantité de code testé](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)|
|**Effectuer une analyse des performances et de la contrainte à l’aide de tests de charge :** Découvrez comment créer des tests de charge pour isoler les problèmes de performances et de stress dans votre application.|- [Démarrage rapide : créer un projet de test de charge](../test/quickstart-create-a-load-test-project.md)<br />- [Tests de charge (Azure Test Plans et TFS)](/azure/devops/test/load-test/index?view=vsts)|
|**Définir les portes de qualité :** Apprenez à créer des portes de qualité pour imposer que les tests soient exécutés avant que le code ne soit archivé ou fusionné.|- [Stratégies d’archivage (Azure Repos TFVC)](/azure/devops/repos/tfvc/add-check-policies?view=vsts)|
|**Définir les options de test :** Découvrez comment configurer les options de test, par exemple, l’emplacement de stockage des résultats des tests.|[Configurer des tests unitaires à l'aide d'un fichier .runsettings](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)|

## <a name="api-reference-documentation"></a>Documentation de référence de l’API

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting> décrit l’espace de noms UnitTesting, qui fournit des attributs, des exceptions, des assertions et d’autres classes qui prennent en charge les tests unitaires.
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Web> décrit l’espace de noms UnitTesting.Web, qui étend l’espace de noms UnitTesting en assurant la prise en charge des tests unitaires pour ASP.NET et les services web.

## <a name="see-also"></a>Voir aussi

- [Améliorer la qualité du code](../test/improve-code-quality.md)
