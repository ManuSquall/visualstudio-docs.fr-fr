---
title: Actions rapides courantes
description: Les actions rapides les plus populaires pour C# et Visual Basic, notamment la correction de mots clés ou de symboles mal orthographiés, la résolution de conflits de fusion, la suppression des importations nécessaires, la génération de types, l’introduction de variables locales, etc.
ms.date: 03/28/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: d24b03bc79c32c32c570d26b7607d1ba36c1c1df
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99970905"
---
# <a name="common-quick-actions"></a>Actions rapides courantes

Les sections de cette rubrique répertorient certaines des **actions rapides** courantes qui s’appliquent à la fois au code C# et Visual Basic. Ces actions sont des *corrections du code* pour les diagnostics du compilateur ou pour les [analyseurs .NET Compiler Platform](../code-quality/roslyn-analyzers-overview.md) intégrés dans Visual Studio.

## <a name="actions-that-fix-errors"></a>Actions permettant de résoudre des erreurs

Les actions rapides de cette section corrigent les erreurs dans le code qui provoquent un échec de génération. Quand des actions rapides sont disponibles pour corriger une erreur sur une ligne de code, l’icône qui s’affiche dans la marge ou en dessous de la ligne ondulée rouge est une ampoule avec un « x » rouge dessus.

![Menu et icône d’erreur Actions rapide](media/error-light-bulb-with-code.png)

### <a name="correct-misspelled-symbol-or-keyword"></a>Symbole ou mot clé mal orthographié correct

Si par erreur vous orthographiez mal un type ou un mot clé dans Visual Studio, cette action rapide le corrige automatiquement pour vous. Ces éléments s’affichent dans le menu ampoule en tant que **« changer » en \<misspelled word> \<correct word>**«». Par exemple :

```csharp
// Before
private viod MyMethod()
{
}

// Change 'viod' to 'void'

// After
private void MyMethod()
{
}
```

```vb
' Before
Function MyFunction as Intger
End Function

' Change 'Intger' to 'Integer'

' After
Function MyFunction as Integer
End Function
```

| ID d'erreur | Langages applicables |
| - | - |
| CS0103, BC30002 | C# et Visual Basic |

### <a name="resolve-git-merge-conflict"></a>Résoudre un conflit de fusion Git

Ces actions rapides vous permettent de résoudre les conflits de fusion Git par une « modification » qui supprime les marqueurs et le code en conflit.

```csharp
// Before
private void MyMethod()
{
    if (false)
    {

    }
}

// Take changes from 'HEAD'

// After
private void MyMethod()
{
    if (true)
    {

    }
}
```

| ID d'erreur | Langages applicables | Version prise en charge |
| ------- | -------------------- | ---------------- |
| CS8300, BC37284 | C# et Visual Basic | Visual Studio 2017 version 15,3 et versions ultérieures |

## <a name="actions-that-remove-unnecessary-code"></a>Actions permettant de supprimer du code inutile

### <a name="remove-unnecessary-usingsimports"></a>Supprimer les Usings inutiles/les importations superflues

L’action rapide supprimer les instructions **using inutiles/Imports** supprime toutes les directives inutilisées et inutilisées `using` `Import` pour le fichier actuel. Quand vous sélectionnez cet élément, les importations d’espaces de noms inutilisées sont supprimées.

| Langages applicables | Version prise en charge |
| - | - |
| C# et Visual Basic | Visual Studio 2015 et versions ultérieures |

### <a name="remove-unnecessary-cast"></a>Supprimer le cast inutile

Si vous castez un type en un autre type qui ne nécessite pas de cast, l’élément d’Action rapide **Supprimer le cast inutile** supprime le cast inutile.

```csharp
// before
int number = (int)3;

// Remove Unnecessary Cast

// after
int number = 3;
```

```vb
' Before
Dim number as Integer = CType(3, Integer)

' Remove Unnecessary Cast

' After
Dim number as Integer = 3
```

| ID de diagnostic | Langages applicables | Version prise en charge |
| ------- | -------------------- | ---------------- |
| IDE0004 | C# et Visual Basic | Visual Studio 2015 et versions ultérieures |

### <a name="remove-unused-variables"></a>Supprimer les variables inutilisées

Cette action rapide vous permet de supprimer les variables qui ont été déclarées, mais jamais utilisées dans votre code.

```csharp
// Before
public MyMethod()
{
    var unused = 8;
    var used = 1;
    return DoStuff(used);
}

// Remove unused variables

// After
public MyMethod()
{
    var used = 1;
    return DoStuff(used);
}
```

| ID de diagnostic | Langages applicables | Version prise en charge |
| ------- | -------------------- | ---------------- |
| CS0219, BC42024 | C# et Visual Basic | Visual Studio 2017 version 15,3 et versions ultérieures |

### <a name="remove-type-from-default-value-expression"></a>Supprimer le type de l’expression de valeur par défaut

Cette action rapide permet de supprimer le type de valeur d’une expression de valeur par défaut et utilise le [littéral par défaut](/dotnet/csharp/language-reference/operators/default#default-literal) quand le compilateur peut déduire le type de l’expression.

```csharp
// Before
void DoWork(CancellationToken cancellationToken = default(CancellationToken)) { ... }

// Simplify default expression

// After
void DoWork(CancellationToken cancellationToken = default) { ... }
```

| ID de diagnostic | Langages applicables | Version prise en charge |
| ------- | -------------------- | ---------------- |
| IDE0034 | C# 7.1+ | Visual Studio 2017 version 15,3 et versions ultérieures |

## <a name="actions-that-add-missing-code"></a>Actions permettant d’ajouter du code manquant

### <a name="add-usingsimports-for-types-in-reference-assemblies-nuget-packages-or-other-types-in-your-solution"></a>Ajouter des instructions using/imports pour les types dans les assemblys de référence, les packages NuGet ou d’autres types de votre solution

L’utilisation de types situés dans d’autres projets de votre solution permet d’afficher automatiquement l’action rapide, mais vous devez activer les autres à partir de l’onglet **Outils > Options > C#** ou **De base > Avancé** :

- Suggérer des usings/imports pour les types dans les assemblys de référence
- Suggérer des usings/imports pour les types dans les packages NuGet

Quand cette option est activée, si vous utilisez un type dans un espace de noms qui n’est pas importé actuellement, mais qui existe dans un assembly de référence ou un package NuGet, la directive using ou Import est créée.

```csharp
// Before
Debug.WriteLine("Hello");

// using System.Diagnostics;

// After
using System.Diagnostics;

Debug.WriteLine("Hello");
```

```vb
' Before
Debug.WriteLine("Hello")

' Imports System.Diagnostics

' After
Imports System.Diagnostics

Debug.WriteLine("Hello")
```

| ID de diagnostic | Langages applicables |
| - | - |
| CS0103, BC30451 | C# et Visual Basic|

### <a name="add-missing-casesdefault-caseboth"></a>Ajouter les instructions case manquantes/une instruction case par défaut/les deux

Quand vous créez une instruction `switch` en C# ou une instruction `Select Case` en Visual Basic, vous pouvez utiliser une action de code pour ajouter automatiquement des éléments case manquants, une instruction case par défaut, ou les deux.

Considérons l’énumération et l’instruction `switch` ou `Select Case` vide suivantes :

```csharp
enum MyEnum
{
    Item1,
    Item2,
    Item3
}

...

MyEnum myEnum = MyEnum.Item1;

switch(myEnum)
{
}
```

```vb
Enum MyEnum
    Item1
    Item2
    Item3
End Enum

...

Dim myEnum as MyEnum = MyEnum.Item1

Select Case myEnum
End Select
```

Utilisez l’action rapide **Ajouter les deux** pour renseigner à la fois les instructions case manquantes et une instruction case par défaut :

```csharp
switch(myEnum)
{
    case MyEnum.Item1:
        break;
    case MyEnum.Item2:
        break;
    case MyEnum.Item3:
        break;
    default:
        break;
}
```

```vb
Select Case myEnum
    Case MyEnum.Item1
        Exit Select
    Case MyEnum.Item2
        Exit Select
    Case Else
        Exit Select
End Select
```

| ID de diagnostic | Langages applicables | Version prise en charge |
| ------- | -------------------- | ---------------- |
| IDE0010 | C# et Visual Basic| Visual Studio 2017 version 15,3 et versions ultérieures |

### <a name="add-null-checks-for-parameters"></a>Ajouter des contrôles de valeurs Null pour les paramètres

Cette action rapide vous permet d’ajouter un contrôle dans votre code pour déterminer si un paramètre est Null.

```csharp
// Before
class MyClass
{
    public string MyProperty { get; set; }

    public MyClass(string myProperty) // cursor inside myProperty
    {
        MyProperty = myProperty;
    }
}

// Add null check

// After
class MyClass
{
    public string MyProperty { get; set; }

    public MyClass(string myProperty)
    {
        MyProperty = myProperty ?? throw new ArgumentNullException(nameof(myProperty));
    }
}
```

| Langages applicables | Version prise en charge |
| -------------------- | ---------------- |
| C# et Visual Basic| Visual Studio 2017 version 15,3 et versions ultérieures |

### <a name="add-argument-name"></a>Ajouter le nom de l’argument

```csharp
// Before
var date = new DateTime(1997, 7, 8);

// Include argument name 'year' (include trailing arguments)

// After
var date = new DateTime(year: 1997, month: 7, day: 8);
```

| Langages applicables | Version prise en charge |
| -------------------- | ---------------- |
| C# et Visual Basic| Visual Studio 2017 version 15,3 et versions ultérieures |

### <a name="add-braces"></a>Ajouter des accolades

L’action rapide Ajouter des accolades place des accolades autour des instructions `if` sur une seule ligne.

```csharp
// Before
if (true)
    return "hello,world";

// Add braces

// After
if (true)
{
    return "hello,world";
}
```

| ID de diagnostic | Langages applicables | Version prise en charge |
| ------- | -------------------- | ---------------- |
| IDE0011 | C# | Visual Studio 2017 et versions ultérieures |

### <a name="add-and-order-modifiers"></a>Ajouter et trier des modificateurs

Ces actions rapides facilitent l’organisation des modificateurs en vous permettant de trier les modificateurs existants et d’ajouter des modificateurs d’accessibilité manquants.

```csharp
// Before
enum Color
{
    Red, White, Blue
}

// Add accessibility modifiers

// After
internal enum Color
{
    Red, White, Blue
}
```

```csharp
// Before
static private int thisFieldIsPublic;

// Order modifiers

// After
private static int thisFieldIsPublic;
```

| ID de diagnostic | Langages applicables | Version prise en charge |
| ------- | -------------------- | ---------------- |
| IDE0036 | C# et Visual Basic| Visual Studio 2017 versions 15.5 et ultérieures |
| IDE0040 | C# et Visual Basic| Visual Studio 2017 versions 15.5 et ultérieures |

## <a name="code-transformations"></a>Transformations de code

### <a name="convert-if-construct-to-switch"></a>Convertir une construction « if » en « switch »

Cette action rapide vous permet de convertir une construction **if-then-else** en construction **switch**.

```csharp
// Before
if (obj is string s)
{
  Console.WriteLine("obj is a string: " + s);
}

else if (obj is int i && i > 10)
{
  Console.WriteLine("obj is an int greater than 10");
}

// Convert to switch

// After
switch (obj)
{
  case string s:
    Console.WriteLine("Obj is a string: " + s);
    break;
  case int i when i > 10:
    Console.WriteLine("obj is an int greater than 10");
    break;
}
```

```vb
' Before
If TypeOf obj Is String s Then
    Console.WriteLine("obj is a string: " + s)
Else If TypeOf obj Is Integer i And i > 10 Then
    Console.WriteLine("obj is an int greater than 10")
End If

' Convert to switch

' After
Select Case obj
  Case String s
    Console.WriteLine("Obj is a string: " + s)
    Exit Sub
  Case Integer i when i > 10
    Console.WriteLine("obj is an int greater than 10")
    Exit Sub
End Select
```

| Langages applicables | Version prise en charge |
| -------------------- | ---------------- |
| C# et Visual Basic| Visual Studio 2017 version 15,3 et versions ultérieures |

### <a name="convert-to-interpolated-string"></a>Convertir en chaîne interpolée

Les [chaînes interpolées](/dotnet/csharp/language-reference/keywords/interpolated-strings) représentent un moyen simple d’exprimer des chaînes avec des variables incorporées, similaire à la méthode **[String.Format](/dotnet/api/system.string.format#overloads)**.  Cette action rapide reconnaît les chaînes concaténées ou l’utilisation de **String.Format** et met une chaîne interpolée à la place.

```csharp
// Before
int num = 3;
string s = string.Format("My string with {0} in the middle", num);

// Convert to interpolated string

// After
int num = 3;
string s = $"My string with {num} in the middle";
```

```vb
' Before
Dim num as Integer = 3
Dim s as String = String.Format("My string with {0} in the middle", num)

' Convert to interpolated string

' After
Dim num as Integer = 3
Dim s As String = $"My string with {num} in the middle"
```

| Langages applicables | Version prise en charge |
| -------------------- | ---------------- |
| C# 6.0+ et Visual Basic 14+ | Visual Studio 2017 et versions ultérieures |

### <a name="use-object-initializers"></a>Utiliser des initialiseurs d’objets

Cette Action rapide permet d’utiliser des [initialiseurs d’objets](/dotnet/csharp/programming-guide/classes-and-structs/object-and-collection-initializers) au lieu d’appeler le constructeur et d’avoir des lignes supplémentaires d’instructions d’assignation.

```csharp
// Before
var c = new Customer();
c.Age = 21;

// Object initialization can be simplified

// After
var c = new Customer() { Age = 21 };
```

```vb
' Before
Dim c = New Customer()
c.Age = 21

' Object initialization can be simplified

' After
Dim c = New Customer() With {.Age = 21}
```

| ID de diagnostic | Langages applicables | Version prise en charge |
| ------- | -------------------- | ---------------- |
| IDE0017 | C# et Visual Basic | Visual Studio 2017 et versions ultérieures |

### <a name="use-collection-initializers"></a>Utiliser des initialiseurs de collections

Cette action rapide vous permet d’utiliser des [initialiseurs de collection](/dotnet/csharp/programming-guide/classes-and-structs/object-and-collection-initializers) au lieu de plusieurs appels à la méthode `Add` de votre classe.

```csharp
// Before
var list = new List<int>();
list.Add(1);
list.Add(2);
list.Add(3);

// Collection initialization can be simplified

// After
var list = new List<int> { 1, 2, 3 };
```

```vb
' Before
Dim list = New List(Of Integer)
list.Add(1)
list.Add(2)
list.Add(3)

' Collection initialization can be simplified

' After
Dim list = New List(Of Integer) From {1, 2, 3}
```

| ID de diagnostic | Langages applicables | Version prise en charge |
| ------- | -------------------- | ---------------- |
| IDE0028 | C# et Visual Basic | Visual Studio 2017 et versions ultérieures |

### <a name="convert-auto-property-to-full-property"></a>Convertir une propriété automatique en propriété complète

Cette action rapide vous permet de convertir une propriété automatique en propriété complète, et vice versa.

```csharp
// Before
private int MyProperty { get; set; }

// Convert to full property

// After
private int MyProperty
{
    get { return _myProperty; }
    set { _myProperty = value; }
}
```

```vb
' Before
Public Property Name As String

' Convert to full property

' After
Private _Name As String

Public Property Name As String
    Get
        Return _Name
    End Get
    Set
        _Name = Value
    End Set
End Property
```

| Langages applicables | Version prise en charge |
| -------------------- | ---------------- |
| C# et Visual Basic | Visual Studio 2017 versions 15.5 et ultérieures |

### <a name="convert-block-body-to-expression-bodied-member"></a>Convertir un corps de bloc en membre expression-bodied

Cette action rapide vous permet de convertir des corps de bloc en membres expression-bodied pour des méthodes, des constructeurs, des opérateurs, des propriétés, des indexeurs et des accesseurs.

```csharp
//Before
class MyClass4
{
    private int _myProperty;

    public int MyProperty
    {
        get { return _myProperty; }
        set
        {
            _myProperty = value;
        }
    }

    public MyClass4(int myProperty)
    {
        MyProperty = myProperty;
    }

    public void PrintProperty()
    {
        Console.WriteLine(MyProperty);
    }
}

// Use expression body for accessors/constructors/methods

// After
class MyClass4
{
    private int _myProperty;

    public int MyProperty
    {
        get => _myProperty;
        set => _myProperty = value;
    }

    public MyClass4(int myProperty) => MyProperty = myProperty;

    public void PrintProperty() => Console.WriteLine(MyProperty);
}
```

| ID de diagnostic | Langages applicables | Version prise en charge |
| ------- | -------------------- | ---------------- |
| IDE0021-27 | C# 6.0+ | Visual Studio 2017 et versions ultérieures |

### <a name="convert-anonymous-function-to-local-function"></a>Convertir une fonction anonyme en fonction locale

Cette action rapide convertit les fonctions anonymes en fonctions locales.

```csharp
// Before
Func<int, int> fibonacci = null;
fibonacci = (int n) =>
{
    return n <= 1 ? 1 : fibonacci(n - 1) + fibonacci(n - 2);
};

// Use local function

// After
int fibonacci(int n)
{
    return n <= 1 ? 1 : fibonacci(n-1) + fibonacci(n-2);
}
```

### <a name="convert-referenceequals-to-is-null"></a>Convertir « ReferenceEquals» en « is null »

| ID de diagnostic | Langages applicables | Version prise en charge |
| ------- | -------------------- | ---------------- |
| IDE0041 | C# 7.0+ | Visual Studio 2017 versions 15.5 et ultérieures |

Cette action rapide suggère l’utilisation de [critères spéciaux](/dotnet/csharp/pattern-matching) plutôt que le modèle de codage ```ReferenceEquals```, dans la mesure du possible.

```csharp
// Before
var value = "someString";
if (object.ReferenceEquals(value, null))
{
    return;
}

// Use 'is null' check

// After
var value = "someString";
if (value is null)
{
    return;
}
```

| ID de diagnostic | Langages applicables | Version prise en charge |
| ------- | -------------------- | ---------------- |
| IDE0039 | C# 7.0+ | Visual Studio 2017 version 15. et versions ultérieures |

### <a name="introduce-pattern-matching"></a>Introduire des critères spéciaux

Cette action rapide suggère l’utilisation de [critères spéciaux](/dotnet/csharp/pattern-matching) avec des casts et des contrôles de valeur null en C#.

```csharp
// Before
if (o is int)
{
    var i = (int)o;
    ...
}

// Use pattern matching

// After
if (o is int i)
{
    ...
}
```

```csharp
// Before
var s = o as string;
if (s != null)
{
    ...
}

// Use pattern matching

// After
if (o is string s)
{
    ...
}
```

| ID de diagnostic | Langages applicables | Version prise en charge |
| ------- | -------------------- | ---------------- |
| IDE0020 | C# 7.0+ | Visual Studio 2017 et versions ultérieures |
| IDE0019 | C# 7.0+ | Visual Studio 2017 et versions ultérieures |

### <a name="change-base-for-numeric-literals"></a>Changer la base des littéraux numériques

Cette action rapide vous permet de convertir un littéral numérique d’un système numérique de base en un autre. Par exemple, vous pouvez convertir un nombre en un format hexadécimal ou binaire.

```csharp
// Before
int countdown = 2097152;

// Convert to hex

// After
int countdown = 0x200000;
```

```vb
' Before
Dim countdown As Integer = 2097152

' Convert to hex

' After
Dim countdown As Integer = &H200000
```

| Langages applicables | Version prise en charge |
| ------- | -------------------- | ---------------- |
| C# 7.0+ et Visual Basic 14+ | Visual Studio 2017 version 15,3 et versions ultérieures |

### <a name="insert-digit-separators-into-literals"></a>Insérer des séparateurs numériques dans les littéraux

Cette action rapide vous permet d’ajouter des caractères de séparation aux valeurs littérales.

```csharp
// Before
int countdown = 1000000;

// Separate thousands

// After
int countdown = 1_000_000;
```

```vb
' Before
Dim countdown As Integer = 1000000

' Separate thousands

' After
Dim countdown As Integer = 1_000_000
```

| Langages applicables | Version prise en charge |
| ------- | -------------------- | ---------------- |
| C# 7.0+ et Visual Basic 14+ | Visual Studio 2017 version 15,3 et versions ultérieures |

### <a name="use-explicit-tuple-names"></a>Utiliser des noms de tuples explicites

Cette action rapide identifie les zones où le nom de tuple explicite peut être utilisé au lieu de Item1, Item2, etc.

```csharp
// Before
(string name, int age) customer = GetCustomer();
var name = customer.Item1;

// Use explicit tuple name

// After
(string name, int age) customer = GetCustomer();
var name = customer.name;
```

```vb
' Before
Dim customer As (name As String, age As Integer) = GetCustomer()
Dim name = customer.Item1

' Use explicit tuple name

' After
Dim customer As (name As String, age As Integer) = GetCustomer()
Dim name = customer.name
```

| ID de diagnostic | Langages applicables | Version prise en charge |
| ------- | -------------------- | ---------------- |
| IDE0033 | C# 7.0+ et Visual Basic 15+ | Visual Studio 2017 et versions ultérieures |

### <a name="use-inferred-names"></a>Utiliser des noms déduits

Cette action rapide indique quand du code peut être simplifié de façon à utiliser des noms de membre inférés dans les types anonymes ou des noms d’éléments inférés dans les tuples.

```csharp
// Before
var anon = new { age = age, name = name };

// Use inferred member name

// After
var anon = new { age, name };
```

```csharp
// Before
var tuple = (age: age, name: name);

// Use inferred tuple element name

// After
var tuple = (age, name);
```

| ID de diagnostic | Langages applicables | Version prise en charge |
| ------- | -------------------- | ---------------- |
| IDE0037 | C# | Visual Studio 2017 versions 15.5 et ultérieures |
| IDE0037 | C# 7.1+ | Visual Studio 2017 versions 15.5 et ultérieures |

### <a name="deconstruct-tuple-declaration"></a>Déconstruire la déclaration de tuple

Cette action rapide permet de déconstruire les déclarations de variables de tuple.

```csharp
// Before
var person = GetPersonTuple();
Console.WriteLine($"{person.name} {person.age}");

(int x, int y) point = GetPointTuple();
Console.WriteLine($"{point.x} {point.y}");

//Deconstruct variable declaration

// After
var (name, age) = GetPersonTuple();
Console.WriteLine($"{name} {age}");

(int x, int y) = GetPointTuple();
Console.WriteLine($"{x} {y}");
```

| ID de diagnostic | Langages applicables | Version prise en charge |
| ------- | -------------------- | ---------------- |
| IDE0042 | C# 7.0+ | Visual Studio 2017 versions 15.5 et ultérieures |

### <a name="make-method-synchronous"></a>Rendre la méthode synchrone

Lors de l’utilisation du mot clé `async` ou `Async` sur une méthode, le mot clé `await` ou `Await` doit également être utilisé dans cette méthode. Cependant, si ce n’est pas le cas, une action rapide apparaît, qui vous permet de rendre la méthode synchrone en supprimant le mot clé `async` ou `Async`, et en changeant le type de retour. Utilisez l’option **Rendre la méthode synchrone** dans le menu Actions rapides.

```csharp
// Before
async Task<int> MyAsyncMethod()
{
    return 3;
}

// Make method synchronous

// After
int MyAsyncMethod()
{
    return 3;
}
```

```vb
' Before
Async Function MyAsyncMethod() As Task(Of Integer)
    Return 3
End Function

' Make method synchronous

' After
Function MyAsyncMethod() As Integer
    Return 3
End Function
```

| ID d'erreur | Langages applicables |
| ------- | -------------------- |
| CS1998, BC42356 | C# et Visual Basic |

### <a name="make-method-asynchronous"></a>Rendre la méthode asynchrone

Si le mot clé `await` ou `Await` est utilisé dans une méthode, cette méthode doit se retrouver marquée du mot clé `async` ou `Async`. Toutefois, si ce n’est pas le cas, une Action rapide apparaît, qui rend la méthode asynchrone. Utilisez l’option **Make method/Function asynchronous** (Rendre la méthode/fonction asynchrone) dans le menu Actions rapides.

```csharp
// Before
int MyAsyncMethod()
{
    return await Task.Run(...);
}

// Make method asynchronous

// After
async Task<int> MyAsyncMethod()
{
    return await Task.Run(...);
}
```

```vb
' Before
Function MyAsyncMethod() as Integer
    Return  Await Task.Run(...)
End Function

' Make method asynchronous

' After
Async Function MyAsyncMethod() As Task(Of Integer)
    Return Await Task.Run(...)
End Function
```

| ID d'erreur | Langages applicables | Version prise en charge |
| ------- | -------------------- | ---------------- |
| CS4032, BC37057 | C# et Visual Basic | Visual Studio 2017 et versions ultérieures |

## <a name="see-also"></a>Voir aussi

- [Actions rapides](../ide/quick-actions.md)
