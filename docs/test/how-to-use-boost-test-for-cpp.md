---
title: Guide pratique pour utiliser Boost.Test pour C++
description: Utilisez Boost.Test pour créer des tests unitaires dans Visual Studio.
ms.date: 01/29/2020
ms.topic: conceptual
author: corob-msft
ms.author: corob
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: 0a1a621c7ee7175d86b2cbcf9a6e2c02c0aecbb3
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "76922920"
---
# <a name="how-to-use-boosttest-for-c-in-visual-studio"></a>Guide pratique pour utiliser Boost.Test pour C++ dans Visual Studio

Dans Visual Studio 2017 et plus tard, l’adaptateur de test Boost.Test est intégré dans l’IDE Visual Studio. Il s’agit d’un élément du développement de bureau avec la charge de travail **de C.**

![Adaptateur de test pour Boost.Test](media/cpp-boost-component.png)

Si la charge de travail **Développement Desktop en C++** n’est pas installée, ouvrez **Visual Studio Installer**. Sélectionnez la charge de travail **Développement Desktop en C++**, puis choisissez le bouton **Modifier**.

## <a name="install-boost"></a>Installer Boost

Boost.Test nécessite [Boost](https://www.boost.org/)! Si vous n’avez pas de Boost installé, nous vous recommandons d’utiliser le gestionnaire de paquetS Vcpkg.

1. Suivez les instructions chez [Vcpkg : un gestionnaire de paquets CMD pour Windows pour](/cpp/vcpkg) installer des vcpkg (si vous ne l’avez pas déjà).

1. Installez la bibliothèque dynamique ou statique de Boost.Test :

    - Exécutez `vcpkg install boost-test` pour installer la bibliothèque dynamique de Boost.Test.

       OU

    - Exécutez `vcpkg install boost-test:x86-windows-static` pour installer la bibliothèque statique de Boost.Test.

1. Exécutez `vcpkg integrate install` pour configurer Visual Studio avec la bibliothèque et inclure les chemins des fichiers d’en-tête et des fichiers binaires de Boost.

Vous avez le choix de configurer vos tests dans votre solution dans Visual Studio : vous pouvez inclure votre code de test dans le projet testé, ou vous pouvez créer un projet de test distinct pour vos tests. Les deux choix ont des avantages et des inconvénients.

## <a name="add-tests-inside-your-project"></a>Ajoutez des tests à l’intérieur de votre projet

Dans Visual Studio 2017 version 15.6 et plus tard, vous pouvez ajouter un modèle d’élément pour les tests dans votre projet. Les tests et votre code vivent dans le même projet. Vous devrez créer une configuration de construction séparée pour générer une version de test. Et, vous aurez besoin de garder les tests hors de votre débbug et la libération construit.

Dans Visual Studio 2017 version 15.5, aucun modèle de projet ou d’élément de test préconfiguré n’est disponible pour Boost.Test. Utilisez les instructions pour créer et configurer un projet de test distinct.

### <a name="create-a-boosttest-item"></a>Créer un élément Boost.Test

1. Pour créer un fichier *.cpp* pour vos tests, cliquez à droite sur le nœud de projet dans **Solution Explorer** et choisissez **Ajouter** > **un nouvel article**.

1. Dans le dialogue **Add New Item,** étendre **le** > test**Visual CMD** > **installé**. Sélectionnez **Boost.Test**, puis choisissez **Ajouter** pour ajouter *Test.cpp* à votre projet.

   ![Modèle d’élément Boost.Test](media/boost_test_item_template.png)

Le nouveau fichier *Test.cpp* contient une méthode d’essai d’échantillon. Ce fichier est l’endroit où vous pouvez inclure vos propres fichiers d’en-tête et écrire des tests pour votre application.

Le fichier de test utilise également `main` des macros pour définir une nouvelle routine pour les configurations de test. Si vous construisez votre projet maintenant, vous verrez une erreur LNK2005, telle que "_main déjà défini dans main.obj."

### <a name="create-and-update-build-configurations"></a>Créer et mettre à jour les configurations de construction

1. Pour créer une configuration de test, sur la barre de menu, sélectionnez **Build** > **Configuration Manager**. Dans le dialogue **Configuration Manager,** ouvrez le dropdown sous **la configuration de la solution Active** et choisissez **New**. Dans le **dialogue New Solution Configuration,** entrez un nom tel que "Debug UnitTests". Sous **Les paramètres de copie de** select **Debug**, puis choisissez **OK**.

1. Exclure le code de test de vos configurations Debug et Release : In **Solution Explorer**, cliquez à droite sur Test.cpp et sélectionnez **les propriétés.** Dans le dialogue **des pages de propriété,** sélectionnez **toutes les configurations** dans le décrochage **de configuration.** Sélectionnez **Configuration Properties** > **General** et ouvrez le dépôt pour la propriété **Excluded From Build.** Sélectionnez **Oui,** puis choisissez **Apply** pour enregistrer vos modifications.

1. Pour inclure le code de test dans votre configuration Debug UnitTests, dans le dialogue **des pages de propriété,** sélectionnez **Les tests d’unités Debug** dans le dropdown **Configuration.** Sélectionnez **Non** dans la propriété **Excluded From Build,** puis choisissez **OK** pour enregistrer vos modifications.

1. Exclure le code principal de votre configuration Debug UnitTests. Dans **Solution Explorer**, cliquez à droite `main` sur le fichier qui contient votre fonction et sélectionnez **les propriétés**. Dans le dialogue **des pages de propriété,** sélectionnez **Les unités Debug** dans le dropdown **configuration.** Sélectionnez **Configuration Properties** > **General** et ouvrez le dépôt pour la propriété **Excluded From Build.** Sélectionnez **Oui,** puis choisissez **OK** pour enregistrer vos modifications.

1. Définissez la configuration de la solution pour **Debug UnitTests,** puis construisez votre projet pour permettre à **Test Explorer** de découvrir la méthode.

Tant que le nom de configuration que vous créez commence par les mots "Debug" ou "Release", les bibliothèques Boost.Test correspondantes sont captées automatiquement.

Le modèle d’élément utilise la variante à en-tête unique de Boost.Test, mais vous pouvez modifier le chemin d’accès #include pour utiliser la variante avec bibliothèque autonome. Pour plus d’informations, consultez la section [Ajouter des directives include](#add-include-directives).

## <a name="create-a-separate-test-project"></a>Créer un projet d’essai distinct

Dans de nombreux cas, il est plus facile d’utiliser un projet distinct pour vos tests. Vous n’aurez pas à créer une configuration de test spéciale pour votre projet. Ou, exclure les fichiers de test de Debug et Release construit.

### <a name="to-create-a-separate-test-project"></a>Créer un projet d’essai distinct

1. Dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur le nœud de la solution et choisissez **Ajouter** > **Nouveau projet**.

1. Dans le **dialogue Ajouter un nouveau projet,** choisissez C **,** **Windows**, et **Console** dans les décrocheurs de filtre. Sélectionnez le modèle **d’application console,** puis choisissez **Next**.

1. Nommez le projet et choisissez **Créer**.

1. Supprimer `main` la fonction dans le fichier *.cpp.*

1. Si vous utilisez la version d’en-tête unique ou dynamique de la bibliothèque de Boost.Test, allez [ajouter des directives](#add-include-directives). Si vous utilisez la version de la bibliothèque statique, alors vous devez faire une configuration supplémentaire:

   a. Pour modifier le fichier projet, commencez par le décharger. Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le nœud du projet et choisissez **Décharger le projet**. Ensuite, cliquez avec le bouton droit sur le nœud du projet et choisissez **Modifier <nom\>.vcxproj**.

   b. Ajouter deux lignes au groupe de propriétés **Globals** comme indiqué ici :

    ```xml
    <PropertyGroup Label="Globals">
    ....
        <VcpkgTriplet>x86-windows-static</VcpkgTriplet>
        <VcpkgEnabled>true</VcpkgEnabled>
    </PropertyGroup>
    ```

   c. Enregistrer et fermer le * \*fichier .vcxproj,* puis recharger le projet.

   d. Pour ouvrir les **pages de propriétés**, cliquez avec le bouton droit sur le nœud du projet et choisissez **Propriétés**.

   e. Élargissez la**génération de code** **C/CMD,** > puis sélectionnez **Runtime Library**. Sélectionnez **/MTd** pour une bibliothèque runtime statique de débogage ou **/MT** pour une bibliothèque runtime statique de publication.

   f. Élargir le**système** **Linker** > . Verify **SubSystem** est **configuré**sur console .

   g. Choisissez **OK** pour fermer les pages de propriétés.

## <a name="add-include-directives"></a>Ajouter des directives include

1. Dans votre fichier test *.cpp,* ajoutez toutes les directives nécessaires `#include` pour rendre les types et les fonctions de votre programme visibles au code de test. Si vous utilisez un projet de test distinct, généralement, le programme est au niveau des frères et sœurs dans la hiérarchie du dossier. Si vous tapez `#include "../"`, une fenêtre IntelliSense apparaît et vous permet de sélectionner le chemin complet du fichier d’en-tête.

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

Vous êtes maintenant prêt à écrire et à exécuter des tests Boost. Consultez la documentation de la [bibliothèque de test Boost](https://www.boost.org/doc/libs/1_71_0/libs/test/doc/html/index.html) pour obtenir des informations sur les macros de test. Pour plus d’informations sur la découverte, l’exécution et le regroupement de vos tests avec **l’Explorateur de tests**, consultez [Exécuter des tests unitaires avec l’Explorateur de tests](run-unit-tests-with-test-explorer.md).

## <a name="see-also"></a>Voir aussi

- [Écrire des tests unitaires pour C/C++](writing-unit-tests-for-c-cpp.md)
