---
title: Options de mise en forme de l’éditeur C#
ms.date: 08/14/2018
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.Spacing
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.NewLines
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.Indentation
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.Wrapping
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.General
- VS.ToolsOptionsPages.Text_Editor.CSharp.Code_Style.Formatting.General
helpviewer_keywords:
- formatting options [C#]
- Text editor Options dialog box, formatting
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 57d95cd3f3dcf68e7af143bdde3a16474beda20c
ms.sourcegitcommit: c025a5e2013c4955ca685092b13e887ce64aaf64
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2020
ms.locfileid: "91659275"
---
# <a name="options-dialog-box-text-editor--c--code-style--formatting"></a>Boîte de dialogue Options : éditeur de texte \> \> \> mise en forme du style de code C#

Utilisez la page d’options **Mise en forme** et ses sous-pages ([**Mise en retrait**](#indentation-page), **Nouvelles lignes**, **Espacement** et **Retour à la ligne**) pour définir les options de mise en forme du code dans l’éditeur de code.

Pour accéder à cette page d’options, choisissez **Outils**  >  **options** dans la barre de menus. Dans la boîte de dialogue **Options**, choisissez **Éditeur de texte** > **C#** > **Style de code** > **Mise en forme**.

> [!TIP]
> Les sous-pages **Mise en retrait**, **Nouvelles lignes**, **Espacement** et **Retour à la ligne** affichent toutes une fenêtre d’aperçu au bas de l’écran qui montrent l’effet de chaque option. Pour utiliser la fenêtre d’aperçu, sélectionnez une option de mise en forme. La fenêtre d’aperçu montre un exemple de l’option sélectionnée. Quand vous changez un paramètre en sélectionnant une case d’option ou en cochant une case, la fenêtre d’aperçu se met à jour pour afficher l’effet du nouveau paramètre.

## <a name="formatting-general-page"></a>Page Mise en forme (Général)

### <a name="general-settings"></a>Paramètres généraux :

Ces paramètres affectent le *moment* où l’éditeur de code applique les options de mise en forme au code.

|Étiquette|Description|
|-----------|-----------------|
|**Mise en forme automatique en cours de frappe**|Quand cette option est désélectionnée, les options **Mettre en forme automatiquement l’instruction lors de la saisie d’un ;** et **Mise en forme automatique du bloc lors de la saisie d’une }** sont désactivées.|
|**Mise en forme automatique de l’instruction lors de la saisie d’un ;**|Quand elle est sélectionnée, cette option met en forme les instructions conformément aux options sélectionnées pour l’éditeur, dès la fin de l’instruction.|
|**Mise en forme automatique du bloc lors de la saisie d’une }**|Quand elle est sélectionnée, cette option met en forme les blocs de code conformément aux options sélectionnées pour l’éditeur, dès la fin du bloc de code.|
|**Mise en forme automatique au retour**|Quand elle est sélectionnée, cette option met en forme le texte après un appui sur la touche **Entrée**, conformément aux options sélectionnées pour l’éditeur.|
|**Mise en forme automatique lors du collage**|Quand elle est sélectionnée, cette option met en forme le texte collé dans l’éditeur conformément aux options sélectionnées pour l’éditeur.|

::: moniker range="vs-2019"

Si vous avez précédemment appliqué des paramètres de style de code pour les fichiers C# via la commande **Mettre en forme le document** dans Visual Studio 2017, cette fonctionnalité est désormais disponible sous l’intitulé [**Nettoyage du code**](../code-styles-and-code-cleanup.md#apply-code-styles).

::: moniker-end

::: moniker range="vs-2017"

### <a name="format-document-settings"></a>Paramètres de mise en forme de document

Ces paramètres permettent de configurer la commande **Mettre le document en forme** pour effectuer du nettoyage de code supplémentaire dans un fichier. Pour plus d’informations sur l’application de ces paramètres, consultez [Mettre le document en forme, commande](../code-styles-and-code-cleanup.md#apply-code-styles).

|Étiquette|Description|Règles correspondantes pour EditorConfig et Outils > Options|
|-----------|-----------------|-----------------|-----------------|
|**Appliquer toutes les règles de mise en forme C# (retrait, retour automatique à la ligne, espacement)**|La commande **Mettre le document en forme** corrige toujours les problèmes de mise en forme. Vous ne pouvez pas changer ce paramètre.| [Options EditorConfig principales](../../ide/create-portable-custom-editor-options.md)<br/>[Options de mise en forme EditorConfig .NET](/dotnet/fundamentals/code-analysis/style-rules/formatting-rules)<br/><br/>**Outils**  >  **Options**  >  **Éditeur**  >  de texte **C#**  >  **Mise en forme** > [mise en**retrait** ou **nouvelles lignes** ou **espacement** ou **habillage**]|
|**Effectuer un nettoyage du code supplémentaire durant la mise en forme**|Quand cette option est sélectionnée, applique les correctifs des règles spécifiées ci-dessous à la commande **Edit.FormatDocument**.| N/A |
|**Supprimer les using inutiles**|Quand cette option est sélectionnée, supprime les directives `using` inutiles au moment où **Edit.FormatDocument** se déclenche.| N/A |
|**Trier les instructions Using**|Quand cette option est sélectionnée, trie les directives `using` au moment où **Edit.FormatDocument** se déclenche.| dotnet_sort_system_directives_first<br/><br/>**Outils**  >  **Options**  >  **Éditeur**  >  de texte **C#**  >  **Paramètres avancés**  >  **Placer les directives’System’en premier lors du tri des using** |
|**Ajouter/supprimer des accolades pour les instructions de contrôle d’une seule ligne**|Quand cette option est sélectionnée, ajoute ou supprime les accolades provenant d’instructions de contrôle sur une seule ligne au moment où **Edit.FormatDocument** se déclenche.| csharp_prefer_braces<br/><br/>**Outils**  >  **Options**  >  **Éditeur**  >  de texte **C#**  >  **Style**  >  de code Préférences des blocs de **code**  >  **Préférer des accolades** |
|**Ajouter des modificateurs d’accessibilité**|Quand cette option est sélectionnée, ajoute les modificateurs d’accessibilité manquants au moment où **Edit.FormatDocument** se déclenche.| dotnet_style_require_accessibility_modifiers |
|**Trier les modificateurs d’accessibilité**|Quand cette option est sélectionnée, trie les modificateurs d’accessibilité au moment où **Edit.FormatDocument** se déclenche.| csharp_preferred_modifier_order<br/>visual_basic_preferred_modifier_order |
|**Appliquer les préférences de corps pour l’expression/le bloc**|Quand cette option est sélectionnée, convertit les membres expression-bodied en corps de bloc, ou inversement, au moment où **Edit.FormatDocument** se déclenche.| [Options EditorConfig de membre expression-bodied](/dotnet/fundamentals/code-analysis/style-rules/language-rules#expression-bodied-members)<br/><br/>**Outils**  >  **Options**  >  **Éditeur**  >  de texte **C#**  >  **Style**  >  de code **Préférences**  >  des expressions **Utilisez le corps d’expression pour les méthodes, les constructeurs, etc.** |
|**Appliquer les préférences de type implicite/explicite**|Quand cette option est sélectionnée, convertit `var` en type explicite, ou inversement, au moment où **Edit.FormatDocument** se déclenche.| [Options EditorConfig de type explicite](/dotnet/fundamentals/code-analysis/style-rules/language-rules#implicit-and-explicit-types)<br/><br/>**Outils**  >  **Options**  >  **Éditeur**  >  de texte **C#**  >  **Style**  >  de code **Préférences’var'** |
|**Appliquer les préférences de variables ‘out’ inline**|Quand cette option est sélectionnée, vous pouvez afficher les variables `out` inline, chaque fois que cela est possible et au moment où **Edit.FormatDocument** se déclenche.| csharp_style_inlined_variable_declaration<br/><br/>**Outils**  >  **Options**  >  **Éditeur**  >  de texte **C#**  >  **Style**  >  de code **Préférences**  >  des variables **Préférer la déclaration de variable Inline** |
|**Appliquer les préférences de type pour le langage/framework**|Quand cette option est sélectionnée, convertit les types de langage en types de framework, ou inversement, au moment où **Edit.FormatDocument** se déclenche.| dotnet_style_predefined_type_for_locals_parameters_members<br/>dotnet_style_predefined_type_for_member_access<br/><br/>**Outils**  >  **Options**  >  **Éditeur**  >  de texte **C#**  >  **Style**  >  de code **Préférences de type prédéfini** |
|**Appliquer les préférences d’initialisation pour l’objet/la collection**|Quand cette option est sélectionnée, utilise les initialiseurs d’objets et de collections, chaque fois que cela est possible et au moment où **Edit.FormatDocument** se déclenche.| dotnet_style_object_initializer<br/>dotnet_style_collection_initializer<br/><br/>**Outils**  >  **Options**  >  **Éditeur**  >  de texte **C#**  >  **Style**  >  de code **Préférences**  >  des expressions **Préférer l’initialiseur d’objet** ou **préférer l’initialiseur de collection** |
|**Appliquer les préférences de qualification pour ‘this.’**|Quand cette option est sélectionnée, applique les préférences pour `this.` au moment où **Edit.FormatDocument** se déclenche.| [Options EditorConfig de qualification pour this.](/dotnet/fundamentals/code-analysis/style-rules/language-rules#this-and-me)<br/><br/>**Outils**  >  **Options**  >  **Éditeur**  >  de texte **C#**  >  **Style**  >  de code **Préférences’This. '** |
|**Mettre les champs privés en lecture seule quand cela est possible**|Quand cette option est sélectionnée, rend les champs privés `readonly`, chaque fois que cela est possible et au moment où **Edit.FormatDocument** se déclenche.| dotnet_style_readonly_field<br/><br/>**Outils**  >  **Options**  >  **Éditeur**  >  de texte **C#**  >  **Style**  >  de code **Préférences**  >  de champ **Préférer ReadOnly** |
|**Supprimer les casts inutiles**|Quand cette option est sélectionnée, supprime les casts inutiles, chaque fois que cela est possible et au moment où **Edit.FormatDocument** se déclenche.| N/A |
|**Supprimer les variables inutilisées**|Quand cette option est sélectionnée, supprime les variables inutilisées au moment où **Edit.FormatDocument** se déclenche.| N/A |

![Paramètres de nettoyage du code pour C# dans Visual Studio](media/format-document-settings.png)

::: moniker-end

## <a name="indentation-page"></a>Page Mise en retrait

Les options de mise en retrait figurant dans cette page s’appliquent quand le code est mis en forme automatiquement. La mise en forme automatique du code se produit par exemple quand vous collez du code dans le fichier alors que l’option **Mettre en forme automatiquement lors du collage** est sélectionnée. (L’option **Mettre en forme automatiquement lors du collage** se trouve sous **Mise en forme** > **Général**.)

![Options de mise en retrait de l’éditeur de texte C# dans Visual Studio](media/csharp-indentation-options.png)

> [!TIP]
> Il existe également des options de mise en **Text Editor**retrait dans la  >  **C#**  >  page Options des**onglets** C# de l’éditeur de texte. Ces options déterminent uniquement l’endroit où l’éditeur de code place le curseur quand vous appuyez sur **Entrée** en fin de ligne.
>
> ![Options Onglets de l’éditeur de texte C# dans Visual Studio](media/csharp-tabs-options.png)

## <a name="see-also"></a>Voir aussi

- [Général, Environnement, boîte de dialogue Options](../../ide/reference/general-environment-options-dialog-box.md)
