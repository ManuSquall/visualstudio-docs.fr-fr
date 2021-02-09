---
title: Extension de l’éditeur et des services de langage | Microsoft Docs
description: Vous pouvez ajouter des fonctionnalités de service de langage à un éditeur et étendre les fonctionnalités de l’éditeur de code Visual Studio. En savoir plus sur les Managed Extensibility Framework.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new -
ms.assetid: 8d04f8db-eda7-4b3e-b6eb-c06df104502a
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 81b1e46db4f38f37296798a645d6547cdd6f017f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99895724"
---
# <a name="extend-the-editor-and-language-services"></a>Étendre l’éditeur et les services de langage
Vous pouvez ajouter des fonctionnalités du service de langage (par exemple, IntelliSense) à votre propre éditeur et étendre la plupart des fonctionnalités de l’éditeur de code Visual Studio.  Pour obtenir une liste complète de ce que vous pouvez étendre, consultez [services de langage et points d’extension](../extensibility/language-service-and-editor-extension-points.md)de l’éditeur.

 Vous étendez la plupart des fonctionnalités de l’éditeur à l’aide de la Managed Extensibility Framework (MEF). Par exemple, si la fonctionnalité de l’éditeur que vous souhaitez étendre est la coloration de la syntaxe, vous pouvez écrire une *partie du composant* MEF qui définit les classifications pour lesquelles vous souhaitez une coloration différente et la manière dont vous souhaitez les gérer. L’éditeur prend également en charge plusieurs extensions de la même fonctionnalité.

 La couche de présentation de l’éditeur est basée sur Windows Presentation Framework (WPF). WPF fournit une bibliothèque de graphiques pour la mise en forme de texte flexible et fournit également des visualisations telles que des graphiques et des animations.

 Le kit de développement logiciel (SDK) Visual Studio fournit des adaptateurs appelés *shims* pour prendre en charge les VSPackages qui ont été écrits pour des versions antérieures. Néanmoins, si vous disposez déjà d’un VSPackage, nous vous recommandons de le mettre à jour vers la nouvelle technologie pour obtenir de meilleures performances et une meilleure fiabilité.

## <a name="related-topics"></a>Rubriques connexes

|Titre|Description|
|-----------|-----------------|
|[Prise en main du service de langage et des extensions de l’éditeur](../extensibility/getting-started-with-language-service-and-editor-extensions.md)|Explique comment créer une extension de l’éditeur.|
|[Dans l’éditeur](../extensibility/inside-the-editor.md)|Décrit la structure générale de l’éditeur et répertorie certaines de ses fonctionnalités.|
|[Managed Extensibility Framework dans l’éditeur](../extensibility/managed-extensibility-framework-in-the-editor.md)|Explique comment utiliser le Managed Extensibility Framework (MEF) avec l’éditeur.|
|[Points d’extension du service de langage et de l’éditeur](../extensibility/language-service-and-editor-extension-points.md)|Répertorie les points d’extension de l’éditeur. Les points d’extension représentent les fonctionnalités de l’éditeur qui peuvent être étendues.|
|[Procédure pas à pas : créer un ornement, des commandes et des paramètres d’affichage (repères de colonne)](../extensibility/walkthrough-creating-a-view-adornment-commands-and-settings-column-guides.md)|Présente et explique la création d’un ornement de vue qui dessine des lignes de repère de colonne pour vous aider à conserver le code à une certaine largeur d’affichage.  Affiche également les paramètres de lecture et d’écriture, ainsi que la déclaration et l’implémentation des commandes que vous pouvez appeler à partir de la fenêtre de commande.|
|[Importations de l’éditeur](../extensibility/editor-imports.md)|Répertorie les services qu’une extension peut importer.|
|[Adapter le code hérité à l’éditeur](/previous-versions/visualstudio/visual-studio-2015/extensibility/adapting-legacy-code-to-the-editor?preserve-view=true&view=vs-2015)|Explique les différentes façons d’adapter le code hérité (pré-Visual Studio 2010) pour étendre l’éditeur.|
|[Migrer un service de langage hérité](../extensibility/internals/migrating-a-legacy-language-service.md)|Explique comment migrer un service de langage VSPackage.|
|[Procédure pas à pas : liaison d’un type de contenu à une extension de nom de fichier](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)|Montre comment lier un type de contenu à une extension de nom de fichier.|
|[Procédure pas à pas : créer un glyphe de marge](../extensibility/walkthrough-creating-a-margin-glyph.md)|Montre comment ajouter une icône à une marge.|
|[Procédure pas à pas : texte en surbrillance](../extensibility/walkthrough-highlighting-text.md)|Montre comment utiliser des *balises* pour mettre en surbrillance du texte.|
|[Procédure pas à pas : ajouter le mode plan](../extensibility/walkthrough-outlining.md)|Montre comment ajouter le mode plan à des types spécifiques d’accolades.|
|[Procédure pas à pas : afficher les accolades correspondantes](../extensibility/walkthrough-displaying-matching-braces.md)|Montre comment mettre en surbrillance les accolades correspondantes.|
|[Procédure pas à pas : afficher les info-bulles Info Express](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)|Montre comment afficher des menus contextuels Express qui décrivent des éléments de code tels que les propriétés, les méthodes et les événements.|
|[Procédure pas à pas : afficher l’aide sur les signatures](../extensibility/walkthrough-displaying-signature-help.md)|Montre comment afficher des fenêtres contextuelles qui fournissent des informations sur le nombre et les types de paramètres dans une signature.|
|[Procédure pas à pas : afficher la saisie semi-automatique des instructions](../extensibility/walkthrough-displaying-statement-completion.md)|Montre comment implémenter la saisie semi-automatique des instructions.|
|[Procédure pas à pas : implémenter des extraits de code](../extensibility/walkthrough-implementing-code-snippets.md)|Montre comment implémenter l’expansion d’extrait de code.|
|[Procédure pas à pas : afficher les suggestions d’ampoules](../extensibility/walkthrough-displaying-light-bulb-suggestions.md)|Montre comment afficher les ampoules pour les suggestions de code.|
|[Procédure pas à pas : utiliser une commande d’interpréteur de commandes avec une extension d’éditeur](../extensibility/walkthrough-using-a-shell-command-with-an-editor-extension.md)|Montre comment associer une commande de menu dans un VSPackage à un composant MEF.|
|[Procédure pas à pas : utiliser une touche de raccourci avec une extension d’éditeur](../extensibility/walkthrough-using-a-shortcut-key-with-an-editor-extension.md)|Montre comment associer un raccourci de menu dans un VSPackage à un composant MEF.|
|[Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index)|Fournit des informations sur le Managed Extensibility Framework (MEF).|
|[Windows Presentation Foundation](/dotnet/framework/wpf/index)|Fournit des informations sur le Windows Presentation Foundation (WPF).|

## <a name="reference"></a>Référence
 L’éditeur Visual Studio comprend les espaces de noms suivants.

 <xref:Microsoft.VisualStudio.Language.Intellisense>

 <xref:Microsoft.VisualStudio.Language.StandardClassification>

 <xref:Microsoft.VisualStudio.Editor>

 <xref:Microsoft.VisualStudio.Text>

 <xref:Microsoft.VisualStudio.Text.Adornments>

 <xref:Microsoft.VisualStudio.Text.Classification>

 <xref:Microsoft.VisualStudio.Text.Differencing>

 <xref:Microsoft.VisualStudio.Text.Document>

 <xref:Microsoft.VisualStudio.Text.Editor>

 <xref:Microsoft.VisualStudio.Text.Editor.OptionsExtensionMethods>

 <xref:Microsoft.VisualStudio.Text.Formatting>

 <xref:Microsoft.VisualStudio.Text.IncrementalSearch>

 <xref:Microsoft.VisualStudio.Text.Operations>

 <xref:Microsoft.VisualStudio.Text.Outlining>

 <xref:Microsoft.VisualStudio.Text.Projection>

 <xref:Microsoft.VisualStudio.Text.Tagging>

 <xref:Microsoft.VisualStudio.Utilities>