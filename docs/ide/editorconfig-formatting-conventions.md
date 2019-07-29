---
title: Conventions de mise en forme .NET pour EditorConfig
ms.date: 07/17/2019
ms.topic: reference
dev_langs:
- CSharp
- VB
helpviewer_keywords:
- formatting conventions [EditorConfig]
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: ccebfc38d5170920fe3f3c37ee77aabaf660a3b8
ms.sourcegitcommit: 8562a337cc9f674c756a4a0b2c7e288ebd61b51e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/19/2019
ms.locfileid: "68345667"
---
# <a name="formatting-conventions"></a>Conventions de mise en forme

Les conventions de mise en forme liées à EditorConfig pour Visual Studio correspondent aux catégories suivantes :

- [Paramètres de mise en forme .NET](#net-formatting-settings)

- [Paramètres de mise en forme C#](#c-formatting-settings)

## <a name="rule-format"></a>Format de la règle

Règles pour les conventions de mise en forme ont le format suivant :

`rule_name = value`

Pour de nombreuses règles, vous spécifiez `true` (préférer ce style) ou `false` (ne pas préférer ce style) pour `value`. Pour les autres règles, vous spécifiez une valeur comme `flush_left` ou `before_and_after` pour décrire quand et où appliquer la règle. Vous ne spécifiez pas un niveau de gravité.

## <a name="net-formatting-settings"></a>Paramètres de mise en forme .NET

Les règles de mise en forme mentionnées dans cette section s’appliquent aux langages C# et Visual Basic.

- [Organiser les instructions using](#organize-using-directives)
  - dotnet_sort_system_directives_first
  - dotnet_separate_import_directive_groups

### <a name="organize-using-directives"></a>Organiser les directives using

Ces règles de mise en forme concernent le tri et l’affichage des directives `using` et instructions `Imports`.

Exemple de fichier *.editorconfig* :

```ini
# .NET formatting settings
[*.{cs,vb}]
dotnet_sort_system_directives_first = true
dotnet_separate_import_directive_groups = true
```

#### <a name="dotnetsortsystemdirectivesfirst"></a>dotnet\_sort\_system\_directives_first

|||
|-|-|
| **Nom de la règle** | dotnet_sort_system_directives_first |
| **Langages applicables** | C# et Visual Basic |
| **Version introduite** | Visual Studio 2017 version 15.3 |
| **Valeurs** | `true` - Trier les directives using System.* `using` par ordre alphabétique et les placer avant les autres directives using.<br /><br />`false` - Ne pas placer de directives System.* `using` avant les autres directives `using`. |
| **Valeur par défaut de Visual Studio** | `true` |

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

#### <a name="dotnetseparateimportdirectivegroups"></a>dotnet\_separate\_import\_directive\_groups

|||
|-|-|
| **Nom de la règle** | dotnet_separate_import_directive_groups |
| **Langages applicables** | C# et Visual Basic |
| **Version introduite** | Visual Studio 2017 version 15.5 |
| **Valeurs** | `true` - Placer une ligne vide entre les groupes de directives `using`.<br /><br />`false` - Ne pas placer de ligne vide entre les groupes de directives `using`. |
| **Valeur par défaut de Visual Studio** | `false` |

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

## <a name="c-formatting-settings"></a>Paramètres de mise en forme C#

Les règles de mise en forme mentionnées dans cette section s’appliquent uniquement au code C#.

- [Options de saut de ligne](#new-line-options)
  - csharp_new_line_before_open_brace
  - csharp_new_line_before_else
  - csharp_new_line_before_catch
  - csharp_new_line_before_finally
  - csharp_new_line_before_members_in_object_initializers
  - csharp_new_line_before_members_in_anonymous_types
  - csharp_new_line_between_query_expression_clauses
- [Options de mise en retrait](#indentation-options)
  - csharp_indent_case_contents
  - csharp_indent_switch_labels
  - csharp_indent_labels
  - csharp_indent_block_contents
  - csharp_indent_braces
  - csharp_indent_case_contents_when_block
- [Options d’espacement](#spacing-options)
  - csharp_space_after_cast
  - csharp_space_after_keywords_in_control_flow_statements
  - csharp_space_between_parentheses
  - csharp_space_before_colon_in_inheritance_clause
  - csharp_space_after_colon_in_inheritance_clause
  - csharp_space_around_binary_operators
  - csharp_space_between_method_declaration_parameter_list_parentheses
  - csharp_space_between_method_declaration_empty_parameter_list_parentheses
  - csharp_space_between_method_declaration_name_and_open_parenthesis
  - csharp_space_between_method_call_parameter_list_parentheses
  - csharp_space_between_method_call_empty_parameter_list_parentheses
  - csharp_space_between_method_call_name_and_opening_parenthesis
  - csharp_space_after_comma
  - csharp_space_before_comma
  - csharp_space_after_dot
  - csharp_space_before_dot
  - csharp_space_after_semicolon_in_for_statement
  - csharp_space_before_semicolon_in_for_statement
  - csharp_space_around_declaration_statements
  - csharp_space_before_open_square_brackets
  - csharp_space_between_empty_square_brackets
  - csharp_space_between_square_brackets
- [Options d’encapsulage](#wrap-options)
  - csharp_preserve_single_line_statements
  - csharp_preserve_single_line_blocks

### <a name="new-line-options"></a>Options de nouvelle ligne

Ces règles de mise en forme concernent l’utilisation de nouvelles lignes pour mettre en forme du code.

Exemple de fichier *.editorconfig* :

```ini
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

#### <a name="csharpnewlinebeforeopenbrace"></a>csharp\_new\_line\_before\_open_brace

Cette règle vise à déterminer si une accolade ouvrante `{` doit être placée sur la même ligne que le code précédent, ou sur une nouvelle ligne. Pour cette règle, vous spécifiez à la place **all**, **none**, ou un ou plusieurs éléments de code tels que **methods** ou **proprerties**, pour définir quand cette règle doit être appliquée. Pour spécifier plusieurs éléments de code, séparez-les par une virgule (,).

|||
|-|-|
| **Nom de la règle** | csharp_new_line_before_open_brace |
| **Langages applicables** | C# |
| **Version introduite** | Visual Studio 2017 version 15.3 |
| **Valeurs** | `all` - Les accolades doivent se trouver sur une nouvelle ligne pour toutes les expressions (style « Allman »).<br /><br />`none` - Les accolades doivent se trouver sur la même ligne pour toutes les expressions ("K&R").<br /><br />`accessors`, `anonymous_methods`, `anonymous_types`, `control_blocks`, `events`, `indexers`, `lambdas`, `local_functions`, `methods`, `object_collection_array_initializers`, `properties`, `types` - Nécessiter la présence d’accolades sur une nouvelle ligne pour l’élément de code spécifié (style « Allman »). |
| **Valeur par défaut de Visual Studio** | `all` |

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

#### <a name="csharpnewlinebeforeelse"></a>csharp\_new\_line\_before_else

|||
|-|-|
| **Nom de la règle** | csharp_new_line_before_else |
| **Langages applicables** | C# |
| **Version introduite** | Visual Studio 2017 version 15.3 |
| **Valeurs** | `true` - Placer les instructions `else` sur une nouvelle ligne.<br /><br />`false` - Placer les instructions `else` sur la même ligne. |
| **Valeur par défaut de Visual Studio** | `true` |

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

#### <a name="csharpnewlinebeforecatch"></a>csharp\_new\_line\_before_catch

|||
|-|-|
| **Nom de la règle** | csharp_new_line_before_catch |
| **Langages applicables** | C# |
| **Version introduite** | Visual Studio 2017 version 15.3 |
| **Valeurs** | `true` - Placer les instructions `catch` sur une nouvelle ligne.<br /><br />`false` - Placer les instructions `catch` sur la même ligne. |
| **Valeur par défaut de Visual Studio** | `true` |

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

#### <a name="csharpnewlinebeforefinally"></a>csharp\_new\_line\_before_finally

|||
|-|-|
| **Nom de la règle** | csharp_new_line_before_finally |
| **Langages applicables** | C# |
| **Version introduite** | Visual Studio 2017 version 15.3 |
| **Valeurs** | `true` - Les instructions `finally` doivent se trouver sur une nouvelle ligne après l’accolade fermante.<br /><br />`false` - Les instructions `finally` doivent se trouver sur la même ligne que l’accolade fermante. |
| **Valeur par défaut de Visual Studio** | `true` |

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

#### <a name="csharpnewlinebeforemembersinobjectinitializers"></a>csharp\_new\_line\_before\_members\_in\_object_initializers

|||
|-|-|
| **Nom de la règle** | csharp_new_line_before_members_in_object_initializers |
| **Langages applicables** | C# |
| **Version introduite** | Visual Studio 2017 version 15.3 |
| **Valeurs** | `true` - Les membres d’initialiseurs d’objet doivent être sur des lignes distinctes<br /><br />`false` - Les membres d’initialiseurs d’objet doivent être sur la même ligne |
| **Valeur par défaut de Visual Studio** | `true` |

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

#### <a name="csharpnewlinebeforemembersinanonymoustypes"></a>csharp\_new\_line\_before\_members\_in\_anonymous_types

|||
|-|-|
| **Nom de la règle** | csharp_new_line_before_members_in_anonymous_types |
| **Langages applicables** | C# |
| **Version introduite** | Visual Studio 2017 version 15.3 |
| **Valeurs** | `true` - Les membres de types anonymes doivent être sur des lignes distinctes<br /><br />`false` - Les membres de types anonymes doivent être sur la même ligne |
| **Valeur par défaut de Visual Studio** | `true` |

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

#### <a name="csharpnewlinebetweenqueryexpressionclauses"></a>csharp_new_line_between_query_expression_clauses

|||
|-|-|
| **Nom de la règle** | csharp_new_line_between_query_expression_clauses |
| **Langages applicables** | C# |
| **Version introduite** | Visual Studio 2017 version 15.3 |
| **Valeurs** | `true` - Les éléments des clauses d’expression de requête doivent se trouver sur des lignes distinctes<br /><br />`false` - Les éléments des clauses d’expression de requête doivent se trouver sur la même ligne |
| **Valeur par défaut de Visual Studio** | `true` |

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

### <a name="indentation-options"></a>Options d’indentation

Ces règles de mise en forme concernent l’utilisation de l’indentation pour mettre en forme du code.

Exemple de fichier *.editorconfig* :

```ini
# CSharp formatting settings:
[*.cs]
csharp_indent_case_contents = true
csharp_indent_switch_labels = true
csharp_indent_labels = flush_left
csharp_indent_block_contents = true
csharp_indent_braces = false
csharp_indent_case_contents_when_block = true
```

#### <a name="csharpindentcasecontents"></a>csharp\_indent\_case_contents

|||
|-|-|
| **Nom de la règle** | csharp_indent_case_contents |
| **Langages applicables** | C# |
| **Version introduite** | Visual Studio 2017 version 15.3 |
| **Valeurs** | `true` - Mettre en retrait le contenu de `switch` case<br /><br />`false` - Ne pas mettre en retrait le contenu de `switch` case |
| **Valeur par défaut de Visual Studio** | `true` |

- Quand cette règle est définie sur **true**, i.
- Quand cette règle est définie sur **false**, d.

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

#### <a name="csharpindentswitchlabels"></a>csharp\_indent\_switch_labels

|||
|-|-|
| **Nom de la règle** | csharp_indent_switch_labels |
| **Langages applicables** | C# |
| **Version introduite** | Visual Studio 2017 version 15.3 |
| **Valeurs** | `true` - Mettre en retrait les étiquettes `switch`<br /><br />`false` - Ne pas mettre en retrait les étiquettes `switch` |
| **Valeur par défaut de Visual Studio** | `true` |

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

#### <a name="csharpindentlabels"></a>csharp\_indent_labels

|||
|-|-|
| **Nom de la règle** | csharp_indent_labels |
| **Langages applicables** | C# |
| **Version introduite** | Visual Studio 2017 version 15.3 |
| **Valeurs** | `flush_left` - Les étiquettes sont positionnées au niveau de la colonne la plus à gauche<br /><br />`one_less_than_current` - Les étiquettes sont positionnées d’un retrait à gauche par rapport au contexte actuel<br /><br />`no_change` - Les étiquettes sont placées au même niveau de retrait que le contexte actuel |
| **Valeur par défaut de Visual Studio** | `no_change` |

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

#### <a name="csharpindentblockcontents"></a>csharp_indent_block_contents

|||
|-|-|
| **Nom de la règle** | csharp_indent_block_contents |
| **Langages applicables** | C# |
| **Valeurs** | `true` - <br /><br />`false` -  |
| **Valeur par défaut de Visual Studio** | `true` |

Exemples de code :

```csharp
// csharp_indent_block_contents = true
static void Hello()
{
    Console.WriteLine("Hello");
}

// csharp_indent_block_contents = false
static void Hello()
{
Console.WriteLine("Hello");
}
```

#### <a name="csharpindentbraces"></a>csharp_indent_braces

|||
|-|-|
| **Nom de la règle** | csharp_indent_braces |
| **Langages applicables** | C# |
| **Valeurs** | `true` - <br /><br />`false` -  |
| **Valeur par défaut de Visual Studio** | `false` |

Exemples de code :

```csharp
// csharp_indent_braces = true
static void Hello()
    {
    Console.WriteLine("Hello");
    }

// csharp_indent_braces = false
static void Hello()
{
    Console.WriteLine("Hello");
}
```

#### <a name="csharpindentcasecontentswhenblock"></a>csharp_indent_case_contents_when_block

|||
|-|-|
| **Nom de la règle** | csharp_indent_case_contents_when_block |
| **Langages applicables** | C# |
| **Valeurs** | `true` - <br /><br />`false` -  |
| **Valeur par défaut de Visual Studio** | `true` |

Exemples de code :

```csharp
// csharp_indent_case_contents_when_block = true
case 0:
    {
        Console.WriteLine("Hello");
        break;
    }

// csharp_indent_case_contents_when_block = false
case 0:
{
    Console.WriteLine("Hello");
    break;
}
```

### <a name="spacing-options"></a>Options d’espacement

Ces règles de mise en forme concernent l’utilisation de caractères d’espacement pour mettre en forme du code.

Exemple de fichier *.editorconfig* :

```ini
# CSharp formatting settings:
[*.cs]
csharp_space_after_cast = true
csharp_space_after_keywords_in_control_flow_statements = true
csharp_space_between_parentheses = control_flow_statements, type_casts
csharp_space_before_colon_in_inheritance_clause = true
csharp_space_after_colon_in_inheritance_clause = true
csharp_space_around_binary_operators = before_and_after
csharp_space_between_method_declaration_parameter_list_parentheses = true
csharp_space_between_method_declaration_empty_parameter_list_parentheses = false
csharp_space_between_method_declaration_name_and_open_parenthesis = false
csharp_space_between_method_call_parameter_list_parentheses = true
csharp_space_between_method_call_empty_parameter_list_parentheses = false
csharp_space_between_method_call_name_and_opening_parenthesis = false
csharp_space_after_comma = true
csharp_space_before_comma = false
csharp_space_after_dot = false
csharp_space_before_dot = false
csharp_space_after_semicolon_in_for_statement = true
csharp_space_before_semicolon_in_for_statement = false
csharp_space_around_declaration_statements = false
csharp_space_before_open_square_brackets = false
csharp_space_between_empty_square_brackets = false
csharp_space_between_square_brackets = false
```

#### <a name="csharpspaceaftercast"></a>csharp\_space\_after_cast

|||
|-|-|
| **Nom de la règle** | csharp_space_after_cast |
| **Langages applicables** | C# |
| **Version introduite** | Visual Studio 2017 version 15.3 |
| **Valeurs** | `true` - Placer un espace entre un cast et la valeur<br /><br />`false` - Supprimer l’espace entre le cast et la valeur |
| **Valeur par défaut de Visual Studio** | `false` |

Exemples de code :

```csharp
// csharp_space_after_cast = true
int y = (int) x;

// csharp_space_after_cast = false
int y = (int)x;
```

#### <a name="csharpspaceafterkeywordsincontrolflowstatements"></a>csharp_space_after_keywords_in_control_flow_statements

|||
|-|-|
| **Nom de la règle** | csharp_space_after_keywords_in_control_flow_statements |
| **Langages applicables** | C# |
| **Version introduite** | Visual Studio 2017 version 15.3 |
| **Valeurs** | `true` - Placer un espace après un mot clé dans une instruction de flux de contrôle, par exemple une boucle `for`<br /><br />`false` - Supprimer l’espace après un mot clé dans une instruction de flux de contrôle, par exemple une boucle `for` |
| **Valeur par défaut de Visual Studio** | `true` |

Exemples de code :

```csharp
// csharp_space_after_keywords_in_control_flow_statements = true
for (int i;i<x;i++) { ... }

// csharp_space_after_keywords_in_control_flow_statements = false
for(int i;i<x;i++) { ... }
```

#### <a name="csharpspacebetweenparentheses"></a>csharp_space_between_parentheses

|||
|-|-|
| **Nom de la règle** | csharp_space_between_parentheses |
| **Langages applicables** | C# |
| **Version introduite** | Visual Studio 2017 version 15.3 |
| **Valeurs** | `control_flow_statements` - Placer un espace entre les parenthèses d’instructions de flux de contrôle<br /><br />`expressions` - Placer un espace entre les parenthèses d’expressions<br /><br />`type_casts` - Placer un espace entre les parenthèses dans les casts de type |
| **Valeur par défaut de Visual Studio** | `false` |

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

#### <a name="csharpspacebeforecolonininheritanceclause"></a>csharp\_space\_before\_colon\_in\_inheritance_clause

|||
|-|-|
| **Nom de la règle** | csharp_space_before_colon_in_inheritance_clause |
| **Langages applicables** | C# |
| **Version introduite** | Visual Studio 2017 version 15.7 |
| **Valeurs** | `true` - Placer un espace avant le signe deux-points pour les bases ou les interfaces dans une déclaration de type<br /><br />`false` - Supprimer l’espace avant le signe deux-points pour les bases ou les interfaces dans une déclaration de type |
| **Valeur par défaut de Visual Studio** | `true` |

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

#### <a name="csharpspaceaftercolonininheritanceclause"></a>csharp\_space\_after\_colon\_in\_inheritance_clause

|||
|-|-|
| **Nom de la règle** | csharp_space_after_colon_in_inheritance_clause |
| **Langages applicables** | C# |
| **Version introduite** | Visual Studio 2017 version 15.7 |
| **Valeurs** | `true` - Placer un espace après le signe deux-points pour les bases ou les interfaces dans une déclaration de type<br /><br />`false` - Supprimer l’espace après le signe deux-points pour les bases ou les interfaces dans une déclaration de type |
| **Valeur par défaut de Visual Studio** | `true` |

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

#### <a name="csharpspacearoundbinaryoperators"></a>csharp\_space\_around\_binary_operators

|||
|-|-|
| **Nom de la règle** | csharp_space_around_binary_operators |
| **Langages applicables** | C# |
| **Version introduite** | Visual Studio 2017 version 15.7 |
| **Valeurs** | `before_and_after` - Insérer un espace avant et après l’opérateur binaire<br /><br />`none` - Supprimer les espaces avant et après l’opérateur binaire<br /><br />`ignore` - Ignorer les espaces autour des opérateurs binaires |
| **Valeur par défaut de Visual Studio** | `before_and_after` |

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

#### <a name="csharpspacebetweenmethoddeclarationparameterlistparentheses"></a>csharp_space_between_method_declaration_parameter_list_parentheses

|||
|-|-|
| **Nom de la règle** | csharp_space_between_method_declaration_parameter_list_parentheses |
| **Langages applicables** | C# |
| **Version introduite** | Visual Studio 2017 version 15.3 |
| **Valeurs** | `true` - Placez un espace après la parenthèse ouvrante et avant la parenthèse fermante d’une liste de paramètres de déclaration de méthode.<br /><br />`false` - Supprimer les espaces après la parenthèse ouvrante et avant la parenthèse fermante d’une liste de paramètres de déclaration de méthode |
| **Valeur par défaut de Visual Studio** | `false` |

Exemples de code :

```csharp
// csharp_space_between_method_declaration_parameter_list_parentheses = true
void Bark( int x ) { ... }

// csharp_space_between_method_declaration_parameter_list_parentheses = false
void Bark(int x) { ... }
```

#### <a name="csharpspacebetweenmethoddeclarationemptyparameterlistparentheses"></a>csharp_space_between_method_declaration_empty_parameter_list_parentheses

|||
|-|-|
| **Nom de la règle** | csharp_space_between_method_declaration_empty_parameter_list_parentheses |
| **Langages applicables** | C# |
| **Version introduite** | Visual Studio 2017 version 15.7 |
| **Valeurs** | `true` - Insérer un espace dans les parenthèses de liste de paramètres vides pour une déclaration de méthode<br /><br />`false` - Supprimer l’espace dans les parenthèses de liste de paramètres vides pour une déclaration de méthode |
| **Valeur par défaut de Visual Studio** | `false` |

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

#### <a name="csharpspacebetweenmethoddeclarationnameandopenparenthesis"></a>csharp_space_between_method_declaration_name_and_open_parenthesis

|||
|-|-|
| **Nom de la règle** | csharp_space_between_method_declaration_name_and_open_parenthesis |
| **Langages applicables** | C# |
| **Valeurs** | `true` - Placer un espace entre le nom de la méthode et la parenthèse ouvrante dans la déclaration de méthode<br /><br />`false` - Supprimer les espaces entre le nom de la méthode et la parenthèse ouvrante dans la déclaration de méthode |
| **Valeur par défaut de Visual Studio** | `false` |

Exemples de code :

```csharp
// csharp_space_between_method_declaration_name_and_open_parenthesis = true
void M () { }

// csharp_space_between_method_declaration_name_and_open_parenthesis = false
void M() { }
```

#### <a name="csharpspacebetweenmethodcallparameterlistparentheses"></a>csharp_space_between_method_call_parameter_list_parentheses

|||
|-|-|
| **Nom de la règle** | csharp_space_between_method_call_parameter_list_parentheses |
| **Langages applicables** | C# |
| **Version introduite** | Visual Studio 2017 version 15.3 |
| **Valeurs** | `true` - Placer un caractère d’espacement après la parenthèse ouvrante et avant la parenthèse fermante d’un appel de méthode<br /><br />`false` - Supprimer les espaces après la parenthèse ouvrante et avant la parenthèse fermante d’un appel de méthode |
| **Valeur par défaut de Visual Studio** | `false` |

Exemples de code :

```csharp
// csharp_space_between_method_call_parameter_list_parentheses = true
MyMethod( argument );

// csharp_space_between_method_call_parameter_list_parentheses = false
MyMethod(argument);
```

#### <a name="csharpspacebetweenmethodcallemptyparameterlistparentheses"></a>csharp_space_between_method_call_empty_parameter_list_parentheses

|||
|-|-|
| **Nom de la règle** | csharp_space_between_method_call_empty_parameter_list_parentheses |
| **Langages applicables** | C# |
| **Version introduite** | Visual Studio 2017 version 15.7 |
| **Valeurs** | `true` - Insérer un espace dans les parenthèses de la liste d’arguments vide<br /><br />`false` - Supprimer un espace dans les parenthèses de la liste d’arguments vide |
| **Valeur par défaut de Visual Studio** | `false` |

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

#### <a name="csharpspacebetweenmethodcallnameandopeningparenthesis"></a>csharp_space_between_method_call_name_and_opening_parenthesis

|||
|-|-|
| **Nom de la règle** | csharp_space_between_method_call_name_and_opening_parenthesis |
| **Langages applicables** | C# |
| **Version introduite** | Visual Studio 2017 version 15.7 |
| **Valeurs** | `true` - Insérer un espace entre le nom d’appel de méthode et la parenthèse ouvrante<br /><br />`false` - Supprimer l’espace entre le nom d’appel de méthode et la parenthèse ouvrante |
| **Valeur par défaut de Visual Studio** | `false` |

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

#### <a name="csharpspaceaftercomma"></a>csharp_space_after_comma

|||
|-|-|
| **Nom de la règle** | csharp_space_after_comma |
| **Langages applicables** | C# |
| **Valeurs** | `true` - Insérer un espace après une virgule<br /><br />`false` - Supprimer l’espace après une virgule |
| **Valeur par défaut de Visual Studio** | `true` |

Exemples de code :

```csharp
// csharp_space_after_comma = true
int[] x = new int[] { 1, 2, 3, 4, 5 };

// csharp_space_after_comma = false
int[] x = new int[] { 1,2,3,4,5 }
```

#### <a name="csharpspacebeforecomma"></a>csharp_space_before_comma

|||
|-|-|
| **Nom de la règle** | csharp_space_before_comma |
| **Langages applicables** | C# |
| **Valeurs** | `true` - Insérer un espace avant une virgule<br /><br />`false` - Supprimer l’espace avant une virgule |
| **Valeur par défaut de Visual Studio** | `false` |

Exemples de code :

```csharp
// csharp_space_before_comma = true
int[] x = new int[] { 1 , 2 , 3 , 4 , 5 };

// csharp_space_before_comma = false
int[] x = new int[] { 1, 2, 3, 4, 5 };
```

#### <a name="csharpspaceafterdot"></a>csharp_space_after_dot

|||
|-|-|
| **Nom de la règle** | csharp_space_after_dot |
| **Langages applicables** | C# |
| **Valeurs** | `true` - Insérer un espace après un point<br /><br />`false` - Supprimer l’espace après un point |
| **Valeur par défaut de Visual Studio** | `false` |

Exemples de code :

```csharp
// csharp_space_after_dot = true
this. Goo();

// csharp_space_after_dot = false
this.Goo();
```

#### <a name="csharpspacebeforedot"></a>csharp_space_before_dot

|||
|-|-|
| **Nom de la règle** | csharp_space_before_dot |
| **Langages applicables** | C# |
| **Valeurs** | `true` - Insérer un espace avant un point <br /><br />`false` - Supprimer l’espace avant un point |
| **Valeur par défaut de Visual Studio** | `false` |

Exemples de code :

```csharp
// csharp_space_before_dot = true
this .Goo();

// csharp_space_before_dot = false
this.Goo();
```

#### <a name="csharpspaceaftersemicoloninforstatement"></a>csharp_space_after_semicolon_in_for_statement

|||
|-|-|
| **Nom de la règle** | csharp_space_after_semicolon_in_for_statement |
| **Langages applicables** | C# |
| **Valeurs** | `true` - Insérer un espace après chaque point-virgule dans une instruction `for`<br /><br />`false` - Supprimer l’espace après chaque point-virgule dans une instruction `for` |
| **Valeur par défaut de Visual Studio** | `true` |

Exemples de code :

```csharp
// csharp_space_after_semicolon_in_for_statement = true
for (int i = 0; i < x.Length; i++)

// csharp_space_after_semicolon_in_for_statement = false
for (int i = 0;i < x.Length;i++)
```

##### <a name="csharpspacebeforesemicoloninforstatement"></a>csharp_space_before_semicolon_in_for_statement

|||
|-|-|
| **Nom de la règle** | csharp_space_before_semicolon_in_for_statement |
| **Langages applicables** | C# |
| **Valeurs** | `true` - Insérer un espace avant chaque point-virgule dans une instruction `for` <br /><br />`false` - Supprimer l’espace avant chaque point-virgule dans une instruction `for` |
| **Valeur par défaut de Visual Studio** | `false` |

Exemples de code :

```csharp
// csharp_space_before_semicolon_in_for_statement = true
for (int i = 0 ; i < x.Length ; i++)

// csharp_space_before_semicolon_in_for_statement = false
for (int i = 0; i < x.Length; i++)
```

#### <a name="csharpspacearounddeclarationstatements"></a>csharp_space_around_declaration_statements

|||
|-|-|
| **Nom de la règle** | csharp_space_around_declaration_statements |
| **Langages applicables** | C# |
| **Valeurs** | `ignore` - Ne pas supprimer les espaces supplémentaires dans les instructions de déclaration<br /><br />`false` - Supprimer les espaces supplémentaires dans les instructions de déclaration |
| **Valeur par défaut de Visual Studio** | `false` |

Exemples de code :

```csharp
// csharp_space_around_declaration_statements = ignore
int    x    =    0   ;

// csharp_space_around_declaration_statements = false
int x = 0;
```

#### <a name="csharpspacebeforeopensquarebrackets"></a>csharp_space_before_open_square_brackets

|||
|-|-|
| **Nom de la règle** | csharp_space_before_open_square_brackets |
| **Langages applicables** | C# |
| **Valeurs** | `true` - Insérer un espace avant les crochets ouvrants `[` <br /><br />`false` - Supprimer l’espace avant les crochets ouvrants `[` |
| **Valeur par défaut de Visual Studio** | `false` |

Exemples de code :

```csharp
// csharp_space_before_open_square_brackets = true
int [] numbers = new int [] { 1, 2, 3, 4, 5 };

// csharp_space_before_open_square_brackets = false
int[] numbers = new int[] { 1, 2, 3, 4, 5 };
```

#### <a name="csharpspacebetweenemptysquarebrackets"></a>csharp_space_between_empty_square_brackets

|||
|-|-|
| **Nom de la règle** | csharp_space_between_empty_square_brackets |
| **Langages applicables** | C# |
| **Valeurs** | `true` - Insérer un espace entre des crochets vides `[ ]` <br /><br />`false` - Supprimer l’espace entre des crochets vides `[]` |
| **Valeur par défaut de Visual Studio** | `false` |

Exemples de code :

```csharp
// csharp_space_between_empty_square_brackets = true
int[ ] numbers = new int[ ] { 1, 2, 3, 4, 5 };

// csharp_space_between_empty_square_brackets = false
int[] numbers = new int[] { 1, 2, 3, 4, 5 };
```

#### <a name="csharpspacebetweensquarebrackets"></a>csharp_space_between_square_brackets

|||
|-|-|
| **Nom de la règle** | csharp_space_between_square_brackets |
| **Langages applicables** | C# |
| **Valeurs** | `true` - Insérer des espaces entre des crochets non vides `[ 0 ]` <br /><br />`false` - Supprimer des espaces entre des crochets non vides `[0]` |
| **Valeur par défaut de Visual Studio** | `false` |

Exemples de code :

```csharp
// csharp_space_between_square_brackets = true
int index = numbers[ 0 ];

// csharp_space_between_square_brackets = false
int index = numbers[0];
```

### <a name="wrap-options"></a>Options d’encapsulage

Ces règles de mise en forme concernent l’utilisation de lignes uniques ou de lignes distinctes pour les instructions et les blocs de code.

Exemple de fichier *.editorconfig* :

```ini
# CSharp formatting settings:
[*.cs]
csharp_preserve_single_line_statements = true
csharp_preserve_single_line_blocks = true
```

#### <a name="csharppreservesinglelinestatements"></a>csharp_preserve_single_line_statements

|||
|-|-|
| **Nom de la règle** | csharp_preserve_single_line_statements |
| **Langages applicables** | C# |
| **Version introduite** | Visual Studio 2017 version 15.3 |
| **Valeurs** | `true` - Laisser les instructions et les déclarations de membre sur la même ligne<br /><br />`false` - Laisser les instructions et les déclarations de membre sur des lignes différentes |
| **Valeur par défaut de Visual Studio** | `true` |

Exemples de code :

```csharp
//csharp_preserve_single_line_statements = true
int i = 0; string name = "John";

//csharp_preserve_single_line_statements = false
int i = 0;
string name = "John";
```

#### <a name="csharppreservesinglelineblocks"></a>csharp_preserve_single_line_blocks

|||
|-|-|
| **Nom de la règle** | csharp_preserve_single_line_blocks |
| **Langages applicables** | C# |
| **Version introduite** | Visual Studio 2017 version 15.3 |
| **Valeurs** | `true` - Laisser le bloc de code sur une seule ligne<br /><br />`false` - Laisser le bloc de code sur des lignes distinctes |
| **Valeur par défaut de Visual Studio** | `true` |

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

## <a name="see-also"></a>Voir aussi

- [Conventions de langage](editorconfig-language-conventions.md)
- [Conventions d’attribution d’un nom](editorconfig-naming-conventions.md)
- [Paramètres des conventions de codage .NET pour EditorConfig](editorconfig-code-style-settings-reference.md)
