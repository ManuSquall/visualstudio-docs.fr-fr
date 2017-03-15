---
title: "Dans l’&#233;diteur | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "éditeurs (Visual Studio SDK), nouvelles - architecture"
ms.assetid: 822cbb8d-7ab4-40ee-bd12-44016ebcce81
caps.latest.revision: 31
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 31
---
# Dans l’&#233;diteur
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L’éditeur est composée d’un nombre de différents sous\-systèmes, qui sont conçues pour conserver l’éditeur de texte modèle distinct à partir de l’affichage de texte et l’interface utilisateur.  
  
 Les sections suivantes décrivent les différents aspects de l’éditeur :  
  
-   [Vue d’ensemble des sous-systèmes](../extensibility/inside-the-editor.md#overview)  
  
-   [Le modèle de texte](../extensibility/inside-the-editor.md#textmodel)  
  
-   [L’affichage de texte](../extensibility/inside-the-editor.md#textview)  
  
 Les sections suivantes décrivent les fonctionnalités de l’éditeur :  
  
-   [Les balises et les classifieurs](../extensibility/inside-the-editor.md#tagsandclassifiers)  
  
-   [Ornements](../extensibility/inside-the-editor.md#adornments)  
  
-   [Projection](../extensibility/inside-the-editor.md#projection)  
  
-   [Mode Plan](../extensibility/inside-the-editor.md#outlining)  
  
-   [Liaisons de la souris](../extensibility/inside-the-editor.md#mousebindings)  
  
-   [Opérations de l’éditeur](../extensibility/inside-the-editor.md#editoroperations)  
  
-   [IntelliSense](../extensibility/inside-the-editor.md#intellisense)  
  
##  <a name="overview"></a> Vue d’ensemble des sous\-systèmes  
  
### Sous\-système de modèle de texte  
 Le sous\-système de modèle de texte est chargé de représenter le texte et l’activation de sa manipulation. Le sous\-système de modèle de texte contient le <xref:Microsoft.VisualStudio.Text.ITextBuffer> interface, qui décrit la séquence de caractères qui doit être affichée par l’éditeur. Ce texte peut être modifié, suivi et manipulé de différentes façons. Le modèle de texte fournit également des types pour les aspects suivants :  
  
-   Un service qui associe le texte avec des fichiers et gère la lecture et de les écrire dans le système de fichiers.  
  
-   Un service de différenciation qui recherche les différences entre deux séquences d’objets minimales.  
  
-   Un système qui décrit le texte dans une mémoire tampon en termes de sous\-ensembles du texte dans les autres mémoires tampons.  
  
 Le sous\-système de modèle de texte est libre de concepts d’interface graphique utilisateur. Par exemple, il n’est pas responsable de la mise en forme du texte ou à la disposition du texte, et il ne connaît pas d’ornements visuels qui peuvent être associés à du texte.  
  
 Les types publics du sous\-système de modèle de texte sont contenus dans Microsoft.VisualStudio.Text.Data.dll et Microsoft.VisualStudio.CoreUtilitiy.dll, qui dépendent uniquement de la bibliothèque de classes de base .NET Framework et Managed Extensibility Framework \(MEF\).  
  
### Sous\-système d’affichage de texte  
 Le sous\-système d’affichage de texte est responsable de la mise en forme et l’affichage du texte. Les types de ce sous\-système sont divisées en deux couches, selon que les types s’appuient sur Windows Presentation Foundation \(WPF\). Les types les plus importants sont <xref:Microsoft.VisualStudio.Text.Editor.ITextView> et <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>, qui contrôle l’ensemble de lignes de texte qui doivent être affichées, et également le point d’insertion, la sélection et les fonctionnalités pour agrémenter le texte à l’aide des éléments de WPF UI. Ce sous\-système fournit également des marges autour du texte de zone d’affichage. Ces marges peuvent être étendues et peuvent contenir différents types d’effets de contenu et de visual. Ligne numéro s’affiche et barres de défilement sont des exemples des marges.  
  
 Les types publics du sous\-système d’affichage de texte sont contenus dans Microsoft.VisualStudio.Text.UI.dll et Microsoft.VisualStudio.Text.UI.Wpf.dll. Le premier assembly contient les éléments d’indépendant de la plate\-forme et le second contient les éléments spécifiques à WPF.  
  
### Sous\-système de classification  
 Le sous\-système de classification est chargé de déterminer les propriétés de police du texte. Un classifieur fractionne le texte en différentes classes, par exemple, « mot clé » ou « commentaire ». Le mappage de format de classification lie ces classes pour les propriétés de police réelle, par exemple, « bleu Consolas 10 pt ». Ces informations sont utilisées par l’affichage de texte lorsqu’il met en forme et restitue le texte. Balisage, qui est décrit plus en détail plus loin dans cette rubrique, permet d’associer à des étendues de texte.  
  
 Les types publics du sous\-système de classification sont contenus dans Microsoft.VisualStudio.Text.Logic.dll, et ils interagissent avec les aspects visuels de la classification, qui sont contenues dans Microsoft.VisualStudio.Text.UI.Wpf.dll.  
  
### Sous\-système d’opérations  
 Le sous\-système d’opérations définit le comportement de l’éditeur. Il fournit l’implémentation pour les commandes de l’éditeur Visual Studio et le système d’annulation.  
  
## Examinez de plus près le modèle de texte et l’affichage de texte  
  
###  <a name="textmodel"></a> Le modèle de texte  
 Le sous\-système de modèle de texte se compose de différents groupes de types de texte. Ceux\-ci incluent la mémoire tampon de texte, les instantanés de texte et les étendues de texte.  
  
#### Mémoires tampons de texte et les instantanés de texte  
 Le <xref:Microsoft.VisualStudio.Text.ITextBuffer> interface représente une séquence de caractères Unicode qui sont codés en UTF\-16, qui est l’encodage utilisé par le `String` type dans le .NET Framework. Mémoire tampon de texte peut être rendu persistant comme un document de système de fichiers, mais cela n’est pas nécessaire.  
  
 Le <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService> est utilisé pour créer un tampon de texte vide, ou une mémoire tampon de texte qui est initialisée à partir d’une chaîne ou de <xref:System.IO.TextReader>. La mémoire tampon de texte peut être rendu persistant dans le système de fichiers comme un <xref:Microsoft.VisualStudio.Text.ITextDocument>.  
  
 La mémoire tampon de texte peut être modifié par n’importe quel thread jusqu'à ce qu’un thread a s’approprie le tampon de texte en appelant <xref:Microsoft.VisualStudio.Text.ITextBuffer.TakeThreadOwnership%2A>. Après cela, seul ce thread peut apporter des modifications.  
  
 Mémoire tampon de texte peut passer par plusieurs versions pendant sa durée de vie. Une nouvelle version est générée chaque fois que la mémoire tampon est modifiée et qu’un immuable <xref:Microsoft.VisualStudio.Text.ITextSnapshot> représente le contenu de cette version de la mémoire tampon. Étant donné que les instantanés de texte sont immuables, vous pouvez accéder un instantané de texte sur n’importe quel thread, sans restriction, même si la mémoire tampon qu’elle représente continue d’être modifié.  
  
#### Instantanés de texte et lignes de capture instantanée de texte  
 Vous pouvez afficher le contenu d’un instantané de texte sous la forme d’une séquence de caractères ou une séquence de lignes. Caractères et les lignes sont que tous deux indexées à partir de zéro. Un instantané de texte vide contient zéro caractères et une ligne vide. Une ligne est délimitée par une séquence de caractères de saut de ligne Unicode valide, ou par le début ou la fin de la mémoire tampon. Caractères de saut de ligne sont explicitement représentées dans l’instantané de texte et les sauts de ligne dans un instantané de texte ne possèdent pas les mêmes.  
  
> [!NOTE]
>  Pour plus d’informations sur les caractères de saut de ligne dans l’éditeur Visual Studio, consultez [Encodages et sauts de ligne](../ide/encodings-and-line-breaks.md).  
  
 Une ligne de texte est représentée par un <xref:Microsoft.VisualStudio.Text.ITextSnapshotLine> objet, qui peut être obtenu à partir d’un instantané de texte pour un numéro de ligne particulier ou pour un caractère particulier.  
  
#### SnapshotPoints, SnapshotSpans et NormalizedSnapshotSpanCollections  
 Un <xref:Microsoft.VisualStudio.Text.SnapshotPoint> représente une position de caractère dans un instantané. La position est garantie être comprise entre zéro et la longueur de l’instantané. Un <xref:Microsoft.VisualStudio.Text.SnapshotSpan> représente une plage de texte dans un instantané. Sa position de fin est garantie être comprise entre zéro et la longueur de l’instantané. Le <xref:Microsoft.VisualStudio.Text.NormalizedSnapshotSpanCollection> se compose d’un ensemble de <xref:Microsoft.VisualStudio.Text.SnapshotSpan> objets à partir du même instantané.  
  
#### Étendues et NormalizedSpanCollections  
 Un <xref:Microsoft.VisualStudio.Text.Span> représente un intervalle qui peut être appliqué à une plage de texte dans un instantané de texte. Les positions de capture instantanée commencent à zéro, afin de commencer à toute position zéro compris étendues. Le `End` la propriété d’une plage est égale à la somme de ses `Start` propriété et son `Length` propriété. Un `Span` n’inclut pas le caractère qui est indexé par le `End` propriété. Par exemple, une étendue qui a \= 5 et longueur \= 3 a fin \= 8, et elle inclut les caractères aux positions 5, 6 et 7. La notation pour cette étendue est 5..8\).  
  
 Deux étendues se croisent si elles ont des positions en commun, y compris la position de fin. Par conséquent, l’intersection de \[3, 5\) et \[2, 7\) est \[3, 5\) et l’intersection des \[3, 5\) et \[5, 7\) est \[5, 5\). \(Notez que \[5, 5\) est une plage vide.\)  
  
 Deux étendues se chevauchent si elles ont des positions en commun, à l’exception de la position de fin. Une étendue vide chevauche jamais d’autres étendues, et le chevauchement de deux étendues n’est jamais vide.  
  
 Un <xref:Microsoft.VisualStudio.Text.NormalizedSpanCollection> est une liste d’étendues dans l’ordre les propriétés de démarrage des étendues. Dans la liste, qui se chevauchent ou attenants étendues sont fusionnée. Par exemple, étant donné le jeu d’étendues de \[5..9\), \[0..1\), \[3..6\), et \[9..10\), la liste d’étendues normalisée est \[0..1\), \[3..10\).  
  
#### ITextEdit, TextVersion et les Notifications de modification de texte  
 Le contenu de la mémoire tampon de texte peut être modifié en utilisant un <xref:Microsoft.VisualStudio.Text.ITextEdit> objet. Création d’un tel objet \(en utilisant l’une de le `CreateEdit()` méthodes de <xref:Microsoft.VisualStudio.Text.ITextBuffer>\) démarre une transaction de texte qui se compose de modifications de texte. Chaque modification est un remplacement d’une plage de texte dans la mémoire tampon en une chaîne. Les coordonnées et le contenu de chaque modification sont exprimées par rapport à l’instantané de la mémoire tampon lors de la transaction. Le <xref:Microsoft.VisualStudio.Text.ITextEdit> objet ajuste les coordonnées de modifications qui sont affectées par d’autres modifications dans la même transaction.  
  
 Par exemple, considérez une mémoire tampon de texte qui contient cette chaîne :  
  
```  
abcdefghij  
```  
  
 Appliquer une transaction qui contient deux modifications, une modification qui remplace l’étendue à \[2..4\) en utilisant le caractère `X` et une seconde Edition qui remplace l’étendue à \[6..9\) en utilisant le caractère `Y`. Le résultat est cette mémoire tampon :  
  
```  
abXefYj  
```  
  
 Les coordonnées de la deuxième modification ont été calculées en ce qui concerne le contenu de la mémoire tampon au début de la transaction, avant la première modification a été appliquée.  
  
 Les modifications apportées à la mémoire tampon prennent effet lors de la <xref:Microsoft.VisualStudio.Text.ITextEdit> objet est validé en appelant son `Apply()` \(méthode\). S’il y a au moins une modification non vide, un nouveau <xref:Microsoft.VisualStudio.Text.ITextVersion> est créée, un nouveau <xref:Microsoft.VisualStudio.Text.ITextSnapshot> est créé et un `Changed` événement est déclenché. Chaque version de texte comporte un autre instantané de texte. Un instantané de texte représente l’état complet de la mémoire tampon de texte après une transaction de modification, mais une version texte décrit uniquement les modifications d’un instantané à l’autre. En général, les instantanés de texte sont destinés à être utilisés qu’une seule fois et ensuite ignorés, alors que les versions de texte doivent rester actives pendant un certain temps.  
  
 Une version texte contient un <xref:Microsoft.VisualStudio.Text.INormalizedTextChangeCollection>. Cette collection décrit les modifications qui, lorsqu’il est appliqué à l’instantané, génère l’instantané suivant. Chaque <xref:Microsoft.VisualStudio.Text.ITextChange> dans la collection contient la position de caractère de la chaîne de remplacement, la modification et la chaîne remplacée. La chaîne de remplacement est vide pour une insertion de base, et la chaîne de remplacement est vide pour une suppression de base. La collection normalisée est toujours `null` pour la version la plus récente de la mémoire tampon de texte.  
  
 Seul <xref:Microsoft.VisualStudio.Text.ITextEdit> objet peut être instancié pour une mémoire tampon de texte à tout moment, et toutes les modifications de texte doivent être effectuées sur le thread qui détient la mémoire tampon \(si la propriété a été déclarée\). Une modification de texte peut être abandonnée en appelant son `Cancel` méthode ou son `Dispose` \(méthode\).  
  
 <xref:Microsoft.VisualStudio.Text.ITextBuffer> fournit également `Insert()`, `Delete()`, et `Replace()` méthodes semblables à celles disponibles sur le <xref:Microsoft.VisualStudio.Text.ITextEdit> interface. L’appel à ces a le même effet que la création d’un <xref:Microsoft.VisualStudio.Text.ITextEdit> objet, l’appel semblable et en appliquant la modification.  
  
#### Points de suivi et de suivi  
 Un <xref:Microsoft.VisualStudio.Text.ITrackingPoint> représente une position de caractère dans la mémoire tampon de texte. Si la mémoire tampon est modifiée d’une manière qui entraîne la position du caractère à déplacer, le point de suivi se déplace avec lui. Par exemple, si un point de suivi fait référence à la position 10 dans une mémoire tampon et cinq caractères sont insérés au début de la mémoire tampon, le point de suivi, fait référence à la position 15. Si une insertion se produit précisément la position désignée par le point de suivi, son comportement est déterminé par ses <xref:Microsoft.VisualStudio.Text.PointTrackingMode>, qui peut être `Positive` ou `Negative`. Si le mode de suivi est positif, que le point de suivi fait référence au même caractère, qui est maintenant disponible à la fin de l’insertion ; Si le mode de suivi est négatif, le point de suivi fait référence au premier caractère inséré à la position d’origine. Si le caractère situé à la position qui est représenté par un point de suivi est supprimé, le point de suivi se déplace vers le premier caractère qui suit la plage supprimée. Par exemple, si un point de suivi fait référence au caractère à la position 5 et les caractères 3 à 6 positions sont supprimés, le point de suivi fait référence au caractère à la position 3.  
  
 Un <xref:Microsoft.VisualStudio.Text.ITrackingSpan> représente une plage de caractères au lieu de simplement une position. Son comportement est déterminé par ses <xref:Microsoft.VisualStudio.Text.SpanTrackingMode>. Si le mode de suivi span est <xref:Microsoft.VisualStudio.Text.SpanTrackingMode>, l’étendue de suivi s’agrandit pour incorporer le texte inséré à ses bords ; si le mode de suivi span est <xref:Microsoft.VisualStudio.Text.SpanTrackingMode>, l’étendue de suivi ne comporte pas de texte insérée sur ses bords. Toutefois, si le mode de suivi span est <xref:Microsoft.VisualStudio.Text.SpanTrackingMode>, d’insertion exécute un push de la position actuelle vers le début et si le mode de suivi span <xref:Microsoft.VisualStudio.Text.SpanTrackingMode>, d’insertion exécute un push de la position actuelle vers la fin.  
  
 Vous pouvez obtenir la position d’un point de suivi ou de l’étendue d’une étendue de suivi pour tous les instantanés de la mémoire tampon de texte auquel elles appartiennent. Points de suivi et de suivi peuvent être référencées en toute sécurité à partir de n’importe quel thread.  
  
#### Types de contenu  
 Types de contenu sont un mécanisme permettant de définir différents types de contenu. Un type de contenu peut être un type de fichier tel que « text », « code » ou « binaire », ou un type de technologie tels que « xml », « vb » ou « c\# ». Par exemple, le mot « using » est un mot clé en c\# et Visual Basic, mais pas dans d’autres langages de programmation. Par conséquent, la définition de ce mot clé serait limitée aux types de contenu « c\# » et « vb ».  
  
 Types de contenu sont utilisés en tant que filtre pour les ornements et d’autres éléments de l’éditeur. Plusieurs fonctionnalités de l’éditeur et les points d’extension sont définies par le type de contenu ; par exemple, coloration du texte est différent pour les fichiers de texte brut, les fichiers XML et les fichiers de code source Visual Basic. Mémoires tampons de texte prennent généralement un type de contenu lorsqu’ils sont créés, et le type de contenu de la mémoire tampon de texte peut être modifié.  
  
 Types de contenu peuvent multiple\-hériter d’autres types de contenu. Le <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> vous permet de spécifier plusieurs types de base en tant que les parents d’un type de contenu donné.  
  
 Les développeurs peuvent définir leurs propres types de contenu et les enregistrer à l’aide de la <xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService>. Plusieurs fonctionnalités de l’éditeur peuvent être définies par rapport à un type de contenu spécifique à l’aide de la <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>. Par exemple, les marges d’éditeur, motifs et les gestionnaires de la souris peuvent être définies afin qu’ils s’appliquent uniquement aux éditeurs qui affichent des types de contenu particuliers.  
  
###  <a name="textview"></a> L’affichage de texte  
 La partie de la vue du modèle model view controller \(MVC\) définit l’affichage de texte, la mise en forme de la vue, des éléments graphiques tels que la barre de défilement et le point d’insertion. Tous les éléments de présentation de l’éditeur de Visual Studio sont basés sur WPF.  
  
#### Affichages de texte  
 Le <xref:Microsoft.VisualStudio.Text.Editor.ITextView> interface est une représentation indépendante de la plate\-forme d’une vue de texte. Elle sert principalement à afficher des documents de texte dans une fenêtre, mais il peut également être utilisé à d’autres fins, par exemple, dans une info\-bulle.  
  
 La vue fait référence à différents types de mémoires tampons de texte. Le <xref:Microsoft.VisualStudio.Text.Editor.ITextView.TextViewModel%2A> propriété fait référence à un <xref:Microsoft.VisualStudio.Text.Editor.ITextViewModel> objet qui pointe vers ces trois mémoires tampons de texte différente : le tampon de données, c'est\-à\-dire au niveau des données de mémoire tampon supérieure, le tampon d’édition, où les modifications se produit et la mémoire tampon visuelle, qui est la mémoire tampon qui est affichée dans la vue de texte.  
  
 Le texte est mis en forme en fonction de classifieurs associés à la mémoire tampon sous\-jacente et est agrémenté en utilisant les fournisseurs d’ornements sont attachés à la vue de texte lui\-même.  
  
#### Le système de coordonnées de vue de texte  
 Le système de coordonnées de vue de texte spécifie des positions dans la vue de texte. Dans ce système de coordonnées, la x valeur 0.0 correspond et le bord gauche du texte affiché et le y valeur 0.0 correspond et le bord supérieur du texte affiché. La x coordonnée augmente de gauche à droite et la y coordonnée augmente de haut en bas.  
  
 Une fenêtre d’affichage \(la partie du texte visible dans la fenêtre texte\) ne peut pas faire défiler horizontalement de la même manière qu’il défile verticalement. Une fenêtre d’affichage défilement horizontal en modifiant sa coordonnée gauche afin qu’il se déplace en ce qui concerne la surface de dessin. Toutefois, une fenêtre d’affichage peut défiler verticalement qu’en modifiant le texte affiché, ce qui entraîne une <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> événement soit déclenché.  
  
 Les distances dans le système de coordonnées correspondent aux pixels logiques. Si la surface de rendu de texte s’affiche sans échelle, une unité dans le système de coordonnées de rendu de texte correspond à un pixel dans l’affichage.  
  
#### Marges  
 Le <xref:Microsoft.VisualStudio.Text.Editor.ITextViewMargin> interface représente une marge et permet de contrôler la visibilité de la marge et sa taille. Il existe quatre marges prédéfinis, qui sont nommés « Top », « Gauche », « Droite » et « Bas » et associés au haut, bas, gauche ou droite d’une vue. Ces marges sont des conteneurs dans lesquels les autres marges peuvent être placés. L’interface définit les méthodes qui retournent la taille de la marge et la visibilité d’une marge. Les marges sont des éléments visuels qui fournissent des informations supplémentaires sur l’affichage de texte auquel ils sont associés. Par exemple, la marge de numéro de ligne affiche les numéros de ligne pour la vue de texte. La marge de glyphe affiche les éléments d’interface utilisateur.  
  
 Le <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMarginProvider> interface gère la création et le positionnement des marges. Les marges peuvent être classées en ce qui concerne les autres marges. Marges de priorité plus élevée se trouvent plus proche pour l’affichage de texte. Par exemple, s’il existe deux marges de gauche, marge A et B de marge et marge B a une priorité inférieure à la marge A, marge B s’affiche à gauche de la marge A.  
  
#### L’hôte d’affichage de texte  
 Le <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> interface contient la vue de texte et les décorations attenants qui accompagnent la vue, par exemple, les barres de défilement. L’hôte de vue de texte contient également les marges qui sont attachés à une bordure de la vue.  
  
#### Texte mis en forme  
 Le texte qui s’affiche dans une vue de texte se compose de <xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine> objets. Chaque ligne de la vue de texte correspond à une ligne de texte dans la vue de texte. Longues lignes dans la mémoire tampon sous\-jacente peuvent être partiellement masqués \(si le retour n’est pas activé\) ou répartis sur plusieurs lignes de texte à afficher. Le <xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine> interface contient les méthodes et propriétés pour le mappage entre les coordonnées et les caractères et les motifs qui peuvent être associés à la ligne.  
  
 <xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine> les objets sont créés en utilisant un <xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource> interface. Si vous craignez simplement le texte qui est actuellement affiché dans la vue, vous pouvez ignorer la mise en forme source. Si vous êtes intéressé par le format de texte qui n’est pas affiché dans la vue \(par exemple, pour prendre en charge une coupe de texte enrichi et la coller\), vous pouvez utiliser <xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource> pour mettre le texte dans une mémoire tampon de texte.  
  
 Un des formats de l’affichage de texte <xref:Microsoft.VisualStudio.Text.ITextSnapshotLine> à la fois.  
  
## Fonctionnalités de l’éditeur  
 Les fonctionnalités de l’éditeur sont conçues pour que la définition de la fonctionnalité est séparée de son implémentation. L’éditeur inclut ces fonctionnalités :  
  
-   Les balises et les classifieurs  
  
-   Ornements  
  
-   Projection  
  
-   Mode Plan  
  
-   Liaisons de la souris et la clé  
  
-   Primitives et des opérations  
  
-   IntelliSense  
  
###  <a name="tagsandclassifiers"></a> Les balises et les classifieurs  
 Les balises sont des marqueurs qui sont associés à une plage de texte. Ils peuvent être présentées de différentes façons, par exemple, à l’aide de couleurs de texte, des soulignements, graphiques ou les fenêtres publicitaires intempestives. Les classifieurs sont un type de balise.  
  
 Autres types de balises sont <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> pour mettre en surbrillance de texte, <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag> pour un plan, et <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag> pour les erreurs de compilation.  
  
#### Types de classification  
 Un <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType> interface représente une classe d’équivalence, qui est une catégorie de texte abstraite. Types de classification peuvent plusieurs\-hériter d’autres types de classification. Par exemple, classifications de langage de programmation peut inclure « mots clés », « commentaire » et « identificateur », qui héritent de « code ». Types de classification de langage naturel peuvent inclure « nom », « verbe » et « adjectif », qui héritent de « langage naturel ».  
  
#### Classifications  
 Une classification est une instance d’un type particulier de classification, généralement sur une plage de texte. Un <xref:Microsoft.VisualStudio.Text.Classification.ClassificationSpan> est utilisé pour représenter une classification. Une étendue de classification peut considérer comme une étiquette qui couvre une plage de texte particulier et indique au système que cette étendue de texte est d’un type de classification particulier.  
  
#### Classifieurs  
 Un <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> est un mécanisme qui découpe le texte en un ensemble de classifications. Les classifieurs doivent être définis pour les types de contenu spécifiques et instanciés pour les mémoires tampons de texte spécifique. Les clients doivent implémenter <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> participer de classification du texte.  
  
#### Agrégateurs de classifieur  
 Une agrégation du classifieur est un mécanisme qui combine tous les classifieurs pour la mémoire tampon de texte en simplement une série de classifications. Par exemple, un classifieur c\# et un classifieur en langue anglaise peut créer des classifications sur un commentaire dans un fichier c\#. Prenez en compte ce commentaire :  
  
```  
// This method produces a classifier  
```  
  
 Un classifieur c\# peut\-être étiqueter la plage complète de commentaire, et le classifieur en langue anglaise peut classer « produit » en tant que « verbe » et « méthode » comme un « nom ». L’agrégation génère un ensemble de classifications sans chevauchement, et le type de l’ensemble est basé sur toutes les contributions.  
  
 Une agrégation du classifieur est également un classifieur car elle découpe le texte en un ensemble de classifications. L’agrégation du classifieur garantit également qu’il n’y a aucune classification qui se chevauchent et que les classifications sont triées. Les classifieurs individuels sont libre de renvoyer un jeu de classifications, dans n’importe quel ordre et qui se chevauchent en aucune façon.  
  
#### Classification de mise en forme et la coloration du texte  
 Mise en forme du texte est un exemple de cette fonctionnalité repose sur la classification du texte. Elle est utilisée par la couche de vue de texte pour déterminer l’affichage du texte dans une application. La zone de mise en forme de texte dépend de WPF, mais la définition des classifications logique n’est pas.  
  
 Un format de classification est un ensemble de propriétés d’un type spécifique de classification de mise en forme. Ces formats héritent du format du parent du type de classification.  
  
 Un <xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMap> est un mappage à partir d’un type de classification à un ensemble de propriétés de mise en forme. L’implémentation de la carte de format dans l’éditeur gère toutes les exportations de formats de classification.  
  
###  <a name="adornments"></a> Ornements  
 Ornements sont des effets graphiques qui ne sont pas directement liées à la police et la couleur des caractères dans la vue de texte. Par exemple, le trait de soulignement rouge ondulée qui est utilisé pour marquer le code non compilé dans de nombreux langages de programmation est un ornement incorporé et info\-bulles sont les motifs publicitaires. Ornements sont dérivés de <xref:System.Windows.UIElement> et mettre en œuvre <xref:Microsoft.VisualStudio.Text.Tagging.ITag>. Deux types de balise d’ornement spécialisés sont le <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>, pour des motifs qui occupent le même espace que le texte dans une vue, et la <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>, pour la ligne de soulignement ondulée.  
  
 Ornements incorporées sont des graphiques qui font partie de la vue de texte mis en forme. Ils sont organisés dans les différentes couches de l’axe z. Il existe trois couches intégrés, comme suit : texte, le point d’insertion et la sélection. Toutefois, les développeurs peuvent définir des couches et les placer dans l’ordre par rapport à l’autre. Les trois types de motifs incorporées sont des ornements de texte relatif \(lequel déplacer lorsque le texte se déplace et sont supprimés lorsque le texte est supprimé\), relatifs à l’affichage des ornements \(dont il faut faire avec les parties non textuelles de la vue\) et ornements contrôlée par le propriétaire \(le développeur doit gérer leur placement\).  
  
 Motifs publicitaires sont des graphiques qui s’affichent dans une petite fenêtre au\-dessus de l’affichage de texte, par exemple, les info\-bulles.  
  
###  <a name="projection"></a> Projection  
 Projection est une technique permettant de construire un autre type de mémoire tampon de texte qui ne stocke pas réellement de texte, mais les combine à la place du texte à partir d’autres mémoires tampons de texte. Par exemple, une mémoire tampon de projection peut être utilisé pour concaténer le texte à partir de deux autres tampons et présente le résultat comme s’il se trouve dans un seul tampon, ou pour masquer des parties de texte dans une mémoire tampon. Une mémoire tampon de projection peut agir comme une mémoire tampon source à une autre mémoire tampon de projection. Un jeu de mémoires tampons qui sont liés par projection peut être construit pour réorganiser le texte de différentes façons. \(Un tel jeu est également appelé un *graphique de mémoire tampon*.\) La fonctionnalité mode plan de texte Visual Studio est implémentée à l’aide d’une mémoire tampon de projection pour masquer le texte réduit, et l’éditeur Visual Studio pour les pages ASP.NET utilise la projection pour prendre en charge incorporée des langages tels que Visual Basic et c\#.  
  
 Un <xref:Microsoft.VisualStudio.Text.Projection.IProjectionBuffer> est créé à l’aide de <xref:Microsoft.VisualStudio.Text.Projection.IProjectionBufferFactoryService>. Une mémoire tampon de projection est représenté par une séquence ordonnée de <xref:Microsoft.VisualStudio.Text.ITrackingSpan> objets appelés *étendues de sources*. Le contenu de ces plages est présenté comme une séquence de caractères. Les mémoires tampons de texte à partir de laquelle sont dessinés les étendues de sources sont nommés *source tampons*. Les clients d’une mémoire tampon de projection n’ont pas à être conscient qu’il diffère d’un tampon de texte ordinaire.  
  
 La mémoire tampon de projection écoute les événements de modification du texte dans la mémoire tampon source. Lorsque le texte dans une source de couvrir les modifications, la mémoire tampon de projection mappe les coordonnées du texte modifié ses coordonnées et déclenche des événements de modification de texte appropriée. Par exemple, tenez compte des mémoires tampons source A et B ont ce contenu :  
  
```  
A: ABCDE  
B: vwxyz  
```  
  
 Si la mémoire tampon de projection P est formé à partir de deux plages de texte, une dont toutes les mémoires tampons A et un autre qui contient toutes les mémoires tampons B, P présente le contenu suivant :  
  
```  
P: ABCDEvwxyz  
```  
  
 Si la sous\-chaîne `xy` est supprimé de la mémoire tampon B, puis tampon P déclenche un événement qui indique que les caractères en position 7 et 8 ont été supprimés.  
  
 La mémoire tampon de projection peut également être modifiée directement. Il propage les modifications apportées à la mémoire tampon source appropriée. Par exemple, si une chaîne est insérée dans la mémoire tampon P à la position 6 \(la position d’origine du caractère « v »\), l’insertion est propagée au tampon B à la position 1.  
  
 Il existe des restrictions sur les étendues de source qui contribuent à une mémoire tampon de projection. Étendues de sources ne peuvent pas se chevaucher ; Impossible de mapper un emplacement dans une mémoire tampon de projection à plusieurs emplacements dans une mémoire tampon source et un emplacement dans une mémoire tampon source ne peut pas mapper à plusieurs emplacements dans une mémoire tampon de projection. Aucun circularities ne sont autorisées dans la relation de la mémoire tampon source.  
  
 Les événements sont déclenchés lorsque le jeu de code source met en mémoire tampon pour une mémoire tampon change de projection et lorsque l’ensemble de la source s’étend sur les modifications.  
  
 Une mémoire tampon d’élision est un type spécial de la mémoire tampon de projection. Il est principalement utilisé pour le mode plan et les opérations que développer et réduire des blocs de texte. Une mémoire tampon d’élision est basé sur simplement une mémoire tampon source, et les étendues de la mémoire tampon d’élision doivent être ordonnées identiques car ils sont classés dans la mémoire tampon source.  
  
##### Le graphique de mémoire tampon  
 Le <xref:Microsoft.VisualStudio.Text.Projection.IBufferGraph> interface Active le mappage entre un graphique des mémoires tampons de projection. Toutes les mémoires tampons de texte et les mémoires tampons de projection sont collectées dans un graphique acyclique dirigé, comme l’arborescence de syntaxe abstraite qui est généré par un compilateur de langage. Le graphique est défini par la mémoire tampon supérieure, ce qui peut être une mémoire tampon de texte. Le graphique de mémoire tampon peut mapper à partir d’un point dans la mémoire tampon supérieure à un point dans une mémoire tampon source ou une étendue dans la mémoire tampon supérieure à un jeu d’étendues dans une mémoire tampon source. De même, il peut mapper un point ou s’étendent d’une mémoire tampon source à un point dans la mémoire tampon supérieure. Graphiques de la mémoire tampon sont créés à l’aide de la <xref:Microsoft.VisualStudio.Text.Projection.IBufferGraphFactoryService>.  
  
##### Les événements et les mémoires tampons de Projection  
 Lorsqu’une mémoire tampon de projection est modifiée, les modifications sont envoyées à partir de la mémoire tampon de projection aux mémoires tampons qui en dépendent. Une fois toutes les mémoires tampons sont modifiées, les événements de modification de mémoire tampon sont déclenchés, commençant par la mémoire tampon plus profonde.  
  
###  <a name="outlining"></a> Mode Plan  
 Le mode plan est la possibilité de développer ou réduire différents blocs de texte dans une vue de texte. Le mode plan est défini comme une sorte de <xref:Microsoft.VisualStudio.Text.Tagging.ITag>, de la même façon que les motifs sont définis. Un <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag> est une balise qui définit une zone de texte qui peut être développée ou réduite. Pour utiliser le mode plan, vous devez importer le <xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManagerService> pour obtenir un <xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManager>. Le Gestionnaire de mode plan énumère, réduit et développe les différents blocs, qui sont représentées sous la forme <xref:Microsoft.VisualStudio.Text.Outlining.ICollapsible> des objets et déclenche des événements en conséquence.  
  
###  <a name="mousebindings"></a> Liaisons de la souris  
 Liaisons de souris lier les mouvements de souris à différentes commandes. Liaisons de souris sont définies en utilisant une <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessorProvider>, et les combinaisons de touches sont définies en utilisant une <xref:Microsoft.VisualStudio.Text.Editor.IKeyProcessorProvider>. Le <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> automatiquement instancie toutes les liaisons et les connecter aux événements de souris dans la vue.  
  
 Le <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessor> interface contient les gestionnaires d’événements de prétraitement et de post\-traitement pour différents événements de souris. Pour gérer un des événements, vous pouvez remplacer certaines méthodes dans <xref:Microsoft.VisualStudio.Text.Editor.MouseProcessorBase>.  
  
###  <a name="editoroperations"></a> Opérations de l’éditeur  
 Éditeur peuvent être utilisées pour automatiser l’interaction avec l’éditeur, pour les scripts ou d’autres fins. Vous pouvez importer les <xref:Microsoft.VisualStudio.Text.Operations.IEditorOperationsFactoryService> aux opérations d’accès sur une donnée <xref:Microsoft.VisualStudio.Text.Editor.ITextView>. Vous pouvez ensuite utiliser ces objets pour modifier la sélection, faites défiler l’affichage ou déplacer le signe insertion vers différentes parties de la vue.  
  
###  <a name="intellisense"></a> IntelliSense  
 IntelliSense prend en charge la saisie semi\-automatique des instructions, l’assistance de signature \(également connu sous les informations de paramètre\), Info Express et ampoules.  
  
 Saisie semi\-automatique des instructions fournit des listes contextuelles des saisies semi\-automatiques potentiels pour les noms de méthode, des éléments XML et autres éléments de balisage ou de codage. En général, un mouvement utilisateur appelle une session de saisie semi\-automatique. La session affiche la liste des saisies semi\-automatiques potentiels, et l’utilisateur peut sélectionner un ou fermer la liste. Le <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker> est chargé de créer et de déclencher la <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSession>. Le <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource> calcule le <xref:Microsoft.VisualStudio.Language.Intellisense.CompletionSet> des éléments de saisie semi\-automatique pour la session.  
  
## Voir aussi  
 [Service de langage et les Points d’Extension Éditeur](../extensibility/language-service-and-editor-extension-points.md)   
 [Importations d'éditeur](../extensibility/editor-imports.md)