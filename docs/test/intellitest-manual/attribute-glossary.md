---
title: Glossaire des attributs | Outil de test Microsoft IntelliTest pour les développeurs
ms.date: 05/02/2017
ms.topic: reference
helpviewer_keywords:
- IntelliTest, Attribute glossary
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 00d8b24d26237a3c7b4130eba4614b5ea7b7eccd
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75594303"
---
# <a name="attribute-glossary"></a>Glossaire des attributs

## <a name="attributes-by-namespace"></a>Attributs par espace de noms

* **Microsoft.Pex.Framework**
  * [PexAssumeNotNull](#pexassumenotnull)
  * [PexClass](#pexclass)
  * [PexGenericArguments](#pexgenericarguments)
  * [PexMethod](#pexmethod)
    * [PexExplorationAttributeBase](#pexexplorationattributebase)

* **Microsoft.Pex.Framework.Settings**
  * [PexAssemblySettings](#pexassemblysettings)

* **Microsoft.Pex.Framework.Instrumentation**
  * [PexAssemblyUnderTest](#pexassemblyundertest)
  * [PexInstrumentAssembly](#pexinstrumentassemblyattribute)

* **Microsoft.Pex.Framework.Using**
  * [PexUseType](#pexusetype)

* **Microsoft.Pex.Framework.Validation**
  * [PexAllowedException](#pexallowedexception)
  * [PexAllowedExceptionFromAssembly](#pexallowedexceptionfromassembly)
  * [PexAllowedExceptionFromType](#pexallowedexceptionfromtype)
  * [PexAllowedExceptionFromTypeUnderTest](#pexallowedexceptionfromtypeundertest)

<a name="pexassumenotnull"></a>
## <a name="pexassumenotnull"></a>PexAssumeNotNull

Cet attribut indique que la valeur gérée ne peut pas être **null**. Il peut être associé à :

* un **paramètre** d’une méthode de test paramétrable

  ```csharp
  // assume foo is not null
  [PexMethod]
  public void SomeTest([PexAssumeNotNull]IFoo foo, ...) {}
  ```

* un **champ**

  ```csharp
  public class Foo {
     // this field should not be null
     [PexAssumeNotNull]
     public object Bar;
  }
  ```

* un **type**

  ```csharp
  // never consider null for Foo types
  [PexAssumeNotNull]
  public class Foo {}
  ```

Il peut également être associé à un assembly de test, un élément ou une méthode de test ; dans ce cas, les premiers arguments doivent indiquer le champ ou le type auquel les hypothèses s’appliquent. Quand l’attribut s’applique à un type, il s’applique à tous les champs avec ce type formel.

<a name="pexclass"></a>
## <a name="pexclass"></a>PexClass

Cet attribut marque une classe qui contient des *explorations*. Il est l’équivalent de l’attribut MSTest **TestClassAttribute** (ou NUnit **TestFixtureAttribute**). Cet attribut est facultatif.

Les classes marquées avec [PexClass](#pexclass) doivent être *constructibles par défaut* :

* type exporté publiquement
* constructeur par défaut
* non abstraite

Si la classe ne répond pas à ces exigences, une erreur est signalée et l’exploration échoue.

Il est également vivement conseillé que ces classes soient **partielles** pour qu’IntelliTest puisse générer de nouveaux tests qui font partie de la classe, mais dans un fichier distinct. Cette approche résout de nombreux problèmes de [visibilité](input-generation.md#visibility) et est une technique classique en C#.

**Suite et catégories supplémentaires** :

```csharp
[TestClass] // MSTest test fixture attribute
[PexClass(Suite = "checkin")] // fixture attribute
public partial class MyTests { ... }
```

**Spécification du type de test** :

```csharp
[PexClass(typeof(Foo))] // this is a test for Foo
public partial class FooTest { ... }
```

La classe peut contenir des méthodes annotées avec [PexMethod](#pexmethod). IntelliTest comprend également les [méthodes d’installation et de suppression](test-generation.md#setup-teardown).

<a name="pexgenericarguments"></a>
## <a name="pexgenericarguments"></a>PexGenericArguments

Cet attribut fournit un type tuple pour l’instanciation d’un [test unitaire paramétrable générique](test-generation.md#generic-parameterized).

<a name="pexmethod"></a>
## <a name="pexmethod"></a>PexMethod

Cet attribut marque une méthode comme [test unitaire paramétrable](test-generation.md#parameterized-unit-testing).
La méthode doit résider dans une classe marquée avec l’attribut [PexClass](#pexclass).

IntelliTest génère des tests sans paramètre classiques qui appellent le [test unitaire paramétrable](test-generation.md#parameterized-unit-testing) avec différents paramètres.

Le test unitaire paramétrable :

* doit être une méthode d’instance
* doit être [visible](input-generation.md#visibility) pour la classe de test dans laquelle les tests générés sont placés en fonction de la [cascade des paramètres](settings-waterfall.md)
* peut accepter un nombre quelconque de paramètres
* peut être générique

**Exemple**

```csharp
[PexClass]
public partial class MyTests {
     [PexMethod]
     public void MyTest(int i)
     { ... }
}
```

<a name="pexexplorationattributebase"></a>
## <a name="pexexplorationattributebase"></a>PexExplorationAttributeBase

[Complément d’information](xref:Microsoft.Pex.Framework.PexExplorationAttributeBase)

<a name="pexassemblysettings"></a>
## <a name="pexassemblysettings"></a>PexAssemblySettings

Cet attribut peut être défini au niveau de l’assembly pour remplacer les valeurs de paramètre par défaut pour toutes les explorations.

```csharp
using Microsoft.Pex.Framework;
// overriding the test framework selection
[assembly: PexAssemblySettings(TestFramework = "MSTestv2")]
```

<a name="pexassemblyundertest"></a>
## <a name="pexassemblyundertest"></a>PexAssemblyUnderTest

Cet attribut spécifie un assembly qui est testé par le projet de test actuel.

```csharp
[assembly: PexAssemblyUnderTest("MyAssembly")]
```

<a name="pexinstrumentassemblyattribute"></a>
## <a name="pexinstrumentassemblyattribute"></a>PexInstrumentAssemblyAttribute

Cet attribut est utilisé pour spécifier un assembly à instrumenter.

**Exemple**

```csharp
using Microsoft.Pex.Framework;

// the assembly containing ATypeFromTheAssemblyToInstrument should be instrumented
[assembly: PexInstrumentAssembly(typeof(ATypeFromTheAssemblyToInstrument))]

// the assembly name can be used as well
[assembly: PexInstrumentAssembly("MyAssemblyName")]
```

<a name="pexusetype"></a>
## <a name="pexusetype"></a>PexUseType

Cet attribut indique à IntelliTest qu’il peut utiliser un type particulier pour instancier des interfaces ou des types de base (abstrait).

**Exemple**

```csharp
[PexMethod]
[PexUseType(typeof(A))]
[PexUseType(typeof(B))]
public void MyTest(object testParameter)
{
     ... // IntelliTest will consider types A and B to instantiate 'testParameter'
}
```

<a name="pexallowedexception"></a>
## <a name="pexallowedexception"></a>PexAllowedException

Si cet attribut est associé à [PexMethod](#pexmethod) (ou à [PexClass](#pexclass)), il modifie la logique IntelliTest par défaut qui indique quand les tests échouent. Le test ne sera pas considéré comme ayant échoué, même s’il lève l’exception spécifiée.

**Exemple**

Le test suivant spécifie que le constructeur de **Stack** peut lever une **ArgumentOutOfRangeException** :

```csharp
class Stack {
  int[] _elements;
  int _count;
  public Stack(int capacity) {
    if (capacity<0) throw new ArgumentOutOfRangeException();
    _elements = new int[capacity];
    _count = 0;
  }
  ...
}
```

Le filtre est attaché à un élément comme suit (il peut également être défini au niveau de l’assembly ou du test) :

```csharp
[PexMethod]
[PexAllowedException(typeof(ArgumentOutOfRangeException))]
class CtorTest(int capacity) {
  Stack s = new Stack(capacity); // may throw ArgumentOutOfRangeException
}
```

<a name="pexallowedexceptionfromassembly"></a>
## <a name="pexallowedexceptionfromassembly"></a>PexAllowedExceptionFromAssembly

[Complément d’information](xref:Microsoft.Pex.Framework.Validation.PexAllowedExceptionFromAssemblyAttribute)

<a name="pexallowedexceptionfromtype"></a>
## <a name="pexallowedexceptionfromtype"></a>PexAllowedExceptionFromType

[Complément d’information](xref:Microsoft.Pex.Framework.Validation.PexAllowedExceptionFromTypeAttribute)

<a name="pexallowedexceptionfromtypeundertest"></a>
## <a name="pexallowedexceptionfromtypeundertest"></a>PexAllowedExceptionFromTypeUnderTest

[Complément d’information](xref:Microsoft.Pex.Framework.Validation.PexAllowedExceptionFromTypeUnderTestAttribute)

## <a name="got-feedback"></a>Vous avez des commentaires ?

Postez vos idées et demandes de fonctionnalités sur la [Communauté des développeurs](https://developercommunity.visualstudio.com/content/idea/post.html?space=8).
