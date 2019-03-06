---
title: Paramètres des conventions de codage .NET pour EditorConfig
ms.date: 06/14/2018
ms.topic: reference
dev_langs:
- CSharp
- VB
helpviewer_keywords:
- coding conventions [EditorConfig]
- EditorConfig coding conventions
- language code style rules [EditorConfig]
- formatting conventions [EditorConfig]
author: kuhlenh
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 52848599e05f5b7e5050e408f98d9ff4d670ca72
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55911869"
---
# <a name="net-coding-convention-settings-for-editorconfig"></a>Paramètres des conventions de codage .NET pour EditorConfig

Dans Visual Studio 2017, vous pouvez définir le style de votre code base, et le maintenir cohérent, à l’aide d’un fichier [EditorConfig](../ide/create-portable-custom-editor-options.md). EditorConfig inclut plusieurs propriétés de mise en forme de base, telles que `indent_style` et `indent_size`. Dans Visual Studio, les paramètres des conventions de codage .NET peuvent également être configurés à l’aide d’un fichier EditorConfig. Grâce aux fichiers EditorConfig, vous pouvez activer ou désactiver des conventions de codage .NET spécifiques, et configurer le degré d’application de la convention au moyen d’un niveau de gravité. Pour en savoir plus sur l’utilisation d’EditorConfig pour appliquer la cohérence dans votre code base, lisez [Créer des options d’éditeur personnalisées et portables](../ide/create-portable-custom-editor-options.md).

Voir [l’exemple de fichier .editorconfig](#example-editorconfig-file) à la fin de cet article.

## <a name="convention-categories"></a>Catégories de conventions

Trois catégories de conventions de codage .NET sont prises en charge :

- [Styles de code de langage](#language-code-styles)

   Règles relatives au langage C# ou Visual Basic. Par exemple, vous pouvez spécifier des règles régissant l’utilisation de `var` ou de types explicites lors de la définition de variables, ou l’utilisation préférentielle de membres expression-bodied.

- [Conventions de mise en forme](#formatting-conventions)

   Règles relatives à la disposition et la structure de votre code pour en faciliter la lecture. Par exemple, vous pouvez spécifier des règles régissant les accolades Allman ou l’utilisation préférentielle d’espaces dans les blocs de contrôle.

- [Conventions d’attribution d’un nom](../ide/editorconfig-naming-conventions.md)

   Règles régissant la façon dont les éléments de code sont nommés. Par exemple, vous pouvez spécifier que les méthodes `async` doivent se terminer par "Async".

## <a name="language-code-styles"></a>Styles de code de langage

Les règles relatives aux styles de code de langage ont le format suivant :

`options_name = false|true : none|silent|suggestion|warning|error`

Pour chaque règle de style de code de langage, vous devez spécifier **true** (préférer ce style) ou **false** (ne pas préférer ce style), ainsi qu’un niveau de **gravité**. La gravité spécifie le niveau de l’application de ce style.

Le tableau suivant répertorie les valeurs de gravité possibles, ainsi que leurs effets :

Gravité | Effet
:------- | ------
`none` | Ne rien afficher à l’utilisateur en cas de violation de cette règle. Toutefois, les fonctionnalités de génération de code génèrent du code dans ce style. Les règles avec une gravité `none` n’apparaissent jamais dans le menu **Actions rapides et refactorisations**. Dans la plupart des cas, ceci est considéré comme « désactivé » ou « ignoré ».
`silent` (également `refactoring` dans Visual Studio 2017 version 15.8) | Ne rien afficher à l’utilisateur en cas de violation de cette règle. Toutefois, les fonctionnalités de génération de code génèrent du code dans ce style. Les règles avec la gravité `silent` participent au nettoyage et apparaissent dans le menu **Actions rapides et refactorisations**.
`suggestion` | En cas de violation de cette règle de style, l’afficher à l’utilisateur comme une suggestion. Les suggestions s’affichent sous la forme de trois points gris sous les deux premiers caractères.
`warning` | En cas de violation de cette règle de style, afficher un avertissement du compilateur.
`error` | En cas de violation de cette règle de style, afficher une erreur du compilateur.

La liste suivante affiche les paramètres de style de code de langage autorisés :

- Paramètres de style de code .NET
    - [Qualificateurs "This." et "Me."](#this_and_me)
        - dotnet\_style\_qualification\_for_field
        - dotnet\_style\_qualification\_for_property
        - dotnet\_style\_qualification\_for_method
        - dotnet\_style\_qualification\_for_event
    - [Mots clés de langage plutôt que des noms de types d’infrastructure pour les références de type](#language_keywords)
        - dotnet\_style\_predefined\_type\_for\_locals\_parameters_members
        - dotnet\_style\_predefined\_type\_for\_member_access
    - [Préférences des modificateurs](#normalize_modifiers)
        - dotnet\_style\_require\_accessibility_modifiers
        - csharp\_preferred\_modifier_order
        - visual\_basic\_preferred\_modifier_order
        - dotnet\_style\_readonly\_field
    - [Préférences de parenthèses](#parentheses)
        - dotnet\_style\_parentheses\_in\_arithmetic\_binary\_operators
        - dotnet\_style\_parentheses\_in\_other\_binary\_operators
        - dotnet\_style\_parentheses\_in\_other\_operators
        - dotnet\_style\_parentheses\_in\_relational\_binary\_operators
    - [Préférences au niveau de l’expression](#expression_level)
        - dotnet\_style\_object_initializer
        - dotnet\_style\_collection_initializer
        - dotnet\_style\_explicit\_tuple_names
        - dotnet\_style\_prefer\_inferred\_tuple_names
        - dotnet\_style\_prefer\_inferred\_anonymous\_type\_member_names
        - dotnet\_style\_prefer\_auto\_properties
        - dotnet\_style\_prefer\_is\_null\_check\_over\_reference\_equality\_method
        - dotnet\_style\_prefer\_conditional\_expression\_over\_assignment
        - dotnet\_style\_prefer\_conditional\_expression\_over\_return
    - [Préférences de vérification de valeur "Null"](#null_checking)
        - dotnet\_style\_coalesce_expression
        - dotnet\_style\_null_propagation
- Paramètres de style de code C#
    - [Types implicites et explicites](#implicit-and-explicit-types)
        - csharp\_style\_var\_for\_built\_in_types
        - csharp\_style\_var\_when\_type\_is_apparent
        - csharp\_style\_var_elsewhere
    - [Membres expression-bodied](#expression_bodied_members)
        - csharp\_style\_expression\_bodied_methods
        - csharp\_style\_expression\_bodied_constructors
        - csharp\_style\_expression\_bodied_operators
        - csharp\_style\_expression\_bodied_properties
        - csharp\_style\_expression\_bodied_indexers
        - csharp\_style\_expression\_bodied_accessors
    - [Critères spéciaux](#pattern_matching)
        - csharp\_style\_pattern\_matching\_over\_is\_with\_cast_check
        - csharp\_style\_pattern\_matching\_over\_as\_with\_null_check
    - [Déclarations de variables inline](#inlined_variable_declarations)
        - csharp\_style\_inlined\_variable_declaration
    - [Préférences au niveau de l’expression](#expression_level_csharp)
        - csharp\_prefer\_simple\_default_expression
        - csharp\_style\_deconstructed\_variable_declaration
        - csharp\_style\_pattern\_local\_over\_anonymous_function
    - [Préférences de vérification de valeur "Null"](#null_checking_csharp)
        - csharp\_style\_throw_expression
        - csharp\_style\_conditional\_delegate_call
    - [Préférences des blocs de code](#code_block)
        - csharp\_prefer_braces

### <a name="net-code-style-settings"></a>Paramètres de style de code .NET

Les règles de style mentionnées dans cette section s’appliquent aussi bien au langage C# qu’au langage Visual Basic. Pour voir des exemples de code dans votre langage de programmation préféré, choisissez-le dans le menu déroulant **Langage** menu situé en haut à droite dans la fenêtre du navigateur.

#### Qualificateurs <a name="this_and_me"></a>« This. » et « Me. »

Cette règle de style (ID de règle IDE0003 et IDE0009) peut s’appliquer à des champs, à des propriétés, à des méthodes ou à des événements. La valeur **true** signifie qu’il faut faire en sorte de faire précéder le symbole de code de `this.` en C# ou de `Me.` en Visual Basic. La valeur **false** signifie qu’il faut faire en sorte de ne _pas_ faire précéder l’élément de code de `this.` ou de `Me.`.

Le tableau suivant indique le nom des règles, les langages de programmation applicables et les valeurs par défaut :

| Nom de la règle | Langages applicables | Valeur par défaut de Visual Studio |
| ----------- | -------------------- | ----------------------|
| dotnet_style_qualification_for_field | C# et Visual Basic | false:none |
| dotnet_style_qualification_for_property | C# et Visual Basic | false:none |
| dotnet_style_qualification_for_method | C# et Visual Basic | false:none |
| dotnet_style_qualification_for_event | C# et Visual Basic | false:none |

**dotnet\_style\_qualification\_for_field**

- Quand cette règle est définie sur **true**, il faut faire en sorte de faire précéder les champs de `this.` en C# ou de `Me.` en Visual Basic.
- Quand cette règle est définie sur **false**, il faut faire en sorte de ne _pas_ faire précéder les champs de `this.` ou de `Me.`.

Exemples de code :

```csharp
// dotnet_style_qualification_for_field = true
this.capacity = 0;

// dotnet_style_qualification_for_field = false
capacity = 0;
```

```vb
' dotnet_style_qualification_for_field = true
Me.capacity = 0

' dotnet_style_qualification_for_field = false
capacity = 0
```

**dotnet\_style\_qualification\_for_property**

- Quand cette règle est définie sur **true**, il faut faire en sorte de faire précéder les propriétés de `this.` en C# ou de `Me.` en Visual Basic.
- Quand cette règle est définie sur **false**, il faut faire en sorte de ne _pas_ faire précéder les propriétés de `this.` ou de `Me.`.

Exemples de code :

```csharp
// dotnet_style_qualification_for_property = true
this.ID = 0;

// dotnet_style_qualification_for_property = false
ID = 0;
```

```vb
' dotnet_style_qualification_for_property = true
Me.ID = 0

' dotnet_style_qualification_for_property = false
ID = 0
```

**dotnet\_style\_qualification\_for_method**

- Quand cette règle est définie sur **true**, il faut faire en sorte de faire précéder les méthodes de `this.` en C# ou de `Me.` en Visual Basic.
- Quand cette règle est définie sur **false**, il faut faire en sorte de ne _pas_ faire précéder les méthodes de `this.` ou de `Me.`.

Exemples de code :

```csharp
// dotnet_style_qualification_for_method = true
this.Display();

// dotnet_style_qualification_for_method = false
Display();
```

```vb
' dotnet_style_qualification_for_method = true
Me.Display()

' dotnet_style_qualification_for_method = false
Display()
```

**dotnet\_style\_qualification\_for_event**

- Quand cette règle est définie sur **true**, il faut faire en sorte de faire précéder les événements de `this.` en C# ou de `Me.` en Visual Basic.
- Quand cette règle est définie sur **false**, il faut faire en sorte de ne _pas_ faire précéder les événements de `this.` ou de `Me.`.

Exemples de code :

```csharp
// dotnet_style_qualification_for_event = true
this.Elapsed += Handler;

// dotnet_style_qualification_for_event = false
Elapsed += Handler;
```

```vb
' dotnet_style_qualification_for_event = true
AddHandler Me.Elapsed, AddressOf Handler

' dotnet_style_qualification_for_event = false
AddHandler Elapsed, AddressOf Handler
```

Ces règles peuvent apparaître dans un fichier *.editorconfig* comme suit :

```EditorConfig
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_qualification_for_field = false:suggestion
dotnet_style_qualification_for_property = false:suggestion
dotnet_style_qualification_for_method = false:suggestion
dotnet_style_qualification_for_event = false:suggestion
```

#### <a name="language_keywords"></a>Mots clés du langage au lieu des noms de types de framework pour les références de type

Cette règle de style peut être appliquée à des variables locales, des paramètres de méthode et des membres de classe, ou comme une règle distincte à des expressions d’accès de membre de type. La valeur **true** signifie que, pour les types représentés par un mot clé de langage (par exemple, `int` ou `Integer`), on utilise de préférence ce mot clé plutôt que le nom de type (par exemple, `Int32`). La valeur **false** signifie qu’il faut faire en sorte que le nom du type soit utilisé plutôt que le mot clé du langage.

Le tableau suivant indique le nom des règles, les ID de règles, les langages de programmation applicables et les valeurs par défaut :

| Nom de la règle | ID de règle | Langages applicables | Valeur par défaut de Visual Studio |
| --------- | ------- | -------------------- | ----------------------|
| dotnet_style_predefined_type_for_locals_parameters_members | IDE0012 et IDE0014 | C# et Visual Basic | true:none |
| dotnet_style_predefined_type_for_member_access | IDE0013 et IDE0015 | C# et Visual Basic | true:none |

**dotnet\_style\_predefined\_type\_for\_locals\_parameters_members**

- Quand cette règle est définie sur **true**, il faut faire en sorte que les types qui ont un mot clé de langage pour les représenter utilisent le mot clé du langage plutôt que le nom du type pour les variables locales, les paramètres de méthode et les membres de classe.
- Quand cette règle est définie sur **false**, il faut faire en sorte que les variables locales, les paramètres de méthode et les membres de classe utilisent le nom de type plutôt que le mot clé du langage.

Exemples de code :

```csharp
// dotnet_style_predefined_type_for_locals_parameters_members = true
private int _member;

// dotnet_style_predefined_type_for_locals_parameters_members = false
private Int32 _member;
```

```vb
' dotnet_style_predefined_type_for_locals_parameters_members = true
Private _member As Integer

' dotnet_style_predefined_type_for_locals_parameters_members = false
Private _member As Int32
```

**dotnet\_style\_predefined\_type\_for\_member_access**

- Quand cette règle est définie sur **true**, il faut faire en sorte que les types qui ont un mot clé de langage pour les représenter utilisent le mot clé du langage plutôt que le nom du type pour les expressions d’accès de membre.
- Quand cette règle est définie sur **false**, il faut faire en sorte que les expressions d’accès de membre utilisent le nom de type plutôt que le mot clé du langage.

Exemples de code :

```csharp
// dotnet_style_predefined_type_for_member_access = true
var local = int.MaxValue;

// dotnet_style_predefined_type_for_member_access = false
var local = Int32.MaxValue;
```

```vb
' dotnet_style_predefined_type_for_member_access = true
Dim local = Integer.MaxValue

' dotnet_style_predefined_type_for_member_access = false
Dim local = Int32.MaxValue
```

Ces règles peuvent apparaître dans un fichier *.editorconfig* comme suit :

```EditorConfig
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_predefined_type_for_locals_parameters_members = true:suggestion
dotnet_style_predefined_type_for_member_access = true:suggestion
```

#### <a name="normalize_modifiers"></a>Préférences des modificateurs

Les règles de style de cette section concernent les préférences des modificateurs, notamment la spécification obligatoire des modificateurs d’accessibilité, l’indication de l’ordre de tri souhaité pour les modificateurs, ainsi que la spécification obligatoire du modificateur en lecture seule.

Le tableau suivant indique le nom des règles, les ID de règles, les langages de programmation applicables, les valeurs par défaut et la première version de Visual Studio prise en charge :

| Nom de la règle | ID de règle | Langages applicables | Valeur par défaut de Visual Studio | Version de Visual Studio 2017 |
| --------- | ------- | -------------------- | ----------------------| ---------------- |
| dotnet_style_require_accessibility_modifiers | IDE0040 | C# et Visual Basic | for_non_interface_members:none | 15.5 |
| csharp_preferred_modifier_order | IDE0036 | C# | public, private, protected, internal, static, extern, new, virtual, abstract, sealed, override, readonly, unsafe, volatile, async:none | 15.5 |
| visual_basic_preferred_modifier_order | IDE0036 | Visual Basic | Partial, Default, Private, Protected, Public, Friend, NotOverridable, Overridable, MustOverride, Overloads, Overrides, MustInherit, NotInheritable, Static, Shared, Shadows, ReadOnly, WriteOnly, Dim, Const,WithEvents, Widening, Narrowing, Custom, Async:none | 15.5 |
| dotnet_style_readonly_field | IDE0044 | C# et Visual Basic | true:suggestion | 15.7 |

**dotnet\_style\_require\_accessibility_modifiers**

Cette règle n’accepte pas une valeur **true** ou **false**, elle accepte à la place une valeur du tableau suivant :

| Value | Description |
| ----- |:----------- |
| always | Préférer la déclaration de modificateurs d’accessibilité |
| for\_non\_interface_members | Préférer la déclaration de modificateurs d’accessibilité, sauf pour des membres d’interface publique. Ceci est identique à **always** et a été ajouté à des fins de vérification future, si C# ajoute des méthodes d’interface par défaut. |
| never | Ne jamais préférer la déclaration de modificateurs d’accessibilité |

Exemples de code :

```csharp
// dotnet_style_require_accessibility_modifiers = always
// dotnet_style_require_accessibility_modifiers = for_non_interface_members
class MyClass
{
    private const string thisFieldIsConst = "constant";
}

// dotnet_style_require_accessibility_modifiers = never
class MyClass
{
    const string thisFieldIsConst = "constant";
}
```

**csharp_preferred_modifier_order**

- Quand cette règle est définie sur une liste de modificateurs, préférer l’ordre spécifié.
- Quand cette règle est omise dans le fichier, il n’y a pas d’ordre préféré pour les modificateurs.

Exemples de code :

```csharp
// csharp_preferred_modifier_order = public,private,protected,internal,static,extern,new,virtual,abstract,sealed,override,readonly,unsafe,volatile,async
class MyClass
{
    private static readonly int _daysInYear = 365;
}
```

**visual_basic_preferred_modifier_order**

- Quand cette règle est définie sur une liste de modificateurs, préférer l’ordre spécifié.
- Quand cette règle est omise dans le fichier, il n’y a pas d’ordre préféré pour les modificateurs.

Exemples de code :

```vb
' visual_basic_preferred_modifier_order = Partial,Default,Private,Protected,Public,Friend,NotOverridable,Overridable,MustOverride,Overloads,Overrides,MustInherit,NotInheritable,Static,Shared,Shadows,ReadOnly,WriteOnly,Dim,Const,WithEvents,Widening,Narrowing,Custom,Async
Public Class MyClass
    Private Shared ReadOnly daysInYear As Int = 365
End Class
```

**dotnet_style_readonly_field**

- Quand cette règle a la valeur **true**, les champs doivent être marqués de préférence avec `readonly` (C#) ou `ReadOnly` (Visual Basic), s’ils sont assignés inline ou dans un constructeur.
- Quand cette règle a la valeur **false**, aucune préférence n’est spécifiée concernant le marquage des champs avec `readonly` (C#) ou `ReadOnly` (Visual Basic).

Exemples de code :

```csharp
// dotnet_style_readonly_field = true
class MyClass
{
    private readonly int _daysInYear = 365;
}
```

```vb
' dotnet_style_readonly_field = true
Public Class MyClass
    Private ReadOnly daysInYear As Int = 365
End Class
```

Ces règles peuvent apparaître dans un fichier *.editorconfig* comme suit :

```EditorConfig
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_require_accessibility_modifiers = always:suggestion
dotnet_style_readonly_field = true:warning

# CSharp code style settings:
[*.cs]
csharp_preferred_modifier_order = public,private,protected,internal,static,extern,new,virtual,abstract,sealed,override,readonly,unsafe,volatile,async:suggestion

# Visual Basic code style settings:
[*.vb]
visual_basic_preferred_modifier_order = Partial,Default,Private,Protected,Public,Friend,NotOverridable,Overridable,MustOverride,Overloads,Overrides,MustInherit,NotInheritable,Static,Shared,Shadows,ReadOnly,WriteOnly,Dim,Const,WithEvents,Widening,Narrowing,Custom,Async:suggestion
```

#### <a name="parentheses"></a>Préférences de parenthèses

Les règles de style de cette section concernent les préférences de parenthèses, notamment l’utilisation de parenthèses pour les opérateurs arithmétiques, relationnels et autres opérateurs binaires.

Le tableau suivant indique le nom des règles, les ID de règles, les langages de programmation applicables, les valeurs par défaut et la première version de Visual Studio prise en charge :

| Nom de la règle | ID de règle | Langages applicables | Valeur par défaut de Visual Studio | Version de Visual Studio 2017 |
| --------- | ------- | -------------------- | ----------------------| ---- |
| dotnet_style_parentheses_in_arithmetic_binary_operators | IDE0047 | C# et Visual Basic | always_for_clarity:none | 15.8 |
| dotnet_style_parentheses_in_relational_binary_operators | IDE0047 | C# et Visual Basic | always_for_clarity:none | 15.8 |
| dotnet_style_parentheses_in_other_binary_operators | IDE0047 | C# et Visual Basic | always_for_clarity:none | 15.8 |
| dotnet_style_parentheses_in_other_operators | IDE0047 | C# et Visual Basic | never_if_unnecessary:none | 15.8 |

**dotnet\_style\_parentheses\_in\_arithmetic\_binary_operators**

- Quand cette règle a la valeur **always_for_clarity**, il est préférable d’utiliser des parenthèses pour clarifier la priorité des opérateurs arithmétiques (`*`, `/`, `%`, `+`, `-`, `<<`, `>>`, `&`, `^`, `|`).
- Quand cette règle a la valeur **never_if_unnecessary**, il est préférable d’éviter les parenthèses si la priorité des opérateurs arithmétiques (`*`, `/`, `%`, `+`, `-`, `<<`, `>>`, `&`, `^`, `|`) est évidente.

Exemples de code :

```csharp
// dotnet_style_parentheses_in_arithmetic_binary_operators = always_for_clarity
var v = a + (b * c);

// dotnet_style_parentheses_in_arithmetic_binary_operators = never_if_unnecessary
var v = a + b * c;
```

```vb
' dotnet_style_parentheses_in_arithmetic_binary_operators = always_for_clarity
Dim v = a + (b * c)

' dotnet_style_parentheses_in_arithmetic_binary_operators = never_if_unnecessary
Dim v = a + b * c
```

**dotnet\_style\_parentheses\_in\_relational\_binary_operators**

- Quand cette règle a la valeur **always_for_clarity**, on utilise de préférence des parenthèses pour clarifier la précédence des opérateurs relationnels (`>`, `<`, `<=`, `>=`, `is`, `as`, `==`, `!=`).
- Quand cette règle a la valeur **never_if_unnecessary**, il est préférable d’éviter les parenthèses si la priorité des opérateurs relationnels (`>`, `<`, `<=`, `>=`, `is`, `as`, `==`, `!=`) est évidente.

Exemples de code :

```csharp
// dotnet_style_parentheses_in_relational_binary_operators = always_for_clarity
var v = (a < b) == (c > d);

// dotnet_style_parentheses_in_relational_binary_operators = never_if_unnecessary
var v = a < b == c > d;
```

```vb
' dotnet_style_parentheses_in_relational_binary_operators = always_for_clarity
Dim v = (a < b) = (c > d)

' dotnet_style_parentheses_in_relational_binary_operators = never_if_unnecessary
Dim v = a < b = c > d
```

**dotnet\_style\_parentheses\_in\_other\_binary_operators**

- Quand cette règle a la valeur **always_for_clarity**, il est préférable d’utiliser des parenthèses pour clarifier la priorité des autres opérateurs binaires (`&&`, `||`, `??`).
- Quand cette règle a la valeur **never_if_unnecessary**, il est préférable d’éviter les parenthèses si la priorité des autres opérateurs binaires (`&&`, `||`, `??`) est évidente.

Exemples de code :

```csharp
// dotnet_style_parentheses_in_other_binary_operators = always_for_clarity
var v = a || (b && c);

// dotnet_style_parentheses_in_other_binary_operators = never_if_unnecessary
var v = a || b && c;
```

```vb
' dotnet_style_parentheses_in_other_binary_operators = always_for_clarity
Dim v = a OrElse (b AndAlso c)

' dotnet_style_parentheses_in_other_binary_operators = never_if_unnecessary
Dim v = a OrElse b AndAlso c
```

**dotnet\_style\_parentheses\_in\_other_operators**

- Quand cette règle a la valeur **always_for_clarity**, il est préférable d’utiliser des parenthèses pour clarifier la priorité des opérateurs.
- Quand cette règle a la valeur **never_if_unnecessary**, il est préférable d’éviter les parenthèses si la priorité des opérateurs est évidente.

Exemples de code :

```csharp
// dotnet_style_parentheses_in_other_operators = always_for_clarity
var v = (a.b).Length;

// dotnet_style_parentheses_in_other_operators = never_if_unnecessary
var v = a.b.Length;
```

```vb
' dotnet_style_parentheses_in_other_operators = always_for_clarity
Dim v = (a.b).Length

' dotnet_style_parentheses_in_other_operators = never_if_unnecessary
Dim v = a.b.Length
```

Ces règles peuvent apparaître dans un fichier *.editorconfig* comme suit :

```EditorConfig
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_parentheses_in_arithmetic_binary_operators = always_for_clarity:none
dotnet_style_parentheses_in_relational_binary_operators = always_for_clarity:none
dotnet_style_parentheses_in_other_binary_operators = always_for_clarity:none
dotnet_style_parentheses_in_other_operators = never_if_unnecessary:none
```

#### <a name="expression_level"></a>Préférences au niveau des expressions

Les règles de style mentionnées dans cette section concernent les préférences au niveau de l’expression, notamment l’utilisation d’initialiseurs d’objets, d’initialiseurs de collections, de noms de tuples explicites ou déduits, et de types anonymes déduits.

Le tableau suivant indique le nom des règles, les ID de règles, les langages de programmation applicables, les valeurs par défaut et la première version de Visual Studio prise en charge :

| Nom de la règle | ID de règle | Langages applicables | Valeur par défaut de Visual Studio | Version de Visual Studio 2017 |
| --------- | ------- | -------------------- | ----------------------| ---- |
| dotnet_style_object_initializer | IDE0017 | C# et Visual Basic | true:suggestion | Première version |
| dotnet_style_collection_initializer | IDE0028 | C# et Visual Basic | true:suggestion | Première version |
| dotnet_style_explicit_tuple_names | IDE0033 | C# 7.0+ et Visual Basic 15+ | true:suggestion | Première version |
| dotnet_style_prefer_inferred_tuple_names | IDE0037 | C# 7.1+ et Visual Basic 15+ | true:suggestion | 15,6 |
| dotnet_style_prefer_inferred_anonymous_type_member_names | IDE0037 | C# et Visual Basic | true:suggestion | 15,6 |
| dotnet_style_prefer_auto_properties | IDE0032 | C# et Visual Basic | true:none | 15.7 |
| dotnet_style_prefer_is_null_check_over_reference_equality_method | IDE0041 | C# et Visual Basic | true:suggestion | 15.7 |
| dotnet_style_prefer_conditional_expression_over_assignment | IDE0045 | C# et Visual Basic | true:none | 15.8 |
| dotnet_style_prefer_conditional_expression_over_return | IDE0046 | C# et Visual Basic | true:none | 15.8 |

**dotnet\_style\_object_initializer**

- Quand cette règle est définie sur **true**, il faut faire en sorte que les objets soient initialisés à l’aide d’initialiseurs d’objets, dans la mesure du possible.
- Quand cette règle est définie sur **false**, il faut faire en sorte que les objets ne soient *pas* initialisés à l’aide d’initialiseurs d’objets.

Exemples de code :

```csharp
// dotnet_style_object_initializer = true
var c = new Customer() { Age = 21 };

// dotnet_style_object_initializer = false
var c = new Customer();
c.Age = 21;
```

```vb
' dotnet_style_object_initializer = true
Dim c = New Customer() With {.Age = 21}

' dotnet_style_object_initializer = false
Dim c = New Customer()
c.Age = 21
```

**dotnet\_style\_collection_initializer**

- Quand cette règle est définie sur **true**, il faut faire en sorte que les collections soient initialisées à l’aide d’initialiseurs de collections, dans la mesure du possible.
- Quand cette règle est définie sur **false**, il faut faire en sorte que les collections ne soient *pas* initialisées à l’aide d’initialiseurs de collections.

Exemples de code :

```csharp
// dotnet_style_collection_initializer = true
var list = new List<int> { 1, 2, 3 };

// dotnet_style_collection_initializer = false
var list = new List<int>();
list.Add(1);
list.Add(2);
list.Add(3);
```

```vb
' dotnet_style_collection_initializer = true
Dim list = New List(Of Integer) From {1, 2, 3}

' dotnet_style_collection_initializer = false
Dim list = New List(Of Integer)
list.Add(1)
list.Add(2)
list.Add(3)
```

**dotnet\_style\_explicit\_tuple_names**

- Quand cette règle est définie sur **true**, il faut préférer les noms de tuples aux propriétés ItemX.
- Quand cette règle est définie sur **false**, il faut préférer les propriétés ItemX aux noms de tuples.

Exemples de code :

```csharp
// dotnet_style_explicit_tuple_names = true
(string name, int age) customer = GetCustomer();
var name = customer.name;

// dotnet_style_explicit_tuple_names = false
(string name, int age) customer = GetCustomer();
var name = customer.Item1;
```

```vb
 ' dotnet_style_explicit_tuple_names = true
Dim customer As (name As String, age As Integer) = GetCustomer()
Dim name = customer.name

' dotnet_style_explicit_tuple_names = false
Dim customer As (name As String, age As Integer) = GetCustomer()
Dim name = customer.Item1
```

**dotnet\_style\_prefer\_inferred\_tuple_names**

- Lorsque cette règle est définie sur **true**, préférer les noms d’éléments de tuple déduits.
- Lorsque cette règle est définie sur **false**, préférer les noms d’éléments de tuple explicites.

Exemples de code :

```csharp
// dotnet_style_prefer_inferred_tuple_names = true
var tuple = (age, name);

// dotnet_style_prefer_inferred_tuple_names = false
var tuple = (age: age, name: name);
```

```vb
' dotnet_style_prefer_inferred_tuple_names = true
Dim tuple = (name, age)

' dotnet_style_prefer_inferred_tuple_names = false
Dim tuple = (name:=name, age:=age)
```

**dotnet\_style\_prefer\_inferred\_anonymous\_type\_member_names**

- Lorsque cette règle est définie sur **true**, préférer les noms de membres de type anonyme déduits.
- Lorsque cette règle est définie sur **false**, préférer les noms de membres de type anonyme explicites.

Exemples de code :

```csharp
// dotnet_style_prefer_inferred_anonymous_type_member_names = true
var anon = new { age, name };

// dotnet_style_prefer_inferred_anonymous_type_member_names = false
var anon = new { age = age, name = name };
```

```vb
' dotnet_style_prefer_inferred_anonymous_type_member_names = true
Dim anon = New With {name, age}

' dotnet_style_prefer_inferred_anonymous_type_member_names = false
Dim anon = New With {.name = name, .age = age}
```

**dotnet\_style\_prefer\_auto\_properties**

- Quand cette règle est définie sur **true**, on utilise de préférence des propriétés automatiques plutôt que des propriétés comportant des champs de stockage privés.
- Quand cette règle est définie sur **False**, on utilise de préférence des propriétés comportant des champs de stockage privés plutôt que des propriétés automatiques.

Exemples de code :

```csharp
// dotnet_style_prefer_auto_properties = true
private int Age { get; }

// dotnet_style_prefer_auto_properties = false
private int age;

public int Age
{
    get
    {
        return age;
    }
}
```

```vb
' dotnet_style_prefer_auto_properties = true
Public ReadOnly Property Age As Integer

' dotnet_style_prefer_auto_properties = false
Private _age As Integer

Public ReadOnly Property Age As Integer
    Get
        return _age
    End Get
End Property
```

**dotnet\_style\_prefer\_is\_null\_check\_over\_reference\_equality\_method**

- Quand cette règle est définie sur **true**, préférer l’utilisation d’un contrôle de valeur null avec critères spéciaux à object.ReferenceEquals.
- Quand cette règle est définie sur **false**, préférer object.ReferenceEquals à un contrôle de valeur null avec critères spéciaux.

Exemples de code :

```csharp
// dotnet_style_prefer_is_null_check_over_reference_equality_method = true
if (value is null)
    return;

// dotnet_style_prefer_is_null_check_over_reference_equality_method = false
if (object.ReferenceEquals(value, null))
    return;
```

```vb
' dotnet_style_prefer_is_null_check_over_reference_equality_method = true
If value Is Nothing
    Return
End If

' dotnet_style_prefer_is_null_check_over_reference_equality_method = false
If Object.ReferenceEquals(value, Nothing)
    Return
End If
```



**dotnet\_style\_prefer\_conditional\_expression\_over_assignment**

- Quand cette règle a la valeur **true**, préférez les assignations avec une expression conditionnelle ternaire aux assignations avec une instruction if-else.
- Quand cette règle a la valeur **false**, préférez les assignations avec une instruction if-else aux assignations avec une expression conditionnelle ternaire.

Exemples de code :

```csharp
// dotnet_style_prefer_conditional_expression_over_assignment = true
string s = expr ? "hello" : "world";

// dotnet_style_prefer_conditional_expression_over_assignment = false
string s;
if (expr)
{
    s = "hello";
}
else
{
    s = "world";
}
```

```vb
' dotnet_style_prefer_conditional_expression_over_assignment = true
Dim s As String = If(expr, "hello", "world")

' dotnet_style_prefer_conditional_expression_over_assignment = false
Dim s As String
If expr Then
    s = "hello"
Else
    s = "world"
End If
```

**dotnet\_style\_prefer\_conditional\_expression\_over_return**

- Quand cette règle a la valeur **true**, préférez les instructions de retour avec une expression conditionnelle ternaire aux instructions de retour avec une instruction if-else.
- Quand cette règle a la valeur **false**, préférez les instructions de retour avec une instruction if-else aux instructions de retour avec une expression conditionnelle ternaire.

Exemples de code :

```csharp
// dotnet_style_prefer_conditional_expression_over_return = true
return expr ? "hello" : "world"

// dotnet_style_prefer_conditional_expression_over_return = false
if (expr)
{
    return "hello";
}
else
{
    return "world";
}
```

```vb
' dotnet_style_prefer_conditional_expression_over_return = true
Return If(expr, "hello", "world")

' dotnet_style_prefer_conditional_expression_over_return = false
If expr Then
    Return "hello"
Else
    Return "world"
End If
```

Ces règles peuvent apparaître dans un fichier *.editorconfig* comme suit :

```EditorConfig
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_object_initializer = true:suggestion
dotnet_style_collection_initializer = true:suggestion
dotnet_style_explicit_tuple_names = true:suggestion
dotnet_style_prefer_inferred_tuple_names = true:suggestion
dotnet_style_prefer_inferred_anonymous_type_member_names = true:suggestion
dotnet_style_prefer_auto_properties = true:none
dotnet_style_prefer_conditional_expression_over_assignment = true:suggestion
dotnet_style_prefer_conditional_expression_over_return = true:suggestion
```

#### <a name="null_checking"></a>Préférences de vérification de valeur null

Les règles de style de cette section concernent les préférences de vérification de valeur null.

Le tableau suivant indique le nom des règles, les ID de règles, les langages de programmation applicables, les valeurs par défaut et la première version de Visual Studio prise en charge :

| Nom de la règle | ID de règle | Langages applicables | Valeur par défaut de Visual Studio | Version de Visual Studio 2017 |
| --------- | ------- | -------------------- | ----------------------| ---- |
| dotnet_style_coalesce_expression | IDE0029 | C# et Visual Basic | true:suggestion | Première version |
| dotnet_style_null_propagation | IDE0031 | C# 6.0+ et Visual Basic 14+ | true:suggestion | Première version |

**dotnet\_style\_coalesce_expression**

- Quand cette règle est définie sur **true**, il faut préférer les expressions de fusion null à la vérification d’opérateur ternaire.
- Quand cette règle est définie sur **false**, il faut préférer la vérification d’opérateur ternaire aux expressions de fusion null.

Exemples de code :

```csharp
// dotnet_style_coalesce_expression = true
var v = x ?? y;

// dotnet_style_coalesce_expression = false
var v = x != null ? x : y; // or
var v = x == null ? y : x;
```

```vb
' dotnet_style_coalesce_expression = true
Dim v = If(x, y)

' dotnet_style_coalesce_expression = false
Dim v = If(x Is Nothing, y, x) ' or
Dim v = If(x IsNot Nothing, x, y)
```

**dotnet\_style\_null_propagation**

- Quand cette règle est définie sur **true**, il faut préférer utiliser l’opérateur conditionnel null, dans la mesure du possible.
- Quand cette règle est définie sur **false**, il faut préférer utiliser la vérification de la valeur null ternaire, dans la mesure du possible.

Exemples de code :

```csharp
// dotnet_style_null_propagation = true
var v = o?.ToString();

// dotnet_style_null_propagation = false
var v = o == null ? null : o.ToString(); // or
var v = o != null ? o.String() : null;
```

```vb
' dotnet_style_null_propagation = true
Dim v = o?.ToString()

' dotnet_style_null_propagation = false
Dim v = If(o Is Nothing, Nothing, o.ToString()) ' or
Dim v = If(o IsNot Nothing, o.ToString(), Nothing)
```

Ces règles peuvent apparaître dans un fichier *.editorconfig* comme suit :

```EditorConfig
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_coalesce_expression = true:suggestion
dotnet_style_null_propagation = true:suggestion
```

### <a name="c-code-style-settings"></a>Paramètres de style de code C#

Les règles de style mentionnées dans cette section s’appliquent uniquement à C#.

#### <a name="implicit-and-explicit-types"></a>Types implicites et explicites

Les règles de style mentionnées dans cette section (ID de règles IDE0007 et IDE0008) concernent l’utilisation du mot clé [var](/dotnet/csharp/language-reference/keywords/var) ou d’un type explicite dans une déclaration de variables. Cette règle peut être appliquée séparément à des types intégrés, quand le type est visible, et ailleurs.

Le tableau suivant indique le nom des règles, les langages de programmation applicables et les valeurs par défaut :

| Nom de la règle | Langages applicables | Valeur par défaut de Visual Studio |
| ----------- | -------------------- | ----------------------|
| csharp_style_var_for_built_in_types | C# | true:none |
| csharp_style_var_when_type_is_apparent | C# | true:none |
| csharp_style_var_elsewhere | C# | true:none |

**csharp\_style\_var\_for\_built\_in_types**

- Quand cette règle est définie sur **true**, il faut faire en sorte d’utiliser `var` pour déclarer des variables avec des types intégrés tels que `int`.
- Quand cette règle est définie sur **false**, il faut faire en sorte d’utiliser un type explicite plutôt que `var` pour déclarer des variables avec des types intégrés tels que `int`.

Exemples de code :

```csharp
// csharp_style_var_for_built_in_types = true
var x = 5;

// csharp_style_var_for_built_in_types = false
int x = 5;
```

**csharp\_style\_var\_when\_type\_is_apparent**

- Quand cette règle est définie sur **true**, il faut faire en sorte d’utiliser `var` quand le type est déjà mentionné dans la partie droite d’une expression de déclaration.
- Quand cette règle est définie sur **false**, il faut faire en sorte d’utiliser `var` quand le type est déjà mentionné dans la partie droite d’une expression de déclaration.

Exemples de code :

```csharp
// csharp_style_var_when_type_is_apparent = true
var obj = new Customer();

// csharp_style_var_when_type_is_apparent = false
Customer obj = new Customer();
```

**csharp\_style\_var_elsewhere**

- Quand cette règle est définie sur **true**, il faut faire en sorte d’utiliser `var` plutôt qu’un type explicite dans tous les cas, sauf substitution par une autre règle de style de code.
- Quand cette règle est définie sur **false**, il faut faire en sorte d’utiliser un type explicite plutôt que `var` dans tous les cas, sauf substitution par une autre règle de style de code.

Exemples de code :

```csharp
// csharp_style_var_elsewhere = true
var f = this.Init();

// csharp_style_var_elsewhere = false
bool f = this.Init();
```

Exemple de fichier *.editorconfig* :

```EditorConfig
# CSharp code style settings:
[*.cs]
csharp_style_var_for_built_in_types = true:suggestion
csharp_style_var_when_type_is_apparent = true:suggestion
csharp_style_var_elsewhere = true:suggestion
```

#### <a name="expression_bodied_members"></a>Membres expression-bodied

Les règles de style mentionnées dans cette section concernent l’utilisation de [membres expression-bodied](/dotnet/csharp/programming-guide/statements-expressions-operators/expression-bodied-members) quand la logique se compose d’une expression unique. Cette règle peut être appliquée à des méthodes, des constructeurs, des opérateurs, des propriétés, des indexeurs et des accesseurs.

Le tableau suivant indique le nom des règles, l’ID des règles, les versions de langage applicables, les valeurs par défaut et la première version de Visual Studio prise en charge :

| Nom de la règle | ID de règle | Langages applicables | Valeur par défaut de Visual Studio | Version de Visual Studio 2017 |
| --------- | ------- | -------------------- | ----------------------| ---------------- |
| csharp_style_expression_bodied_methods | IDE0022 | C# 6.0+ | false:none | 15.3 |
| csharp_style_expression_bodied_constructors | IDE0021 | C# 7.0+ | false:none | 15.3 |
| csharp_style_expression_bodied_operators | IDE0023 et IDE0024 | C# 7.0+ | false:none | 15.3 |
| csharp_style_expression_bodied_properties | IDE0025 | C# 7.0+ | true:none | 15.3 |
| csharp_style_expression_bodied_indexers | IDE0026 | C# 7.0+ | true:none | 15.3 |
| csharp_style_expression_bodied_accessors | IDE0027 | C# 7.0+ | true:none | 15.3 |

**csharp\_style\_expression\_bodied_methods**

Cette règle accepte les valeurs du tableau suivant :

| Value | Description |
| ----- |:----------- |
| true | Préférer les membres expression-bodied pour les méthodes |
| when_on_single_line | Préférer les membres expression-bodied pour les méthodes sur une seule ligne |
| False | Préférer les corps de bloc pour les méthodes |

Exemples de code :

```csharp
// csharp_style_expression_bodied_methods = true
public int GetAge() => this.Age;

// csharp_style_expression_bodied_methods = false
public int GetAge() { return this.Age; }
```

**csharp\_style\_expression\_bodied_constructors**

Cette règle accepte les valeurs du tableau suivant :

| Value | Description |
| ----- |:----------- |
| true | Préférer les membres expression-bodied pour les constructeurs |
| when_on_single_line | Préférer les membres expression-bodied pour les constructeurs sur une seule ligne |
| False | Préférer les corps de bloc pour les constructeurs |

Exemples de code :

```csharp
// csharp_style_expression_bodied_constructors = true
public Customer(int age) => Age = age;

// csharp_style_expression_bodied_constructors = false
public Customer(int age) { Age = age; }
```

**csharp\_style\_expression\_bodied_operators**

Cette règle accepte les valeurs du tableau suivant :

| Value | Description |
| ----- |:----------- |
| true | Préférer les membres expression-bodied pour les opérateurs |
| when_on_single_line | Préférer les membres expression-bodied pour les opérateurs sur une seule ligne |
| False | Préférer les corps de bloc pour les opérateurs |

Exemples de code :

```csharp
// csharp_style_expression_bodied_operators = true
public static ComplexNumber operator + (ComplexNumber c1, ComplexNumber c2)
    => new ComplexNumber(c1.Real + c2.Real, c1.Imaginary + c2.Imaginary);

// csharp_style_expression_bodied_operators = false
public static ComplexNumber operator + (ComplexNumber c1, ComplexNumber c2)
{ return new ComplexNumber(c1.Real + c2.Real, c1.Imaginary + c2.Imaginary); }
```

**csharp\_style\_expression\_bodied_properties**

Cette règle accepte les valeurs du tableau suivant :

| Value | Description |
| ----- |:----------- |
| true | Préférer les membres expression-bodied pour les propriétés |
| when_on_single_line | Préférer les membres expression-bodied pour les propriétés sur une seule ligne |
| False | Préférer les corps de bloc pour les propriétés |

Exemples de code :

```csharp
// csharp_style_expression_bodied_properties = true
public int Age => _age;

// csharp_style_expression_bodied_properties = false
public int Age { get { return _age; }}
```

**csharp\_style\_expression\_bodied_indexers**

Cette règle accepte les valeurs du tableau suivant :

| Value | Description |
| ----- |:----------- |
| true | Préférer les membres expression-bodied pour les indexeurs |
| when_on_single_line | Préférer les membres expression-bodied pour les indexeurs sur une seule ligne |
| False | Préférer les corps de bloc pour les indexeurs |

Exemples de code :

```csharp
// csharp_style_expression_bodied_indexers = true
public T this[int i] => _values[i];

// csharp_style_expression_bodied_indexers = false
public T this[int i] { get { return _values[i]; } }
```

**csharp\_style\_expression\_bodied_accessors**

Cette règle accepte les valeurs du tableau suivant :

| Value | Description |
| ----- |:----------- |
| true | Préférer les membres expression-bodied pour les accesseurs |
| when_on_single_line | Préférer les membres expression-bodied pour les accesseurs sur une seule ligne |
| False | Préférer les corps de bloc pour les accesseurs |

Exemples de code :

```csharp
// csharp_style_expression_bodied_accessors = true
public int Age { get => _age; set => _age = value; }

// csharp_style_expression_bodied_accessors = false
public int Age { get { return _age; } set { _age = value; } }
```

Exemple de fichier *.editorconfig* :

```EditorConfig
# CSharp code style settings:
[*.cs]
csharp_style_expression_bodied_methods = false:none
csharp_style_expression_bodied_constructors = false:none
csharp_style_expression_bodied_operators = false:none
csharp_style_expression_bodied_properties = true:suggestion
csharp_style_expression_bodied_indexers = true:suggestion
csharp_style_expression_bodied_accessors = true:suggestion
```

#### <a name="pattern_matching"></a>Critères spéciaux

Les règles de style mentionnées dans cette section concernent l’utilisation de [critères spéciaux](/dotnet/csharp/pattern-matching) en C#.

Le tableau suivant indique le nom des règles, les ID de règles, les versions de langage applicables et les valeurs par défaut :

| Nom de la règle | ID de règle | Langages applicables | Valeur par défaut de Visual Studio |
| --------- | ------- | -------------------- | ----------------------|
| csharp_style_pattern_matching_over_is_with_cast_check | IDE0020 | C# 7.0+ | true:suggestion |
| csharp_style_pattern_matching_over_as_with_null_check | IDE0019 | C# 7.0+ | true:suggestion |

**csharp\_style\_pattern\_matching\_over\_is\_with\_cast_check**

- Quand cette règle est définie sur **true**, il faut faire en sorte d’utiliser des critères spéciaux plutôt que des expressions `is` avec des casts de type.
- Quand cette règle est définie sur **false**, il faut faire en sorte d’utiliser des expressions `is` avec des casts de type plutôt que des critères spéciaux.

Exemples de code :

```csharp
// csharp_style_pattern_matching_over_is_with_cast_check = true
if (o is int i) {...}

// csharp_style_pattern_matching_over_is_with_cast_check = false
if (o is int) {var i = (int)o; ... }
```

**csharp\_style\_pattern\_matching\_over\_as\_with\_null_check**

- Quand cette règle est définie sur **true**, il faut faire en sorte d’utiliser des critères spéciaux plutôt que des expressions `as` avec contrôles de valeur null pour déterminer si un élément est d’un type particulier.
- Quand cette règle est définie sur **false**, il faut faire en sorte d’utiliser des expressions `as` avec contrôles de valeur null plutôt que des critères spéciaux pour déterminer si un élément est d’un type particulier.

Exemples de code :

```csharp
// csharp_style_pattern_matching_over_as_with_null_check = true
if (o is string s) {...}

// csharp_style_pattern_matching_over_as_with_null_check = false
var s = o as string;
if (s != null) {...}
```

Exemple de fichier *.editorconfig* :

```EditorConfig
# CSharp code style settings:
[*.cs]
csharp_style_pattern_matching_over_is_with_cast_check = true:suggestion
csharp_style_pattern_matching_over_as_with_null_check = true:suggestion
```

#### <a name="inlined_variable_declarations"></a>Déclarations de variables inline

Cette règle de style vise à déterminer si des variables `out` sont déclarées inline ou non. À compter de C# 7, vous pouvez [déclarer une variable out dans la liste d’arguments d’un appel de méthode](/dotnet/csharp/language-reference/keywords/out-parameter-modifier#calling-a-method-with-an-out-argument) au lieu de le faire dans une déclaration de variable distincte.

Le tableau suivant indique le nom de la règle, l’ID de la règle, les versions de langage applicables et les valeurs par défaut :

| Nom de la règle | ID de règle | Langages applicables | Valeur par défaut de Visual Studio |
| --------- | -------- | -------------------- | ----------------------|
| csharp_style_inlined_variable_declaration | IDE0018 | C# 7.0+ | true:suggestion |

**csharp\_style\_inlined\_variable_declaration**

- Quand cette règle est définie sur **true**, il faut faire en sorte de déclarer les variables `out` inline dans la liste d’arguments d’un appel de méthode, dans la mesure du possible.
- Quand cette règle est définie sur **false**, il faut faire en sorte de déclarer les variables `out` avant l’appel de méthode.

Exemples de code :

```csharp
// csharp_style_inlined_variable_declaration = true
if (int.TryParse(value, out int i) {...}

// csharp_style_inlined_variable_declaration = false
int i;
if (int.TryParse(value, out i) {...}
```

Exemple de fichier *.editorconfig* :

```EditorConfig
# CSharp code style settings:
[*.cs]
csharp_style_inlined_variable_declaration = true:suggestion
```

#### <a name="expression_level_csharp"></a>Préférences au niveau des expressions

Les règles de style mentionnées dans cette section concernent les préférences au niveau de l’expression, notamment l’utilisation des [expressions par défaut](/dotnet/csharp/programming-guide/statements-expressions-operators/default-value-expressions#default-literal-and-type-inference), des variables déconstruites et des fonctions locales plutôt que des fonctions anonymes.

Le tableau suivant indique le nom de la règle, l’ID de la règle, les versions de langage applicables, les valeurs par défaut et la première version de Visual Studio prise en charge :

| Nom de la règle | ID de règle | Langages applicables | Valeur par défaut de Visual Studio | Version de Visual Studio 2017 |
| --------- | ------- | -------------------- | ----------------------| ---------------- |
| csharp_prefer_simple_default_expression | IDE0034 | C# 7.1+ | true:suggestion | 15.3 |
| csharp_style_deconstructed_variable_declaration | IDE0042 | C# 7.0+ | true:suggestion | 15.5 |
| csharp_style_pattern_local_over_anonymous_function | IDE0039 | C# 7.0+ | true:suggestion | 15.5 |

**csharp\_prefer\_simple\_default_expression**

Cette règle de style concerne l’utilisation du [littéral `default` pour les expressions de valeur par défaut](/dotnet/csharp/programming-guide/statements-expressions-operators/default-value-expressions#default-literal-and-type-inference) quand le compilateur peut déduire le type de l’expression.

- Quand cette règle est définie sur **true**, il faut faire en sorte d’utiliser `default` plutôt que `default(T)`.
- Quand cette règle est définie sur **false**, il faut faire en sorte d’utiliser `default(T)` plutôt que `default`.

Exemples de code :

```csharp
// csharp_prefer_simple_default_expression = true
void DoWork(CancellationToken cancellationToken = default) { ... }

// csharp_prefer_simple_default_expression = false
void DoWork(CancellationToken cancellationToken = default(CancellationToken)) { ... }
```

**csharp\_style\_deconstructed\_variable_declaration**

- Quand cette règle est définie sur **true**, préférer la déclaration de variables déconstruites.
- Quand cette règle est définie sur **false**, ne pas préférer la déclaration de variables déconstruites.

Exemples de code :

```csharp
// csharp_style_deconstructed_variable_declaration = true
var (name, age) = GetPersonTuple();
Console.WriteLine($"{name} {age}");

(int x, int y) = GetPointTuple();
Console.WriteLine($"{x} {y}");

// csharp_style_deconstructed_variable_declaration = false
var person = GetPersonTuple();
Console.WriteLine($"{person.name} {person.age}");

(int x, int y) point = GetPointTuple();
Console.WriteLine($"{point.x} {point.y}");
```

**csharp\_style\_pattern\_local\_over\_anonymous_function**

- Quand cette règle est définie sur **true**, préférer les fonctions locales aux fonctions anonymes.
- Quand cette règle est définie sur **false**, préférer les fonctions anonymes aux fonctions locales.

Exemples de code :

```csharp
// csharp_style_pattern_local_over_anonymous_function = true
int fibonacci(int n)
{
    return n <= 1 ? 1 : fibonacci(n-1) + fibonacci(n-2);
}

// csharp_style_pattern_local_over_anonymous_function = false
Func<int, int> fibonacci = null;
fibonacci = (int n) =>
{
    return n <= 1 ? 1 : fibonacci(n - 1) + fibonacci(n - 2);
};
```

Exemple de fichier *.editorconfig* :

```EditorConfig
# CSharp code style settings:
[*.cs]
csharp_prefer_simple_default_expression = true:suggestion
csharp_style_deconstructed_variable_declaration = true:suggestion
csharp_style_pattern_local_over_anonymous_function = true:suggestion
```

#### <a name="null_checking_csharp"></a>Préférences de vérification des valeurs « Null »

Ces règles de style concernent la syntaxe autour de la vérification de valeur `null`, notamment l’utilisation d’expressions `throw` ou d’instructions `throw`, et s’il convient d’effectuer, ou non, une vérification de valeur null ou d’utiliser l’opérateur de fusion conditionnelle (`?.`) lors de l’appel d’une [expression lambda](/dotnet/csharp/lambda-expressions).

Le tableau suivant indique le nom des règles, les ID de règles, les versions de langage applicables et les valeurs par défaut :

| Nom de la règle | ID de règle | Langages applicables | Valeur par défaut de Visual Studio |
| --------- | ------- | -------------------- | ----------------------|
| csharp_style_throw_expression | IDE0016 | C# 7.0+ | true:suggestion |
| csharp_style_conditional_delegate_call | IDE0041 | C# 6.0+ | true:suggestion |

**csharp\_style\_throw_expression**

- Quand cette règle est définie sur **true**, il faut faire en sorte d’utiliser des expressions `throw` plutôt que des instructions `throw`.
- Quand cette règle est définie sur **false**, il faut faire en sorte d’utiliser des instructions `throw` plutôt que des expressions `throw`.

Exemples de code :

```csharp
// csharp_style_throw_expression = true
this.s = s ?? throw new ArgumentNullException(nameof(s));

// csharp_style_throw_expression = false
if (s == null) { throw new ArgumentNullException(nameof(s)); }
this.s = s;
```

**csharp\_style\_conditional\_delegate_call**

- Quand cette règle est définie sur **true**, il faut faire en sorte d’utiliser l’opérateur de fusion conditionnelle (`?.`) lors de l’appel d’une expression lambda, plutôt que d’effectuer une vérification de valeur null.
- Quand cette règle est définie sur **false**, il faut faire en sorte d’effectuer une vérification de valeur null avant d’appeler une expression lambda, plutôt que d’utiliser l’opérateur de fusion conditionnelle (`?.`).

Exemples de code :

```csharp
// csharp_style_conditional_delegate_call = true
func?.Invoke(args);

// csharp_style_conditional_delegate_call = false
if (func != null) { func(args); }
```

Exemple de fichier *.editorconfig* :

```EditorConfig
# CSharp code style settings:
[*.cs]
csharp_style_throw_expression = true:suggestion
csharp_style_conditional_delegate_call = false:suggestion
```

#### <a name="code_block"></a>Préférences des blocs de code

Cette règle de style concerne l’utilisation d’accolades `{ }` pour entourer les blocs de code.

Le tableau suivant indique le nom de la règle, l’ID de la règle, les versions de langage applicables, les valeurs par défaut et la première version de Visual Studio prise en charge :

| Nom de la règle | ID de règle | Langages applicables | Valeur par défaut de Visual Studio | Version de Visual Studio 2017 |
| --------- | ------- | -------------------- | ----------------------| ---------------- |
| csharp_prefer_braces | IDE0011 | C# | true:none | 15.3 |

**csharp\_prefer\_braces**

- Quand cette règle est définie sur **true**, il faut faire en sorte d’utiliser des accolades même pour une seule ligne de code.
- Quand cette règle est définie sur **false**, il faut faire en sorte de ne pas utiliser d’accolades, si c’est autorisé.

Exemples de code :

```csharp
// csharp_prefer_braces = true
if (test) { this.Display(); }

// csharp_prefer_braces = false
if (test) this.Display();
```

Exemple de fichier *.editorconfig* :

```EditorConfig
# CSharp code style settings:
[*.cs]
csharp_prefer_braces = true:none
```

## <a name="formatting-conventions"></a>Conventions de mise en forme

La plupart des règles pour les conventions de mise en forme ont le format suivant :

`rule_name = false|true`

Vous spécifiez **true** (préférer ce style) ou **false** (ne pas préférer ce style). Vous ne spécifiez pas de niveau de gravité. Pour certaines règles, au lieu de true ou de false, vous spécifiez d’autres valeurs pour décrire quand et où appliquer la règle.

La liste suivante présente les règles de conventions de mise en forme disponibles dans Visual Studio :

- Paramètres de mise en forme .NET
    - [Organiser les instructions using](#usings)
        - dotnet_sort_system_directives_first
        - dotnet_separate_import_directive_groups
- Paramètres de mise en forme C#
    - [Options de saut de ligne](#newline)
        - csharp_new_line_before_open_brace
        - csharp_new_line_before_else
        - csharp_new_line_before_catch
        - csharp_new_line_before_finally
        - csharp_new_line_before_members_in_object_initializers
        - csharp_new_line_before_members_in_anonymous_types
        - csharp_new_line_between_query_expression_clauses
    - [Options de mise en retrait](#indent)
        - csharp_indent_case_contents
        - csharp_indent_switch_labels
        - csharp_indent_labels
    - [Options d’espacement](#spacing)
        - csharp_space_after_cast
        - csharp_space_after_keywords_in_control_flow_statements
        - csharp_space_between_method_declaration_parameter_list_parentheses
        - csharp_space_between_method_call_parameter_list_parentheses
        - csharp_space_between_parentheses
        - csharp_space_before_colon_in_inheritance_clause
        - csharp_space_after_colon_in_inheritance_clause
        - csharp_space_around_binary_operators
        - csharp_space_between_method_declaration_empty_parameter_list_parentheses
        - csharp_space_between_method_call_name_and_opening_parenthesis
        - csharp_space_between_method_call_empty_parameter_list_parentheses
    - [Options d’inclusion dans un wrapper](#wrapping)
        - csharp_preserve_single_line_statements
        - csharp_preserve_single_line_blocks

### <a name="net-formatting-settings"></a>Paramètres de mise en forme .NET

Les règles de mise en forme mentionnées dans cette section s’appliquent aux langages C# et Visual Basic.

#### <a name="usings"></a>Organiser les directives using

Cette règle de mise en forme concerne l’emplacement des directives using System.* par rapport aux autres directives using.

Le tableau suivant indique le nom de la règle, les langages applicables, la valeur par défaut et la première version de Visual Studio prise en charge :

| Nom de la règle | Langages applicables | Valeur par défaut de Visual Studio | Version de Visual Studio 2017 |
| ----------- | -------------------- | ----------------------| ---------------- |
| dotnet_sort_system_directives_first | C# et Visual Basic | true | 15.3 |
| dotnet_separate_import_directive_groups | C# et Visual Basic | False | 15.5 |

**dotnet\_sort\_system\_directives_first**

- Quand cette règle est définie sur **true**, triez les directives using System.* par ordre alphabétique et placez-les avant les autres directives using.
- Quand cette règle est définie sur **false**, ne placez pas de directives using System.* avant les autres directives using.

Exemples de code :

```csharp
// dotnet_sort_system_directives_first = true
using System.Collections.Generic;
using System.Threading.Tasks;
using Octokit;

// dotnet_sort_system_directives_first = false
using System.Collections.Generic;
using Octokit;
using System.Threading.Tasks;
```

Exemple de fichier *.editorconfig* :

```EditorConfig
# .NET formatting settings:
[*.{cs,vb}]
dotnet_sort_system_directives_first = true
```

**dotnet\_separate\_import\_directive\_groups**

- Quand cette règle est définie sur **true**, placez une ligne vide entre les groupes de directives using.
- Quand cette règle est définie sur **false**, ne placez pas de ligne vide entre les groupes de directives using.

Exemples de code :

```csharp
// dotnet_separate_import_directive_groups = true
using System.Collections.Generic;
using System.Threading.Tasks;

using Octokit;

// dotnet_separate_import_directive_groups = false
using System.Collections.Generic;
using System.Threading.Tasks;
using Octokit;
```

Exemple de fichier *.editorconfig* :

```EditorConfig
# .NET formatting settings:
[*.{cs,vb}]
dotnet_separate_import_directive_groups = true
```

### <a name="c-formatting-settings"></a>Paramètres de mise en forme C#

Les règles de mise en forme mentionnées dans cette section s’appliquent uniquement au code C#.

#### <a name="newline"></a>Options de saut de ligne

Ces règles de mise en forme concernent l’utilisation de nouvelles lignes pour mettre en forme du code.

Le tableau suivant indique le nom des règles de "nouvelles lignes", les langages applicables, les valeurs par défaut et la première version de Visual Studio prise en charge :

| Nom de la règle | Langages applicables | Valeur par défaut de Visual Studio | Version de Visual Studio 2017 |
| ----------- | -------------------- | ----------------------| ---------------- |
| csharp_new_line_before_open_brace | C# | all | 15.3 |
| csharp_new_line_before_else | C# | true | 15.3 |
| csharp_new_line_before_catch | C# | true | 15.3 |
| csharp_new_line_before_finally | C# | true | 15.3 |
| csharp_new_line_before_members_in_object_initializers | C# | true | 15.3 |
| csharp_new_line_before_members_in_anonymous_types | C# | true | 15.3 |
| csharp_new_line_between_query_expression_clauses | C# | true | 15.3 |

**csharp\_new\_line\_before\_open_brace**

Cette règle vise à déterminer si une accolade ouvrante `{` doit être placée sur la même ligne que le code précédent, ou sur une nouvelle ligne. Pour cette règle, vous ne spécifiez pas **true** ou **false**. Vous spécifiez à la place **all**, **none**, ou un ou plusieurs éléments de code tels que **methods** ou **proprerties**, pour définir quand cette règle doit être appliquée. La liste complète des valeurs autorisées est présentée dans le tableau suivant :

| Value | Description
| ------------- |:-------------|
| accessors, anonymous_methods, anonymous_types, control_blocks, events, indexers, lambdas, local_functions, methods, object_collection_array_initializers, properties, types.<br>(Pour indiquer plusieurs genres, séparez-les par ','). | Les accolades doivent se trouver sur une nouvelle ligne pour les éléments de code spécifiés (également appelé style « Allman ») |
| all | Les accolades doivent se trouver sur une nouvelle ligne pour toutes les expressions (style "Allman") |
| none | Les accolades doivent se trouver sur la même ligne pour toutes les expressions ("K&R") |

Exemples de code :

```csharp
// csharp_new_line_before_open_brace = all
void MyMethod()
{
    if (...)
    {
        ...
    }
}

// csharp_new_line_before_open_brace = none
void MyMethod() {
    if (...) {
        ...
    }
}
```

**csharp\_new\_line\_before_else**

- Quand cette règle est définie sur **true**, placez les instructions `else` sur une nouvelle ligne.
- Quand cette règle est définie sur **false**, placez les instructions `else` sur la même ligne.

Exemples de code :

```csharp
// csharp_new_line_before_else = true
if (...) {
    ...
}
else {
    ...
}

// csharp_new_line_before_else = false
if (...) {
    ...
} else {
    ...
}
```

**csharp\_new\_line\_before_catch**

- Quand cette règle est définie sur **true**, placez les instructions `catch` sur une nouvelle ligne.
- Quand cette règle est définie sur **false**, placez les instructions `catch` sur la même ligne.

Exemples de code :

```csharp
// csharp_new_line_before_catch = true
try {
    ...
}
catch (Exception e) {
    ...
}

// csharp_new_line_before_catch = false
try {
    ...
} catch (Exception e) {
    ...
}
```

**csharp\_new\_line\_before_finally**

- Quand cette règle est définie sur **true**, les instructions `finally` doivent se trouver sur une nouvelle ligne après l’accolade fermante.
- Quand cette règle est définie sur **false**, les instructions `finally` doivent se trouver sur la même ligne que l’accolade fermante.

Exemples de code :

```csharp
// csharp_new_line_before_finally = true
try {
    ...
}
catch (Exception e) {
    ...
}
finally {
    ...
}

// csharp_new_line_before_finally = false
try {
    ...
} catch (Exception e) {
    ...
} finally {
    ...
}
```

**csharp\_new\_line\_before\_members\_in\_object_initializers**

- Quand cette règle est définie sur **true**, les membres des initialiseurs d’objets doivent se trouver sur des lignes distinctes.
- Quand cette règle est définie sur **false**, les membres des initialiseurs d’objet doivent se trouver sur la même ligne.

Exemples de code :

```csharp
// csharp_new_line_before_members_in_object_initializers = true
var z = new B()
{
    A = 3,
    B = 4
}

// csharp_new_line_before_members_in_object_initializers = false
var z = new B()
{
    A = 3, B = 4
}
```

**csharp\_new\_line\_before\_members\_in\_anonymous_types**

- Quand cette règle est définie sur **true**, les membres des types anonymes doivent se trouver sur des lignes distinctes.
- Quand cette règle est définie sur **false**, les membres des types anonymes doivent se trouver sur la même ligne.

Exemples de code :

```csharp
// csharp_new_line_before_members_in_anonymous_types = true
var z = new
{
    A = 3,
    B = 4
}

// csharp_new_line_before_members_in_anonymous_types = false
var z = new
{
    A = 3, B = 4
}
```

**csharp_new_line_between_query_expression_clauses**

- Quand cette règle est définie sur **true**, les éléments des clauses d’expression de requête doivent se trouver sur des lignes distinctes.
- Quand cette règle est définie sur **false**, les éléments des clauses d’expression de requête doivent se trouver sur la même ligne.

Exemples de code :

```csharp
// csharp_new_line_between_query_expression_clauses = true
var q = from a in e
        from b in e
        select a * b;

// csharp_new_line_between_query_expression_clauses = false
var q = from a in e from b in e
        select a * b;
```

Exemple de fichier *.editorconfig* :

```EditorConfig
# CSharp formatting settings:
[*.cs]
csharp_new_line_before_open_brace = methods, properties, control_blocks, types
csharp_new_line_before_else = true
csharp_new_line_before_catch = true
csharp_new_line_before_finally = true
csharp_new_line_before_members_in_object_initializers = true
csharp_new_line_before_members_in_anonymous_types = true
csharp_new_line_between_query_expression_clauses = true
```

#### <a name="indent"></a>Options d’indentation

Ces règles de mise en forme concernent l’utilisation de l’indentation pour mettre en forme du code.

Le tableau suivant indique le nom des règles, les langages applicables, les valeurs par défaut et la première version de Visual Studio prise en charge :

| Nom de la règle | Langages applicables | Valeur par défaut de Visual Studio | Version de Visual Studio 2017 |
| ----------- | -------------------- | ----------------------| ---------------- |
| csharp_indent_case_contents | C# | true | 15.3 |
| csharp_indent_switch_labels | C# | true | 15.3 |
| csharp_indent_labels | C# | no_change | 15.3 |

**csharp\_indent\_case_contents**

- Quand cette règle est définie sur **true**, il faut mettre en retrait le contenu de case `switch`.
- Quand cette règle est définie sur **false**, il ne faut pas mettre en retrait le contenu de case `switch`.

Exemples de code :

```csharp
// csharp_indent_case_contents = true
switch(c) {
    case Color.Red:
        Console.WriteLine("The color is red");
        break;
    case Color.Blue:
        Console.WriteLine("The color is blue");
        break;
    default:
        Console.WriteLine("The color is unknown.");
        break;
}

// csharp_indent_case_contents = false
switch(c) {
    case Color.Red:
    Console.WriteLine("The color is red");
    break;
    case Color.Blue:
    Console.WriteLine("The color is blue");
    break;
    default:
    Console.WriteLine("The color is unknown.");
    break;
}
```

**csharp\_indent\_switch_labels**

- Quand cette règle est définie sur **true**, il faut mettre en retrait les étiquettes `switch`.
- Quand cette règle est définie sur **false**, il ne faut pas mettre en retrait les étiquettes `switch`.

Exemples de code :

```csharp
// csharp_indent_switch_labels = true
switch(c) {
    case Color.Red:
        Console.WriteLine("The color is red");
        break;
    case Color.Blue:
        Console.WriteLine("The color is blue");
        break;
    default:
        Console.WriteLine("The color is unknown.");
        break;
}

// csharp_indent_switch_labels = false
switch(c) {
case Color.Red:
    Console.WriteLine("The color is red");
    break;
case Color.Blue:
    Console.WriteLine("The color is blue");
    break;
default:
    Console.WriteLine("The color is unknown.");
    break;
}
```

**csharp\_indent_labels**

Cette règle n’accepte pas une valeur **true** ou **false**, elle accepte à la place une valeur du tableau suivant :

| Value | Description |
| ----- |:----------- |
| flush_left | Les étiquettes sont positionnées au niveau de la colonne la plus à gauche |
| one_less_than_current | Les étiquettes sont positionnées d’un retrait à gauche par rapport au contexte actuel |
| no_change | Les étiquettes sont placées au même niveau de retrait que le contexte actuel |

Exemples de code :

```csharp
// csharp_indent_labels= flush_left
class C
{
    private string MyMethod(...)
    {
        if (...) {
            goto error;
        }
error:
        throw new Exception(...);
    }
}

// csharp_indent_labels = one_less_than_current
class C
{
    private string MyMethod(...)
    {
        if (...) {
            goto error;
        }
    error:
        throw new Exception(...);
    }
}

// csharp_indent_labels= no_change
class C
{
    private string MyMethod(...)
    {
        if (...) {
            goto error;
        }
        error:
        throw new Exception(...);
    }
}
```

Exemple de fichier *.editorconfig* :

```EditorConfig
# CSharp formatting settings:
[*.cs]
csharp_indent_case_contents = true
csharp_indent_switch_labels = true
csharp_indent_labels = flush_left
```

#### <a name="spacing"></a>Options d’espacement

Ces règles de mise en forme concernent l’utilisation de caractères d’espacement pour mettre en forme du code.

Le tableau suivant indique le nom des règles, les langages applicables, les valeurs par défaut et la première version de Visual Studio prise en charge :

| Nom de la règle | Langages applicables | Valeur par défaut de Visual Studio | Version de Visual Studio 2017 |
| ----------- | -------------------- | ----------------------| ---------------- |
| csharp_space_after_cast | C# | False | 15.3 |
| csharp_space_after_keywords_in_control_flow_statements | C# | true | 15.3 |
| csharp_space_between_method_declaration_parameter_list_parentheses | C# | False | 15.3 |
| csharp_space_between_method_call_parameter_list_parentheses | C# | False | 15.3 |
| csharp_space_between_parentheses | C# | False | 15.3 |
| csharp_space_before_colon_in_inheritance_clause | C# | true | 15.7 |
| csharp_space_after_colon_in_inheritance_clause | C# | true | 15.7 |
| csharp_space_around_binary_operators | C# | before_and_after | 15.7 |
| csharp_space_between_method_declaration_empty_parameter_list_parentheses | C# | False | 15.7 |
| csharp_space_between_method_call_name_and_opening_parenthesis | C# | False | 15.7 |
| csharp_space_between_method_call_empty_parameter_list_parentheses | C# | False | 15.7 |

**csharp\_space\_after_cast**

- Quand cette règle est définie sur **true**, un espace doit figurer entre un cast et la valeur.
- Quand cette règle est définie sur **false**, _aucun_ espace ne doit figurer entre le cast et la valeur.

Exemples de code :

```csharp
// csharp_space_after_cast = true
int y = (int) x;

// csharp_space_after_cast = false
int y = (int)x;
```

**csharp_space_after_keywords_in_control_flow_statements**

- Quand cette règle est définie sur **true**, un espace est nécessaire après un mot clé dans une instruction de flux de contrôle telle qu’une boucle `for`.
- Quand cette règle est définie sur **false**, _aucun_ espace n’est nécessaire après un mot clé dans une instruction de flux de contrôle telle qu’une boucle `for`.

Exemples de code :

```csharp
// csharp_space_after_keywords_in_control_flow_statements = true
for (int i;i<x;i++) { ... }

// csharp_space_after_keywords_in_control_flow_statements = false
for(int i;i<x;i++) { ... }
```

**csharp_space_between_method_declaration_parameter_list_parentheses**

- Quand cette règle est définie sur **true**, placez un espace après la parenthèse ouvrante et avant la parenthèse fermante d’une liste de paramètres de déclaration de méthode.
- Quand cette règle est définie sur **false**, ne placez pas d’espace après la parenthèse ouvrante et avant la parenthèse fermante d’une liste de paramètres de déclaration de méthode.

Exemples de code :

```csharp
// csharp_space_between_method_declaration_parameter_list_parentheses = true
void Bark( int x ) { ... }

// csharp_space_between_method_declaration_parameter_list_parentheses = false
void Bark(int x) { ... }
```

**csharp_space_between_method_call_parameter_list_parentheses**

- Quand cette règle est définie sur **true**, placez un caractère d’espacement après la parenthèse ouvrante et avant la parenthèse fermante d’un appel de méthode.
- Quand cette règle est définie sur **false**, ne placez pas de caractères d’espacement après la parenthèse ouvrante et avant la parenthèse fermante d’un appel de méthode.

Exemples de code :

```csharp
// csharp_space_between_method_call_parameter_list_parentheses = true
MyMethod( argument );

// csharp_space_between_method_call_parameter_list_parentheses = false
MyMethod(argument);
```

**csharp_space_between_parentheses**

Cette règle accepte une ou plusieurs valeurs du tableau suivant :

| Value | Description |
| ----- |:------------|
| control_flow_statements | Placer un espace entre les parenthèses d’instructions de flux de contrôle |
| expressions | Placer un espace entre les parenthèses d’expressions |
| type_casts | Placer un espace entre les parenthèses dans les casts de type |

Si vous omettez cette règle, ou si vous utilisez une valeur autre que `control_flow_statements`, `expressions` ou `type_casts`, le paramètre n’est pas appliqué.

Exemples de code :

```csharp
// csharp_space_between_parentheses = control_flow_statements
for ( int i = 0; i < 10; i++ ) { }

// csharp_space_between_parentheses = expressions
var z = ( x * y ) - ( ( y - x ) * 3 );

// csharp_space_between_parentheses = type_casts
int y = ( int )x;
```

**csharp\_space\_before\_colon\_in\_inheritance_clause**

- Quand cette règle est définie sur **true**, exiger un espace avant le signe deux-points pour les bases ou les interfaces dans une déclaration de type.
- Quand cette règle est définie sur **false**, ne _pas_ exiger d’espace avant le signe deux-points pour les bases ou les interfaces dans une déclaration de type.

Exemples de code :

```csharp
// csharp_space_before_colon_in_inheritance_clause = true
interface I
{

}

class C : I
{

}

// csharp_space_before_colon_in_inheritance_clause = false
interface I
{

}

class C: I
{

}
```

**csharp\_space\_after\_colon\_in\_inheritance_clause**

- Quand cette règle est définie sur **true**, exiger un espace après le signe deux-points pour les bases ou les interfaces dans une déclaration de type.
- Quand cette règle est définie sur **false**, ne _pas_ exiger d’espace après le signe deux-points pour les bases ou les interfaces dans une déclaration de type.

Exemples de code :

```csharp
// csharp_space_after_colon_in_inheritance_clause = true
interface I
{

}

class C : I
{

}

// csharp_space_after_colon_in_inheritance_clause = false
interface I
{

}

class C :I
{

}
```

**csharp\_space\_around\_binary_operators**

Cette règle accepte une valeur du tableau suivant :

| Value | Description |
| ----- |:------------|
| before_and_after | Insérer un espace avant et après l’opérateur binaire |
| none | Supprimer les espaces avant et après l’opérateur binaire |
| ignorer | Ignorer les espaces autour des opérateurs binaires |

Si vous omettez cette règle, ou si vous utilisez une valeur autre que `before_and_after`, `none` ou `ignore`, le paramètre n’est pas appliqué.

Exemples de code :

```csharp
// csharp_space_around_binary_operators = before_and_after
return x * (x - y);

// csharp_space_around_binary_operators = none
return x*(x-y);

// csharp_space_around_binary_operators = ignore
return x  *  (x-y);
```

**csharp_space_between_method_declaration_empty_parameter_list_parentheses**

- Quand cette règle est définie sur **true**, insérer un espace dans les parenthèses de liste de paramètres vides pour une déclaration de méthode.
- Quand cette règle est définie sur **false**, supprimer l’espace dans les parenthèses de liste de paramètres vides pour une déclaration de méthode.

Exemples de code :

```csharp
// csharp_space_between_method_declaration_empty_parameter_list_parentheses = true
void Goo( )
{
    Goo(1);
}

void Goo(int x)
{
    Goo();
}

// csharp_space_between_method_declaration_empty_parameter_list_parentheses = false
void Goo()
{
    Goo(1);
}

void Goo(int x)
{
    Goo();
}
```

**csharp_space_between_method_call_name_and_opening_parenthesis**

- Quand cette règle est définie sur **true**, insérer un espace entre le nom d’appel de méthode et la parenthèse ouvrante.
- Quand cette règle est définie sur **false**, supprimer l’espace entre le nom d’appel de méthode et la parenthèse ouvrante.

Exemples de code :

```csharp
// csharp_space_between_method_call_name_and_opening_parenthesis = true
void Goo()
{
    Goo (1);
}

void Goo(int x)
{
    Goo ();
}

// csharp_space_between_method_call_name_and_opening_parenthesis = false
void Goo()
{
    Goo(1);
}

void Goo(int x)
{
    Goo();
}
```

**csharp_space_between_method_call_empty_parameter_list_parentheses**

- Quand cette règle est définie sur **true**, insérer un espace dans les parenthèses de liste d’arguments vides.
- Quand cette règle est définie sur **false**, supprimer l’espace dans les parenthèses de liste d’arguments vides.

Exemples de code :

```csharp
// csharp_space_between_method_call_empty_parameter_list_parentheses = true
void Goo()
{
    Goo(1);
}

void Goo(int x)
{
    Goo( );
}

// csharp_space_between_method_call_empty_parameter_list_parentheses = false
void Goo()
{
    Goo(1);
}

void Goo(int x)
{
    Goo();
}
```

Exemple de fichier *.editorconfig* :

```EditorConfig
# CSharp formatting settings:
[*.cs]
csharp_space_after_cast = true
csharp_space_after_keywords_in_control_flow_statements = true
csharp_space_between_method_declaration_parameter_list_parentheses = true
csharp_space_between_method_call_parameter_list_parentheses = true
csharp_space_between_parentheses = control_flow_statements, type_casts
csharp_space_before_colon_in_inheritance_clause = true
csharp_space_after_colon_in_inheritance_clause = true
csharp_space_around_binary_operators = before_and_after
csharp_space_between_method_declaration_empty_parameter_list_parentheses = false
csharp_space_between_method_call_name_and_opening_parenthesis = false
csharp_space_between_method_call_empty_parameter_list_parentheses = false
```

#### <a name="wrapping"></a>Options de wrapping

Ces règles de mise en forme concernent l’utilisation de lignes uniques ou de lignes distinctes pour les instructions et les blocs de code.

Le tableau suivant indique le nom des règles, les langages applicables, les valeurs par défaut et la première version de Visual Studio prise en charge :

| Nom de la règle | Langages applicables | Valeur par défaut de Visual Studio | Version de Visual Studio 2017 |
| ----------- | -------------------- | ----------------------| ---------------- |
| csharp_preserve_single_line_statements | C# | true | 15.3 |
| csharp_preserve_single_line_blocks | C# | true | 15.3 |

**csharp_preserve_single_line_statements**

- Quand cette règle est définie sur **true**, laissez les instructions et les déclarations de membre sur la même ligne.
- Quand cette règle est définie sur **false**, laissez les instructions et les déclarations de membre sur des lignes distinctes.

Exemples de code :

```csharp
//csharp_preserve_single_line_statements = true
int i = 0; string name = "John";

//csharp_preserve_single_line_statements = false
int i = 0;
string name = "John";
```

**csharp_preserve_single_line_blocks**

- Quand cette règle est définie sur **true**, laissez un bloc de code sur une ligne unique.
- Quand cette règle est définie sur **false**, laissez un bloc de code sur des lignes distinctes.

Exemples de code :

```csharp
//csharp_preserve_single_line_blocks = true
public int Foo { get; set; }

//csharp_preserve_single_line_blocks = false
public int MyProperty
{
    get; set;
}
```

Exemple de fichier *.editorconfig* :

```EditorConfig
# CSharp formatting settings:
[*.cs]
csharp_preserve_single_line_statements = true
csharp_preserve_single_line_blocks = true
```

## <a name="example-editorconfig-file"></a>Exemple de fichier EditorConfig

Pour vous aider à commencer, voici un exemple de fichier *.editorconfig* avec les options par défaut :

```EditorConfig
###############################
# Core EditorConfig Options   #
###############################

root = true

# All files
[*]
indent_style = space

# Code files
[*.{cs,csx,vb,vbx}]
indent_size = 4
insert_final_newline = true
charset = utf-8-bom

###############################
# .NET Coding Conventions     #
###############################

[*.{cs,vb}]
# Organize usings
dotnet_sort_system_directives_first = true
dotnet_separate_import_directive_groups = false

# this. preferences
dotnet_style_qualification_for_field = false:none
dotnet_style_qualification_for_property = false:none
dotnet_style_qualification_for_method = false:none
dotnet_style_qualification_for_event = false:none

# Language keywords vs BCL types preferences
dotnet_style_predefined_type_for_locals_parameters_members = true:none
dotnet_style_predefined_type_for_member_access = true:none

# Parentheses preferences
dotnet_style_parentheses_in_arithmetic_binary_operators = always_for_clarity:silent
dotnet_style_parentheses_in_relational_binary_operators = always_for_clarity:silent
dotnet_style_parentheses_in_other_binary_operators = always_for_clarity:silent
dotnet_style_parentheses_in_other_operators = never_if_unnecessary:silent

# Modifier preferences
dotnet_style_require_accessibility_modifiers = for_non_interface_members:none
dotnet_style_readonly_field = true:suggestion

# Expression-level preferences
dotnet_style_object_initializer = true:suggestion
dotnet_style_collection_initializer = true:suggestion
dotnet_style_explicit_tuple_names = true:suggestion
dotnet_style_null_propagation = true:suggestion
dotnet_style_coalesce_expression = true:suggestion
dotnet_style_prefer_is_null_check_over_reference_equality_method = true:silent
dotnet_style_prefer_inferred_tuple_names = true:suggestion
dotnet_style_prefer_inferred_anonymous_type_member_names = true:suggestion
dotnet_style_prefer_auto_properties = true:silent
dotnet_style_prefer_conditional_expression_over_assignment = true:silent
dotnet_style_prefer_conditional_expression_over_return = true:silent

###############################
# Naming Conventions          #
###############################

# Style Definitions
dotnet_naming_style.pascal_case_style.capitalization             = pascal_case

# Use PascalCase for constant fields
dotnet_naming_rule.constant_fields_should_be_pascal_case.severity = suggestion
dotnet_naming_rule.constant_fields_should_be_pascal_case.symbols  = constant_fields
dotnet_naming_rule.constant_fields_should_be_pascal_case.style    = pascal_case_style
dotnet_naming_symbols.constant_fields.applicable_kinds            = field
dotnet_naming_symbols.constant_fields.applicable_accessibilities  = *
dotnet_naming_symbols.constant_fields.required_modifiers          = const

###############################
# C# Code Style Rules         #
###############################

[*.cs]
# var preferences
csharp_style_var_for_built_in_types = true:none
csharp_style_var_when_type_is_apparent = true:none
csharp_style_var_elsewhere = true:none

# Expression-bodied members
csharp_style_expression_bodied_methods = false:none
csharp_style_expression_bodied_constructors = false:none
csharp_style_expression_bodied_operators = false:none
csharp_style_expression_bodied_properties = true:none
csharp_style_expression_bodied_indexers = true:none
csharp_style_expression_bodied_accessors = true:none

# Pattern-matching preferences
csharp_style_pattern_matching_over_is_with_cast_check = true:suggestion
csharp_style_pattern_matching_over_as_with_null_check = true:suggestion

# Null-checking preferences
csharp_style_throw_expression = true:suggestion
csharp_style_conditional_delegate_call = true:suggestion

# Modifier preferences
csharp_preferred_modifier_order = public,private,protected,internal,static,extern,new,virtual,abstract,sealed,override,readonly,unsafe,volatile,async:suggestion

# Expression-level preferences
csharp_prefer_braces = true:none
csharp_style_deconstructed_variable_declaration = true:suggestion
csharp_prefer_simple_default_expression = true:suggestion
csharp_style_pattern_local_over_anonymous_function = true:suggestion
csharp_style_inlined_variable_declaration = true:suggestion

###############################
# C# Formatting Rules         #
###############################

# New line preferences
csharp_new_line_before_open_brace = all
csharp_new_line_before_else = true
csharp_new_line_before_catch = true
csharp_new_line_before_finally = true
csharp_new_line_before_members_in_object_initializers = true
csharp_new_line_before_members_in_anonymous_types = true
csharp_new_line_between_query_expression_clauses = true

# Indentation preferences
csharp_indent_case_contents = true
csharp_indent_switch_labels = true
csharp_indent_labels = flush_left

# Space preferences
csharp_space_after_cast = false
csharp_space_after_keywords_in_control_flow_statements = true
csharp_space_between_method_call_parameter_list_parentheses = false
csharp_space_between_method_declaration_parameter_list_parentheses = false
csharp_space_between_parentheses = false
csharp_space_before_colon_in_inheritance_clause = true
csharp_space_after_colon_in_inheritance_clause = true
csharp_space_around_binary_operators = before_and_after
csharp_space_between_method_declaration_empty_parameter_list_parentheses = false
csharp_space_between_method_call_name_and_opening_parenthesis = false
csharp_space_between_method_call_empty_parameter_list_parentheses = false

# Wrapping preferences
csharp_preserve_single_line_statements = true
csharp_preserve_single_line_blocks = true

##################################
# Visual Basic Code Style Rules  #
##################################

[*.vb]
# Modifier preferences
visual_basic_preferred_modifier_order = Partial,Default,Private,Protected,Public,Friend,NotOverridable,Overridable,MustOverride,Overloads,Overrides,MustInherit,NotInheritable,Static,Shared,Shadows,ReadOnly,WriteOnly,Dim,Const,WithEvents,Widening,Narrowing,Custom,Async:suggestion
```

## <a name="see-also"></a>Voir aussi

- [Actions rapides](../ide/quick-actions.md)
- [Conventions de nommage .NET pour EditorConfig](../ide/editorconfig-naming-conventions.md)
- [Créer des options d’éditeur personnalisées et portables](../ide/create-portable-custom-editor-options.md)
- [Fichier .editorconfig de .NET Compiler Platform](https://github.com/dotnet/roslyn/blob/master/.editorconfig)
