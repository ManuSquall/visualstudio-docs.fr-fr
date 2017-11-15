---
title: "Bien démarrer avec les tests unitaires - Créer des plans de test | Microsoft Docs"
ms.custom: 
ms.date: 05/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: unit testing, create unit test plans
ms.assetid: 2171CD69-FBB1-4994-9DCC-3BFFDFD26662
caps.latest.revision: "56"
ms.author: douge
manager: douge
ms.openlocfilehash: 17113215615ff87ef0af611a5bc2061ca0126911
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="get-started-with-unit-testing"></a>Bien démarrer avec les tests unitaires

Utilisez Visual Studio pour définir et exécuter vos tests unitaires afin de maintenir l’intégrité du code, garantir la couverture du code et rechercher les erreurs ainsi que les pannes avant vos clients.

<a name="create-tests"></a>
## <a name="create-unit-tests"></a>Créer des tests unitaires

Créez des tests unitaires et exécutez-les souvent pour vérifier que votre code fonctionne correctement.

1. Créez un projet de test unitaire.
        
   ![Ajouter un projet de test unitaire à votre solution](media/createunittest1.png)
    
1. Nommez votre projet.
        
   ![Modèle de projet de test unitaire](media/createunittest2.png)
  
   Le projet est ajouté à votre solution.
    
   ![Projet de test unitaire dans l’Explorateur de solutions](media/createunittest5.png)
    
1. Dans le projet de test unitaire, ajoutez une référence au projet que vous voulez tester.
        
   ![Ajouter une référence à votre projet de test unitaire](media/createunittest6.png)
    
1. Sélectionnez le projet qui contient le code que vous allez tester.
        
   ![Sélectionner la référence à ajouter](media/createunittest7.png)
    
1. Codez votre test unitaire.

   ![Ajouter du code à votre test unitaire](media/createunittest8.png) 

Vous pouvez aussi créer des stubs de méthodes de tests unitaires avec la [commande **Créer des tests unitaires**](create-unit-tests-menu.md).
Vous pouvez également utiliser un [autre framework de tests unitaires](#frameworks) afin de créer des tests pour plusieurs langages de code.

![Utilisation de la commande Créer des tests unitaires](media/createunittestcommand2.png)

## <a name="run-unit-tests"></a>Exécuter des tests unitaires

1. Ouvrez l’Explorateur de tests.
        
   ![Dans le menu Test, ouvrir Explorateur de tests](media/rununittest1.png) 

1. Exécutez des tests unitaires.
        
   ![Exécuter des tests unitaires dans l'Explorateur de tests](media/rununittest2.png) 

   Dans l’Explorateur de tests, vous pouvez voir les tests unitaires qui ont abouti ou échoué.
      
   ![Examiner les résultats des tests unitaires dans l’Explorateur de tests](media/rununittest3.png) 

## <a name="view-live-unit-test-results"></a>Afficher les résultats des tests unitaires en direct

Si vous utilisez le framework de test MSTest, xUnit ou NUnit dans Visual Studio 2017 ou ultérieur, vous pouvez afficher les résultats en direct de vos tests unitaires dans l’interface utilisateur de Visual Studio.

1. Activez les tests unitaires en direct à partir du menu **Test**.

   ![Activer les tests unitaires en direct](media/live-test-results-start.png) 

1. Affichez les résultats des tests dans la fenêtre d’éditeur de code quand vous écrivez et modifiez le code.

   ![Pointer et cliquer sur les indicateurs des résultats des tests](media/live-test-results-ui.png) 

1. Pointez et cliquez sur les indicateurs des résultats des tests pour afficher d’autres informations.

   ![Afficher les résultats des tests](media/live-test-results-details.png) 

Pour plus d’informations, consultez [Live Unit Testing in Visual Studio](https://blogs.msdn.microsoft.com/visualstudio/2016/11/18/live-unit-testing-visual-studio-2017-rc/).

<a name="intellitest"></a>
## <a name="generate-unit-tests-with-intellitest"></a>Générer des tests unitaires avec IntelliTest

Lorsque vous exécutez IntelliTest, vous pouvez facilement détecter les tests qui échouent et ajouter le code nécessaire pour les corriger. Vous pouvez sélectionner les tests générés à enregistrer dans un projet de test pour fournir une suite de régression. À mesure que vous modifiez votre code, relancez IntelliTest pour synchroniser les tests générés avec les changements de code. Pour savoir comment procéder, consultez [Génération de tests unitaires pour votre code avec IntelliTest](https://docs.microsoft.com/visualstudio/test/generate-unit-tests-for-your-code-with-intellitest).

![Génération de tests unitaires avec IntelliTest](media/intellitest.png)

<a name="unit-tests"></a>
## <a name="run-unit-tests-with-test-explorer"></a>Exécuter des tests unitaires avec l'Explorateur de tests

Utilisez l'Explorateur de tests pour exécuter des tests unitaires à partir de Visual Studio ou de projets de tests unitaires tiers, regrouper des tests en catégories, filtrer la liste de tests et créer, enregistrer et exécuter des sélections de tests. Vous pouvez également déboguer des tests et analyser les performances des tests et la couverture du code. Pour savoir comment procéder, consultez [Exécuter des tests unitaires avec l’Explorateur de tests](https://docs.microsoft.com/visualstudio/test/run-unit-tests-with-test-explorer).

![Exécution de tests unitaires avec l’Explorateur de tests](media/testexplorer.png)

<a name="code-coverage"></a>
## <a name="use-code-coverage-to-determine-how-much-code-is-being-tested"></a>Utiliser la couverture du code pour déterminer la quantité de code testé

Pour déterminer la proportion de code de votre projet qui sera réellement testée par des tests codés, par exemple des tests unitaires, recourez à la fonctionnalité de couverture du code de Visual Studio. Pour apporter une protection efficace contre les bogues, les tests doivent s'effectuer ou « couvrir » une proportion importante de votre code. Pour savoir comment procéder, consultez [Utiliser la couverture du code pour déterminer la quantité de code testé](https://docs.microsoft.com/visualstudio/test/using-code-coverage-to-determine-how-much-code-is-being-tested).

![Utilisation de la couverture du code pour déterminer la quantité de code testé](media/codecoverage.png)

## <a name="q--a"></a>Q et R

<!-- BEGINSECTION class="m-qanda" -->

<a name="frameworks">
</a>
####Q :    Puis-je exécuter des tests unitaires dans Visual Studio si j’utilise un autre framework de  tests unitaires ?

R : Oui, utilisez le plug-in de ce framework afin que Visual Studio Test Runner soit compatible avec celui-ci. Voici certains des [plug-ins de framework de tests unitaires pour Visual Studio](http://go.microsoft.com/fwlink/?LinkID=246630).

1. Utilisez le gestionnaire d’extensions de Visual Studio pour télécharger votre plug-in.
        
   ![Sélectionner des plug-ins de tests unitaires tiers avec le gestionnaire d’extensions](media/install3rdpartyunittestframeworks1.png) 

1. Téléchargez votre plug-in dans la galerie Visual Studio sous Outils/Test, ou recherchez-le si vous connaissez son nom.
        
   ![Télécharger votre plug-in](media/install3rdpartyunittestframeworks2.png) 

1. Créez un projet de bibliothèque de classes.
        
   ![Créer un projet de bibliothèque de classes](media/create3rdpartyunittest1.png) 

   Ajoutez le projet à votre solution.
    
   ![Nommer le projet de bibliothèque de classes et l’ajouter](media/create3rdpartyunittest3.png) 

1. Dans le projet de bibliothèque de classes, exécutez NuGet pour installer le plug-in.

   ![Gérer les packages NuGet pour installer le plug-in](media/create3rdpartyunittest3a.png) 

   [NuGet](https://www.nuget.org/) est une extension de Visual Studio que vous pouvez utiliser pour ajouter et mettre à jour des bibliothèques et des outils pour vos projets.

1. Installez votre plug-in. Si vous connaissez son nom, vous pouvez le rechercher en ligne.

   ![Installer votre framework tiers](media/create3rdpartyunittest4.png) 

   Le framework est référencé dans votre projet.
        
   ![La référence du framework de tests unitaires tiers est ajoutée à votre solution](media/create3rdpartyunittest6.png) 

1. Dans le projet de bibliothèque de classes, ajoutez une référence au projet que vous voulez tester.
        
   ![Ajouter une référence au projet](media/createunittest6.png) 

1. Sélectionnez le projet qui contient le code que vous allez tester.
        
   ![Sélectionner le projet de code à tester](media/createunittest7.png) 

1. Codez votre test unitaire.

   ![Ajouter du code à votre test unitaire](media/create3rdpartyunittest7.png)   

<!-- ENDSECTION -->

## <a name="see-also"></a>Voir aussi

* [Créer des tests unitaires, commande](create-unit-tests-menu.md)
* [Générer des tests avec IntelliTest](generate-unit-tests-for-your-code-with-intellitest.md)
* [Exécuter des tests avec l’Explorateur de tests](run-unit-tests-with-test-explorer.md)
* [Déterminer la couverture du code](using-code-coverage-to-determine-how-much-code-is-being-tested.md)
* [Améliorer la qualité du code](improve-code-quality.md)
