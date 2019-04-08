---
title: Préférences de style de code
ms.date: 03/12/2019
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Code_Style.General
- VS.ToolsOptionsPages.Text_Editor.Basic.Code_Style.General
ms.workload:
- multiple
ms.openlocfilehash: 689bdb62d5a4bc9aea21da67e8e5e844660756d6
ms.sourcegitcommit: b14b7a938a2aba9fcce4d5e813aadf2040b0dcda
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2019
ms.locfileid: "58647308"
---
# <a name="code-style-preferences"></a>Préférences de style de code

Vous pouvez définir les préférences de style de code pour vos projets C# et Visual Basic dans la boîte de dialogue **Options** accessible à partir du menu **Outils**. Dans la boîte de dialogue **Options**, sélectionnez **Éditeur de texte** > [**C#** ou **De base**] > **Style de code** > **Général**.

Chaque élément de la liste affiche un aperçu de la préférence sélectionnée :

::: moniker range="vs-2017"

![Options de style de code](media/code-style-quick-actions-dialog.png)

::: moniker-end

::: moniker range=">=vs-2019"

![Options de style de code](media/vs-2019/code-style-quick-actions-dialog.png)

::: moniker-end

Les options définies dans cette fenêtre sont applicables à votre compte de personnalisation Visual Studio et ne sont pas associées à un projet ou code base particulier. Elles ne sont non plus appliquées au moment de la génération, y compris dans les builds d’intégration continue (CI). Si vous souhaitez associer des préférences de style de code à votre projet et que les styles sont appliqués lors de la génération, spécifiez les préférences dans un [fichier .editorconfig](#editorconfig-files).

> [!NOTE]
> Cette rubrique s’applique à Visual Studio sur Windows. Pour Visual Studio pour Mac, consultez [Comportement de l’éditeur dans Visual Studio pour Mac](/visualstudio/mac/editor-behavior).

## <a name="editorconfig-files"></a>Fichiers EditorConfig

Les paramètres de style de code pour .NET peuvent également être spécifiés en ajoutant un fichier [EditorConfig](../ide/editorconfig-code-style-settings-reference.md) à votre projet.

::: moniker range=">=vs-2019"

Cliquez sur **Générer le fichier .editorconfig à partir des paramètres** pour générer automatiquement un fichier .editorconfig de style de codage basé sur les options que vous avez définies dans cette page **Options**.

![Générer un fichier editorconfig à partir des paramètres dans VS 2019](media/vs-2019/generate-editorconfig-file-small.png)

::: moniker-end

Les fichiers EditorConfig sont associés à un code base plutôt qu’à un compte de personnalisation Visual Studio. Les paramètres d’un fichier EditorConfig sont prioritaires sur les options sélectionnées dans la boîte de dialogue **Options**. Utilisez un fichier EditorConfig lorsque vous souhaitez appliquer des styles de codage pour tous les contributeurs à votre référentiel ou projet.

## <a name="preference-and-severity"></a>Préférence et gravité

Pour chaque paramètre de style de code de cette page, vous pouvez définir les valeurs **Préférence** et **Gravité** en utilisant les listes déroulantes sur chaque ligne. L’option Gravité peut avoir la valeur **Aucune**, **Suggestion**, **Avertissement** ou **Erreur**. Si vous souhaitez activer les [actions rapides](../ide/quick-actions.md) pour un style de code, assurez-vous que la valeur de l’option **Gravité** n’est pas **Aucune**. L’icône d’ampoule **Actions rapides** ![ampoule](media/light-bulb-dropdown.png), d’ampoule d’erreur ![ampoule d’erreur](media/error-bulb.png)ou de tournevis ![tournevis](media/screwdriver.png) apparaît quand un style qui n’est pas un style par défaut est utilisé. Vous pouvez choisir une option dans la liste **Actions rapides** pour réécrire automatiquement le code avec le style par défaut.

## <a name="format-document-command"></a>Commande Mettre le document en forme

Vous pouvez configurer la commande **Mettre le document en forme** (**Edition** > **Avancé** > **Mettre le document en forme**) pour effectuer un nettoyage de code supplémentaire sur un fichier, par exemple supprimer et trier les using ou appliquer des préférences de style de code. Vous pouvez définir les paramètres que la commande **Mettre le document en forme** doit appliquer dans la page [Options de mise en forme](reference/options-text-editor-csharp-formatting.md#format-document-settings).

Le nettoyage du code respecte les paramètres configurés dans un fichier *.editorconfig* ou, en l’absence de la règle ou du fichier approprié, ceux définis dans **Outils** > **Options** > **Éditeur de texte** > **C#** > [**Style de code** ou **Mise en forme**].

La première fois que vous déclenchez la commande **Mettre le document en forme** dans Visual Studio, une barre d’informations jaune vous invite à configurer vos paramètres de nettoyage du code.

> [!TIP]
> Les règles configurées avec la gravité **Aucune** ne participent pas au nettoyage du code. Toutefois, elles peuvent être appliquées individuellement via le menu **Actions rapides et refactorisations**.

## <a name="see-also"></a>Voir aussi

- [Actions rapides](../ide/quick-actions.md)
- [Paramètres des conventions de codage .NET pour EditorConfig](../ide/editorconfig-code-style-settings-reference.md)
- [Comportement de l’éditeur (Visual Studio pour Mac)](/visualstudio/mac/editor-behavior)