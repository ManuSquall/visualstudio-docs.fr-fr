---
title: "Extension de l’éditeur et Services de langage | Documents Microsoft"
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
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 4e81409f8ac93c80bf16b5040c6f388b64ffabbe
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="extending-the-editor-and-language-services"></a>Extension de l’éditeur et Services de langage
Vous pouvez ajouter des fonctionnalités de service de langage (telles qu’IntelliSense) à votre propre éditeur et étendre la plupart des fonctionnalités de l’éditeur de code Visual Studio.  Pour obtenir une liste complète de ce que vous pouvez étendre, consultez [Service de langage et les Points d’Extension Éditeur](../extensibility/language-service-and-editor-extension-points.md).  
  
 Vous étendez la plupart des fonctionnalités de l’éditeur à l’aide de Managed Extensibility Framework (MEF). Par exemple, si la fonctionnalité de l’éditeur que vous souhaitez étendre est une coloration de syntaxe, vous pouvez écrire un MEF *composant* qui définit les classifications pour lequel vous souhaitez que la coloration différents et comment vous souhaitez les géré. L’éditeur prend également en charge plusieurs extensions de la même fonctionnalité.  
  
 La couche de présentation de l’éditeur est basée Windows Presentation Framework (WPF). WPF fournit une bibliothèque de graphiques pour la mise en forme du texte flexible et fournit également des visualisations telles que les graphiques et les animations.  
  
 Le Kit de développement logiciel Visual Studio fournit des adaptateurs appelés *shims* pour prendre en charge des VSPackages qui ont été écrites pour les versions antérieures. Néanmoins, si vous avez un VSPackage existant, nous recommandons que vous mettre à jour vers la nouvelle technologie pour obtenir de meilleures performances et fiabilité.  
  
## <a name="related-topics"></a>Rubriques connexes  
  
|Titre|Description|  
|-----------|-----------------|  
|[Bien démarrer avec les extensions du service de langage et de l’éditeur](../extensibility/getting-started-with-language-service-and-editor-extensions.md)|Explique comment créer une extension à l’éditeur.|  
|[Dans l’éditeur](../extensibility/inside-the-editor.md)|Décrit la structure générale de l’éditeur et répertorie certaines de ses fonctionnalités.|  
|[Managed Extensibility Framework (MEF) dans l’éditeur](../extensibility/managed-extensibility-framework-in-the-editor.md)|Explique comment utiliser Managed Extensibility Framework (MEF) avec l’éditeur.|  
|[Points d’extension du service de langage et de l’éditeur](../extensibility/language-service-and-editor-extension-points.md)|Répertorie les points d’extension de l’éditeur. Points d’extension représentent les fonctionnalités de l’éditeur qui peuvent être étendues.|  
|[Procédure pas à pas : Création d’un ornement, de commandes et de paramètres pour l’affichage (repères de colonne)](../extensibility/walkthrough-creating-a-view-adornment-commands-and-settings-column-guides.md)|Guide et explique la création d’un ornement de vue qui extrait les lignes gudie de colonne pour vous aider à maintenir le code pour une certaine largeur d’affichage.  Montre également la lecture et écriture des paramètres ainsi que déclaration et l’implémentation de commandes que vous pouvez appeler à partir de la fenêtre de commande.|  
|[Importations de l’éditeur](../extensibility/editor-imports.md)|Répertorie les services une extension peut importer.|  
|[Adaptation de l’éditeur de Code hérité](../extensibility/adapting-legacy-code-to-the-editor.md)|Décrit les différents moyens d’adapter le code hérité (avant Visual Studio 2010) pour étendre l’éditeur.|  
|[Migration d’un service de langage hérité](../extensibility/internals/migrating-a-legacy-language-service.md)|Explique comment migrer un service de langage VSPackage basé.|  
|[Procédure pas à pas : Liaison d’un type de contenu à une extension de nom de fichier](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)|Montre comment lier un type de contenu pour une extension de nom de fichier.|  
|[Procédure pas à pas : Création d’un glyphe de marge](../extensibility/walkthrough-creating-a-margin-glyph.md)|Montre comment ajouter une icône pour une marge.|  
|[Procédure pas à pas : Mise en surbrillance de texte](../extensibility/walkthrough-highlighting-text.md)|Montre comment utiliser *balises* pour mettre en surbrillance de texte.|  
|[Procédure pas à pas : Mode Plan](../extensibility/walkthrough-outlining.md)|Montre comment ajouter le mode plan pour certains genres d’accolades.|  
|[Procédure pas à pas : Affichage d’accolades correspondantes](../extensibility/walkthrough-displaying-matching-braces.md)|Montre comment mettre en évidence les accolades correspondantes.|  
|[Procédure pas à pas : Affichage d’info-bulles Info express](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)|Montre comment afficher les fenêtres contextuelles info Express qui décrivent les éléments de code tels que les propriétés, méthodes et événements.|  
|[Procédure pas à pas : Affichage d’aide sur les signatures](../extensibility/walkthrough-displaying-signature-help.md)|Montre comment afficher les fenêtres contextuelles qui fournissent des informations sur le nombre et les types de paramètres dans une signature.|  
|[Procédure pas à pas : affichage de la saisie semi-automatique des instructions](../extensibility/walkthrough-displaying-statement-completion.md)|Montre comment implémenter la saisie semi-automatique des instructions.|  
|[Procédure pas à pas : Implémentation d’extraits de code](../extensibility/walkthrough-implementing-code-snippets.md)|Montre comment implémenter l’expansion de l’extrait de code.|  
|[Procédure pas à pas : Affichage de suggestions Ampoule](../extensibility/walkthrough-displaying-light-bulb-suggestions.md)|Montre comment afficher les ampoules pour obtenir des suggestions de code.|  
|[Procédure pas à pas : Utilisation d’une commande Shell avec une extension de l’éditeur](../extensibility/walkthrough-using-a-shell-command-with-an-editor-extension.md)|Montre comment associer une commande de menu dans un VSPackage à un composant MEF.|  
|[Procédure pas à pas : Utilisation d’une touche de raccourci avec une extension de l’éditeur](../extensibility/walkthrough-using-a-shortcut-key-with-an-editor-extension.md)|Montre comment associer un raccourci de menu dans un VSPackage à un composant MEF.|  
|[Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index)|Fournit des informations sur Managed Extensibility Framework (MEF).|  
|[Windows Presentation Foundation](/dotnet/framework/wpf/index)|Fournit des informations sur Windows Presentation Foundation (WPF).|  
  
## <a name="reference"></a>Référence  
 L’éditeur Visual Studio inclut des espaces de noms suivants.  
  
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