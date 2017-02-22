---
title: "Service de langage et les Points d’Extension &#201;diteur | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "éditeurs (Visual Studio SDK), nouvelles - points d’extension"
ms.assetid: 91a6417e-a6fe-4bc2-9d9f-5173c634a99b
caps.latest.revision: 33
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 33
---
# Service de langage et les Points d’Extension &#201;diteur
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L’éditeur fournit des points d’extension que vous pouvez étendre en tant que composants Managed Extensibility Framework \(MEF\), y compris la plupart des fonctionnalités de service de langage. Voici les catégories de point d’extension principal :  
  
-   Types de contenu  
  
-   Types de classification et les formats de classification  
  
-   Marges et des barres de défilement  
  
-   Étiquettes  
  
-   Ornements  
  
-   Processeurs de la souris  
  
-   Gestionnaires de déplacement  
  
-   Options  
  
-   IntelliSense  
  
## Étendre les Types de contenu  
 Types de contenu sont les définitions des types de texte géré par l’éditeur, par exemple, « texte », « code » ou « CSharp ». Vous définissez un nouveau type de contenu en déclarant une variable du type <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> et en attribuant le nouveau type de contenu à un nom unique. Pour inscrire le type de contenu dans l’éditeur, vous devez l’exporter avec les attributs suivants :  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute> est le nom du type de contenu.  
  
-   <xref:Microsoft.VisualStudio.Utilities.BaseDefinitionAttribute> est le nom du type de contenu à partir duquel ce type de contenu est dérivé. Un type de contenu peut hériter de plusieurs autres types de contenu.  
  
 Étant donné que la <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> classe est sealed, vous pouvez l’exporter avec aucun paramètre de type.  
  
 L’exemple suivant montre les attributs d’exportation sur une définition de type de contenu.  
  
```  
[Export]  
[Name("test")]  
[BaseDefinition("code")]  
[BaseDefinition("projection")]  
internal static ContentTypeDefinition TestContentTypeDefinition;  
```  
  
 Types de contenu peuvent reposer sur zéro ou plusieurs types de contenu existants. Il s’agit des types intégrés :  
  
-   N’importe laquelle : le type de contenu de base. Parent de tous les autres types de contenu.  
  
-   Texte : le type de base pour le contenu non projection. Hérite de « tout ».  
  
-   Texte brut : pour le texte de pas de code. Hérite de « texte ».  
  
-   Code : code de tous les types. Hérite de « texte ».  
  
-   Inerte : exclut le texte à partir de n’importe quel système de gestion. Texte de ce type de contenu n’aura jamais toute extension appliquée.  
  
-   Projection : pour le contenu des mémoires tampons de projection. Hérite de « tout ».  
  
-   IntelliSense : pour le contenu d’IntelliSense. Hérite de « texte ».  
  
-   Sighelp : aide pour la signature. Hérite de « intellisense ».  
  
-   Sighelp\-doc : documentation d’aide signature. Hérite de « intellisense ».  
  
 Voici certains des types de contenu qui sont définies par Visual Studio et autres langues sont hébergés dans Visual Studio :  
  
-   Basic  
  
-   C\/C\+\+  
  
-   ConsoleOutput  
  
-   CSharp  
  
-   CSS  
  
-   ENC  
  
-   FindResults  
  
-   F\#  
  
-   HTML  
  
-   JScript  
  
-   XAML  
  
-   XML  
  
 Pour découvrir la liste des types de contenu disponibles, importez le <xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService>, qui gère la collection de types de contenu de l’éditeur. Le code suivant importe ce service en tant que propriété.  
  
```  
[Import]  
internal IContentTypeRegistryService ContentTypeRegistryService { get; set; }  
```  
  
 Pour associer un type de contenu avec une extension de nom de fichier, utilisez <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition>.  
  
> [!NOTE]
>  Dans Visual Studio, les extensions de nom de fichier sont enregistrées à l’aide de la <xref:Microsoft.VisualStudio.Shell.ProvideLanguageExtensionAttribute> sur un package de service de langage. Le <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> associe un type de contenu de MEF avec une extension de nom de fichier qui a été enregistrée de cette manière.  
  
 Pour exporter l’extension de nom de fichier à la définition de type de contenu, vous devez inclure les attributs suivants :  
  
-   <xref:Microsoft.VisualStudio.Utilities.FileExtensionAttribute>: Spécifie l’extension de nom de fichier.  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: Spécifie le type de contenu.  
  
 Étant donné que la <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> classe est sealed, vous pouvez l’exporter avec aucun paramètre de type.  
  
 L’exemple suivant montre les attributs d’exportation sur une extension de nom de fichier à une définition de type de contenu.  
  
```  
[Export]  
[FileExtension(".test")]  
[ContentType("test")]  
internal static FileExtensionToContentTypeDefinition TestFileExtensionDefinition;  
```  
  
 Le <xref:Microsoft.VisualStudio.Utilities.IFileExtensionRegistryService> gère les associations entre les types de contenu et les extensions de nom de fichier.  
  
## Extension de Classification et Types de Classification des Formats  
 Vous pouvez utiliser les types de classification pour définir les types de texte pour lequel vous souhaitez fournir un traitement différent \(par exemple, la couleur du texte « mot clé » bleu et le texte « commentaire » vert\). Définissez un nouveau type de classification en déclarant une variable de type <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeDefinition> et en lui attribuant un nom unique.  
  
 Pour inscrire le type de classification avec l’éditeur, vous devez l’exporter avec les attributs suivants :  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: le nom du type de classification.  
  
-   <xref:Microsoft.VisualStudio.Utilities.BaseDefinitionAttribute>: le nom du type de classification hérite de ce type de classification. Tous les types de classification héritent de « text » et un type de classification peut hériter de plusieurs autres types de classification.  
  
 Étant donné que la <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeDefinition> classe est sealed, vous pouvez l’exporter avec aucun paramètre de type.  
  
 L’exemple suivant montre les attributs d’exportation sur une définition de type de classification.  
  
```  
[Export]  
[Name("csharp.test")]  
[BaseDefinition("test")]  
internal static ClassificationTypeDefinition CSharpTestDefinition;  
```  
  
 Le <xref:Microsoft.VisualStudio.Language.StandardClassification.IStandardClassificationService> fournit l’accès aux classifications standards. Types de classification intégrées à savoir :  
  
-   « texte »  
  
-   « langage naturel » \(dérive de « texte »\)  
  
-   « langage formel » \(dérive de « texte »\)  
  
-   « string » \(dérive de « literal »\)  
  
-   « caractère » \(dérive de « literal »\)  
  
-   « numérique » \(dérive de « literal »\)  
  
 Un ensemble de différents types d’erreur héritent de <xref:Microsoft.VisualStudio.Text.Adornments.ErrorTypeDefinition>. Elles comprennent les types d’erreur suivant :  
  
-   « Erreur de syntaxe »  
  
-   « Erreur du compilateur »  
  
-   « autre erreur »  
  
-   « avertissement »  
  
 Pour découvrir la liste des types de Classification disponibles, importez le <xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService>, qui gère la collection de types de classification de l’éditeur. Le code suivant importe ce service en tant que propriété.  
  
```  
[Import]  
internal IClassificationTypeRegistryService ClassificationTypeRegistryService { get; set; }  
```  
  
 Vous pouvez définir une définition de format de classification pour votre nouveau type de classification. Dérivez une classe de <xref:Microsoft.VisualStudio.Text.Classification.ClassificationFormatDefinition> et exportez\-le avec le type <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition>, conjointement avec les attributs suivants :  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: le nom du format.  
  
-   <xref:Microsoft.VisualStudio.Utilities.DisplayNameAttribute>: le nom complet du format.  
  
-   <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>: indique si le format s’affiche sur le **polices et couleurs** page de la **Options** boîte de dialogue.  
  
-   <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: la priorité du format. Les valeurs valides sont comprises entre <xref:Microsoft.VisualStudio.Text.Classification.Priority>.  
  
-   <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeAttribute>: nom de la classification type pour lequel ce format est mappé.  
  
 L’exemple suivant montre les attributs d’exportation d’une définition de format de classification.  
  
```  
[Export(typeof(EditorFormatDefinition))]  
[ClassificationType(ClassificationTypeNames = "test")]  
[Name("test")]  
[DisplayName("Test")]  
[UserVisible(true)]  
[Order(After = Priority.Default, Before = Priority.High)]  
internal sealed class TestFormat : ClassificationFormatDefinition  
```  
  
 Pour découvrir la liste des formats disponibles, importez le <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>, qui gère la collection des formats pour l’éditeur. Le code suivant importe ce service en tant que propriété.  
  
```  
[Import]  
internal IEditorFormatMapService FormatMapService { get; set; }  
```  
  
## Barres de défilement et d’extension  
 Marges et des barres de défilement sont les éléments de la vue principale de l’éditeur en plus de l’affichage de texte lui\-même. Vous pouvez fournir n’importe quel nombre de marges en plus les marges standard qui apparaissent autour de l’affichage de texte.  
  
 Implémentez un <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMargin> interface pour définir une marge. Vous devez également implémenter la <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMarginProvider> interface permettant de créer la marge.  
  
 Pour inscrire le fournisseur de marge avec l’éditeur, vous devez exporter le fournisseur avec les attributs suivants :  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: le nom de la marge.  
  
-   <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: l’ordre dans lequel la marge apparaît, par rapport aux autres marges.  
  
     Il s’agit des marges prédéfinies :  
  
    -   « Barre de défilement horizontale de Wpf »  
  
    -   « Barre de défilement verticale de Wpf »  
  
    -   « Marge de numéro de ligne de Wpf »  
  
     Marges horizontales qui ont un attribut de l’ordre de `After="Wpf Horizontal Scrollbar"` s’affichent sous la marge intégrée et les marges horizontales qui ont un attribut de l’ordre de `Before ="Wpf Horizontal Scrollbar"` sont affichés au\-dessus de la marge intégrée. Avec le bouton droit des marges verticales qui ont un attribut de l’ordre de `After="Wpf Vertical Scrollbar"` sont affichés à droite de la barre de défilement. À gauche des marges verticales qui ont un attribut de l’ordre de `After="Wpf Line Number Margin"` apparaissent à gauche de la marge de numéro de ligne \(si elle est visible\).  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.MarginContainerAttribute>: le type de marge \(gauche, droite, haut ou bas\).  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: le type de contenu \(par exemple, « texte » ou « code »\) pour lesquels votre marge est valide.  
  
 L’exemple suivant montre les attributs d’exportation sur un fournisseur de marge pour une marge s’affiche à droite de la marge de numéro de ligne.  
  
```  
[Export(typeof(IWpfTextViewMarginProvider))]  
[Name("TestMargin")]  
[Order(Before = "Wpf Line Number Margin")]  
[MarginContainer(PredefinedMarginNames.Left)]  
[ContentType("text")]   
```  
  
## Extension de balises  
 Les balises sont un moyen d’associer des données à différents types de texte. Dans de nombreux cas, les données associées sont affichées comme un effet visuel, mais pas toutes les balises ont une présentation visuelle. Vous pouvez définir votre propre type de balise en implémentant <xref:Microsoft.VisualStudio.Text.Tagging.ITag>. Vous devez également implémenter <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> pour fournir les balises pour un ensemble donné de plages de texte et un <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider> pour fournir la balise. Vous devez exporter le fournisseur de balise avec les attributs suivants :  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: le type de contenu \(par exemple, « texte » ou « code »\) pour lequel votre balise est valide.  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>: le type de balise.  
  
 L’exemple suivant montre les attributs d’exportation sur un fournisseur de balise.  
  
<CodeContentPlaceHolder>8</CodeContentPlaceHolder>  
 Les types de balise suivants sont prédéfinis :  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.ClassificationTag>: associé à un <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType>.  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>: associé aux types d’erreurs.  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>: associé à un ornement.  
  
    > [!NOTE]
    >  Pour obtenir un exemple d’un <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>, consultez la définition de HighlightWordTag dans [Procédure pas à pas : Mise en surbrillance de texte](../extensibility/walkthrough-highlighting-text.md).  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag>: associées aux régions qui peuvent être développées ou réduites en plan.  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>: définit l’espace occupé par un ornement dans une vue de texte. Pour plus d’informations sur les ornements négociant espace, consultez la section suivante.  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.IntraTextAdornmentTag>: fournit le dimensionnement de l’ornement et d’espacement automatique.  
  
 Pour rechercher et utiliser des balises pour les mémoires tampons et des vues, importez le <xref:Microsoft.VisualStudio.Text.Tagging.IViewTagAggregatorFactoryService> ou le <xref:Microsoft.VisualStudio.Text.Tagging.IBufferTagAggregatorFactoryService>, qui permettent un <xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601> du type demandé. Le code suivant importe ce service en tant que propriété.  
  
```  
[Import]  
internal IViewTagAggregatorFactoryService ViewTagAggregatorFactoryService { get; set; }  
```  
  
#### Balises et MarkerFormatDefinitions  
 Vous pouvez étendre la <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition> classe pour définir l’apparence d’une balise. Vous devez exporter votre classe \(comme un <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition>\) avec les attributs suivants :  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: le nom utilisé pour faire référence à ce format  
  
-   <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>: cela entraîne la mise en forme s’affichent dans l’interface utilisateur  
  
 Dans le constructeur, vous définissez le nom d’affichage et l’apparence de la balise.<xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.BackgroundColor%2A> définit la couleur de remplissage, et <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.ForegroundColor%2A> définit la couleur de bordure. Le <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.DisplayName%2A> est le nom localisé de la définition de format.  
  
 Voici un exemple d’une définition de format :  
  
```  
[Export(typeof(EditorFormatDefinition))]  
[Name("MarkerFormatDefinition/HighlightWordFormatDefinition")]  
[UserVisible(true)]  
internal class HighlightWordFormatDefinition : MarkerFormatDefinition  
{  
    public HighlightWordFormatDefinition()  
    {  
        this.BackgroundColor = Colors.LightBlue;  
        this.ForegroundColor = Colors.DarkBlue;  
        this.DisplayName = "Highlight Word";   
        this.ZOrder = 5;  
    }  
}  
  
```  
  
 Pour appliquer cette définition de format à une balise, référencer le nom que vous définissez dans l’attribut de nom de la classe \(pas le nom d’affichage\).  
  
> [!NOTE]
>  Pour obtenir un exemple d’un <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition>, consultez la classe HighlightWordFormatDefinition dans [Procédure pas à pas : Mise en surbrillance de texte](../extensibility/walkthrough-highlighting-text.md).  
  
## Extension des ornements  
 Ornements de définissent les effets visuels qui peuvent être ajoutés au texte affiché dans une vue de texte ou au texte afficher lui\-même. Vous pouvez définir vos propres ornements comme n’importe quel type de <xref:System.Windows.UIElement>.  
  
 Dans votre classe d’ornement, vous devez déclarer un <xref:Microsoft.VisualStudio.Text.Editor.AdornmentLayerDefinition>. Pour inscrire votre couche d’ornement, exportez\-le avec les attributs suivants :  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: le nom de l’ornement.  
  
-   <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: le classement de l’ornement en ce qui concerne les autres couches d’ornement. La classe <xref:Microsoft.VisualStudio.Text.Editor.PredefinedAdornmentLayers> définit quatre couches par défaut : sélection, mode plan, du signe insertion et le texte.  
  
 L’exemple suivant montre les attributs d’exportation sur une définition de couche d’ornement.  
  
```  
[Export]  
[Name("TestEmbeddedAdornment")]  
[Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]  
internal AdornmentLayerDefinition testLayerDefinition;  
```  
  
 Vous devez créer une deuxième classe qui implémente <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> et gère son <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> événement en instanciant l’ornement. Vous devez exporter cette classe avec les attributs suivants :  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: le type de contenu \(par exemple, « texte » ou « code »\) pour lequel l’ornement est valide.  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>: le type d’affichage de texte pour lequel cet ornement est valide. La classe <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles> possède le jeu de rôles d’affichage de texte prédéfini. Par exemple, <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document> est principalement utilisé pour les vues des fichiers texte.<xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> est utilisé pour les vues de texte qu’un utilisateur peut modifier ou accédez à l’aide de la souris et du clavier. Exemples de <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> les vues sont l’affichage de l’éditeur de texte et la **sortie** fenêtre.  
  
 L’exemple suivant montre les attributs d’exportation sur le fournisseur d’ornements.  
  
```  
[Export(typeof(IWpfTextViewCreationListener))]  
[ContentType("csharp")]  
[TextViewRole(PredefinedTextViewRoles.Document)]  
internal sealed class TestAdornmentProvider : IWpfTextViewCreationListener  
```  
  
 Un ornement à espace négocié est celle qui occupe le même niveau que le texte d’espace. Pour créer ce type d’ornement, vous devez définir une classe de balise qui hérite de <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>, qui définit la quantité d’espace occupé par l’ornement.  
  
 Comme avec tous les ornements, vous devez exporter la définition de couche d’ornement.  
  
```  
[Export]  
[Name("TestAdornment")]  
[Order(After = DefaultAdornmentLayers.Text)]  
internal AdornmentLayerDefinition testAdornmentLayer;  
```  
  
 Pour instancier l’ornement à espace négocié, vous devez créer une classe qui implémente <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>, en plus de la classe qui implémente <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> \(comme avec les autres types d’ornements\).  
  
 Pour inscrire le fournisseur de balise, vous devez l’exporter avec les attributs suivants :  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: le type de contenu \(par exemple, « texte » ou « code »\) pour lequel votre ornement est valide.  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>: le type d’affichage de texte pour lesquels cette balise ou ornement est valide. La classe <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles> possède le jeu de rôles d’affichage de texte prédéfini. Par exemple, <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document> est principalement utilisé pour les vues des fichiers texte.<xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> est utilisé pour les vues de texte qu’un utilisateur peut modifier ou accédez à l’aide de la souris et du clavier. Exemples de <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> les vues sont l’affichage de l’éditeur de texte et la **sortie** fenêtre.  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>: le type de balise ou ornement que vous avez définis. Vous devez ajouter un second <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> pour <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>.  
  
 L’exemple suivant montre les attributs d’exportation sur le fournisseur de balise pour une balise d’ornement à espace négocié.  
  
```  
[Export(typeof(ITaggerProvider))]  
[ContentType("text")]  
[TextViewRole(PredefinedTextViewRoles.Document)]  
[TagType(typeof(SpaceNegotiatingAdornmentTag))]  
[TagType(typeof(TestSpaceNegotiatingTag))]  
internal sealed class TestTaggerProvider : ITaggerProvider  
```  
  
## Extension des processeurs de la souris  
 Vous pouvez ajouter une gestion spéciale pour l’entrée de la souris. Créez une classe qui hérite de <xref:Microsoft.VisualStudio.Text.Editor.MouseProcessorBase> et remplacer les événements de souris pour l’entrée que vous souhaitez gérer. Vous devez également implémenter <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessorProvider> dans une deuxième classe et de l’exporter avec la <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> qui spécifie le type de contenu \(par exemple, « texte » ou « code »\) pour lequel le Gestionnaire de souris est valide.  
  
 L’exemple suivant montre les attributs d’exportation sur un fournisseur de processeur de la souris.  
  
```  
[Export(typeof(IMouseProcessorProvider))]  
[Name("test mouse processor")]  
[ContentType("text")]  
[TextViewRole(PredefinedTextViewRoles.Interactive)]   
internal sealed class TestMouseProcessorProvider : IMouseProcessorProvider  
```  
  
## Extension des gestionnaires de déplacement  
 Vous pouvez personnaliser le comportement des gestionnaires de déplacement pour certains types de texte en créant une classe qui implémente <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.IDropHandler> et une deuxième classe qui implémente <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.IDropHandlerProvider> pour créer le Gestionnaire de déplacement. Vous devez exporter le Gestionnaire de déplacement, ainsi que les attributs suivants :  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.DropFormatAttribute>: le format du texte pour lequel ce gestionnaire de déplacement est valide. Les formats suivants sont traités dans l’ordre de priorité, du plus élevé au plus bas :  
  
    1.  N’importe quel format personnalisé  
  
    2.  FileDrop  
  
    3.  EnhancedMetafile  
  
    4.  WaveAudio  
  
    5.  RIFF  
  
    6.  DIF  
  
    7.  Paramètres régionaux  
  
    8.  Palette  
  
    9. PenData  
  
    10. Sérialisable  
  
    11. SymbolicLink  
  
    12. XAML  
  
    13. XamlPackage  
  
    14. TIFF  
  
    15. Bitmap  
  
    16. DIB  
  
    17. MetafilePicture  
  
    18. CSV  
  
    19. System.String  
  
    20. Au Format HTML  
  
    21. UnicodeText  
  
    22. OEMText  
  
    23. Texte  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: le nom du Gestionnaire de liste.  
  
-   <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: le classement du Gestionnaire de dépôt avant ou après le Gestionnaire de liste par défaut. Le Gestionnaire de déplacement par défaut pour Visual Studio est nommé « DefaultFileDropHandler ».  
  
 L’exemple suivant montre les attributs d’exportation sur un fournisseur Gestionnaire de dépôt.  
  
```  
[Export(typeof(IDropHandlerProvider))]  
[DropFormat("Text")]   
[Name("TestDropHandler")]  
[Order(Before="DefaultFileDropHandler")]   
internal class TestDropHandlerProvider : IDropHandlerProvider  
```  
  
## Extension des Options de l’éditeur  
 Vous pouvez définir des options pour être valide uniquement dans une certaine étendue, par exemple, dans une vue de texte. L’éditeur fournit cet ensemble d’options prédéfinies : options de l’éditeur, les options d’affichage et les options d’affichage de Windows Presentation Foundation \(WPF\). Ces options sont accessibles dans <xref:Microsoft.VisualStudio.Text.Editor.DefaultOptions>, <xref:Microsoft.VisualStudio.Text.Editor.DefaultTextViewOptions>, et <xref:Microsoft.VisualStudio.Text.Editor.DefaultWpfViewOptions>.  
  
 Pour ajouter une nouvelle option, dérivez une classe à partir d’une de ces classes de définition d’option :  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.EditorOptionDefinition%601>  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.ViewOptionDefinition%601>  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.WpfViewOptionDefinition%601>  
  
 L’exemple suivant montre comment exporter une définition d’option qui a une valeur booléenne.  
  
```  
[Export(typeof(EditorOptionDefinition))]  
internal sealed class TestOption : EditorOptionDefinition<bool>  
```  
  
## Étendre IntelliSense  
 IntelliSense est un terme général qui désigne un groupe de fonctionnalités qui fournissent des informations à propos du texte structuré et saisie semi\-automatique des instructions pour celui\-ci. Ces fonctionnalités incluent la saisie semi\-automatique des instructions, l’aide de la signature, Info Express et ampoules. Saisie semi\-automatique des instructions aide les utilisateurs à entrer un nom de langage \(mot clé\) ou un membre correctement. Assistance de signature affiche la signature ou les signatures pour la méthode que l’utilisateur vient de saisir. Infos Express affiche une signature complète pour un nom de type ou membre lorsque la souris pointe dessus. Ampoule fournir des actions supplémentaires pour certains identificateurs dans certains contextes, par exemple, renommer toutes les occurrences d’une variable après qu’une occurrence a été renommée.  
  
 La conception d’une fonctionnalité IntelliSense est similaire dans tous les cas :  
  
-   Un IntelliSense *broker* est responsable de l’ensemble du processus.  
  
-   Un IntelliSense *session* représente la séquence d’événements entre le déclenchement du présenteur et descendant ou d’annulation de la sélection. La session est généralement déclenchée par un mouvement de l’utilisateur.  
  
-   Un IntelliSense *contrôleur* est chargé de décider quand la session doit commencer et se terminer. Il détermine également si les informations doivent être validées et lorsque la session doit être annulée.  
  
-   Un IntelliSense *source* fournit le contenu et décide de la meilleure correspondance.  
  
-   Un IntelliSense *presenter* est chargé d’afficher le contenu.  
  
 Dans la plupart des cas, nous vous recommandons de fournir au moins une source et un contrôleur. Vous pouvez également fournir un présentateur pour personnaliser l’affichage.  
  
### Implémentation d’une Source d’IntelliSense  
 Pour personnaliser une source, vous devez implémenter une des interfaces suivantes du code source \(ou plus\) :  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>  
  
> [!IMPORTANT]
>  <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagSource> a été déconseillé en faveur de <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>.  
  
 En outre, vous devez implémenter un fournisseur du même type :  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>  
  
> [!IMPORTANT]
>  <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagSourceProvider> a été déconseillé en faveur de <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>.  
  
 Vous devez exporter le fournisseur avec les attributs suivants :  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: le nom de la source.  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: le type de contenu \(par exemple, « texte » ou « code »\) à laquelle s’applique la source.  
  
-   <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: l’ordre dans lequel la source doit apparaître \(par rapport à d’autres sources\).  
  
-   L’exemple suivant montre les attributs d’exportation sur un fournisseur de source de saisie semi\-automatique.  
  
```  
Export(typeof(ICompletionSourceProvider))]  
[Name(" Test Statement Completion Provider")]  
[Order(Before = "default")]  
[ContentType("text")]  
internal class TestCompletionSourceProvider : ICompletionSourceProvider  
```  
  
 Pour plus d’informations sur l’implémentation des sources d’IntelliSense, consultez les procédures suivantes :  
  
 [Procédure pas à pas : Affichage des info\-bulles Info express](../Topic/Walkthrough:%20Displaying%20QuickInfo%20Tooltips.md)  
  
 [Procédure pas à pas : Affichage de l’aide de Signature](../extensibility/walkthrough-displaying-signature-help.md)  
  
 [Procédure pas à pas : Affichage de saisie semi\-automatique des instructions](../extensibility/walkthrough-displaying-statement-completion.md)  
  
### L’implémentation d’un contrôleur IntelliSense  
 Pour personnaliser un contrôleur, vous devez implémenter le <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController> interface. En outre, vous devez implémenter un fournisseur de contrôleur ainsi que les attributs suivants :  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: le nom du contrôleur.  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: le type de contenu \(par exemple, « texte » ou « code »\) à laquelle s’applique le contrôleur.  
  
-   <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: l’ordre dans lequel le contrôleur doit apparaître \(en ce qui concerne les autres contrôleurs\).  
  
 L’exemple suivant montre les attributs d’exportation sur un fournisseur de contrôleur d’achèvement.  
  
```  
Export(typeof(IIntellisenseControllerProvider))]  
[Name(" Test Controller Provider")]  
[Order(Before = "default")]  
[ContentType("text")]  
internal class TestIntellisenseControllerProvider : IIntellisenseControllerProvider  
```  
  
 Pour plus d’informations sur l’utilisation de contrôleurs IntelliSense, consultez les procédures suivantes :  
  
 [Procédure pas à pas : Affichage des info\-bulles Info express](../Topic/Walkthrough:%20Displaying%20QuickInfo%20Tooltips.md)