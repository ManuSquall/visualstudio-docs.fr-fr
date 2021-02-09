---
title: Options, Éditeur de texte, Tous les langages, Barres de défilement
description: Découvrez comment utiliser la page barres de défilement dans la section tous les langages pour modifier le comportement par défaut des barres de défilement de l’éditeur de code dans Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 10/25/2018
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.All_Languages.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.Basic.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.CSharp.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.C%2FC%2B%2B.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.CoffeeScript.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.CSS.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.Dockerfile.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.F%2523.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.HQL.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.HTML.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.HTMLX.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.JavaScript.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.TypeScript.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.JSON.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.LESS.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.Plain_Text.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.ResJSON.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.SCSS.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.SQL_Server_Tools.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.StreamAnalytics.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.T-SQL90.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.U-SQL.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.XAML.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.XML.ScrollBars
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c9f9b53807d0ae2160798f29b98fa315c43c330c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99841967"
---
# <a name="options-text-editor-all-languages-scroll-bars"></a>Options, Éditeur de texte, Tous les langages, Barres de défilement
Cette boîte de dialogue vous permet de modifier le comportement par défaut de la barre de défilement de l’éditeur de code. Pour afficher ces options, sélectionnez **Options** dans le menu **Outils**. Dans le dossier **Éditeur de texte**, développez le sous-dossier **Tous les langages**, puis choisissez **Barres de défilement**.

> [!CAUTION]
> Cette page définit les options par défaut pour tous les langages de développement. La réinitialisation d’une option dans cette boîte de dialogue entraîne la réinitialisation des options de barres de défilement dans tous les langages, quels que soient les choix effectués. Pour modifier les options de l’éditeur de texte pour un seul langage, développez le sous-dossier de ce langage et sélectionnez ses pages d’options.

## <a name="show-horizontal-scroll-bar"></a>Afficher la barre de défilement horizontale

Quand cette option est sélectionnée, une barre de défilement horizontale s’affiche, ce qui vous permet de faire défiler horizontalement les éléments situés hors de la zone d’affichage de l’éditeur. Si les barres de défilement horizontales ne sont pas disponibles, vous pouvez faire défiler le contenu de l’éditeur à l’aide des touches du curseur.

## <a name="show-vertical-scroll-bar"></a>Afficher la barre de défilement verticale

Quand cette option est sélectionnée, une barre de défilement verticale s’affiche, ce qui vous permet de faire défiler verticalement les éléments situés hors de la zone d’affichage de l’éditeur. Si des barres de défilement verticales ne sont pas disponibles, vous pouvez faire défiler le contenu de l’éditeur à l’aide des touches du curseur et des touches Page précédente et Page suivante.

## <a name="display"></a>Afficher

### <a name="show-annotations-over-vertical-scroll-bar"></a>Afficher les annotations au-dessus de la barre de défilement verticale

Indiquez si la barre de défilement verticale doit afficher les annotations suivantes :

- modifications
- marques
- erreurs
- position du signe d’insertion

> [!TIP]
> L’option **Afficher les marques** inclut les points d’arrêt et les signets.

Testez-la en ouvrant un long fichier de code et en remplaçant du texte qui se répète à différents endroits dans le fichier. La barre de défilement affiche l'effet de ces remplacements. Vous pouvez ainsi annuler des modifications si vous avez remplacé un élément par erreur.

Consultez le billet de blog [Barre de défilement améliorée](/archive/blogs/cdnstudents/visual-studio-tips-and-tricks-enhanced-scroll-bar) sur la signification des différentes couleurs et des divers symboles utilisés quand vous modifiez du code.

## <a name="behavior"></a>Comportement

La barre de défilement offre deux modes : le mode barre et le mode mappage.

### <a name="use-bar-mode-for-vertical-scroll-bar"></a>Utiliser le mode barre pour la barre de défilement verticale

Le *mode barre* affiche les indicateurs d’annotation dans la barre de défilement. En cliquant sur la barre de défilement, la page défile vers le haut ou vers le bas, mais ne va pas à cet emplacement dans le fichier.

### <a name="use-map-mode-for-vertical-scroll-bar"></a>Utiliser le mode mappage pour la barre de défilement verticale

En *mode mappage*, quand vous cliquez sur un emplacement dans la barre de défilement, le curseur va à cet emplacement dans le fichier au lieu de faire simplement défiler la page vers le haut ou vers le bas. Les lignes de code sont indiquées, en miniature, dans la barre de défilement. Vous pouvez choisir la largeur de la colonne de mappage en sélectionnant une valeur dans **Vue d’ensemble de la source**. Pour permettre un aperçu plus grand du code quand vous placez le pointeur sur le mappage, sélectionnez l’option **Afficher une info-bulle d’aperçu**. Les zones réduites sont grisées différemment et se développent quand vous double-cliquez dessus.

> [!TIP]
> Vous pouvez désactiver l’affichage du code miniature en mode mappage en définissant **Vue d’ensemble de la source** sur **Désactivé**. Si l’option **Afficher une info-bulle d’aperçu** est sélectionnée, vous voyez toujours un aperçu du code à cet emplacement quand vous placez votre pointeur sur la barre de défilement, et le curseur va toujours à cet emplacement dans le fichier quand vous cliquez.

## <a name="see-also"></a>Voir aussi

- [Procédure : Personnaliser la barre de défilement](../how-to-track-your-code-by-customizing-the-scrollbar.md)