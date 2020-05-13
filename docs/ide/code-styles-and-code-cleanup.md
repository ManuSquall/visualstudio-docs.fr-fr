---
title: Options de style de code et de nettoyage du code
ms.date: 04/25/2019
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jillfra
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Code_Style.General
- VS.ToolsOptionsPages.Text_Editor.Basic.Code_Style.General
ms.workload:
- multiple
ms.openlocfilehash: 9d540339ca25fc42fc05df4818a6d05204ccae0e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79301859"
---
# <a name="code-style-preferences"></a>Préférences de style de code

Vous pouvez définir des paramètres de style de code par projet en utilisant un [fichier EditorConfig](#code-styles-in-editorconfig-files), ou pour tout le code que vous éditez dans Visual Studio dans la page [**Options** de l’éditeur de texte](#code-styles-in-the-options-dialog-box). Pour le code C#, vous pouvez aussi configurer Visual Studio pour appliquer ces préférences de style de code avec les commandes **Nettoyage du code** (Visual Studio 2019) et **Mettre en forme le document** (Visual Studio 2017).

> [!NOTE]
> Cette rubrique s’applique à Visual Studio sur Windows. Pour Visual Studio pour Mac, consultez [Comportement de l’éditeur dans Visual Studio pour Mac](/visualstudio/mac/editor-behavior).

## <a name="code-styles-in-editorconfig-files"></a>Styles de code dans les fichiers EditorConfig

Vous pouvez aussi spécifier des [paramètres de style de code](../ide/editorconfig-code-style-settings-reference.md) pour .NET en ajoutant un fichier [EditorConfig](create-portable-custom-editor-options.md) à votre projet. Les fichiers EditorConfig sont associés à un code base plutôt qu’à un compte de personnalisation Visual Studio. Les paramètres d’un fichier EditorConfig sont prioritaires sur les styles de code spécifiés dans la boîte de dialogue **Options**. Utilisez un fichier EditorConfig lorsque vous souhaitez appliquer des styles de codage pour tous les contributeurs à votre référentiel ou projet.

::: moniker range=">=vs-2019"

Vous pouvez remplir manuellement votre fichier EditorConfig, ou vous pouvez générer automatiquement le fichier en fonction des paramètres de style de code que vous avez définis dans la boîte de dialogue **Options** de Visual Studio. Cette page d’options est disponible à **Tools** > **Options** > **Text Editor** > [ C **'** ou **Basic**] > **Code Style** > **General**. Cliquez sur **Générer le fichier .editorconfig à partir des paramètres** pour générer automatiquement un fichier *.editorconfig* de style de codage basé sur les paramètres de cette page **Options**.

![Générer un fichier .editorconfig à partir des paramètres dans Visual Studio 2019](media/vs-2019/generate-editorconfig-file-small.png)

::: moniker-end

## <a name="code-styles-in-the-options-dialog-box"></a>Styles de code dans la boîte de dialogue Options

Vous pouvez définir les préférences de style de code pour tous vos projets C# et Visual Basic dans la boîte de dialogue **Options** accessible à partir du menu **Outils**. Dans la boîte de dialogue **Options**, sélectionnez **Éditeur de texte** > [**C#** ou **De base**] > **Style de code** > **Général**.

Chaque élément de la liste affiche un aperçu de la préférence sélectionnée :

::: moniker range="vs-2017"

![Options de style de code](media/code-style-quick-actions-dialog.png)

::: moniker-end

::: moniker range=">=vs-2019"

![Options de style de code](media/vs-2019/code-style-quick-actions-dialog.png)

::: moniker-end

Les options définies dans cette fenêtre sont applicables à votre compte de personnalisation Visual Studio et ne sont pas associées à un projet ou code base particulier. Elles ne sont non plus appliquées au moment de la génération, y compris dans les builds d’intégration continue (CI). Si vous voulez associer des préférences de style de code à votre projet et que les styles soient appliqués lors de la génération, spécifiez les préférences dans un [fichier .editorconfig](#code-styles-in-editorconfig-files) associé au projet.

### <a name="preference-and-severity"></a>Préférence et gravité

Pour chaque paramètre de style de code de cette page, vous pouvez définir les valeurs **Préférence** et **Gravité** en utilisant les listes déroulantes sur chaque ligne. L’option Gravité peut avoir la valeur **Refactorisation uniquement**, **Suggestion**, **Avertissement** ou **Erreur**. Si vous souhaitez activer les [actions rapides](../ide/quick-actions.md) pour un style de code, vérifiez que la valeur de l’option **Gravité** n’est pas **Refactorisation uniquement**. ](media/light-bulb-dropdown.png)L’ampoule Quick ![ **Actions,** l’ampoule à](media/error-bulb.png)erreur ![erreur ![ampoule d’erreur, ou tournevis icône tournevis](media/screwdriver.png) apparaît quand un modèle non-préféré est utilisé, et vous pouvez choisir une option sur la liste Actions **rapides** pour réécrire automatiquement le code au style préféré.

## <a name="apply-code-styles"></a>Appliquer des styles de code

::: moniker range="vs-2017"

Vous pouvez configurer la commande **Mettre en forme le document** (**Modifier** > **Avancé** > **Mettre en forme le document**) pour appliquer vos paramètres de style de code (à partir d’un fichier EditorConfig ou des options **Style de code**), ainsi que la mise en forme régulière qu’il effectue (par exemple l’indentation). S’il existe un fichier *.editorconfig* pour le projet, ces paramètres sont prioritaires.

> [!NOTE]
> L’application de styles de code avec la commande **Mettre en forme le document** est disponible seulement pour les fichiers de code C#. Il s’agit d’une fonctionnalité expérimentale.

Configurez les paramètres que la commande **Mettre en forme le document** doit appliquer dans la page [Options de mise en forme](reference/options-text-editor-csharp-formatting.md#format-document-settings).

![Paramètres de style de code pour mettre en forme le document dans Visual Studio 2017](media/format-document-settings-experiment.png)

> [!TIP]
> Les règles configurées avec une sévérité de **Aucun** ne participent pas au nettoyage du code, mais peuvent être appliquées individuellement via le menu **Actions rapides et Refactorings.**

La première fois que vous déclenchez la commande **Mettre en forme le document**, une barre d’informations jaune vous invite à configurer vos paramètres de nettoyage du code.

::: moniker-end

::: moniker range=">=vs-2019"

Pour les fichiers de code C, Visual Studio 2019 dispose **d’un** bouton Code Cleanup en bas de **l’éditeur** (clavier : **Ctrl**+**K**, **Ctrl**+**E**) pour appliquer les styles de code à partir d’un fichier EditorConfig ou de la page d’options Code Style. S’il existe un fichier *.editorconfig* pour le projet, ces paramètres sont prioritaires.

![Exécuter le nettoyage du code dans Visual Studio 2019](media/execute-code-cleanup.png)

> [!TIP]
> Les règles configurées avec une sévérité de **Aucun** ne participent pas au nettoyage du code, mais peuvent être appliquées individuellement via le menu **Actions rapides et Refactorings.**

Configurez d’abord les styles de code que vous voulez appliquer (dans un des deux profils) dans la boîte de dialogue **Configurer le nettoyage du code**. Pour ouvrir cette boîte de dialogue, cliquez sur la flèche en regard de l’icône de balai de nettoyage du code, puis choisissez **Configurer le nettoyage du code**.

![Configurer le nettoyage du code dans Visual Studio 2019](media/configure-code-cleanup.png)

Une fois que vous avez configuré le nettoyage du code, vous pouvez soit cliquer sur l’icône du balai ou appuyer sur **Ctrl**+**K**, **Ctrl**+**E** pour exécuter le nettoyage du code. Vous pouvez également exécuter le nettoyage du code sur l’ensemble de votre projet ou solution. Cliquez avec le bouton droit sur le nom du projet ou de la solution dans **l’Explorateur de solutions**, sélectionnez **Analyser et nettoyer le code**, puis sélectionnez **Exécuter le nettoyage du code**.

![Exécuter le nettoyage du code sur l’ensemble du projet ou de la solution](media/run-code-cleanup-project-solution.png)

Si vous voulez que vos paramètres de style de code soient appliqués chaque fois que vous enregistrez un fichier, vous pouvez utiliser l’extension [Code Cleanup on Save](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.CodeCleanupOnSave).

::: moniker-end

## <a name="see-also"></a>Voir aussi

- [Actions rapides](../ide/quick-actions.md)
- [Paramètres de convention de codage .NET pour EditorConfig](../ide/editorconfig-code-style-settings-reference.md)
- [Comportement de l’éditeur (Visual Studio pour Mac)](/visualstudio/mac/editor-behavior)
