---
title: Options, Éditeur de texte, C#, Mise en forme | Microsoft Docs
ms.date: 02/09/2018
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.Spacing
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.NewLines
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.Indentation
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.Wrapping
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.General
helpviewer_keywords:
- formatting options [C#]
- Text editor Options dialog box, formatting
ms.assetid: 5a7bb668-1d0c-4ffe-9508-24592813162e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: db7140248818cc92f95150e7a368fa0f71d1d010
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="options-text-editor-c-formatting"></a>Options, Éditeur de texte, C#, Mise en forme

Utilisez la page d’options **Mise en forme** pour définir des options de mise en forme du code dans l’éditeur de code. Pour accéder à cette page d’options, choisissez **Outils** > **Options**, puis **Éditeur de texte** > **C#** > **Style de code** > **Mise en forme**.

> [!NOTE]
> Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).

## <a name="general-settings"></a>Paramètres généraux

Les paramètres généraux affectent la façon dont l’éditeur de code applique les options de mise en forme au code.

## <a name="uielement-list"></a>Liste UIElement

|Ajouter des contrôles|Description|
|-----------|-----------------|
|**Mise en forme automatique en cours de frappe**|Quand cette option est désélectionnée, les options **Mettre en forme automatiquement l’instruction lors de la saisie d’un ;** et **Mise en forme automatique du bloc lors de la saisie d’une }** sont désactivées.|
|**Mise en forme automatique de l’instruction lors de la saisie d’un ;**|Quand elle est sélectionnée, cette option met en forme les instructions conformément aux options sélectionnées pour l’éditeur, dès la fin de l’instruction.|
|**Mise en forme automatique du bloc lors de la saisie d’une }**|Quand elle est sélectionnée, cette option met en forme les blocs de code conformément aux options sélectionnées pour l’éditeur, dès la fin du bloc de code.|
|**Mise en forme automatique au retour**|Quand elle est sélectionnée, cette option met en forme le texte après un appui sur la touche **Entrée**, conformément aux options sélectionnées pour l’éditeur.|
|**Mise en forme automatique lors du collage**|Quand elle est sélectionnée, cette option met en forme le texte collé dans l’éditeur conformément aux options sélectionnées pour l’éditeur.|

## <a name="preview-window"></a>Fenêtre Aperçu

Les volets d’options **Mise en retrait**, **Nouvelles lignes**, **Espacement** et **Retour à la ligne** offrent tous une fenêtre d’aperçu. La fenêtre d’aperçu montre l’effet de chaque option. Pour utiliser la fenêtre d’aperçu, sélectionnez une option de mise en forme. La fenêtre d’aperçu montre un exemple de l’option sélectionnée. Quand vous changez un paramètre en sélectionnant une case d’option ou en cochant une case, la fenêtre d’aperçu se met à jour pour afficher l’effet du nouveau paramètre.

## <a name="remarks"></a>Notes

Les options de mise en retrait dans les pages **Tabulations** de chaque langage déterminent uniquement l’endroit où l’éditeur de code place le curseur quand vous appuyez sur **Entrée** en fin de ligne. Les options de mise en retrait sous **Mise en forme** s’appliquent quand le code est mis en forme automatiquement, par exemple, quand vous collez du code dans le fichier alors que l’option **Mise en forme automatique lors du collage** est sélectionnée, et quand le bloc qui est mis en forme est tapé manuellement.

## <a name="see-also"></a>Voir aussi

[Général, Environnement, boîte de dialogue Options](../../ide/reference/general-environment-options-dialog-box.md)
