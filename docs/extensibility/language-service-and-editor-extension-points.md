---
title: Language Service et Editor Extension Points (en anglais seulement) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - extension points
ms.assetid: 91a6417e-a6fe-4bc2-9d9f-5173c634a99b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 28bb086eb99e4b8128c04f62f9b370eb2eab8fa3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703055"
---
# <a name="language-service-and-editor-extension-points"></a>Service linguistique et points d’extension de l’éditeur
L’éditeur fournit des points d’extension que vous pouvez étendre en tant que pièces de composant Du cadre d’exténuabilité gérée (MEF), y compris la plupart des fonctionnalités de service linguistique. Voici les principales catégories de points d’extension :

- Types de contenu

- Types de classification et formats de classification

- Marges et barres de défilement

- Balises

- Ornements

- Processeurs de souris

- Gestionnaires de goutte

- Options

- IntelliSense

## <a name="extend-content-types"></a>Étendre les types de contenu
 Les types de contenu sont les définitions des types de texte traités par l’éditeur, par exemple, "texte", "code" ou "CSharp". Vous définissez un nouveau type de contenu <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> en déclarant une variable du type et en donnant au nouveau type de contenu un nom unique. Pour enregistrer le type de contenu auprès de l’éditeur, exportez-le avec les attributs suivants :

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>est le nom du type de contenu.

- <xref:Microsoft.VisualStudio.Utilities.BaseDefinitionAttribute>est le nom du type de contenu à partir duquel ce type de contenu est dérivé. Un type de contenu peut hériter de plusieurs autres types de contenu.

  Parce <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> que la classe est scellée, vous pouvez l’exporter sans paramètre de type.

  L’exemple suivant montre les attributs d’exportation sur une définition de type de contenu.

```
[Export]
[Name("test")]
[BaseDefinition("code")]
[BaseDefinition("projection")]
internal static ContentTypeDefinition TestContentTypeDefinition;
```

 Les types de contenu peuvent être basés sur des types de contenu zéro ou plus préexistants. Ce sont les types intégrés:

- N’importe quel: le type de contenu de base. Parent de tous les autres types de contenu.

- Texte : le type de base pour le contenu non-projection. Hérite de "n’importe quoi".

- Texte clair : pour le texte non code. Hérite du "texte".

- Code: pour le code de toutes sortes. Hérite du "texte".

- Inerte: exclut le texte de tout type de manipulation. Texte de ce type de contenu n’aura jamais aucune extension appliquée à elle.

- Projection : pour le contenu des tampons de projection. Hérite de "n’importe quoi".

- Intellisense: pour le contenu d’IntelliSense. Hérite du "texte".

- Sighelp: aide signature. Hérite de "intellisense".

- Sighelp-doc: documentation d’aide signature. Hérite de "intellisense".

  Ce sont quelques-uns des types de contenu qui sont définis par Visual Studio et certaines des langues qui sont hébergées dans Visual Studio:

- Basic

- C/C++

- ConsoleOutput

- CSharp

- CSS

- Enc

- FindResults (en)

- F#

- HTML

- JScript

- XAML

- XML

  Pour découvrir la liste des types <xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService>de contenu disponibles, importez le , qui maintient la collecte de types de contenu pour l’éditeur. Le code suivant importe ce service comme une propriété.

```
[Import]
internal IContentTypeRegistryService ContentTypeRegistryService { get; set; }
```

 Pour associer un type de contenu <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition>à une extension de nom de fichier, utilisez .

> [!NOTE]
> Dans Visual Studio, les extensions de <xref:Microsoft.VisualStudio.Shell.ProvideLanguageExtensionAttribute> nom de fichier sont enregistrées en utilisant le sur un forfait de service linguistique. L’associe <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> un type de contenu MEF avec une extension de nom de fichier qui a été enregistrée de cette manière.

 Pour exporter l’extension du nom de fichier à la définition de type de contenu, vous devez inclure les attributs suivants :

- <xref:Microsoft.VisualStudio.Utilities.FileExtensionAttribute>: spécifie l’extension du nom du fichier.

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: spécifie le type de contenu.

  Parce <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> que la classe est scellée, vous pouvez l’exporter sans paramètre de type.

  L’exemple suivant montre les attributs d’exportation sur une extension de nom de fichier à une définition de type de contenu.

```
[Export]
[FileExtension(".test")]
[ContentType("test")]
internal static FileExtensionToContentTypeDefinition TestFileExtensionDefinition;
```

 La <xref:Microsoft.VisualStudio.Utilities.IFileExtensionRegistryService> gestion des associations entre les extensions de nom de fichier et les types de contenu.

## <a name="extend-classification-types-and-classification-formats"></a>Étendre les types de classification et les formats de classification
 Vous pouvez utiliser des types de classification pour définir les types de texte pour lesquels vous souhaitez fournir une manipulation différente (par exemple, colorier le texte bleu "mot clé" et le texte "commentaire" vert). Définissez un nouveau type de classification <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeDefinition> en déclarant une variable de type et en lui donnant un nom unique.

 Pour enregistrer le type de classification auprès de l’éditeur, exportez-le avec les attributs suivants :

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: le nom du type de classification.

- <xref:Microsoft.VisualStudio.Utilities.BaseDefinitionAttribute>: le nom du type de classification dont ce type de classification hérite. Tous les types de classification héritent du « texte » et un type de classification peut hériter de plusieurs autres types de classification.

  Parce <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeDefinition> que la classe est scellée, vous pouvez l’exporter sans paramètre de type.

  L’exemple suivant montre les attributs d’exportation sur une définition de type de classification.

```
[Export]
[Name("csharp.test")]
[BaseDefinition("test")]
internal static ClassificationTypeDefinition CSharpTestDefinition;
```

 Le <xref:Microsoft.VisualStudio.Language.StandardClassification.IStandardClassificationService> donne accès à des classifications standard. Les types de classification intégré comprennent les suivants :

- "text"

- "langage naturel" (dérive du "texte")

- "langage formel" (dérive du "texte")

- "corde" (dérive de "littérale")

- "caractère" (dérive de "littérale")

- "numérique" (dérive de "littérale")

  Un ensemble de différents <xref:Microsoft.VisualStudio.Text.Adornments.ErrorTypeDefinition>types d’erreurs héritent de . Ils comprennent les types d’erreurs suivants :

- "erreur de syntaxe"

- "erreur de compilateur"

- "autre erreur"

- "avertissement"

  Pour découvrir la liste des types <xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService>de classification disponibles, importez le , qui maintient la collecte des types de classification pour l’éditeur. Le code suivant importe ce service comme une propriété.

```
[Import]
internal IClassificationTypeRegistryService ClassificationTypeRegistryService { get; set; }
```

 Vous pouvez définir une définition de format de classification pour votre nouveau type de classification. Dérivez une <xref:Microsoft.VisualStudio.Text.Classification.ClassificationFormatDefinition> classe et exportez-la avec le type, <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition>ainsi que les attributs suivants :

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: le nom du format.

- <xref:Microsoft.VisualStudio.Utilities.DisplayNameAttribute>: le nom d’affichage du format.

- <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>: précise si le format apparaît sur la page **Fonts et Couleurs** de la boîte de dialogue **Options.**

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: la priorité du format. Les valeurs <xref:Microsoft.VisualStudio.Text.Classification.Priority>valides sont de .

- <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeAttribute>: le nom du type de classification auquel ce format est cartographié.

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

 Pour découvrir la liste des formats disponibles, importez le <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>, qui maintient la collection de formats pour l’éditeur. Le code suivant importe ce service comme une propriété.

```
[Import]
internal IEditorFormatMapService FormatMapService { get; set; }
```

## <a name="extend-margins-and-scrollbars"></a>Étendre les marges et les barres de défilement
 Les marges et les barres de défilement sont les éléments de vue principal de l’éditeur en plus de la vue de texte elle-même. Vous pouvez fournir n’importe quel nombre de marges en plus des marges standard qui apparaissent autour de la vue de texte.

 Implémentez une <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMargin> interface pour définir une marge. Vous devez également <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMarginProvider> implémenter l’interface pour créer la marge.

 Pour enregistrer le fournisseur de marge auprès de l’éditeur, vous devez exporter le fournisseur avec les attributs suivants :

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: le nom de la marge.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: l’ordre dans lequel la marge apparaît, par rapport aux autres marges.

   Voici les marges intégrées :

  - "Wpf Horizontal Scrollbar"

  - "Wpf Vertical Scrollbar"

  - "Wpf Line Number Margin"

    Les marges horizontales dont `After="Wpf Horizontal Scrollbar"` l’attribut d’ordre est affiché en dessous de `Before ="Wpf Horizontal Scrollbar"` la marge intégrée, et les marges horizontales dont l’attribut d’ordre est affichée au-dessus de la marge intégrée. Les marges verticales droites `After="Wpf Vertical Scrollbar"` qui ont un attribut d’ordre sont affichées à droite de la barre de défilement. Les marges verticales gauches `After="Wpf Line Number Margin"` qui ont un attribut d’ordre d’apparaître à gauche de la marge de numéro de ligne (si elle est visible).

- <xref:Microsoft.VisualStudio.Text.Editor.MarginContainerAttribute>: le type de marge (gauche, droite, en haut ou en bas).

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: le type de contenu (par exemple, "texte" ou "code") pour lequel votre marge est valide.

  L’exemple suivant montre les attributs d’exportation sur un fournisseur de marge pour une marge qui apparaît à droite de la marge de numéro de ligne.

```
[Export(typeof(IWpfTextViewMarginProvider))]
[Name("TestMargin")]
[Order(Before = "Wpf Line Number Margin")]
[MarginContainer(PredefinedMarginNames.Left)]
[ContentType("text")]
```

## <a name="extend-tags"></a>Étendre les balises
 Les balises sont un moyen d’associer les données à différents types de texte. Dans de nombreux cas, les données associées sont affichées comme un effet visuel, mais pas toutes les balises ont une présentation visuelle. Vous pouvez définir votre propre type <xref:Microsoft.VisualStudio.Text.Tagging.ITag>d’étiquette en implémentant . Vous devez <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> également implémenter pour fournir les balises pour un ensemble donné de travées de texte, et un <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider> pour fournir le tagger. Vous devez exporter le fournisseur de tagger avec les attributs suivants :

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: le type de contenu (par exemple, "texte" ou "code") pour lequel votre balise est valide.

- <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>: le genre d’étiquette.

  L’exemple suivant montre les attributs d’exportation sur un fournisseur de tagger.

\<CodeContentPlaceHolder>8</CodeContentPlaceHolder> Les types d’étiquettes suivants sont intégrés :

- <xref:Microsoft.VisualStudio.Text.Tagging.ClassificationTag>: associé <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType>à un .

- <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>: associé à des types d’erreurs.

- <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>: associé à une parure.

  > [!NOTE]
  > Par exemple, <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>voir la définition HighlightWordTag dans [Walkthrough: Highlighting Text](../extensibility/walkthrough-highlighting-text.md).

- <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag>: associés à des régions qui peuvent être élargies ou effondrées dans la mise en ligne.

- <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>: définit l’espace qu’une parure occupe dans une vue textuelle. Pour plus d’informations sur les ornements de négociation spatiale, voir la section suivante.

- <xref:Microsoft.VisualStudio.Text.Editor.IntraTextAdornmentTag>: fournit un espacement et un dimensionnement automatiques pour la parure.

  Pour trouver et utiliser des balises <xref:Microsoft.VisualStudio.Text.Tagging.IViewTagAggregatorFactoryService> pour <xref:Microsoft.VisualStudio.Text.Tagging.IBufferTagAggregatorFactoryService>les tampons <xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601> et les vues, importez le ou le , qui vous donnent un du type demandé. Le code suivant importe ce service comme une propriété.

```
[Import]
internal IViewTagAggregatorFactoryService ViewTagAggregatorFactoryService { get; set; }
```

#### <a name="tags-and-markerformatdefinitions"></a>Tags et MarkerFormatDéfinitions
 Vous pouvez <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition> étendre la classe pour définir l’apparence d’une balise. Vous devez exporter votre <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition>classe (en tant que) avec les attributs suivants :

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: le nom utilisé pour référencer ce format

- <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>: cela provoque l’apparition du format dans l’interface utilisateur

  Dans le constructeur, vous définissez le nom d’affichage et l’apparence de l’étiquette. <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.BackgroundColor%2A>définit la couleur de <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.ForegroundColor%2A> remplissage, et définit la couleur de la frontière. Le <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.DisplayName%2A> est le nom localisable de la définition de format.

  Voici un exemple de définition de format :

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

 Pour appliquer cette définition de format à une balise, faites référence au nom que vous définissez dans l’attribut nom de la classe (et non au nom d’affichage).

> [!NOTE]
> Par exemple, <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition>voir la classe HighlightWordFormatDefinition dans [Walkthrough: Highlighting Text](../extensibility/walkthrough-highlighting-text.md).

## <a name="extend-adornments"></a>Étendre les parures
 Les ornements définissent les effets visuels qui peuvent être ajoutés soit au texte qui est affiché dans une vue de texte ou à la vue de texte elle-même. Vous pouvez définir votre propre ornement <xref:System.Windows.UIElement>comme n’importe quel type de .

 Dans votre cours d’ornement, <xref:Microsoft.VisualStudio.Text.Editor.AdornmentLayerDefinition>vous devez déclarer un . Pour enregistrer votre couche d’ornement, exportez-la avec les attributs suivants :

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: le nom de la parure.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: la commande de la parure par rapport à d’autres couches d’ornement. La <xref:Microsoft.VisualStudio.Text.Editor.PredefinedAdornmentLayers> classe définit quatre couches par défaut : Sélection, Décrivant, Caret et Texte.

  L’exemple suivant montre les attributs d’exportation sur une définition de couche d’ornement.

```
[Export]
[Name("TestEmbeddedAdornment")]
[Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]
internal AdornmentLayerDefinition testLayerDefinition;
```

 Vous devez créer une deuxième <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> classe qui <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> met en œuvre et gère son événement en instantanéisant la parure. Vous devez exporter cette classe avec les attributs suivants :

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: le type de contenu (par exemple, "texte" ou "code") pour lequel la parure est valide.

- <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>: le type de vue de texte pour laquelle cette parure est valide. La <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles> classe a l’ensemble des rôles de vue de texte prédéfinis. Par exemple, <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document> est principalement utilisé pour les vues textuelles des fichiers. <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive>est utilisé pour les vues de texte qu’un utilisateur peut modifier ou naviguer à l’aide d’une souris et d’un clavier. Des <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> exemples de vues sont la vue de texte de l’éditeur et la fenêtre **de sortie.**

  L’exemple suivant montre des attributs d’exportation sur le fournisseur d’ornements.

```
[Export(typeof(IWpfTextViewCreationListener))]
[ContentType("csharp")]
[TextViewRole(PredefinedTextViewRoles.Document)]
internal sealed class TestAdornmentProvider : IWpfTextViewCreationListener
```

 Une parure de négociation d’espace est celle qui occupe l’espace au même niveau que le texte. Pour créer ce genre d’ornement, vous devez définir <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>une classe d’étiquettes qui hérite de , qui définit la quantité d’espace que la parure occupe.

 Comme avec toutes les parures, vous devez exporter la définition de couche d’ornement.

```
[Export]
[Name("TestAdornment")]
[Order(After = DefaultAdornmentLayers.Text)]
internal AdornmentLayerDefinition testAdornmentLayer;
```

 Pour instantanéer l’ornement de négociation d’espace, vous <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>devez créer une classe qui <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> met en œuvre , en plus de la classe qui met en œuvre (comme avec d’autres types de ornements).

 Pour enregistrer le fournisseur de tagger, vous devez l’exporter avec les attributs suivants :

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: le type de contenu (par exemple, "texte" ou "code") pour lequel votre ornement est valide.

- <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>: le type de vue de texte pour laquelle cette étiquette ou ornement est valide. La <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles> classe a l’ensemble des rôles de vue de texte prédéfinis. Par exemple, <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document> est principalement utilisé pour les vues textuelles des fichiers. <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive>est utilisé pour les vues de texte qu’un utilisateur peut modifier ou naviguer à l’aide d’une souris et d’un clavier. Des <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> exemples de vues sont la vue de texte de l’éditeur et la fenêtre **de sortie.**

- <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>: le genre d’étiquette ou d’ornement que vous avez défini. Vous devez ajouter <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>une seconde pour .

  L’exemple suivant montre des attributs d’exportation sur le fournisseur de tagger pour une étiquette d’ornement de négociation d’espace.

```
[Export(typeof(ITaggerProvider))]
[ContentType("text")]
[TextViewRole(PredefinedTextViewRoles.Document)]
[TagType(typeof(SpaceNegotiatingAdornmentTag))]
[TagType(typeof(TestSpaceNegotiatingTag))]
internal sealed class TestTaggerProvider : ITaggerProvider
```

## <a name="extending-mouse-processors"></a>Extension des processeurs de souris
 Vous pouvez ajouter une manipulation spéciale pour l’entrée de la souris. Créez une classe qui <xref:Microsoft.VisualStudio.Text.Editor.MouseProcessorBase> hérite des événements de souris et l’emporte sur les événements de souris pour l’entrée que vous souhaitez gérer. Vous devez <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessorProvider> également implémenter en deuxième <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> classe et l’exporter en même temps que le type de contenu (par exemple, "texte" ou "code") pour lequel votre gestionnaire de souris est valide.

 L’exemple suivant montre les attributs d’exportation sur un fournisseur de processeur de souris.

```
[Export(typeof(IMouseProcessorProvider))]
[Name("test mouse processor")]
[ContentType("text")]
[TextViewRole(PredefinedTextViewRoles.Interactive)]
internal sealed class TestMouseProcessorProvider : IMouseProcessorProvider
```

## <a name="extend-drop-handlers"></a>Étendre les gestionnaires de goutte
 Vous pouvez personnaliser le comportement des gestionnaires de drop pour des <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.IDropHandler> types spécifiques de texte <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.IDropHandlerProvider> en créant une classe qui implémente et une deuxième classe qui implémente pour créer le gestionnaire de goutte. Vous devez exporter le maître-goutte avec les attributs suivants :

- <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.DropFormatAttribute>: le format texte pour lequel ce maître-goutte est valide. Les formats suivants sont traités dans l’ordre prioritaire du plus haut au plus bas :

  1. N’importe quel format personnalisé

  2. FichierDrop

  3. EnhancedMetafile (en)

  4. WaveAudio

  5. Riff

  6. Dif

  7. Paramètres régionaux

  8. Palette

  9. PenData PenData

  10. Sérialisable

  11. SymbolicLink (en)

  12. Xaml

  13. XamlPackage XamlPackage

  14. TIFF

  15. Bitmap

  16. Dib

  17. MetafilePicture

  18. CSV

  19. System.String

  20. HTML Format

  21. UnicodeText

  22. OEMText

  23. Texte

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: le nom du maître-goutte.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: la commande du gestionnaire de largage avant ou après le gestionnaire de drop par défaut. Le gestionnaire de drop par défaut pour Visual Studio s’appelle "DefaultFileDropHandler".

  L’exemple suivant montre les attributs d’exportation sur un fournisseur de manutention de drop.

```
[Export(typeof(IDropHandlerProvider))]
[DropFormat("Text")]
[Name("TestDropHandler")]
[Order(Before="DefaultFileDropHandler")]
internal class TestDropHandlerProvider : IDropHandlerProvider
```

## <a name="extending-editor-options"></a>Élargir les options d’éditeur
 Vous pouvez définir des options qui ne sont valables que dans une certaine portée, par exemple, dans une vue textuelle. L’éditeur fournit cet ensemble d’options prédéfinies : options d’éditeur, options de vue et options de vue de la Fondation de présentation Windows (WPF). Ces options peuvent <xref:Microsoft.VisualStudio.Text.Editor.DefaultOptions>être <xref:Microsoft.VisualStudio.Text.Editor.DefaultTextViewOptions>trouvées dans , , et <xref:Microsoft.VisualStudio.Text.Editor.DefaultWpfViewOptions>.

 Pour ajouter une nouvelle option, tirer une classe de l’une de ces classes de définition d’option :

- <xref:Microsoft.VisualStudio.Text.Editor.EditorOptionDefinition%601>

- <xref:Microsoft.VisualStudio.Text.Editor.ViewOptionDefinition%601>

- <xref:Microsoft.VisualStudio.Text.Editor.WpfViewOptionDefinition%601>

  L’exemple suivant montre comment exporter une définition d’option qui a une valeur Boolean.

```
[Export(typeof(EditorOptionDefinition))]
internal sealed class TestOption : EditorOptionDefinition<bool>
```

## <a name="extend-intellisense"></a>Étendre IntelliSense
 IntelliSense est un terme général pour un groupe de fonctionnalités qui fournissent des informations sur le texte structuré, et l’achèvement de l’instruction pour elle. Ces caractéristiques comprennent l’achèvement de l’instruction, l’aide à la signature, Quick Info et les ampoules. L’achèvement de l’énoncé aide les utilisateurs à taper correctement un mot clé de langue ou un nom de membre. Signature aide affiche la signature ou les signatures pour la méthode que l’utilisateur vient d’taper. Quick Info affiche une signature complète pour un type ou un nom de membre lorsque la souris se repose dessus. L’ampoule fournit des actions supplémentaires pour certains identificateurs dans certains contextes, par exemple, renommant tous les événements d’une variable après qu’un événement a été renommé.

 La conception d’une fonctionnalité IntelliSense est à peu près la même dans tous les cas:

- Un *courtier* IntelliSense est responsable de l’ensemble du processus.

- Une *session* IntelliSense représente la séquence des événements entre le déclenchement du présentateur et l’incarcération ou l’annulation de la sélection. La session est généralement déclenchée par un geste de l’utilisateur.

- Un *contrôleur* IntelliSense est chargé de décider quand la session doit commencer et se terminer. Il décide également quand l’information doit être validée et quand la session doit être annulée.

- Une *source* IntelliSense fournit le contenu et décide du meilleur match.

- Un *présentateur* d’IntelliSense est responsable de l’affichage du contenu.

  Dans la plupart des cas, nous vous recommandons de fournir au moins une source et un contrôleur. Vous pouvez également fournir un présentateur si vous souhaitez personnaliser l’affichage.

### <a name="implement-an-intellisense-source"></a>Mettre en œuvre une source IntelliSense
 Pour personnaliser une source, vous devez implémenter une (ou plusieurs) des interfaces sources suivantes :

- <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource>

- <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource>

- <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource>

- <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>

> [!IMPORTANT]
> <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagSource>a été déprécié <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>en faveur de .

 En outre, vous devez implémenter un fournisseur du même type :

- <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider>

- <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider>

- <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider>

- <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>

> [!IMPORTANT]
> <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagSourceProvider>a été déprécié <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>en faveur de .

 Vous devez exporter le fournisseur avec les attributs suivants :

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: le nom de la source.

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: le type de contenu (par exemple, "texte" ou "code") auquel la source s’applique.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: l’ordre dans lequel la source doit apparaître (en ce qui concerne d’autres sources).

- L’exemple suivant montre les attributs d’exportation sur un fournisseur de source d’achèvement.

```
Export(typeof(ICompletionSourceProvider))]
[Name(" Test Statement Completion Provider")]
[Order(Before = "default")]
[ContentType("text")]
internal class TestCompletionSourceProvider : ICompletionSourceProvider
```

 Pour plus d’informations sur la mise en œuvre des sources IntelliSense, voir les procédures à pas suivantes:

- [Procédure pas à pas: Afficher des outils QuickInfo](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)

- [Procédure pas à pas : Offrez l’aide signature d’affichage](../extensibility/walkthrough-displaying-signature-help.md)

- [Procédure pas à pas : afficher la saisie semi-automatique des instructions](../extensibility/walkthrough-displaying-statement-completion.md)

### <a name="implement-an-intellisense-controller"></a>Mettre en œuvre un contrôleur IntelliSense
 Pour personnaliser un contrôleur, vous <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController> devez implémenter l’interface. En outre, vous devez implémenter un fournisseur de contrôleurs avec les attributs suivants :

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: le nom du contrôleur.

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: le type de contenu (par exemple, "texte" ou "code") auquel le contrôleur s’applique.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: l’ordre dans lequel le contrôleur doit apparaître (par rapport à d’autres contrôleurs).

  L’exemple suivant montre les attributs d’exportation sur un fournisseur de contrôleur d’achèvement.

```
Export(typeof(IIntellisenseControllerProvider))]
[Name(" Test Controller Provider")]
[Order(Before = "default")]
[ContentType("text")]
internal class TestIntellisenseControllerProvider : IIntellisenseControllerProvider
```

 Pour plus d’informations sur l’utilisation des contrôleurs IntelliSense, voir les procédures à pas suivantes :

- [Procédure pas à pas: Afficher des outils QuickInfo](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)
