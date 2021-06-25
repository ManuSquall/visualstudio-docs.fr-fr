---
title: Points d’extension du service de langage et de l’éditeur | Microsoft Docs
description: Découvrez les points d’extension de l’éditeur de code Visual Studio que vous pouvez étendre, y compris la plupart des fonctionnalités du service de langage.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- editors [Visual Studio SDK], new - extension points
ms.assetid: 91a6417e-a6fe-4bc2-9d9f-5173c634a99b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 293851f1f3e72508a9bc119fb7551b0118ab2a9b
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903145"
---
# <a name="language-service-and-editor-extension-points"></a>Points d’extension du service de langage et de l’éditeur
L’éditeur fournit des points d’extension que vous pouvez étendre en tant que composants de Managed Extensibility Framework (MEF), y compris la plupart des fonctionnalités du service de langage. Voici les principales catégories de points d’extension :

- Types de contenu

- Types de classifications et formats de classification

- Marges et barres de défilement

- Balises

- Ornements

- Processeurs de souris

- Gestionnaires de suppression

- Options

- IntelliSense

## <a name="extend-content-types"></a>Étendre les types de contenu
 Les types de contenu sont les définitions des genres de texte gérés par l’éditeur, par exemple « Text », « code » ou « CSharp ». Vous définissez un nouveau type de contenu en déclarant une variable du type <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> et en attribuant un nom unique au nouveau type de contenu. Pour inscrire le type de contenu à l’aide de l’éditeur, exportez-le avec les attributs suivants :

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute> nom du type de contenu.

- <xref:Microsoft.VisualStudio.Utilities.BaseDefinitionAttribute> nom du type de contenu à partir duquel ce type de contenu est dérivé. Un type de contenu peut hériter de plusieurs autres types de contenu.

  Étant donné que la <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> classe est sealed, vous pouvez l’exporter sans paramètre de type.

  L’exemple suivant montre des attributs d’exportation sur une définition de type de contenu.

```
[Export]
[Name("test")]
[BaseDefinition("code")]
[BaseDefinition("projection")]
internal static ContentTypeDefinition TestContentTypeDefinition;
```

 Les types de contenu peuvent être basés sur zéro, un ou plusieurs types de contenu préexistants. Voici les types intégrés :

- Any : type de contenu de base. Parent de tous les autres types de contenu.

- Text : type de base pour le contenu sans projection. Hérite de « any ».

- Texte en clair : pour le texte sans code. Hérite de « Text ».

- Code : pour le code de tous genres. Hérite de « Text ».

- Inerte : exclut le texte de tout type de gestion. Aucune extension n’est appliquée au texte de ce type de contenu.

- Projection : pour le contenu des mémoires tampons de projection. Hérite de « any ».

- IntelliSense : pour le contenu d’IntelliSense. Hérite de « Text ».

- Sighelp : aide sur la signature. Hérite de « IntelliSense ».

- Sighelp-doc : signature Help documentation. Hérite de « IntelliSense ».

  Voici quelques-uns des types de contenu définis par Visual Studio et certains des langages qui sont hébergés dans Visual Studio :

- De base

- C/C++

- ConsoleOutput

- CSharp

- CSS

- AIM

- Résultats

- F#

- HTML

- JScript

- XAML

- XML

  Pour découvrir la liste des types de contenu disponibles, importez le <xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService> , qui gère la collection de types de contenu pour l’éditeur. Le code suivant importe ce service en tant que propriété.

```
[Import]
internal IContentTypeRegistryService ContentTypeRegistryService { get; set; }
```

 Pour associer un type de contenu à une extension de nom de fichier, utilisez <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> .

> [!NOTE]
> Dans Visual Studio, les extensions de nom de fichier sont inscrites à l’aide <xref:Microsoft.VisualStudio.Shell.ProvideLanguageExtensionAttribute> de sur un package de service de langage. Le <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> associe un type de contenu MEF à une extension de nom de fichier qui a été inscrite de cette manière.

 Pour exporter l’extension de nom de fichier vers la définition de type de contenu, vous devez inclure les attributs suivants :

- <xref:Microsoft.VisualStudio.Utilities.FileExtensionAttribute>: spécifie l’extension de nom de fichier.

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: spécifie le type de contenu.

  Étant donné que la <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> classe est sealed, vous pouvez l’exporter sans paramètre de type.

  L’exemple suivant montre des attributs d’exportation sur une extension de nom de fichier dans une définition de type de contenu.

```
[Export]
[FileExtension(".test")]
[ContentType("test")]
internal static FileExtensionToContentTypeDefinition TestFileExtensionDefinition;
```

 Le <xref:Microsoft.VisualStudio.Utilities.IFileExtensionRegistryService> gère les associations entre les extensions de nom de fichier et les types de contenu.

## <a name="extend-classification-types-and-classification-formats"></a>Étendre les types de classifications et les formats de classification
 Vous pouvez utiliser des types de classification pour définir les genres de texte pour lesquels vous souhaitez fournir une gestion différente (par exemple, en coloriant le texte « mot clé » en bleu et le texte « commentaire » en vert). Définissez un nouveau type de classification en déclarant une variable de type <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeDefinition> et en lui attribuant un nom unique.

 Pour inscrire le type de classification auprès de l’éditeur, exportez-le avec les attributs suivants :

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: nom du type de classification.

- <xref:Microsoft.VisualStudio.Utilities.BaseDefinitionAttribute>: nom du type de classification dont ce type de classification hérite. Tous les types de classification héritent de « Text » et un type de classification peut hériter de plusieurs autres types de classification.

  Étant donné que la <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeDefinition> classe est sealed, vous pouvez l’exporter sans paramètre de type.

  L’exemple suivant montre des attributs d’exportation sur une définition de type de classification.

```
[Export]
[Name("csharp.test")]
[BaseDefinition("test")]
internal static ClassificationTypeDefinition CSharpTestDefinition;
```

 Le <xref:Microsoft.VisualStudio.Language.StandardClassification.IStandardClassificationService> fournit l’accès aux classifications standard. Les types de classification intégrés incluent les éléments suivants :

- "text"

- « langage naturel » (dérive de « texte »)

- « langage formel » (dérive de « texte »)

- « String » (dérive de « Literal »)

- « Character » (dérive de « Literal »)

- « numérique » (dérive de « Literal »)

  Un ensemble de types d’erreur différents héritent de <xref:Microsoft.VisualStudio.Text.Adornments.ErrorTypeDefinition> . Elles incluent les types d’erreur suivants :

- « erreur de syntaxe »

- « erreur du compilateur »

- « autre erreur »

- tres

  Pour découvrir la liste des types de classification disponibles, importez le <xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService> , qui gère la collection de types de classification pour l’éditeur. Le code suivant importe ce service en tant que propriété.

```
[Import]
internal IClassificationTypeRegistryService ClassificationTypeRegistryService { get; set; }
```

 Vous pouvez définir une définition de format de classification pour votre nouveau type de classification. Dérivez une classe de <xref:Microsoft.VisualStudio.Text.Classification.ClassificationFormatDefinition> et exportez-la avec le type <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition> , ainsi que les attributs suivants :

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: nom du format.

- <xref:Microsoft.VisualStudio.Utilities.DisplayNameAttribute>: nom complet du format.

- <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>: spécifie si le format apparaît dans la page **polices et couleurs** de la boîte de dialogue **options** .

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: priorité du format. Les valeurs valides sont de <xref:Microsoft.VisualStudio.Text.Classification.Priority> .

- <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeAttribute>: nom du type de classification auquel ce format est mappé.

  L’exemple suivant montre des attributs d’exportation sur une définition de format de classification.

```
[Export(typeof(EditorFormatDefinition))]
[ClassificationType(ClassificationTypeNames = "test")]
[Name("test")]
[DisplayName("Test")]
[UserVisible(true)]
[Order(After = Priority.Default, Before = Priority.High)]
internal sealed class TestFormat : ClassificationFormatDefinition
```

 Pour découvrir la liste des formats disponibles, importez le <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService> , qui gère la collection de formats pour l’éditeur. Le code suivant importe ce service en tant que propriété.

```
[Import]
internal IEditorFormatMapService FormatMapService { get; set; }
```

## <a name="extend-margins-and-scrollbars"></a>Étendre les marges et les barres de défilement
 Les marges et les barres de défilement sont les éléments d’affichage principaux de l’éditeur, en plus de l’affichage de texte lui-même. Vous pouvez fournir n’importe quel nombre de marges en plus des marges standard qui apparaissent autour de l’affichage de texte.

 Implémentez une <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMargin> interface pour définir une marge. Vous devez également implémenter l' <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMarginProvider> interface pour créer la marge.

 Pour inscrire le fournisseur de marge auprès de l’éditeur, vous devez exporter le fournisseur avec les attributs suivants :

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: nom de la marge.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: ordre dans lequel la marge s’affiche, par rapport aux autres marges.

   Les marges prédéfinies sont les suivantes :

  - « ScrollBar horizontal WPF »

  - « Barre de défilement verticale WPF »

  - « Marge des nombres de lignes WPF »

    Les marges horizontales qui ont un attribut Order de `After="Wpf Horizontal Scrollbar"` sont affichées sous la marge intégrée, et les marges horizontales qui ont un attribut Order de `Before ="Wpf Horizontal Scrollbar"` sont affichées au-dessus de la marge intégrée. Les marges verticales droites qui ont un attribut Order de `After="Wpf Vertical Scrollbar"` sont affichées à droite de la barre de défilement. Les marges verticales gauches ayant un attribut ordre de `After="Wpf Line Number Margin"` apparaissent à gauche de la marge du numéro de ligne (si elle est visible).

- <xref:Microsoft.VisualStudio.Text.Editor.MarginContainerAttribute>: type de marge (gauche, droite, haut ou bas).

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: type de contenu (par exemple, « texte » ou « code ») pour lequel votre marge est valide.

  L’exemple suivant montre des attributs d’exportation sur un fournisseur de marge pour une marge qui apparaît à droite de la marge de numéro de ligne.

```
[Export(typeof(IWpfTextViewMarginProvider))]
[Name("TestMargin")]
[Order(Before = "Wpf Line Number Margin")]
[MarginContainer(PredefinedMarginNames.Left)]
[ContentType("text")]
```

## <a name="extend-tags"></a>Étendre les étiquettes
 Les balises sont un moyen d’associer des données à différents genres de texte. Dans de nombreux cas, les données associées s’affichent sous la forme d’un effet visuel, mais toutes les balises n’ont pas une présentation visuelle. Vous pouvez définir votre propre type de balise en implémentant <xref:Microsoft.VisualStudio.Text.Tagging.ITag> . Vous devez également implémenter <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> pour fournir les balises pour un ensemble donné d’étendues de texte et un <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider> pour fournir la balise. Vous devez exporter le fournisseur de balises avec les attributs suivants :

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: type de contenu (par exemple, « texte » ou « code ») pour lequel votre balise est valide.

- <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>: type de balise.

  L’exemple suivant montre des attributs d’exportation sur un fournisseur de balises.

\<CodeContentPlaceHolder>8 </CodeContentPlaceHolder> les genres suivants de balises sont intégrés :

- <xref:Microsoft.VisualStudio.Text.Tagging.ClassificationTag>: associé à un <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType> .

- <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>: associé aux types d’erreur.

- <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>: associé à un ornement.

  > [!NOTE]
  > Pour obtenir un exemple d’un <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> , consultez la définition HighlightWordTag dans [procédure pas à pas : mise en surbrillance du texte](../extensibility/walkthrough-highlighting-text.md).

- <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag>: associé aux régions qui peuvent être développées ou réduites dans le mode plan.

- <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>: définit l’espace occupé par un ornement dans une vue de texte. Pour plus d’informations sur les ornements de négociation spatiale, consultez la section suivante.

- <xref:Microsoft.VisualStudio.Text.Editor.IntraTextAdornmentTag>: fournit l’espacement et le dimensionnement automatiques pour l’ornement.

  Pour rechercher et utiliser des balises pour les mémoires tampons et les vues, importez le <xref:Microsoft.VisualStudio.Text.Tagging.IViewTagAggregatorFactoryService> ou le <xref:Microsoft.VisualStudio.Text.Tagging.IBufferTagAggregatorFactoryService> , qui vous donne un <xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601> du type demandé. Le code suivant importe ce service en tant que propriété.

```
[Import]
internal IViewTagAggregatorFactoryService ViewTagAggregatorFactoryService { get; set; }
```

#### <a name="tags-and-markerformatdefinitions"></a>Balises et MarkerFormatDefinitions
 Vous pouvez étendre la <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition> classe pour définir l’apparence d’une balise. Vous devez exporter votre classe (en tant que <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition> ) avec les attributs suivants :

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: nom utilisé pour référencer ce format

- <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>: le format apparaît alors dans l’interface utilisateur

  Dans le constructeur, vous définissez le nom d’affichage et l’apparence de la balise. <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.BackgroundColor%2A> définit la couleur de remplissage et <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.ForegroundColor%2A> définit la couleur de la bordure. <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.DisplayName%2A>Est le nom localisable de la définition de format.

  Voici un exemple de définition de format :

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

 Pour appliquer cette définition de format à une balise, référencez le nom que vous avez défini dans l’attribut Name de la classe (pas le nom complet).

> [!NOTE]
> Pour obtenir un exemple d’un <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition> , consultez la classe HighlightWordFormatDefinition dans [procédure pas à pas : mise en surbrillance du texte](../extensibility/walkthrough-highlighting-text.md).

## <a name="extend-adornments"></a>Étendre les ornements
 Les ornements définissent des effets visuels qui peuvent être ajoutés au texte affiché dans une vue de texte ou à l’affichage de texte lui-même. Vous pouvez définir votre propre ornement comme n’importe quel type de <xref:System.Windows.UIElement> .

 Dans votre classe d’ornements, vous devez déclarer un <xref:Microsoft.VisualStudio.Text.Editor.AdornmentLayerDefinition> . Pour inscrire votre couche d’ornements, exportez-la avec les attributs suivants :

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: nom de l’ornement.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: classement de l’ornement par rapport à d’autres couches d’ornement. La classe <xref:Microsoft.VisualStudio.Text.Editor.PredefinedAdornmentLayers> définit quatre couches par défaut : la sélection, le mode plan, le signe insertion et le texte.

  L’exemple suivant montre des attributs d’exportation sur une définition de la couche d’ornement.

```
[Export]
[Name("TestEmbeddedAdornment")]
[Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]
internal AdornmentLayerDefinition testLayerDefinition;
```

 Vous devez créer une deuxième classe qui implémente <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> et gère son <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> événement en instanciant l’ornement. Vous devez exporter cette classe avec les attributs suivants :

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: type de contenu (par exemple, « texte » ou « code ») pour lequel l’ornement est valide.

- <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>: type de vue de texte pour lequel cet ornement est valide. La classe <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles> possède l’ensemble de rôles d’affichage de texte prédéfinis. Par exemple, <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document> est principalement utilisé pour les affichages de texte des fichiers. <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> est utilisé pour les affichages de texte qu’un utilisateur peut modifier ou parcourir à l’aide de la souris et du clavier. <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive>L’affichage de texte de l’éditeur et la fenêtre **sortie** sont des exemples de vues.

  L’exemple suivant montre des attributs d’exportation sur le fournisseur d’ornements.

```
[Export(typeof(IWpfTextViewCreationListener))]
[ContentType("csharp")]
[TextViewRole(PredefinedTextViewRoles.Document)]
internal sealed class TestAdornmentProvider : IWpfTextViewCreationListener
```

 Un ornement à espace négocié est un ornement qui occupe de l’espace au même niveau que le texte. Pour créer ce type d’ornement, vous devez définir une classe de balise qui hérite de <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag> , qui définit la quantité d’espace occupée par l’ornement.

 Comme avec tous les ornements, vous devez exporter la définition de la couche d’ornement.

```
[Export]
[Name("TestAdornment")]
[Order(After = DefaultAdornmentLayers.Text)]
internal AdornmentLayerDefinition testAdornmentLayer;
```

 Pour instancier l’ornement à espace négocié, vous devez créer une classe qui implémente <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider> , en plus de la classe qui implémente <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> (comme avec d’autres genres d’ornements).

 Pour inscrire le fournisseur de balises, vous devez l’exporter avec les attributs suivants :

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: type de contenu (par exemple, « texte » ou « code ») pour lequel votre ornement est valide.

- <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>: type de vue de texte pour lequel cette balise ou ornement est valide. La classe <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles> possède l’ensemble de rôles d’affichage de texte prédéfinis. Par exemple, <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document> est principalement utilisé pour les affichages de texte des fichiers. <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> est utilisé pour les affichages de texte qu’un utilisateur peut modifier ou parcourir à l’aide de la souris et du clavier. <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive>L’affichage de texte de l’éditeur et la fenêtre **sortie** sont des exemples de vues.

- <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>: type de balise ou d’ornement que vous avez défini. Vous devez ajouter un second <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> pour <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag> .

  L’exemple suivant montre des attributs d’exportation sur le fournisseur de balises pour une balise d’ornement à espace négocié.

```
[Export(typeof(ITaggerProvider))]
[ContentType("text")]
[TextViewRole(PredefinedTextViewRoles.Document)]
[TagType(typeof(SpaceNegotiatingAdornmentTag))]
[TagType(typeof(TestSpaceNegotiatingTag))]
internal sealed class TestTaggerProvider : ITaggerProvider
```

## <a name="extending-mouse-processors"></a>Extension des processeurs de souris
 Vous pouvez ajouter un traitement spécial pour l’entrée de la souris. Créez une classe qui hérite de <xref:Microsoft.VisualStudio.Text.Editor.MouseProcessorBase> et substituez les événements de souris pour l’entrée que vous souhaitez gérer. Vous devez également implémenter <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessorProvider> dans une deuxième classe et l’exporter avec le <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> qui spécifie le type de contenu (par exemple, « text » ou « code ») pour lequel le gestionnaire de la souris est valide.

 L’exemple suivant montre des attributs d’exportation sur un fournisseur de processeurs de souris.

```
[Export(typeof(IMouseProcessorProvider))]
[Name("test mouse processor")]
[ContentType("text")]
[TextViewRole(PredefinedTextViewRoles.Interactive)]
internal sealed class TestMouseProcessorProvider : IMouseProcessorProvider
```

## <a name="extend-drop-handlers"></a>Étendre les gestionnaires de suppression
 Vous pouvez personnaliser le comportement des gestionnaires de suppression pour des genres de texte spécifiques en créant une classe qui implémente <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.IDropHandler> et une deuxième classe qui implémente <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.IDropHandlerProvider> pour créer le gestionnaire de suppression. Vous devez exporter le gestionnaire de suppression avec les attributs suivants :

- <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.DropFormatAttribute>: format de texte pour lequel ce gestionnaire de suppression est valide. Les formats suivants sont gérés par ordre de priorité, de la plus élevée à la plus faible :

  1. Tout format personnalisé

  2. FileDrop

  3. EnhancedMetafile

  4. WaveAudio

  5. Répartition

  6. Comporte

  7. Paramètres régionaux

  8. Palette

  9. PenData

  10. Sérialisable

  11. SymbolicLink

  12. Langage

  13. XamlPackage

  14. TIFF

  15. Bitmap

  16. Bitmap

  17. MetafilePicture

  18. CSV

  19. System.String

  20. Format HTML

  21. UnicodeText

  22. OEMText

  23. Texte

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: nom du gestionnaire de suppression.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: classement du gestionnaire de suppression avant ou après le gestionnaire de suppression par défaut. Le gestionnaire de suppression par défaut pour Visual Studio est nommé « DefaultFileDropHandler ».

  L’exemple suivant montre des attributs d’exportation sur un fournisseur Drop handler.

```
[Export(typeof(IDropHandlerProvider))]
[DropFormat("Text")]
[Name("TestDropHandler")]
[Order(Before="DefaultFileDropHandler")]
internal class TestDropHandlerProvider : IDropHandlerProvider
```

## <a name="extending-editor-options"></a>Extension des options de l’éditeur
 Vous pouvez définir des options qui ne sont valides que dans une certaine étendue, par exemple dans une vue de texte. L’éditeur fournit cet ensemble d’options prédéfinies : options de l’éditeur, options d’affichage et options d’affichage de Windows Presentation Foundation (WPF). Ces options se trouvent dans <xref:Microsoft.VisualStudio.Text.Editor.DefaultOptions> , <xref:Microsoft.VisualStudio.Text.Editor.DefaultTextViewOptions> et <xref:Microsoft.VisualStudio.Text.Editor.DefaultWpfViewOptions> .

 Pour ajouter une nouvelle option, dérivez une classe de l’une de ces classes de définition d’options :

- <xref:Microsoft.VisualStudio.Text.Editor.EditorOptionDefinition%601>

- <xref:Microsoft.VisualStudio.Text.Editor.ViewOptionDefinition%601>

- <xref:Microsoft.VisualStudio.Text.Editor.WpfViewOptionDefinition%601>

  L’exemple suivant montre comment exporter une définition d’option qui a une valeur booléenne.

```
[Export(typeof(EditorOptionDefinition))]
internal sealed class TestOption : EditorOptionDefinition<bool>
```

## <a name="extend-intellisense"></a>Étendre IntelliSense
 IntelliSense est un terme général pour un groupe de fonctionnalités qui fournissent des informations sur du texte structuré et la saisie semi-automatique des instructions pour celui-ci. Ces fonctionnalités incluent la saisie semi-automatique des instructions, l’aide sur les signatures, les informations rapides et les ampoules. La saisie semi-automatique des instructions aide les utilisateurs à taper correctement un mot clé de langage ou un nom de membre. Aide sur la signature affiche la ou les signatures de la méthode que l’utilisateur vient de taper. Infos Express affiche une signature complète pour un type ou un nom de membre lorsque la souris se trouve sur celui-ci. L’ampoule fournit des actions supplémentaires pour certains identificateurs dans certains contextes, par exemple, en renommant toutes les occurrences d’une variable après le changement de nom d’une occurrence.

 La conception d’une fonctionnalité IntelliSense est très similaire dans tous les cas :

- Un *répartiteur* IntelliSense est responsable de l’ensemble du processus.

- Une *session* IntelliSense représente la séquence d’événements entre le déclenchement du présenteur et la validation ou l’annulation de la sélection. La session est généralement déclenchée par un mouvement utilisateur.

- Un *contrôleur* IntelliSense est chargé de déterminer à quel moment la session doit commencer et se terminer. Elle détermine également le moment où les informations doivent être validées et le moment où la session doit être annulée.

- Une *source* IntelliSense fournit le contenu et décide de la meilleure correspondance.

- Un *présentateur* IntelliSense est chargé d’afficher le contenu.

  Dans la plupart des cas, nous vous recommandons de fournir au moins une source et un contrôleur. Vous pouvez également fournir un présentateur si vous souhaitez personnaliser l’affichage.

### <a name="implement-an-intellisense-source"></a>Implémenter une source IntelliSense
 Pour personnaliser une source, vous devez implémenter une (ou plusieurs) des interfaces sources suivantes :

- <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource>

- <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource>

- <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource>

- <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>

> [!IMPORTANT]
> <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagSource> a été déconseillé en faveur de <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource> .

 En outre, vous devez implémenter un fournisseur du même type :

- <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider>

- <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider>

- <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider>

- <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>

> [!IMPORTANT]
> <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagSourceProvider> a été déconseillé en faveur de <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider> .

 Vous devez exporter le fournisseur avec les attributs suivants :

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: nom de la source.

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: type de contenu (par exemple, « texte » ou « code ») auquel la source s’applique.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: ordre dans lequel la source doit apparaître (par rapport à d’autres sources).

- L’exemple suivant montre des attributs d’exportation sur un fournisseur de source de saisie semi-automatique.

```
Export(typeof(ICompletionSourceProvider))]
[Name(" Test Statement Completion Provider")]
[Order(Before = "default")]
[ContentType("text")]
internal class TestCompletionSourceProvider : ICompletionSourceProvider
```

 Pour plus d’informations sur l’implémentation des sources IntelliSense, consultez les procédures pas à pas suivantes :

- [Procédure pas à pas : afficher les info-bulles Info Express](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)

- [Procédure pas à pas : afficher l’aide sur les signatures](../extensibility/walkthrough-displaying-signature-help.md)

- [Procédure pas à pas : afficher la saisie semi-automatique des instructions](../extensibility/walkthrough-displaying-statement-completion.md)

### <a name="implement-an-intellisense-controller"></a>Implémenter un contrôleur IntelliSense
 Pour personnaliser un contrôleur, vous devez implémenter l' <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController> interface. En outre, vous devez implémenter un fournisseur de contrôleur avec les attributs suivants :

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: nom du contrôleur.

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: type de contenu (par exemple, « texte » ou « code ») auquel le contrôleur s’applique.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: ordre dans lequel le contrôleur doit apparaître (par rapport à d’autres contrôleurs).

  L’exemple suivant montre des attributs d’exportation sur un fournisseur de contrôleur d’achèvement.

```
Export(typeof(IIntellisenseControllerProvider))]
[Name(" Test Controller Provider")]
[Order(Before = "default")]
[ContentType("text")]
internal class TestIntellisenseControllerProvider : IIntellisenseControllerProvider
```

 Pour plus d’informations sur l’utilisation des contrôleurs IntelliSense, consultez les procédures pas à pas suivantes :

- [Procédure pas à pas : afficher les info-bulles Info Express](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)
