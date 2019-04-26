---
title: Conventions de nommage .NET pour les fichiers EditorConfig
ms.date: 11/20/2017
ms.topic: reference
helpviewer_keywords:
- naming conventions [EditorConfig]
- EditorConfig naming conventions
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bb72f491046d16f028561c19995a27a6ab64a830
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62557302"
---
# <a name="net-naming-conventions-for-editorconfig"></a>Conventions de nommage .NET pour EditorConfig

Les conventions de nommage concernent le nommage d’éléments de code tels que les classes, les propriétés et les méthodes. Par exemple, vous pouvez spécifier que les membres publics doivent être en majuscules ou que les méthodes asynchrones doivent se terminer par « Async ». Vous pouvez appliquer ces règles en les spécifiant dans un [fichier .editorconfig](../ide/create-portable-custom-editor-options.md). Les violations des règles de nommage apparaissent dans la **Liste d’erreurs** ou sous forme de suggestion sous le nom, selon la gravité choisie pour vos règles. Il n’est pas nécessaire de générer le projet pour afficher les violations.

Les conventions de nommage doivent être classées de la plus spécifique à la moins spécifique dans le fichier EditorConfig. La première règle applicable rencontrée est la seule règle appliquée. Toutefois, s’il existe plusieurs *propriétés* de règle portant le même nom, la propriété la plus récemment trouvée portant ce nom est prioritaire. Pour plus d’informations, consultez [Priorité et hiérarchie des fichiers](create-portable-custom-editor-options.md#file-hierarchy-and-precedence).

Pour chaque convention de nommage, vous devez spécifier les symboles auxquels elle s’applique, un style de nommage et un niveau de gravité pour l’application de la convention, en utilisant les propriétés décrites ci-dessous. L’ordre des propriétés n’est pas important.

Pour commencer, choisissez un titre pour votre règle de nommage que vous utiliserez dans chacune des propriétés nécessaires pour décrire complètement la règle. Par exemple, `public_members_must_be_capitalized` est un nom descriptif correct pour une règle de nommage. Nous allons nous référer au titre que vous choisissez par **<namingRuleTitle\>** dans les sections qui suivent.

## <a name="symbols"></a>Symboles

Tout d’abord, identifiez un groupe de symboles auxquels appliquer la règle de nommage. Cette propriété se présente sous la forme suivante :

`dotnet_naming_rule.<namingRuleTitle>.symbols = <symbolTitle>`

Donnez un nom au groupe de symboles en remplaçant la valeur **< symbolTitle\>** par un titre descriptif, par exemple `public_symbols`. Vous allez utiliser la valeur **<symbolTitle\>** dans les noms des trois propriétés qui décrivent les symboles auxquels la règle est appliquée (types de symboles, niveaux d’accessibilité et modificateurs).

### <a name="kinds-of-symbols"></a>Types de symboles

Pour décrire le type de symboles auquel appliquer la règle de nommage, spécifiez une propriété au format suivant :

`dotnet_naming_symbols.<symbolTitle>.applicable_kinds = <values>`

La liste suivante répertorie les valeurs autorisées, et vous pouvez spécifier plusieurs valeurs en les séparant par une virgule.

- \* (Utilisez cette valeur pour spécifier tous les symboles.)
- namespace
- class
- struct
- interface
- enum
- propriété
- méthode
- champ
- événement
- délégué
- paramètre
- type_parameter
- locaux
- local_function

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
- locaux

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

Maintenant que nous avons identifié le groupe de symboles auquel appliquer la règle de nommage, nous devons décrire le style de nommage. Un style peut stipuler que le nom a un certain préfixe ou un certain suffixe, ou que des mots individuels inclus dans le nom sont séparés par un certain caractère. Vous pouvez également spécifier un style de mise en majuscules. La propriété de style se présente sous la forme suivante :

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

## <a name="severity"></a>Gravité

Pour décrire la gravité d’une violation de votre règle de nommage, spécifiez une propriété au format suivant :

`dotnet_naming_rule.<namingRuleTitle>.severity = <value>`

Le tableau suivant montre les valeurs de gravité autorisées, ainsi que leur signification :

Gravité | Effet
------------ | -------------
none ou silent | Quand ce style n’est pas suivi, ne rien afficher à l’utilisateur ; toutefois, le code généré automatiquement suit ce style.
suggestion | Quand ce style n’est pas suivi, l’afficher à l’utilisateur comme suggestion, sous la forme de points de soulignement sur les deux premiers caractères. Il n’a aucun effet au moment de la compilation.
warning | Quand ce style n’est pas suivi, afficher un avertissement du compilateur dans la **Liste d’erreurs**.
error | Quand ce style n’est pas suivi, afficher une erreur du compilateur dans la **Liste d’erreurs**.

> [!NOTE]
> Vous n’avez pas à générer votre projet pour afficher les violations de règle de nommage. Elles apparaissent au fur et à mesure que le code est modifié, dans la **Liste d’erreurs** ou comme suggestion.

## <a name="example"></a>Exemple

Le fichier *.editorconfig* suivant contient une convention de nommage qui spécifie que les propriétés publiques, les méthodes, les champs, les événements et les délégués doivent être mis en majuscules. Notez que cette convention de nommage spécifie plusieurs types de symboles auxquels appliquer la règle, en utilisant une virgule pour séparer les valeurs.

```EditorConfig
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

```EditorConfig
dotnet_naming_rule.public_members_must_be_capitalized.severity = warning
```

Si vous fermez et que vous rouvrez votre fichier de code, au lieu de voir la suggestion sous la violation de nom, vous voyez une ligne ondulée verte et un avertissement dans la **Liste d’erreurs** :

![Avertissement de règle de nommage](media/editorconfig-naming-rule-warning.png)

## <a name="see-also"></a>Voir aussi

- [Langage .NET et conventions de mise en forme](../ide/editorconfig-code-style-settings-reference.md)
- [Créer des options d’éditeur personnalisées et portables](../ide/create-portable-custom-editor-options.md)
- [Fichier .editorconfig de .NET Compiler Platform](https://github.com/dotnet/roslyn/blob/master/.editorconfig)
