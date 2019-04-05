---
title: Extension de l’éditeur et les Services de langage | Microsoft Docs
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
ms.openlocfilehash: 9f828e6daff97f7c0ad8b3872691f5ad424cb2f4
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58938597"
---
# <a name="extending-the-editor-and-language-services"></a>Extension de l’éditeur et des services de langage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez ajouter des fonctionnalités de service de langage (tels qu’IntelliSense) à votre propre éditeur et étendre la plupart des fonctionnalités de l’éditeur de code Visual Studio.  Pour obtenir une liste complète de ce que vous pouvez étendre, consultez [Service de langage et les Points d’Extension Éditeur](../extensibility/language-service-and-editor-extension-points.md).  
  
 Vous étendez la plupart des fonctionnalités de l’éditeur à l’aide de Managed Extensibility Framework (MEF). Par exemple, si la fonctionnalité d’éditeur à étendre est la coloration de syntaxe, vous pouvez écrire un MEF *composant* qui définit les classifications pour lequel vous souhaitez différentes couleurs et comment vous souhaitez les gérée. L’éditeur prend également en charge plusieurs extensions de la même fonctionnalité.  
  
 La couche de présentation de l’éditeur est basée la Windows Presentation Framework (WPF). WPF fournit une bibliothèque de graphiques pour la mise en forme de texte flexible et fournit également des visualisations telles que des graphiques et des animations.  
  
 Le SDK Visual Studio fournit des adaptateurs appelés *shims* pour prendre en charge les VSPackages qui ont été écrites pour les versions antérieures. Néanmoins, si vous avez un VSPackage existant, nous recommandons que vous mettre à jour vers la nouvelle technologie pour obtenir la fiabilité et meilleures performances.  
  
## <a name="related-topics"></a>Rubriques connexes  
  
|Titre|Description|  
|-----------|-----------------|  
|[Bien démarrer avec les extensions du service de langage et de l’éditeur](../extensibility/getting-started-with-language-service-and-editor-extensions.md)|Explique comment créer une extension de l’éditeur.|  
|[Dans l’éditeur](../extensibility/inside-the-editor.md)|Décrit la structure générale de l’éditeur et répertorie certaines de ses fonctionnalités.|  
|[Managed Extensibility Framework (MEF) dans l’éditeur](../extensibility/managed-extensibility-framework-in-the-editor.md)|Explique comment utiliser le Managed Extensibility Framework (MEF) avec l’éditeur.|  
|[Points d’extension du service de langage et de l’éditeur](../extensibility/language-service-and-editor-extension-points.md)|Répertorie les points d’extension de l’éditeur. Points d’extension représentent les fonctionnalités de l’éditeur qui peuvent être étendues.|  
|[Procédure pas à pas : Création d’un ornement de vue, les commandes et paramètres (repères de colonne)](../extensibility/walkthrough-creating-a-view-adornment-commands-and-settings-column-guides.md)|Présente et explique la création d’un ornement de vue qui dessine des lignes gudie de colonne pour vous aider à maintenir le code à une certaine largeur d’affichage.  Montre également la lecture et écriture des paramètres ainsi que déclaration et l’implémentation des commandes que vous pouvez appeler à partir de la fenêtre de commande.|  
|[Importations de l’éditeur](../extensibility/editor-imports.md)|Répertorie les services qui une extension peut importer.|  
|[Adaptation du code hérité à l’éditeur](../extensibility/adapting-legacy-code-to-the-editor.md)|Explique les différentes méthodes pour adapter le code hérité (préalable Visual Studio 2010) pour étendre l’éditeur.|  
|[Migration d’un service de langage hérité](../extensibility/internals/migrating-a-legacy-language-service.md)|Explique comment migrer un service de langage VSPackage basé.|  
|[Procédure pas à pas : Liaison d’un Type de contenu à une Extension de nom de fichier](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)|Montre comment lier un type de contenu à une extension de nom de fichier.|  
|[Procédure pas à pas : Création d’un glyphe de marge](../extensibility/walkthrough-creating-a-margin-glyph.md)|Montre comment ajouter une icône pour une marge.|  
|[Procédure pas à pas : Mise en surbrillance de texte](../extensibility/walkthrough-highlighting-text.md)|Montre comment utiliser *balises* pour mettre en surbrillance de texte.|  
|[Procédure pas à pas : Le mode plan](../extensibility/walkthrough-outlining.md)|Montre comment ajouter le mode plan pour des types spécifiques d’accolades.|  
|[Procédure pas à pas : Affichage d’accolades correspondantes](../extensibility/walkthrough-displaying-matching-braces.md)|Montre comment mettre en surbrillance les accolades correspondantes.|  
|[Procédure pas à pas : Affichage des info-bulles Info express](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)|Montre comment afficher les fenêtres contextuelles info Express qui décrivent les éléments de code tels que les propriétés, méthodes et événements.|  
|[Procédure pas à pas : Affichage de l’aide de la Signature](../extensibility/walkthrough-displaying-signature-help.md)|Montre comment afficher les menus contextuels qui donnent des informations sur le nombre et les types de paramètres dans une signature.|  
|[Procédure pas à pas : Affichage de saisie semi-automatique des instructions](../extensibility/walkthrough-displaying-statement-completion.md)|Montre comment implémenter la saisie semi-automatique des instructions.|  
|[Procédure pas à pas : Implémentation d’extraits de Code](../extensibility/walkthrough-implementing-code-snippets.md)|Montre comment implémenter l’expansion d’extrait de code.|  
|[Procédure pas à pas : Displaying Light Bulb Suggestions](../extensibility/walkthrough-displaying-light-bulb-suggestions.md)|Montre comment afficher des ampoules pour obtenir des suggestions de code.|  
|[Procédure pas à pas : À l’aide d’une invite de commandes avec une Extension de l’éditeur](../extensibility/walkthrough-using-a-shell-command-with-an-editor-extension.md)|Montre comment associer une commande de menu dans un VSPackage à un composant MEF.|  
|[Procédure pas à pas : À l’aide d’une touche de raccourci avec une Extension de l’éditeur](../extensibility/walkthrough-using-a-shortcut-key-with-an-editor-extension.md)|Montre comment associer un raccourci du menu dans un VSPackage à un composant MEF.|  
|[Managed Extensibility Framework (MEF)](http://msdn.microsoft.com/library/6c61b4ec-c6df-4651-80f1-4854f8b14dde)|Fournit des informations sur le Managed Extensibility Framework (MEF).|  
|[Windows Presentation Foundation](http://msdn.microsoft.com/library/f667bd15-2134-41e9-b4af-5ced6fafab5d)|Fournit des informations sur Windows Presentation Foundation (WPF).|  
  
## <a name="reference"></a>Référence  
 L’éditeur de Visual Studio inclut des espaces de noms suivants.  
  
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
