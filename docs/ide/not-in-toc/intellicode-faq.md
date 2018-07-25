---
title: Questions et réponses sur IntelliCode
ms.date: 07/12/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
manager: douge
author: markw-t
ms.author: mwthomas
ms.openlocfilehash: 79e18778eae231d16cf32c0fa68bcb6f5564b09d
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/17/2018
ms.locfileid: "39079309"
---
# Questions fréquentes (FAQ) sur Visual Studio IntelliCode

Merci de vous intéresser à Visual Studio IntelliCode ! Nous espérons que ce petit FAQ répondra à certaines des questions que vous vous posez peut-être.

## Q. Qu’est-ce que Visual Studio IntelliCode ?

Dans la Build 2018, Microsoft a annoncé Visual Studio IntelliCode, une nouvelle fonctionnalité qui améliore le développement logiciel avec l’intelligence artificielle (IA). IntelliCode aide les développeurs et les équipes à coder avec confiance, à trouver plus rapidement les problèmes et à se concentrer sur les revues du code.

Un premier aperçu a montré comment IntelliCode améliore le processus de développement logiciel de plusieurs manières :

- Il fournit une complétion de code en fonction du contexte.
- Il aide les développeurs à respecter les modèles et les styles de leur équipe.
- Il trouve des problèmes de codage difficiles à détecter.
- Il facilite les revues de code en attirant l’attention sur les problèmes qui sont vraiment importants.

Les développeurs trouveront plus d’informations sur IntelliCode et pourront s’inscrire pour connaître les nouveautés et obtenir les prochaines préversions privées sur [https://aka.ms/intellicode](https://aka.ms/intellicode).

## Q. Que peuvent faire les clients avec Visual Studio IntelliCode ?

Visual Studio IntelliCode est constitué de différentes fonctionnalités qui offrent de nouvelles améliorations de productivité via l’intelligence artificielle (IA).

Les développeurs peuvent [télécharger une extension expérimentale](https://go.microsoft.com/fwlink/?linkid=872707) pour Visual Studio 2017 version 15.7 et ultérieure. L’extension fournit actuellement ce qui suit :

- Fonctionnalité IntelliSense améliorée grâce à l’AI, qui prédit l’API la plus probablement correcte que le développeur doit utiliser, au lieu de simplement présenter une liste alphabétique des membres. Elle utilise le contexte actuel du code du développeur et des modèles pour fournir cette liste dynamique.

- Inférence des conventions de style et de mise en forme de code, qui aide à préserver la cohérence du code en créant dynamiquement un [fichier .editorconfig](../create-portable-custom-editor-options.md) à partir de votre base de code pour définir des styles et formats de codage. Ces conventions permettent à Visual Studio d’offrir des correctifs de format et de style automatiques pour nettoyer votre document.

Nous allons mettre à jour l’extension en ajoutant des fonctionnalités dans les mois à venir.

## Q. Pourquoi l’inférence EditorConfig ajoute-t-elle 1 au nom de fichier ?

Un problème connu dans l’extensibilité de Visual Studio entraîne l’ajout d’un 1 devant le nom du fichier .editorconfig quand vous le créez en effectuant un clic droit et en choisissant **Ajouter > Nouvel élément**. Les fichiers nommés de cette façon ne sont pas reconnus par le processeur d’editorconfig dans Visual Studio. Ce problème est résolu dans Visual Studio 2017 version 15.8 Préversion 4, mais en attendant vous pouvez le contourner en supprimant le 1 dans la boîte de dialogue **Ajouter un nouvel élément**.

## Q. Mes conventions EditorConfig ne semblent pas prendre effet ; pourquoi ?
Il existe deux raisons courantes à ce problème :

- Dans les versions de Visual Studio 2017 antérieures à 15.8 Préversion 3, vous devez fermer puis rouvrir tous les documents ouverts pour que les conventions dans le fichier EditorConfig que vous créez prennent effet. Ce problème est résolu dans la version 15.8 Préversion 3.
- Les conventions de mise en forme n’apparaissent jamais dans la **Liste d’erreurs** ou sous forme de « tildes » dans votre code. Elles peuvent, toutefois, être corrigées à l’aide de la nouvelle extension Format du document (Ctrl+K, Ctrl+D) dans Visual Studio 2017 version 15.8 Préversion 3 ou version ultérieure.

## Q. Pourquoi Format du document ne corrige-t-il pas mes conventions de style ?
Il existe deux raisons courantes à ce problème :

- Vous n’utilisez peut-être pas Visual Studio 2017 version 15.8 Préversion 3 ou version ultérieure. Vous aurez besoin de cette version pour pouvoir utiliser la commande « Format du document » étendue afin d’effectuer un nettoyage supplémentaire du code pour le document actif.
- Il se peut que les correctifs de style ne soient pas activés. La capacité étendue de correction des problèmes liés aux conventions dans Format du document couvre uniquement un ensemble fixe de problèmes. Vous pouvez modifier les problèmes qui sont résolus dans **Outils-Options** sous **Éditeur de texte > C# > Style de code > Mise en forme > Général > Paramètres de mise en forme de document (essai)**. Notez que les paramètres par défaut ne résolvent pas certaines conventions de style. Vous pouvez activer ces corrections par le biais d’**Outils > Options**. Par exemple « Appliquer les préférences de type implicite/explicite » exécutera des règles de style concernant l’utilisation de `var`.

## Q. Quelles conventions d’EditorConfig Visual Studio IntelliCode peut-il déduire ?

Cette fonctionnalité étant à l’heure actuelle expérimentale, nous ne prenons pas encore en charge l’ensemble complet des conventions décrites dans la [référence des paramètres de style de code](../editorconfig-code-style-settings-reference.md).

IntelliCode peut actuellement déduire les conventions suivantes :

Conventions de mise en forme :

-   csharp_space_between_method_declaration_parameter_list_parentheses
-   csharp_space_between_method_declaration_empty_parameter_list_parentheses
-   csharp_space_between_method_call_name_and_opening_parenthesis
-   csharp_space_between_method_call_parameter_list_parentheses
-   csharp_space_between_method_call_empty_parameter_list_parentheses
-   csharp_space_after_keywords_in_control_flow_statements
-   csharp_space_between_parentheses
-   csharp_space_after_cast
-   csharp_space_after_colon_in_inheritance_clause
-   csharp_space_before_colon_in_inheritance_clause
-   csharp_space_around_binary_operators
-   csharp_indent_switch_labels
-   csharp_indent_case_contents
-   csharp_indent_case_contents_when_block
-   csharp_indent_labels
-   csharp_preserve_single_line_blocks
-   csharp_preserve_single_line_statements
-   csharp_new_line_before_open_brace
-   csharp_new_line_before_else
-   csharp_new_line_before_catch
-   csharp_new_line_before_finally
-   csharp_new_line_before_members_in_object_initializers
-   csharp_new_line_before_members_in_anonymous_types
-   csharp_new_line_between_query_expression_clauses

Conventions de style
-   csharp__new_line_before_catch
-   csharp_new_line_before_else
-   csharp_new_line_before_members_in_anonymous_types
-   csharp_new_line_before_members_in_object_initializers
-   csharp_new_line_before_finally_style
-   csharp_new_line_between_query_expression_clauses
-   csharp_prefer_braces_style
-   csharp_preferred_modifier_order_style
-   csharp_prefer_simple_default_expression
-   csharp_preserve_single_line_blocks
-   csharp_space_after_cast
-   csharp_space_after_keywords_in_control_flow_statements
-   csharp_space_between_method_call_parameter_list_parentheses
-   csharp_space_between_method_declaration_parameter_list_parentheses
-   csharp_space_between_parentheses
-   csharp_style_expression_bodied_accessors
-   csharp_style_expression_bodied_constructors
-   csharp_style_expression_bodied_indexers
-   csharp_style_expression_bodied_methods
-   csharp_style_expression_bodied_operators
-   csharp_style_expression_bodied_properties
-   csharp_style_inlined_variable_declaration
-   csharp_style_pattern_local_over_anonymous_function
-   csharp_style_pattern_matching_over_as_with_null_check
-   csharp_style_var_for_built_in_types
-   csharp_style_var_when_type_is_apparent
-   dotnet_sort_system_directives_first
-   dotnet_style_explicit_tuple_names
-   dotnet_style_object_initializer
-   dotnet_style_predefined_type_for_locals_parameters_members
-   dotnet_style_predefined_type_for_member_access
-   dotnet_style_prefer_inferred_anonymous_type_member_names
-   dotnet_style_qualification_for_event
-   dotnet_style_qualification_for_field
-   dotnet_style_qualification_for_method
-   dotnet_style_qualification_for_property
-   dotnet_style_require_accessibility_modifiers

## Q. Existe-t-il d’autres fonctionnalités à venir pour l’extension IntelliCode de Visual Studio ?

Nous travaillons activement sur un certain nombre de fonctionnalités que nous sommes heureux de partager publiquement à mesure qu’elles deviennent disponibles. Vous pouvez vous inscrire pour connaître les nouveautés et les mises à jour sur le site [https://aka.ms/intellicode](https://aka.ms/intellicode) pour être le premier informé quand de nouvelles fonctionnalités sont disponibles.

## Q : En quoi « IntelliSense assisté par IA » s’appuyant sur la technologie IntelliCode est-il meilleur que la version normale d’IntelliSense ?

Avec IntelliCode, la liste de complétion suggère l’API la plus probablement correcte qu’un développeur doit utiliser, au lieu de présenter une simple liste alphabétique des membres. Il utilise le contexte actuel du code du développeur et des modèles, en se basant sur 2 000 projets open source de grande qualité ayant obtenu plus de 100 étoiles sur GitHub pour fournir cette liste dynamique. Les résultats forment un modèle qui prédit les appels d’API les plus probables et les plus pertinents.

## Q : Quelle est la qualité des suggestions de complétion de code d’IntelliCode ?

Chez Microsoft, nous utilisons les recommandations d’IntelliCode en interne depuis un certain temps et nous estimons que ces suggestions sont utiles. Mais au final, ce seront vos propres commentaires, en votre qualité de rédacteur de code, qui détermineront ses performances et son utilité réelles. Nous vous encourageons vivement à essayer l’[extension IntelliCode](https://go.microsoft.com/fwlink/?linkid=872707) de Visual Studio. N’hésitez pas à nous faire part de vos commentaires sur son usage. Nous formerons également notre modèle en fonction de ce que vous choisirez dans nos recommandations et nous mettrons à jour l’extension à mesure que le modèle s’améliorera.

> [!NOTE]
> Votre code défini par l’utilisateur ne sera pas collecté. Consultez la question sur la [confidentialité](#privacy).

## Q. Quel est l’avenir d’IntelliCode ?

Nous allons explorer de nombreuses façons d’améliorer la productivité des développeurs avec l’IA et d’autres techniques avancées. Dans Microsoft Build 2018, nous vous avons montré un premier aperçu de certains des scénarios où nous pensons que l’IA peut aider les développeurs, mais il y en a encore tant d’autres ! Nous sommes intéressés par les commentaires des développeurs qui ont testé ce que nous avons montré, alors n’hésitez pas à vous inscrire pour connaître les nouveautés et les mises à jour sur [https://aka.ms/intellicode](https://aka.ms/intellicode).

## Q. Quel est son coût ?

Nous n’avons jusqu’à présent fait aucune annonce concernant son prix.

## Q. Quand la version finale d’IntelliCode sera-t-elle disponible ?

La fonctionnalité IntelliSense assistée par IA d’IntelliCode est actuellement dans sa première préversion expérimentale. Nous allons continuer à mettre à jour l’extension expérimentale en ajoutant d’autres fonctionnalités au fil du temps. Nous n’avons aucun calendrier pour une version finale, mais nous prenons en compte les commentaires des développeurs afin de pouvoir offrir les meilleures expériences possibles. Vous pouvez vous inscrire pour connaître les nouveautés et les mises à jour sur [https://aka.ms/intellicode](https://aka.ms/intellicode).

## Q. Cette fonctionnalité est-elle disponible seulement dans Visual Studio et pour C# ?

L’expérience a été présentée dans la Build 2018 de Visual Studio 2017 sur un code base C#. Mais nous sommes impatients d’étendre IntelliCode à d’autres langages et d’autres outils de la famille Visual Studio.

## Q. <a name="whynointellisense"/> Je ne peux pas voir les suggestions IntelliCode dans mon expérience d’édition C#. Que se passe-t-il ?

Les suggestions IntelliCode s’affichent dans l’interface utilisateur de Visual Studio IntelliSense standard pour C#. Les extensions qui remplacent cette interface utilisateur empêchent les suggestions IntelliCode « marquées d’une étoile » de s’afficher en haut de la liste. Vous pouvez vérifier si les extensions sont à l’origine de ce comportement en les désactivant, puis en réessayant IntelliSense.

Si cela ne résout pas le problème, signalez-le en utilisant la fonctionnalité [Signaler un problème](https://docs.microsoft.com/en-us/visualstudio/ide/how-to-report-a-problem-with-visual-studio-2017) de Visual Studio, et mentionnez IntelliCode dans votre rapport.

## Q. De quelle version de Visual Studio ai-je besoin pour exécuter cette extension ?

L’extension IntelliCode de Visual Studio est prise en charge sur Visual Studio 2017 version 15.7 (préversion 5) et ultérieure (toutes les références SKU). L’installation de l’extension s’arrête avec le message « Cette extension n’est installée sur aucun des produits actuellement installés. » si la version minimale requise n’est pas installée sur votre ordinateur.

## Q. Cette fonctionnalité est-elle disponible seulement en anglais ?

IntelliCode est aujourd’hui une extension en préversion. Nous souhaiterions vivement connaître dans quelle mesure ces fonctionnalités son utiles pour un large éventail de clients. Quand IntelliCode ne sera plus en préversion, nous prendrons assurément vos commentaires en compte quand nous définirons les paramètres régionaux et la langue pris en charge, ainsi que le mode d’empaquetage.

## <a name="privacy"/> Q : Qu’en est-il de la confidentialité ? Envoyez-vous mon code dans le cloud ? Quelles sont les données des clients envoyées à Microsoft ?

Les développeurs sont invités à expérimenter Visual Studio IntelliCode aujourd’hui sous la forme d’une extension en préversion expérimentale. L’objectif de l’extension est de permettre aux développeurs de tester les fonctionnalités IntelliCode et d’envoyer des commentaires à l’équipe du produit.

Nous capturons avec l’extension certaines données d’utilisation et de rapports d’erreurs anonymisées pour améliorer le produit. Aucun code défini par l’utilisateur n’est envoyé à Microsoft, mais nous collectons des informations sur votre utilisation des résultats d’IntelliCode. Les données incluent seulement les types et les membres .NET open source que vous avez sélectionnés dans la liste des suggestions d’IntelliCode. Les développeurs peuvent refuser le [Programme d’amélioration de l’expérience utilisateur Visual Studio](../../ide/visual-studio-experience-improvement-program.md), ce qui désactive également la collecte de données pour l’extension IntelliCode. Dans la barre de menus, sélectionnez **Aide** > **Envoyer des commentaires** > **Paramètres**. Dans la boîte de dialogue **Programme d’amélioration du produit Visual Studio**, sélectionnez **Non, je ne souhaite pas participer**, puis sélectionnez **OK**.

L’extension IntelliCode peut demander régulièrement au développeur de répondre à une enquête, qui est également anonymisée. Les utilisateurs peuvent s’inscrire pour obtenir les nouveautés et une préversion privée, mais ce n’est actuellement pas obligatoire pour utiliser l’extension expérimentale.

Des fonctionnalités futures pourront exiger l’accès à un service, ce qui nécessitera une inscription. Nous publierons plus de détails quand ces fonctionnalités seront prêtes pour la préversion privée.
