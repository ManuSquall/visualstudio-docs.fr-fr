---
title: Outils de test Visual Studio pour Mac
ms.date: 08/03/2020
ms.topic: conceptual
helpviewer_keywords:
- testing tools [Visual Studio for Mac]
- unit tests [Visual Studio for Mac]
ms.author: jomatthi
author: jmatthiesen
ms.openlocfilehash: acf34677e8d9b477512763be3c43bb9df0c53c46
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "88200983"
---
# <a name="testing-tools-in-visual-studio-for-mac"></a>Outils de test dans Visual Studio pour Mac

Les outils de test Visual Studio pour Mac peuvent vous aider, vous et votre équipe, à développer et à soutenir des niveaux élevés d’excellence du code. Les tests unitaires peuvent être écrits et exécutés à l’aide de l’infrastructure de tests unitaires Microsoft (MSTest), xUnit ou NUnit.

## <a name="creating-tests"></a>Créer des tests
Pour commencer à tester, vous pouvez créer un projet de test dans votre solution en cliquant avec le bouton droit sur votre solution et en choisissant le menu **ajouter > nouveau projet** .... Choisissez ensuite l’une des catégories de test sur le côté gauche de la boîte de dialogue (par exemple, la catégorie **Web et Console > tests** ). Sélectionnez le type de projet de test que vous souhaitez créer, puis cliquez sur suivant. Suivez les instructions dans les boîtes de dialogue qui s’affichent, puis un nouveau projet de test sera ajouté à votre solution.

![Boîte de dialogue Nouveau projet avec le Web et la console > les tests sélectionnés, avec les projets xUnit, MSTest et NUnit](media/create-new-test-project.PNG)

> [!NOTE]
> Pour plus d’informations sur les tests unitaires de vos applications .NET Core et la sélection d’infrastructures de tests unitaires, consultez la documentation [sur les tests unitaires dans .net Core et .NET standard](https://docs.microsoft.com/dotnet/core/testing/?pivots=xunit) .

## <a name="running-tests"></a>Exécution des tests
La fenêtre **tests unitaires** est utilisée pour exécuter des tests unitaires et est ouverte à l’aide du menu **affichage > Pad > des tests unitaires** . Les tests unitaires de votre solution sont automatiquement détectés et affichés dans cette fenêtre, où vous pouvez exécuter tous les tests ou un ensemble de tests que vous avez sélectionnés.

![Fenêtre de test présentant une liste de tests unitaires et une barre d’outils pour l’exécution ou l’arrêt des tests.](media/test-window.PNG)

Lors de la modification d’une classe C# qui contient des tests unitaires, vous pouvez exécuter des tests en cliquant avec le bouton droit dans la classe de test ou une méthode de test et en choisissant le menu **exécuter** les tests ou le ou les **tests de débogage** . Si vous choisissez l’élément de menu **exécuter** les tests, les tests sont exécutés dans la fenêtre de test. Si vous choisissez le menu Déboguer les **tests** , vous le faites et vous attachez le débogueur afin de pouvoir résoudre les problèmes de votre code.

![Menu contextuel de l’éditeur avec les options exécuter et déboguer les tests](media/run-tests-context-menu.PNG)

À mesure que les tests sont exécutés, une fenêtre de **résultats des tests** s’affiche pour vous permettre d’examiner les tests réussis ou ayant échoué, ainsi que la sortie de l’exécution de ces tests.

![Fenêtre résultats des tests présentant un test ayant échoué et un nombre de 21 tests réussis et 1 échec du test.](media/test-results-window.PNG)

## <a name="see-also"></a>Voir aussi

- [Tests unitaires dans .NET Core et .NET Standard](/dotnet/core/testing)
- [Prise en main des tests unitaires (Visual Studio sur Windows)](/visualstudio/test/getting-started-with-unit-testing)
- [Concepts de base des tests unitaires (Visual Studio sur Windows)](/visualstudio/test/unit-test-basics)
