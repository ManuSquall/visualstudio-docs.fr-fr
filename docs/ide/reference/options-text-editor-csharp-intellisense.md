---
title: Options, Éditeur de texte, C#, IntelliSense
description: Découvrez comment utiliser la page IntelliSense de la section C# pour modifier les paramètres qui affectent le comportement d’IntelliSense pour C#.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 8e727fad6d3cb15f70cf630b1077170d16d28b7f
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96039742"
---
# <a name="options-text-editor-c-intellisense"></a>Options, Éditeur de texte, C#, IntelliSense

Utilisez la page d’options **IntelliSense** pour modifier les paramètres qui affectent le comportement d’IntelliSense pour C#. Pour accéder à cette page d’options, choisissez **Outils**  >  **options**, puis **éditeur de texte**  >  **C#**  >  **IntelliSense**.

La page d’options **IntelliSense** contient les options suivantes :

## <a name="completion-lists"></a>Listes de saisie semi-automatique

- Afficher la liste de saisie semi-automatique après la saisie d’un caractère*

   Quand cette option est sélectionnée et que vous commencez à taper, IntelliSense affiche automatiquement la liste de saisie semi-automatique. Lorsque cette option n’est pas sélectionnée, la saisie semi-automatique IntelliSense est toujours disponible dans le menu **IntelliSense** ou en appuyant sur **CTRL** + **Space**.

- Afficher la liste de saisie semi-automatique après la suppression d’un caractère

- Mettre en surbrillance les parties correspondantes des éléments de liste de saisie semi-automatique

- Afficher les filtres d’éléments de complétion

## <a name="snippets-behavior"></a>Comportement des extraits de code

- Ne jamais inclure d’extrait de code

   Quand cette option est sélectionnée, IntelliSense n’ajoute jamais d’alias pour les extraits de code C# à la liste de saisie semi-automatique.

- Toujours inclure les extraits de code

   Quand cette option est sélectionnée, IntelliSense ajoute des alias pour les extraits de code C# à la liste de saisie semi-automatique. Si l’alias d’extrait de code est identique à un mot clé, par exemple, [class](/dotnet/csharp/language-reference/keywords/class), le mot clé est remplacé par le raccourci. Pour plus d’informations, consultez [Extraits de code C#](../../ide/visual-csharp-code-snippets.md).

- Inclure les extraits de code quand ?-Tab est typé après un identificateur

   Lorsque cette option est sélectionnée, IntelliSense ajoute des alias pour les extraits de code C# à la liste de saisie semi-automatique quand **?** + L' **onglet** est appuyé après un identificateur

## <a name="enter-key-behavior"></a>Comportement de la touche Entrée

- Ne jamais ajouter de nouvelle ligne après Entrée

   Spécifie qu’une nouvelle ligne n’est jamais ajoutée automatiquement après la sélection d’un élément dans la liste de saisie semi-automatique et après l’appui sur **Entrée**.

- Ajouter uniquement une nouvelle ligne après Entrée à la fin d’un mot complet tapé

   Spécifie que si vous tapez tous les caractères d’une entrée dans la liste de saisie semi-automatique et que vous appuyez ensuite sur **Entrée**, une ligne est automatiquement créée et le curseur se déplace vers la nouvelle ligne.

   Par exemple, si vous tapez `else` et appuyez sur **entrée**, les éléments suivants s’affichent dans l’éditeur :

   `else`

   `|` (emplacement du curseur)

   Toutefois, si vous tapez uniquement `el` et que vous appuyez sur **entrée**, les éléments suivants s’affichent dans l’éditeur :

   `else|` (emplacement du curseur)

- Toujours ajouter une nouvelle ligne après Entrée

   Spécifie que si vous tapez *n’importe lequel* des caractères d’une entrée dans la liste de saisie semi-automatique et que vous appuyez ensuite sur **Entrée**, une ligne est automatiquement créée et le curseur passe à la nouvelle ligne.

## <a name="show-name-suggestions"></a>Afficher les suggestions de nom

Effectue la complétion automatique du nom d’objet pour les membres que vous avez sélectionnés récemment.

## <a name="see-also"></a>Voir aussi

- [Général, environnement, boîte de dialogue Options](../../ide/reference/general-environment-options-dialog-box.md)
- [Utilisation d’IntelliSense](../../ide/using-intellisense.md)
