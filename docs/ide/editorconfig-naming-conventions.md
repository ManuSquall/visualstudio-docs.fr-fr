---
title: Conventions de nommage .NET pour les fichiers EditorConfig
ms.date: 03/31/2020
ms.topic: reference
helpviewer_keywords:
- naming conventions [EditorConfig]
- EditorConfig naming conventions
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ccf62c5ffc3f526eada85478f37480fcf5d75cba
ms.sourcegitcommit: 334024a43477290ecc610e70c80a0f772787a7d6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/01/2020
ms.locfileid: "80528014"
---
# <a name="net-naming-conventions-for-editorconfig"></a>Conventions de nommage .NET pour EditorConfig

Les conventions de nommage concernent le nommage d’éléments de code tels que les classes, les propriétés et les méthodes. Par exemple, vous pouvez spécifier que les membres `_`du public doivent être capitalisés ou que les champs privés doivent commencer par . Vous pouvez appliquer ces règles en les spécifiant dans un [fichier .editorconfig](../ide/create-portable-custom-editor-options.md). Les violations des règles de nommage apparaissent dans la **Liste d’erreurs** ou sous forme de suggestion sous le nom, selon la gravité choisie pour vos règles. Il n’est pas nécessaire de générer le projet pour afficher les violations.

Pour chaque convention de nommage, vous devez spécifier les symboles auxquels elle s’applique, un style de nommage et un niveau de gravité pour l’application de la convention, en utilisant les propriétés décrites ci-dessous. L’ordre des propriétés n’est pas important.

Pour commencer, choisissez un titre pour votre règle de nommage que vous utiliserez dans chacune des propriétés nécessaires pour décrire complètement la règle. Par exemple, `public_members_must_be_capitalized` est un nom descriptif correct pour une règle de nommage. Cette page se référera au titre que vous choisissez par **<namingRuleTitle\>** dans les sections qui suivent.

## <a name="symbols"></a>Symboles

Tout d’abord, identifiez un groupe de symboles auxquels appliquer la règle de nommage. Cette propriété se présente sous la forme suivante :

`dotnet_naming_rule.<namingRuleTitle>.symbols = <symbolTitle>`

Donnez un nom au groupe de symboles en remplaçant la valeur **< symbolTitle\>** par un titre descriptif, par exemple `public_symbols`. Vous allez utiliser la valeur **<symbolTitle\>** dans les noms des trois propriétés qui décrivent les symboles auxquels la règle est appliquée (types de symboles, niveaux d’accessibilité et modificateurs).

### <a name="kinds-of-symbols"></a>Types de symboles

Pour décrire le type de symboles auquel appliquer la règle de nommage, spécifiez une propriété au format suivant :

`dotnet_naming_symbols.<symbolTitle>.applicable_kinds = <values>`

La liste suivante répertorie les valeurs autorisées, et vous pouvez spécifier plusieurs valeurs en les séparant par une virgule.

- \* (Utilisez cette valeur pour spécifier tous les symboles.)
- espace de noms
- class
- struct
- interface
- enum
- propriété
- method
- field
- event
- délégué
- paramètre
- type_parameter
- local
- local_function

[!NOTE] Les membres tuple ne sont pas actuellement pris en charge.

### <a name="accessibility-levels-of-symbols"></a>Niveaux d’accessibilité des symboles

Pour décrire les niveaux d’accessibilité des symboles auxquels vous voulez appliquer la règle de nommage, spécifiez un nom de propriété au format suivant :

`dotnet_naming_symbols.<symbolTitle>.applicable_accessibilities = <values>`

La liste suivante répertorie les valeurs autorisées, et vous pouvez spécifier plusieurs valeurs en les séparant par une virgule.

- \* (Utilisez cette valeur pour spécifier tous les niveaux d’accessibilité.)
- public
- internal ou friend
- private
- protected
- protected\_internal ou protected_friend
- private\_protected
- local

   Le niveau d’accessibilité `local` s’applique aux symboles définis dans une méthode. Il est utile pour définir des conventions d’affectation de noms pour les symboles dont l’accessibilité ne peut être spécifiée dans le code. Par exemple, si vous indiquez `applicable_accessibilities = local` sur une convention d’affectation de noms pour les constantes (`required_modifiers = const`), la règle s’applique uniquement aux constantes définies au sein d’une méthode, et non dans un type.

   ```csharp
   class TypeName
   {
     // Constant defined in a type.
     const int X = 3;

     void Method()
     {
       // Constant defined in a method with "local" accessibility.
       const int Y = 4;
     }
   }
   ```

### <a name="symbol-modifiers-optional"></a>Modificateurs de symboles (facultatif)

Pour décrire les modificateurs des symboles auxquels vous voulez appliquer la règle de nommage, spécifiez un nom de propriété au format suivant :

`dotnet_naming_symbols.<symbolTitle>.required_modifiers = <values>`

La liste suivante répertorie les valeurs autorisées (séparez les valeurs par une virgule) :

- `abstract` ou `must_inherit`
- `async`
- `const`
- `readonly`
- `static` ou `shared`

   > [!NOTE]
   > S’il existe une règle d’affectation des noms pour les symboles `static` ou `shared`, elle est également appliquée aux symboles `const`, car ils sont implicitement statiques. Si vous ne souhaitez pas que la règle d’affectation des noms `static` s’applique aux symboles `const`, créez une règle d’affectation des noms distincte pour les symboles `const`.

Une règle de nommage fait correspondre les signatures contenant *tous* les modificateurs spécifiés dans `required_modifiers`. Si vous omettez cette propriété, la valeur par défaut d’une liste vide est utilisée. En d’autres termes, aucun modificateur spécifique n’est nécessaire pour une correspondance. Cela signifie que les modificateurs d’un symbole n’ont aucun effet sur l’application ou non de cette règle.

> [!TIP]
> Ne spécifiez pas une valeur `*` pour `required_modifiers`. Omettez simplement la propriété `required_modifiers` et votre règle de nommage s’appliquera à tous les types de modificateurs.

## <a name="style"></a>Style

Maintenant que vous avez identifié le groupe de symboles auquel appliquer la règle de nommage, vous pouvez décrire le style de nommage. Un style peut stipuler que le nom a un certain préfixe ou un certain suffixe, ou que des mots individuels inclus dans le nom sont séparés par un certain caractère. Vous pouvez également spécifier un style de mise en majuscules. La propriété de style se présente sous la forme suivante :

`dotnet_naming_rule.<namingRuleTitle>.style = <styleTitle>`

Nommez le style en remplaçant la valeur **<styleTitle\>** par un titre descriptif, par exemple `first_word_upper_case_style`. Vous allez utiliser la valeur **<styleTitle\>** dans les noms des propriétés qui décrivent le style de nommage (préfixe, suffixe, caractère de séparation de mots et mise en majuscules). Utilisez une ou plusieurs de ces propriétés pour décrire votre style.

### <a name="require-a-prefix"></a>Exiger un préfixe

Pour spécifier que les noms de symboles doivent commencer par certains caractères, utilisez cette propriété :

`dotnet_naming_style.<styleTitle>.required_prefix = <prefix>`

### <a name="require-a-suffix"></a>Exiger un suffixe

Pour spécifier que les noms de symboles doivent se terminer par certains caractères, utilisez cette propriété :

`dotnet_naming_style.<styleTitle>.required_suffix = <suffix>`

### <a name="require-a-certain-word-separator"></a>Exiger un certain séparateur de mots

Pour spécifier que les mots individuels inclus dans les noms de symboles doivent être séparés par un certain caractère, utilisez cette propriété :

`dotnet_naming_style.<styleTitle>.word_separator = <separator character>`

### <a name="require-a-capitalization-style"></a>Exiger un style de mise en majuscules

Pour spécifier un style de mise en majuscules particulier pour les noms de symboles, utilisez cette propriété :

`dotnet_naming_style.<styleTitle>.capitalization = <value>`

Les valeurs autorisées pour cette propriété sont :

- pascal_case
- camel_case
- first\_word_upper
- all\_upper
- all_lower

> [!NOTE]
> Vous devez spécifier un style de mise en majuscules dans le cadre de votre style de nommage, sans quoi votre style de nommage risque d’être ignoré.

## <a name="severity"></a>severity

Pour décrire la gravité d’une violation de votre règle de nommage, spécifiez une propriété au format suivant :

`dotnet_naming_rule.<namingRuleTitle>.severity = <value>`

Le tableau suivant montre les valeurs de gravité autorisées, ainsi que leur signification :

severity | Résultat
------------ | -------------
Aucun | La règle est entièrement supprimée.
refactorisation ou silence | Quand ce style n’est pas suivi, ne rien afficher à l’utilisateur ; toutefois, le code généré automatiquement suit ce style.
suggestion | Quand ce style n’est pas suivi, l’afficher à l’utilisateur comme suggestion, sous la forme de points de soulignement sur les deux premiers caractères. Il n’a aucun effet au moment de la compilation.
warning | Quand ce style n’est pas suivi, afficher un avertissement du compilateur dans la **Liste d’erreurs**.
error | Quand ce style n’est pas suivi, afficher une erreur du compilateur dans la **Liste d’erreurs**.

> [!NOTE]
> Vous n’avez pas à générer votre projet pour afficher les violations de règle de nommage. Elles apparaissent au fur et à mesure que le code est modifié, dans la **Liste d’erreurs** ou comme suggestion.

## <a name="rule-order"></a>Ordre des règles

::: moniker range="vs-2017"

Les conventions de nommage doivent être classées de la plus spécifique à la moins spécifique dans le fichier EditorConfig. La première règle applicable rencontrée est la seule règle appliquée. Toutefois, s’il existe plusieurs *propriétés* de règle portant le même nom, la propriété la plus récemment trouvée portant ce nom est prioritaire. Pour plus d’informations, consultez [Priorité et hiérarchie des fichiers](create-portable-custom-editor-options.md#file-hierarchy-and-precedence).

::: moniker-end

::: moniker range=">=vs-2019"

À partir de Visual Studio 2019 version 16.2, l’ordre dans lequel les règles de nommage sont définies dans un fichier EditorConfig n’a pas d’importance. À la place, Visual Studio trie automatiquement les règles de nommage en fonction de la définition des règles proprement dites. [L’extension du service linguistique EditorConfig](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.EditorConfig) peut analyser un fichier EditorConfig et signaler les cas où la commande de règles dans le fichier est différente de ce que le compilateur utilisera au moment de l’exécution.

Si vous utilisez une version antérieure de Visual Studio, les conventions de nommage doivent être classées de la plus spécifique à la moins spécifique dans le fichier EditorConfig. La première règle applicable rencontrée est la seule règle appliquée. Toutefois, s’il existe plusieurs *propriétés* de règle portant le même nom, la propriété la plus récemment trouvée portant ce nom est prioritaire. Pour plus d’informations, consultez [Priorité et hiérarchie des fichiers](create-portable-custom-editor-options.md#file-hierarchy-and-precedence).

::: moniker-end

## <a name="default-naming-styles"></a>Styles de dénomination par défaut

Si vous ne spécifiez pas de règles de dénomination personnalisées, Visual Studio utilise les styles par défaut suivants :

- Pour les classes, structures, énumérations, propriétés et événements avec l’accessibilité `public`, `private`, `internal`, `protected` ou `protected_internal`, le style de dénomination par défaut est la casse Pascal.

- Pour les interfaces avec l’accessibilité `public`, `private`, `internal`, `protected` ou `protected_internal`, le style de dénomination par défaut est la casse Pascal avec le préfixe **I** requis.

## <a name="example"></a>Exemple

Le fichier *.editorconfig* suivant contient une convention de nommage qui spécifie que les propriétés publiques, les méthodes, les champs, les événements et les délégués doivent être mis en majuscules. Notez que cette convention de nommage spécifie plusieurs types de symboles auxquels appliquer la règle, en utilisant une virgule pour séparer les valeurs.

```ini
# Public members must be capitalized (public_members_must_be_capitalized)
[*.{cs,vb}]
dotnet_naming_rule.public_members_must_be_capitalized.symbols   = public_symbols
dotnet_naming_symbols.public_symbols.applicable_kinds           = property,method,field,event,delegate
dotnet_naming_symbols.public_symbols.applicable_accessibilities = public
dotnet_naming_symbols.public_symbols.required_modifiers         = readonly

dotnet_naming_rule.public_members_must_be_capitalized.style    = first_word_upper_case_style
dotnet_naming_style.first_word_upper_case_style.capitalization = first_word_upper

dotnet_naming_rule.public_members_must_be_capitalized.severity = suggestion
```

La capture d’écran suivante montre l’effet de cette convention de nommage dans l’éditeur. Deux variables publiques ont été nommées sans mettre en majuscules la première lettre. L’une est `const` et l’autre est `readonly`. Étant donné que la règle de nommage s’applique uniquement aux symboles `readonly`, seule la variable `readonly` montre une suggestion de règle de nommage.

![Suggestion de règle de nommage](media/editorconfig-naming-rule-suggestion.png)

Remplaçons maintenant la gravité de la violation par `warning` :

```ini
dotnet_naming_rule.public_members_must_be_capitalized.severity = warning
```

Si vous fermez et rouvrez votre fichier de code, au lieu de voir la suggestion sous la violation du nom, vous voyez un squiggle vert et un avertissement dans la liste d’erreur:

![Avertissement de règle de nommage](media/editorconfig-naming-rule-warning.png)

## <a name="see-also"></a>Voir aussi

- [Conventions de langage](editorconfig-language-conventions.md)
- [Conventions de mise en forme](editorconfig-formatting-conventions.md)
- [Conventions d'affectation de noms Roslyn](https://github.com/dotnet/roslyn/blob/master/.editorconfig#L63)
- [Créer des options d’éditeur personnalisé portables](../ide/create-portable-custom-editor-options.md)
- [Paramètres de convention de codage .NET pour EditorConfig](editorconfig-code-style-settings-reference.md)
