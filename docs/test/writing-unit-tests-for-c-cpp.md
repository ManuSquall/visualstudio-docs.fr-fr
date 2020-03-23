---
title: Écrire des tests unitaires pour C/C++
description: Écrivez des tests unitaires CMD dans Visual Studio à l’aide de divers cadres de test, y compris CTest, Boost.Test et Google Test.
ms.date: 02/08/2020
ms.topic: conceptual
ms.author: corob
manager: markl
ms.workload:
- cplusplus
author: corob-msft
ms.openlocfilehash: 354ccad121884c99541057a2e0e0a47d9d2a4341
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "78937552"
---
# <a name="write-unit-tests-for-cc-in-visual-studio"></a>Écrire des tests unitaires pour C/C++ dans Visual Studio

Vous pouvez écrire et exécuter vos tests unitaires CMD en utilisant la fenêtre **Test Explorer.** Il fonctionne comme il le fait pour d’autres langues. Pour plus d’informations sur l’utilisation de **l’Explorateur de tests**, consultez [Exécuter des tests unitaires avec l’Explorateur de tests](run-unit-tests-with-test-explorer.md).

> [!NOTE]
> Certaines fonctionnalités, comme Live Unit Testing, les tests codés de l’interface utilisateur et IntelliTest, ne sont pas prises en charge pour C++.

Visual Studio inclut ces frameworks de test C++, aucun téléchargement supplémentaire n’étant nécessaire :

- Framework de tests unitaires Microsoft pour C++
- Google Test
- Boost.Test
- CTest

En plus d’utiliser les cadres installés, vous pouvez écrire votre propre adaptateur de test pour n’importe quel cadre que vous souhaitez utiliser dans Visual Studio. Un adaptateur de test peut intégrer des tests unitaires à la fenêtre de **l’Explorateur de tests**. Plusieurs adaptateurs de tiers sont disponibles sur [Visual Studio Marketplace](https://marketplace.visualstudio.com). Pour plus d’informations, consultez [Installer des frameworks de tests unitaires de tiers](install-third-party-unit-test-frameworks.md).

**Visual Studio 2017 et ultérieur (Professional et Enterprise)**

Prise en charge de projets de test unitaire C++ [CodeLens](../ide/find-code-changes-and-other-history-with-codelens.md).

**Visual Studio 2017 et ultérieur (toutes les éditions)**

- **Google Test Adapt est** inclus comme un composant par défaut du **développement de bureau avec** la charge de travail C . Il a un modèle de projet que vous pouvez ajouter à une solution. Utilisez le menu **Add New Project** en clic droit sur le nœud de solution dans Solution **Explorer** pour l’ajouter. Il dispose également d’options que vous pouvez configurer via **Tools** > **Options**. Pour plus d’informations, voir [Comment : Utilisez Google Test dans Visual Studio](how-to-use-google-test-for-cpp.md).

- **Boost.Test** est inclus comme un composant par défaut du **développement de bureau avec la** charge de travail C . Il est intégré à **Test Explorer**, mais n’a actuellement pas de modèle de projet. Il doit être configuré manuellement. Pour plus d’informations, voir [Comment : Utilisez Boost.Test dans Visual Studio](how-to-use-boost-test-for-cpp.md).

- La prise en charge de **CTest** est incluse dans le composant **Outils CMake pour C++** qui fait partie de la charge de travail **Développement Desktop en C++**. Pour plus d’informations, voir [Comment : Utilisez CTest dans Visual Studio](how-to-use-ctest-for-cpp.md).

**Visual Studio 2015 et antérieur**

Vous pouvez télécharger l’adaptateur Google Test et les extensions Boost.Test Adapt sur le visual Studio Marketplace. Trouvez-les à [l’adaptateur de test pour Boost.Test](https://marketplace.visualstudio.com/items?itemName=VisualCPPTeam.TestAdapterforBoostTest) et [adaptateur de test pour Google Test](https://marketplace.visualstudio.com/items?itemName=VisualCPPTeam.TestAdapterforGoogleTest).

## <a name="basic-test-workflow"></a>Workflow de base des tests

Les sections suivantes décrivent les étapes de base pour vous familiariser avec les tests unitaires C++. La configuration de base est similaire pour les cadres Microsoft et Google Test. Boost.Test nécessite la création manuelle d’un projet de test.

::: moniker range="vs-2019"

### <a name="create-a-test-project-in-visual-studio-2019"></a>Créer un projet de test dans Visual Studio 2019

Vous définissez et exécutez des tests à l’intérieur d’un ou de plusieurs projets de test. Vous créez les projets dans la même solution que le code que vous souhaitez tester. Pour ajouter un nouveau projet de test à une solution existante, cliquez à droite sur le nœud Solution dans **Solution Explorer**. Dans le menu pop-up, choisissez **Add** > **New Project**. Définissez **Langage** sur C++ et tapez « test » dans la zone de recherche. L’illustration suivante montre les projets de test qui sont disponibles quand les charges de travail **Développement Desktop en C++** et **Développement UWP** sont installées :

![Projets de test C++ dans Visual Studio 2019](media/vs-2019/cpp-new-test-project-vs2019.png)

::: moniker-end

::: moniker range="vs-2017"

### <a name="create-a-test-project-in-visual-studio-2017"></a>Créer un projet de test dans Visual Studio 2017

Vous définissez et exécutez des tests à l’intérieur d’un ou de plusieurs projets de test. Vous créez les projets dans la même solution que le code que vous souhaitez tester. Pour ajouter un nouveau projet de test, cliquez à droite sur le nœud Solution dans **Solution Explorer** et choisissez **Add** > **New Project**. Dans la vitre gauche, choisissez **Visual CMD Test**. Ensuite, choisissez l’un des types de projet à partir de la vitre centrale. L’illustration suivante montre les projets de test qui sont disponibles quand la charge de travail **Développement Desktop en C++** est installée :

![Projets de test C++](media/cpp-new-test-project.png)

::: moniker-end

### <a name="create-references-to-other-projects-in-the-solution"></a>Créer des références à d’autres projets de la solution

Pour permettre l’accès aux fonctions du projet à l’essai, ajoutez une référence au projet dans votre projet d’essai. Cliquez à droite sur le nœud du projet de test dans **Solution Explorer** pour un menu pop-up. Choisissez **Ajouter la** > **référence**. Dans le dialogue Add Reference, choisissez le projet (s) que vous souhaitez tester.

![Ajouter la référence](media/cpp-add-ref-test-project.png)

### <a name="link-to-object-or-library-files"></a>Lier à des fichiers objets ou bibliothèques

Si le code de test n’exporte pas les fonctions que vous voulez tester, vous pouvez ajouter les fichiers de sortie .obj ou .lib aux dépendances du projet de test. Pour plus d’informations, voir [Pour lier les tests aux fichiers objet ou bibliothèque](/visualstudio/test/how-to-use-microsoft-test-framework-for-cpp#object_files).

### <a name="add-include-directives-for-header-files"></a>Ajouter des directives #include pour les fichiers d’en-tête

Ensuite, dans votre fichier *.cpp* `#include` test d’unité, ajoutez une directive pour tous les fichiers d’en-tête qui déclarent les types et les fonctions que vous souhaitez tester. Tapez `#include "` : IntelliSense s’active alors pour vous aider à choisir. Répétez cette opération pour les autres en-têtes.

![Ajouter des directives include](media/cpp-add-includes-test-project.png)

Pour éviter d’avoir à taper le chemin complet dans chaque déclaration inclure dans le fichier source, vous pouvez ajouter les dossiers requis dans les**propriétés** >  **du projet** > **C / C 'General** > **General** > **Inclus Directories**.

### <a name="write-test-methods"></a>Écrire des méthodes de test

> [!NOTE]
> Cette section décrit la syntaxe du framework de tests unitaires Microsoft pour C/C++. Il est documenté ici: [Microsoft.VisualStudio.TestTools.CppUnitTestFramework API référence](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md). Pour la documentation Google Test, voir [l’amorce Google Test](https://github.com/google/googletest/blob/master/googletest/docs/primer.md). Pour Boost.Test, voir [Boost Test library: The unit test framework](https://www.boost.org/doc/libs/1_46_0/libs/test/doc/html/utf.html).

Le fichier *.cpp* dans votre projet de test a une classe de talons et la méthode définie pour vous. Ils montrent un exemple de la façon d’écrire du code de test. Les signatures utilisent les TEST_CLASS et TEST_METHOD macros, qui rendent les méthodes détectables à partir de la fenêtre **Test Explorer.**

![Ajouter des directives include](media/cpp-write-test-methods.png)

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

Vous pouvez ajouter *des traits* aux méthodes de test pour spécifier les propriétaires de tests, la priorité et d’autres informations. Vous pouvez ensuite utiliser ces valeurs pour trier et regrouper des tests dans **l’Explorateur de tests**. Pour plus d’informations, voir [tests d’unités Run avec Test Explorer](run-unit-tests-with-test-explorer.md).

### <a name="run-the-tests"></a>Exécuter les tests

1. Dans le menu **Test**, choisissez **Fenêtres** > **Explorateur de tests**. L’illustration suivante montre un projet de test dont les tests n’ont pas encore été exécutés.

   ![Test Explorer avant d’exécuter des tests](media/cpp-test-explorer.png)

   > [!NOTE]
   > L’intégration de CTest à **l’Explorateur de tests** n’est pas encore disponible. Exécutez des tests CTest à partir du menu principal de CMake.

1. Si tous vos tests ne sont pas visibles dans la fenêtre, construisez le projet de test en cliquant à droite sur son nœud dans **Solution Explorer** et en choisissant **Build** or **Rebuild**.

1. Dans **Test Explorer**, choisissez Run **All**, ou sélectionnez les tests spécifiques que vous souhaitez exécuter. Cliquez avec le bouton droit sur un test pour accéder à d’autres options, notamment son exécution en mode débogage avec des points d’arrêt activés. Une fois tous les tests exécutés, la fenêtre montre quels tests ont réussi et ceux qui ont échoué :

![L’Explorateur de tests après l’exécution des tests](media/cpp-test-explorer-passed.png)

Pour les tests ayant échoué, le message montre des détails qui vous aident à diagnostiquer la cause de l’échec. Cliquez à droite sur le test défaillant pour un menu pop-up. Choisissez **Debug Selected Tests** pour passer à travers la fonction où l’échec s’est produit.

Pour plus d’informations sur l’utilisation de **l’Explorateur de tests**, consultez [Exécuter des tests unitaires avec l’Explorateur de tests](run-unit-tests-with-test-explorer.md).

Pour plus d’informations sur les tests unitaires, voir [les bases du test de l’Unité](unit-test-basics.md)

## <a name="use-codelens"></a>Utiliser CodeLens

**Visual Studio 2017 et ultérieur (éditions Professional et Enterprise)**

[CodeLens](../ide/find-code-changes-and-other-history-with-codelens.md) vous permet de voir rapidement l’état d’un test unitaire sans quitter l’éditeur de code.

Vous pouvez initialiser CodeLens pour un projet de test unitaire C++ de l’une des manières suivantes :

- Modifiez et générez votre projet de test ou solution.
- Régénérez votre projet ou solution.
- Exécuter des tests à partir de la fenêtre **Test Explorer.**

Une fois qu’il est paracé, vous pouvez voir des icônes d’état de test au-dessus de chaque test unitaire.

![C++ CodeLens - Icônes](media/cpp-test-codelens-icons.png)

Cliquez sur l’icône pour plus d’informations, ou pour exécuter ou déboguer le test unitaire :

![C++ CodeLens - Exécuter et déboguer](media/cpp-test-codelens-run-debug.png)

## <a name="see-also"></a>Voir aussi

- [Test unitaire de votre code](unit-test-your-code.md)
