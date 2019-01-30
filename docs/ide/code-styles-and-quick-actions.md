---
title: Préférences de style de code
ms.date: 03/10/2017
ms.prod: visual-studio-dev15
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Code_Style.General
- VS.ToolsOptionsPages.Text_Editor.Basic.Code_Style.General
ms.workload:
- multiple
ms.openlocfilehash: 065a4c21be596b409ed82718e0b38c38367612cc
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55039053"
---
# <a name="code-style-preferences"></a>Préférences de style de code

Vous pouvez définir les préférences de style de code pour vos projets C# et Visual Basic dans la boîte de dialogue **Options** accessible à partir du menu **Outils**. Dans la boîte de dialogue **Options**, sélectionnez **Éditeur de texte** > [**C#** ou **De base**] > **Style de code** > **Général**. Les options définies dans cette fenêtre s’appliquent uniquement à la machine locale.

Chaque élément de la liste affiche un aperçu de la préférence sélectionnée :

![Options de style de code](media/code-style-quick-actions-dialog.png)

> [!NOTE]
> Cette rubrique s’applique à Visual Studio sur Windows. Pour Visual Studio pour Mac, consultez [Comportement de l’éditeur dans Visual Studio pour Mac](/visualstudio/mac/editor-behavior).

## <a name="preference-and-severity"></a>Préférence et gravité

Pour chaque élément, vous pouvez définir les valeurs **Préférence** et **Gravité** en utilisant les listes déroulantes sur chaque ligne. L’option Gravité peut avoir la valeur **Aucune**, **Suggestion**, **Avertissement** ou **Erreur**. Si vous souhaitez activer les [actions rapides](../ide/quick-actions.md) pour un style de code, assurez-vous que la valeur de l’option **Gravité** n’est pas **Aucune**. L’icône en forme d’ampoule **Actions rapides** ![Petite icône en forme d’ampoule](media/vs2015_lightbulbsmall.png) s’affiche quand un style qui n’est pas un style par défaut est utilisé. Vous pouvez choisir une option dans la liste **Actions rapides** pour réécrire automatiquement le code avec le style par défaut.

## <a name="editorconfig-files"></a>Fichiers EditorConfig

Les paramètres de style de code pour .NET peuvent également être gérés avec un fichier [EditorConfig](../ide/editorconfig-code-style-settings-reference.md). Les paramètres du fichier EditorConfig sont prioritaires sur les options sélectionnées dans la boîte de dialogue **Options**. Vous pouvez utiliser le fichier EditorConfig pour appliquer et configurer le style de codage pour l’intégralité de votre référentiel ou projet.

## <a name="format-document-command"></a>Commande Mettre le document en forme

Dans Visual Studio 2017 version 15.8 et les versions ultérieures, vous pouvez configurer la commande **Mettre le document en forme** (**Edition** > **Avancé** > **Mettre le document en forme**) pour effectuer un nettoyage de code supplémentaire sur un fichier, par exemple supprimer et trier les using ou appliquer des préférences de style de code. Vous pouvez définir les paramètres que la commande **Mettre le document en forme** doit appliquer dans la page [Options de mise en forme](reference/options-text-editor-csharp-formatting.md#format-document-settings).

Le nettoyage du code respecte les paramètres configurés dans un fichier *.editorconfig* ou, en l’absence de la règle ou du fichier approprié, ceux définis dans **Outils** > **Options** > **Éditeur de texte** > **C#** > [**Style de code** ou **Mise en forme**].

La première fois que vous déclenchez la commande **Mettre le document en forme** dans Visual Studio 2017, une barre d’informations jaune vous invite à configurer vos paramètres de nettoyage du code.

> [!TIP]
> Les règles configurées avec la valeur **none** dans un fichier *.editorconfig* ne participent pas au nettoyage du code. Toutefois, elles peuvent être appliquées individuellement via le menu **Actions rapides et refactorisations**.

## <a name="see-also"></a>Voir aussi

- [Actions rapides](../ide/quick-actions.md)
- [Paramètres des conventions de codage .NET pour EditorConfig](../ide/editorconfig-code-style-settings-reference.md)
- [Comportement de l’éditeur (Visual Studio pour Mac)](/visualstudio/mac/editor-behavior)