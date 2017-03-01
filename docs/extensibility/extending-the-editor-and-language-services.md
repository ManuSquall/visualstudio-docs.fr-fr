---
title: "Extension de l’éditeur et les Services de langage | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new -
ms.assetid: 8d04f8db-eda7-4b3e-b6eb-c06df104502a
caps.latest.revision: 22
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 4d04f4588b1005e9b5ccb42c6042d01aacb45710
ms.lasthandoff: 02/22/2017

---
# <a name="extending-the-editor-and-language-services"></a>Extension de l’éditeur et les Services de langage
Vous pouvez ajouter des fonctionnalités de service de langage (tels qu’IntelliSense) pour votre propre éditeur et d’étendre la plupart des fonctionnalités de l’éditeur de code Visual Studio.  Pour obtenir une liste complète de ce que vous pouvez étendre, consultez [Service de langage et les Points d’Extension Éditeur](../extensibility/language-service-and-editor-extension-points.md).  
  
 Vous étendez la plupart des fonctionnalités de l’éditeur à l’aide de Managed Extensibility Framework (MEF). Par exemple, si la fonctionnalité de l’éditeur que vous souhaitez étendre est la coloration de syntaxe, vous pouvez écrire un MEF *composant* qui définit les classifications pour lesquelles vous souhaitez différentes couleurs et comment vous souhaitez les géré. L’éditeur prend également en charge plusieurs extensions de la même fonctionnalité.  
  
 La couche de présentation éditeur Windows Presentation Framework (WPF). WPF fournit une bibliothèque de graphiques pour mettre en forme le texte flexible et fournit également des visualisations telles que des graphiques et des animations.  
  
 Le Kit de développement logiciel Visual Studio fournit des adaptateurs appelés *shims* pour prendre en charge les packages VS qui ont été écrits pour les versions antérieures. Néanmoins, si vous avez un VSPackage existant, nous vous recommandons de mettre à la nouvelle technologie pour obtenir de meilleures performances et la fiabilité.  
  
## <a name="related-topics"></a>Rubriques connexes  
  
|Titre|Description|  
|-----------|-----------------|  
|[Prise en main de Service de langage et les Extensions de l’éditeur](../extensibility/getting-started-with-language-service-and-editor-extensions.md)|Explique comment créer une extension de l’éditeur.|  
|[Dans l’éditeur](../extensibility/inside-the-editor.md)|Décrit la structure générale de l’éditeur et répertorie certaines de ses fonctionnalités.|  
|[Managed Extensibility Framework dans l’éditeur](../extensibility/managed-extensibility-framework-in-the-editor.md)|Explique comment utiliser Managed Extensibility Framework (MEF) avec l’éditeur.|  
|[Service de langage et les Points d’Extension Éditeur](../extensibility/language-service-and-editor-extension-points.md)|Répertorie les points d’extension de l’éditeur. Points d’extension représentent les fonctionnalités de l’éditeur qui peuvent être étendues.|  
|[Procédure pas à pas : Création d’un ornement de vue, les commandes et paramètres (repères de colonne)](../extensibility/walkthrough-creating-a-view-adornment-commands-and-settings-column-guides.md)|Guide et explique la création d’un ornement de vue qui dessine des lignes gudie de colonne pour vous aider à maintenir le code pour une certaine largeur d’affichage.  Montre également lire et écrire les paramètres ainsi que déclarer et implémenter des commandes que vous pouvez appeler à partir de la fenêtre de commande.|  
|[Importations d’éditeur](../extensibility/editor-imports.md)|Répertorie les services une extension peut importer.|  
|[Adaptation de l’éditeur de Code hérité](../extensibility/adapting-legacy-code-to-the-editor.md)|Décrit les différents moyens d’adapter le code hérité (avant Visual Studio 2010) pour étendre l’éditeur.|  
|[Migration d’un Service de langage hérité](../extensibility/internals/migrating-a-legacy-language-service.md)|Explique comment migrer un service de langage VSPackage en fonction.|  
|[Procédure pas à pas : Liaison d’un Type de contenu à une Extension de nom de fichier](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)|Montre comment associer un type de contenu à une extension de nom de fichier.|  
|[Procédure pas à pas : Création d’un glyphe de marge](../extensibility/walkthrough-creating-a-margin-glyph.md)|Montre comment ajouter une icône à une marge.|  
|[Procédure pas à pas : Mise en surbrillance de texte](../extensibility/walkthrough-highlighting-text.md)|Montre comment utiliser *balises* pour mettre en surbrillance de texte.|  
|[Procédure pas à pas : mise en relief](../extensibility/walkthrough-outlining.md)|Montre comment ajouter le mode plan pour des types spécifiques d’accolades.|  
|[Procédure pas à pas : Affichage des accolades correspondantes](../extensibility/walkthrough-displaying-matching-braces.md)|Montre comment mettre en évidence les accolades correspondantes.|  
|[Procédure pas à pas : Affichage des info-bulles Info express](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)|Montre comment afficher les fenêtres contextuelles info Express qui décrivent des éléments de code tels que les propriétés, méthodes et événements.|  
|[Procédure pas à pas : Affichage de l’aide de Signature](../extensibility/walkthrough-displaying-signature-help.md)|Montre comment afficher les fenêtres contextuelles qui fournissent des informations sur le nombre et les types de paramètres dans une signature.|  
|[Procédure pas à pas : affichage de la saisie semi-automatique des instructions](../extensibility/walkthrough-displaying-statement-completion.md)|Montre comment implémenter la saisie semi-automatique des instructions.|  
|[Procédure pas à pas : Implémentation d’extraits de Code](../extensibility/walkthrough-implementing-code-snippets.md)|Montre comment implémenter l’expansion des extraits de code.|  
|[Procédure pas à pas : Affichage des Suggestions d’ampoule](../extensibility/walkthrough-displaying-light-bulb-suggestions.md)|Montre comment afficher des ampoules pour obtenir des suggestions de code.|  
|[Procédure pas à pas : Utilisant une invite de commandes avec une Extension de l’éditeur](../extensibility/walkthrough-using-a-shell-command-with-an-editor-extension.md)|Montre comment associer une commande de menu dans un VSPackage comportant un composant MEF.|  
|[Procédure pas à pas : L’utilisation d’une touche de raccourci avec une Extension de l’éditeur](../extensibility/walkthrough-using-a-shortcut-key-with-an-editor-extension.md)|Montre comment associer un raccourci de menu dans un VSPackage comportant un composant MEF.|  
|[Managed Extensibility Framework (MEF)](http://msdn.microsoft.com/Library/6c61b4ec-c6df-4651-80f1-4854f8b14dde)|Fournit des informations sur le Managed Extensibility Framework (MEF).|  
|[Windows Presentation Foundation](http://msdn.microsoft.com/Library/f667bd15-2134-41e9-b4af-5ced6fafab5d)|Fournit des informations sur Windows Presentation Foundation (WPF).|  
  
## <a name="reference"></a>Référence  
 L’éditeur Visual Studio inclut des espaces de noms suivants.  
  
 <xref:Microsoft.VisualStudio.Language.Intellisense></xref:Microsoft.VisualStudio.Language.Intellisense>  
  
 <xref:Microsoft.VisualStudio.Language.StandardClassification></xref:Microsoft.VisualStudio.Language.StandardClassification>  
  
 <xref:Microsoft.VisualStudio.Editor></xref:Microsoft.VisualStudio.Editor>  
  
 <xref:Microsoft.VisualStudio.Text></xref:Microsoft.VisualStudio.Text>  
  
 <xref:Microsoft.VisualStudio.Text.Adornments></xref:Microsoft.VisualStudio.Text.Adornments>  
  
 <xref:Microsoft.VisualStudio.Text.Classification></xref:Microsoft.VisualStudio.Text.Classification>  
  
 <xref:Microsoft.VisualStudio.Text.Differencing></xref:Microsoft.VisualStudio.Text.Differencing>  
  
 <xref:Microsoft.VisualStudio.Text.Document></xref:Microsoft.VisualStudio.Text.Document>  
  
 <xref:Microsoft.VisualStudio.Text.Editor></xref:Microsoft.VisualStudio.Text.Editor>  
  
 <xref:Microsoft.VisualStudio.Text.Editor.OptionsExtensionMethods></xref:Microsoft.VisualStudio.Text.Editor.OptionsExtensionMethods>  
  
 <xref:Microsoft.VisualStudio.Text.Formatting></xref:Microsoft.VisualStudio.Text.Formatting>  
  
 <xref:Microsoft.VisualStudio.Text.IncrementalSearch></xref:Microsoft.VisualStudio.Text.IncrementalSearch>  
  
 <xref:Microsoft.VisualStudio.Text.Operations></xref:Microsoft.VisualStudio.Text.Operations>  
  
 <xref:Microsoft.VisualStudio.Text.Outlining></xref:Microsoft.VisualStudio.Text.Outlining>  
  
 <xref:Microsoft.VisualStudio.Text.Projection></xref:Microsoft.VisualStudio.Text.Projection>  
  
 <xref:Microsoft.VisualStudio.Text.Tagging></xref:Microsoft.VisualStudio.Text.Tagging>  
  
 <xref:Microsoft.VisualStudio.Utilities></xref:Microsoft.VisualStudio.Utilities>
