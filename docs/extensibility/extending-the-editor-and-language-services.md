---
title: Élargir les services d’éditeur et de langue (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new -
ms.assetid: 8d04f8db-eda7-4b3e-b6eb-c06df104502a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 239c638ec32cc0dc2b2e275a5dbe0c4213a3423e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711713"
---
# <a name="extend-the-editor-and-language-services"></a>Étendre les services d’éditeur et de langue
Vous pouvez ajouter des fonctionnalités de service linguistique (comme IntelliSense) à votre propre éditeur, et étendre la plupart des fonctionnalités de l’éditeur de code Visual Studio.  Pour une liste complète de ce que vous pouvez étendre, voir [Le service de langue et les points d’extension de l’éditeur](../extensibility/language-service-and-editor-extension-points.md).

 Vous étendez la plupart des fonctionnalités de l’éditeur en utilisant le Cadre d’Extégabilité gérée (MEF). Par exemple, si la fonction d’éditeur que vous souhaitez étendre est la coloration syntaxe, vous pouvez écrire une *partie composante* MEF qui définit les classifications pour lesquelles vous voulez coloration différente et comment vous voulez qu’ils sont manipulés. L’éditeur prend également en charge plusieurs extensions d’une même fonctionnalité.

 La couche de présentation de l’éditeur est basée sur le cadre de présentation Windows (WPF). WPF fournit une bibliothèque graphique pour le formatage flexible de texte, et fournit également des visualisations telles que des graphiques et des animations.

 Le Visual Studio SDK fournit des adaptateurs connus sous le nom *de cales* pour prendre en charge VSPackages qui ont été écrits pour les versions antérieures. Néanmoins, si vous avez un VSPackage existant, nous vous recommandons de le mettre à jour vers la nouvelle technologie pour obtenir de meilleures performances et fiabilité.

## <a name="related-topics"></a>Rubriques connexes

|Intitulé|Description|
|-----------|-----------------|
|[Commencer avec le service linguistique et les extensions d’éditeur](../extensibility/getting-started-with-language-service-and-editor-extensions.md)|Explique comment créer une extension à l’éditeur.|
|[À l’intérieur de l’éditeur](../extensibility/inside-the-editor.md)|Décrit la structure générale de l’éditeur, et énumère certaines de ses caractéristiques.|
|[Cadre d’extéabilité géré dans l’éditeur](../extensibility/managed-extensibility-framework-in-the-editor.md)|Explique comment utiliser le Cadre d’exténuabilité gérée (MEF) avec l’éditeur.|
|[Service linguistique et points d’extension de l’éditeur](../extensibility/language-service-and-editor-extension-points.md)|Répertorie les points d’extension de l’éditeur. Les points d’extension représentent les fonctionnalités de l’éditeur qui peuvent être étendues.|
|[Procédure pas à pas : Créez une parure de vue, des commandes et des paramètres (guides de colonne)](../extensibility/walkthrough-creating-a-view-adornment-commands-and-settings-column-guides.md)|Marche à travers et explique la construction d’une parure de vue qui dessine des lignes de guidage de colonne pour vous aider à garder le code à une certaine largeur d’affichage.  Affiche également les paramètres de lecture et d’écriture ainsi que la déclaration et la mise en œuvre des commandes que vous pouvez invoquer à partir de la fenêtre de commande.|
|[Importations de rédacteurs](../extensibility/editor-imports.md)|Répertorie les services qu’une extension peut importer.|
|[Adapter le code hérité à l’éditeur](/visualstudio/extensibility/adapting-legacy-code-to-the-editor?view=vs-2015)|Explique différentes façons d’adapter le code hérité (pré-Visual Studio 2010) pour étendre l’éditeur.|
|[Migrer un service linguistique hérité](../extensibility/internals/migrating-a-legacy-language-service.md)|Explique comment migrer un service linguistique basé sur VSPackage.|
|[Procédure pas à pas : liez un type de contenu à une extension de nom de fichier](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)|Affiche comment lier un type de contenu à une extension de nom de fichier.|
|[Procédure pas à pas: Créer un glyphe de marge](../extensibility/walkthrough-creating-a-margin-glyph.md)|Montre comment ajouter une icône à une marge.|
|[Procédure pas à pas : Mettre en évidence le texte](../extensibility/walkthrough-highlighting-text.md)|Montre comment utiliser *des balises* pour mettre en évidence le texte.|
|[Procédure pas à pas : Ajouter la mise en valeur](../extensibility/walkthrough-outlining.md)|Montre comment ajouter la mise en valeur pour des types spécifiques d’accolades.|
|[Procédure pas à pas : Afficher des accolades assorties](../extensibility/walkthrough-displaying-matching-braces.md)|Montre comment mettre en évidence les accolades assorties.|
|[Procédure pas à pas: Afficher des outils QuickInfo](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)|Montre comment afficher des popups QuickInfo qui décrivent des éléments de code tels que les propriétés, les méthodes et les événements.|
|[Procédure pas à pas : Montrez l’aide à la signature](../extensibility/walkthrough-displaying-signature-help.md)|Montre comment afficher des popups qui donnent des informations sur le nombre et les types de paramètres dans une signature.|
|[Procédure pas à pas : afficher la saisie semi-automatique des instructions](../extensibility/walkthrough-displaying-statement-completion.md)|Montre comment mettre en œuvre l’achèvement de l’énoncé.|
|[Procédure pas à pas : Implémentez des extraits de code](../extensibility/walkthrough-implementing-code-snippets.md)|Montre comment implémenter l’extension de l’extrait de code.|
|[Procédure pas à pas : Afficher les suggestions d’ampoules](../extensibility/walkthrough-displaying-light-bulb-suggestions.md)|Montre comment afficher des ampoules pour des suggestions de code.|
|[Procédure pas à pas : Utilisez une commande de coquillages avec une extension d’éditeur](../extensibility/walkthrough-using-a-shell-command-with-an-editor-extension.md)|Montre comment associer une commande de menu dans un VSPackage avec un composant MEF.|
|[Procédure pas à pas : Utilisez une clé raccourcie avec une extension de l’éditeur](../extensibility/walkthrough-using-a-shortcut-key-with-an-editor-extension.md)|Montre comment associer un raccourci de menu dans un VSPackage avec un composant MEF.|
|[Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index)|Fournit des informations sur le Cadre d’exténuabilité gérée (MEF).|
|[Windows Presentation Foundation](/dotnet/framework/wpf/index)|Fournit des informations sur la Windows Presentation Foundation (WPF).|

## <a name="reference"></a>Informations de référence
 L’éditeur visual Studio inclut les espaces de nom suivants.

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
