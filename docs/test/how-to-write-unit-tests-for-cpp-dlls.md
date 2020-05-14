---
title: Écrire des tests unitaires pour des DLL C++
ms.date: 05/01/2019
ms.topic: conceptual
ms.author: corob
manager: markl
ms.workload:
- cplusplus
author: corob-msft
ms.openlocfilehash: 856bc21fdee8945ddcd97e3978f46af0008af616
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77279272"
---
# <a name="write-unit-tests-for-c-dlls-in-visual-studio"></a>Écrire des tests unitaires pour des DLL C++ dans Visual Studio

Il existe plusieurs façons de tester du code de DLL, selon qu’elle exporte ou non les fonctions que vous voulez tester. Choisissez l'un des moyens suivants :

**Les tests unitaires appellent seulement des fonctions exportées depuis la DLL :** ajoutez un projet de test distinct comme décrit dans [Écrire des tests unitaires pour C/C++](writing-unit-tests-for-c-cpp.md). Dans le projet de test, ajoutez une référence au projet DLL.

Passez à la procédure [Pour référencer des fonctions exportées depuis le projet DLL](#projectRef).

**La DLL est générée sous la forme d’un fichier .exe :** ajoutez un projet de test distinct. Liez-le au fichier objet de sortie.

Passez à la procédure [Pour lier les tests aux fichiers objets ou bibliothèques](#objectRef).

**Les tests unitaires appellent des fonctions non-membres qui ne sont pas exportées depuis la DLL, et la DLL peut être générée sous forme de bibliothèque statique :** modifiez le projet DLL pour qu’il soit compilé en un fichier *.lib*. Ajoutez un projet de test distinct qui référence le projet testé.

Cette approche présente l’avantage de permettre à vos tests d’utiliser des membres non exportés, mais de conserver les tests dans un projet distinct.

Passez à la procédure [Pour changer la DLL en une bibliothèque statique](#staticLink).

**Les tests unitaires doivent appeler des fonctions non-membres qui ne sont pas exportées, et le code doit être généré sous la forme d’une bibliothèque de liens dynamiques (DLL) :** ajoutez des tests unitaires dans le même projet que le code du produit.

Passez à la procédure [Pour ajouter des tests unitaires dans le même projet](#sameProject).

## <a name="create-the-tests"></a>Créer les tests

### <a name="to-change-the-dll-to-a-static-library"></a><a name="staticLink"></a> Pour changer la DLL en une bibliothèque statique

- Si vos tests doivent utiliser des membres qui ne sont pas exportés par le projet DLL et que le projet de test est généré sous forme d’une bibliothèque dynamique, envisagez de le convertir en bibliothèque statique.

  1. Dans **Solution Explorer**, sur le menu raccourci du projet à l’essai, choisissez **Propriétés**. La fenêtre **Propriétés** du projet s’ouvre.

  2. Choisissez **Configuration Properties** > **General**.

  3. Définissez **Type de configuration** sur **Bibliothèque statique (.lib)**.

  Poursuivez avec la procédure [Pour lier les tests aux fichiers objets ou bibliothèques](#objectRef).

### <a name="to-reference-exported-dll-functions-from-the-test-project"></a><a name="projectRef"></a> Pour référencer des fonctions de DLL exportées depuis le projet de test

- Si un projet DLL exporte les fonctions que vous voulez tester, vous pouvez ajouter une référence au projet de code depuis le projet de test.

  1. Créez un projet de test unitaire natif.

      ::: moniker range="vs-2019"

      1. Dans le menu **Fichier**, choisissez **Nouveau** > **Projet**. Dans la boîte de dialogue **Ajouter un nouveau projet**, définissez **Langage** sur C++ et tapez « test » dans la zone de recherche. Choisissez ensuite **Projet de test unitaire natif**.

      ::: moniker-end

      ::: moniker range="vs-2017"

      1. Dans le menu **Fichier**, choisissez **Nouveau** > **Projet** > **Visual C++** > **Test** > **Projet de test unitaire C++**.

      ::: moniker-end

  1. Cliquez avec le bouton droit sur le projet de test dans **l’Explorateur de solutions**, puis choisissez **Ajouter** > ** Référence**.

  1. Sélectionnez **Projets**, puis le projet à tester.

       Choisissez le bouton **Ajouter**.

  1. Dans les propriétés du projet de test, ajoutez l'emplacement du projet testé aux répertoires Include.

       Choisissez **Configuration Properties** > **VCMD Directories** > **Inclure des annuaires**.

       Choisissez **Modifier**, puis ajoutez le répertoire d’en-tête du projet testé.

  Passez à [Écrire les tests unitaires](#addTests).

### <a name="to-link-the-tests-to-the-object-or-library-files"></a><a name="objectRef"></a> Pour lier les tests aux fichiers objets ou bibliothèques

- Si la DLL n’exporte pas les fonctions que vous voulez tester, vous pouvez ajouter le fichier de sortie *.obj* ou *.lib* aux dépendances du projet de test.

  1. Créez un projet de test unitaire natif.

      ::: moniker range="vs-2019"

      1. Dans le menu **Fichier**, choisissez **Nouveau** > **Projet**. Dans la boîte de dialogue **Ajouter un nouveau projet**, définissez **Langage** sur C++ et tapez « test » dans la zone de recherche. Choisissez ensuite **Projet de test unitaire natif**.

      ::: moniker-end

      ::: moniker range="vs-2017"

      1. Dans le menu **Fichier**, choisissez **Nouveau** > **Projet** > **Visual C++** > **Test** > **Projet de test unitaire C++**.

      ::: moniker-end

  2. Dans **Solution Explorer**, sur le menu raccourci du projet d’essai, choisissez **Properties**.

  3. Choisissez **Configuration Properties** > **Linker** > **Input** > **Dépendances supplémentaires**.

       Choisissez **Modifier**, puis ajoutez les noms des fichiers **.obj** ou **.lib**. N’utilisez pas les chemins d’accès complets.

  4. Choisissez **Configuration Properties** > **Linker** > **General** > Additional Library**Directories**.

       Choisissez **Modifier**, puis ajoutez le chemin d’accès au répertoire des fichiers **.obj** ou **.lib**. Le chemin d’accès se trouve généralement dans le dossier de build du projet testé.

  5. Choisissez **Configuration Properties** > **VCMD Directories** > **Inclure des annuaires**.

       Choisissez **Modifier**, puis ajoutez le répertoire d’en-tête du projet testé.

  Passez à [Écrire les tests unitaires](#addTests).

### <a name="to-add-unit-tests-in-the-same-project"></a><a name="sameProject"></a> Pour ajouter des tests unitaires dans le même projet

1. Modifiez les propriétés du projet du code du produit pour inclure les en-têtes et les fichiers bibliothèques qui sont requis pour le test unitaire.

   1. Dans **l’Explorateur de solutions**, dans le menu contextuel du projet testé, choisissez **Propriétés**. La fenêtre **Propriétés** du projet s’ouvre.

   2. Choisissez **Configuration Properties** > **VCMD Directories**.

   3. Modifiez les répertoires Include et de bibliothèques :

       |Répertoire|Propriété|
       |-|-|
       |**Répertoires Include** | **$(VCInstallDir)UnitTest\include;$(IncludePath)**|
       |**Répertoires de bibliothèques** | **$(VCInstallDir)UnitTest\lib;$(LibraryPath)**|

2. Ajoutez un fichier de test unitaire C++ :

   - Dans **l’Explorateur de solutions**, dans le menu contextuel du projet, choisissez **Ajouter** > **Nouvel élément** > **Test unitaire C++**.

   Passez à [Écrire les tests unitaires](#addTests).

## <a name="write-the-unit-tests"></a><a name="addTests"></a> Écrire les tests unitaires

1. Dans chaque fichier de code de test unitaire, ajoutez une instruction `#include` pour les en-têtes du projet testé.

2. Ajoutez les classes et les méthodes de test aux fichiers de code de test unitaire. Par exemple :

    ```cpp
    #include "stdafx.h"
    #include "CppUnitTest.h"
    #include "MyProjectUnderTest.h"
    using namespace Microsoft::VisualStudio::CppUnitTestFramework;
    namespace MyTest
    {
      TEST_CLASS(MyTests)
      {
      public:
          TEST_METHOD(MyTestMethod)
          {
              Assert::AreEqual(MyProject::Multiply(2,3), 6);
          }
      };
    }
    ```

## <a name="run-the-tests"></a>Exécuter les tests

1. Dans le menu **Test**, choisissez **Fenêtres** > **Explorateur de tests**.

1. Si tous vos tests ne sont pas visibles dans la fenêtre, générez le projet de test en cliquant avec le bouton droit sur son nœud dans **l’Explorateur de solutions** et en choisissant **Générer** ou **Régénérer**.

1. Dans **Test Explorer**, choisissez Run **All**, ou sélectionnez les tests spécifiques que vous souhaitez exécuter. Cliquez avec le bouton droit sur un test pour accéder à d’autres options, notamment son exécution en mode débogage avec des points d’arrêt activés.

## <a name="see-also"></a>Voir aussi

- [Écrire des tests unitaires pour C/C++](writing-unit-tests-for-c-cpp.md)
- [Microsoft.VisualStudio.TestTools.CppUnitTestFramework API Référence](../test/microsoft-visualstudio-testtools-cppunittestframework-api-reference.md)
- [Déboguer du code natif](../debugger/debugging-native-code.md)
- [Procédure pas à pas : création et utilisation d’une bibliothèque de liens dynamiques (C++)](/cpp/build/walkthrough-creating-and-using-a-dynamic-link-library-cpp)
- [Importer et exporter](/cpp/build/importing-and-exporting)
- [Démarrage rapide : développement piloté par les tests avec l’Explorateur de tests](../test/quick-start-test-driven-development-with-test-explorer.md)
