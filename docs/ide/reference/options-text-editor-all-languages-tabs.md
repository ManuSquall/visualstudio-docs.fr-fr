---
title: Options, Éditeur de texte, Tous les langages, Onglets
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.All_Languages.Tabs
- VS.ToolsOptionsPages.Text_Editor.Basic.Tabs
- VS.ToolsOptionsPages.Text_Editor.CSharp.Tabs
- VS.ToolsOptionsPages.Text_Editor.C%2FC%2B%2B.Tabs
- VS.ToolsOptionsPages.Text_Editor.CoffeeScript.Tabs
- VS.ToolsOptionsPages.Text_Editor.CSS.Tabs
- VS.ToolsOptionsPages.Text_Editor.Dockerfile.Tabs
- VS.ToolsOptionsPages.Text_Editor.F%2523.Tabs
- VS.ToolsOptionsPages.Text_Editor.HQL.Tabs
- VS.ToolsOptionsPages.Text_Editor.HTML.Tabs
- VS.ToolsOptionsPages.Text_Editor.HTMLX.Tabs
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Tabs
- VS.ToolsOptionsPages.Text_Editor.TypeScript.Tabs
- VS.ToolsOptionsPages.Text_Editor.JSON.Tabs
- VS.ToolsOptionsPages.Text_Editor.LESS.Tabs
- VS.ToolsOptionsPages.Text_Editor.Plain_Text.Tabs
- VS.ToolsOptionsPages.Text_Editor.ResJSON.Tabs
- VS.ToolsOptionsPages.Text_Editor.SCSS.Tabs
- VS.ToolsOptionsPages.Text_Editor.SQL_Server_Tools.Tabs
- VS.ToolsOptionsPages.Text_Editor.StreamAnalytics.Tabs
- VS.ToolsOptionsPages.Text_Editor.T-SQL90.Tabs
- VS.ToolsOptionsPages.Text_Editor.U-SQL.Tabs
- VS.ToolsOptionsPages.Text_Editor.XAML.Tabs
- VS.ToolsOptionsPages.Text_Editor.XML.Tabs
helpviewer_keywords:
- indents, Code Editor
- Code Editor, default behavior
- tabs, setting in Code Editor
- All Languages Text Editor Options dialog box
- editors, Code Editor
- Code Editor, indenting
- Code Editor, tabs
ms.assetid: 7e208e1d-5e3a-4bf7-a27b-4417e3e049c7
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0fc169960cf757e4e334d5f77b06ff70b0d6da7c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75594745"
---
# <a name="options-text-editor-all-languages-tabs"></a>Options, Éditeur de texte, Tous les langages, Onglets

Cette boîte de dialogue vous permet de modifier le comportement par défaut de l’éditeur de code. Ces paramètres s’appliquent également à d’autres éditeurs basés sur l’éditeur de code, tels que le mode Source du concepteur HTML. Pour afficher ces options, sélectionnez **Options** dans le menu **Outils**. Dans le dossier **Éditeur de texte**, développez le sous-dossier **Tous les langages**, puis choisissez **Onglets**.

> [!CAUTION]
> Cette page définit les options par défaut pour tous les langages de développement. N’oubliez pas que la réinitialisation d’une option dans cette boîte de dialogue entraîne la réinitialisation des options des onglets dans tous les langages quels que soient les choix effectués. Pour modifier les options de l’éditeur de texte pour un seul langage, développez le sous-dossier de ce langage et sélectionnez ses pages d’options.

Si des paramètres différents sont sélectionnés dans les pages d’options Onglets pour des langages de programmation particuliers, le message « Les paramètres de mise en retrait pour les formats de texte individuels sont en conflit » s’affiche pour les options **Mise en retrait** qui diffèrent. De plus, le message « Les paramètres de tabulation pour les formats de texte individuels sont en conflit » s’affiche pour les options **Onglets** qui diffèrent. Par exemple, ce rappel s’affiche si l’option **Retrait intelligent** est sélectionnée pour Visual Basic, mais l’option **Retrait de bloc** est sélectionnée pour Visual C++.

## <a name="indenting"></a>Mise en retrait

None

Lorsque cette option est sélectionnée, les nouvelles lignes ne sont pas mises en retrait. Le point d'insertion est placé dans la première colonne d'une nouvelle ligne.

Bloquer

Lorsque cette option est sélectionnée, les nouvelles lignes sont automatiquement mises en retrait. Le point d'insertion est placé sur le même point de départ que la ligne précédente.

Intelligente

Lorsque cette option est sélectionnée, les nouvelles lignes sont positionnées en fonction du contexte de code, selon les paramètres de mise en forme d’un autre code et les conventions IntelliSense de votre langage de développement. Cette option n’est pas disponible pour tous les langages de développement.

Par exemple, les lignes comprises entre une accolade ouvrante ( { ) et une accolade fermante ( } ) peuvent automatiquement être mises en retrait d’un taquet de tabulation supplémentaire à partir de la position des accolades alignées.

## <a name="tabs"></a>Onglets

Taille des tabulation

Définit la distance en espaces entre les taquets de tabulation. La valeur par défaut est quatre espaces.

Taille du retrait

Définit la taille en espaces d'une mise en retrait automatique. La valeur par défaut est quatre espaces. Des tabulations et/ou des espaces seront insérés pour occuper la taille spécifiée.

Insérer des espaces

Lorsque cette option est sélectionnée, les opérations de mise en retrait n’insèrent que des caractères d’espacement et non des caractères de tabulation. Par exemple, si **Taille du retrait** a la valeur 5, cinq espaces sont insérés lorsque vous appuyez sur la touche Tab ou cliquez sur le bouton **Augmenter le retrait** de la barre d’outils **Mise en forme**.

Conserver les tabulations

Lorsque cette option est sélectionnée, les opérations de mise en retrait insèrent autant de caractères de tabulation que possible. Chaque caractère de tabulation remplit le nombre d’espaces spécifié dans **taille des tabulations**. Si la valeur de **Taille du retrait** n’est pas un multiple pair de la valeur de **Taille des tabulations**, des espaces sont ajoutés pour combler la différence.

## <a name="see-also"></a>Voir aussi

- [Options, Éditeur de texte, Tous les langages](../../ide/reference/options-text-editor-all-languages.md)
- [Général, environnement, boîte de dialogue Options](../../ide/reference/general-environment-options-dialog-box.md)
