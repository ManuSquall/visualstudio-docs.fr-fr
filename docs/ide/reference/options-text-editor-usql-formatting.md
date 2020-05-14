---
title: Options de mise en forme de l’éditeur U-SQL
ms.date: 01/17/2019
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.U-SQL.Formatting.Spacing
- VS.ToolsOptionsPages.Text_Editor.U-SQL.Formatting.NewLines
- VS.ToolsOptionsPages.Text_Editor.U-SQL.Formatting.Indentation
- VS.ToolsOptionsPages.Text_Editor.U-SQL.Formatting
- VS.ToolsOptionsPages.Text_Editor.U-SQL.Formatting.General
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 200ec41a1295178f1127d10053985384a7813158
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75568267"
---
# <a name="options-text-editor-u-sql-formatting"></a>Options, Éditeur de texte, U-SQL, Mise en forme

Utilisez la page d’options **de formatage** pour définir des options de formatage du code dans l’éditeur de code. Pour accéder à cette page d’options, choisissez **Tools** > **Options**. Dans la boîte de dialogue **Options**, choisissez **Éditeur de texte** > **U-SQL** > **Mise en forme**.

## <a name="general-page"></a>Page Général

### <a name="general-settings"></a>Paramètres généraux :

Ces paramètres affectent le *moment* où l’éditeur de code applique les options de mise en forme au code.

- **Mettre en forme automatiquement l’instruction terminée lors de l’entrée du point-virgule**

   Quand elle est sélectionnée, cette option met en forme les instructions conformément aux options sélectionnées pour l’éditeur quand vous appuyez sur la touche point-virgule.

- **Mise en forme automatique lors du collage**

   Quand elle est sélectionnée, cette option met en forme le texte collé dans l’éditeur conformément aux options sélectionnées pour l’éditeur.

## <a name="preview-windows"></a>Fenêtres d’aperçu

Les sous-pages **Retrait**, **Nouvelles lignes** et **Espacement** proposent toutes une fenêtre d’aperçu au bas de l’affichage. La fenêtre d’aperçu montre l’effet de chaque option. Pour utiliser la fenêtre d’aperçu, sélectionnez une option de mise en forme. La fenêtre d’aperçu montre un exemple de l’option sélectionnée. Quand vous changez un paramètre en cochant une case, la fenêtre d’aperçu se met à jour pour afficher l’effet du nouveau paramètre.

### <a name="indentation-remarks"></a>Notes relatives au retrait

Les options d’indentation sur les pages **Onglets** pour chaque langue ne déterminent que l’endroit où l’éditeur de code place le curseur lorsque vous appuyez **sur Enter** à la fin d’une ligne. Les options de mise en retrait sous **Mise en forme** s’appliquent quand le code est mis en forme automatiquement, par exemple :

- Quand vous collez du code dans le fichier alors que l’option **Mettre en forme automatiquement lors du collage** est sélectionnée.
- Quand le bloc en cours de mise en forme est tapé manuellement.

## <a name="see-also"></a>Voir aussi

- [Général, Environnement, boîte de dialogue Options](../../ide/reference/general-environment-options-dialog-box.md)
