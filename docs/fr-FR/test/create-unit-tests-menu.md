---
title: Créer des stubs de méthodes de tests unitaires dans Visual Studio
ms.date: 05/02/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- unit testing, create unit tests
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 39c59d76d10c2028214b2a1ea15ff139000e3080
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="create-unit-test-method-stubs-with-the-create-unit-tests-command"></a>Créer des stubs de méthodes de tests unitaires avec la commande Créer des tests unitaires

La commande **Créer des tests unitaires** de Visual Studio permet de créer des stubs de méthodes de tests unitaires. Cette fonctionnalité permet de configurer facilement un projet de test, la classe de test et le stub de méthode de test qui y est contenu.

## <a name="availability-and-extensions"></a>Disponibilité et extensions

La commande de menu **Créer des tests unitaires** :

* est disponible dans les éditions Community, Professional et Enterprise de Visual Studio 2015 et versions ultérieures ;

* prend uniquement en charge le code C# qui cible le .NET Framework ;

* est extensible et prend en charge l’émission de tests aux formats MSTest, MSTest V2, NUnit et xUnit.

## <a name="get-started"></a>Prise en main

Pour commencer, sélectionnez une méthode, un type ou un espace de noms dans l’éditeur de code dans le projet que vous souhaitez tester, ouvrez le menu contextuel et choisissez **Créer des tests unitaires**. Vous ouvrez ainsi la boîte de dialogue **Créer des tests unitaires** où vous pouvez sélectionner les options de création de tests unitaires.

![Utilisation de la commande Créer des tests unitaires](media/createunittestcommand.png)

## <a name="setting-unit-test-traits"></a>Définition des caractéristiques des tests unitaires

Si vous prévoyez d’exécuter ces tests dans le cadre du processus d’automatisation des tests, vous pouvez envisager de créer le test dans un autre projet de test (la deuxième option dans la boîte de dialogue ci-dessus) et de définir les caractéristiques pour le test unitaire. Cela vous permet d’inclure ou d’exclure plus facilement ces tests spécifiques dans le cadre d’une intégration ou d’un pipeline de déploiement continu. Les caractéristiques sont définies en ajoutant des métadonnées au test unitaire directement, comme indiqué ci-dessous.

![Définition des caractéristiques des tests unitaires](media/createunittest.png)

## <a name="using-third-party-unit-test-frameworks"></a>Utilisation de frameworks de tests unitaires tiers

Avec Visual Studio, vous pouvez facilement avoir des tests unitaires créés automatiquement à l’aide d’un framework de test. Pour installer d’autres frameworks de tests :

1. Choisissez **Outils** > **Extensions et mises à jour**.
2. Développez **En ligne** > **Visual Studio Marketplace** > **Outils**, puis choisissez **Test**.

![Utilisation de frameworks de test tiers](media/createunittestfx.png)

Les extensions de framework de test sont disponibles dans Visual Studio Marketplace :

* [Extension NUnit pour les générateurs de tests](https://marketplace.visualstudio.com/items?itemName=NUnitDevelopers.TestGeneratorNUnitextension)
* [Extension xUnit.net pour les générateurs de tests](https://marketplace.visualstudio.com/items?itemName=BradWilson.xUnitnetTestExtensions)

## <a name="when-should-i-use-this-feature"></a>Quand dois-je utiliser cette fonctionnalité ?

Utilisez cette fonctionnalité chaque fois que vous devez créer des tests unitaires, mais en particulier quand vous testez le code existant qui a très peu ou pas de couverture de test, et aucune documentation. En d’autres termes, utilisez-la quand la spécification de code est limitée ou inexistante. Elle implémente efficacement une approche semblable aux [tests unitaires intelligents](http://blogs.msdn.com/b/visualstudioalm/archive/2014/11/19/introducing-smart-unit-tests.aspx) qui caractérisent le comportement observé du code.

Toutefois, cette fonctionnalité est également applicable à la situation où le développeur commence par écrire du code et l’utilise pour amorcer la discipline des tests unitaires. Dans le flux de codage, le développeur peut vouloir rapidement créer un stub de méthode de test unitaire (avec une classe de test et un projet de test appropriés) pour un élément de code spécifique.

## <a name="see-also"></a>Voir aussi

- [Creating unit test method stubs with "Create Unit Tests"](https://blogs.msdn.microsoft.com/visualstudioalm/2015/03/06/creating-unit-test-method-stubs-with-create-unit-tests/) (Créer des stubs de méthodes de tests unitaires avec la commande « Créer des tests unitaires »)
- [Billets de blog sur les tests unitaires](https://blogs.msdn.microsoft.com/devops/?s=unit+testing)
