---
title: Utiliser le framework de tests unitaires Microsoft pour C++
description: Utilisez le cadre de test unitaire Microsoft pour créer des tests unitaires pour votre code CMD.
ms.date: 01/08/2020
ms.topic: conceptual
ms.author: corob
manager: markl
ms.workload:
- cplusplus
author: corob-msft
ms.openlocfilehash: 5c8cb794ce7891e74610f1a73164ce403d294925
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75755568"
---
# <a name="use-the-microsoft-unit-testing-framework-for-c-in-visual-studio"></a>Utiliser le framework de tests unitaires Microsoft pour C++ dans Visual Studio

Le framework de tests unitaires Microsoft pour C++ est par défaut dans la charge de travail **Développement Desktop en C++**.

## <a name="to-write-unit-tests-in-a-separate-project"></a><a name="separate_project"></a> Pour écrire des tests unitaires dans un projet distinct

En règle générale, vous exécutez votre code de test dans son propre projet, dans la même solution que le code que vous voulez tester. Pour installer et configurer un nouveau projet de test, consultez [Écriture de tests unitaires pour C/C++](writing-unit-tests-for-c-cpp.md).

## <a name="to-write-unit-tests-in-the-same-project"></a><a name="same_project"></a>Pour écrire des tests unitaires dans le même projet

Dans certains cas, par exemple lors du test de fonctions non exportées dans une DLL, il peut être nécessaire de créer les tests dans le même projet que le programme que vous testez. Pour écrire des tests unitaires dans le même projet :

1. Modifiez les propriétés du projet de façon à inclure les fichiers d’en-tête et les fichiers bibliothèques nécessaires aux tests unitaires.

   1. Dans Solution Explorer, sur le menu raccourci du projet que vous testez, choisissez **Properties**. La fenêtre des propriétés du projet s'ouvre.

   1. Dans le dialogue sur les pages de propriété, sélectionnez **Configuration Properties** > **VCMD Directories**.

   1. Cliquez sur la flèche vers le ** \< **bas dans les rangées suivantes et choisissez Edit>. Ajoutez ces chemins :

      | Répertoire | Propriété |
      |-| - |
      | **Répertoires Include** | **$(VCInstallDir)Auxiliary\VS\UnitTest\include** |
      | **Répertoires de bibliothèques** | **$(VCInstallDir)Auxiliary\VS\UnitTest\lib** |

1. Ajoutez un fichier de test unitaire C++ :

   - Cliquez avec le bouton droit sur le nœud du projet dans l’**Explorateur de solutions**, puis choisissez **Ajouter** > **Nouvel élément** > **Fichier C++ (.cpp)**.

## <a name="to-link-the-tests-to-the-object-or-library-files"></a><a name="object_files"></a> Pour lier les tests aux fichiers objets ou bibliothèques

Si le code testé n’exporte pas les fonctions que vous souhaitez tester, vous pouvez ajouter le fichier **.obj** ou **.lib** à la dépendance du projet de test. Modifier les propriétés du projet de test pour inclure les en-têtes et les fichiers de bibliothèque ou d’objet qui sont nécessaires pour les tests unitaires.

1. Dans l’Explorateur de solutions, dans le menu contextuel du projet de test, choisissez **Propriétés**. La fenêtre des propriétés du projet s'ouvre.

1. Sélectionnez la page > **d’entrée De Lien de** > **Input** **propriétés de configuration,** puis sélectionnez **des dépendances supplémentaires**.

   Choisissez **Modifier**, puis ajoutez les noms des fichiers **.obj** ou **.lib**. N’utilisez pas les noms complets du chemin.

1. Sélectionnez la page > **Générale** De > **Connexion**de **propriétés de configuration,** puis sélectionnez **des annuaires de bibliothèque supplémentaires.**

   Choisissez **Modifier**, puis ajoutez le chemin d’accès au répertoire des fichiers **.obj** ou **.lib**. Le chemin d’accès se trouve généralement dans le dossier de build du projet testé.

1. Sélectionnez la page **Configuration Properties** > **VCMD Directories,** puis **sélectionnez Inclure les annuaires**.

   Choisissez **Modifier**, puis ajoutez le répertoire d’en-tête du projet testé.

## <a name="write-the-tests"></a>Écrire les tests

Tout fichier *.cpp* avec des classes de test doit inclure "CppUnitTest.h" et avoir une instruction d’utilisation pour `using namespace Microsoft::VisualStudio::CppUnitTestFramework`. Le projet de test est déjà configuré pour vous. Il contient également une définition d’espace de noms et une TEST_CLASS avec une TEST_METHOD pour vous aider à démarrer. Vous pouvez modifier le nom de l’espace de nom et les noms entre parenthèses dans la classe et les macros de méthode.

Le cadre de test définit des macros spéciales pour l’initialisation des modules de test, des classes et des méthodes, et pour le nettoyage des ressources après la fin des tests. Ces macros génèrent du code à exécuter avant qu’une classe ou une méthode ne soit accessible pour la première fois, et après le dernier test. Pour plus d’informations, consultez [Initialiser et nettoyer](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md#Initialize_and_cleanup).

Utilisez les méthodes statiques de la classe [Assert](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md#general_asserts) pour définir des conditions de test. Utilisez la classe [Logger](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md#logger) pour écrire des messages dans la **fenêtre Sortie**. Ajouter des attributs aux méthodes de test

## <a name="run-the-tests"></a>Exécuter les tests

1. Dans le menu **Test**, choisissez **Fenêtres** > **Explorateur de tests**.

1. Si tous vos tests ne sont pas visibles dans la fenêtre, construisez le projet de test en cliquant à droite sur son nœud dans **Solution Explorer** et en choisissant **Build** or **Rebuild**.

1. Dans **Test Explorer**, choisissez Run **All**, ou sélectionnez les tests spécifiques que vous souhaitez exécuter. Cliquez avec le bouton droit sur un test pour accéder à d’autres options, notamment son exécution en mode débogage avec des points d’arrêt activés.

1. Dans la **fenêtre de sortie** choisir les **tests** dans `Logger` le drop-down pour afficher les messages écrits par la classe:

   ![Fenêtre Sortie C++ affichant des messages de test](media/cpp-test-output-window.png)

## <a name="define-traits-to-enable-grouping"></a>Définir des caractéristiques pour permettre le regroupement

Vous pouvez définir des traits sur les méthodes de test, qui vous permettent de classer et de classer les tests de groupe dans **Test Explorer**. Pour définir une caractéristique, utilisez la macro `TEST_METHOD_ATTRIBUTE` . Par exemple, pour définir une caractéristique nommée `TEST_MY_TRAIT`:

```cpp
#define TEST_MY_TRAIT(traitValue) TEST_METHOD_ATTRIBUTE(L"MyTrait", traitValue)
```

Pour utiliser la caractéristique définie dans vos tests unitaires :

```cpp
BEGIN_TEST_METHOD_ATTRIBUTE(Method1)
    TEST_OWNER(L"OwnerName")
    TEST_PRIORITY(1)
    TEST_MY_TRAIT(L"thisTraitValue")
END_TEST_METHOD_ATTRIBUTE()

TEST_METHOD(Method1)
{
    Logger::WriteMessage("In Method1");
    Assert::AreEqual(0, 0);
}
```

### <a name="c-trait-attribute-macros"></a>Macros d'attribut de fonctionnalités C++

Les caractéristiques prédéfinies suivantes se trouvent dans `CppUnitTest.h`. Pour plus d’informations, consultez [le cadre de test de l’unité Microsoft pour la référence API](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md).

|Macro|Description|
|-|-----------------|
|`TEST_METHOD_ATTRIBUTE(attributeName, attributeValue)`|Utilisez la macro TEST_METHOD_ATTRIBUTE pour définir une caractéristique.|
|`TEST_OWNER(ownerAlias)`|Utilisez la caractéristique Owner prédéfinie pour spécifier un propriétaire de la méthode de test.|
|`TEST_PRIORITY(priority)`|Utilisez la caractéristique Priority prédéfinie pour assigner des priorités relatives à vos méthodes de test.|

## <a name="see-also"></a>Voir aussi

- [Démarrage rapide : développement piloté par les tests avec l’Explorateur de tests](../test/quick-start-test-driven-development-with-test-explorer.md)
