---
title: Préférences de style de code Visual Studio
ms.date: 03/10/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Code_Style.General
- VS.ToolsOptionsPages.Text_Editor.Basic.Code_Style.General
ms.workload:
- multiple
ms.openlocfilehash: 6dd046fa8a01cde7abdc33484da3ff8227eda966
ms.sourcegitcommit: 046a9adc5fa6d6d05157204f5fd1a291d89760b7
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/11/2018
---
# <a name="code-style-preferences"></a>Préférences de style de code

Vous pouvez définir les préférences de style de code pour vos projets C# et Visual Basic dans la boîte de dialogue **Options** accessible à partir du menu **Outils**. Sélectionnez **Éditeur de texte** > **C#** ou  **De base** > **Style de code** > **Général**. Les options définies dans cette fenêtre sont applicables à l’ordinateur local.

Chaque élément de la liste affiche un aperçu de la préférence sélectionnée :

![Options de style de code](media/code-style-quick-actions-dialog.png)

## <a name="preference-and-severity"></a>Préférence et gravité

Pour chaque élément, vous pouvez définir les valeurs **Préférence** et **Gravité** en utilisant les listes déroulantes sur chaque ligne. L’option Gravité peut avoir la valeur **Aucune**, **Suggestion**, **Avertissement** ou **Erreur**. Si vous souhaitez activer les [actions rapides](../ide/quick-actions.md) pour un style de code, assurez-vous que la valeur de l’option **Gravité** n’est pas **Aucune**. L’icône en forme d’ampoule Actions rapides ![Petite icône en forme d’ampoule](media/vs2015_lightbulbsmall.png) s’affiche quand un style autre que par défaut est utilisé, et vous pouvez choisir une option dans la liste Actions rapides pour réécrire automatiquement le code avec le style par défaut.

## <a name="editorconfig-files"></a>Fichiers EditorConfig

Les paramètres de style de code pour .NET peuvent également être gérés avec un fichier [EditorConfig](../ide/editorconfig-code-style-settings-reference.md). Les paramètres du fichier EditorConfig sont prioritaires sur les options sélectionnées dans la boîte de dialogue **Options**. Vous pouvez utiliser le fichier EditorConfig pour appliquer et configurer le style de codage pour l’intégralité de votre référentiel ou projet.

## <a name="see-also"></a>Voir aussi

- [Actions rapides](../ide/quick-actions.md)
- [Paramètres des conventions de codage .NET pour EditorConfig](../ide/editorconfig-code-style-settings-reference.md)