---
title: "Service de langage et les Points d’Extension Éditeur | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], new - extension points
ms.assetid: 91a6417e-a6fe-4bc2-9d9f-5173c634a99b
caps.latest.revision: "33"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 7e62f1f3cac8f279dedbc79f283b908119d66ff2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="language-service-and-editor-extension-points"></a>Service de langage et les Points d’Extension de l’éditeur
L’éditeur fournit des points d’extension que vous pouvez étendre en tant que parties de composant de Managed Extensibility Framework (MEF), y compris la plupart des fonctionnalités de service de langage. Voici les catégories de point d’extension principale :  
  
-   Types de contenu  
  
-   Les formats de classification et les types de classification  
  
-   Les marges et les barres de défilement  
  
-   Balises  
  
-   Ornements  
  
-   Processeurs de la souris  
  
-   Gestionnaires de déplacement  
  
-   Options  
  
-   IntelliSense  
  
## <a name="extending-content-types"></a>Étendre les Types de contenu  
 Types de contenu sont les définitions des types de texte géré par l’éditeur, par exemple, « texte », « code » ou « CSharp ». Vous définissez un nouveau type de contenu en déclarant une variable du type <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> et en donnant le type de contenu à un nom unique. Pour inscrire le type de contenu avec l’éditeur, vous devez l’exporter avec les attributs suivants :  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>est le nom du type de contenu.  
  
-   <xref:Microsoft.VisualStudio.Utilities.BaseDefinitionAttribute>est le nom du type de contenu à partir duquel ce type de contenu est dérivé. Un type de contenu peut-être hériter de plusieurs autres types de contenu.  
  
 Étant donné que la <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> classe est sealed, vous pouvez l’exporter avec aucun paramètre de type.  
  
 L’exemple suivant montre les attributs d’exportation sur une définition de type de contenu.  
  
```  
[Export]  
[Name("test")]  
[BaseDefinition("code")]  
[BaseDefinition("projection")]  
internal static ContentTypeDefinition TestContentTypeDefinition;  
```  
  
 Types de contenu peuvent être basés sur zéro ou plusieurs types de contenu existants. Voici les types intégrés :  
  
-   N’importe laquelle : le type de contenu de base. Parent de tous les autres types de contenu.  
  
-   Texte : le type de base pour le contenu non-projection. Hérite de « tout ».  
  
-   Texte en clair : pour le texte de non code. Hérite de « texte ».  
  
-   Code : code de tous les types. Hérite de « texte ».  
  
-   Inertes : exclut le texte à partir de n’importe quel type de gestion. Texte de ce type de contenu n’aura jamais n’importe quelle extension appliquée.  
  
-   Projection : pour le contenu des mémoires tampons de projection. Hérite de « tout ».  
  
-   IntelliSense : pour le contenu d’IntelliSense. Hérite de « texte ».  
  
-   Sighelp : aide pour la signature. Hérite de « intellisense ».  
  
-   Sighelp-doc : documentation d’aide signature. Hérite de « intellisense ».  
  
 Voici certains des types de contenu qui sont définies par Visual Studio et des langues qui sont hébergés dans Visual Studio :  
  
-   Basic  
  
-   C/C++  
  
-   ConsoleOutput  
  
-   CSharp  
  
-   CSS  
  
-   ENC  
  
-   FindResults  
  
-   F#  
  
-   HTML  
  
-   JScript  
  
-   XAML  
  
-   XML  
  
 Pour découvrir la liste des types de contenu disponibles, vous devez importer le <xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService>, qui gère la collection des types de contenu de l’éditeur. Le code suivant importe ce service en tant que propriété.  
  
```  
[Import]  
internal IContentTypeRegistryService ContentTypeRegistryService { get; set; }  
```  
  
 Pour associer un type de contenu avec une extension de nom de fichier, utilisez <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition>.  
  
> [!NOTE]
>  Dans Visual Studio, les extensions de nom de fichier sont inscrits à l’aide de la <xref:Microsoft.VisualStudio.Shell.ProvideLanguageExtensionAttribute> sur un package de service de langage. Le <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> associe un type de contenu de MEF avec une extension de nom de fichier qui a été inscrit de cette manière.  
  
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
  
## <a name="extending-classification-types-and-classification-formats"></a>Extension de Classification et Types de Classification des Formats  
 Vous pouvez utiliser des types de classification pour définir les types de texte pour lequel vous souhaitez fournir un traitement différent (par exemple, la coloration du texte « mot clé » bleu et le texte « commentaire » vert). Définir un nouveau type de classification en déclarant une variable de type <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeDefinition> et en lui attribuant un nom unique.  
  
 Pour inscrire le type de classification avec l’éditeur, vous devez l’exporter avec les attributs suivants :  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: le nom du type de classification.  
  
-   <xref:Microsoft.VisualStudio.Utilities.BaseDefinitionAttribute>: le nom du type de classification à partir de laquelle hérite de ce type de classification. Tous les types de classification héritent de « texte », et un type de classification peut-être hériter de plusieurs autres types de classification.  
  
 Étant donné que la <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeDefinition> classe est sealed, vous pouvez l’exporter avec aucun paramètre de type.  
  
 L’exemple suivant montre les attributs d’exportation sur une définition de type de classification.  
  
```  
[Export]  
[Name("csharp.test")]  
[BaseDefinition("test")]  
internal static ClassificationTypeDefinition CSharpTestDefinition;  
```  
  
 Le <xref:Microsoft.VisualStudio.Language.StandardClassification.IStandardClassificationService> fournit l’accès aux classifications standards. Types de classification intégrées citer :  
  
-   « texte »  
  
-   « langage naturel » (dérive de « texte »)  
  
-   « langage formel » (dérive de « texte »)  
  
-   « chaîne » (dérive de « literal »)  
  
-   « caractère » (dérive de « literal »)  
  
-   « numérique » (dérive de « literal »)  
  
 Un ensemble de différents types d’erreur héritent de <xref:Microsoft.VisualStudio.Text.Adornments.ErrorTypeDefinition>. Elles comprennent les types d’erreur suivant :  
  
-   « Erreur de syntaxe »  
  
-   « Erreur du compilateur »  
  
-   autres « erreur »  
  
-   « avertissement »  
  
 Pour découvrir la liste des types de Classification disponibles, vous devez importer le <xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService>, qui gère la collection de types de classification de l’éditeur. Le code suivant importe ce service en tant que propriété.  
  
```  
[Import]  
internal IClassificationTypeRegistryService ClassificationTypeRegistryService { get; set; }  
```  
  
 Vous pouvez définir une définition de format de classification pour votre nouveau type de classification. Dérivez une classe de <xref:Microsoft.VisualStudio.Text.Classification.ClassificationFormatDefinition> et l’exporter avec le type <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition>, avec les attributs suivants :  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: le nom du format.  
  
-   <xref:Microsoft.VisualStudio.Utilities.DisplayNameAttribute>: le nom d’affichage du format.  
  
-   <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>: Spécifie si le format s’affiche sur le **polices et couleurs** page de la **Options** boîte de dialogue.  
  
-   <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: la priorité du format. Les valeurs valides sont comprises entre <xref:Microsoft.VisualStudio.Text.Classification.Priority>.  
  
-   <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeAttribute>: le nom de la classification de type à qui ce format est mappé.  
  
 L’exemple suivant montre les attributs d’exportation sur une définition de format de classification.  
  
```  
[Export(typeof(EditorFormatDefinition))]  
[ClassificationType(ClassificationTypeNames = "test")]  
[Name("test")]  
[DisplayName("Test")]  
[UserVisible(true)]  
[Order(After = Priority.Default, Before = Priority.High)]  
internal sealed class TestFormat : ClassificationFormatDefinition  
```  
  
 Pour découvrir la liste des formats disponibles, vous devez importer le <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>, qui gère la collection de formats pour l’éditeur. Le code suivant importe ce service en tant que propriété.  
  
```  
[Import]  
internal IEditorFormatMapService FormatMapService { get; set; }  
```  
  
## <a name="extending-margins-and-scrollbars"></a>Barres de défilement et d’extension  
 Les marges et les barres de défilement sont des éléments de la vue principale de l’éditeur en plus de l’affichage de texte lui-même. Vous pouvez fournir un nombre quelconque de marges en plus les marges standard qui apparaissent autour de l’affichage de texte.  
  
 Implémentez un <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMargin> interface pour définir une marge. Vous devez également implémenter la <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMarginProvider> interface permettant de créer la marge.  
  
 Pour inscrire le fournisseur de marge avec l’éditeur, vous devez exporter le fournisseur avec les attributs suivants :  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: le nom de la marge.  
  
-   <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: l’ordre dans lequel la marge s’affiche, par rapport à d’autres marges.  
  
     Il s’agit des marges prédéfinies :  
  
    -   « Barre de défilement horizontale de Wpf »  
  
    -   « Barre de défilement verticale de Wpf »  
  
    -   « Marge de numéro de ligne de Wpf »  
  
     Les marges horizontales qui ont un attribut de l’ordre de `After="Wpf Horizontal Scrollbar"` s’affichent dans la marge intégrée et les marges horizontales qui ont un attribut de l’ordre de `Before ="Wpf Horizontal Scrollbar"` affichés au-dessus de la marge intégrée. Avec le bouton droit des marges verticales qui ont un attribut de l’ordre de `After="Wpf Vertical Scrollbar"` sont affichés à droite de la barre de défilement. Gauche des marges verticales qui ont un attribut de l’ordre de `After="Wpf Line Number Margin"` apparaissent à gauche de la marge de numéro de ligne (si elle est visible).  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.MarginContainerAttribute>: le type de marge (gauche, droite, haut ou bas).  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: le type de contenu (par exemple, « text » ou « code ») pour lesquels votre marge est valide.  
  
 L’exemple suivant montre les attributs d’exportation sur un fournisseur de marge pour une marge s’affiche à droite de la marge de numéro de ligne.  
  
```  
[Export(typeof(IWpfTextViewMarginProvider))]  
[Name("TestMargin")]  
[Order(Before = "Wpf Line Number Margin")]  
[MarginContainer(PredefinedMarginNames.Left)]  
[ContentType("text")]   
```  
  
## <a name="extending-tags"></a>Extension des balises  
 Les balises sont un moyen d’associer des données avec différents types de texte. Dans de nombreux cas, les données associées sont affichées en tant qu’un effet visuel, mais pas toutes les balises ont une présentation visuelle. Vous pouvez définir votre propre type de balise en implémentant <xref:Microsoft.VisualStudio.Text.Tagging.ITag>. Vous devez également implémenter <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> pour fournir les balises pour un ensemble donné d’étendues de texte et un <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider> pour fournir la balise. Vous devez exporter le fournisseur de baliseur avec les attributs suivants :  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: le type de contenu (par exemple, « text » ou « code ») pour laquelle la balise est valide.  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>: le type de balise.  
  
 L’exemple suivant montre les attributs d’exportation sur un fournisseur de baliseur.  
  
<CodeContentPlaceHolder>8</CodeContentPlaceHolder>  
 Les types de balise suivants sont prédéfinis :  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.ClassificationTag>: associé à un <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType>.  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>: associé aux types d’erreurs.  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>: associé à un ornement.  
  
    > [!NOTE]
    >  Pour obtenir un exemple d’un <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>, consultez la définition de HighlightWordTag dans [procédure pas à pas : mise en surbrillance de texte](../extensibility/walkthrough-highlighting-text.md).  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag>: associées aux régions qui peuvent être développées ou réduites en plan.  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>: définit l’espace occupé par un ornement dans une vue de texte. Pour plus d’informations sur les ornements de négociation d’espace, consultez la section suivante.  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.IntraTextAdornmentTag>: fournit l’espacement automatique et dimensionnement pour l’ornement.  
  
 Pour rechercher et utiliser des balises pour les mémoires tampons et des vues, importez le <xref:Microsoft.VisualStudio.Text.Tagging.IViewTagAggregatorFactoryService> ou <xref:Microsoft.VisualStudio.Text.Tagging.IBufferTagAggregatorFactoryService>, qui permettent un <xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601> du type demandé. Le code suivant importe ce service en tant que propriété.  
  
```  
[Import]  
internal IViewTagAggregatorFactoryService ViewTagAggregatorFactoryService { get; set; }  
```  
  
#### <a name="tags-and-markerformatdefinitions"></a>Balises et MarkerFormatDefinitions  
 Vous pouvez étendre la <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition> classe pour définir l’apparence d’une balise. Vous devez exporter votre classe (comme un <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition>) avec les attributs suivants :  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: le nom utilisé pour faire référence à ce format.  
  
-   <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>: cela entraîne le format s’affichent dans l’interface utilisateur  
  
 Dans le constructeur, vous définissez le nom d’affichage et l’apparence de la balise. <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.BackgroundColor%2A>définit la couleur de remplissage et <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.ForegroundColor%2A> définit la couleur de bordure. Le <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.DisplayName%2A> est le nom localisé de la définition de format.  
  
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
  
 Pour appliquer cette définition de format pour une balise, faites référence au nom que vous définissez dans l’attribut de nom de la classe (pas le nom d’affichage).  
  
> [!NOTE]
>  Pour obtenir un exemple d’un <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition>, consultez la classe HighlightWordFormatDefinition dans [procédure pas à pas : mise en surbrillance de texte](../extensibility/walkthrough-highlighting-text.md).  
  
## <a name="extending-adornments"></a>Extension des ornements  
 Ornements de définissent les effets visuels qui peuvent être ajoutés au texte affiché dans une vue de texte ou le texte afficher lui-même. Vous pouvez définir vos propres ornement comme n’importe quel type de <xref:System.Windows.UIElement>.  
  
 Dans votre classe d’ornement, vous devez déclarer une <xref:Microsoft.VisualStudio.Text.Editor.AdornmentLayerDefinition>. Pour inscrire votre couche d’ornement, vous devez l’exporter avec les attributs suivants :  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: le nom de l’ornement.  
  
-   <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: le classement de l’ornement en ce qui concerne les autres couches d’ornement. La classe <xref:Microsoft.VisualStudio.Text.Editor.PredefinedAdornmentLayers> définit quatre couches par défaut : sélection, mode plan, du point d’insertion et de texte.  
  
 L’exemple suivant montre les attributs d’exportation sur une définition de couche d’ornement.  
  
```  
[Export]  
[Name("TestEmbeddedAdornment")]  
[Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]  
internal AdornmentLayerDefinition testLayerDefinition;  
```  
  
 Vous devez créer une deuxième classe qui implémente <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> et gère son <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> événement en instanciant l’ornement. Vous devez exporter cette classe ainsi que les attributs suivants :  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: le type de contenu (par exemple, « text » ou « code ») pour lequel l’ornement n’est valide.  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>: le type d’affichage de texte pour lequel cet ornement n’est valide. La classe <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles> a l’ensemble de rôles de vue de texte prédéfini. Par exemple, <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document> est principalement utilisé pour les vues des fichiers texte. <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive>est utilisé pour les affichages de texte qu’un utilisateur peut modifier ou accédez à l’aide de la souris et du clavier. Exemples de <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> les vues sont l’affichage de l’éditeur de texte et la **sortie** fenêtre.  
  
 L’exemple suivant montre les attributs d’exportation sur le fournisseur d’ornement.  
  
```  
[Export(typeof(IWpfTextViewCreationListener))]  
[ContentType("csharp")]  
[TextViewRole(PredefinedTextViewRoles.Document)]  
internal sealed class TestAdornmentProvider : IWpfTextViewCreationListener  
```  
  
 Un ornement à espace négocié est celle qui occupe le même niveau que le texte d’espace. Pour créer ce genre d’ornement, vous devez définir une classe de balise qui hérite de <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>, qui définit la quantité d’espace occupé par l’ornement.  
  
 Comme avec tous les motifs, vous devez exporter la définition de couche d’ornement.  
  
```  
[Export]  
[Name("TestAdornment")]  
[Order(After = DefaultAdornmentLayers.Text)]  
internal AdornmentLayerDefinition testAdornmentLayer;  
```  
  
 Pour instancier l’ornement à espace négocié, vous devez créer une classe qui implémente <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>, en plus de la classe qui implémente <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> (comme avec d’autres types d’ornements).  
  
 Pour inscrire le fournisseur de baliseur, vous devez l’exporter avec les attributs suivants :  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: le type de contenu (par exemple, « text » ou « code ») pour lequel votre ornement n’est valide.  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>: le type d’affichage de texte pour lequel cette balise ou ornement n’est valide. La classe <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles> a l’ensemble de rôles de vue de texte prédéfini. Par exemple, <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document> est principalement utilisé pour les vues des fichiers texte. <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive>est utilisé pour les affichages de texte qu’un utilisateur peut modifier ou accédez à l’aide de la souris et du clavier. Exemples de <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> les vues sont l’affichage de l’éditeur de texte et la **sortie** fenêtre.  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>: le type de balise ou ornement que vous avez définies. Vous devez ajouter un deuxième <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> pour <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>.  
  
 L’exemple suivant montre les attributs d’exportation sur le fournisseur de baliseur d’une balise d’ornement à espace négocié.  
  
```  
[Export(typeof(ITaggerProvider))]  
[ContentType("text")]  
[TextViewRole(PredefinedTextViewRoles.Document)]  
[TagType(typeof(SpaceNegotiatingAdornmentTag))]  
[TagType(typeof(TestSpaceNegotiatingTag))]  
internal sealed class TestTaggerProvider : ITaggerProvider  
```  
  
## <a name="extending-mouse-processors"></a>Extension des processeurs de la souris  
 Vous pouvez ajouter un traitement spécial pour l’entrée de la souris. Créez une classe qui hérite de <xref:Microsoft.VisualStudio.Text.Editor.MouseProcessorBase> et remplacer les événements de souris pour l’entrée que vous souhaitez gérer. Vous devez également implémenter <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessorProvider> dans une deuxième classe et l’exporter avec la <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> qui spécifie le type de contenu (par exemple, « text » ou « code ») pour lequel votre gestionnaire de la souris est valide.  
  
 L’exemple suivant montre les attributs d’exportation sur un fournisseur de processeur de la souris.  
  
```  
[Export(typeof(IMouseProcessorProvider))]  
[Name("test mouse processor")]  
[ContentType("text")]  
[TextViewRole(PredefinedTextViewRoles.Interactive)]   
internal sealed class TestMouseProcessorProvider : IMouseProcessorProvider  
```  
  
## <a name="extending-drop-handlers"></a>Extension des gestionnaires de déplacement  
 Vous pouvez personnaliser le comportement des gestionnaires de déplacement pour certains genres de texte en créant une classe qui implémente <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.IDropHandler> et une deuxième classe qui implémente <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.IDropHandlerProvider> pour créer le Gestionnaire de déplacement. Vous devez exporter le Gestionnaire de déplacement, ainsi que les attributs suivants :  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.DropFormatAttribute>: le format du texte pour lequel ce gestionnaire de dépôt est valid. Les formats suivants sont traités dans l’ordre de priorité, du plus élevé au plus bas :  
  
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
  
    20. Format HTML  
  
    21. UnicodeText  
  
    22. OEMText  
  
    23. Texte  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: le nom du Gestionnaire de dépôt.  
  
-   <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: le classement du Gestionnaire de dépôt avant ou après le Gestionnaire de dépôt par défaut. Le Gestionnaire de dépôt par défaut pour Visual Studio est nommé « DefaultFileDropHandler ».  
  
 L’exemple suivant montre les attributs d’exportation sur un fournisseur Gestionnaire de dépôt.  
  
```  
[Export(typeof(IDropHandlerProvider))]  
[DropFormat("Text")]   
[Name("TestDropHandler")]  
[Order(Before="DefaultFileDropHandler")]   
internal class TestDropHandlerProvider : IDropHandlerProvider  
```  
  
## <a name="extending-editor-options"></a>Extension des Options de l’éditeur  
 Vous pouvez définir des options pour être valide uniquement dans une certaine étendue, par exemple, dans une vue de texte. L’éditeur fournit cet ensemble d’options prédéfinies : options de vue de Windows Presentation Foundation (WPF), les options d’affichage et les options de l’éditeur. Ces options sont accessibles dans <xref:Microsoft.VisualStudio.Text.Editor.DefaultOptions>, <xref:Microsoft.VisualStudio.Text.Editor.DefaultTextViewOptions>, et <xref:Microsoft.VisualStudio.Text.Editor.DefaultWpfViewOptions>.  
  
 Pour ajouter une nouvelle option, dérivez une classe à partir d’une de ces classes de définition d’option :  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.EditorOptionDefinition%601>  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.ViewOptionDefinition%601>  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.WpfViewOptionDefinition%601>  
  
 L’exemple suivant montre comment exporter une définition d’option qui a une valeur booléenne.  
  
```  
[Export(typeof(EditorOptionDefinition))]  
internal sealed class TestOption : EditorOptionDefinition<bool>  
```  
  
## <a name="extending-intellisense"></a>Étendre IntelliSense  
 IntelliSense est un terme général qui désigne un groupe de fonctionnalités qui fournissent des informations sur le texte structuré et saisie semi-automatique des instructions pour celle-ci. Ces fonctionnalités incluent la saisie semi-automatique des instructions, l’aide de la signature, Info Express et des ampoules. Saisie semi-automatique des instructions permet aux utilisateurs d’entrer un nom de langue mot clé ou un membre correctement. Aide pour la signature affiche la signature ou les signatures de la méthode entrés par l’utilisateur a seulement. Info Express affiche une signature complète pour un nom de type ou membre lorsque la souris pointe dessus. Ampoule fournir des actions supplémentaires pour certains identificateurs dans certains contextes, par exemple, renommer toutes les occurrences d’une variable après qu’une occurrence a été renommée.  
  
 La conception d’une fonctionnalité IntelliSense est similaire dans tous les cas :  
  
-   Une IntelliSense *broker* est responsable de l’ensemble du processus.  
  
-   Une IntelliSense *session* représente la séquence d’événements entre le déclenchement du présentateur et moment de la validation ou l’annulation de la sélection. La session est généralement déclenchée par des mouvements de l’utilisateur.  
  
-   Une IntelliSense *contrôleur* est chargé de décider quand la session doit commencer et se terminer. Il décide également lorsque les informations doivent être validées et lorsque la session doit être annulée.  
  
-   Une IntelliSense *source* fournit le contenu et décide de la meilleure correspondance.  
  
-   Une IntelliSense *présentateur* est responsable de l’affichage du contenu.  
  
 Dans la plupart des cas, nous vous recommandons de fournir au moins une source et un contrôleur. Vous pouvez également fournir un présentateur si vous souhaitez personnaliser l’affichage.  
  
### <a name="implementing-an-intellisense-source"></a>Implémentation d’une Source d’IntelliSense  
 Pour personnaliser une source, vous devez implémenter une des interfaces suivantes source (ou plus) :  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>  
  
> [!IMPORTANT]
>  <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagSource>a été déconseillé en faveur de <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>.  
  
 En outre, vous devez implémenter un fournisseur du même type :  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>  
  
> [!IMPORTANT]
>  <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagSourceProvider>a été déconseillé en faveur de <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>.  
  
 Vous devez exporter le fournisseur avec les attributs suivants :  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: le nom de la source.  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: le type de contenu (par exemple, « text » ou « code ») à laquelle s’applique la source.  
  
-   <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: l’ordre dans lequel la source doit apparaître (par rapport à d’autres sources).  
  
-   L’exemple suivant montre les attributs d’exportation sur un fournisseur de source de saisie semi-automatique.  
  
```  
Export(typeof(ICompletionSourceProvider))]  
[Name(" Test Statement Completion Provider")]  
[Order(Before = "default")]  
[ContentType("text")]  
internal class TestCompletionSourceProvider : ICompletionSourceProvider  
```  
  
 Pour plus d’informations sur l’implémentation des sources d’IntelliSense, consultez les procédures suivantes :  
  
 [Procédure pas à pas : Affichage d’info-bulles Info express](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)  
  
 [Procédure pas à pas : Affichage d’aide sur les signatures](../extensibility/walkthrough-displaying-signature-help.md)  
  
 [Procédure pas à pas : affichage de la saisie semi-automatique des instructions](../extensibility/walkthrough-displaying-statement-completion.md)  
  
### <a name="implementing-an-intellisense-controller"></a>Implémentation d’un contrôleur IntelliSense  
 Pour personnaliser un contrôleur, vous devez implémenter la <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController> interface. En outre, vous devez implémenter un fournisseur de contrôleur avec les attributs suivants :  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: le nom du contrôleur.  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: le type de contenu (par exemple, « text » ou « code ») à laquelle s’applique le contrôleur.  
  
-   <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: l’ordre dans lequel le contrôleur doit apparaître (en ce qui concerne les autres contrôleurs).  
  
 L’exemple suivant montre les attributs d’exportation sur un fournisseur de contrôleur d’achèvement.  
  
```  
Export(typeof(IIntellisenseControllerProvider))]  
[Name(" Test Controller Provider")]  
[Order(Before = "default")]  
[ContentType("text")]  
internal class TestIntellisenseControllerProvider : IIntellisenseControllerProvider  
```  
  
 Pour plus d’informations sur l’utilisation de contrôleurs IntelliSense, consultez les procédures suivantes :  
  
 [Procédure pas à pas : Affichage d’info-bulles Info express](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)