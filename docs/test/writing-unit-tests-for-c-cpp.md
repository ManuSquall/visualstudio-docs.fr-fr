---
title: "Écrire des tests unitaires pour C/C++ dans Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4f4b5f10-7314-4725-8c6e-e72f52eff918
caps.latest.revision: "14"
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: dd663d17dc7d0dc66af7cdd27f0da3cf9a253523
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="write-unit-tests-for-cc-in-visual-studio"></a>Écrire des tests unitaires pour C/C++ dans Visual Studio
Vous pouvez écrire et exécuter vos tests unitaires C++ en utilisant la fenêtre **Explorateur de tests**, tout comme pour d’autres langages. Pour plus d’informations sur l’utilisation de **l’Explorateur de tests**, consultez [Exécuter des tests unitaires avec l’Explorateur de tests](run-unit-tests-with-test-explorer.md). 

> [!NOTE]
> Certaines fonctionnalités, comme Live Unit Testing, les tests codés de l’interface utilisateur et IntelliTest, ne sont pas prises en charge pour C++. 

Visual Studio inclut ces frameworks de test C++, aucun téléchargement supplémentaire n’étant nécessaire :
 -  Framework de tests unitaires Microsoft pour C++  
 -  Google Test
 -  Boost.Test
 -  CTest

En plus des frameworks installés, vous pouvez écrire votre propre adaptateur de test pour n’importe quel framework que vous voulez utiliser dans Visual Studio. Un adaptateur de test peut intégrer des tests unitaires à la fenêtre de **l’Explorateur de tests**. Plusieurs adaptateurs de tiers sont disponibles sur [Visual Studio Marketplace](https://marketplace.visualstudio.com). Pour plus d’informations, consultez [Installer des frameworks de tests unitaires de tiers](install-third-party-unit-test-frameworks.md).

**Visual Studio 2017 version 15.5**  

1) **L’Adaptateur Google Test** est inclus comme composant par défaut de la charge de travail **Développement Desktop en C++**. Il a un modèle de projet que vous pouvez ajouter à une solution via le menu contextuel **Ajouter un nouveau projet** sur le nœud de la solution dans **l’Explorateur de solutions**, et des options que vous pouvez configurer via **Outils | Options**. Pour plus d’informations, consultez [Guide pratique pour utiliser Google Test dans Visual Studio](how-to-use-google-test-for-cpp.md).

2) **Boost.Test** est inclus comme composant par défaut de la charge de travail **Développement Desktop en C++**. Il est intégré à **l’Explorateur de tests**, mais il n’a actuellement pas de modèle de projet : il doit donc être configuré manuellement. Pour plus d’informations, consultez [Guide pratique pour utiliser Boost.Test dans Visual Studio](how-to-use-boost-test-for-cpp.md). 

3) La prise en charge de **CTest** est incluse dans le composant [Outils CMake pour Visual Studio](/cpp/ide/cmake-tools-for-cpp.md) qui fait partie de la charge de travail **Développement Desktop en C++**. Toutefois, CTest n’est pas encore entièrement intégré à **l’Explorateur de tests**. Pour plus d’informations, consultez [Guide pratique pour utiliser CTest dans Visual Studio](how-to-use-ctest-for-cpp.md).


**Visual Studio 2015 et antérieur**
  
Vous pouvez télécharger les extensions de l’adaptateur Google Test et de l’adaptateur Boost.Test sur Visual Studio Marketplace depuis [Adaptateur de test pour Boost.Test](https://marketplace.visualstudio.com/items?itemName=VisualCPPTeam.TestAdapterforBoostTest) et [Adaptateur de test pour Google Test](https://marketplace.visualstudio.com/items?itemName=VisualCPPTeam.TestAdapterforGoogleTest). 

  
## <a name="basic-test-workflow"></a>Workflow de base des tests
Les sections suivantes décrivent les étapes de base pour vous familiariser avec les tests unitaires C++. La configuration de base est très similaire pour les frameworks Microsoft et Google Test. Boost.Test nécessite la création manuelle d’un projet de test. 
  
### <a name="create-a-test-project"></a>Créer un projet de test
Vous définissez et vous exécutez des tests au sein d’un ou plusieurs projets de test qui se trouvent dans la même solution que le code que vous voulez tester. Pour ajouter un nouveau projet de test à une solution existante, cliquez avec le bouton droit sur le nœud de la solution dans **l’Explorateur de solutions**, puis choisissez **Ajouter | Nouveau projet**. Ensuite, dans le volet gauche, choisissez **Test Visual C++** et choisissez un des types de projet dans le volet central. L’illustration suivante montre les projets de test qui sont disponibles quand la charge de travail **Développement Desktop en C++** est installée :

![Projets de test C++](media/cpp-new-test-project.png "Modèles de nouveaux projets de test C++")

### <a name="create-references-to-other-projects-in-the-solution"></a>Créer des références à d’autres projets de la solution
Pour permettre à votre code de test d’accéder aux fonctions du projet à tester, ajoutez une référence au projet dans votre projet de test. Cliquez avec le bouton droit sur le nœud du projet de test dans **l’Explorateur de solutions**, puis choisissez **Ajouter | Référence**. Ensuite, dans la boîte de dialogue, choisissez le ou les projets que vous voulez tester.

![Ajouter une référence](media/cpp-add-ref-test-project.png "Test C++ : ajouter une référence à des projets à tester")

### <a name="add-include-directives-for-header-files"></a>Ajouter des directives #include pour les fichiers d’en-tête
Ensuite, dans votre fichier .cpp de test unitaire, ajoutez une directive `#include` pour les fichiers d’en-tête qui déclarent les types et les fonctions que vous voulez tester. Tapez `#include "` : Intellisense s’active alors pour vous aider à choisir. Répétez cette opération pour les autres en-têtes.

![Ajouter des directives include](media/cpp-add-includes-test-project.png "Test C++ : ajouter des directives include pour les fichiers d’en-tête")

### <a name="write-test-methods"></a>Écrire des méthodes de test
> [!NOTE] 
> Cette section décrit la syntaxe du framework de tests unitaires Microsoft pour C/C++. Elle est documentée ici : [Informations de référence sur l’API Microsoft.VisualStudio.TestTools.CppUnitTestFramework](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md). Pour la documentation de Google Test, consultez [Google Test Primer](https://github.com/google/googletest/blob/master/googletest/docs/Primer.md). Pour Boost.Test, consultez [Boost Test Library: The Unit Test Framework](http://www.boost.org/doc/libs/1_46_0/libs/test/doc/html/utf.html).

Le fichier .cpp de votre projet de test a une classe et une méthode stub définies pour vous, à titre d’exemple de la façon d’écrire du code de test. Notez que les signatures utilisent les macros TEST_CLASS et TEST_METHOD, qui rendent les méthodes découvrables à partir de la fenêtre Explorateur de tests.

![Ajouter des directives include](media/cpp-write-test-methods.png "Test C++ : ajouter des directives include pour les fichiers d’en-tête")

TEST_CLASS et TEST_METHOD font partie du [framework de tests unitaires Microsoft]((microsoft-visualstudio-testtools-cppunittestframework-api-reference.md). **L’Explorateur de tests** découvre de la même façon les méthodes de test dans les autres frameworks pris en charge.

TEST_METHOD retourne void. Pour produire un résultat de test, utilisez les méthodes statiques de la classe `Assert` pour tester les résultats réels par rapport à ce qui est attendu. Dans l’exemple suivant, supposons que `MyClass` a un constructeur qui accepte une `std::string`. Nous pouvons tester que le constructeur initialise la classe comme attendu :

```cpp
        TEST_METHOD(TestClassInit)
        {
            std::string name = "Bill";
            MyClass mc(name);
            Assert::AreEqual(name, mc.GetName());
        }
```
Dans l’exemple précédent, le résultat de l’appel `Assert::AreEqual` détermine si le test réussit ou échoue. La classe Assert contient de nombreuses autres méthodes pour la comparaison entre des résultats attendus et des résultats réels. 

Vous pouvez ajouter des *caractéristiques* aux méthodes de test pour spécifier des propriétaires, la priorité et d’autres informations sur les tests. Vous pouvez ensuite utiliser ces valeurs pour trier et regrouper des tests dans **l’Explorateur de tests**. Pour plus d’informations, consultez [Exécuter des tests unitaires avec l’Explorateur de tests](run-unit-tests-with-test-explorer.md).


### <a name="run-the-tests"></a>Exécuter les tests  
  
1.  Dans le menu **Test**, choisissez **Fenêtres**, puis **Explorateur de tests**. L’illustration suivante montre un projet de test dont les tests n’ont pas encore été exécutés. 

![L’Explorateur de tests avant l’exécution des tests](media/cpp-test-explorer.png "Explorateur de tests C++")

> [!NOTE]
> L’intégration de CTest à **l’Explorateur de tests** n’est pas encore disponible. Exécutez des tests CTest à partir du menu principal de CMake.

2. Si vos tests n’apparaissent pas tous dans la fenêtre, générez le projet de test en cliquant avec le bouton droit sur son nœud dans **l’Explorateur de solutions** et en choisissant **Générer** ou **Régénérer**.
  
3.  Dans l’Explorateur de tests, choisissez **Exécuter tout** ou sélectionnez les tests spécifiques à exécuter. Cliquez avec le bouton droit sur un test pour accéder à d’autres options, notamment son exécution en mode débogage avec des points d’arrêt activés. Une fois tous les tests exécutés, la fenêtre montre quels tests ont réussi et ceux qui ont échoué :

![L’Explorateur de tests après l’exécution des tests](media/cpp-test-explorer-passed.png "Explorateur de tests C++ après l’exécution des tests")

Pour les tests ayant échoué, le message montre des détails qui vous aident à diagnostiquer la cause de l’échec. Vous pouvez cliquer avec le bouton droit sur le test qui a échoué et choisir **Déboguer les tests sélectionnés** pour exécuter un pas à pas détaillé de la fonction où l’échec s’est produit. 

Pour plus d’informations sur l’utilisation de **l’Explorateur de tests**, consultez [Exécuter des tests unitaires avec l’Explorateur de tests](run-unit-tests-with-test-explorer.md).

Pour les bonnes pratiques relatives aux tests unitaires, consultez [Concepts de base des tests unitaires](unit-test-basics.md)

## <a name="see-also"></a>Voir aussi
[Tests unitaires sur votre code](unit-test-your-code.md)

