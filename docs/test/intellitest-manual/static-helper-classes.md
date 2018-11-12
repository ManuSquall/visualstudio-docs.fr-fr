---
title: Classes d’assistance statiques | Outil de test Microsoft IntelliTest pour les développeurs
ms.date: 05/02/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: reference
helpviewer_keywords:
- IntelliTest, Static helper classes
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: a5c635c8fb3def61b8278b7b7c4b66aa196d82b8
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2018
ms.locfileid: "51000475"
---
# <a name="static-helper-classes"></a>Classes d’assistance statiques

IntelliTest fournit un ensemble de classes d’assistance statiques qui peuvent être utilisées lors de la création [des tests unitaires paramétrables](test-generation.md#parameterized-unit-testing) :

* [PexAssume](#pexassume) : utilisée pour définir des hypothèses sur les entrées ; elle est utile pour filtrer les entrées indésirables.
* [PexAssert](#pexassert) : une classe d’assertion simple à utiliser si votre framework de tests n’en fournit pas.
* [PexChoose](#pexchoose) : un flux d’entrées de test supplémentaires géré par IntelliTest.
* [PexObserve](#pexobserve) : consigne les valeurs concrètes et les valide éventuellement dans le code généré

Certaines classes vous permettent d’interagir avec le moteur de raisonnement d’IntelliTest à un bas niveau :

* [PexSymbolicValue](#pexsymbolicvalue) : utilitaires pour inspecter ou modifier des contraintes symboliques sur des variables.

<a name="pexassume"></a>
## <a name="pexassume"></a>PexAssume

Classe statique utilisée pour exprimer des hypothèses, comme des [conditions préalables](test-generation.md#precondition), dans des [tests unitaires paramétrables](test-generation.md#parameterized-unit-testing). Les méthodes de cette classe peuvent être utilisées pour filtrer les entrées de test indésirables.

Si la condition supposée n’est pas satisfaite pour certaines entrées de test, une **PexAssumeFailedException** est levée. Ceci a pour effet que le test est ignoré sans que ce soit mentionné.

**Exemple**

Le test paramétrable suivant ne prend pas en compte **j=0** :

```csharp
public void TestSomething(int i, int j) {
     PexAssume.AreNotEqual(j, 0);
     int k = i/j;
     ...
}
```

**Remarques**

Le code ci-dessus est équivaut presque à :

```csharp
     if (j==0)
          return;
```

sauf qu’un **PexAssume** en échec ne produit pas de cas de test. Dans le cas d’une instruction **if**, IntelliTest génère un cas de test distinct pour couvrir la branche **then** de l’instruction **if**.

**PexAssume** contient également des classes imbriquées spécialisées pour les hypothèses sur les chaînes, les tableaux et les collections.

<a name="pexassert"></a>
## <a name="pexassert"></a>PexAssert

Classe statique utilisée pour exprimer des assertions, comme des [post-conditions](test-generation.md#postcondition), dans des [tests unitaires paramétrables](test-generation.md#parameterized-unit-testing).

Si la condition déclarée n’est pas satisfaite pour une entrée de test, une **PexAssertFailedException** est levée, ce qui entraîne l’échec du test.

**Exemple**

Ce qui suit déclare que la valeur absolue d’un entier positive :

```csharp
public void TestSomething(int i) {
     int j = Maths.Abs(i);
     PexAssert.IsTrue(j >= 0);
     ...
}
```

<a name="pexchoose"></a>
## <a name="pexchoose"></a>PexChoose

Classe statique qui fournit des valeurs d’entrée auxiliaires à un test, qui peuvent être utilisées pour implémenter des [objets fictifs paramétrables](input-generation.md#parameterized-mocks).

La classe **PexChoose** ne permet pas de déterminer si un test réussit ou échoue pour des valeurs d’entrée particulières. **PexChoose** fournit simplement des valeurs d’entrée, qui s’appellent des *choix*. Il revient toujours à l’utilisateur de limiter les valeurs d’entrée et d’écrire des assertions pour définir quand un test réussit ou échoue.

**Modes de fonctionnement**

La classe **PexChoose** peut fonctionner dans deux modes :

* Quand IntelliTest effectue une analyse symbolique du test et du code testé pendant la [génération des entrées](input-generation.md), le sélecteur retourne des valeurs arbitraires et IntelliTest suit la façon dont chaque valeur est utilisée dans le test et le code testé. IntelliTest génère des valeurs appropriées pour déclencher les différents chemins d’exécution dans le test et le code testé.

* Le code généré pour des cas de test particuliers configure le fournisseur de choix d’une façon spécifique, de façon que la réexécution d’un tel cas de test fasse des choix spécifiques pour déclencher un chemin d’exécution spécifique.

**Utilisation**

* Appel simple **PexChoose.Value** pour générer une nouvelle valeur :

```csharp
public int Foo() {
    return PexChoose.Value<int>("foo");
}
```

<a name="pexobserve"></a>
## <a name="pexobserve"></a>PexObserve

Classe statique pour consigner des valeurs nommées.

Quand IntelliTest explore le code, **PexObserve** est utilisée pour enregistrer des valeurs calculées en utilisant leur représentation sous forme de chaîne mise en forme. Les valeurs sont associées à des noms uniques.

```csharp
PexObserve.Value<string>("result", result);
```

**Exemple**

```csharp
// product code
public static class MathEx {
     public static int Square(int value) { return value * value; }
}


// fixture
[TestClass]
public partial class MathExTests {
     [PexMethod]
     public int SquareTest(int a) {
        int result = MathEx.Square(a); 
        // storing result
        return result;
     }
}
```

<a name="pexsymbolicvalue"></a>
## <a name="pexsymbolicvalue"></a>PexSymbolicValue

Classe statique utilisée pour ignorer des contraintes sur les paramètres et pour afficher les informations symboliques associées aux valeurs.

**Utilisation**

Normalement, IntelliTest tente de couvrir tous les chemins d’exécution du code lors de l’exécution. Cependant, en particulier lors du calcul des conditions des hypothèses et des assertions, il ne doit pas explorer tous les cas possibles.

**Exemple**

Cet exemple montre l’implémentation de la méthode **PexAssume.Arrays.ElementsAreNotNull**. Dans la méthode, vous ignorez les contraintes sur la valeur de la longueur du tableau, afin d’éviter qu’IntelliTest tente de générer différentes tailles de tableau. Les contraintes sont ignorées seulement ici. Si le code testé se comporte différemment pour des longueurs de tableau différentes, IntelliTest ne peut pas générer des tableaux de tailles différentes à partir des contraintes du code testé.

```csharp
public static void AreElementsNotNull<T>(T[] value)
    where T : class
{
    PexAssume.NotNull(value);
    // the followings prevents the exploration of all array lengths
    int len = PexSymbolicValue.Ignore<int>(value.Length);

    // building up a boolean value as follows prevents exploration
    // of all combinations of non-null (instead, there are just two cases)
    bool anyNull = false;
    for (int i = 0; i < len; ++i)
        anyNull |= value[i] == null;

    // was any element null?
    if (anyNull)
        PexAssume.Fail("some element of array is a null reference");
}
```

## <a name="got-feedback"></a>Vous avez des commentaires ?

Postez vos idées et demandes de fonctionnalités sur la [Communauté des développeurs](https://developercommunity.visualstudio.com/content/idea/post.html?space=8).