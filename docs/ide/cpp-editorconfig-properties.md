---
title: Conventions de mise en forme C++ EditorConfig
titleSuffix: ''
description: Découvrez comment utiliser EditorConfig pour mettre en forme le code C++ dans Visual Studio.
ms.date: 9/14/2020
author: jureid
ms.author: jureid
manager: jillfra
dev_langs:
- CPP
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.topic: reference
ms.workload:
- cplusplus
monikerRange: vs-2019
ms.openlocfilehash: 31a7db73a4487267c2a74fe628d28b577d339aba
ms.sourcegitcommit: 14637be49401f56341c93043eab560a4ff6b57f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2020
ms.locfileid: "90078840"
---
# <a name="c-editorconfig-formatting-conventions"></a>Conventions de mise en forme C++ EditorConfig

Le formateur Visual Studio C++ possède un ensemble complet de paramètres configurables qui peuvent être appliqués globalement. Pour définir les paramètres de mise en forme C++ d’un espace de travail spécifique, utilisez [clangformat](https://clang.llvm.org/docs/ClangFormat.html) ou [EditorConfig](https://editorconfig.org/). Visual Studio et Visual Studio Code disposent tous deux d’une prise en charge intégrée de EditorConfig pour chacun des paramètres de mise en forme globaux de Visual Studio C++, les paramètres EditorConfig étant prioritaires. Cela signifie que vous pouvez ajouter des fichiers EditorConfig à votre espace de travail pour configurer la mise en forme C++ à un niveau plus granulaire et appliquer un style de code cohérent pour tout le monde qui contribue au projet.

## <a name="c-formatting-conventions"></a>Conventions de mise en forme C++

Les paramètres de mise en forme C++ EditorConfig sont préfixés avec `_cpp__` . Voici un exemple de ce à quoi peut ressembler votre fichier EditorConfig :

```ini
[\*.{c++,cc,cpp,cxx,h,h++,hh,hpp,hxx,inl,ipp,tlh,tli}]

cpp_indent_case_contents_when_block = true
cpp_new_line_before_open_brace_namespace = same_line
```

Le reste de ce document répertorie tous les paramètres de mise en forme EditorConfig C++ pris en charge par Visual Studio et VS Code.

### <a name="indentation-settings"></a>Paramètres de mise en retrait

**Mettre en retrait les accolades**

- Nom : `cpp_indent_braces`
- Valeurs : `true` , `false`

**Mettez en retrait chaque ligne de façon relative à**

- Nom : `cpp_indent_multi_line_relative_to`
- Valeurs :
  - `outermost_parenthesis` -Lorsqu’une nouvelle ligne est tapée, elle est mise en retrait relativement à la parenthèse ouverte la plus à l’extérieur.
  - `innermost_parenthesis` -Lorsqu’une nouvelle ligne est tapée, elle est mise en retrait relativement à la parenthèse ouverte la plus profonde.
  - `statement_begin` -Lorsqu’une nouvelle ligne est tapée, elle est mise en retrait relativement au début de l’instruction actuelle.

**Entre parenthèses, aligner les nouvelles lignes lors de leur saisie**

- Nom : `cpp_indent_within_parentheses`
- Valeurs :
  - `align_to_parenthesis` -Aligner le contenu sur la parenthèse ouvrante.
  - `indent` -Mettre en retrait les nouvelles lignes.

**Dans le code existant, n’utilisez pas le paramètre pour l’alignement des nouvelles lignes entre parenthèses**

- Nom : `cpp_indent_preserve_within_parentheses`
- Valeurs : `true` , `false`

**Mettre en retrait le contenu de case**

- Nom : `cpp_indent_case_contents`
- Valeurs : `true` , `false`

**Mettre en retrait les étiquettes case**

- Nom : `cpp_indent_case_labels`
- Valeurs : `true` , `false`

**Mettre en retrait les accolades suivant une instruction case**

- Nom : `cpp_indent_case_contents_when_block`
- Valeurs : `true` , `false`

**Mettre en retrait les accolades d’expressions lambda utilisées en tant que paramètres**

- Nom : `cpp_indent_lambda_braces_when_parameter`
- Valeurs : `true` , `false`

**Position des étiquettes Goto**

- Nom : `cpp_indent_goto_labels`
- Valeurs :
  - `one_left` -Un retrait à gauche
  - `leftmost_column` -Déplacer vers la colonne la plus à gauche
  - `none` -Ne pas mettre en retrait

**Position des directives de préprocesseur**

- Nom : `cpp_indent_preprocessor`
- Valeurs :
  - `one_left` -Un retrait à gauche
  - `leftmost_column` -Déplacer vers la colonne la plus à gauche
  - `none` -Ne pas mettre en retrait

**Mettre en retrait les spécificateurs d’accès**

- Nom : `cpp_indent_access_specifiers`
- Valeurs : `true` , `false`

**Mettre en retrait le contenu d’espace de noms**

- Nom : `cpp_indent_namespace_contents`
- Valeurs : `true` , `false`

**Conserver le retrait des commentaires**

- Nom : `cpp_indent_preserve_comments`
- Valeurs : `true` , `false`

### <a name="newline-settings"></a>Paramètres de saut de ligne

**Position des accolades ouvrantes pour les espaces de noms**

- Nom : `cpp_new_line_before_open_brace_namespace`
- Valeurs :
  - `new_line` -Déplacer vers une nouvelle ligne
  - `same_line` -Conserver sur la même ligne, mais ajouter un espace avant
  - `ignore` -Ne pas repositionner automatiquement

**Position des accolades ouvrantes pour les types**

- Nom : `cpp_new_line_before_open_brace_type`
- Valeurs :
  - `new_line` -Déplacer vers une nouvelle ligne
  - `same_line` -Conserver sur la même ligne, mais ajouter un espace avant
  - `ignore` -Ne pas repositionner automatiquement

**Position des accolades ouvrantes pour les fonctions**

- Nom : `cpp_new_line_before_open_brace_function`
- Valeurs :
  - `new_line` -Déplacer vers une nouvelle ligne
  - `same_line` -Conserver sur la même ligne, mais ajouter un espace avant
  - `ignore` -Ne pas repositionner automatiquement

**Position des accolades ouvrantes pour les blocs de contrôle**

- Nom : `cpp_new_line_before_open_brace_block`
- Valeurs :
  - `new_line` -Déplacer vers une nouvelle ligne
  - `same_line` -Conserver sur la même ligne, mais ajouter un espace avant
  - `ignore` -Ne pas repositionner automatiquement

**Position des accolades ouvrantes pour les expressions lambda**

- Nom : `cpp_new_line_before_open_brace_lambda`
- Valeurs :
  - `new_line` -Déplacer vers une nouvelle ligne
  - `same_line` -Conserver sur la même ligne, mais ajouter un espace avant
  - `ignore` -Ne pas repositionner automatiquement
 
**Placer les accolades de portée sur des lignes distinctes**

- Nom : `cpp_new_line_scope_braces_on_separate_lines`
- Valeurs : `true` , `false`

**Pour les types vides, placer les accolades fermantes sur la même ligne que les accolades ouvrantes**

- Nom : `cpp_new_line_close_brace_same_line_empty_type`
- Valeurs : `true` , `false`

**Pour les corps de fonction vides, placer les accolades fermantes sur la même ligne que les accolades ouvrantes**

- Nom : `cpp_new_line_close_brace_same_line_empty_function`
- Valeurs : `true` , `false`

**Placer’Catch’et des mots clés similaires sur une nouvelle ligne**

- Nom : `cpp_new_line_before_catch`
- Valeurs : `true` , `false`

**Placer’Else’sur une nouvelle ligne**

- Nom : `cpp_new_line_before_else`
- Valeurs : `true` , `false`

**Placer’while’dans une boucle do-while sur une nouvelle ligne**

- Nom : `cpp_new_line_before_while_in_do_while`
- Valeurs : `true` , `false`

### <a name="spacing-settings"></a>Paramètres d’espacement

**Espacement entre les noms de fonctions et les parenthèses ouvrantes des listes d’arguments**

- Nom : `cpp_space_before_function_open_parenthesis`
- Valeurs :
  - `insert` -Insérer un espace
  - `remove` -Supprimer les espaces
  - `ignore` -Ne pas modifier les espaces

**Insérer un espace dans les parenthèses d’une liste d’arguments**

- `cpp_space_within_parameter_list_parentheses`Valeurs de nom : `true` ,`false`

**Insérer un espace entre les parenthèses lorsque la liste d’arguments est vide**

- Nom : `cpp_space_between_empty_parameter_list_parentheses`
- Valeurs : `true` , `false`

**Insérer un espace entre le mot clé et la parenthèse ouvrante dans les instructions de workflow de contrôle**

- Nom : `cpp_space_after_keywords_in_control_flow_statements`
- Valeurs : `true` , `false`

**Insérer un espace dans les parenthèses d’une instruction de contrôle**

- Nom : `cpp_space_within_control_flow_statement_parentheses`
- Valeurs : `true` , `false`

**Insérer un espace avant la parenthèse ouvrante des listes d’arguments lambda**

- Nom : `cpp_space_before_lambda_open_parenthesis`
- Valeurs : `true` , `false`

**Insérer un espace dans les parenthèses d’un cast de style C**

- Nom : `cpp_space_within_cast_parentheses`
- Valeurs : `true` , `false`

**Insérer un espace après la parenthèse fermante du cast de style C**

- Nom : `cpp_space_after_cast_close_parenthesis`
- Valeurs : `true` , `false`

**Insérer un espace entre les parenthèses d’une expression entre parenthèses**

- Nom : `cpp_space_within_expression_parentheses`
- Valeurs : `true` , `false`

**Insérer un espace avant l’accolade ouvrante des blocs**

- Nom : `cpp_space_before_block_open_brace`
- Valeurs : `true` , `false`

**Insérer un espace entre les accolades vides**

- Nom : `cpp_space_between_empty_braces`
- Valeurs : `true` , `false`

**Insérer un espace avant l’accolade ouvrante de l’initialisation uniforme et des listes d’initialiseurs**

- Nom : `cpp_space_before_initializer_list_open_brace`
- Valeurs : `true` , `false`

**Insérer un espace entre les accolades d’initialisation uniforme et les listes d’initialiseurs**

- Nom : `cpp_space_within_initializer_list_braces`
- Valeurs : `true` , `false`

**Conserver les espaces à l’intérieur d’une initialisation uniforme et des listes d’initialiseurs**

- Nom : `cpp_space_preserve_in_initializer_list`
- Valeurs : `true` , `false`

**Insérer un espace avant les crochets ouvrants**

- Nom : `cpp_space_before_open_square_bracket`
- Valeurs : `true` , `false`

**Insérer un espace entre les crochets**

- Nom : `cpp_space_within_square_brackets`
- Valeurs : `true` , `false`

**Insérer un espace avant les crochets vides**

- Nom : `cpp_space_before_empty_square_brackets`
- Valeurs : `true` , `false`

**Insérer un espace entre les crochets vides**

- Nom : `cpp_space_between_empty_square_brackets`
- Valeurs : `true` , `false`

**Grouper des crochets pour les tableaux multidimensionnels**

- Nom : `cpp_space_group_square_brackets`
- Valeurs : `true` , `false`

**Insérer un espace entre les crochets pour les expressions lambda**

- Nom : `cpp_space_within_lambda_brackets`
- Valeurs : `true` , `false`

**SpaceBetweenEmptyLambdaBrackets**

- Nom : `cpp_space_between_empty_lambda_brackets`
- Valeurs : `true` , `false`

**Insérer un espace avant les virgules**

- Nom : `cpp_space_before_comma`
- Valeurs : `true` , `false`

**Insérer un espace après les virgules**

- Nom : `cpp_space_after_comma`
- Valeurs : `true` , `false`

**Supprimer les espaces avant et après les opérateurs membres**

- Nom : `cpp_space_remove_around_member_operators`
- Valeurs : `true` , `false`

**Insérer un espace avant le signe deux-points pour base dans les déclarations de type**

- Nom : `cpp_space_before_inheritance_colon`
- Valeurs : `true` , `false`

**Insérer un espace avant le signe deux-points pour les constructeurs**

- Nom : `cpp_space_before_constructor_colon`
- Valeurs : `true` , `false`

**Supprimer l’espace avant les points-virgules**

- Nom : `cpp_space_remove_before_semicolon`
- Valeurs : `true` , `false`

**Insérer un espace après des points-virgules**

- Nom : `cpp_space_after_semicolon`
- Valeurs : `true` , `false`

**Supprimer les espaces entre les opérateurs unaires et leurs opérandes**

- Nom : `cpp_space_remove_around_unary_operator`
- Valeurs : `true` , `false`

**Espacement des opérateurs binaires**

- Nom : `cpp_space_around_binary_operator`
- Valeurs :
  - `insert` -Insérer des espaces avant et après les opérateurs binaires.
  - `remove` -Supprimez les espaces autour des opérateurs binaires.
  - `ignore` -Ne pas modifier les espaces autour des opérateurs binaires.

**Espacement des opérateurs d’assignation**

- Nom : `cpp_space_around_assignment_operator`
- Valeurs :
  - `insert` -Insérer des espaces autour des opérateurs d’assignation.
  - `remove` -Supprimez les espaces autour des opérateurs d’assignation.
  - `ignore` -Ne pas modifier les espaces autour des opérateurs d’assignation.

**Alignement des pointeurs/références**

- Nom : `cpp_space_pointer_reference_alignment`
- Valeurs :
  - `left` -Aligner à gauche.
  - `center` -Aligne le centre.
  - `right` -Aligner à droite.
  - `ignore` -Laissez le reste inchangé.

**Espacement des opérateurs conditionnels**

- Nom : `cpp_space_around_ternary_operator`
- Valeurs :
  - `insert` -Insérer des espaces autour des opérateurs conditionnels.
  - `remove` -Supprimez les espaces autour des opérateurs conditionnels.
  - `ignore` -Ne pas modifier les espaces autour des opérateurs conditionnels.

### <a name="wrapping-options"></a>Options d’ajustement

**Options d’habillage pour les blocs**

- Nom : `cpp_wrap_preserve_blocks`
- Valeurs :
  - `one_liners` -Ne pas encapsuler les blocs de code d’une ligne.
  - `all_one_line_scopes` -Ne pas encapsuler les blocs de code où les accolades ouvrantes et fermantes sont sur la ligne suivante.
  - `never` -Appliquer toujours les nouveaux paramètres de lignes pour les blocs.

## <a name="see-also"></a>Voir aussi

- [EditorConfig.org](https://editorconfig.org/)
- [Prise en charge d’EditorConfig pour un service de langage](../extensibility/supporting-editorconfig.md)
- [Fonctionnalités de l’éditeur de code](writing-code-in-the-code-and-text-editor.md)
