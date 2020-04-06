---
title: Importations de rédacteurs en chef (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - services
ms.assetid: 8d096de3-33b4-427a-a122-4aeff8a72da0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c6af95b452166aa71950ac1e869d333d12d857b9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712012"
---
# <a name="editor-imports"></a>Importations de rédacteurs
Vous pouvez importer un certain nombre de services d’éditeur, d’usines et de courtiers qui fournissent à votre extension différents types d’accès à l’éditeur de base. Par exemple, vous <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> pouvez importer le <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator> pour vous fournir un pour un type de contenu donné. (Ce navigateur vous permet d’effectuer différents types de recherches sur un tampon texte.)

 Pour utiliser une importation d’éditeur, vous l’importez comme un champ ou une propriété d’une classe qui exporte une partie de la composante Cadre d’Extégabilité gérée.

> [!NOTE]
> Pour plus d’informations sur le Cadre d’exténuabilité gérée, voir [Cadre d’exténuabilité gérée (MEF)](/dotnet/framework/mef/index).

## <a name="import-syntax"></a>Syntaxe d’importation
 L’exemple suivant montre comment importer le service d’usine d’options d’éditeur.

```
[Import]
internal IEditorOptionsFactoryService EditorOptions { get; set; }
```

 Si vous souhaitez importer le service comme un champ et `null` non comme une propriété, vous devez le définir dans la déclaration afin d’éviter les avertissements de compilateur de ne pas attribuer à une variable:

```
[Import]
internal IEditorOptionsFactoryService m_editorOptions = null;
```

 Pour plus d’exemples d’utilisation des importations, voir les procédures pas à pas suivantes:

- [Procédure pas à pas: Créer un glyphe de marge](../extensibility/walkthrough-creating-a-margin-glyph.md)

- [Procédure pas à pas : Personnalisez la vue du texte](../extensibility/walkthrough-customizing-the-text-view.md)

- [Procédure pas à pas : Mettre en évidence le texte](../extensibility/walkthrough-highlighting-text.md)

- [Procédure pas à pas: Afficher des outils QuickInfo](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)

- [Procédure pas à pas : Offrez l’aide signature d’affichage](../extensibility/walkthrough-displaying-signature-help.md)

- [Procédure pas à pas : afficher la saisie semi-automatique des instructions](../extensibility/walkthrough-displaying-statement-completion.md)

- [Procédure pas à pas : Afficher les suggestions d’ampoules](../extensibility/walkthrough-displaying-light-bulb-suggestions.md)

## <a name="import-the-service-provider"></a>Importer le fournisseur de services
 Vous pouvez également <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> importer un (trouvé dans l’assemblage Microsoft.VisualStudio.Shell.Immutable.10.0) de la même manière pour accéder aux services Visual Studio:

```csharp
[Import]
internal SVsServiceProvider ServiceProvider = null;
```

 Voir [Procédure pas à pas : Accédez à l’objet DTE à partir d’une extension de l’éditeur](../extensibility/walkthrough-accessing-the-dte-object-from-an-editor-extension.md) pour plus d’informations.

## <a name="services"></a>Services
 Les services d’éditeur sont généralement des entités uniques qui fournissent un service et sont partagées entre plusieurs composantes.

|Importer|offre les services|
|------------|--------------|
|<xref:Microsoft.VisualStudio.Utilities.IFileExtensionRegistryService>|La relation entre les <xref:Microsoft.VisualStudio.Utilities.IContentType> extensions de fichiers et les objets.|
|<xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService>|Collection d'objets <xref:Microsoft.VisualStudio.Utilities.IContentType>.|
|<xref:Microsoft.VisualStudio.Editor.IVsFontsAndColorsInformationService>|<xref:Microsoft.VisualStudio.Editor.IVsFontsAndColorsInformation>Objets.|
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>|Beaucoup d’objets adaptateurs d’éditeur :<br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|
|<xref:Microsoft.VisualStudio.Text.IncrementalSearch.IIncrementalSearchFactoryService>|Objet <xref:Microsoft.VisualStudio.Text.IncrementalSearch.IIncrementalSearch> pour une vue textuelle donnée.|
|<xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>|<xref:Microsoft.VisualStudio.Text.ITextBuffer>.|
|<xref:Microsoft.VisualStudio.Text.ITextDocumentFactoryService>|<xref:Microsoft.VisualStudio.Text.ITextDocument>.|
|<xref:Microsoft.VisualStudio.Text.Differencing.IDifferenceService>|Une <xref:Microsoft.VisualStudio.Text.Differencing.IDifferenceCollection%601> des différences.|
|<xref:Microsoft.VisualStudio.Text.Differencing.IHierarchicalStringDifferenceService>|Une <xref:Microsoft.VisualStudio.Text.Differencing.IHierarchicalDifferenceCollection> des différences.|
|<xref:Microsoft.VisualStudio.Text.Projection.IProjectionBufferFactoryService>|Un <xref:Microsoft.VisualStudio.Text.Projection.IProjectionBuffer> ou <xref:Microsoft.VisualStudio.Text.Projection.IElisionBuffer>un .|
|<xref:Microsoft.VisualStudio.Text.Projection.IBufferGraphFactoryService>|Un <xref:Microsoft.VisualStudio.Text.Projection.IBufferGraph> pour un <xref:Microsoft.VisualStudio.Text.ITextBuffer> ensemble d’objets.|
|<xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService>|Un <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> pour <xref:Microsoft.VisualStudio.Text.ITextBuffer>un .|
|<xref:Microsoft.VisualStudio.Text.Classification.IViewClassifierAggregatorService>|Un <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> pour <xref:Microsoft.VisualStudio.Text.Editor.ITextView>un .|
|<xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMapService>|Un <xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMap> pour <xref:Microsoft.VisualStudio.Text.Editor.ITextView>un .|
|<xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>|Un <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap> pour <xref:Microsoft.VisualStudio.Text.Editor.ITextView>un .|
|<xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService>|Maintient la collection <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType> d’objets.|
|<xref:Microsoft.VisualStudio.Text.Tagging.IBufferTagAggregatorFactoryService>|Un <xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601> tampon de texte.|
|<xref:Microsoft.VisualStudio.Text.Tagging.IViewTagAggregatorFactoryService>|Une <xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601> vue de texte.|
|<xref:Microsoft.VisualStudio.Text.Editor.IEditorOptionsFactoryService>|Le <xref:Microsoft.VisualStudio.Text.Editor.IEditorOptions> pour la portée spécifiée.|
|<xref:Microsoft.VisualStudio.Text.Editor.IScrollMapFactoryService>|Une <xref:Microsoft.VisualStudio.Text.Editor.IScrollMap> vue de texte.|
|<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentationService>|Un <xref:Microsoft.VisualStudio.Text.Editor.ISmartIndent> pour <xref:Microsoft.VisualStudio.Text.Editor.ITextView>un .|
|<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentationService>|Obtient l’indentation <xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentProvider> automatique à travers les objets.|
|<xref:Microsoft.VisualStudio.Text.Editor.ITextEditorFactoryService>|Gère <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> le <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>pour un .|
|<xref:Microsoft.VisualStudio.Text.Formatting.IFormattedTextSourceFactoryService>|<xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource>.|
|<xref:Microsoft.VisualStudio.Text.Formatting.IRtfBuilderService>|Génère du texte formaté RTF à partir d’un ensemble de travées d’instantanés.|
|<xref:Microsoft.VisualStudio.Text.Formatting.ITextAndAdornmentSequencerFactoryService>|Un <xref:Microsoft.VisualStudio.Text.Formatting.ITextAndAdornmentSequencer> pour <xref:Microsoft.VisualStudio.Text.Editor.ITextView>un .|
|<xref:Microsoft.VisualStudio.Text.Formatting.ITextParagraphPropertiesFactoryService>|A <xref:System.Windows.Media.TextFormatting.TextParagraphProperties> pour formater les lignes de texte en vue.|
|<xref:Microsoft.VisualStudio.Text.Operations.IEditorOperationsFactoryService>|Un <xref:Microsoft.VisualStudio.Text.Operations.IEditorOperations> objet <xref:Microsoft.VisualStudio.Text.Editor.ITextView>pour un .|
|<xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService>|Recherche un instantané de texte.|
|<xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>|Un <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator> pour <xref:Microsoft.VisualStudio.Text.ITextBuffer> <xref:Microsoft.VisualStudio.Utilities.IContentType>un par .|
|<xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManagerService>|Une <xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManager> vue de texte.|
|<xref:Microsoft.VisualStudio.Language.Intellisense.IGlyphService>|Un ensemble standard de glyphes.|
|<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSessionStackMapService>|Un <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSessionStack> pour <xref:Microsoft.VisualStudio.Text.Editor.ITextView>un .|
|<xref:Microsoft.VisualStudio.Language.Intellisense.IWpfKeyboardTrackingService>|Suit la manipulation du clavier.|
|<xref:Microsoft.VisualStudio.Language.StandardClassification.IStandardClassificationService>|Objets <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType> standard.|
|<xref:Microsoft.VisualStudio.Text.Operations.ITextUndoHistoryRegistry>|Maintient la relation entre les <xref:Microsoft.VisualStudio.Text.Operations.ITextUndoHistory> tampons de texte et les objets.|

## <a name="other-imports"></a>Autres importations
 Les usines et les courtiers fournisseurs sont généralement des entités qui peuvent avoir plusieurs cas dans plusieurs composants.

|Importer|offre les services|
|------------|--------------|
|<xref:Microsoft.VisualStudio.Text.Adornments.IErrorProviderFactory>|A <xref:Microsoft.VisualStudio.Text.Tagging.SimpleTagger%601> de <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>type ) pour le tampon donné.|
|<xref:Microsoft.VisualStudio.Text.Adornments.ITextMarkerProviderFactory>|Un tagger marqueur <xref:Microsoft.VisualStudio.Text.Tagging.SimpleTagger%601> de <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>texte (un type ).|
|<xref:Microsoft.VisualStudio.Text.Adornments.IToolTipProviderFactory>|Un <xref:Microsoft.VisualStudio.Text.Adornments.IToolTipProvider> pour <xref:Microsoft.VisualStudio.Text.Editor.ITextView>un donné .|
|<xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>|<xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSession>.|
|<xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker>|<xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSession>.|
|<xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker>|<xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSession>.|

## <a name="see-also"></a>Voir aussi
- [Service linguistique et points d’extension de l’éditeur](../extensibility/language-service-and-editor-extension-points.md)
