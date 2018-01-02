---
title: "Préférences de style de code Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 03/10/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Code_Style.General
- VS.ToolsOptionsPages.Text_Editor.Basic.Code_Style.General
ms.openlocfilehash: 24470f4fdb1a75d6ebd2743b2ade72e6195842b4
ms.sourcegitcommit: ebe9fb5eda724936f7a059d35d987c29dffdb50d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/07/2017
---
# <a name="code-style-preferences"></a>Préférences de style de code

Vous pouvez définir les préférences de style de code pour vos projets C# et Visual Basic dans la boîte de dialogue **Options** accessible à partir du menu **Outils**. Sélectionnez **Éditeur de texte**, **C#** ou **De base**, **Style de code**, **Général**. Les options définies dans cette fenêtre sont applicables à l’ordinateur local. Chaque élément de la liste affiche un aperçu de la préférence sélectionnée, comme indiqué ci-dessous.

![Options de style de code](media/code-style-quick-actions-dialog.png)

Pour chaque élément, vous pouvez définir les options **Préférence** et **Gravité** en utilisant les listes déroulantes sur chaque ligne. L’option Gravité peut avoir la valeur **None** (Aucune), **Suggestion**, **Avertissement** ou **Erreur**, et le comportement de Visual Studio s’adapte en conséquence. Si vous souhaitez utiliser les [actions rapides](quick-actions.md) avec ces styles de code pour réécrire automatiquement le code avec le style par défaut, vérifiez que la valeur du paramètre n’est pas **None** (Aucune) pour que l’icône d’ampoule ![Petite icône en forme d’ampoule](media/vs2015_lightbulbsmall.png "VS2017_LightBulbSmall") s’affiche quand les styles autres que par défaut sont utilisés. Ces préférences peuvent ensuite être appliquées en cliquant sur l’icône d’ampoule ou en appuyant sur **Ctrl+.** quand votre curseur se trouve sur la ligne de code appropriée.

Les paramètres de style de code pour .NET peuvent également être gérés avec un fichier [EditorConfig](../ide/editorconfig-code-style-settings-reference.md). Dans ce cas, les paramètres du fichier EditorConfig sont prioritaires sur les options sélectionnées dans la boîte de dialogue **Options**. Vous pouvez utiliser le fichier EditorConfig pour appliquer et configurer le style de codage pour l’intégralité de votre référentiel ou projet.

## <a name="see-also"></a>Voir aussi

[Actions rapides](quick-actions.md)  
[Paramètres des conventions de codage .NET pour EditorConfig](../ide/editorconfig-code-style-settings-reference.md)