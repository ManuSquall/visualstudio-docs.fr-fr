---
title: Options, Éditeur de texte, C#, IntelliSense
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Intellisense
helpviewer_keywords:
- underlines, wavy
- IntelliSense [C#], options
- IntelliSense [C#], wavy underlines
- wavy underlines
- Text Editor Options dialog box, IntelliSense
ms.assetid: 3466dedb-e5f4-424c-8dd8-e4941b2f4fc2
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: d8f6928dd09b971e2c5924d34058a1a0d5e28394
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31947389"
---
# <a name="options-text-editor-c-intellisense"></a>Options, Éditeur de texte, C#, IntelliSense

Utilisez la page d’options **IntelliSense** pour modifier les paramètres qui affectent le comportement d’IntelliSense pour C#. Pour accéder à cette page d’options, choisissez **Outils** > **Options**, puis **Éditeur de texte** > **C#** > **IntelliSense**.

> [!NOTE]
> Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).

La page d’options **IntelliSense** contient les options suivantes :

## <a name="completion-lists"></a>Listes de saisie semi-automatique

- Afficher la liste de saisie semi-automatique après la saisie d’un caractère*

   Quand cette option est sélectionnée et que vous commencez à taper, IntelliSense affiche automatiquement la liste de saisie semi-automatique. Quand cette option n’est pas sélectionnée, vous pouvez utiliser la saisie semi-automatique IntelliSense à partir du menu **IntelliSense** ou en appuyant sur **Ctrl**+**Espace**.

- Afficher la liste de saisie semi-automatique après la suppression d’un caractère

- Mettre en surbrillance les parties correspondantes des éléments de liste de saisie semi-automatique

- Afficher les filtres d’éléments de saisie semi-automatique

- Afficher les suggestions de nom

### <a name="snippets-behavior"></a>Comportement des extraits de code

- Ne jamais inclure d’extrait de code

   Quand cette option est sélectionnée, IntelliSense n’ajoute jamais d’alias pour les extraits de code C# à la liste de saisie semi-automatique.

- Toujours inclure les extraits de code

   Quand cette option est sélectionnée, IntelliSense ajoute des alias pour les extraits de code C# à la liste de saisie semi-automatique. Si l’alias d’extrait de code est identique à un mot clé, par exemple, [class](/dotnet/csharp/language-reference/keywords/class), le mot clé est remplacé par le raccourci. Pour plus d’informations, consultez [Extraits de code C#](../../ide/visual-csharp-code-snippets.md).

- Inclure les extraits de code quand ?-Tab est typé après un identificateur

   Quand cette option est sélectionnée, IntelliSense ajoute des alias pour les extraits de code C# à la liste de saisie semi-automatique à la suite d’un appui sur **?**+**Tab** après un identificateur.

### <a name="enter-key-behavior"></a>Comportement de la touche Entrée

- Ne jamais ajouter de nouvelle ligne après Entrée

   Spécifie qu’une nouvelle ligne n’est jamais ajoutée automatiquement après la sélection d’un élément dans la liste de saisie semi-automatique et après l’appui sur **Entrée**.

- Ajouter uniquement une nouvelle ligne après Entrée à la fin d’un mot complet tapé

   Spécifie que si vous tapez tous les caractères d’une entrée dans la liste de saisie semi-automatique et que vous appuyez ensuite sur **Entrée**, une ligne est automatiquement créée et le curseur se déplace vers la nouvelle ligne.

   Par exemple, si vous tapez `else` et que vous appuyez ensuite sur **Entrée**, voici ce qui apparaît dans l’éditeur :

   `else`

   `|` (emplacement du curseur)

   Toutefois, si vous tapez uniquement `el` et que vous appuyez ensuite sur **Entrée**, voici ce qui apparaît dans l’éditeur :

   `else|` (emplacement du curseur)

- Toujours ajouter une nouvelle ligne après Entrée

   Spécifie que si vous tapez *n’importe lequel* des caractères d’une entrée dans la liste de saisie semi-automatique et que vous appuyez ensuite sur **Entrée**, une ligne est automatiquement créée et le curseur passe à la nouvelle ligne.

## <a name="see-also"></a>Voir aussi

- [Général, Environnement, boîte de dialogue Options](../../ide/reference/general-environment-options-dialog-box.md)
- [Utilisation de la fonctionnalité IntelliSense](../../ide/using-intellisense.md)