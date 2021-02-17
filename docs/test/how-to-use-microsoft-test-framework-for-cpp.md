---
title: Utiliser le framework de tests unitaires Microsoft pour C++
description: Utilisez l’infrastructure de tests unitaires Microsoft pour C++ pour créer des tests unitaires pour votre code C++.
ms.date: 02/16/2021
ms.topic: how-to
ms.author: corob
manager: markl
ms.workload:
- cplusplus
author: corob-msft
ms.openlocfilehash: a76c6ac83956cd1e6514ff958278d0b4cbcf0d2f
ms.sourcegitcommit: cc8547eb211c43b67b8123d1211b80b5642e3b18
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/17/2021
ms.locfileid: "100563434"
---
# <a name="use-the-microsoft-unit-testing-framework-for-c-in-visual-studio"></a>Utiliser le framework de tests unitaires Microsoft pour C++ dans Visual Studio

Le framework de tests unitaires Microsoft pour C++ est par défaut dans la charge de travail **Développement Desktop en C++**.

## <a name="to-write-unit-tests-in-a-separate-project"></a><a name="separate_project"></a> Pour écrire des tests unitaires dans un projet distinct

En règle générale, vous exécutez votre code de test dans son propre projet, dans la même solution que le code que vous voulez tester. Pour installer et configurer un nouveau projet de test, consultez [Écriture de tests unitaires pour C/C++](writing-unit-tests-for-c-cpp.md).

## <a name="to-write-unit-tests-in-the-same-project"></a><a name="same_project"></a> Pour écrire des tests unitaires dans le même projet

Dans certains cas, par exemple lors du test de fonctions non exportées dans une DLL, il peut être nécessaire de créer les tests dans le même projet que le programme que vous testez. Pour écrire des tests unitaires dans le même projet :

1. Modifiez les propriétés du projet de façon à inclure les fichiers d’en-tête et les fichiers bibliothèques nécessaires aux tests unitaires.

   1. Dans Explorateur de solutions, dans le menu contextuel du projet que vous testez, choisissez **Propriétés**. La fenêtre des propriétés du projet s'ouvre.

   1. Dans la boîte de dialogue pages de propriétés, sélectionnez **Propriétés de configuration**  >  **Répertoires VC + +**.

   1. Sélectionnez la flèche vers le bas dans les lignes suivantes et choisissez **\<Edit>** . Ajoutez ces chemins :

      | Répertoire | Propriété |
      |-| - |
      | **Répertoires Include** | **$(VCInstallDir)Auxiliary\VS\UnitTest\include** |
      | **Répertoires de bibliothèques** | **$(VCInstallDir)Auxiliary\VS\UnitTest\lib** |

1. Ajoutez un fichier de test unitaire C++ :

   1. Cliquez avec le bouton droit sur le nœud du projet dans **Explorateur de solutions** et choisissez **Ajouter**  >  **un nouvel élément**.

   1. Dans la boîte de dialogue **Ajouter un nouvel élément** , sélectionnez  **fichier C++ (. cpp)**, donnez-lui un nom approprié, puis choisissez **Ajouter**.

## <a name="to-link-the-tests-to-the-object-or-library-files"></a><a name="object_files"></a> Pour lier les tests aux fichiers objets ou bibliothèques

Si le code testé n’exporte pas les fonctions que vous souhaitez tester, vous pouvez ajouter le fichier de sortie *. obj* ou *. lib* aux dépendances du projet de test. Modifiez les propriétés du projet de test pour inclure les en-têtes et les fichiers d’objets ou de bibliothèque requis pour le test unitaire.

1. Dans l’Explorateur de solutions, dans le menu contextuel du projet de test, choisissez **Propriétés**. La fenêtre des propriétés du projet s'ouvre.

1. Sélectionnez la page d’entrée de l’éditeur de liens **Propriétés de configuration**  >    >   , puis sélectionnez **dépendances supplémentaires**.

   Choisissez **Modifier**, puis ajoutez les noms des fichiers *.obj* ou *.lib*. N’utilisez pas les noms de chemins d’accès complets.

1. Sélectionnez la page **Propriétés de configuration**  >  **éditeur de liens**  >  **général** , puis sélectionnez **autres répertoires de bibliothèque**.

   Choisissez **Modifier**, puis ajoutez le chemin d’accès au répertoire des fichiers *.obj* ou *.lib*. Le chemin d’accès se trouve généralement dans le dossier de build du projet testé.

1. Sélectionnez la page **Propriétés de configuration** des  >  **Répertoires VC + +** , puis sélectionnez **répertoires Include**.

   Choisissez **Modifier**, puis ajoutez le répertoire d’en-tête du projet testé.

## <a name="write-the-tests"></a>Écrire les tests

Tout fichier *. cpp* avec les classes de test doit inclure « CppUnitTest. h » et avoir une instruction using pour `using namespace Microsoft::VisualStudio::CppUnitTestFramework` . Le projet de test est déjà configuré pour vous. Il contient également une définition d’espace de noms et une TEST_CLASS avec une TEST_METHOD pour vous aider à démarrer. Vous pouvez modifier le nom de l’espace de noms et les noms entre parenthèses dans les macros de la classe et de la méthode.

L’infrastructure de test définit des macros spéciales pour l’initialisation des modules, des classes et des méthodes de test, ainsi que pour le nettoyage des ressources une fois les tests terminés. Ces macros génèrent du code à exécuter avant la première consultation d’une classe ou d’une méthode, et après l’exécution du dernier test. Pour plus d’informations, consultez [Initialiser et nettoyer](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md#Initialize_and_cleanup).

Utilisez les méthodes statiques de la classe [Assert](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md#general_asserts) pour définir des conditions de test. Utilisez la classe [Logger](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md#logger) pour écrire des messages dans la **fenêtre Sortie**. Ajouter des attributs aux méthodes de test

## <a name="run-the-tests"></a>Exécuter les tests

1. Dans le menu **Test**, choisissez **Fenêtres** > **Explorateur de tests**.

1. Si tous vos tests ne sont pas visibles dans la fenêtre, générez le projet de test en cliquant avec le bouton droit sur son nœud dans **Explorateur de solutions** et en choisissant **générer** ou **régénérer**.

1. Dans l' **Explorateur de tests**, choisissez **exécuter tout** ou sélectionnez les tests spécifiques que vous souhaitez exécuter. Cliquez avec le bouton droit sur un test pour accéder à d’autres options, notamment son exécution en mode débogage avec des points d’arrêt activés.

1. Dans la **fenêtre Sortie** choisissez **tests** dans la liste déroulante pour afficher les messages écrits par la `Logger` classe :

   ![Fenêtre Sortie C++ affichant des messages de test](media/cpp-test-output-window.png)

## <a name="define-traits-to-enable-grouping"></a>Définir des caractéristiques pour permettre le regroupement

Vous pouvez définir des caractéristiques sur les méthodes de test, ce qui vous permet de catégoriser et de regrouper les tests dans l' **Explorateur de tests**. Pour définir une caractéristique, utilisez la macro `TEST_METHOD_ATTRIBUTE` . Par exemple, pour définir une caractéristique nommée `TEST_MY_TRAIT`:

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

Les caractéristiques prédéfinies suivantes sont disponibles dans *`CppUnitTest.h`* . Pour plus d’informations, consultez [la référence sur l’API de l’infrastructure de tests unitaires Microsoft pour C++](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md).

|Macro|Description|
|-|-----------------|
|`TEST_METHOD_ATTRIBUTE(attributeName, attributeValue)`|Utilisez la macro TEST_METHOD_ATTRIBUTE pour définir une caractéristique.|
|`TEST_OWNER(ownerAlias)`|Utilisez la caractéristique Owner prédéfinie pour spécifier un propriétaire de la méthode de test.|
|`TEST_PRIORITY(priority)`|Utilisez la caractéristique Priority prédéfinie pour assigner des priorités relatives à vos méthodes de test.|

## <a name="see-also"></a>Voir aussi

- [Démarrage rapide : développement piloté par les tests avec l’Explorateur de tests](../test/quick-start-test-driven-development-with-test-explorer.md)
