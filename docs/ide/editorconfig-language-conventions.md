---
title: Conventions du langage .NET pour EditorConfig
ms.date: 07/17/2019
ms.topic: reference
dev_langs:
- CSharp
- VB
helpviewer_keywords:
- language code style rules [EditorConfig]
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 7b88824e6be7dbb216aa14ca9a22fd692474ec2f
ms.sourcegitcommit: a124076dfd6b4e5aecda4d01984fee7b0c034745
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2019
ms.locfileid: "68787422"
---
# <a name="language-conventions"></a>Conventions de langage

Les conventions de langage pour EditorConfig dans Visual Studio se répartissent en deux catégories : celles qui s’appliquent à Visual Basic et C#, et celles qui sont spécifiques à C#. Les conventions de langage affectent la manière dont les différents aspects d’un langage de programmation sont utilisés, par exemple, les modificateurs et les parenthèses.

> [!TIP]
> - Utilisez les liens de la section **Dans cet article** pour accéder aux différentes sections de la page.
> - Pour voir des exemples de code dans votre langage de programmation préféré, choisissez-le avec l’outil de sélection de langage en haut à droite de la fenêtre du navigateur.
>
>   ![Contrôle du sélecteur de langages de code](media/code-language-picker.png)

## <a name="rule-format"></a>Format de la règle

Les règles relatives aux conventions de langage ont le format général suivant :

`option_name = value:severity`

Pour chaque convention de langage, vous spécifiez une valeur qui définit si ou quand favoriser ce style. De nombreuses règles acceptent une valeur de `true` (préférer ce style) ou `false` (ne pas préférer ce style) ; d’autres acceptent des valeurs telles que `when_on_single_line` ou `never`. La seconde partie de la règle spécifie la **gravité**.

### <a name="severity"></a>Gravité

Un niveau de gravité de convention de langage spécifie le niveau auquel appliquer ce style. Le tableau suivant répertorie les valeurs de gravité possibles, ainsi que leurs effets :

Gravité | Effet
:------- | ------
`none` | Ne rien afficher à l’utilisateur en cas de violation de cette règle. Toutefois, les fonctionnalités de génération de code génèrent du code dans ce style. Les règles avec une gravité `none` n’apparaissent jamais dans le menu **Actions rapides et refactorisations**. Dans la plupart des cas, ceci est considéré comme « désactivé » ou « ignoré ».
`silent` (aussi `refactoring` dans Visual Studio 2017 versions 15.8 et ultérieures) | Ne rien afficher à l’utilisateur en cas de violation de cette règle. Toutefois, les fonctionnalités de génération de code génèrent du code dans ce style. Les règles avec la gravité `silent` participent au nettoyage et apparaissent dans le menu **Actions rapides et refactorisations**.
`suggestion` | En cas de violation de cette règle de style, l’afficher à l’utilisateur comme une suggestion. Les suggestions s’affichent sous la forme de trois points gris sous les deux premiers caractères.
`warning` | En cas de violation de cette règle de style, afficher un avertissement du compilateur.
`error` | En cas de violation de cette règle de style, afficher une erreur du compilateur.

## <a name="net-code-style-settings"></a>Paramètres de style de code .NET

Les règles de style mentionnées dans cette section s’appliquent aussi bien au langage C# qu’au langage Visual Basic.

- [Qualificateurs "This." et "Me."](#this-and-me)
  - dotnet\_style\_qualification\_for_field
  - dotnet\_style\_qualification\_for_property
  - dotnet\_style\_qualification\_for_method
  - dotnet\_style\_qualification\_for_event
- [Mots clés de langage plutôt que des noms de types d’infrastructure pour les références de type](#language-keywords)
  - dotnet\_style\_predefined\_type\_for\_locals\_parameters_members
  - dotnet\_style\_predefined\_type\_for\_member_access
- [Préférences des modificateurs](#normalize-modifiers)
  - dotnet\_style\_require\_accessibility_modifiers
  - csharp\_preferred\_modifier_order
  - visual\_basic\_preferred\_modifier_order
  - dotnet\_style\_readonly\_field
- [Préférences de parenthèses](#parentheses-preferences)
  - dotnet\_style\_parentheses\_in\_arithmetic\_binary\_operators
  - dotnet\_style\_parentheses\_in\_other\_binary\_operators
  - dotnet\_style\_parentheses\_in\_other\_operators
  - dotnet\_style\_parentheses\_in\_relational\_binary\_operators
- [Préférences au niveau de l’expression](#expression-level-preferences)
  - dotnet\_style\_object_initializer
  - dotnet\_style\_collection_initializer
  - dotnet\_style\_explicit\_tuple_names
  - dotnet\_style\_prefer\_inferred\_tuple_names
  - dotnet\_style\_prefer\_inferred\_anonymous\_type\_member_names
  - dotnet\_style\_prefer\_auto\_properties
  - dotnet\_style\_prefer\_is\_null\_check\_over\_reference\_equality\_method
  - dotnet\_style\_prefer\_conditional\_expression\_over\_assignment
  - dotnet\_style\_prefer\_conditional\_expression\_over\_return
  - dotnet\_style\_prefer\_compound\_assignment
- [Préférences de vérification de valeur "Null"](#null-checking-preferences)
  - dotnet\_style\_coalesce_expression
  - dotnet\_style\_null_propagation

### Qualificateurs <a name="this-and-me"></a>« This. » et « Me. »

Cette règle de style peut être appliquée à des champs, à des propriétés, à des méthodes ou à des événements. La valeur **true** signifie qu’il faut faire en sorte de faire précéder le symbole de code de `this.` en C# ou de `Me.` en Visual Basic. La valeur **false** signifie qu’il faut faire en sorte de ne _pas_ faire précéder l’élément de code de `this.` ou de `Me.`.

Ces règles peuvent apparaître dans un fichier *.editorconfig* comme suit :

```ini
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_qualification_for_field = false:suggestion
dotnet_style_qualification_for_property = false:suggestion
dotnet_style_qualification_for_method = false:suggestion
dotnet_style_qualification_for_event = false:suggestion
```

#### <a name="dotnet_style_qualification_for_field"></a>dotnet\_style\_qualification\_for_field

|||
|-|-|
| **Nom de la règle** | dotnet_style_qualification_for_field |
| **ID de règle** | IDE0003 et IDE0009 |
| **Langages applicables** | C# et Visual Basic |
| **Valeurs** | `true` - Faire en sorte de faire précéder les champs de `this.` en C# ou de `Me.` en Visual Basic<br /><br />`false` - Préférer que les champs ne soient _pas_ précédés par `this.` ou `Me.` |
| **Valeur par défaut de Visual Studio** | `false:silent` |

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

#### <a name="dotnet_style_qualification_for_property"></a>dotnet\_style\_qualification\_for_property

|||
|-|-|
| **Nom de la règle** | dotnet_style_qualification_for_property |
| **ID de règle** | IDE0003 et IDE0009 |
| **Langages applicables** | C# et Visual Basic |
| **Valeurs** | `true` - Faire en sorte de faire précéder les propriétés de `this.` en C# ou de `Me.` en Visual Basic<br /><br />`false` - Préférer que les propriétés ne soient _pas_ précédées par `this.` ou `Me.` |
| **Valeur par défaut de Visual Studio** | `false:silent` |

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

#### <a name="dotnet_style_qualification_for_method"></a>dotnet\_style\_qualification\_for_method

|||
|-|-|
| **Nom de la règle** | dotnet_style_qualification_for_method |
| **ID de règle** | IDE0003 et IDE0009 |
| **Langages applicables** | C# et Visual Basic |
| **Valeurs** | `true` - Faire en sorte de faire précéder les méthodes de `this.` en C# ou de `Me.` en Visual Basic.<br /><br />`false` - Préférer que les méthodes ne soient _pas_ précédées par `this.` ou `Me.`. |
| **Valeur par défaut de Visual Studio** | `false:silent` |

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

#### <a name="dotnet_style_qualification_for_event"></a>dotnet\_style\_qualification\_for_event

|||
|-|-|
| **Nom de la règle** | dotnet_style_qualification_for_event |
| **ID de règle** | IDE0003 et IDE0009 |
| **Langages applicables** | C# et Visual Basic |
| **Valeurs** | `true` - Faire en sorte de faire précéder les événements de `this.` en C# ou de `Me.` en Visual Basic.<br /><br />`false` - Préférer que les événements ne soient _pas_ précédés par `this.` ou `Me.`. |
| **Valeur par défaut de Visual Studio** | `false:silent` |

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

### <a name="language-keywords"></a>Mots clés du langage au lieu des noms de types de framework pour les références de type

Cette règle de style peut être appliquée à des variables locales, des paramètres de méthode et des membres de classe, ou comme une règle distincte à des expressions d’accès de membre de type. La valeur **true** signifie que, pour les types représentés par un mot clé de langage (par exemple, `int` ou `Integer`), on utilise de préférence ce mot clé plutôt que le nom de type (par exemple, `Int32`). La valeur **false** signifie qu’il faut faire en sorte que le nom du type soit utilisé plutôt que le mot clé du langage.

Ces règles peuvent apparaître dans un fichier *.editorconfig* comme suit :

```ini
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_predefined_type_for_locals_parameters_members = true:suggestion
dotnet_style_predefined_type_for_member_access = true:suggestion
```

#### <a name="dotnet_style_predefined_type_for_locals_parameters_members"></a>dotnet\_style\_predefined\_type\_for\_locals\_parameters_members

|||
|-|-|
| **Nom de la règle** | dotnet_style_predefined_type_for_locals_parameters_members |
| **ID de règle** | IDE0012 et IDE0014 |
| **Langages applicables** | C# et Visual Basic |
| **Valeurs** | `true` - Faire en sorte que les types qui ont un mot clé de langage pour les représenter utilisent le mot clé du langage plutôt que le nom du type pour les variables locales, les paramètres de méthode et les membres de classe<br /><br />`false` - Faire en sorte que les variables locales, les paramètres de méthode et les membres de classe utilisent le nom de type plutôt que le mot clé du langage. |
| **Valeur par défaut de Visual Studio** | `true:silent` |

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

#### <a name="dotnet_style_predefined_type_for_member_access"></a>dotnet\_style\_predefined\_type\_for\_member_access

|||
|-|-|
| **Nom de la règle** | dotnet_style_predefined_type_for_member_access |
| **ID de règle** | IDE0013 et IDE0015 |
| **Langages applicables** | C# et Visual Basic |
| **Valeurs** | `true` - Faire en sorte que les types qui ont un mot clé de langage pour les représenter utilisent le mot clé du langage plutôt que le nom du type pour les expressions d’accès de membre.<br /><br />`false` - Faire en sorte que les expressions d’accès de membre utilisent le nom de type plutôt que le mot clé du langage |
| **Valeur par défaut de Visual Studio** | `true:silent` |

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

### <a name="normalize-modifiers"></a>Préférences des modificateurs

Les règles de style de cette section concernent les préférences des modificateurs, notamment la spécification obligatoire des modificateurs d’accessibilité, l’indication de l’ordre de tri souhaité pour les modificateurs, ainsi que la spécification obligatoire du modificateur en lecture seule.

Ces règles peuvent apparaître dans un fichier *.editorconfig* comme suit :

```ini
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

#### <a name="dotnet_style_require_accessibility_modifiers"></a>dotnet\_style\_require\_accessibility_modifiers

|||
|-|-|
| **Nom de la règle** | dotnet_style_require_accessibility_modifiers |
| **ID de règle** | IDE0040 |
| **Langages applicables** | C# et Visual Basic |
| **Valeurs** | `always` - Préférer la déclaration de modificateurs d’accessibilité.<br /><br />`for_non_interface_members` - Préférer la déclaration de modificateurs d’accessibilité, sauf pour des membres d’interface publique. (Ceci est identique à **always** et a été ajouté à des fins de vérification future, si C# ajoute des méthodes d’interface par défaut.)<br /><br />`never` - Ne jamais préférer la déclaration de modificateurs d’accessibilité.<br /><br />`omit_if_default` - Préférer la déclaration de modificateurs d’accessibilité, sauf s’il s’agit du modificateur par défaut. |
| **Valeur par défaut de Visual Studio** | `for_non_interface_members:silent` |
| **Version introduite** | Visual Studio 2017 version 15.5 |

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

#### <a name="csharp_preferred_modifier_order"></a>csharp_preferred_modifier_order

|||
|-|-|
| **Nom de la règle** | csharp_preferred_modifier_order |
| **ID de règle** | IDE0036 |
| **Langages applicables** | C# |
| **Valeurs** | Un ou plusieurs modificateurs C#, tels que `public`, `private` et `protected` |
| **Valeur par défaut de Visual Studio** | `public, private, protected, internal, static, extern, new, virtual, abstract, sealed, override, readonly, unsafe, volatile, async:silent` |
| **Version introduite** | Visual Studio 2017 version 15.5 |

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

#### <a name="visual_basic_preferred_modifier_order"></a>visual_basic_preferred_modifier_order

|||
|-|-|
| **Nom de la règle** | visual_basic_preferred_modifier_order |
| **ID de règle** | IDE0036 |
| **Langages applicables** | Visual Basic |
| **Valeurs** | Un ou plusieurs modificateurs Visual Basic, tels que `Partial`, `Private` et `Public` |
| **Valeur par défaut de Visual Studio** | `Partial, Default, Private, Protected, Public, Friend, NotOverridable, Overridable, MustOverride, Overloads, Overrides, MustInherit, NotInheritable, Static, Shared, Shadows, ReadOnly, WriteOnly, Dim, Const,WithEvents, Widening, Narrowing, Custom, Async:silent` |
| **Version introduite** | Visual Studio 2017 version 15.5 |

- Quand cette règle est définie sur une liste de modificateurs, préférer l’ordre spécifié.
- Quand cette règle est omise dans le fichier, il n’y a pas d’ordre préféré pour les modificateurs.

Exemples de code :

```vb
' visual_basic_preferred_modifier_order = Partial,Default,Private,Protected,Public,Friend,NotOverridable,Overridable,MustOverride,Overloads,Overrides,MustInherit,NotInheritable,Static,Shared,Shadows,ReadOnly,WriteOnly,Dim,Const,WithEvents,Widening,Narrowing,Custom,Async
Public Class MyClass
    Private Shared ReadOnly daysInYear As Int = 365
End Class
```

#### <a name="dotnet_style_readonly_field"></a>dotnet_style_readonly_field

|||
|-|-|
| **Nom de la règle** | dotnet_style_readonly_field |
| **ID de règle** | IDE0044 |
| **Langages applicables** | C# et Visual Basic |
| **Valeurs** | `true` - Quand cette règle a la valeur true, les champs doivent être marqués de préférence avec `readonly` (C#) ou `ReadOnly` (Visual Basic), s’ils sont assignés inline ou dans un constructeur.<br /><br />`false` - Ne spécifier aucune préférence concernant le marquage des champs avec `readonly` (C#) ou `ReadOnly` (Visual Basic) |
| **Valeur par défaut de Visual Studio** | `true:suggestion` |
| **Version introduite** | Visual Studio 2017 version 15.7 |

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

### <a name="parentheses-preferences"></a>Préférences relatives aux parenthèses

Les règles de style de cette section concernent les préférences de parenthèses, notamment l’utilisation de parenthèses pour les opérateurs arithmétiques, relationnels et autres opérateurs binaires.

Ces règles peuvent apparaître dans un fichier *.editorconfig* comme suit :

```ini
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_parentheses_in_arithmetic_binary_operators = always_for_clarity:silent
dotnet_style_parentheses_in_relational_binary_operators = always_for_clarity:silent
dotnet_style_parentheses_in_other_binary_operators = always_for_clarity:silent
dotnet_style_parentheses_in_other_operators = never_if_unnecessary:silent
```

#### <a name="dotnet_style_parentheses_in_arithmetic_binary_operators"></a>dotnet\_style\_parentheses\_in\_arithmetic\_binary_operators

|||
|-|-|
| **Nom de la règle** | dotnet_style_parentheses_in_arithmetic_binary_operators |
| **ID de règle** | IDE0047 |
| **Langages applicables** | C# et Visual Basic |
| **Valeurs** | `always_for_clarity` - Préférer les parenthèses pour clarifier la priorité des opérateurs arithmétiques (`*`, `/`, `%`, `+`, `-`, `<<`, `>>`, `&`, `^`, `|`)<br /><br />`never_if_unnecessary` - Préférer éviter les parenthèses si la priorité des opérateurs arithmétiques (`*`, `/`, `%`, `+`, `-`, `<<`, `>>`, `&`, `^`, `|`) est évidente |
| **Valeur par défaut de Visual Studio** | `always_for_clarity:silent` |
| **Version introduite** | Visual Studio 2017 version 15.8 |

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

#### <a name="dotnet_style_parentheses_in_relational_binary_operators"></a>dotnet\_style\_parentheses\_in\_relational\_binary_operators

|||
|-|-|
| **Nom de la règle** | dotnet_style_parentheses_in_relational_binary_operators |
| **ID de règle** | IDE0047 |
| **Langages applicables** | C# et Visual Basic |
| **Valeurs** | `always_for_clarity` - Préférer les parenthèses pour clarifier la priorité des opérateurs relationnels (`>`, `<`, `<=`, `>=`, `is`, `as`, `==`, `!=`)<br /><br />`never_if_unnecessary` - Préférer éviter les parenthèses si la priorité des opérateurs relationnels (`>`, `<`, `<=`, `>=`, `is`, `as`, `==`, `!=`) est évidente |
| **Valeur par défaut de Visual Studio** | `always_for_clarity:silent` |
| **Version introduite** | Visual Studio 2017 version 15.8 |

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

#### <a name="dotnet_style_parentheses_in_other_binary_operators"></a>dotnet\_style\_parentheses\_in\_other\_binary_operators

|||
|-|-|
| **Nom de la règle** | dotnet_style_parentheses_in_other_binary_operators |
| **ID de règle** | IDE0047 |
| **Langages applicables** | C# et Visual Basic |
| **Valeurs** | `always_for_clarity` - Préférer les parenthèses pour clarifier la priorité des autres opérateurs binaires (`&&`, `||`, `??`)<br /><br />`never_if_unnecessary` - Préférer éviter les parenthèses si la priorité des autres opérateurs binaires (`&&`, `||`, `??`) est évidente |
| **Valeur par défaut de Visual Studio** | `always_for_clarity:silent` |
| **Version introduite** | Visual Studio 2017 version 15.8 |

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

#### <a name="dotnet_style_parentheses_in_other_operators"></a>dotnet\_style\_parentheses\_in\_other_operators

|||
|-|-|
| **Nom de la règle** | dotnet_style_parentheses_in_other_operators |
| **ID de règle** | IDE0047 |
| **Langages applicables** | C# et Visual Basic |
| **Valeurs** | `always_for_clarity` - Préférer les parenthèses pour clarifier la priorité des opérateurs<br /><br />`never_if_unnecessary` - Préférer éviter les parenthèses si la priorité des opérateurs est évidente |
| **Valeur par défaut de Visual Studio** | `never_if_unnecessary:silent` |
| **Version introduite** | Visual Studio 2017 version 15.8 |

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

### <a name="expression-level-preferences"></a>Préférences au niveau des expressions

Les règles de style mentionnées dans cette section concernent les préférences au niveau de l’expression, notamment l’utilisation d’initialiseurs d’objets, d’initialiseurs de collections, de noms de tuples explicites ou déduits, et de types anonymes déduits.

Ces règles peuvent apparaître dans un fichier *.editorconfig* comme suit :

```ini
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_object_initializer = true:suggestion
dotnet_style_collection_initializer = true:suggestion
dotnet_style_explicit_tuple_names = true:suggestion
dotnet_style_prefer_inferred_tuple_names = true:suggestion
dotnet_style_prefer_inferred_anonymous_type_member_names = true:suggestion
dotnet_style_prefer_auto_properties = true:silent
dotnet_style_prefer_conditional_expression_over_assignment = true:suggestion
dotnet_style_prefer_conditional_expression_over_return = true:suggestion
dotnet_style_prefer_compound_assignment = true:suggestion
```

#### <a name="dotnet_style_object_initializer"></a>dotnet\_style\_object_initializer

|||
|-|-|
| **Nom de la règle** | dotnet_style_object_initializer |
| **ID de règle** | IDE0017 |
| **Langages applicables** | C# et Visual Basic |
| **Valeurs** | `true` - Préférer l’initialisation des objets à l’aide d’initialiseurs d’objets dans la mesure du possible<br /><br />`false` - Faire en sorte que les objets ne soient *pas* initialisés à l’aide d’initialiseurs d’objets |
| **Valeur par défaut de Visual Studio** | `true:suggestion` |

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

#### <a name="dotnet_style_collection_initializer"></a>dotnet\_style\_collection_initializer

|||
|-|-|
| **Nom de la règle** | dotnet_style_collection_initializer |
| **ID de règle** | IDE0028 |
| **Langages applicables** | C# et Visual Basic |
| **Valeurs** | `true` - Préférer l’initialisation des collections à l’aide d’initialiseurs de collection dans la mesure du possible.<br /><br />`false` - Faire en sorte que les collections ne soient *pas* initialisées à l’aide d’initialiseurs de collection. |
| **Valeur par défaut de Visual Studio** | `true:suggestion` |

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

#### <a name="dotnet_style_explicit_tuple_names"></a>dotnet\_style\_explicit\_tuple_names

|||
|-|-|
| **Nom de la règle** | dotnet_style_explicit_tuple_names |
| **ID de règle** | IDE0033 |
| **Langages applicables** | C# 7.0+ et Visual Basic 15+ |
| **Valeurs** | `true` - Préférer les noms de tuple aux propriétés ItemX<br /><br />`false` - Préférer les propriétés ItemX aux noms de tuple |
| **Valeur par défaut de Visual Studio** | `true:suggestion` |

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

#### <a name="dotnet_style_prefer_inferred_tuple_names"></a>dotnet\_style\_prefer\_inferred\_tuple_names

|||
|-|-|
| **Nom de la règle** | dotnet_style_prefer_inferred_tuple_names |
| **ID de règle** | IDE0037 |
| **Langages applicables** | C# 7.1+ et Visual Basic 15+ |
| **Valeurs** | `true` - Préférer les noms des éléments de tuple inférés<br /><br />`false` - Préférer les noms des éléments de tuple explicites |
| **Valeur par défaut de Visual Studio** | `true:suggestion` |
| **Version introduite** | Visual Studio 2017 version 15.6 |

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

#### <a name="dotnet_style_prefer_inferred_anonymous_type_member_names"></a>dotnet\_style\_prefer\_inferred\_anonymous\_type\_member_names

|||
|-|-|
| **Nom de la règle** | dotnet_style_prefer_inferred_anonymous_type_member_names |
| **ID de règle** | IDE0037 |
| **Langages applicables** | C# et Visual Basic |
| **Valeurs** | `true` - Préférer les noms de membre de type anonyme déduits<br /><br />`false` - Préférer les noms de membre de type anonyme explicites |
| **Valeur par défaut de Visual Studio** | `true:suggestion` |
| **Version introduite** | Visual Studio 2017 version 15.6 |

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

#### <a name="dotnet_style_prefer_auto_properties"></a>dotnet\_style\_prefer\_auto\_properties

|||
|-|-|
| **Nom de la règle** | dotnet_style_prefer_auto_properties |
| **ID de règle** | IDE0032 |
| **Langages applicables** | C# et Visual Basic |
| **Valeurs** | `true` - Préférer les propriétés automatiques plutôt que des propriétés comportant des champs de stockage privés<br /><br />`false` - Préférer les propriétés comportant des champs de stockage privés plutôt que des propriétés automatiques. |
| **Valeur par défaut de Visual Studio** | `true:suggestion` |
| **Version introduite** | Visual Studio 2017 version 15.7 |

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

#### <a name="dotnet_style_prefer_is_null_check_over_reference_equality_method"></a>dotnet\_style\_prefer\_is\_null\_check\_over\_reference\_equality\_method

|||
|-|-|
| **Nom de la règle** | dotnet_style_prefer_is_null_check_over_reference_equality_method |
| **ID de règle** | IDE0041 |
| **Langages applicables** | C# et Visual Basic |
| **Valeurs** | `true` - Préférer utiliser une vérification de valeur null avec les critères spéciaux à `object.ReferenceEquals`<br /><br />`false` - Préférer `object.ReferenceEquals` à une vérification de valeur null avec les critères spéciaux |
| **Valeur par défaut de Visual Studio** | `true:suggestion` |
| **Version introduite** | Visual Studio 2017 version 15.7 |

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

#### <a name="dotnet_style_prefer_conditional_expression_over_assignment"></a>dotnet\_style\_prefer\_conditional\_expression\_over_assignment

|||
|-|-|
| **Nom de la règle** | dotnet_style_prefer_conditional_expression_over_assignment |
| **ID de règle** | IDE0045 |
| **Langages applicables** | C# et Visual Basic |
| **Valeurs** | `true` - Préferer les assignations avec une expression conditionnelle ternaire aux assignations avec une instruction if-else<br /><br />`false` - Préférer les assignations avec une instruction if-else aux assignations avec une expression conditionnelle ternaire |
| **Valeur par défaut de Visual Studio** | `true:suggestion` |
| **Version introduite** | Visual Studio 2017 version 15.8 |

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

#### <a name="dotnet_style_prefer_conditional_expression_over_return"></a>dotnet\_style\_prefer\_conditional\_expression\_over_return

|||
|-|-|
| **Nom de la règle** | dotnet_style_prefer_conditional_expression_over_return |
| **ID de règle** | IDE0046 |
| **Langages applicables** | C# et Visual Basic |
| **Valeurs** | `true` - Préférer les instructions de retour avec une expression conditionnelle ternaire aux instructions de retour avec une instruction if-else<br /><br />`false` - Préférer les instructions de retour avec une instruction if-else aux instructions de retour avec une expression conditionnelle ternaire |
| **Valeur par défaut de Visual Studio** | `true:suggestion` |
| **Version introduite** | Visual Studio 2017 version 15.8 |

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

#### <a name="dotnet_style_prefer_compound_assignment"></a>dotnet\_style\_prefer\_compound\_assignment

|||
|-|-|
| **Nom de la règle** | dotnet_style_prefer_compound_assignment |
| **ID de règle** | IDE0054 |
| **Langages applicables** | C# et Visual Basic |
| **Valeurs** | `true` - Préférer les expressions d’[assignation composée](/dotnet/csharp/language-reference/operators/assignment-operator#compound-assignment)<br /><br />`false` - Ne pas préférer les expressions d’assignation composée |
| **Valeur par défaut de Visual Studio** | `true:suggestion` |

Exemples de code :

```csharp
// dotnet_style_prefer_compound_assignment = true
x += 1;

// dotnet_style_prefer_compound_assignment = false
x = x + 1;
```

```vb
' dotnet_style_prefer_compound_assignment = true
x += 1

' dotnet_style_prefer_compound_assignment = false
x = x + 1
```

### <a name="null-checking-preferences"></a>Préférences de vérification de valeur null

Les règles de style de cette section concernent les préférences de vérification de valeur null.

Ces règles peuvent apparaître dans un fichier *.editorconfig* comme suit :

```ini
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_coalesce_expression = true:suggestion
dotnet_style_null_propagation = true:suggestion
```

#### <a name="dotnet_style_coalesce_expression"></a>dotnet\_style\_coalesce_expression

|||
|-|-|
| **Nom de la règle** | dotnet_style_coalesce_expression |
| **ID de règle** | IDE0029 |
| **Langages applicables** | C# et Visual Basic |
| **Valeurs** | `true` - Préférer l’expression de fusion null à la vérification d’opérateur ternaire<br /><br />`false` - Préférer la vérification d’opérateur ternaire aux expressions de fusion null |
| **Valeur par défaut de Visual Studio** | `true:suggestion` |

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

#### <a name="dotnet_style_null_propagation"></a>dotnet\_style\_null_propagation

|||
|-|-|
| **Nom de la règle** | dotnet_style_null_propagation |
| **ID de règle** | IDE0031 |
| **Langages applicables** | C# 6.0+ et Visual Basic 14+ |
| **Valeurs** | `true` - Préférer l’utilisation de l’opérateur de condition null dans la mesure du possible<br /><br />`false` - Préférer la vérification de la valeur null ternaire dans la mesure du possible |
| **Valeur par défaut de Visual Studio** | `true:suggestion` |

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

## <a name="net-code-quality-settings"></a>Paramètres de qualité de code .NET

Les règles de qualité décrites dans cette section s’appliquent à la fois au code C# et au code Visual Basic. Elles servent à configurer les analyseurs de code intégrés à l’environnement de développement intégré Visual Studio. Pour plus d’informations sur la configuration des analyseurs FxCop avec un fichier EditorConfig, consultez [Configurer les analyseurs FxCop](../code-quality/configure-fxcop-analyzers.md).

- [Préférences relatives aux paramètres](#parameter-preferences)
  - dotnet\_code\_quality\_unused\_parameters

### <a name="parameter-preferences"></a>Préférences relatives aux paramètres

Les règles de qualité de cette section concernent les paramètres de méthode.

Ces règles peuvent apparaître dans un fichier *.editorconfig* comme suit :

```ini
# CSharp and Visual Basic code quality settings:
[*.{cs,vb}]
dotnet_code_quality_unused_parameters = all:suggestion
```

#### <a name="dotnet_code_quality_unused_parameters"></a>dotnet\_code\_quality\_unused\_parameters

|||
|-|-|
| **Nom de la règle** | dotnet_code_quality_unused_parameters |
| **ID de règle** | IDE0060 |
| **Langages applicables** | C# et Visual Basic |
| **Valeurs** | `all` - Marquer les méthodes d’accessibilité qui contiennent des paramètres inutilisés<br /><br />`non_public` - Marquer uniquement les méthodes non publiques qui contiennent des paramètres inutilisés |
| **Valeur par défaut de Visual Studio** | `all:suggestion` |

Exemples de code :

```csharp
// dotnet_code_quality_unused_parameters = all:suggestion
public int GetNum() { return 1; }

// dotnet_code_quality_unused_parameters = non_public:suggestion
public int GetNum(int arg1) { return 1; }
```

```vb
' dotnet_code_quality_unused_parameters = all:suggestion
Public Function GetNum()
    Return 1
End Function

' dotnet_code_quality_unused_parameters = non_public:suggestion
Public Function GetNum(arg1 As Integer)
    Return 1
End Function
```

## <a name="c-code-style-settings"></a>Paramètres de style de code C#

Les règles de style mentionnées dans cette section s’appliquent uniquement à C#.

- [Types implicites et explicites](#implicit-and-explicit-types)
  - csharp\_style\_var\_for\_built\_in_types
  - csharp\_style\_var\_when\_type\_is_apparent
  - csharp\_style\_var_elsewhere
- [Membres expression-bodied](#expression-bodied-members)
  - csharp\_style\_expression\_bodied_methods
  - csharp\_style\_expression\_bodied_constructors
  - csharp\_style\_expression\_bodied_operators
  - csharp\_style\_expression\_bodied_properties
  - csharp\_style\_expression\_bodied_indexers
  - csharp\_style\_expression\_bodied_accessors
  - csharp\_style\_expression\_bodied_lambdas
  - csharp\_style\_expression\_bodied\_local_functions
- [Critères spéciaux](#pattern-matching)
  - csharp\_style\_pattern\_matching\_over\_is\_with\_cast_check
  - csharp\_style\_pattern\_matching\_over\_as\_with\_null_check
- [Déclarations de variables inline](#inlined-variable-declarations)
  - csharp\_style\_inlined\_variable_declaration
- [Préférences au niveau de l’expression](#c-expression-level-preferences)
  - csharp\_prefer\_simple\_default_expression
- [Préférences de vérification de valeur "Null"](#c-null-checking-preferences)
  - csharp\_style\_throw_expression
  - csharp\_style\_conditional\_delegate_call
- [Préférences des blocs de code](#code-block-preferences)
  - csharp\_prefer_braces
- [Préférences relatives aux valeurs inutilisées](#unused-value-preferences)
  - csharp\_style\_unused\_value\_expression\_statement_preference
  - csharp\_style\_unused\_value\_assignment_preference
- [Préférences relatives aux index et aux plages](#index-and-range-preferences)
  - csharp\_style\_prefer\_index_operator
  - csharp\_style\_prefer\_range_operator
- [Préférences diverses](#miscellaneous-preferences)
  - csharp\_style\_deconstructed\_variable_declaration
  - csharp\_style\_pattern\_local\_over\_anonymous_function
  - csharp\_using\_directive\_placement
  - csharp\_prefer\_static\_local_function
  - csharp\_prefer\_simple\_using_statement
  - csharp\_style\_prefer\_switch_expression

### <a name="implicit-and-explicit-types"></a>Types implicites et explicites

Les règles de style mentionnées dans cette section concernent l’utilisation du mot clé [var](/dotnet/csharp/language-reference/keywords/var) ou d’un type explicite dans une déclaration de variables. Cette règle peut être appliquée séparément à des types intégrés, quand le type est visible, et ailleurs.

Exemple de fichier *.editorconfig* :

```ini
# CSharp code style settings:
[*.cs]
csharp_style_var_for_built_in_types = true:suggestion
csharp_style_var_when_type_is_apparent = true:suggestion
csharp_style_var_elsewhere = true:suggestion
```

#### <a name="csharp_style_var_for_built_in_types"></a>csharp\_style\_var\_for\_built\_in_types

|||
|-|-|
| **Nom de la règle** | csharp_style_var_for_built_in_types |
| **ID de règle** | IDE0007 et IDE0008 |
| **Langages applicables** | C#  |
| **Valeurs** | `true` - Préférer utiliser `var` pour déclarer des variables avec des types intégrés tels que `int`<br /><br />`false` - Préférer utiliser un type explicite plutôt que `var` pour déclarer des variables avec des types intégrés tels que `int` |
| **Valeur par défaut de Visual Studio** | `true:silent` |

Exemples de code :

```csharp
// csharp_style_var_for_built_in_types = true
var x = 5;

// csharp_style_var_for_built_in_types = false
int x = 5;
```

#### <a name="csharp_style_var_when_type_is_apparent"></a>csharp\_style\_var\_when\_type\_is_apparent

|||
|-|-|
| **Nom de la règle** | csharp_style_var_when_type_is_apparent |
| **ID de règle** | IDE0007 et IDE0008 |
| **Langages applicables** | C#  |
| **Valeurs** | `true` - Préférer `var` quand le type est déjà mentionné dans la partie droite d’une expression de déclaration.<br /><br />`false` - Préférer le type explicite à `var` quand le type est déjà mentionné dans la partie droite d’une expression de déclaration. |
| **Valeur par défaut de Visual Studio** | `true:silent` |

Exemples de code :

```csharp
// csharp_style_var_when_type_is_apparent = true
var obj = new Customer();

// csharp_style_var_when_type_is_apparent = false
Customer obj = new Customer();
```

#### <a name="csharp_style_var_elsewhere"></a>csharp\_style\_var_elsewhere

|||
|-|-|
| **Nom de la règle** | csharp_style_var_elsewhere |
| **ID de règle** | IDE0007 et IDE0008 |
| **Langages applicables** | C#  |
| **Valeurs** | `true` - Préférer utiliser `var` plutôt qu’un type explicite dans tous les cas, sauf substitution par une autre règle de style de code<br /><br />`false` - Préférer un type explicite plutôt que `var` dans tous les cas, sauf substitution par une autre règle de style de code |
| **Valeur par défaut de Visual Studio** | `true:silent` |

Exemples de code :

```csharp
// csharp_style_var_elsewhere = true
var f = this.Init();

// csharp_style_var_elsewhere = false
bool f = this.Init();
```

### <a name="expression-bodied-members"></a>Membres expression-bodied

Les règles de style mentionnées dans cette section concernent l’utilisation de [membres expression-bodied](/dotnet/csharp/programming-guide/statements-expressions-operators/expression-bodied-members) quand la logique se compose d’une expression unique. Cette règle peut être appliquée à des méthodes, des constructeurs, des opérateurs, des propriétés, des indexeurs et des accesseurs.

Exemple de fichier *.editorconfig* :

```ini
# CSharp code style settings:
[*.cs]
csharp_style_expression_bodied_methods = false:silent
csharp_style_expression_bodied_constructors = false:silent
csharp_style_expression_bodied_operators = false:silent
csharp_style_expression_bodied_properties = true:suggestion
csharp_style_expression_bodied_indexers = true:suggestion
csharp_style_expression_bodied_accessors = true:suggestion
csharp_style_expression_bodied_lambdas = true:silent
csharp_style_expression_bodied_local_functions = false:silent
```

#### <a name="csharp_style_expression_bodied_methods"></a>csharp\_style\_expression\_bodied_methods

|||
|-|-|
| **Nom de la règle** | csharp_style_expression_bodied_methods |
| **ID de règle** | IDE0022 |
| **Langages applicables** | C# 6.0+  |
| **Valeurs** | `true` - Préférer les corps d’expression pour les méthodes<br /><br />`when_on_single_line` - Préférer les corps d’expression pour les méthodes sur une seule ligne<br /><br />`false` - Préférer les corps de bloc pour les méthodes |
| **Valeur par défaut de Visual Studio** | `false:silent` |

Exemples de code :

```csharp
// csharp_style_expression_bodied_methods = true
public int GetAge() => this.Age;

// csharp_style_expression_bodied_methods = false
public int GetAge() { return this.Age; }
```

#### <a name="csharp_style_expression_bodied_constructors"></a>csharp\_style\_expression\_bodied_constructors

|||
|-|-|
| **Nom de la règle** | csharp_style_expression_bodied_constructors |
| **ID de règle** | IDE0021 |
| **Langages applicables** | C# 7.0+ |
| **Valeurs** | `true` - Préférer les corps d’expression pour les constructeurs<br /><br />`when_on_single_line` - Préférer les corps d’expression pour les constructeurs sur une seule ligne<br /><br />`false` - Préférer les corps de bloc pour les constructeurs |
| **Valeur par défaut de Visual Studio** | `false:silent` |

Exemples de code :

```csharp
// csharp_style_expression_bodied_constructors = true
public Customer(int age) => Age = age;

// csharp_style_expression_bodied_constructors = false
public Customer(int age) { Age = age; }
```

#### <a name="csharp_style_expression_bodied_operators"></a>csharp\_style\_expression\_bodied_operators

|||
|-|-|
| **Nom de la règle** | csharp_style_expression_bodied_operators |
| **ID de règle** | IDE0023 et IDE0024 |
| **Langages applicables** | C# 7.0+ |
| **Valeurs** | `true` - Préférer les corps d’expression pour les opérateurs<br /><br />`when_on_single_line` - Préférer les corps d’expression pour les opérateurs sur une seule ligne<br /><br />`false` - Préférer les corps de bloc pour les opérateurs |
| **Valeur par défaut de Visual Studio** | `false:silent` |

Exemples de code :

```csharp
// csharp_style_expression_bodied_operators = true
public static ComplexNumber operator + (ComplexNumber c1, ComplexNumber c2)
    => new ComplexNumber(c1.Real + c2.Real, c1.Imaginary + c2.Imaginary);

// csharp_style_expression_bodied_operators = false
public static ComplexNumber operator + (ComplexNumber c1, ComplexNumber c2)
{ return new ComplexNumber(c1.Real + c2.Real, c1.Imaginary + c2.Imaginary); }
```

#### <a name="csharp_style_expression_bodied_properties"></a>csharp\_style\_expression\_bodied_properties

|||
|-|-|
| **Nom de la règle** | csharp_style_expression_bodied_properties |
| **ID de règle** | IDE0025 |
| **Langages applicables** | C# 7.0+ |
| **Valeurs** | `true` - Préférer les corps d’expression pour les propriétés<br /><br />`when_on_single_line` - Préférer les corps d’expression pour les propriétés sur une seule ligne<br /><br />`false` - Préférer les corps de bloc pour les propriétés |
| **Valeur par défaut de Visual Studio** | `true:silent` |

Exemples de code :

```csharp
// csharp_style_expression_bodied_properties = true
public int Age => _age;

// csharp_style_expression_bodied_properties = false
public int Age { get { return _age; }}
```

#### <a name="csharp_style_expression_bodied_indexers"></a>csharp\_style\_expression\_bodied_indexers

|||
|-|-|
| **Nom de la règle** | csharp_style_expression_bodied_indexers |
| **ID de règle** | IDE0026 |
| **Langages applicables** | C# 7.0+ |
| **Valeurs** | `true` - Préférer les corps d’expression pour les indexeurs<br /><br />`when_on_single_line` - Préférer les corps d’expression pour les indexeurs sur une seule ligne<br /><br />`false` - Préférer les corps de bloc pour les indexeurs |
| **Valeur par défaut de Visual Studio** | `true:silent` |

Exemples de code :

```csharp
// csharp_style_expression_bodied_indexers = true
public T this[int i] => _values[i];

// csharp_style_expression_bodied_indexers = false
public T this[int i] { get { return _values[i]; } }
```

#### <a name="csharp_style_expression_bodied_accessors"></a>csharp\_style\_expression\_bodied_accessors

|||
|-|-|
| **Nom de la règle** | csharp_style_expression_bodied_accessors |
| **ID de règle** | IDE0027 |
| **Langages applicables** | C# 7.0+ |
| **Valeurs** | `true` - Préférer les corps d’expression pour les accesseurs<br /><br />`when_on_single_line` - Préférer les corps d’expression pour les accesseurs sur une seule ligne<br /><br />`false` - Préférer les corps de bloc pour les accesseurs |
| **Valeur par défaut de Visual Studio** | `true:silent` |

Exemples de code :

```csharp
// csharp_style_expression_bodied_accessors = true
public int Age { get => _age; set => _age = value; }

// csharp_style_expression_bodied_accessors = false
public int Age { get { return _age; } set { _age = value; } }
```

#### <a name="csharp_style_expression_bodied_lambdas"></a>csharp\_style\_expression\_bodied_lambdas

|||
|-|-|
| **Nom de la règle** | csharp_style_expression_bodied_lambdas |
| **ID de règle** | IDE0053 |
| **Valeurs** | `true` - Préférer les corps d’expression pour les expressions lambda<br /><br />`when_on_single_line` - Préférer les corps d’expression pour les expressions lambda sur une seule ligne<br /><br />`false` - Préférer les corps de bloc pour les expressions lambda |
| **Valeur par défaut de Visual Studio** | `true:silent` |

Exemples de code :

```csharp
// csharp_style_expression_bodied_lambdas = true
Func<int, int> square = x => x * x;

// csharp_style_expression_bodied_lambdas = false
Func<int, int> square = x => { return x * x; };
```

#### <a name="csharp_style_expression_bodied_local_functions"></a>csharp\_style\_expression\_bodied\_local_functions

À compter de C# 7.0, C# prend en charge les [fonctions locales](/dotnet/csharp/programming-guide/classes-and-structs/local-functions). Les fonctions locales sont des méthodes privées d’un type qui sont imbriqués dans un autre membre.

|||
|-|-|
| **Nom de la règle** | csharp_style_expression_bodied_local_functions |
| **ID de règle** | IDE0061 |
| **Langages applicables** | C# 7.0+ |
| **Valeurs** | `true` - Préférer les corps d’expression pour les fonctions locales<br /><br />`when_on_single_line` - Préférer les corps d’expression pour les fonctions locales sur une seule ligne<br /><br />`false` - Préférer les corps de bloc pour les fonctions locales |
| **Valeur par défaut de Visual Studio** | `false:silent` |

Exemples de code :

```csharp
// csharp_style_expression_bodied_local_functions = true
void M()
{
    Hello();
    void Hello() => Console.WriteLine("Hello");
}

// csharp_style_expression_bodied_local_functions = false
void M()
{
    Hello();
    void Hello()
    {
        Console.WriteLine("Hello");
    }
}
```

### <a name="pattern-matching"></a>Critères spéciaux

Les règles de style mentionnées dans cette section concernent l’utilisation de [critères spéciaux](/dotnet/csharp/pattern-matching) en C#.

Exemple de fichier *.editorconfig* :

```ini
# CSharp code style settings:
[*.cs]
csharp_style_pattern_matching_over_is_with_cast_check = true:suggestion
csharp_style_pattern_matching_over_as_with_null_check = true:suggestion
```

#### <a name="csharp_style_pattern_matching_over_is_with_cast_check"></a>csharp\_style\_pattern\_matching\_over\_is\_with\_cast_check

|||
|-|-|
| **Nom de la règle** | csharp_style_pattern_matching_over_is_with_cast_check |
| **ID de règle** | IDE0020 |
| **Langages applicables** | C# 7.0+ |
| **Valeurs** | `true` - Préférer les critères spéciaux plutôt que les expressions `is` avec des casts de type<br /><br />`false` Préférer les expressions `is` avec des casts de type plutôt que les critères spéciaux |
| **Valeur par défaut de Visual Studio** | `true:suggestion` |

Exemples de code :

```csharp
// csharp_style_pattern_matching_over_is_with_cast_check = true
if (o is int i) {...}

// csharp_style_pattern_matching_over_is_with_cast_check = false
if (o is int) {var i = (int)o; ... }
```

#### <a name="csharp_style_pattern_matching_over_as_with_null_check"></a>csharp\_style\_pattern\_matching\_over\_as\_with\_null_check

|||
|-|-|
| **Nom de la règle** | csharp_style_pattern_matching_over_as_with_null_check |
| **ID de règle** | IDE0019 |
| **Langages applicables** | C# 7.0+ |
| **Valeurs** | `true` - Préférer les critères spéciaux plutôt que les expressions `as` avec vérifications « null » pour déterminer si un élément est d’un type particulier<br /><br />`false` - Préférer les expressions `as` avec vérifications « null » plutôt que les critères spéciaux pour déterminer si un élément est d’un type particulier |
| **Valeur par défaut de Visual Studio** | `true:suggestion` |

Exemples de code :

```csharp
// csharp_style_pattern_matching_over_as_with_null_check = true
if (o is string s) {...}

// csharp_style_pattern_matching_over_as_with_null_check = false
var s = o as string;
if (s != null) {...}
```

### <a name="inlined-variable-declarations"></a>Déclarations de variables inline

Cette règle de style vise à déterminer si des variables `out` sont déclarées inline ou non. À compter de C# 7, vous pouvez [déclarer une variable out dans la liste d’arguments d’un appel de méthode](/dotnet/csharp/language-reference/keywords/out-parameter-modifier#calling-a-method-with-an-out-argument) au lieu de le faire dans une déclaration de variable distincte.

#### <a name="csharp_style_inlined_variable_declaration"></a>csharp\_style\_inlined\_variable_declaration

|||
|-|-|
| **Nom de la règle** | csharp_style_inlined_variable_declaration |
| **ID de règle** | IDE0018 |
| **Langages applicables** | C# 7.0+ |
| **Valeurs** | `true` - Faire en sorte de déclarer les variables `out` inline dans la liste d’arguments d’un appel de méthode, dans la mesure du possible<br /><br />`false` - Préférer déclarer les variables `out` avant l’appel de méthode |
| **Valeur par défaut de Visual Studio** | `true:suggestion` |

Exemples de code :

```csharp
// csharp_style_inlined_variable_declaration = true
if (int.TryParse(value, out int i) {...}

// csharp_style_inlined_variable_declaration = false
int i;
if (int.TryParse(value, out i) {...}
```

Exemple de fichier *.editorconfig* :

```ini
# CSharp code style settings:
[*.cs]
csharp_style_inlined_variable_declaration = true:suggestion
```

### <a name="c-expression-level-preferences"></a>Préférences au niveau des expressions C#

Les règles de style de cette section concernent les préférences au niveau des expressions.

Exemple de fichier *.editorconfig* :

```ini
# CSharp code style settings:
[*.cs]
csharp_prefer_simple_default_expression = true:suggestion
```

#### <a name="csharp_prefer_simple_default_expression"></a>csharp\_prefer\_simple\_default_expression

Cette règle de style concerne l’utilisation du [littéral `default` pour les expressions de valeur par défaut](/dotnet/csharp/programming-guide/statements-expressions-operators/default-value-expressions#default-literal-and-type-inference) quand le compilateur peut déduire le type de l’expression.

|||
|-|-|
| **Nom de la règle** | csharp_prefer_simple_default_expression |
| **ID de règle** | IDE0034 |
| **Langages applicables** | C# 7.1+  |
| **Valeurs** | `true` - Préférer `default` à `default(T)`<br /><br />`false` - Préférer `default(T)` à `default` |
| **Valeur par défaut de Visual Studio** | `true:suggestion` |

Exemples de code :

```csharp
// csharp_prefer_simple_default_expression = true
void DoWork(CancellationToken cancellationToken = default) { ... }

// csharp_prefer_simple_default_expression = false
void DoWork(CancellationToken cancellationToken = default(CancellationToken)) { ... }
```

### <a name="c-null-checking-preferences"></a>Préférences de vérification des valeurs null en C#

Ces règles de style concernent la syntaxe autour de la vérification de valeur `null`, notamment l’utilisation d’expressions `throw` ou d’instructions `throw`, et s’il convient d’effectuer, ou non, une vérification de valeur null ou d’utiliser l’opérateur de fusion conditionnelle (`?.`) lors de l’appel d’une [expression lambda](/dotnet/csharp/lambda-expressions).

Exemple de fichier *.editorconfig* :

```ini
# CSharp code style settings:
[*.cs]
csharp_style_throw_expression = true:suggestion
csharp_style_conditional_delegate_call = false:suggestion
```

#### <a name="csharp_style_throw_expression"></a>csharp\_style\_throw_expression

|||
|-|-|
| **Nom de la règle** | csharp_style_throw_expression |
| **ID de règle** | IDE0016 |
| **Langages applicables** | C# 7.0+ |
| **Valeurs** | `true` - Préférer utiliser des expressions `throw` plutôt que des instructions `throw`<br /><br />`false` - Préférer utiliser des instructions `throw` plutôt que des expressions `throw` |
| **Valeur par défaut de Visual Studio** | `true:suggestion` |

Exemples de code :

```csharp
// csharp_style_throw_expression = true
this.s = s ?? throw new ArgumentNullException(nameof(s));

// csharp_style_throw_expression = false
if (s == null) { throw new ArgumentNullException(nameof(s)); }
this.s = s;
```

#### <a name="csharp_style_conditional_delegate_call"></a>csharp\_style\_conditional\_delegate_call

|||
|-|-|
| **Nom de la règle** | csharp_style_conditional_delegate_call |
| **ID de règle** | IDE0041 |
| **Langages applicables** | C# 6.0+  |
| **Valeurs** | `true` - Faire en sorte d’utiliser l’opérateur de fusion conditionnelle (`?.`) lors de l’appel d’une expression lambda, plutôt que d’effectuer une vérification de valeur null<br /><br />`false` - Préférez exécuter une vérification de valeur null avant d’appeler une expression lambda, plutôt que d’utiliser l’opérateur de fusion conditionnelle (`?.`) |
| **Valeur par défaut de Visual Studio** | `true:suggestion` |

Exemples de code :

```csharp
// csharp_style_conditional_delegate_call = true
func?.Invoke(args);

// csharp_style_conditional_delegate_call = false
if (func != null) { func(args); }
```

### <a name="code-block-preferences"></a>Préférences relatives aux blocs de code

Cette règle de style concerne l’utilisation d’accolades `{ }` pour entourer les blocs de code.

Exemple de fichier *.editorconfig* :

```ini
# CSharp code style settings:
[*.cs]
csharp_prefer_braces = true:silent
```

#### <a name="csharp_prefer_braces"></a>csharp\_prefer\_braces

|||
|-|-|
| **Nom de la règle** | csharp_prefer_braces |
| **ID de règle** | IDE0011 |
| **Langages applicables** | C# |
| **Valeurs** | `true` - Préférer les accolades même pour une seule ligne de code<br /><br />`false` - Préférer n’avoir aucune accolade si cela est autorisé |
| **Valeur par défaut de Visual Studio** | `true:silent` |

Exemples de code :

```csharp
// csharp_prefer_braces = true
if (test) { this.Display(); }

// csharp_prefer_braces = false
if (test) this.Display();
```

### <a name="unused-value-preferences"></a>Préférences relatives aux valeurs inutilisées

Ces règles de style concernent les expressions inutilisées et les assignations de valeurs.

Exemple de fichier *.editorconfig* :

```ini
# CSharp code style settings:
[*.cs]
csharp_style_unused_value_expression_statement_preference = discard_variable:silent
csharp_style_unused_value_assignment_preference = discard_variable:suggestion
```

#### <a name="csharp_style_unused_value_expression_statement_preference"></a>csharp_style_unused_value_expression_statement_preference

|||
|-|-|
| **Nom de la règle** | csharp_style_unused_value_expression_statement_preference |
| **ID de règle** | IDE0058 |
| **Langages applicables** | C# |
| **Valeurs** | `discard_variable` - Préférer l’assignation d’une expression inutilisée à un [discard](/dotnet/csharp/discards) <br /><br />`unused_local_variable` - Préférer l’assignation d’une expression inutilisée à une variable locale |
| **Valeur par défaut de Visual Studio** | `discard_variable:silent` |

Exemples de code :

```csharp
// Original code:
System.Convert.ToInt32("35");

// After code fix for IDE0058:

// csharp_style_unused_value_expression_statement_preference = discard_variable
_ = System.Convert.ToInt32("35");

// csharp_style_unused_value_expression_statement_preference = unused_local_variable
var unused = Convert.ToInt32("35");
```

#### <a name="csharp_style_unused_value_assignment_preference"></a>csharp_style_unused_value_assignment_preference

|||
|-|-|
| **Nom de la règle** | csharp_style_unused_value_assignment_preference |
| **ID de règle** | IDE0059 |
| **Langages applicables** | C# |
| **Valeurs** | `discard_variable` - Préférer l’utilisation d’un [discard](/dotnet/csharp/discards) au moment d’assigner une valeur inutilisée<br /><br />`unused_local_variable` - Préférer l’utilisation d’une variable locale au moment d’assigner une valeur inutilisée |
| **Valeur par défaut de Visual Studio** | `discard_variable:suggestion` |

Exemples de code :

```csharp
// csharp_style_unused_value_assignment_preference = discard_variable
int GetCount(Dictionary<string, int> wordCount, string searchWord)
{
    _ = wordCount.TryGetValue(searchWord, out var count);
    return count;
}

// csharp_style_unused_value_assignment_preference = unused_local_variable
int GetCount(Dictionary<string, int> wordCount, string searchWord)
{
    var unused = wordCount.TryGetValue(searchWord, out var count);
    return count;
}
```

### <a name="index-and-range-preferences"></a>Préférences relatives aux index et aux plages

Ces règles de style concernent l’utilisation des opérateurs d’index et de plage, disponibles dans C# 8.0 et les versions ultérieures.

Exemple de fichier *.editorconfig* :

```ini
# CSharp code style settings:
[*.cs]
csharp_style_prefer_index_operator = true:suggestion
csharp_style_prefer_range_operator = true:suggestion
```

#### <a name="csharp_style_prefer_index_operator"></a>csharp\_style\_prefer\_index_operator

|||
|-|-|
| **Nom de la règle** | csharp_style_prefer_index_operator |
| **ID de règle** | IDE0056 |
| **Langages applicables** | C# 8.0+ |
| **Valeurs** | `true` - Préférer l’utilisation de l’opérateur `^` pour le calcul d’un index à partir de la fin d’une collection<br /><br />`false` - Ne pas préférer l’utilisation de l’opérateur `^` pour le calcul d’un index à partir de la fin d’une collection |
| **Valeur par défaut de Visual Studio** | `true:suggestion` |

Exemples de code :

```csharp
// csharp_style_prefer_index_operator = true
string[] names = { "Archimedes", "Pythagoras", "Euclid" };
var index = names[^1];

// csharp_style_prefer_index_operator = false
string[] names = { "Archimedes", "Pythagoras", "Euclid" };
var index = names[names.Length - 1];
```

#### <a name="csharp_style_prefer_range_operator"></a>csharp\_style\_prefer\_range_operator

|||
|-|-|
| **Nom de la règle** | csharp_style_prefer_range_operator |
| **ID de règle** | IDE0057 |
| **Langages applicables** | C# 8.0+ |
| **Valeurs** | `true` - Préférer l’utilisation de l’opérateur de plage `..` pour l’extraction d’une « section » d’une collection<br /><br />`false` - Ne pas préférer l’utilisation de l’opérateur de plage `..` pour l’extraction d’une « section » d’une collection |
| **Valeur par défaut de Visual Studio** | `true:suggestion` |

Exemples de code :

```csharp
// csharp_style_prefer_range_operator = true
string sentence = "the quick brown fox";
var sub = sentence[0..^4];

// csharp_style_prefer_range_operator = false
string sentence = "the quick brown fox";
var sub = sentence.Substring(0, sentence.Length - 4);
```

### <a name="miscellaneous-preferences"></a>Préférences diverses

Cette section contient diverses règles de style.

Exemple de fichier *.editorconfig* :

```ini
# CSharp code style settings:
[*.cs]
csharp_style_deconstructed_variable_declaration = true:suggestion
csharp_style_pattern_local_over_anonymous_function = true:suggestion
csharp_using_directive_placement = outside_namespace:silent
csharp_prefer_static_local_function = true:suggestion
csharp_prefer_simple_using_statement = true:suggestion
csharp_style_prefer_switch_expression = true:suggestion
```

#### <a name="csharp_style_deconstructed_variable_declaration"></a>csharp\_style\_deconstructed\_variable_declaration

|||
|-|-|
| **Nom de la règle** | csharp_style_deconstructed_variable_declaration |
| **ID de règle** | IDE0042 |
| **Langages applicables** | C# 7.0+ |
| **Valeurs** | `true` - Préférer les déclarations de variable déconstruites<br /><br />`false` - Ne pas préférer la déclaration de variables déconstruites |
| **Valeur par défaut de Visual Studio** | `true:suggestion` |

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

#### <a name="csharp_style_pattern_local_over_anonymous_function"></a>csharp\_style\_pattern\_local\_over\_anonymous_function

À compter de C# 7.0, C# prend en charge les [fonctions locales](/dotnet/csharp/programming-guide/classes-and-structs/local-functions). Les fonctions locales sont des méthodes privées d’un type qui sont imbriqués dans un autre membre.

|||
|-|-|
| **Nom de la règle** | csharp_style_pattern_local_over_anonymous_function |
| **ID de règle** | IDE0039 |
| **Langages applicables** | C# 7.0+ |
| **Valeurs** | `true` - Préférer les fonctions locales aux fonctions anonymes<br /><br />`false` - Préférer les fonctions anonymes aux fonctions locales |
| **Valeur par défaut de Visual Studio** | `true:suggestion` |

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

#### <a name="csharp_using_directive_placement"></a>csharp\_using\_directive_placement

|||
|-|-|
| **Nom de la règle** | csharp_using_directive_placement |
| **ID de règle** | IDE0065 |
| **Langages applicables** | C# |
| **Valeurs** | `outside_namespace` - Préférer les directives `using` devant être placées en dehors de l’espace de noms<br /><br />`inside_namespace` - Préférer les directives `using` devant être placées dans l’espace de noms |
| **Valeur par défaut de Visual Studio** | `outside_namespace:silent` |

Exemples de code :

```csharp
// csharp_using_directive_placement = outside_namespace
using System;

namespace Conventions
{
    ...
}

// csharp_using_directive_placement = inside_namespace
namespace Conventions
{
    using System;
    ...
}
```

#### <a name="csharp_prefer_static_local_function"></a>csharp\_prefer\_static\_local_function

|||
|-|-|
| **Nom de la règle** | csharp_prefer_static_local_function |
| **ID de règle** | IDE0062 |
| **Langages applicables** | C# 8.0+ |
| **Valeurs** | `true` - Préférer le marquage des fonctions locales en tant que `static`<br /><br />`false` - Ne pas préférer le marquage des fonctions locales en tant que `static` |
| **Valeur par défaut de Visual Studio** | `true:suggestion` |

Exemples de code :

```csharp
// csharp_prefer_static_local_function = true
void M()
{
    Hello();
    static void Hello()
    {
        Console.WriteLine("Hello");
    }
}

// csharp_prefer_static_local_function = false
void M()
{
    Hello();
    void Hello()
    {
        Console.WriteLine("Hello");
    }
}
```

#### <a name="csharp_prefer_simple_using_statement"></a>csharp\_prefer\_simple\_using_statement

|||
|-|-|
| **Nom de la règle** | csharp_prefer_simple_using_statement |
| **ID de règle** | IDE0063 |
| **Langages applicables** | C# 8.0+ |
| **Valeurs** | `true` - Préférer l’utilisation d’une instruction `using` *simple*<br /><br />`false` - Ne pas préférer l’utilisation d’une instruction `using` *simple* |
| **Valeur par défaut de Visual Studio** | `true:suggestion` |

Exemples de code :

```csharp
// csharp_prefer_simple_using_statement = true
using var a = b;

// csharp_prefer_simple_using_statement = false
using (var a = b) { }
```

#### <a name="csharp_style_prefer_switch_expression"></a>csharp\_style\_prefer\_switch_expression

|||
|-|-|
| **Nom de la règle** | csharp_style_prefer_switch_expression |
| **ID de règle** | IDE0066 |
| **Langages applicables** | C# 8.0+ |
| **Valeurs** | `true` - Utilisez plutôt une expression `switch` (nouveauté de C# 8.0)<br /><br />`false` - Utilisez plutôt une [instruction switch](/dotnet/csharp/language-reference/keywords/switch) |
| **Valeur par défaut de Visual Studio** | `true:suggestion` |
| **Version introduite** | Visual Studio 2019 version 16.2 |

Exemples de code :

```csharp
// csharp_style_prefer_switch_expression = true
return x switch
{
    1 => 1 * 1,
    2 => 2 * 2,
    _ => 0,
};

// csharp_style_prefer_switch_expression = false
switch (x)
{
    case 1:
        return 1 * 1;
    case 2:
        return 2 * 2;
    default:
        return 0;
}
```

## <a name="see-also"></a>Voir aussi

- [Conventions de mise en forme](editorconfig-formatting-conventions.md)
- [Conventions d’attribution d’un nom](editorconfig-naming-conventions.md)
- [Paramètres des conventions de codage .NET pour EditorConfig](editorconfig-code-style-settings-reference.md)
