---
title: Guide pratique pour utiliser Boost.Test pour C++
description: Utilisez Boost.Test pour créer des tests unitaires dans Visual Studio.
ms.date: 01/29/2020
ms.topic: how-to
author: corob-msft
ms.author: corob
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: 34c593469a586d1314c7ee52f3aeb3ab6faf334c
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85287270"
---
# <a name="how-to-use-boosttest-for-c-in-visual-studio"></a>Guide pratique pour utiliser Boost.Test pour C++ dans Visual Studio

Dans Visual Studio 2017 et versions ultérieures, l’adaptateur de test Boost. test est intégré à l’IDE de Visual Studio. Il s’agit d’un composant de la charge de travail **développement Desktop en C++** .

![Adaptateur de test pour Boost.Test](media/cpp-boost-component.png)

Si la charge de travail **Développement Desktop en C++** n’est pas installée, ouvrez **Visual Studio Installer**. Sélectionnez la charge de travail **Développement Desktop en C++**, puis choisissez le bouton **Modifier**.

## <a name="install-boost"></a>Installer Boost

Boost.Test nécessite [Boost](https://www.boost.org/)! Si Boost n’est pas installé, nous vous recommandons d’utiliser le gestionnaire de package vcpkg.

1. Suivez les instructions de [vcpkg : un gestionnaire de package C++ pour Windows](/cpp/vcpkg) pour installer vcpkg (si vous ne l’avez pas déjà).

1. Installez la bibliothèque dynamique ou statique de Boost.Test :

    - Exécutez `vcpkg install boost-test` pour installer la bibliothèque dynamique de Boost.Test.

       OU

    - Exécutez `vcpkg install boost-test:x86-windows-static` pour installer la bibliothèque statique de Boost.Test.

1. Exécutez `vcpkg integrate install` pour configurer Visual Studio avec la bibliothèque et inclure les chemins des fichiers d’en-tête et des fichiers binaires de Boost.

Vous avez le choix entre la configuration de vos tests dans votre solution dans Visual Studio : vous pouvez inclure votre code de test dans le projet testé, ou vous pouvez créer un projet de test distinct pour vos tests. Les deux choix présentent des avantages et des inconvénients.

## <a name="add-tests-inside-your-project"></a>Ajouter des tests à l’intérieur de votre projet

Dans Visual Studio 2017 version 15,6 et versions ultérieures, vous pouvez ajouter un modèle d’élément pour les tests dans votre projet. Les tests et votre code résident dans le même projet. Vous devrez créer une configuration de build distincte pour générer une build de test. Et, vous devez conserver les tests de vos versions Debug et Release.

Dans Visual Studio 2017 version 15.5, aucun modèle de projet ou d’élément de test préconfiguré n’est disponible pour Boost.Test. Utilisez les instructions pour créer et configurer un projet de test distinct.

### <a name="create-a-boosttest-item"></a>Créer un élément Boost. test

1. Pour créer un fichier *. cpp* pour vos tests, cliquez avec le bouton droit sur le nœud du projet dans **Explorateur de solutions** et choisissez **Ajouter**  >  **un nouvel élément**.

1. Dans la boîte de dialogue **Ajouter un nouvel élément** , développez **Installed**  >  **Visual C++**  >  **test**installé. Sélectionnez **Boost. test**, puis choisissez **Ajouter** pour ajouter *test. cpp* à votre projet.

   ![Modèle d’élément Boost.Test](media/boost_test_item_template.png)

Le nouveau fichier *test. cpp* contient un exemple de méthode de test. Ce fichier vous permet d’inclure vos propres fichiers d’en-tête et d’écrire des tests pour votre application.

Le fichier de test utilise également des macros pour définir une nouvelle `main` routine pour les configurations de test. Si vous générez votre projet maintenant, vous verrez une erreur LNK2005, telle que « _main déjà défini dans main. obj ».

### <a name="create-and-update-build-configurations"></a>Créer et mettre à jour des configurations de build

1. Pour créer une configuration de test, dans la barre de menus, sélectionnez **générer**  >  **Configuration Manager**. Dans la boîte de dialogue **Configuration Manager** , ouvrez la liste déroulante sous Configuration de la **solution active** , puis choisissez **nouveau**. Dans la boîte de dialogue **nouvelle configuration de solution** , entrez un nom tel que « Debug UnitTests ». Sous **copier les paramètres à partir de** , sélectionnez **Déboguer**, puis choisissez **OK**.

1. Excluez le code de test de vos configurations Debug et Release : dans **Explorateur de solutions**, cliquez avec le bouton droit sur test. cpp, puis sélectionnez **Propriétés**. Dans la boîte de dialogue **pages de propriétés** , sélectionnez **toutes les configurations** dans la liste déroulante **configuration** . Sélectionnez **Propriétés de configuration**  >  **général** , puis ouvrez la liste déroulante pour la propriété **exclu de la build** . Sélectionnez **Oui**, puis choisissez **appliquer** pour enregistrer vos modifications.

1. Pour inclure le code de test dans votre configuration UnitTests de débogage, dans la boîte de dialogue **pages de propriétés** , sélectionnez **Déboguer UnitTests** dans la liste déroulante **configuration** . Sélectionnez **non** dans la propriété **exclu de la build** , puis choisissez **OK** pour enregistrer vos modifications.

1. Excluez le code principal de votre configuration UnitTests de débogage. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le fichier qui contient votre `main` fonction et sélectionnez **Propriétés**. Dans la boîte de dialogue **pages de propriétés** , sélectionnez **Déboguer UnitTests** dans la liste déroulante **configuration** . Sélectionnez **Propriétés de configuration**  >  **général** , puis ouvrez la liste déroulante pour la propriété **exclu de la build** . Sélectionnez **Oui**, puis cliquez sur **OK** pour enregistrer vos modifications.

1. Définissez la configuration de la solution sur **Déboguer UnitTests**, puis générez votre projet pour permettre à l' **Explorateur de tests** de découvrir la méthode.

Tant que le nom de la configuration que vous créez commence par les mots « Debug » ou « Release », les bibliothèques Boost. test correspondantes sont récupérées automatiquement.

Le modèle d’élément utilise la variante à en-tête unique de Boost.Test, mais vous pouvez modifier le chemin d’accès #include pour utiliser la variante avec bibliothèque autonome. Pour plus d’informations, consultez la section [Ajouter des directives include](#add-include-directives).

## <a name="create-a-separate-test-project"></a>Créer un projet de test distinct

Dans de nombreux cas, il est plus facile d’utiliser un projet distinct pour vos tests. Vous n’aurez pas à créer une configuration de test spéciale pour votre projet. Ou, excluez les fichiers de test des versions Debug et Release.

### <a name="to-create-a-separate-test-project"></a>Pour créer un projet de test distinct

1. Dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur le nœud de la solution et choisissez **Ajouter** > **Nouveau projet**.

1. Dans la boîte de dialogue **Ajouter un nouveau projet** , choisissez **C++**, **Windows**et **console** dans les listes déroulantes de filtres. Sélectionnez le modèle **application console** , puis choisissez **suivant**.

1. Nommez le projet et choisissez **Créer**.

1. Supprimez la `main` fonction dans le fichier *. cpp* .

1. Si vous utilisez la version d’en-tête unique ou de bibliothèque dynamique de Boost. test, accédez à [Ajouter des directives include](#add-include-directives). Si vous utilisez la version de la bibliothèque statique, vous devez effectuer une configuration supplémentaire :

   a. Pour modifier le fichier projet, commencez par le décharger. Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le nœud du projet et choisissez **Décharger le projet**. Ensuite, cliquez avec le bouton droit sur le nœud du projet et choisissez **Modifier <nom\>.vcxproj**.

   b. Ajouter deux lignes au groupe de propriétés **Globals** comme indiqué ici :

    ```xml
    <PropertyGroup Label="Globals">
    ....
        <VcpkgTriplet>x86-windows-static</VcpkgTriplet>
        <VcpkgEnabled>true</VcpkgEnabled>
    </PropertyGroup>
    ```

   c. Enregistrez et fermez le fichier * \* . vcxproj* , puis rechargez le projet.

   d. Pour ouvrir les **pages de propriétés**, cliquez avec le bouton droit sur le nœud du projet et choisissez **Propriétés**.

   e. Développez génération de code **C/C++**  >  **Code Generation**, puis sélectionnez **bibliothèque Runtime**. Sélectionnez **/MTd** pour une bibliothèque runtime statique de débogage ou **/MT** pour une bibliothèque runtime statique de publication.

   f. Développez le système de l' **éditeur de liens**  >  **System**. Vérifiez que **sous-système** est défini sur **console**.

   g. Choisissez **OK** pour fermer les pages de propriétés.

## <a name="add-include-directives"></a>Ajouter des directives include

1. Dans votre fichier test *. cpp* , ajoutez toutes les `#include` directives nécessaires pour rendre les types et les fonctions de votre programme visibles au code de test. Si vous utilisez un projet de test distinct, en général, le programme se trouve sur un niveau frère dans l’arborescence des dossiers. Si vous tapez `#include "../"`, une fenêtre IntelliSense apparaît et vous permet de sélectionner le chemin complet du fichier d’en-tête.

   ![Ajouter des directives #include](media/cpp-gtest-includes.png)

   Vous pouvez utiliser la bibliothèque autonome avec :

   ```cpp
   #include <boost/test/unit_test.hpp>
   ```

   Ou bien, utilisez la version à un seul en-tête avec :

   ```cpp
   #include <boost/test/included/unit_test.hpp>
   ```

   Ensuite, définissez `BOOST_TEST_MODULE`.

L’exemple suivant est suffisant pour que le test soit découvrable dans **l’Explorateur de tests** :

```cpp
#define BOOST_TEST_MODULE MyTest
#include <boost/test/included/unit_test.hpp\> //single-header
#include "../MyProgram/MyClass.h" // project being tested
#include <string>

BOOST_AUTO_TEST_CASE(my_boost_test)
{
    std::string expected_value = "Bill";

    // assume MyClass is defined in MyClass.h
    // and get_value() has public accessibility
    MyClass mc;
    BOOST_CHECK(expected_value == mc.get_value());
}
```

## <a name="write-and-run-tests"></a>Écrire et exécuter des tests

Vous êtes maintenant prêt à écrire et à exécuter des tests Boost. Pour plus d’informations sur les macros de test, consultez la documentation de la [bibliothèque de test Boost](https://www.boost.org/doc/libs/1_71_0/libs/test/doc/html/index.html) . Pour plus d’informations sur la découverte, l’exécution et le regroupement de vos tests avec **l’Explorateur de tests**, consultez [Exécuter des tests unitaires avec l’Explorateur de tests](run-unit-tests-with-test-explorer.md).

## <a name="see-also"></a>Voir aussi

- [Écrire des tests unitaires pour C/C++](writing-unit-tests-for-c-cpp.md)
