---
title: Service de langage et les Points d’Extension Éditeur | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - extension points
ms.assetid: 91a6417e-a6fe-4bc2-9d9f-5173c634a99b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d99916c31e35f7494a402ff4c5d1a7b182a0c52d
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53907960"
---
# <a name="language-service-and-editor-extension-points"></a>Points d’extension éditeur et le service de langage
L’éditeur fournit des points d’extension que vous pouvez étendre en tant que parties de composant Managed Extensibility Framework (MEF), y compris la plupart des fonctionnalités de service de langage. Voici les catégories de point d’extension principal :  
  
-   Types de contenu  
  
-   Types de classification et de formats de classification  
  
-   Marges et les barres de défilement  
  
-   Balises  
  
-   Ornements  
  
-   Processeurs de la souris  
  
-   Gestionnaires de déplacement  
  
-   Options  
  
-   IntelliSense  
  
## <a name="extend-content-types"></a>Étendre des types de contenu  
 Types de contenu sont les définitions des types de texte géré par l’éditeur, par exemple, « text », « code » ou « CSharp ». Vous définissez un nouveau type de contenu en déclarant une variable du type <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> et en donnant le nouveau type de contenu à un nom unique. Pour inscrire le type de contenu avec l’éditeur, vous devez l’exporter avec les attributs suivants :  
  
- <xref:Microsoft.VisualStudio.Utilities.NameAttribute> est le nom du type de contenu.  
  
- <xref:Microsoft.VisualStudio.Utilities.BaseDefinitionAttribute> est le nom du type de contenu à partir duquel ce type de contenu est dérivé. Un type de contenu peut hériter de plusieurs autres types de contenu.  
  
  Étant donné que la <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> classe est sealed, vous pouvez l’exporter avec aucun paramètre de type.  
  
  L’exemple suivant montre les attributs d’exportation sur une définition de type de contenu.  
  
```  
[Export]  
[Name("test")]  
[BaseDefinition("code")]  
[BaseDefinition("projection")]  
internal static ContentTypeDefinition TestContentTypeDefinition;  
```  
  
 Types de contenu peuvent reposer sur zéro ou plusieurs types de contenu existants. Voici les types intégrés :  
  
- Le : le type de contenu de base. Parent de tous les autres types de contenu.  
  
- Texte : le type de base pour le contenu non projection. Hérite de « tout ».  
  
- Texte en clair : pour le texte de non code. Hérite de « texte ».  
  
- Code : pour le code de toutes sortes. Hérite de « texte ».  
  
- Inerte : exclut le texte à partir de n’importe quel type de gestion. Texte de ce type de contenu n’aura jamais de n’importe quelle extension appliquée.  
  
- Projection : pour le contenu de mémoires tampons de projection. Hérite de « tout ».  
  
- IntelliSense : pour le contenu d’IntelliSense. Hérite de « texte ».  
  
- Sighelp : pour la signature. Hérite de « intellisense ».  
  
- Sighelp-doc : documentation d’aide signature. Hérite de « intellisense ».  
  
  Voici certains des types de contenu qui sont définies par Visual Studio et autres langages qui sont hébergés dans Visual Studio :  
  
- Basic  
  
- C/C++  
  
- ConsoleOutput  
  
- CSharp  
  
- CSS  
  
- ENC  
  
- Résultats  
  
- F#  
  
- HTML  
  
- JScript  
  
- XAML  
  
- XML  
  
  Pour découvrir la liste des types de contenu disponibles, vous devez importer le <xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService>, qui tient à jour la collection de types de contenu de l’éditeur. Le code suivant importe ce service sous la forme d’une propriété.  
  
```  
[Import]  
internal IContentTypeRegistryService ContentTypeRegistryService { get; set; }  
```  
  
 Pour associer un type de contenu avec une extension de nom de fichier, utilisez <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition>.  
  
> [!NOTE]
>  Dans Visual Studio, les extensions de nom de fichier sont inscrits à l’aide de la <xref:Microsoft.VisualStudio.Shell.ProvideLanguageExtensionAttribute> sur un package de service de langage. Le <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> associe un type de contenu de MEF avec une extension de nom de fichier qui a été inscrit de cette manière.  
  
 Pour exporter l’extension de nom de fichier à la définition de type de contenu, vous devez inclure les attributs suivants :  
  
- <xref:Microsoft.VisualStudio.Utilities.FileExtensionAttribute>: Spécifie l’extension de nom de fichier.  
  
- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: Spécifie le type de contenu.  
  
  Étant donné que la <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> classe est sealed, vous pouvez l’exporter avec aucun paramètre de type.  
  
  L’exemple suivant montre les attributs d’exportation sur une extension de nom de fichier à une définition de type de contenu.  
  
```  
[Export]  
[FileExtension(".test")]  
[ContentType("test")]  
internal static FileExtensionToContentTypeDefinition TestFileExtensionDefinition;  
```  
  
 Le <xref:Microsoft.VisualStudio.Utilities.IFileExtensionRegistryService> gère les associations entre les extensions de nom de fichier et les types de contenu.  
  
## <a name="extend-classification-types-and-classification-formats"></a>Étendre les types de classification et de formats de classification  
 Vous pouvez utiliser les types de classification pour définir les types de texte pour lequel vous souhaitez fournir un traitement différent (par exemple, la coloration du texte « mot clé » bleu et le texte « commentaire » vert). Définir un nouveau type de classification en déclarant une variable de type <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeDefinition> et en lui attribuant un nom unique.  
  
 Pour inscrire le type de classification avec l’éditeur, vous devez l’exporter avec les attributs suivants :  
  
- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: le nom du type de classification.  
  
- <xref:Microsoft.VisualStudio.Utilities.BaseDefinitionAttribute>: le nom du type de classification à partir de laquelle hérite de ce type de classification. Tous les types de classification héritent de « text » et un type de classification peut hériter de plusieurs autres types de classification.  
  
  Étant donné que la <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeDefinition> classe est sealed, vous pouvez l’exporter avec aucun paramètre de type.  
  
  L’exemple suivant montre les attributs d’exportation sur une définition de type de classification.  
  
```  
[Export]  
[Name("csharp.test")]  
[BaseDefinition("test")]  
internal static ClassificationTypeDefinition CSharpTestDefinition;  
```  
  
 Le <xref:Microsoft.VisualStudio.Language.StandardClassification.IStandardClassificationService> fournit l’accès aux classifications standards. Types de classification intégrées à savoir :  
  
- « texte »  
  
- « langage naturel » (dérive de « texte »)  
  
- « langage formel » (dérive de « texte »)  
  
- « string » (dérive de « literal »)  
  
- « caractère » (dérive de « literal »)  
  
- « numérique » (dérive de « literal »)  
  
  Un ensemble de différents types d’erreur héritent <xref:Microsoft.VisualStudio.Text.Adornments.ErrorTypeDefinition>. Ils incluent les types d’erreur suivant :  
  
- « Erreur de syntaxe »  
  
- « Erreur du compilateur »  
  
- autres « erreur »  
  
- « avertissement »  
  
  Pour découvrir la liste des types de classification disponibles, vous devez importer le <xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService>, qui tient à jour la collection de types de classification de l’éditeur. Le code suivant importe ce service sous la forme d’une propriété.  
  
```  
[Import]  
internal IClassificationTypeRegistryService ClassificationTypeRegistryService { get; set; }  
```  
  
 Vous pouvez définir une définition de format de classification pour votre nouveau type de classification. Dérivez une classe de <xref:Microsoft.VisualStudio.Text.Classification.ClassificationFormatDefinition> et exportez-le avec le type <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition>, avec les attributs suivants :  
  
- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: le nom du format.  
  
- <xref:Microsoft.VisualStudio.Utilities.DisplayNameAttribute>: le nom d’affichage du format.  
  
- <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>: Spécifie si le format s’affiche sur le **polices et couleurs** page de la **Options** boîte de dialogue.  
  
- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: la priorité du format. Les valeurs valides sont comprises entre <xref:Microsoft.VisualStudio.Text.Classification.Priority>.  
  
- <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeAttribute>: nom de la classification du type auquel ce format est mappée.  
  
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
  
 Pour découvrir la liste des formats disponibles, vous devez importer le <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>, qui tient à jour la collection de formats pour l’éditeur. Le code suivant importe ce service sous la forme d’une propriété.  
  
```  
[Import]  
internal IEditorFormatMapService FormatMapService { get; set; }  
```  
  
## <a name="extend-margins-and-scrollbars"></a>Étendre les marges et les barres de défilement  
 Marges et les barres de défilement sont les éléments de la vue principale de l’éditeur en plus de l’affichage de texte lui-même. Vous pouvez fournir un nombre quelconque de marges en plus les marges standards qui apparaissent autour de l’affichage de texte.  
  
 Implémentez un <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMargin> interface pour définir une marge. Vous devez également implémenter la <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMarginProvider> interface permettant de créer la marge.  
  
 Pour inscrire le fournisseur de marge avec l’éditeur, vous devez exporter le fournisseur avec les attributs suivants :  
  
- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: le nom de la marge.  
  
- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: l’ordre dans lequel la marge s’affiche, par rapport à d’autres marges.  
  
   Il s’agit des marges prédéfinies :  
  
  - « Barre de défilement horizontale de Wpf »  
  
  - « Barre de défilement verticale de Wpf »  
  
  - « Marge de numéro de ligne de Wpf »  
  
    Les marges horizontales qui ont un attribut de l’ordre de `After="Wpf Horizontal Scrollbar"` s’affichent sous la marge intégrée et les marges horizontales qui ont un attribut de l’ordre de `Before ="Wpf Horizontal Scrollbar"` affichés au-dessus de la marge intégrée. Avec le bouton droit marges verticales qui ont un attribut de l’ordre de `After="Wpf Vertical Scrollbar"` sont affichés à droite de la barre de défilement. Gauche des marges verticales qui ont un attribut de l’ordre de `After="Wpf Line Number Margin"` apparaissent à gauche de la marge de numéro de ligne (s’il est visible).  
  
- <xref:Microsoft.VisualStudio.Text.Editor.MarginContainerAttribute>: le type de marge (gauche, droite, haut ou bas).  
  
- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: le type de contenu (par exemple, « text » ou « code ») pour laquelle votre marge est valide.  
  
  L’exemple suivant montre les attributs d’exportation sur un fournisseur de marge pour une marge s’affiche à droite de la marge de numéro de ligne.  
  
```  
[Export(typeof(IWpfTextViewMarginProvider))]  
[Name("TestMargin")]  
[Order(Before = "Wpf Line Number Margin")]  
[MarginContainer(PredefinedMarginNames.Left)]  
[ContentType("text")]   
```  
  
## <a name="extend-tags"></a>Étendre des balises  
 Les balises sont un moyen d’associer des données à différents types de texte. Dans de nombreux cas, les données associées sont affichées en tant qu’un effet visuel, mais pas toutes les balises ont une présentation visuelle. Vous pouvez définir votre propre type de balise en implémentant <xref:Microsoft.VisualStudio.Text.Tagging.ITag>. Vous devez également implémenter <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> pour fournir les balises pour un ensemble donné d’étendues de texte et un <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider> pour fournir la balise. Vous devez exporter le fournisseur de baliseur ainsi que les attributs suivants :  
  
- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: le type de contenu (par exemple, « text » ou « code ») pour laquelle votre balise est valide.  
  
- <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>: le type de balise.  
  
  L’exemple suivant montre les attributs d’exportation sur un fournisseur de baliseur.  
  
<CodeContentPlaceHolder>8</CodeContentPlaceHolder>  
 Les types de balise suivants sont intégrés :  
  
- <xref:Microsoft.VisualStudio.Text.Tagging.ClassificationTag>: associé à un <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType>.  
  
- <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>: associées aux types d’erreur.  
  
- <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>: associé à un ornement.  
  
  > [!NOTE]
  >  Pour obtenir un exemple d’un <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>, consultez la définition de HighlightWordTag dans [procédure pas à pas : Mise en surbrillance de texte](../extensibility/walkthrough-highlighting-text.md).  
  
- <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag>: associées aux régions qui peuvent être développées ou réduites dans le mode plan.  
  
- <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>: définit l’espace occupé par un ornement dans une vue de texte. Pour plus d’informations sur les ornements négociant espaces, consultez la section suivante.  
  
- <xref:Microsoft.VisualStudio.Text.Editor.IntraTextAdornmentTag>: fournit l’espacement automatique et dimensionnement pour l’ornement.  
  
  Pour rechercher et utiliser des balises pour les vues et les mémoires tampons, importer le <xref:Microsoft.VisualStudio.Text.Tagging.IViewTagAggregatorFactoryService> ou <xref:Microsoft.VisualStudio.Text.Tagging.IBufferTagAggregatorFactoryService>, qui vous donnent un <xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601> du type demandé. Le code suivant importe ce service sous la forme d’une propriété.  
  
```  
[Import]  
internal IViewTagAggregatorFactoryService ViewTagAggregatorFactoryService { get; set; }  
```  
  
#### <a name="tags-and-markerformatdefinitions"></a>Balises et MarkerFormatDefinitions  
 Vous pouvez étendre la <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition> classe pour définir l’apparence d’une balise. Vous devez exporter votre classe (comme un <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition>) avec les attributs suivants :  
  
- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: le nom utilisé pour référencer ce format  
  
- <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>: cela entraîne le format d’apparaître dans l’interface utilisateur  
  
  Dans le constructeur, vous définissez le nom d’affichage et l’apparence de la balise. <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.BackgroundColor%2A> définit la couleur de remplissage et <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.ForegroundColor%2A> définit la couleur de bordure. Le <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.DisplayName%2A> est le nom localisé de la définition de format.  
  
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
  
 Pour appliquer cette définition de format à une balise, référencer le nom que vous définissez dans l’attribut de nom de la classe (pas le nom d’affichage).  
  
> [!NOTE]
>  Pour obtenir un exemple d’un <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition>, consultez la classe HighlightWordFormatDefinition dans [procédure pas à pas : Mise en surbrillance de texte](../extensibility/walkthrough-highlighting-text.md).  
  
## <a name="extend-adornments"></a>Étendre des ornements  
 Ornements définissent des effets visuels qui peuvent être ajoutés au texte affiché dans un affichage de texte ou au texte afficher lui-même. Vous pouvez définir vos propres ornements comme n’importe quel type de <xref:System.Windows.UIElement>.  
  
 Dans votre classe d’ornement, vous devez déclarer un <xref:Microsoft.VisualStudio.Text.Editor.AdornmentLayerDefinition>. Pour inscrire votre couche d’ornement, exportez-le avec les attributs suivants :  
  
- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: le nom de l’ornement.  
  
- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: le classement de l’ornement en ce qui concerne les autres couches de l’ornement. La classe <xref:Microsoft.VisualStudio.Text.Editor.PredefinedAdornmentLayers> définit quatre couches par défaut : Sélection, le mode plan, point d’insertion et de texte.  
  
  L’exemple suivant montre les attributs d’exportation sur une définition de couche d’ornement.  
  
```  
[Export]  
[Name("TestEmbeddedAdornment")]  
[Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]  
internal AdornmentLayerDefinition testLayerDefinition;  
```  
  
 Vous devez créer une deuxième classe qui implémente <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> et gère son <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> événement en instanciant l’ornement. Vous devez exporter cette classe avec les attributs suivants :  
  
- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: le type de contenu (par exemple, « text » ou « code ») pour laquelle l’ornement est valide.  
  
- <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>: le type d’affichage de texte pour laquelle cet ornement est valide. La classe <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles> présente l’ensemble des rôles d’affichage de texte prédéfinis. Par exemple, <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document> est principalement utilisé pour les affichages de texte de fichiers. <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> est utilisé pour les affichages de texte qu’un utilisateur peut modifier ou accédez à l’aide de la souris et du clavier. Exemples de <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> vues sont l’affichage de l’éditeur de texte et la **sortie** fenêtre.  
  
  L’exemple suivant montre les attributs d’exportation sur le fournisseur de l’ornement.  
  
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
  
 Pour instancier l’ornement à espace négocié, vous devez créer une classe qui implémente <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>, en plus de la classe qui implémente <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> (comme les autres types d’ornements).  
  
 Pour inscrire le fournisseur de baliseur, vous devez l’exporter avec les attributs suivants :  
  
- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: le type de contenu (par exemple, « text » ou « code ») pour laquelle votre ornement est valide.  
  
- <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>: le type d’affichage de texte pour lequel cet ornement ou la balise est valide. La classe <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles> présente l’ensemble des rôles d’affichage de texte prédéfinis. Par exemple, <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document> est principalement utilisé pour les affichages de texte de fichiers. <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> est utilisé pour les affichages de texte qu’un utilisateur peut modifier ou accédez à l’aide de la souris et du clavier. Exemples de <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> vues sont l’affichage de l’éditeur de texte et la **sortie** fenêtre.  
  
- <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>: le type de balise ou ornement que vous avez définies. Vous devez ajouter un deuxième <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> pour <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>.  
  
  L’exemple suivant montre les attributs d’exportation sur le fournisseur de baliseur pour une balise d’ornement à espace négocié.  
  
```  
[Export(typeof(ITaggerProvider))]  
[ContentType("text")]  
[TextViewRole(PredefinedTextViewRoles.Document)]  
[TagType(typeof(SpaceNegotiatingAdornmentTag))]  
[TagType(typeof(TestSpaceNegotiatingTag))]  
internal sealed class TestTaggerProvider : ITaggerProvider  
```  
  
## <a name="extending-mouse-processors"></a>Extension des processeurs de la souris  
 Vous pouvez ajouter un traitement spécial pour l’entrée de la souris. Créez une classe qui hérite de <xref:Microsoft.VisualStudio.Text.Editor.MouseProcessorBase> et remplacer les événements de souris pour l’entrée que vous souhaitez gérer. Vous devez également implémenter <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessorProvider> dans une deuxième classe et exportez-le avec la <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> qui spécifie le type de contenu (par exemple, « text » ou « code ») pour laquelle votre gestionnaire de la souris est valide.  
  
 L’exemple suivant montre les attributs d’exportation sur un fournisseur de processeur de la souris.  
  
```  
[Export(typeof(IMouseProcessorProvider))]  
[Name("test mouse processor")]  
[ContentType("text")]  
[TextViewRole(PredefinedTextViewRoles.Interactive)]   
internal sealed class TestMouseProcessorProvider : IMouseProcessorProvider  
```  
  
## <a name="extend-drop-handlers"></a>Étendre des gestionnaires de déplacement  
 Vous pouvez personnaliser le comportement des gestionnaires de déplacement pour certains types de texte en créant une classe qui implémente <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.IDropHandler> et une deuxième classe qui implémente <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.IDropHandlerProvider> pour créer le Gestionnaire de déplacement. Vous devez exporter le Gestionnaire de déplacement, ainsi que les attributs suivants :  
  
- <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.DropFormatAttribute>: le format de texte pour laquelle ce gestionnaire de déplacement est valide. Les formats suivants sont traités par ordre de priorité du plus élevé au plus bas :  
  
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
  
- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: le nom du Gestionnaire de liste.  
  
- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: le classement du Gestionnaire de déplacement avant ou après le Gestionnaire de déplacement par défaut. Le Gestionnaire de déplacement par défaut pour Visual Studio est nommé « DefaultFileDropHandler ».  
  
  L’exemple suivant montre les attributs d’exportation sur un fournisseur de gestionnaire de liste.  
  
```  
[Export(typeof(IDropHandlerProvider))]  
[DropFormat("Text")]   
[Name("TestDropHandler")]  
[Order(Before="DefaultFileDropHandler")]   
internal class TestDropHandlerProvider : IDropHandlerProvider  
```  
  
## <a name="extending-editor-options"></a>Extension des Options de l’éditeur  
 Vous pouvez définir des options pour être valide uniquement dans une certaine étendue, par exemple, dans un affichage de texte. L’éditeur fournit cet ensemble d’options prédéfinies : options de vue de Windows Presentation Foundation (WPF), les options d’affichage et les options de l’éditeur. Vous trouverez ces options dans <xref:Microsoft.VisualStudio.Text.Editor.DefaultOptions>, <xref:Microsoft.VisualStudio.Text.Editor.DefaultTextViewOptions>, et <xref:Microsoft.VisualStudio.Text.Editor.DefaultWpfViewOptions>.  
  
 Pour ajouter une nouvelle option, dérivez une classe à partir d’une de ces classes de définition d’option :  
  
- <xref:Microsoft.VisualStudio.Text.Editor.EditorOptionDefinition%601>  
  
- <xref:Microsoft.VisualStudio.Text.Editor.ViewOptionDefinition%601>  
  
- <xref:Microsoft.VisualStudio.Text.Editor.WpfViewOptionDefinition%601>  
  
  L’exemple suivant montre comment exporter une définition d’option qui a une valeur booléenne.  
  
```  
[Export(typeof(EditorOptionDefinition))]  
internal sealed class TestOption : EditorOptionDefinition<bool>  
```  
  
## <a name="extend-intellisense"></a>Étendre IntelliSense  
 IntelliSense est un terme général qui désigne un groupe de fonctionnalités qui fournissent des informations sur le texte structuré et la saisie semi-automatique des instructions pour lui. Ces fonctionnalités incluent la saisie semi-automatique des instructions, pour la signature, Info Express et des ampoules. Saisie semi-automatique des instructions permet aux utilisateurs d’entrer un nom de langage mot clé ou un membre correctement. Pour la signature affiche la signature ou les signatures pour la méthode que l’utilisateur a tapé juste. Infos Express affiche une signature complète pour un nom de type ou membre lorsque la souris se trouve sur celui-ci. Ampoule fournissent des actions supplémentaires pour certains identificateurs dans certains contextes, par exemple, renommer toutes les occurrences d’une variable après qu’une occurrence a été renommée.  
  
 La conception d’une fonctionnalité IntelliSense est très similaire dans tous les cas :  
  
- Un IntelliSense *broker* est responsable de l’ensemble du processus.  
  
- Un IntelliSense *session* représente la séquence d’événements entre le déclenchement du présentateur et descendant ou d’annulation de la sélection. La session est généralement déclenchée par un mouvement utilisateur.  
  
- Un IntelliSense *contrôleur* est chargé de décider quand la session doit commencer et se terminer. Il choisit également quand les informations doivent être validées et lorsque la session doit être annulée.  
  
- Un IntelliSense *source* fournit le contenu et décide de la meilleure correspondance.  
  
- Un IntelliSense *présentateur* est chargée d’afficher le contenu.  
  
  Dans la plupart des cas, nous vous recommandons de fournir au moins une source et un contrôleur. Vous pouvez également fournir un présentateur si vous souhaitez personnaliser l’affichage.  
  
### <a name="implement-an-intellisense-source"></a>Implémenter une Source d’IntelliSense  
 Pour personnaliser une source, vous devez implémenter un (ou plusieurs) des interfaces de source suivantes :  
  
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
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: le type de contenu (par exemple, « text » ou « code ») à laquelle s’applique la source.  
  
-   <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: l’ordre dans lequel la source doit s’afficher (par rapport à d’autres sources).  
  
-   L’exemple suivant montre les attributs d’exportation sur un fournisseur de source de saisie semi-automatique.  
  
```  
Export(typeof(ICompletionSourceProvider))]  
[Name(" Test Statement Completion Provider")]  
[Order(Before = "default")]  
[ContentType("text")]  
internal class TestCompletionSourceProvider : ICompletionSourceProvider  
```  
  
 Pour plus d’informations sur l’implémentation des sources d’IntelliSense, consultez les procédures suivantes :  
  
 [Procédure pas à pas : Afficher des info-bulles Info express](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)  
  
 [Procédure pas à pas : Afficher l’aide de la Signature](../extensibility/walkthrough-displaying-signature-help.md)  
  
 [Procédure pas à pas : Afficher la saisie semi-automatique des instructions](../extensibility/walkthrough-displaying-statement-completion.md)  
  
### <a name="implement-an-intellisense-controller"></a>Implémenter un contrôleur IntelliSense  
 Pour personnaliser un contrôleur, vous devez implémenter le <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController> interface. En outre, vous devez implémenter un fournisseur de contrôleur avec les attributs suivants :  
  
- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: le nom du contrôleur.  
  
- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: le type de contenu (par exemple, « text » ou « code ») à laquelle s’applique le contrôleur.  
  
- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: l’ordre dans lequel le contrôleur doit s’afficher (par rapport à d’autres contrôleurs).  
  
  L’exemple suivant montre les attributs d’exportation sur un fournisseur de contrôleur de saisie semi-automatique.  
  
```  
Export(typeof(IIntellisenseControllerProvider))]  
[Name(" Test Controller Provider")]  
[Order(Before = "default")]  
[ContentType("text")]  
internal class TestIntellisenseControllerProvider : IIntellisenseControllerProvider  
```  
  
 Pour plus d’informations sur l’utilisation des contrôleurs IntelliSense, consultez les procédures suivantes :  
  
 [Procédure pas à pas : Afficher des info-bulles Info express](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)