---
title: Tests unitaires pour les méthodes génériques
description: Découvrez comment générer des tests unitaires pour les méthodes génériques en utilisant ces informations et des exemples de création de tests unitaires pour les méthodes génériques.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- generics, and unit tests
- unit tests, and generics
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 16d1348d74bb459a73dd4a5a4f8de21e367865c1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99962494"
---
# <a name="unit-tests-for-generic-methods"></a>Tests unitaires pour les méthodes génériques

Vous pouvez générer des tests unitaires pour les méthodes génériques exactement comme vous le feriez pour d’autres méthodes. Les sections suivantes fournissent des informations et des exemples de création de tests unitaires pour les méthodes génériques.

## <a name="type-arguments-and-type-constraints"></a>Arguments de type et contraintes de type

Quand Visual Studio génère un test unitaire pour une classe générique, comme `MyList<T>`, il génère deux méthodes : une méthode d'assistance générique et une méthode de test. Si `MyList<T>` a une ou plusieurs contraintes de type, l'argument de type doit satisfaire toutes les contraintes de type. Pour vérifier que le code générique testé fonctionne comme prévu pour toutes les entrées autorisées, la méthode de test appelle la méthode d'assistance générique avec toutes les contraintes que vous souhaitez tester.

## <a name="examples"></a>Exemples
Les exemples suivants illustrent des tests unitaires pour les génériques :

- [Modifier le code de test généré](#EditingGeneratedTestCode). Cet exemple a deux sections, Code de test généré et Code de test modifié. Il montre comment modifier le code de test brut généré à partir d'une méthode générique dans une méthode de test utile.

- [Utiliser une contrainte de type](#TypeConstraintNotSatisfied). Cet exemple montre un test unitaire pour une méthode générique qui utilise une contrainte de type. Dans cet exemple, la contrainte de type n'est pas satisfaite.

### <a name="example-1-editing-generated-test-code"></a><a name="EditingGeneratedTestCode"></a> Exemple 1 : Modification du code de test généré
Le code de test de cette section teste une méthode de code sous test nommée `SizeOfLinkedList()`. Cette méthode retourne un entier qui spécifie le nombre de nœuds dans la liste liée.

Le premier exemple de code, dans la section Code de test généré, affiche le code de test non modifié comme il a été généré par Visual Studio Enterprise. Le deuxième exemple, dans la section Code de test modifié, montre comment vous pourriez lui faire tester le fonctionnement de la méthode SizeOfLinkedList pour deux types de données différents, `int` et `char`.

Ce code illustre deux méthodes :

- une méthode d'assistance au test, `SizeOfLinkedListTestHelper<T>()`. Par défaut, une méthode d'assistance au test contient « TestHelper » dans son nom.

- une méthode de test, `SizeOfLinkedListTest()`. Chaque méthode de test est marquée avec l'attribut TestMethod.

#### <a name="generated-test-code"></a>Code de test généré
Le code de test suivant a été généré à partir de la méthode `SizeOfLinkedList()`. Comme il s'agit du test généré non modifié, il doit être modifié pour tester correctement la méthode SizeOfLinkedList.

```csharp
public void SizeOfLinkedListTestHelper<T>()
{
    T val = default(T); // TODO: Initialize to an appropriate value
    MyLinkedList<T> target = new MyLinkedList<T>(val); // TODO: Initialize to an appropriate value
    int expected = 0; // TODO: Initialize to an appropriate value
    int actual;
    actual = target.SizeOfLinkedList();
    Assert.AreEqual(expected, actual);
    Assert.Inconclusive("Verify the correctness of this test method.");
}

[TestMethod()]
public void SizeOfLinkedListTest()
{
   SizeOfLinkedListTestHelper<GenericParameterHelper>();
}
```

Dans le code précédent, le paramètre de type générique est `GenericParameterHelper`. Même si vous pouvez le modifier pour fournir des types de données spécifiques, comme indiqué dans l’exemple suivant, vous pouvez exécuter le test sans modifier cette instruction.

#### <a name="edited-test-code"></a>Code de test modifié
Dans le code suivant, la méthode de test et la méthode d'assistance au test ont été modifiées de manière à pouvoir tester la méthode de code sous test `SizeOfLinkedList()`.

##### <a name="test-helper-method"></a>Méthode d’assistance au test
La méthode d'assistance au test effectue les étapes suivantes qui correspondent aux lignes du code Étape 1 à Étape 5.

1. Créer une liste liée générique.

2. Ajouter quatre nœuds à la liste liée. Le type de données du contenu de ces nœuds est inconnu.

3. Assigner la taille attendue de la liste liée à la variable `expected`.

4. Calculer la taille réelle de la liste liée et l'assigner à la variable `actual`.

5. Comparer `actual` à `expected` dans une instruction Assert. Si la variable réelle n'est pas égale à celle attendue, le test échoue.

##### <a name="test-method"></a>Méthode de test
La méthode de test est compilée dans le code qui est appelé lorsque vous exécutez le test nommé SizeOfLinkedListTest. Elle effectue les étapes suivantes qui correspondent aux lignes du code Étape 6 à Étape 7.

1. Spécifiez `<int>` lorsque vous appelez la méthode d'assistance au test pour vérifier que le test fonctionne pour les variables `integer`.

2. Spécifiez `<char>` lorsque vous appelez la méthode d'assistance au test pour vérifier que le test fonctionne pour les variables `char`.

```csharp
public void SizeOfLinkedListTestHelper<T>()
{
    T val = default(T);
    MyLinkedList<T> target = new MyLinkedList<T>(val); // step 1
    for (int i = 0; i < 4; i++) // step 2
    {
        MyLinkedList<T> newNode = new MyLinkedList<T>(val);
        target.Append(newNode);
    }
    int expected = 5; // step 3
    int actual;
    actual = target.SizeOfLinkedList(); // step 4
    Assert.AreEqual(expected, actual); // step 5
}

[TestMethod()]
public void SizeOfLinkedListTest()
{
    SizeOfLinkedListTestHelper<int>();  // step 6
    SizeOfLinkedListTestHelper<char>(); // step 7
}
```

> [!NOTE]
> Chaque fois que le test SizeOfLinkedListTest est exécuté, sa méthode TestHelper est appelée deux fois. L'instruction Assert doit chaque fois prendre la valeur True pour que le test réussisse. Si le test échoue, il peut être difficile de savoir lequel de l'appel ayant spécifié `<int>` ou de l'appel ayant spécifié `<char>` a provoqué son échec. Pour trouver la réponse, vous pouvez examiner la pile des appels ou définir des points d'arrêt dans votre méthode de test, puis déboguer pendant l'exécution du test. Pour plus d’informations, consultez [Comment : effectuer un débogage lors de l’exécution d’un test dans une solution ASP.NET](/previous-versions/ms243172(v=vs.140)).

### <a name="example-2-using-a-type-constraint"></a><a name="TypeConstraintNotSatisfied"></a> Exemple 2 : Utilisation d’une contrainte de type
Cet exemple montre un test unitaire pour une méthode générique qui utilise une contrainte de type non satisfaite. La première section affiche le code du projet de code sous test. La contrainte de type est mise en surbrillance.

La deuxième section affiche le code du projet de test.

#### <a name="code-under-test-project"></a>Projet de code sous test

```csharp
using System;
using System.Linq;
using System.Collections.Generic;
using System.Text;

namespace ClassLibrary2
{
    public class Employee
    {
        public Employee(string s, int i)
        {
        }
    }

    public class GenericList<T> where T : Employee
    {
        private class Node
        {
            private T data;
            public T Data
            {
                get { return data; }
                set { data = value; }
            }
        }
    }
}
```

#### <a name="test-project"></a>Projet de test

Comme avec tous les tests unitaires récemment générés, vous devez ajouter des instructions Assert concluantes à ce test unitaire pour lui faire retourner des résultats utiles. Vous ne les ajoutez pas à la méthode marquée avec l'attribut TestMethod mais à la méthode « TestHelper », nommée pour ce test `DataTestHelper<T>()`.

Dans cet exemple, le paramètre de type générique `T` a la contrainte `where T : Employee`. Cette contrainte n'est pas satisfaite dans la méthode de test. Par conséquent, la méthode `DataTest()` contient une instruction Assert qui vous alerte sur la nécessité de fournir la contrainte de type qui a été placée sur `T`. Le message de cette instruction Assert se présente comme suit : `("No appropriate type parameter is found to satisfies the type constraint(s) of T. " + "Please call DataTestHelper<T>() with appropriate type parameters.");`

En d’autres termes, quand vous appelez la méthode `DataTestHelper<T>()` depuis la méthode de test `DataTest()`, vous devez passer un paramètre de type `Employee` ou une classe dérivée de `Employee`.

```csharp
using ClassLibrary2;
using Microsoft.VisualStudio.TestTools.UnitTesting;

namespace TestProject1
{
    [TestClass()]
    public class GenericList_NodeTest
    {

        public void DataTestHelper<T>()
            where T : Employee
        {
            GenericList_Shadow<T>.Node target = new GenericList_Shadow<T>.Node(); // TODO: Initialize to an appropriate value
            T expected = default(T); // TODO: Initialize to an appropriate value
            T actual;
            target.Data = expected;
            actual = target.Data;
            Assert.AreEqual(expected, actual);
            Assert.Inconclusive("Verify the correctness of this test method.");
        }

        [TestMethod()]
        public void DataTest()
        {
            Assert.Inconclusive("No appropriate type parameter is found to satisfies the type constraint(s) of T. " +
            "Please call DataTestHelper<T>() with appropriate type parameters.");
        }
    }
}
```

## <a name="see-also"></a>Voir aussi

- [Test unitaire de votre code](../test/unit-test-your-code.md)