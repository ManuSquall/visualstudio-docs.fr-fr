---
title: Options, Éditeur de texte, C#, Mise en forme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.Spacing
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.NewLines
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Formatting.General
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.Indentation
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Formatting.NewLines
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Formatting.Indentation
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Formatting.Wrapping
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.Wrapping
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.General
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Formatting.Spacing
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Formatting
helpviewer_keywords:
- formatting [C#]
- formatting [J#]
- Text Editor Options dialog box, formatting
ms.assetid: 5a7bb668-1d0c-4ffe-9508-24592813162e
caps.latest.revision: 29
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5371b7180aed462910a57daeb9bf5d43f2ecfedb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662283"
---
# <a name="options-text-editor-c-formatting"></a>Options, Éditeur de texte, C#, Mise en forme
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Utilisez la boîte de dialogue de page de propriétés **Mise en forme** pour définir des options de mise en forme du code dans l’éditeur de code. Pour accéder à cette boîte de dialogue, cliquez sur **Options** dans le menu **Outils**, développez **Éditeur de texte**, développez **C#**, puis cliquez sur **Mise en forme**.

> [!NOTE]
> Les boîtes de dialogue et les commandes de menu affichées peuvent différer de celles décrites dans l'Aide selon les paramètres actifs ou le mode d'édition. Pour modifier vos paramètres, choisissez **Paramètres d'importation et d'exportation** dans le menu **Outils** . Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="general-settings"></a>Paramètres généraux
 Les paramètres généraux affectent la façon dont l’éditeur de code applique les options de mise en forme au code.

## <a name="uielement-list"></a>Liste des éléments de l'interface utilisateur

|Étiquette|Description|
|-----------|-----------------|
|**Mise en forme automatique de l’instruction sur ;**|Quand elle est sélectionnée, cette option met en forme les instructions conformément aux options sélectionnées pour l’éditeur de code, dès la fin de l’instruction. Décochez cette case si vous ne voulez pas que l’éditeur de code modifie les instructions.|
|**Mise en forme automatique du bloc terminé sur }**|Quand elle est sélectionnée, cette option met en forme les blocs de code conformément aux options sélectionnées pour l’éditeur de code, dès la fin du bloc de code. Décochez cette case si vous ne voulez pas que l’éditeur de code modifie les blocs de code.|
|**Ajuster la mise en retrait lors du collage**|Quand elle est sélectionnée, cette option met en forme le texte collé dans l’éditeur de code conformément aux options sélectionnées pour l’éditeur de code. Décochez cette case si vous ne voulez pas que le texte collé soit modifié.|

## <a name="preview-window"></a>Fenêtre Aperçu
 Les volets d’options **Mise en retrait**, **Nouvelles lignes**, **Espacement** et **Retour à la ligne** offrent tous une fenêtre d’aperçu. La fenêtre d’aperçu montre l’effet de chaque option. Pour utiliser la fenêtre d’aperçu, sélectionnez une option de mise en forme. La fenêtre d’aperçu montre un exemple de l’option sélectionnée. Quand vous changez le paramètre, par exemple quand vous cochez ou décochez une case à cocher, la fenêtre d’aperçu se met à jour en affichant l’effet du nouveau paramètre.

## <a name="remarks"></a>Notes
 Les options de mise en retrait dans les pages **Tabulations** de chaque langage déterminent uniquement l’endroit où l’éditeur de code place le curseur quand vous appuyez sur Entrée en fin de ligne. Les options de mise en retrait sous **Mise en forme** s’appliquent quand le code est mis en forme automatiquement, par exemple, quand vous collez du code dans le fichier alors que l’option **Ajuster la mise en retrait lors du collage** est sélectionnée, et quand le bloc qui est mis en forme est tapé manuellement.

## <a name="see-also"></a>Voir aussi
 [Général, environnement, boîte de dialogue Options](../../ide/reference/general-environment-options-dialog-box.md)
