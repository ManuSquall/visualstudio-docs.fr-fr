---
title: Génération de tests | Outil de test Microsoft IntelliTest pour les développeurs | Microsoft Docs
ms.date: 05/02/2017
ms.technology: vs-ide-test
ms.topic: article
helpviewer_keywords:
- IntelliTest, Test generation
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 8cb42b33907b528ee2c4cdd6a85ce5c361111772
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2018
---
# <a name="test-generation"></a>Génération de tests

Dans les tests unitaires traditionnels, plusieurs ingrédients sont nécessaires pour établir un test :

```
[Test]
void MyTest() {
    // data
    ArrayList a = new ArrayList();

    // method sequence
    a.Add(5);

    // assertions
    Assert.IsTrue(a.Count==1);
    Assert.AreEqual(a[0], 5);
}
```

Le test se compose de différents aspects :

* Il établit une [séquence d’appels de méthode](test-generation.md#test-generators).
* Il établit les arguments avec lesquels les méthodes sont appelées ; les arguments sont les [entrées du test](input-generation.md).
* Il vérifie le comportement prévu de l’application testée en établissant un ensemble d’[assertions](#assumptions-and-assertions).

IntelliTest peut souvent déterminer automatiquement les valeurs appropriées des arguments pour des [tests unitaires paramétrables](#parameterized-unit-testing) plus généraux, qui fournissent la séquence des appels de méthode et des assertions.

<a name="test-generators"></a>
## <a name="test-generators"></a>Générateurs de tests

IntelliTest génère des cas de test en sélectionnant une séquence de méthodes de l’implémentation testée à exécuter, puis en générant les entrées pour les méthodes en vérifiant les assertions sur les données dérivées.

Un [test unitaire paramétrable](#parameterized-unit-testing) déclare directement une séquence d’appels de méthode dans son corps.

Quand IntelliTest doit construire des objets, des appels aux constructeurs et aux méthodes de fabrique sont ajoutés automatiquement à la séquence en fonction des besoins.

<a name="parameterized-unit-testing"></a>
## <a name="parameterized-unit-testing"></a>Tests unitaires paramétrables

Les *tests unitaires paramétrables* sont des tests qui prennent des paramètres. Contrairement aux tests unitaires traditionnels, qui sont généralement des méthodes fermées, les tests unitaires paramétrables prennent n’importe quel ensemble de paramètres. C’est aussi simple que ça ? Oui. À partir de là, IntelliTest va essayer de [générer l’ensemble (minimal) des entrées](input-generation.md) qui [couvrent entièrement](input-generation.md#dynamic-code-coverage) le code accessible à partir du test.

Les tests unitaires paramétrables sont définis à l’aide de l’attribut personnalisé [PexMethod](attribute-glossary.md#pexmethod), d’une façon similaire à MSTest (ou NUnit ou xUnit). Les tests unitaires paramétrables sont regroupés logiquement dans des classes marquées avec [PexClass](attribute-glossary.md#pexclass). L’exemple suivant montre un test unitaire paramétrable simple stocké dans la classe **MyPexTest** :

```
[PexMethod]
void ReplaceFirstChar(string target, char c) {

    string result = StringHelper.ReplaceFirstChar(target, c);

    Assert.AreEqual(result[0], c);
}
```

où **ReplaceFirstChar** est une méthode qui remplace le premier caractère d’une chaîne :

```
class StringHelper {
    static string ReplaceFirstChar(string target, char c) {
        if (target == null) throw new ArgumentNullException();
        if (target.Length == 0) throw new ArgumentOutOfRangeException();
        return c + target.Substring(1);
    }
}
```

À partir de ce test, IntelliTest peut automatiquement [générer des entrées](input-generation.md) pour un test unitaire paramétrable qui couvre de nombreux chemins d’exécution du code testé. Chaque entrée couvrant un chemin d’exécution différent est « sérialisé » sous forme de test unitaire :

```
[TestMethod, ExpectedException(typeof(ArgumentNullException))]
void ReplaceFirstChar0() {
    this.ReplaceFirstChar(null, 0);
}
...
[TestMethod]
void ReplaceFirstChar10() {
    this.ReplaceFirstChar("a", 'c');
}
```

<a name="generic-parameterized"></a>
## <a name="generic-parameterized-unit-testing"></a>Tests unitaires paramétrables génériques

Les tests unitaires paramétrables peuvent être des méthodes génériques. Dans ce cas, l’utilisateur doit spécifier les types utilisés pour instancier la méthode en utilisant [PexGenericArguments](attribute-glossary.md#pexgenericarguments).

```
[PexClass]
public partial class ListTest {
    [PexMethod]
    [PexGenericArguments(typeof(int))]
    [PexGenericArguments(typeof(object))]
    public void AddItem<T>(List<T> list, T value)
    { ... }
}
```

<a name="allowing-exceptions"></a>
## <a name="allowing-exceptions"></a>Autorisation des exceptions

IntelliTest fournit de nombreux attributs de validation pour aider au triage des exceptions en exceptions attendues et en exceptions inattendues.

Les exceptions attendues génèrent des cas de test négatifs avec l’annotation appropriée, par exemple **ExpectedException(typeof(*xxx*))**, alors que les exceptions inattendues génèrent des cas de test non réussis.

```
[PexMethod, PexAllowedException(typeof(ArgumentNullException))]
void SomeTest() {...}
```

Les validateurs sont :

* [PexAllowedException](attribute-glossary.md#pexallowedexception) : autorise un type d’exception particulier de n’importe quelle provenance
* [PexAllowedExceptionFromAssembly](attribute-glossary.md#pexallowedexceptionfromassembly) : autorise un type d’exception particulier provenant d’un assembly spécifique
* [PexAllowedExceptionFromType](attribute-glossary.md#pexallowedexceptionfromtype) : autorise un type d’exception particulier provenant d’un type spécifique
* [PexAllowedExceptionFromTypeUnderTest](attribute-glossary.md#pexallowedexceptionfromtypeundertest) : autorise un type d’exception particulier provenant d’un type testé

<a name="internal-types"></a>
## <a name="testing-internal-types"></a>Test de types internes

IntelliTest peut « tester » des types internes dès lors qu’il peut les voir. Pour qu’IntelliTest voie les types, l’attribut suivant est ajouté à votre produit ou votre projet de test par les Assistants IntelliTest de Visual Studio :

```
[assembly: InternalsVisibleTo("Microsoft.Pex, PublicKey=002400000480000094000000060200000024000052534131000400000100010007d1fa57c4aed9f0a32e84aa0faefd0de9e8fd6aec8f87fb03766c834c99921eb23be79ad9d5dcc1dd9ad236132102900b723cf980957fc4e177108fc607774f29e8320e92ea05ece4e821c0a5efe8f1645c4c0c93c1ab99285d622caa652c1dfad63d745d6f2de5f17e5eaf0fc4963d261c8a12436518206dc093344d5ad293
```

<a name="assumptions-and-assertions"></a>
## <a name="assumptions-and-assertions"></a>Hypothèses et assertions

Les utilisateurs peuvent utiliser des hypothèses et des assertions pour exprimer des [conditions préalables](#precondition) (hypothèses) et des [post-conditions](#postcondition) (assertions) sur leurs tests. Quand IntelliTest génère un ensemble de valeurs de paramètre et « explore » le code, il peut ne pas respecter une hypothèse du test. Quand cela se produit, il ne génère pas de test pour ce chemin mais l’ignore sans rien indiquer.

Les assertions sont un concept bien connu dans les frameworks de tests unitaires standard : IntelliTest « comprend » donc déjà les classes **Assert** prédéfinies fournies par chaque framework de test pris en charge. Cependant, la plupart des frameworks ne fournissent pas de classe **Assume**. Dans ce cas, IntelliTest fournit la classe [PexAssume](static-helper-classes.md#pexassume). Si vous ne voulez pas utiliser un framework de tests, IntelliTest a également la classe [PexAssert](static-helper-classes.md#pexassert).

```
[PexMethod]
public void Test1(object o) {
    // precondition: o should not be null
    PexAssume.IsNotNull(o);

    ...
}
```

En particulier, l’hypothèse de non-égalité à Null peut être encodée comme attribut personnalisé :

```
[PexMethod]
public void Test2([PexAssumeNotNull] object o)
// precondition: o should not be null
{
   ...
}
```

<a name="precondition"></a>
## <a name="precondition"></a>Condition préalable

Une condition préalable d’une méthode exprime les conditions sous lesquelles la méthode réussit.

En règle générale, la condition préalable est appliquée en vérifiant les paramètres et l’état de l’objet, et en levant une **ArgumentException** ou une **InvalidOperationException** si elle n’est pas respectée.

Dans IntelliTest, une condition préalable d’un [test unitaire paramétrable](#parameterized-unit-testing) est exprimée avec [PexAssume](static-helper-classes.md#pexassume).

<a name="postcondition"></a>
## <a name="postcondition"></a>Post-condition

Une post-condition d’une méthode exprime les conditions qui doivent être satisfaites pendant et après l’exécution de la méthode, en supposant que ses conditions préalables étaient initialement valides.

En règle générale, la post-condition est appliquée par des appels à des méthodes **Assert**.

Avec IntelliTest, une post-condition d’un [test unitaire paramétrable](#parameterized-unit-testing) est exprimée avec [PexAssert](static-helper-classes.md#pexassert).

<a name="test-failures"></a>
## <a name="test-failures"></a>Échecs des tests
Quand un cas de test généré échoue-t-il ?

1. S’il ne se termine pas dans les [limites configurées pour le chemin ](exploration-bounds.md), il est considéré comme ayant échoué, sauf si l’option [TestExcludePathBoundsExceeded](exploration-bounds.md#testexcludepathboundsexceeded) est définie.

1. Si le test lève une **PexAssumeFailedException**, il réussit. Cependant, il est généralement éliminé, sauf si [TestEmissionFilter](exploration-bounds.md#testemissionfilter) est défini sur **All**.

1. Si le test ne respecte pas une [assertion](#assumptions-and-assertions), par exemple en levant une exception de violation d’assertion d’un framework de tests unitaires, il échoue.

Si aucune des situations ci-dessus ne génère une décision, un test réussit si et seulement si il ne lève pas d’exception. Les violations d’assertion sont traitées de la même façon que les exceptions.

<a name="setup-teardown"></a>
## <a name="setup-and-tear-down"></a>Installation et destruction

Dans le cadre de l’intégration à des frameworks de tests, IntelliTest prend en charge la détection et l’exécution de méthodes d’installation et destruction.

**Exemple**

```
using Microsoft.Pex.Framework;
using NUnit.Framework;

namespace MyTests
{
    [PexClass]
    [TestFixture]
    public partial class MyTestClass
    {
        [SetUp]
        public void Init()
        {
            // monitored
        }

        [PexMethod]
        public void MyTest(int i)
        {
        }

        [TearDown]
        public void Dispose()
        {
            // monitored
        }
    }
}

```

<a name="further-reading"></a>
## <a name="further-reading"></a>Informations supplémentaires

* [Test to code binding](https://blogs.msdn.microsoft.com/visualstudioalm/2015/04/18/smart-unit-tests-test-to-code-binding-test-case-management/)
* [One test to rule them all](https://blogs.msdn.microsoft.com/visualstudioalm/2015/07/05/intellitest-one-test-to-rule-them-all/)

## <a name="got-feedback"></a>Vous avez des commentaires ?

Postez vos idées et demandes de fonctionnalités sur **[UserVoice](https://visualstudio.uservoice.com/forums/121579-visual-studio-2015/category/157869-test-tools?query=IntelliTest)**.
