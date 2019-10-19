---
title: Options, Éditeur de texte, C#, IntelliSense | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Intellisense
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Intellisense
helpviewer_keywords:
- IntelliSense [J#], options
- underlines, wavy
- IntelliSense [C#], options
- IntelliSense [C#], wavy underlines
- wavy underlines
- Text Editor Options dialog box, IntelliSense
ms.assetid: 3466dedb-e5f4-424c-8dd8-e4941b2f4fc2
caps.latest.revision: 30
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1e3f4df9a7a885245e40f7e9fec1b0da207ada39
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662298"
---
# <a name="options-text-editor-c-intellisense"></a>Options, Éditeur de texte, C#, IntelliSense
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Utilisez la page de propriétés **IntelliSense** pour modifier les paramètres qui affectent le comportement d’IntelliSense pour Visual C#. Pour accéder à la page de propriétés **IntelliSense**, cliquez sur **Options** dans le menu **Outils**, cliquez sur **C#** dans le dossier **Éditeur de texte**, puis cliquez sur **IntelliSense**.

> [!NOTE]
> Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

 La page de propriétés **IntelliSense** contient les propriétés suivantes :

## <a name="completion-lists"></a>Listes de saisie semi-automatique
 **Afficher la liste de saisie semi-automatique après la saisie d’un caractère** Lorsque cette option est sélectionnée, IntelliSense affiche automatiquement la liste de saisie semi-automatique lorsque vous commencez à taper. Quand cette option n’est pas sélectionnée, vous pouvez utiliser la saisie semi-automatique IntelliSense à partir du menu **IntelliSense** ou en appuyant sur Ctrl+espace.

 **Placer les mots clés dans les listes de saisie semi-automatique** Lorsque cette option est sélectionnée, IntelliSense ajoute C# des mots clés, par exemple [classe](https://msdn.microsoft.com/library/b95d8815-de18-4c3f-a8cc-a0a53bdf8690), à la liste de saisie semi-automatique.

 **Placer des extraits de code dans les listes de saisie semi-automatique** Lorsque cette option est sélectionnée, IntelliSense ajoute des alias pour C# les extraits de code à la liste de saisie semi-automatique. Si l’alias d’extrait de code est identique à un mot clé, par exemple, [class](https://msdn.microsoft.com/library/b95d8815-de18-4c3f-a8cc-a0a53bdf8690), le mot clé est remplacé par le raccourci. Pour plus d’informations, consultez [Extraits de code Visual C#](../../ide/visual-csharp-code-snippets.md).

## <a name="selection-in-completion-lists"></a>Sélection dans la liste de saisie semi-automatique
 **Validé en tapant les caractères suivants :** Spécifie tous les caractères qui exécutent la saisie semi-automatique IntelliSense pour l’élément sélectionné dans la liste de saisie semi-automatique, une fois qu’ils sont tapés.

 **Validé en appuyant sur la barre d’espace** Spécifie d’inclure l’action d’appuyer sur la barre d’espace pour exécuter la saisie semi-automatique IntelliSense pour l’élément sélectionné dans la liste de saisie semi-automatique.

 **Ajouter une nouvelle ligne à la fin du mot entièrement typé** Spécifie que si vous tapez tous les caractères d’une entrée dans la liste de saisie semi-automatique et que vous appuyez sur entrée, une nouvelle ligne est automatiquement créée et le curseur se déplace vers la nouvelle ligne.

 Par exemple, si vous tapez `else` et appuyez sur Entrée, voici ce qui apparaît dans l’éditeur :

 `else`

 `|` (emplacement du curseur)

 Toutefois, si vous tapez uniquement `el` et appuyez sur Entrée, voici ce qui apparaît dans l’éditeur :

 `else|` (emplacement du curseur)

## <a name="intellisense-member-selection"></a>Sélection de membres IntelliSense
 **Présélectionne le dernier membre utilisé** Lorsque cette option est sélectionnée, IntelliSense présélectionne les membres que vous avez récemment sélectionnés dans la zone liste contextuelle des membres pour la saisie semi-automatique des noms d’objet, pendant votre session active dans l’environnement de développement intégré (IDE). L'historique des membres utilisés récemment est effacé entre chaque session dans l'IDE. Pour plus d’informations, consultez [IntelliSense pour les membres les plus récemment utilisés](../../misc/intellisense-for-most-recently-used-members.md).

## <a name="see-also"></a>Voir aussi
 [Général, environnement, boîte de dialogue Options commentaires de](../../ide/reference/general-environment-options-dialog-box.md) [documentation XML](https://msdn.microsoft.com/library/803b7f7b-7428-4725-b5db-9a6cff273199) [à l’aide d’IntelliSense](../../ide/using-intellisense.md)
