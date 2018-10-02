---
title: Importations de l’éditeur | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - services
ms.assetid: 8d096de3-33b4-427a-a122-4aeff8a72da0
caps.latest.revision: 20
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7017d4a99bbfd58a854ba1cd33230f11928024cc
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47508353"
---
# <a name="editor-imports"></a>Importations de l’éditeur
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [importations de l’éditeur](https://docs.microsoft.com/visualstudio/extensibility/editor-imports).  
  
Vous pouvez importer un nombre de services de l’éditeur, les fabriques et les courtiers et fournissent votre extension avec différents types d’accès à l’éditeur principal. Par exemple, vous pouvez importer le <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> pour vous donner un <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator> pour un type de contenu donné. (Ce navigateur permet de qu'effectuer de différents types de recherche sur une mémoire tampon de texte.)  
  
 Pour utiliser une importation de l’éditeur, importez-le en tant que champ ou propriété d’une classe qui exporte une partie du composant Managed Extensibility Framework.  
  
> [!NOTE]
>  Pour plus d’informations sur Managed Extensibility Framework, consultez [Managed Extensibility Framework (MEF)](http://msdn.microsoft.com/library/6c61b4ec-c6df-4651-80f1-4854f8b14dde).  
  
## <a name="import-syntax"></a>Syntaxe de l’importation  
 L’exemple suivant montre comment importer l’éditeur de service de fabrique d’options.  
  
```  
[Import]  
internal IEditorOptionsFactoryService EditorOptions { get; set; }  
```  
  
 Si vous souhaitez importer le service comme un champ et pas une propriété, vous devez la définir sur `null` dans la déclaration afin d’éviter les avertissements du compilateur sur ne pas attribuer à une variable :  
  
```  
[Import]  
internal IEditorOptionsFactoryService m_editorOptions = null;  
```  
  
 Pour plus d’exemples d’utilisation des importations, consultez les procédures suivantes :  
  
 [Procédure pas à pas : Création d’un glyphe de marge](../extensibility/walkthrough-creating-a-margin-glyph.md)  
  
 [Procédure pas à pas : Personnalisation de l’affichage du texte](../extensibility/walkthrough-customizing-the-text-view.md)  
  
 [Procédure pas à pas : Mise en surbrillance de texte](../extensibility/walkthrough-highlighting-text.md)  
  
 [Procédure pas à pas : Affichage d’info-bulles Info express](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)  
  
 [Procédure pas à pas : Affichage d’aide sur les signatures](../extensibility/walkthrough-displaying-signature-help.md)  
  
 [Procédure pas à pas : affichage de la saisie semi-automatique des instructions](../extensibility/walkthrough-displaying-statement-completion.md)  
  
 [Procédure pas à pas : affichage de SmartTags](../misc/walkthrough-displaying-smarttags.md)  
  
## <a name="importing-the-service-provider"></a>Importez le fournisseur de services  
 Vous pouvez également importer un <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> (trouvée dans l’assembly Microsoft.VisualStudio.Shell.Immutable.10.0) de la même façon pour accéder aux services de Visual Studio :  
  
```  
[Import]  
internal SVsServiceProvider ServiceProvider = null;   
```  
  
 Consultez [procédure pas à pas : accès à l’objet DTE à partir d’une Extension de l’éditeur](../extensibility/walkthrough-accessing-the-dte-object-from-an-editor-extension.md) pour plus d’informations.  
  
## <a name="services"></a>Services  
 Services de l’éditeur sont des entités uniques en général qui fournissent un service et sont partagées entre plusieurs composants.  
  
|Import|Fournit|  
|------------|--------------|  
|<xref:Microsoft.VisualStudio.Utilities.IFileExtensionRegistryService>|La relation entre les extensions de fichier et <xref:Microsoft.VisualStudio.Utilities.IContentType> objets.|  
|<xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService>|Collection d'objets <xref:Microsoft.VisualStudio.Utilities.IContentType>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsFontsAndColorsInformationService>|Objets <xref:Microsoft.VisualStudio.Editor.IVsFontsAndColorsInformation>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>|Plusieurs objets de carte de l’éditeur :<br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|  
|<xref:Microsoft.VisualStudio.Text.IncrementalSearch.IIncrementalSearchFactoryService>|Un <xref:Microsoft.VisualStudio.Text.IncrementalSearch.IIncrementalSearch> objet pour un affichage de texte donné.|  
|<xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>|Élément <xref:Microsoft.VisualStudio.Text.ITextBuffer>.|  
|<xref:Microsoft.VisualStudio.Text.ITextDocumentFactoryService>|Élément <xref:Microsoft.VisualStudio.Text.ITextDocument>.|  
|<xref:Microsoft.VisualStudio.Text.Differencing.IDifferenceService>|Un <xref:Microsoft.VisualStudio.Text.Differencing.IDifferenceCollection%601> des différences.|  
|<xref:Microsoft.VisualStudio.Text.Differencing.IHierarchicalStringDifferenceService>|Un <xref:Microsoft.VisualStudio.Text.Differencing.IHierarchicalDifferenceCollection> des différences.|  
|<xref:Microsoft.VisualStudio.Text.Projection.IProjectionBufferFactoryService>|Un <xref:Microsoft.VisualStudio.Text.Projection.IProjectionBuffer> ou un <xref:Microsoft.VisualStudio.Text.Projection.IElisionBuffer>.|  
|<xref:Microsoft.VisualStudio.Text.Projection.IBufferGraphFactoryService>|Un <xref:Microsoft.VisualStudio.Text.Projection.IBufferGraph> pour un ensemble de <xref:Microsoft.VisualStudio.Text.ITextBuffer> objets.|  
|<xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService>|Un <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> pour un <xref:Microsoft.VisualStudio.Text.ITextBuffer>.|  
|<xref:Microsoft.VisualStudio.Text.Classification.IViewClassifierAggregatorService>|Un <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> pour un <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.|  
|<xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMapService>|Un <xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMap> pour un <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.|  
|<xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>|Un <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap> pour un <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.|  
|<xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService>|Gère la collection de <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType> objets.|  
|<xref:Microsoft.VisualStudio.Text.Tagging.IBufferTagAggregatorFactoryService>|Un <xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601> une mémoire tampon de texte.|  
|<xref:Microsoft.VisualStudio.Text.Tagging.IViewTagAggregatorFactoryService>|Un <xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601> pour un affichage de texte.|  
|<xref:Microsoft.VisualStudio.Text.Editor.IEditorOptionsFactoryService>|Le <xref:Microsoft.VisualStudio.Text.Editor.IEditorOptions> pour l’étendue spécifiée.|  
|<xref:Microsoft.VisualStudio.Text.Editor.IScrollMapFactoryService>|Un <xref:Microsoft.VisualStudio.Text.Editor.IScrollMap> pour un affichage de texte.|  
|<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentationService>|Un <xref:Microsoft.VisualStudio.Text.Editor.ISmartIndent> pour un <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.|  
|<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentationService>|Obtient la mise en retrait automatique le <xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentProvider> objets.|  
|<xref:Microsoft.VisualStudio.Text.Editor.ITextEditorFactoryService>|Gère la <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> pour un <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>.|  
|<xref:Microsoft.VisualStudio.Text.Formatting.IFormattedTextSourceFactoryService>|Élément <xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource>.|  
|<xref:Microsoft.VisualStudio.Text.Formatting.IRtfBuilderService>|Génère du texte au format RTF à partir d’un jeu d’étendues d’instantanés.|  
|<xref:Microsoft.VisualStudio.Text.Formatting.ITextAndAdornmentSequencerFactoryService>|Un <xref:Microsoft.VisualStudio.Text.Formatting.ITextAndAdornmentSequencer> pour un <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.|  
|<xref:Microsoft.VisualStudio.Text.Formatting.ITextParagraphPropertiesFactoryService>|Un <xref:System.Windows.Media.TextFormatting.TextParagraphProperties> pour mettre en forme des lignes de texte dans une vue.|  
|<xref:Microsoft.VisualStudio.Text.Operations.IEditorOperationsFactoryService>|Un <xref:Microsoft.VisualStudio.Text.Operations.IEditorOperations> de l’objet pour un <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.|  
|<xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService>|Recherche un instantané de texte.|  
|<xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>|Un <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator> pour un <xref:Microsoft.VisualStudio.Text.ITextBuffer> par <xref:Microsoft.VisualStudio.Utilities.IContentType>.|  
|<xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManagerService>|Un <xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManager> pour un affichage de texte.|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.IGlyphService>|Un jeu standard de glyphes.|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSessionStackMapService>|Un <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSessionStack> pour un <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.IWpfKeyboardTrackingService>|Effectue le suivi du clavier gestion.|  
|<xref:Microsoft.VisualStudio.Language.StandardClassification.IStandardClassificationService>|Standard <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType> objets.|  
|<xref:Microsoft.VisualStudio.Text.Operations.ITextUndoHistoryRegistry>|Maintient la relation entre les mémoires tampons de texte et <xref:Microsoft.VisualStudio.Text.Operations.ITextUndoHistory> objets.|  
  
## <a name="other-imports"></a>Autres importations  
 Courtiers et les fabriques de fournisseur sont généralement des entités qui peuvent avoir plusieurs instances dans plusieurs composants.  
  
|Import|Fournit|  
|------------|--------------|  
|<xref:Microsoft.VisualStudio.Text.Adornments.IErrorProviderFactory>|Un <xref:Microsoft.VisualStudio.Text.Tagging.SimpleTagger%601> de type <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>) pour la mémoire tampon donnée.|  
|<xref:Microsoft.VisualStudio.Text.Adornments.ITextMarkerProviderFactory>|Une balise de marqueur de texte (un <xref:Microsoft.VisualStudio.Text.Tagging.SimpleTagger%601> de type <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>).|  
|<xref:Microsoft.VisualStudio.Text.Adornments.IToolTipProviderFactory>|Un <xref:Microsoft.VisualStudio.Text.Adornments.IToolTipProvider> pour une donnée <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>|Élément <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSession>.|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker>|Élément <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSession>.|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker>|Élément <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSession>.|  
  
## <a name="see-also"></a>Voir aussi  
 [Points d’extension du service de langage et de l’éditeur](../extensibility/language-service-and-editor-extension-points.md)

