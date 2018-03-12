---
title: Guide pratique pour utiliser Boost.Test pour C++ dans Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 01/29/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b91c4dc3cc3bc3550f11bc60c95f1c3ed511cf62
ms.sourcegitcommit: 8cbe6b38b810529a6c364d0f1918e5c71dee2c68
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2018
---
# <a name="how-to-use-boosttest-for-c-in-visual-studio"></a>Guide pratique pour utiliser Boost.Test pour C++ dans Visual Studio

Dans **Visual Studio 2017 version 15.5** et ultérieur, l’adaptateur de test Boost.Test est intégré dans l’IDE Visual Studio comme composant de la charge de travail **Développement Desktop en C++**.

![Adaptateur de test pour Boost.Test](media/cpp-boost-component.png "Adaptateur de test pour le composant Boost.Test")

Si la charge de travail **Développement Desktop en C++** n’est pas installée, ouvrez **Visual Studio Installer** et sélectionnez **Modifier**. Sélectionnez la charge de travail **Développement Desktop en C++**, puis choisissez le bouton **Modifier**.

## <a name="install-boost"></a>Installer Boost

Boost.Test nécessite [Boost](http://www.boost.org/)! Si Boost n’est pas installé, nous vous recommandons d’utiliser le gestionnaire de package Vcpkg.

1. Suivez les instructions de [Vcpkg : un gestionnaire de package C++ pour Windows](/cpp/vcpkg) pour installer vcpkg (si vous ne l’avez pas déjà).

1. Installez la bibliothèque dynamique ou statique de Boost.Test :

    - Exécutez **vcpkg install boost-test** pour installer la bibliothèque dynamique Boost.Test.

       - OU -

    - Exécutez **vcpkg install boost-test:x86-windows-stati** pour installer la bibliothèque statique Boost.Test.

1. Exécutez **vcpkg integrate install** pour configurer Visual Studio avec la bibliothèque et inclure les chemins d’accès des en-têtes et des binaires Boost.

## <a name="add-the-item-template-visual-studio-2017-version-156-and-later"></a>Ajouter le modèle d’élément (Visual Studio 2017 15.6 et versions ultérieures)

1. Pour créer un fichier .cpp à des fins de tests, cliquez avec le bouton droit sur le nœud du projet dans **l’Explorateur de solutions**, puis choisissez **Ajouter un nouvel élément**.

   ![Modèle d’élément Boost.Test](media/boost_test_item_template.png "Modèle d’élément Boost.Test")

1. Le nouveau fichier contient un exemple de méthode de test. Générez votre projet pour permettre à **l’Explorateur de tests** de découvrir la méthode.

Le modèle d’élément utilise la variante à en-tête unique de Boost.Test, mais vous pouvez modifier le chemin d’accès #include pour utiliser la variante avec bibliothèque autonome. Pour plus d’informations, consultez la section [Ajouter des directives include](#add_include_directives).

## <a name="create-a-test-project-visual-studio-2017-version-155"></a>Créer un projet de test (Visual Studio 2017 version 15.5)

Dans Visual Studio 2017 version 15.5, aucun modèle de projet ou d’élément de test préconfiguré n’est disponible pour Boost.Test. Vous devez donc créer et configurer un projet d’application de console pour y placer vos tests.

1. Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le nœud de la solution et choisissez **Ajouter** > **Nouveau projet**.

1. Dans le volet gauche, choisissez **Visual C++** > **Windows Desktop**, puis le modèle **Application console Windows**.

1. Nommez le projet et choisissez **OK**.
1. Supprimez la fonction `main` dans le fichier .cpp.

1. Si vous utilisez la version à en-tête unique ou la version à bibliothèque dynamique de Boost.Test, accédez à la section [Ajouter des directives #include](#add_include_directives). Si vous utilisez la version avec bibliothèque statique, vous devrez suivre des étapes de configuration supplémentaires :

   a. Pour modifier le fichier projet, commencez par le décharger. Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le nœud du projet et choisissez **Décharger le projet**. Ensuite, cliquez avec le bouton droit sur le nœud du projet et choisissez **Modifier <nom\>.vcxproj**.

   b. Ajouter deux lignes au groupe de propriétés **Globals** comme indiqué ici :

    ```xml
    <PropertyGroup Label="Globals">
    ....
        <VcpkgTriplet>x86-windows-static</VcpkgTriplet>
        <VcpkgEnabled>true</VcpkgEnabled>
    </PropertyGroup>
    ```
   c. Enregistrez et fermez le fichier \*.vcxproj, puis rechargez le projet.

   d. Pour ouvrir les **pages de propriétés**, cliquez avec le bouton droit sur le nœud du projet et choisissez **Propriétés**.

   d. Développez **C/C++** > **Génération de code**, puis sélectionnez **Bibliothèque Runtime**. Sélectionnez **/MTd** pour une bibliothèque runtime statique de débogage ou **/MT** pour une bibliothèque runtime statique de publication.

   f. Développez **Éditeur de liens > Système**. Vérifiez que **Sous-système** a la valeur **Console**.

   g. Choisissez **OK** pour fermer les pages de propriétés.

## <a name="add-include-directives"></a>Ajouter des directives include

1. Dans votre fichier .cpp de test, ajoutez les directives `#include` nécessaires pour rendre les types et les fonctions de votre programme visibles par le code de test. En règle générale, le programme est un niveau au-dessus dans l’arborescence des dossiers. Si vous tapez `#include "../"`, une fenêtre IntelliSense apparaît et vous permet de sélectionner le chemin complet du fichier d’en-tête.

   ![Ajouter des directives #include](media/cpp-gtest-includes.png "Ajouter des directives include dans le fichier .cpp de test")

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

BOOST_AUTO_TEST_CASE(my\_boost_test)
{
    std::string expected_value = "Bill";

    // assume MyClass is defined in MyClass.h
    // and get_value() has public accessibility
    MyClass mc;
    BOOST_CHECK(expected_value == mc.get_value());
}
```

## <a name="write-and-run-tests"></a>Écrire et exécuter des tests
Vous êtes maintenant prêt à écrire et à exécuter des tests Boost. Pour plus d’informations sur les macros de test, consultez la [documentation de la bibliothèque de tests Boost](http://www.boost.org/doc/libs/release/libs/test/doc/html/index.html). Pour plus d’informations sur la découverte, l’exécution et le regroupement de vos tests avec **l’Explorateur de tests**, consultez [Exécuter des tests unitaires avec l’Explorateur de tests](run-unit-tests-with-test-explorer.md).

## <a name="see-also"></a>Voir aussi
[Écriture de tests unitaires pour C/C++](writing-unit-tests-for-c-cpp.md)
