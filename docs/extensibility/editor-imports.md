---
title: "Importations d’éditeur | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - services
ms.assetid: 8d096de3-33b4-427a-a122-4aeff8a72da0
caps.latest.revision: 19
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
ms.openlocfilehash: 2c7daddb7cd40dd0e5d24f01df141ce30ba713f9
ms.lasthandoff: 02/22/2017

---
# <a name="editor-imports"></a>Importations d’éditeur
Vous pouvez importer un nombre de services de l’éditeur, les fabriques et les courtiers et fournissent votre extension avec différents types d’accès à l’éditeur principal. Par exemple, vous pouvez importer le <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>vous fournir un <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator>pour un type de contenu donné.</xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator> </xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> (Ce navigateur permet de que procéder à différents types de recherche sur une mémoire tampon de texte.)  
  
 Pour utiliser une importation de l’éditeur, importez-le comme un champ ou une propriété d’une classe qui exporte un composant Managed Extensibility Framework.  
  
> [!NOTE]
>  Pour plus d’informations sur le Managed Extensibility Framework, consultez [Managed Extensibility Framework (MEF)](http://msdn.microsoft.com/Library/6c61b4ec-c6df-4651-80f1-4854f8b14dde).  
  
## <a name="import-syntax"></a>Syntaxe de l’importation  
 L’exemple suivant montre comment importer l’éditeur de service de fabrique d’options.  
  
```  
[Import]  
internal IEditorOptionsFactoryService EditorOptions { get; set; }  
```  
  
 Si vous souhaitez importer le service comme un champ et non pas une propriété, vous devez le définir `null` dans la déclaration afin d’éviter les avertissements du compilateur sur ne pas attribuer à une variable :  
  
```  
[Import]  
internal IEditorOptionsFactoryService m_editorOptions = null;  
```  
  
 Pour plus d’exemples d’utilisation d’importations, consultez les procédures suivantes :  
  
 [Procédure pas à pas : Création d’un glyphe de marge](../extensibility/walkthrough-creating-a-margin-glyph.md)  
  
 [Procédure pas à pas : Personnalisation de l’affichage de texte](../extensibility/walkthrough-customizing-the-text-view.md)  
  
 [Procédure pas à pas : Mise en surbrillance de texte](../extensibility/walkthrough-highlighting-text.md)  
  
 [Procédure pas à pas : Affichage des info-bulles Info express](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)  
  
 [Procédure pas à pas : Affichage de l’aide de Signature](../extensibility/walkthrough-displaying-signature-help.md)  
  
 [Procédure pas à pas : affichage de la saisie semi-automatique des instructions](../extensibility/walkthrough-displaying-statement-completion.md)  
  
 [Procédure pas à pas : affichage de SmartTags](../misc/walkthrough-displaying-smarttags.md)  
  
## <a name="importing-the-service-provider"></a>L’importation du fournisseur de services  
 Vous pouvez également importer un <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>(trouvée dans l’assembly Microsoft.VisualStudio.Shell.Immutable.10.0) de la même manière pour accéder aux services de Visual Studio :</xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>  
  
```  
[Import]  
internal SVsServiceProvider ServiceProvider = null;   
```  
  
 Consultez la page [procédure pas à pas : accès à l’objet DTE à partir d’une Extension de l’éditeur](../extensibility/walkthrough-accessing-the-dte-object-from-an-editor-extension.md) pour plus d’informations.  
  
## <a name="services"></a>Services  
 Éditeur services sont des entités uniques en général qui fournissent un service et sont partagées entre plusieurs composants.  
  
|Import|Fournit des|  
|------------|--------------|  
|<xref:Microsoft.VisualStudio.Utilities.IFileExtensionRegistryService></xref:Microsoft.VisualStudio.Utilities.IFileExtensionRegistryService>|La relation entre les extensions de fichier et <xref:Microsoft.VisualStudio.Utilities.IContentType>objets.</xref:Microsoft.VisualStudio.Utilities.IContentType>|  
|<xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService></xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService>|La collection de <xref:Microsoft.VisualStudio.Utilities.IContentType>objets.</xref:Microsoft.VisualStudio.Utilities.IContentType>|  
|<xref:Microsoft.VisualStudio.Editor.IVsFontsAndColorsInformationService></xref:Microsoft.VisualStudio.Editor.IVsFontsAndColorsInformationService>|<xref:Microsoft.VisualStudio.Editor.IVsFontsAndColorsInformation>objets</xref:Microsoft.VisualStudio.Editor.IVsFontsAndColorsInformation>|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService></xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>|Plusieurs objets de carte de l’éditeur :<br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow></xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|  
|<xref:Microsoft.VisualStudio.Text.IncrementalSearch.IIncrementalSearchFactoryService></xref:Microsoft.VisualStudio.Text.IncrementalSearch.IIncrementalSearchFactoryService>|Un <xref:Microsoft.VisualStudio.Text.IncrementalSearch.IIncrementalSearch>objet pour un affichage de texte donné.</xref:Microsoft.VisualStudio.Text.IncrementalSearch.IIncrementalSearch>|  
|<xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService></xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>|An <xref:Microsoft.VisualStudio.Text.ITextBuffer>.</xref:Microsoft.VisualStudio.Text.ITextBuffer>|  
|<xref:Microsoft.VisualStudio.Text.ITextDocumentFactoryService></xref:Microsoft.VisualStudio.Text.ITextDocumentFactoryService>|An <xref:Microsoft.VisualStudio.Text.ITextDocument>.</xref:Microsoft.VisualStudio.Text.ITextDocument>|  
|<xref:Microsoft.VisualStudio.Text.Differencing.IDifferenceService></xref:Microsoft.VisualStudio.Text.Differencing.IDifferenceService>|Un <xref:Microsoft.VisualStudio.Text.Differencing.IDifferenceCollection%601>des différences.</xref:Microsoft.VisualStudio.Text.Differencing.IDifferenceCollection%601>|  
|<xref:Microsoft.VisualStudio.Text.Differencing.IHierarchicalStringDifferenceService></xref:Microsoft.VisualStudio.Text.Differencing.IHierarchicalStringDifferenceService>|Un <xref:Microsoft.VisualStudio.Text.Differencing.IHierarchicalDifferenceCollection>des différences.</xref:Microsoft.VisualStudio.Text.Differencing.IHierarchicalDifferenceCollection>|  
|<xref:Microsoft.VisualStudio.Text.Projection.IProjectionBufferFactoryService></xref:Microsoft.VisualStudio.Text.Projection.IProjectionBufferFactoryService>|Un <xref:Microsoft.VisualStudio.Text.Projection.IProjectionBuffer>ou un <xref:Microsoft.VisualStudio.Text.Projection.IElisionBuffer>.</xref:Microsoft.VisualStudio.Text.Projection.IElisionBuffer> </xref:Microsoft.VisualStudio.Text.Projection.IProjectionBuffer>|  
|<xref:Microsoft.VisualStudio.Text.Projection.IBufferGraphFactoryService></xref:Microsoft.VisualStudio.Text.Projection.IBufferGraphFactoryService>|Un <xref:Microsoft.VisualStudio.Text.Projection.IBufferGraph>pour un ensemble de <xref:Microsoft.VisualStudio.Text.ITextBuffer>objets.</xref:Microsoft.VisualStudio.Text.ITextBuffer> </xref:Microsoft.VisualStudio.Text.Projection.IBufferGraph>|  
|<xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService></xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService>|Un <xref:Microsoft.VisualStudio.Text.Classification.IClassifier>pour un <xref:Microsoft.VisualStudio.Text.ITextBuffer>.</xref:Microsoft.VisualStudio.Text.ITextBuffer> </xref:Microsoft.VisualStudio.Text.Classification.IClassifier>|  
|<xref:Microsoft.VisualStudio.Text.Classification.IViewClassifierAggregatorService></xref:Microsoft.VisualStudio.Text.Classification.IViewClassifierAggregatorService>|Un <xref:Microsoft.VisualStudio.Text.Classification.IClassifier>pour un <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.</xref:Microsoft.VisualStudio.Text.Editor.ITextView> </xref:Microsoft.VisualStudio.Text.Classification.IClassifier>|  
|<xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMapService></xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMapService>|Un <xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMap>pour un <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.</xref:Microsoft.VisualStudio.Text.Editor.ITextView> </xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMap>|  
|<xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService></xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>|Un <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap>pour un <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.</xref:Microsoft.VisualStudio.Text.Editor.ITextView> </xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap>|  
|<xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService></xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService>|Gère la collection de <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType>objets.</xref:Microsoft.VisualStudio.Text.Classification.IClassificationType>|  
|<xref:Microsoft.VisualStudio.Text.Tagging.IBufferTagAggregatorFactoryService></xref:Microsoft.VisualStudio.Text.Tagging.IBufferTagAggregatorFactoryService>|Un <xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601>pour une mémoire tampon de texte.</xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601>|  
|<xref:Microsoft.VisualStudio.Text.Tagging.IViewTagAggregatorFactoryService></xref:Microsoft.VisualStudio.Text.Tagging.IViewTagAggregatorFactoryService>|Un <xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601>pour une vue de texte.</xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601>|  
|<xref:Microsoft.VisualStudio.Text.Editor.IEditorOptionsFactoryService></xref:Microsoft.VisualStudio.Text.Editor.IEditorOptionsFactoryService>|Le <xref:Microsoft.VisualStudio.Text.Editor.IEditorOptions>pour l’étendue spécifiée.</xref:Microsoft.VisualStudio.Text.Editor.IEditorOptions>|  
|<xref:Microsoft.VisualStudio.Text.Editor.IScrollMapFactoryService></xref:Microsoft.VisualStudio.Text.Editor.IScrollMapFactoryService>|Un <xref:Microsoft.VisualStudio.Text.Editor.IScrollMap>pour une vue de texte.</xref:Microsoft.VisualStudio.Text.Editor.IScrollMap>|  
|<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentationService></xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentationService>|Un <xref:Microsoft.VisualStudio.Text.Editor.ISmartIndent>pour un <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.</xref:Microsoft.VisualStudio.Text.Editor.ITextView> </xref:Microsoft.VisualStudio.Text.Editor.ISmartIndent>|  
|<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentationService></xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentationService>|Obtient la mise en retrait automatique la <xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentProvider>objets.</xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentProvider>|  
|<xref:Microsoft.VisualStudio.Text.Editor.ITextEditorFactoryService></xref:Microsoft.VisualStudio.Text.Editor.ITextEditorFactoryService>|Gère la <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost>pour un <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>.</xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView> </xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost>|  
|<xref:Microsoft.VisualStudio.Text.Formatting.IFormattedTextSourceFactoryService></xref:Microsoft.VisualStudio.Text.Formatting.IFormattedTextSourceFactoryService>|An <xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource>.</xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource>|  
|<xref:Microsoft.VisualStudio.Text.Formatting.IRtfBuilderService></xref:Microsoft.VisualStudio.Text.Formatting.IRtfBuilderService>|Génère du texte au format RTF à partir d’un jeu d’étendues d’instantanés.|  
|<xref:Microsoft.VisualStudio.Text.Formatting.ITextAndAdornmentSequencerFactoryService></xref:Microsoft.VisualStudio.Text.Formatting.ITextAndAdornmentSequencerFactoryService>|Un <xref:Microsoft.VisualStudio.Text.Formatting.ITextAndAdornmentSequencer>pour un <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.</xref:Microsoft.VisualStudio.Text.Editor.ITextView> </xref:Microsoft.VisualStudio.Text.Formatting.ITextAndAdornmentSequencer>|  
|<xref:Microsoft.VisualStudio.Text.Formatting.ITextParagraphPropertiesFactoryService></xref:Microsoft.VisualStudio.Text.Formatting.ITextParagraphPropertiesFactoryService>|Un <xref:System.Windows.Media.TextFormatting.TextParagraphProperties>pour mettre en forme des lignes de texte dans une vue.</xref:System.Windows.Media.TextFormatting.TextParagraphProperties>|  
|<xref:Microsoft.VisualStudio.Text.Operations.IEditorOperationsFactoryService></xref:Microsoft.VisualStudio.Text.Operations.IEditorOperationsFactoryService>|Un <xref:Microsoft.VisualStudio.Text.Operations.IEditorOperations>objet pour un <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.</xref:Microsoft.VisualStudio.Text.Editor.ITextView> </xref:Microsoft.VisualStudio.Text.Operations.IEditorOperations>|  
|<xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService></xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService>|Recherche un instantané de texte.|  
|<xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService></xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>|Un <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator>pour une <xref:Microsoft.VisualStudio.Text.ITextBuffer>par <xref:Microsoft.VisualStudio.Utilities.IContentType>.</xref:Microsoft.VisualStudio.Utilities.IContentType> </xref:Microsoft.VisualStudio.Text.ITextBuffer> </xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator>|  
|<xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManagerService></xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManagerService>|Un <xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManager>pour une vue de texte.</xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManager>|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.IGlyphService></xref:Microsoft.VisualStudio.Language.Intellisense.IGlyphService>|Un jeu standard de glyphes.|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSessionStackMapService></xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSessionStackMapService>|Un <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSessionStack>pour un <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.</xref:Microsoft.VisualStudio.Text.Editor.ITextView> </xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSessionStack>|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.IWpfKeyboardTrackingService></xref:Microsoft.VisualStudio.Language.Intellisense.IWpfKeyboardTrackingService>|Assure le suivi du clavier gestion.|  
|<xref:Microsoft.VisualStudio.Language.StandardClassification.IStandardClassificationService></xref:Microsoft.VisualStudio.Language.StandardClassification.IStandardClassificationService>|Standard <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType>objets.</xref:Microsoft.VisualStudio.Text.Classification.IClassificationType>|  
|<xref:Microsoft.VisualStudio.Text.Operations.ITextUndoHistoryRegistry></xref:Microsoft.VisualStudio.Text.Operations.ITextUndoHistoryRegistry>|Conserve la relation entre les mémoires tampons de texte et <xref:Microsoft.VisualStudio.Text.Operations.ITextUndoHistory>objets.</xref:Microsoft.VisualStudio.Text.Operations.ITextUndoHistory>|  
  
## <a name="other-imports"></a>Autres importations  
 Courtiers et les fabriques de fournisseur sont généralement des entités qui peuvent avoir plusieurs instances dans plusieurs composants.  
  
|Import|Fournit des|  
|------------|--------------|  
|<xref:Microsoft.VisualStudio.Text.Adornments.IErrorProviderFactory></xref:Microsoft.VisualStudio.Text.Adornments.IErrorProviderFactory>|Un <xref:Microsoft.VisualStudio.Text.Tagging.SimpleTagger%601>de type <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>) pour la mémoire tampon donnée.</xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag> </xref:Microsoft.VisualStudio.Text.Tagging.SimpleTagger%601>|  
|<xref:Microsoft.VisualStudio.Text.Adornments.ITextMarkerProviderFactory></xref:Microsoft.VisualStudio.Text.Adornments.ITextMarkerProviderFactory>|Une balise de marqueur de texte (un <xref:Microsoft.VisualStudio.Text.Tagging.SimpleTagger%601>de type <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>).</xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> </xref:Microsoft.VisualStudio.Text.Tagging.SimpleTagger%601>|  
|<xref:Microsoft.VisualStudio.Text.Adornments.IToolTipProviderFactory></xref:Microsoft.VisualStudio.Text.Adornments.IToolTipProviderFactory>|Un <xref:Microsoft.VisualStudio.Text.Adornments.IToolTipProvider>pour une donnée <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.</xref:Microsoft.VisualStudio.Text.Editor.ITextView> </xref:Microsoft.VisualStudio.Text.Adornments.IToolTipProvider>|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker></xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>|An <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSession>.</xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSession>|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker></xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker>|An <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSession>.</xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSession>|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker></xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker>|An <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSession>.</xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSession>|  
  
## <a name="see-also"></a>Voir aussi  
 [Service de langage et les Points d’Extension Éditeur](../extensibility/language-service-and-editor-extension-points.md)
