---
title: Styles de code et actions rapides | Microsoft Docs
ms.custom: 
ms.date: 03/10/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.devlang: csharp
ms.assetid: 25bb9d99-aeff-4053-925d-2177f5e79574
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Code_Style.General
- VS.ToolsOptionsPages.Text_Editor.Basic.Code_Style.General
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 46846db26bee30841e6cb35913d533b512d01ba0
ms.openlocfilehash: acc01617fffd7465cee01267482112aac5e352fc
ms.contentlocale: fr-fr
ms.lasthandoff: 03/27/2017

---

# <a name="code-styles-and-quick-actions"></a>Styles de code et actions rapides
Les préférences de styles de code peuvent être définies pour vos projets C# et Visual Basic en ouvrant la fenêtre **Outils > Options**, puis en sélectionnant **Éditeur de texte > C# / De base > Style de code > Général**.  Les options définies dans cette fenêtre sont applicables à l’ordinateur local.  Chaque élément de la liste affiche un aperçu de la préférence sélectionnée, comme indiqué ci-dessous.

![Options de style de code](media/code-style-quick-actions-dialog.png)

Pour chaque élément, vous pouvez définir les options **Préférence** et **Gravité** en utilisant les listes déroulantes sur chaque ligne.  L’option Gravité peut avoir la valeur **None** (Aucune), **Suggestion**, **Avertissement** ou **Erreur**, et le comportement de Visual Studio s’adapte en conséquence.  Si vous souhaitez utiliser les [actions rapides](quick-actions.md) avec ces styles de code pour réécrire automatiquement le code avec le style par défaut, vérifiez que la valeur du paramètre n’est pas **None** (Aucune) pour que l’icône d’ampoule ![Petite icône en forme d’ampoule](media/vs2015_lightbulbsmall.png "VS2017_LightBulbSmall") s’affiche quand les styles autres que par défaut sont utilisés.  Ces préférences peuvent ensuite être appliquées en cliquant sur l’icône d’ampoule ou en appuyant sur **Ctrl+.** quand votre curseur se trouve sur la ligne de code appropriée.

Les paramètres de style de code pour .NET peuvent également être gérés avec un fichier [EditorConfig](editorconfig-code-style-settings-reference.md).  Dans ce cas, les paramètres sélectionnés dans la fenêtre Options sont les paramètres de secours, le fichier EditorConfig étant prioritaire.  Vous pouvez utiliser ce fichier pour appliquer et configurer le style de codage pour l’intégralité de votre référentiel ou équipe.

# <a name="see-also"></a>Voir aussi
* [Actions rapides](quick-actions.md)
