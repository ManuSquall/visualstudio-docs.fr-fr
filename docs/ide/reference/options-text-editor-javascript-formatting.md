---
title: Options, Éditeur de texte, JavaScript, Mise en forme
ms.date: 10/29/2018
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Formatting.Spacing
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Formatting.General
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Formatting.New_Lines
- VS.ToolsOptionsPages.Text_Editor.TypeScript.Formatting.Spacing
- VS.ToolsOptionsPages.Text_Editor.TypeScript.Formatting.General
- VS.ToolsOptionsPages.Text_Editor.TypeScript.Formatting.New_Lines
ms.assetid: 28a0aef1-9353-4d94-95a5-54b42e15c0dc
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e995ec564d0260faac02eb3b4a0237fa9f1f89b4
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55933507"
---
# <a name="options-text-editor-javascript-formatting"></a>Options, Éditeur de texte, JavaScript, Mise en forme
Utilisez la page **Mise en forme** de la boîte de dialogue **Options** pour définir les options de mise en forme du code dans l’éditeur de code. Pour accéder à cette page, dans la barre de menus, choisissez **Outils**, **Options**, puis développez **Éditeur de texte**, **JavaScript** et **Mise en forme**.

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

## <a name="automatic-formatting"></a>Mise en forme automatique
 Ces options déterminent à quel moment la mise en forme se produit dans la vue **Source**.

### <a name="uielement-list"></a>Liste des éléments d’interface

|Option|Description|
|------------|-----------------|
|**Mettre en forme la ligne terminée après Entrée**|Quand cette option est sélectionnée et que vous appuyez sur la touche Entrée, l’éditeur de code met automatiquement en forme la ligne.|
|**Mettre en forme l’instruction terminée après ;**|Quand cette option est sélectionnée et que vous appuyez sur la touche point-virgule, l’éditeur de code met automatiquement en forme la ligne.|
|**Mettre en forme le bloc ouvert sur {**|Quand cette option est sélectionnée, l’éditeur de code met automatiquement en forme la ligne quand vous appuyez sur la touche de l’accolade fermante.|
|**Mettre en forme le bloc terminé après }**|Quand cette option est sélectionnée et que vous appuyez sur la touche accolade fermante, l’éditeur de code met automatiquement en forme la ligne.|
|**Mettre en forme lors du collage**|Quand cette option est sélectionnée et que vous collez le code dans l’éditeur de code, celui-ci remet en forme le code. L’éditeur utilise les règles de mise en forme définies. Si cette option n’est pas sélectionnée, l’éditeur utilise la mise en forme d’origine du code collé.|

## <a name="new-lines"></a>Nouvelles lignes
 Ces options déterminent si l’éditeur de code place une accolade ouvrante sur une nouvelle ligne pour les fonctions et les blocs de contrôle.

### <a name="uielement-list"></a>Liste des éléments d’interface

|Option|Description|
|------------|-----------------|
|**Placer une accolade ouvrante sur une nouvelle ligne pour les fonctions**|Quand cette option est sélectionnée, l’éditeur de code déplace l’accolade ouvrante associée à une fonction sur une nouvelle ligne.|
|**Placer l’accolade ouvrante sur une nouvelle ligne pour les blocs de contrôle**|Quand cette option est sélectionnée, l’éditeur de code déplace l’accolade ouvrante associée à un bloc de contrôle (tel que `if` et `while`) sur une nouvelle ligne.|

## <a name="spacing"></a>Espacement
 Ces options déterminent la façon dont les espaces sont insérés dans la vue **Source**.

### <a name="uielement-list"></a>Liste des éléments d’interface

|Option|Description|
|------------|-----------------|
|**Insérer un espace après la virgule de délimitation**|Quand cette option est sélectionnée, l’éditeur de code ajoute un espace après les virgules.|
|**Insérer un espace après le point-virgule dans les instructions « for »**|Quand cette option est sélectionnée, l’éditeur de code ajoute un espace après chaque point-virgule dans la première ligne d’une boucle `for`.|
|**Insérer un espace avant et après les opérateurs binaires**|Quand cette option est sélectionnée, l’éditeur de code ajoute un espace avant et après les opérateurs binaires (par exemple, +, -, &&, &#124;&#124;).|
|**Insérer un espace après les mots clés dans les instructions de flux de contrôle**|Quand cette option est sélectionnée, l’éditeur de code ajoute un espace après les mots clés JavaScript dans les instructions de flux de contrôle.|
|**Insérer un espace après le mot clé function pour les fonctions anonymes**|Quand cette option est sélectionnée, l’éditeur de code ajoute un espace après le mot clé `function` pour les fonctions anonymes.|
|**Insérer un espace après l’ouverture et avant la fermeture de parenthèses non vides**|Quand cette option est sélectionnée, l’éditeur de code ajoute un espace après la parenthèse ouvrante et avant la parenthèse fermante si celles-ci renferment des caractères non vides.|

## <a name="see-also"></a>Voir aussi

- [Général, Environnement, boîte de dialogue Options](../../ide/reference/general-environment-options-dialog-box.md)