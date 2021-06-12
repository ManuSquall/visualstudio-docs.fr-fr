---
title: Écrire des tests unitaires pour C/C++
description: Écrivez des tests unitaires C++ dans Visual Studio à l’aide de différents frameworks de test, notamment CTest, Boost. test et Google Test.
ms.date: 04/01/2021
ms.topic: conceptual
ms.author: corob
manager: markl
ms.workload:
- cplusplus
author: corob-msft
ms.openlocfilehash: 877c9163d05f458ce45a46d6b3e6d14e354df591
ms.sourcegitcommit: 4b2b6068846425f6964c1fd867370863fc4993ce
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2021
ms.locfileid: "112042885"
---
# <a name="write-unit-tests-for-cc-in-visual-studio"></a>Écrire des tests unitaires pour C/C++ dans Visual Studio

Vous pouvez écrire et exécuter vos tests unitaires C++ à l’aide de la fenêtre **Explorateur de tests** . Il fonctionne comme pour d’autres langages. Pour plus d’informations sur l’utilisation de **l’Explorateur de tests**, consultez [Exécuter des tests unitaires avec l’Explorateur de tests](run-unit-tests-with-test-explorer.md).

> [!NOTE]
> Certaines fonctionnalités, comme Live Unit Testing, les tests codés de l’interface utilisateur et IntelliTest, ne sont pas prises en charge pour C++.

Visual Studio inclut ces frameworks de test C++, aucun téléchargement supplémentaire n’étant nécessaire :

- Framework de tests unitaires Microsoft pour C++
- Google Test
- Boost.Test
- CTest

Outre l’utilisation des frameworks installés, vous pouvez écrire votre propre adaptateur de test pour l’infrastructure que vous souhaitez utiliser dans Visual Studio. Un adaptateur de test peut intégrer des tests unitaires à la fenêtre de **l’Explorateur de tests**. Plusieurs adaptateurs de tiers sont disponibles sur [Visual Studio Marketplace](https://marketplace.visualstudio.com). Pour plus d’informations, consultez [Installer des frameworks de tests unitaires de tiers](install-third-party-unit-test-frameworks.md).

**Visual Studio 2017 et ultérieur (Professional et Enterprise)**

Prise en charge de projets de test unitaire C++ [CodeLens](../ide/find-code-changes-and-other-history-with-codelens.md).

**Visual Studio 2017 et ultérieur (toutes les éditions)**

- **Google test adaptateur** est inclus comme composant par défaut de la charge de travail **développement Desktop en C++** . Il possède un modèle de projet que vous pouvez ajouter à une solution. Utilisez le menu contextuel **Ajouter un nouveau projet** sur le nœud de la solution dans **Explorateur de solutions** pour l’ajouter. Il comporte également des options que vous pouvez configurer via les options des **Outils**  >  . Pour plus d’informations, consultez [Comment : utiliser des Google test dans Visual Studio](how-to-use-google-test-for-cpp.md).

- **Boost. test** est inclus comme composant par défaut de la charge de travail **développement Desktop en C++** . Il est intégré à l' **Explorateur de tests**, mais il n’a actuellement aucun modèle de projet. Elle doit être configurée manuellement. Pour plus d’informations, consultez [Comment : utiliser Boost. test dans Visual Studio](how-to-use-boost-test-for-cpp.md).

- La prise en charge de **CTest** est incluse dans le composant **Outils CMake pour C++** qui fait partie de la charge de travail **Développement Desktop en C++**. Pour plus d’informations, consultez [Comment : utiliser ctest dans Visual Studio](how-to-use-ctest-for-cpp.md).

**Visual Studio 2015 et antérieur**

Vous pouvez télécharger les extensions d’adaptateur de Google Test et Boost. test sur le Visual Studio Marketplace. Recherchez-les au niveau de l' [adaptateur de test pour Boost. test](https://marketplace.visualstudio.com/items?itemName=VisualCPPTeam.TestAdapterforBoostTest) et [test adapter pour Google test](https://marketplace.visualstudio.com/items?itemName=VisualCPPTeam.TestAdapterforGoogleTest).

## <a name="basic-test-workflow"></a>Workflow de base des tests

Les sections suivantes décrivent les étapes de base pour vous familiariser avec les tests unitaires C++. La configuration de base est similaire pour les frameworks Microsoft et Google Test. Boost.Test nécessite la création manuelle d’un projet de test.

::: moniker range=">=vs-2019"

### <a name="create-a-test-project-in-visual-studio-2019"></a>Créer un projet de test dans Visual Studio 2019

Vous définissez et exécutez des tests dans un ou plusieurs projets de test. Vous créez les projets dans la même solution que le code que vous souhaitez tester. Pour ajouter un nouveau projet de test à une solution existante, cliquez avec le bouton droit sur le nœud de la solution dans **Explorateur de solutions**. Dans le menu contextuel, choisissez **Ajouter**  >  **un nouveau projet**. Définissez **Langage** sur C++ et tapez « test » dans la zone de recherche. L’illustration suivante montre les projets de test qui sont disponibles quand les charges de travail **Développement Desktop en C++** et **Développement UWP** sont installées :

![Projets de test C++ dans Visual Studio 2019](media/vs-2019/cpp-new-test-project-vs2019.png)

::: moniker-end

::: moniker range="vs-2017"

### <a name="create-a-test-project-in-visual-studio-2017"></a>Créer un projet de test dans Visual Studio 2017

Vous définissez et exécutez des tests dans un ou plusieurs projets de test. Vous créez les projets dans la même solution que le code que vous souhaitez tester. Pour ajouter un nouveau projet de test, cliquez avec le bouton droit sur le nœud de la solution dans **Explorateur de solutions** et choisissez **Ajouter** un  >  **nouveau projet**. Dans le volet gauche, choisissez **Visual C++ test**. Ensuite, choisissez l’un des types de projet dans le volet central. L’illustration suivante montre les projets de test qui sont disponibles quand la charge de travail **Développement Desktop en C++** est installée :

![Projets de test C++](media/cpp-new-test-project.png)

::: moniker-end

### <a name="create-references-to-other-projects-in-the-solution"></a>Créer des références à d’autres projets de la solution

Pour activer l’accès aux fonctions du projet testé, ajoutez une référence au projet dans votre projet de test. Cliquez avec le bouton droit sur le nœud du projet de test dans **Explorateur de solutions** pour un menu contextuel. Choisissez **Ajouter** une  >  **référence**. Dans la boîte de dialogue Ajouter une référence, choisissez le ou les projets que vous voulez tester.

![Ajouter la référence](media/cpp-add-ref-test-project.png)

### <a name="link-to-object-or-library-files"></a>Lier à des fichiers objets ou bibliothèques

Si le code de test n’exporte pas les fonctions que vous voulez tester, vous pouvez ajouter les fichiers de sortie .obj ou .lib aux dépendances du projet de test. Pour plus d’informations, consultez [pour lier les tests aux fichiers objets ou bibliothèques](how-to-use-microsoft-test-framework-for-cpp.md#object_files).

### <a name="add-include-directives-for-header-files"></a>Ajouter des directives #include pour les fichiers d’en-tête

Ensuite, dans votre fichier *. cpp* de test unitaire, ajoutez une `#include` directive pour tous les fichiers d’en-tête qui déclarent les types et les fonctions que vous voulez tester. Tapez `#include "` : IntelliSense s’active alors pour vous aider à choisir. Répétez cette opération pour les autres en-têtes.

![Capture d’écran de l’Explorateur de solutions montrant l’ajout d’une directive #include avec IntelliSense mettant en surbrillance un fichier d’en-tête pour l’inclusion.](media/cpp-add-includes-test-project.png)

Pour éviter d’avoir à taper le chemin d’accès complet dans chaque instruction include dans le fichier source, vous pouvez ajouter les dossiers requis dans les propriétés du **projet**  >    >  **C/C++**  >  **général**  >  **autres répertoires Include**.

### <a name="write-test-methods"></a>Écrire des méthodes de test

> [!NOTE]
> Cette section décrit la syntaxe du framework de tests unitaires Microsoft pour C/C++. Il est documenté ici : informations de référence sur l' [API Microsoft. VisualStudio. TestTools. CppUnitTestFramework](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md). Pour Google Test de la documentation, consultez [Google test Primer](https://github.com/google/googletest/blob/master/docs/primer.md). Pour Boost. test, consultez [Boost test bibliothèque : infrastructure de tests unitaires](https://www.boost.org/doc/libs/1_46_0/libs/test/doc/html/utf.html).

Le fichier *. cpp* de votre projet de test a une classe stub et une méthode définie pour vous. Ils montrent un exemple d’écriture de code de test. Les signatures utilisent les macros TEST_CLASS et TEST_METHOD, qui rendent les méthodes détectables à partir de la fenêtre de l' **Explorateur de tests** .

![Capture d’écran de la fenêtre de l’Explorateur de tests qui affiche le fichier de code UnitTest1. cpp contenant une classe et une méthode stub à l’aide des macros TEST_CLASS et TEST_METHOD.](media/cpp-write-test-methods.png)

TEST_CLASS et TEST_METHOD font partie du [framework de test natif Microsoft](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md). **L’Explorateur de tests** découvre de la même façon les méthodes de test dans les autres frameworks pris en charge.

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

Vous pouvez ajouter des *caractéristiques* aux méthodes de test pour spécifier les propriétaires de test, la priorité et d’autres informations. Vous pouvez ensuite utiliser ces valeurs pour trier et regrouper des tests dans **l’Explorateur de tests**. Pour plus d’informations, consultez [exécuter des tests unitaires avec l’Explorateur de tests](run-unit-tests-with-test-explorer.md).

### <a name="run-the-tests"></a>Exécuter les tests

1. Dans le menu **Test**, choisissez **Fenêtres** > **Explorateur de tests**. L’illustration suivante montre un projet de test dont les tests n’ont pas encore été exécutés.

   ![Explorateur de tests avant d’exécuter des tests](media/cpp-test-explorer.png)

   > [!NOTE]
   > L’intégration de CTest à **l’Explorateur de tests** n’est pas encore disponible. Exécutez des tests CTest à partir du menu principal de CMake.

1. Si tous vos tests ne sont pas visibles dans la fenêtre, générez le projet de test en cliquant avec le bouton droit sur son nœud dans **Explorateur de solutions** et en choisissant **générer** ou **régénérer**.

1. Dans l' **Explorateur de tests**, choisissez **exécuter tout** ou sélectionnez les tests spécifiques que vous souhaitez exécuter. Cliquez avec le bouton droit sur un test pour accéder à d’autres options, notamment son exécution en mode débogage avec des points d’arrêt activés. Une fois tous les tests exécutés, la fenêtre montre quels tests ont réussi et ceux qui ont échoué :

![L’Explorateur de tests après l’exécution des tests](media/cpp-test-explorer-passed.png)

Pour les tests ayant échoué, le message montre des détails qui vous aident à diagnostiquer la cause de l’échec. Cliquez avec le bouton droit sur le test échec d’un menu contextuel. Choisissez **déboguer les tests sélectionnés** pour parcourir la fonction dans laquelle l’erreur s’est produite.

Pour plus d’informations sur l’utilisation de **l’Explorateur de tests**, consultez [Exécuter des tests unitaires avec l’Explorateur de tests](run-unit-tests-with-test-explorer.md).

Pour plus d’informations sur les tests unitaires, consultez [principes de base des tests unitaires](unit-test-basics.md)

## <a name="use-codelens"></a>Utiliser CodeLens

**Visual Studio 2017 et ultérieur (éditions Professional et Enterprise)**

[CodeLens](../ide/find-code-changes-and-other-history-with-codelens.md) vous permet de voir rapidement l’état d’un test unitaire sans quitter l’éditeur de code.

Vous pouvez initialiser CodeLens pour un projet de test unitaire C++ de l’une des manières suivantes :

- Modifiez et générez votre projet de test ou solution.
- Régénérez votre projet ou solution.
- Exécutez les tests à partir de la fenêtre **Explorateur de tests** .

Une fois initialisé, vous pouvez voir les icônes d’état de test au-dessus de chaque test unitaire.

![C++ CodeLens - Icônes](media/cpp-test-codelens-icons.png)

Cliquez sur l’icône pour plus d’informations, ou pour exécuter ou déboguer le test unitaire :

![C++ CodeLens - Exécuter et déboguer](media/cpp-test-codelens-run-debug.png)

## <a name="see-also"></a>Voir aussi

- [Tests unitaires de votre code](unit-test-your-code.md)
