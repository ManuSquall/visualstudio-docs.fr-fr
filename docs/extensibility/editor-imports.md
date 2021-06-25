---
title: Importations de l’éditeur | Microsoft Docs
description: Découvrez comment importer des services de l’éditeur, des fabriques et des courtiers qui fournissent votre extension avec différents types d’accès à l’éditeur principal.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- editors [Visual Studio SDK], new - services
ms.assetid: 8d096de3-33b4-427a-a122-4aeff8a72da0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7f2fa91b41017512b3f38ad61b800b293e0abaa1
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898342"
---
# <a name="editor-imports"></a>Importations de l’éditeur
Vous pouvez importer un certain nombre de services de l’éditeur, de fabriques et de courtiers qui fournissent votre extension avec différents types d’accès à l’éditeur principal. Par exemple, vous pouvez importer le <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> pour fournir un <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator> pour un type de contenu donné. (Ce navigateur vous permet d’effectuer différents types de recherches sur une mémoire tampon de texte.)

 Pour utiliser une importation d’éditeur, importez-la sous forme de champ ou de propriété d’une classe qui exporte une partie Managed Extensibility Framework composant.

> [!NOTE]
> Pour plus d’informations sur la Managed Extensibility Framework, consultez [Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index).

## <a name="import-syntax"></a>Importer la syntaxe
 L’exemple suivant montre comment importer le service de fabrique des options de l’éditeur.

```
[Import]
internal IEditorOptionsFactoryService EditorOptions { get; set; }
```

 Si vous souhaitez importer le service en tant que champ et non pas en tant que propriété, vous devez lui affecter la valeur `null` dans la déclaration afin d’éviter les avertissements du compilateur relatifs à ne pas assigner à une variable :

```
[Import]
internal IEditorOptionsFactoryService m_editorOptions = null;
```

 Pour obtenir plus d’exemples d’utilisation des importations, consultez les procédures pas à pas suivantes :

- [Procédure pas à pas : créer un glyphe de marge](../extensibility/walkthrough-creating-a-margin-glyph.md)

- [Procédure pas à pas : personnaliser l’affichage du texte](../extensibility/walkthrough-customizing-the-text-view.md)

- [Procédure pas à pas : texte en surbrillance](../extensibility/walkthrough-highlighting-text.md)

- [Procédure pas à pas : afficher les info-bulles Info Express](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)

- [Procédure pas à pas : afficher l’aide sur les signatures](../extensibility/walkthrough-displaying-signature-help.md)

- [Procédure pas à pas : afficher la saisie semi-automatique des instructions](../extensibility/walkthrough-displaying-statement-completion.md)

- [Procédure pas à pas : afficher les suggestions d’ampoules](../extensibility/walkthrough-displaying-light-bulb-suggestions.md)

## <a name="import-the-service-provider"></a>Importer le fournisseur de services
 Vous pouvez également importer un <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> (trouvé dans l’assembly Microsoft. VisualStudio. Shell. immuable. 10.0) de la même façon pour accéder aux services Visual Studio :

```csharp
[Import]
internal SVsServiceProvider ServiceProvider = null;
```

 Pour plus d’informations, consultez [procédure pas à pas : accès à l’objet DTE à partir d’une extension d’éditeur](../extensibility/walkthrough-accessing-the-dte-object-from-an-editor-extension.md) .

## <a name="services"></a>Services
 Les services de l’éditeur sont généralement des entités uniques qui fournissent un service et qui sont partagées entre plusieurs composants.

|Importer|offre les services|
|------------|--------------|
|<xref:Microsoft.VisualStudio.Utilities.IFileExtensionRegistryService>|Relation entre les extensions de fichier et les <xref:Microsoft.VisualStudio.Utilities.IContentType> objets.|
|<xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService>|Collection d'objets <xref:Microsoft.VisualStudio.Utilities.IContentType>.|
|<xref:Microsoft.VisualStudio.Editor.IVsFontsAndColorsInformationService>|<xref:Microsoft.VisualStudio.Editor.IVsFontsAndColorsInformation> objets.|
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>|Nombreux objets d’adaptateur d’éditeur :<br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|
|<xref:Microsoft.VisualStudio.Text.IncrementalSearch.IIncrementalSearchFactoryService>|<xref:Microsoft.VisualStudio.Text.IncrementalSearch.IIncrementalSearch>Objet pour un affichage de texte donné.|
|<xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>|Élément <xref:Microsoft.VisualStudio.Text.ITextBuffer>.|
|<xref:Microsoft.VisualStudio.Text.ITextDocumentFactoryService>|Élément <xref:Microsoft.VisualStudio.Text.ITextDocument>.|
|<xref:Microsoft.VisualStudio.Text.Differencing.IDifferenceService>|<xref:Microsoft.VisualStudio.Text.Differencing.IDifferenceCollection%601>De différences.|
|<xref:Microsoft.VisualStudio.Text.Differencing.IHierarchicalStringDifferenceService>|<xref:Microsoft.VisualStudio.Text.Differencing.IHierarchicalDifferenceCollection>De différences.|
|<xref:Microsoft.VisualStudio.Text.Projection.IProjectionBufferFactoryService>|<xref:Microsoft.VisualStudio.Text.Projection.IProjectionBuffer>Ou <xref:Microsoft.VisualStudio.Text.Projection.IElisionBuffer> .|
|<xref:Microsoft.VisualStudio.Text.Projection.IBufferGraphFactoryService>|<xref:Microsoft.VisualStudio.Text.Projection.IBufferGraph>Pour un ensemble d' <xref:Microsoft.VisualStudio.Text.ITextBuffer> objets.|
|<xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService>|<xref:Microsoft.VisualStudio.Text.Classification.IClassifier>Pour un <xref:Microsoft.VisualStudio.Text.ITextBuffer> .|
|<xref:Microsoft.VisualStudio.Text.Classification.IViewClassifierAggregatorService>|<xref:Microsoft.VisualStudio.Text.Classification.IClassifier>Pour un <xref:Microsoft.VisualStudio.Text.Editor.ITextView> .|
|<xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMapService>|<xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMap>Pour un <xref:Microsoft.VisualStudio.Text.Editor.ITextView> .|
|<xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>|<xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap>Pour un <xref:Microsoft.VisualStudio.Text.Editor.ITextView> .|
|<xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService>|Gère la collection d' <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType> objets.|
|<xref:Microsoft.VisualStudio.Text.Tagging.IBufferTagAggregatorFactoryService>|<xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601>Pour une mémoire tampon de texte.|
|<xref:Microsoft.VisualStudio.Text.Tagging.IViewTagAggregatorFactoryService>|<xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601>Pour un affichage de texte.|
|<xref:Microsoft.VisualStudio.Text.Editor.IEditorOptionsFactoryService>|<xref:Microsoft.VisualStudio.Text.Editor.IEditorOptions>Pour la portée spécifiée.|
|<xref:Microsoft.VisualStudio.Text.Editor.IScrollMapFactoryService>|<xref:Microsoft.VisualStudio.Text.Editor.IScrollMap>Pour un affichage de texte.|
|<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentationService>|<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndent>Pour un <xref:Microsoft.VisualStudio.Text.Editor.ITextView> .|
|<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentationService>|Obtient la mise en retrait automatique via les <xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentProvider> objets.|
|<xref:Microsoft.VisualStudio.Text.Editor.ITextEditorFactoryService>|Gère le <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> pour un <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView> .|
|<xref:Microsoft.VisualStudio.Text.Formatting.IFormattedTextSourceFactoryService>|Élément <xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource>.|
|<xref:Microsoft.VisualStudio.Text.Formatting.IRtfBuilderService>|Génère du texte au format RTF à partir d’un ensemble d’étendues d’instantanés.|
|<xref:Microsoft.VisualStudio.Text.Formatting.ITextAndAdornmentSequencerFactoryService>|<xref:Microsoft.VisualStudio.Text.Formatting.ITextAndAdornmentSequencer>Pour un <xref:Microsoft.VisualStudio.Text.Editor.ITextView> .|
|<xref:Microsoft.VisualStudio.Text.Formatting.ITextParagraphPropertiesFactoryService>|<xref:System.Windows.Media.TextFormatting.TextParagraphProperties>Pour mettre en forme des lignes de texte dans une vue.|
|<xref:Microsoft.VisualStudio.Text.Operations.IEditorOperationsFactoryService>|<xref:Microsoft.VisualStudio.Text.Operations.IEditorOperations>Objet pour <xref:Microsoft.VisualStudio.Text.Editor.ITextView> .|
|<xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService>|Recherche un instantané de texte.|
|<xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>|<xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator>Pour un <xref:Microsoft.VisualStudio.Text.ITextBuffer> par <xref:Microsoft.VisualStudio.Utilities.IContentType> .|
|<xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManagerService>|<xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManager>Pour un affichage de texte.|
|<xref:Microsoft.VisualStudio.Language.Intellisense.IGlyphService>|Ensemble standard de glyphes.|
|<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSessionStackMapService>|<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSessionStack>Pour un <xref:Microsoft.VisualStudio.Text.Editor.ITextView> .|
|<xref:Microsoft.VisualStudio.Language.Intellisense.IWpfKeyboardTrackingService>|Effectue le suivi de la gestion du clavier.|
|<xref:Microsoft.VisualStudio.Language.StandardClassification.IStandardClassificationService>|<xref:Microsoft.VisualStudio.Text.Classification.IClassificationType>Objets standard.|
|<xref:Microsoft.VisualStudio.Text.Operations.ITextUndoHistoryRegistry>|Maintient la relation entre les mémoires tampons de texte et les  <xref:Microsoft.VisualStudio.Text.Operations.ITextUndoHistory> objets.|

## <a name="other-imports"></a>Autres importations
 Les fabriques de fournisseurs et les courtiers sont généralement des entités qui peuvent avoir plusieurs instances dans plusieurs composants.

|Importer|offre les services|
|------------|--------------|
|<xref:Microsoft.VisualStudio.Text.Adornments.IErrorProviderFactory>|<xref:Microsoft.VisualStudio.Text.Tagging.SimpleTagger%601>De type <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag> ) pour la mémoire tampon donnée.|
|<xref:Microsoft.VisualStudio.Text.Adornments.ITextMarkerProviderFactory>|Balise de marqueur de texte ( <xref:Microsoft.VisualStudio.Text.Tagging.SimpleTagger%601> de type <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> ).|
|<xref:Microsoft.VisualStudio.Text.Adornments.IToolTipProviderFactory>|<xref:Microsoft.VisualStudio.Text.Adornments.IToolTipProvider>Pour un donné <xref:Microsoft.VisualStudio.Text.Editor.ITextView> .|
|<xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>|Élément <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSession>.|
|<xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker>|Élément <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSession>.|
|<xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker>|Élément <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSession>.|

## <a name="see-also"></a>Voir aussi
- [Points d’extension du service de langage et de l’éditeur](../extensibility/language-service-and-editor-extension-points.md)
