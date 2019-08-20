---
title: Créer des stubs de méthodes de tests unitaires
ms.date: 04/01/2019
ms.topic: conceptual
helpviewer_keywords:
- unit testing, create unit tests
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: aba0edbabdac6eb0e0c391371b51151a5be1ecba
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2019
ms.locfileid: "66745801"
---
# <a name="create-unit-test-method-stubs-with-the-create-unit-tests-command"></a>Créer des stubs de méthodes de tests unitaires avec la commande Créer des tests unitaires

La commande **Créer des tests unitaires** permet de créer des stubs de méthodes de tests unitaires. Cette fonctionnalité permet de configurer facilement un projet de test, la classe de test et le stub de méthode de test qui y est contenu.

> [!NOTE]
> La commande de menu **Créer des tests unitaires** est disponible seulement pour le code managé qui cible le .NET Framework (mais pas .NET Core).

La commande de menu **Créer des tests unitaires** est extensible et peut servir à générer des tests pour MSTest, MSTest V2, NUnit et xUnit.

## <a name="get-started"></a>Prise en main

Pour bien démarrer, sélectionnez une méthode, un type ou un espace de noms dans l’éditeur de code du projet à tester, cliquez avec le bouton droit, puis choisissez **Créer des tests unitaires**. La boîte de dialogue **Créer des tests unitaires** s’ouvre et vous permet de configurer la façon de créer les tests.

![Utilisation de la commande Créer des tests unitaires](media/createunittestcommand.png)

## <a name="set-unit-test-traits"></a>Définir des caractéristiques des tests unitaires

Si vous prévoyez d’exécuter ces tests dans le cadre du processus d’automatisation des tests, vous pouvez envisager de créer le test dans un autre projet de test (la deuxième option dans la boîte de dialogue ci-dessus) et de définir les caractéristiques pour le test unitaire. Cela vous permet d’inclure ou d’exclure plus facilement ces tests spécifiques dans le cadre d’un pipeline d’intégration continue ou de déploiement continu. Les caractéristiques sont définies en ajoutant des métadonnées au test unitaire directement, comme indiqué ci-dessous.

![Définition des caractéristiques des tests unitaires](media/createunittest.png)

## <a name="use-third-party-unit-test-frameworks"></a>Utiliser des infrastructures de tests unitaires tierces

Pour générer automatiquement des tests unitaires pour NUnit ou xUnit, installez l’une de ces extensions de framework de test à partir de Visual Studio Marketplace :

* [Extension NUnit pour les générateurs de tests](https://marketplace.visualstudio.com/items?itemName=NUnitDevelopers.TestGeneratorNUnitextension)
* [Extension xUnit.net pour les générateurs de tests](https://marketplace.visualstudio.com/items?itemName=BradWilson.xUnitnetTestExtensions)

## <a name="when-should-i-use-this-feature"></a>Quand dois-je utiliser cette fonctionnalité ?

Utilisez cette fonctionnalité chaque fois que vous devez créer des tests unitaires, mais plus particulièrement quand vous testez le code existant qui a peu ou pas de couverture de test, et aucune documentation. En d’autres termes, utilisez-la quand la spécification de code est limitée ou inexistante. Elle implémente efficacement une approche semblable aux [tests unitaires intelligents](https://devblogs.microsoft.com/devops/introducing-smart-unit-tests/) qui caractérise le comportement observé du code.

Toutefois, cette fonctionnalité est également applicable quand un développeur commence par écrire du code, puis l’utilise pour amorcer des tests unitaires. Dans le flux de codage, le développeur peut vouloir rapidement créer un stub de méthode de test unitaire (avec une classe de test et un projet de test appropriés) pour un élément de code spécifique.

## <a name="see-also"></a>Voir aussi

- [Creating unit test method stubs with "Create Unit Tests"](https://devblogs.microsoft.com/devops/creating-unit-test-method-stubs-with-create-unit-tests/) (Créer des stubs de méthodes de tests unitaires avec la commande « Créer des tests unitaires »)
- [Billets de blog sur les tests unitaires](https://devblogs.microsoft.com/devops/?s=unit+testing)
