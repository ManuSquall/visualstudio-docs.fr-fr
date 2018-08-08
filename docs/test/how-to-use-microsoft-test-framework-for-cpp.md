---
title: Utiliser le framework de tests unitaires Microsoft pour C++ dans Visual Studio
ms.date: 11/15/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: mblome
manager: douge
ms.workload:
- cplusplus
author: mikeblome
ms.openlocfilehash: 6087b864ba497d3754adfa01dc0168da5317aa5e
ms.sourcegitcommit: 495bba1d8029646653f99ad20df2f80faad8d58b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/31/2018
ms.locfileid: "39379551"
---
# <a name="use-the-microsoft-unit-testing-framework-for-c-in-visual-studio"></a>Utiliser le framework de tests unitaires Microsoft pour C++ dans Visual Studio

Le framework de tests unitaires Microsoft pour C++ est par défaut dans la charge de travail **Développement Desktop en C++**.

##  <a name="separate_project"></a> Pour écrire des tests unitaires dans un projet distinct

En règle générale, vous exécutez votre code de test dans son propre projet, dans la même solution que le code que vous voulez tester. Pour installer et configurer un nouveau projet de test, consultez [Écriture de tests unitaires pour C/C++](writing-unit-tests-for-c-cpp.md).

##  <a name="same_project"></a> Pour écrire des tests unitaires dans le même projet

Dans certains cas, par exemple lors du test de fonctions non exportées dans une DLL, il peut être nécessaire de créer les tests dans le même projet que le programme que vous testez. Pour écrire des tests unitaires dans le même projet :

1.  Modifiez les propriétés du projet de façon à inclure les fichiers d’en-tête et les fichiers bibliothèques nécessaires aux tests unitaires.

    1.  Dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur le nœud du projet du programme que vous testez, puis choisissez **Propriétés** > **Propriétés de configuration** > **Répertoires VC++**.

    3.  Cliquez sur la flèche vers le bas dans les lignes suivantes et choisissez **<Edit>** :

        |Répertoire|Property|
        |-|-|
        |**Répertoires Include**|**$(VCInstallDir)UnitTest\include;$(IncludePath)**|
        |**Répertoires de bibliothèques**|**$(VCInstallDir)UnitTest\lib;$(LibraryPath)**|

2.  Ajoutez un fichier de test unitaire C++ :

    -   Cliquez avec le bouton droit sur le nœud du projet dans **l’Explorateur de solutions**, puis choisissez **Ajouter** > **Nouvel élément** > **Test unitaire C++**.

## <a name="write-the-tests"></a>Écrire les tests

Tout fichier *.cpp* contenant des classes de test doit inclure « CppUnitTest.h » et avoir une instruction using pour `using namespace Microsoft::VisualStudio::CppUnitTestFramework`. Le projet de test est déjà configuré pour vous. Il contient également une définition d’espace de noms et une TEST_CLASS avec une TEST_METHOD pour vous aider à démarrer. Vous pouvez modifier le nom de l’espace de noms, ainsi que les noms entre parenthèses dans les macros de la classe et de la méthode.

Des macros spéciales sont définies pour l’initialisation des modules, des classes et des méthodes de test, et pour le nettoyage des ressources une fois les tests terminés. Ces macros génèrent du code qui est exécuté avant le premier accès à une classe ou à une méthode, et une fois que le dernier test a été exécuté. Pour plus d’informations, consultez [Initialiser et nettoyer](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md#Initialize_and_cleanup).

Utilisez les méthodes statiques de la classe [Assert](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md#general_asserts) pour définir des conditions de test. Utilisez la classe [Logger](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md#logger) pour écrire des messages dans la **fenêtre Sortie**. Ajouter des attributs aux méthodes de test

## <a name="run-the-tests"></a>Exécuter les tests

1.  Dans le menu **Test**, choisissez **Fenêtres** > **Explorateur de tests**.
2. Si vos tests n’apparaissent pas tous dans la fenêtre, générez le projet de test en cliquant avec le bouton droit sur son nœud dans **l’Explorateur de solutions** et en choisissant **Générer** ou **Régénérer**.

2.  Dans **l’Explorateur de tests**, choisissez **Exécuter tout** ou sélectionnez les tests spécifiques à exécuter. Cliquez avec le bouton droit sur un test pour accéder à d’autres options, notamment son exécution en mode débogage avec des points d’arrêt activés.
3. Dans la **fenêtre Sortie**, choisissez **Tests** dans la liste déroulante pour afficher les messages écrits par la classe `Logger` :

  ![Fenêtre Sortie C++ affichant des messages de test](media/cpp-test-output-window.png)

## <a name="define-traits-to-enable-grouping"></a>Définir des caractéristiques pour permettre le regroupement

Vous pouvez définir des caractéristiques sur des méthodes de test, qui vous permettent de catégoriser et de regrouper les tests dans **l’Explorateur de tests**. Pour définir une caractéristique, utilisez la macro `TEST_METHOD_ATTRIBUTE` . Par exemple, pour définir une caractéristique nommée `TEST_MY_TRAIT`:

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

Les caractéristiques prédéfinies suivantes se trouvent dans `CppUnitTest.h`. Pour plus d’informations, consultez [Informations de référence sur l’API du framework de tests unitaires Microsoft pour C++](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md).

|Macro|Description|
|-----------|-----------------|
|`TEST_METHOD_ATTRIBUTE(attributeName, attributeValue)`|Utilisez la macro TEST_METHOD_ATTRIBUTE pour définir une caractéristique.|
|`TEST_OWNER(ownerAlias)`|Utilisez la caractéristique Owner prédéfinie pour spécifier un propriétaire de la méthode de test.|
|`TEST_PRIORITY(priority)`|Utilisez la caractéristique Priority prédéfinie pour assigner des priorités relatives à vos méthodes de test.|

## <a name="see-also"></a>Voir aussi

- [Démarrage rapide : développement piloté par les tests avec l’Explorateur de tests](../test/quick-start-test-driven-development-with-test-explorer.md)

