---
title: Extension de l’éditeur et des services de langage | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new -
ms.assetid: 8d04f8db-eda7-4b3e-b6eb-c06df104502a
caps.latest.revision: 23
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 085e1b5c1fbfbbaf5649966738f2864e0b72ed35
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65674783"
---
# <a name="extending-the-editor-and-language-services"></a>Extension de l’éditeur et des services de langage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez ajouter des fonctionnalités du service de langage (par exemple, IntelliSense) à votre propre éditeur et étendre la plupart des fonctionnalités de l’éditeur de code Visual Studio.  Pour obtenir une liste complète de ce que vous pouvez étendre, consultez [services de langage et points d’extension](../extensibility/language-service-and-editor-extension-points.md)de l’éditeur.  
  
 Vous étendez la plupart des fonctionnalités de l’éditeur à l’aide de la Managed Extensibility Framework (MEF). Par exemple, si la fonctionnalité de l’éditeur que vous souhaitez étendre est la coloration de la syntaxe, vous pouvez écrire une *partie du composant* MEF qui définit les classifications pour lesquelles vous souhaitez une coloration différente et la manière dont vous souhaitez les gérer. L’éditeur prend également en charge plusieurs extensions de la même fonctionnalité.  
  
 La couche de présentation de l’éditeur est basée sur Windows Presentation Framework (WPF). WPF fournit une bibliothèque de graphiques pour la mise en forme de texte flexible et fournit également des visualisations telles que des graphiques et des animations.  
  
 Le kit de développement logiciel (SDK) Visual Studio fournit des adaptateurs appelés *shims* pour prendre en charge les VSPackages qui ont été écrits pour des versions antérieures. Néanmoins, si vous disposez déjà d’un VSPackage, nous vous recommandons de le mettre à jour vers la nouvelle technologie pour obtenir de meilleures performances et une meilleure fiabilité.  
  
## <a name="related-topics"></a>Rubriques connexes  
  
|Titre|Description|  
|-----------|-----------------|  
|[Bien démarrer avec les extensions du service de langage et de l’éditeur](../extensibility/getting-started-with-language-service-and-editor-extensions.md)|Explique comment créer une extension de l’éditeur.|  
|[Dans l’éditeur](../extensibility/inside-the-editor.md)|Décrit la structure générale de l’éditeur et répertorie certaines de ses fonctionnalités.|  
|[Managed Extensibility Framework (MEF) dans l’éditeur](../extensibility/managed-extensibility-framework-in-the-editor.md)|Explique comment utiliser le Managed Extensibility Framework (MEF) avec l’éditeur.|  
|[Points d’extension du service de langage et de l’éditeur](../extensibility/language-service-and-editor-extension-points.md)|Répertorie les points d’extension de l’éditeur. Les points d’extension représentent les fonctionnalités de l’éditeur qui peuvent être étendues.|  
|[Procédure pas à pas : Création d’un ornement, de commandes et de paramètres pour l’affichage (repères de colonne)](../extensibility/walkthrough-creating-a-view-adornment-commands-and-settings-column-guides.md)|Présente et explique la création d’un ornement de vue qui dessine des lignes de gudie de colonne pour vous aider à conserver le code à une certaine largeur d’affichage.  Affiche également les paramètres de lecture et d’écriture, ainsi que la déclaration et l’implémentation des commandes que vous pouvez appeler à partir de la fenêtre de commande.|  
|[Importations de l’éditeur](../extensibility/editor-imports.md)|Répertorie les services qu’une extension peut importer.|  
|[Adaptation du code hérité dans l’éditeur](../extensibility/adapting-legacy-code-to-the-editor.md)|Explique les différentes façons d’adapter le code hérité (pré-Visual Studio 2010) pour étendre l’éditeur.|  
|[Migration d’un service de langage hérité](../extensibility/internals/migrating-a-legacy-language-service.md)|Explique comment migrer un service de langage VSPackage.|  
|[Procédure pas à pas : Liaison d’un type de contenu à une extension de nom de fichier](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)|Montre comment lier un type de contenu à une extension de nom de fichier.|  
|[Procédure pas à pas : Création d’un glyphe de marge](../extensibility/walkthrough-creating-a-margin-glyph.md)|Montre comment ajouter une icône à une marge.|  
|[Procédure pas à pas : Mise en surbrillance de texte](../extensibility/walkthrough-highlighting-text.md)|Montre comment utiliser des *balises* pour mettre en surbrillance du texte.|  
|[Procédure pas à pas : Mode Plan](../extensibility/walkthrough-outlining.md)|Montre comment ajouter le mode plan à des types spécifiques d’accolades.|  
|[Procédure pas à pas : Affichage d’accolades correspondantes](../extensibility/walkthrough-displaying-matching-braces.md)|Montre comment mettre en surbrillance les accolades correspondantes.|  
|[Procédure pas à pas : Affichage d’info-bulles Info express](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)|Montre comment afficher des menus contextuels Express qui décrivent des éléments de code tels que les propriétés, les méthodes et les événements.|  
|[Procédure pas à pas : Affichage d’aide sur les signatures](../extensibility/walkthrough-displaying-signature-help.md)|Montre comment afficher des fenêtres contextuelles qui fournissent des informations sur le nombre et les types de paramètres dans une signature.|  
|[Procédure pas à pas : affichage de la saisie semi-automatique des instructions](../extensibility/walkthrough-displaying-statement-completion.md)|Montre comment implémenter la saisie semi-automatique des instructions.|  
|[Procédure pas à pas : Implémentation d’extraits de code](../extensibility/walkthrough-implementing-code-snippets.md)|Montre comment implémenter l’expansion d’extrait de code.|  
|[Procédure pas à pas : Affichage de suggestions Ampoule](../extensibility/walkthrough-displaying-light-bulb-suggestions.md)|Montre comment afficher les ampoules pour les suggestions de code.|  
|[Procédure pas à pas : Utilisation d’une commande Shell avec une extension de l’éditeur](../extensibility/walkthrough-using-a-shell-command-with-an-editor-extension.md)|Montre comment associer une commande de menu dans un VSPackage à un composant MEF.|  
|[Procédure pas à pas : Utilisation d’une touche de raccourci avec une extension de l’éditeur](../extensibility/walkthrough-using-a-shortcut-key-with-an-editor-extension.md)|Montre comment associer un raccourci de menu dans un VSPackage à un composant MEF.|  
|[Managed Extensibility Framework (MEF)](https://msdn.microsoft.com/library/6c61b4ec-c6df-4651-80f1-4854f8b14dde)|Fournit des informations sur le Managed Extensibility Framework (MEF).|  
|[Windows Presentation Foundation](https://msdn.microsoft.com/library/f667bd15-2134-41e9-b4af-5ced6fafab5d)|Fournit des informations sur le Windows Presentation Foundation (WPF).|  
  
## <a name="reference"></a>Informations de référence  
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
