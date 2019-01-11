---
title: Dans l’éditeur
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - architecture
ms.assetid: 822cbb8d-7ab4-40ee-bd12-44016ebcce81
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 785e47a337eb33eb9416705a4c2c647a99f611d7
ms.sourcegitcommit: 59c48e1e42b48ad25a4e198af670faa4d8dae370
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2019
ms.locfileid: "54204519"
---
# <a name="inside-the-editor"></a>À l’intérieur de l’éditeur

L’éditeur est composé de différents sous-systèmes, lesquels sont conçus pour empêcher l’éditeur de texte modèle distinct l’affichage de texte et l’interface utilisateur.

Ces sections décrivent les différents aspects de l’éditeur :

- [Vue d’ensemble des sous-systèmes](../extensibility/inside-the-editor.md#overview-of-the-subsystems)

- [Le modèle de texte](../extensibility/inside-the-editor.md#the-text-model)

- [L’affichage de texte](../extensibility/inside-the-editor.md#the-text-view)

Ces sections décrivent les fonctionnalités de l’éditeur :

- [Balises et les classifieurs](../extensibility/inside-the-editor.md#tags-and-classifiers)

- [Ornements](../extensibility/inside-the-editor.md#adornments)

- [Projection](../extensibility/inside-the-editor.md#projection)

- [Mode Plan](../extensibility/inside-the-editor.md#outlining)

- [Liaisons de souris](../extensibility/inside-the-editor.md#mouse-bindings)

- [Opérations de l’éditeur](../extensibility/inside-the-editor.md#editor-operations)

- [IntelliSense](../extensibility/inside-the-editor.md#intellisense)

## <a name="overview-of-the-subsystems"></a>Vue d’ensemble des sous-systèmes

### <a name="text-model-subsystem"></a>Sous-système de modèle de texte

Le sous-système de modèle de texte est responsable représentant le texte et l’activation de sa manipulation. Le sous-système de modèle de texte contient le <xref:Microsoft.VisualStudio.Text.ITextBuffer> interface, qui décrit la séquence de caractères qui doit être affichée par l’éditeur. Ce texte peut être modifié, suivi et manipulé à bien des égards. Le modèle de texte fournit également des types pour les aspects suivants :

- Un service qui associe le texte avec des fichiers et gère la lecture et de les écrire dans le système de fichiers.

- Un service de différenciation qui recherche la grande différence entre deux séquences d’objets.

- Un système qui décrit le texte dans une mémoire tampon en termes de sous-ensembles du texte dans les autres mémoires tampons.

Le sous-système de modèle de texte est libre de concepts d’interface (UI) utilisateur. Par exemple, il n’est pas responsable de la mise en forme du texte ou de la disposition du texte, et il n’a aucune connaissance des ornements visuels qui peuvent être associées à du texte.

Les types publics du sous-système de modèle de texte sont contenues dans *Microsoft.VisualStudio.Text.Data.dll* et *Microsoft.VisualStudio.CoreUtility.dll*, qui dépendent uniquement de la base de .NET Framework bibliothèque de classes et de Managed Extensibility Framework (MEF).

### <a name="text-view-subsystem"></a>Sous-système d’affichage de texte

Le sous-système d’affichage de texte est responsable de la mise en forme et l’affichage de texte. Les types dans ce sous-système sont divisées en deux couches, selon que les types s’appuient sur Windows Presentation Foundation (WPF). Les types les plus importants sont <xref:Microsoft.VisualStudio.Text.Editor.ITextView> et <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>, qui contrôle l’ensemble de lignes de texte qui doivent être affichées et également le point d’insertion, la sélection et les installations pour orner le texte à l’aide des éléments de WPF UI. Ce sous-système fournit également des marges autour du texte de zone d’affichage. Ces marges peuvent être étendus et peuvent contenir différents types de contenu et visuelle des effets. Ligne numéro affiche et barres de défilement sont des exemples de marges.

Les types publics du sous-système d’affichage de texte sont contenues dans *Microsoft.VisualStudio.Text.UI.dll* et *Microsoft.VisualStudio.Text.UI.Wpf.dll*. Le premier assembly contient les éléments indépendant de la plateforme, et le second contient les éléments spécifiques à WPF.

### <a name="classification-subsystem"></a>Sous-système de classification

Le sous-système de classification est chargé de déterminer les propriétés de police du texte. Un classifieur fractionne le texte en différentes classes, par exemple, « keyword » ou « commentaire ». Le mappage de format de classification rapporte ces classes à des propriétés de police réelle, par exemple, « bleu Consolas 10 pt ». Ces informations sont utilisées par l’affichage de texte lorsqu’il met en forme et restitue le texte. Balisage, qui est décrite plus en détail plus loin dans cette rubrique, permet de données à associer à des étendues de texte.

Les types publics du sous-système de classification sont contenus dans Microsoft.VisualStudio.Text.Logic.dll, et ils interagissent avec les aspects visuels de la classification, qui sont contenus dans Microsoft.VisualStudio.Text.UI.Wpf.dll.

### <a name="operations-subsystem"></a>Sous-système d’opérations

Le sous-système d’opérations définit le comportement de l’éditeur. Il fournit l’implémentation pour les commandes de l’éditeur Visual Studio et le système d’annulation.

## <a name="a-closer-look-at-the-text-model-and-the-text-view"></a>Examinez de plus près le modèle de texte et l’affichage de texte

### <a name="the-text-model"></a>Le modèle de texte

Le sous-système de modèle de texte se compose de différents groupes de types de texte. Ceux-ci incluent la mémoire tampon de texte, les instantanés de texte et les étendues de texte.

#### <a name="text-buffers-and-text-snapshots"></a>Mémoires tampons de texte et les instantanés de texte

Le <xref:Microsoft.VisualStudio.Text.ITextBuffer> interface représente une séquence de caractères Unicode qui sont codés en UTF-16, ce qui est l’encodage utilisé par le `String` type dans le .NET Framework. Une mémoire tampon de texte peut être rendu persistant comme un document de système de fichiers, mais cela n’est pas nécessaire.

Le <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService> est utilisé pour créer une mémoire tampon de texte vide, ou une mémoire tampon de texte qui est initialisé à partir d’une chaîne ou de <xref:System.IO.TextReader>. La mémoire tampon de texte peut être rendu persistant dans le système de fichiers comme un <xref:Microsoft.VisualStudio.Text.ITextDocument>.

N’importe quel thread peut modifier la mémoire tampon jusqu'à ce qu’un thread prend possession de la mémoire tampon de texte en appelant <xref:Microsoft.VisualStudio.Text.ITextBuffer.TakeThreadOwnership%2A>. Après cela, seulement ce thread peut effectuer des modifications.

Une mémoire tampon de texte peut passer par le nombre de versions pendant sa durée de vie. Une nouvelle version est générée chaque fois que la mémoire tampon est modifiée et qu’un immuable <xref:Microsoft.VisualStudio.Text.ITextSnapshot> représente le contenu de cette version de la mémoire tampon. Étant donné que les instantanés de texte sont immuables, vous pouvez accéder un instantané de texte sur n’importe quel thread, sans restriction, même si la mémoire tampon de texte qu’il représente ne cesse d’évoluer.

#### <a name="text-snapshots-and-text-snapshot-lines"></a>Instantanés de texte et des lignes d’instantané de texte

Vous pouvez afficher le contenu d’un instantané de texte sous la forme d’une séquence de caractères ou une séquence de lignes. Caractères et les lignes sont que tous deux indexés en commençant à zéro. Un instantané de texte vide contient zéro caractère et une ligne vide. Une ligne est délimitée par une séquence de caractères de saut de ligne Unicode valide, ou par le début ou la fin de la mémoire tampon. Caractères de saut de ligne sont explicitement représentées dans l’instantané de texte et les sauts de ligne dans un instantané de texte ne sont pas nécessairement être identiques.

> [!NOTE]
> Pour plus d’informations sur les caractères de saut de ligne dans l’éditeur Visual Studio, consultez [encodages et sauts de ligne](../ide/encodings-and-line-breaks.md).

Une ligne de texte est représentée par un <xref:Microsoft.VisualStudio.Text.ITextSnapshotLine> objet, qui peut être obtenu à partir d’un instantané de texte pour un numéro de ligne particulier ou pour une position de caractère particulier.

#### <a name="snapshotpoints-snapshotspans-and-normalizedsnapshotspancollections"></a>SnapshotPoints, SnapshotSpans et NormalizedSnapshotSpanCollections

Un <xref:Microsoft.VisualStudio.Text.SnapshotPoint> représente une position de caractère dans un instantané. La position est garantie être compris entre zéro et la longueur de l’instantané. Un <xref:Microsoft.VisualStudio.Text.SnapshotSpan> représente une étendue de texte dans un instantané. Sa position de fin est garantie être compris entre zéro et la longueur de l’instantané. Le <xref:Microsoft.VisualStudio.Text.NormalizedSnapshotSpanCollection> se compose d’un ensemble de <xref:Microsoft.VisualStudio.Text.SnapshotSpan> objets à partir du même instantané.

#### <a name="spans-and-normalizedspancollections"></a>Étendues et NormalizedSpanCollections

Un <xref:Microsoft.VisualStudio.Text.Span> représente un intervalle qui peut être appliqué à une étendue de texte dans un instantané de texte. Les positions de capture instantanée sont de base zéro, afin qu’étendues puissent commencer à n’importe quelle position zéro compris. Le `End` propriété d’une étendue est égale à la somme de ses `Start` propriété et sa `Length` propriété. Un `Span` n’inclut pas le caractère qui est indexé par le `End` propriété. Par exemple, une étendue qui a début = 5 et longueur = 3 a fin = 8, et elle inclut les caractères aux positions 5, 6 et 7. La notation pour cette étendue est 5..8).

Deux étendues se croisent si elles ont des positions en commun, y compris la position de fin. Par conséquent, l’intersection de [3, 5) et [2, 7) est [3, 5) et l’intersection de [3, 5) et [5, 7) est [5, 5). (Notez que [5, 5) est une étendue vide.)

Deux étendues se chevauchent si elles ont des positions en commun, à l’exception de la position de fin. Une étendue vide chevauche jamais d’autres étendues, et le chevauchement de deux étendues n’est jamais vide.

Un <xref:Microsoft.VisualStudio.Text.NormalizedSpanCollection> est une liste d’étendues dans l’ordre les propriétés de démarrage des étendues. Dans la liste, qui se chevauche ou attenants étendues sont fusionnée. Par exemple, compte tenu du jeu d’étendues [5..9), [0..1), [3..6), et [9..10), la liste normalisée d’étendues est [0..1), [3..10).

#### <a name="itextedit-textversion-and-text-change-notifications"></a>Notifications de changement ITextEdit, textversion n’et texte

Le contenu d’une mémoire tampon de texte peut être modifié en utilisant un <xref:Microsoft.VisualStudio.Text.ITextEdit> objet. Création d’un tel objet (en utilisant l’une de le `CreateEdit()` méthodes de <xref:Microsoft.VisualStudio.Text.ITextBuffer>) démarre une transaction de texte qui se compose de modifications de texte. Chaque modification est un remplacement d’une étendue de texte dans la mémoire tampon par une chaîne. Les coordonnées et le contenu de chaque modification sont exprimées par rapport à l’instantané de la mémoire tampon lors de la transaction a été démarré. Le <xref:Microsoft.VisualStudio.Text.ITextEdit> objet ajuste les coordonnées de modifications qui sont affectées par d’autres modifications dans la même transaction.

Par exemple, considérez une mémoire tampon de texte qui contient cette chaîne :

```
abcdefghij
```

Appliquer une transaction qui contient deux modifications, une seule modification qui remplace l’étendue à [2..4) en utilisant le caractère `X` et une deuxième modification qui remplace l’étendue à [6..9) en utilisant le caractère `Y`. Le résultat est cette mémoire tampon :

```
abXefYj
```

Les coordonnées pour la deuxième modification ont été calculées en ce qui concerne le contenu de la mémoire tampon au début de la transaction, avant la première modification a été appliquée.

Les modifications apportées à la mémoire tampon prennent effet lors de la <xref:Microsoft.VisualStudio.Text.ITextEdit> objet est validé en appelant son `Apply()` (méthode). S’il y avait au moins une modification de non vide, un nouveau <xref:Microsoft.VisualStudio.Text.ITextVersion> est créé, un nouveau <xref:Microsoft.VisualStudio.Text.ITextSnapshot> est créé et un `Changed` événement est déclenché. Chaque version de texte associé à un autre instantané de texte. Un instantané de texte représente l’état complet de la mémoire tampon de texte après une transaction de modification, mais une version texte décrit uniquement les modifications apportées à partir d’un instantané à l’autre. En général, les instantanés de texte sont destinés à être utilisés qu’une seule fois et ensuite ignorées, tandis que les versions de texte doivent rester actives pendant un certain temps.

Une version texte contient un <xref:Microsoft.VisualStudio.Text.INormalizedTextChangeCollection>. Cette collection décrit les modifications qui, lorsqu’il est appliqué à l’instantané, générer l’instantané suivant. Chaque <xref:Microsoft.VisualStudio.Text.ITextChange> dans la collection contient la position de caractère de la chaîne de remplacement, la modification et la chaîne remplacée. La chaîne remplacée est vide pour une insertion de base, et la chaîne de remplacement est vide pour une suppression de base. La collection normalisée est toujours `null` pour la version la plus récente de la mémoire tampon de texte.

Seul <xref:Microsoft.VisualStudio.Text.ITextEdit> objet peut être instancié une mémoire tampon de texte à tout moment, et toutes les modifications de texte doivent être effectuées sur le thread qui détient la mémoire tampon de texte (si la propriété a été demandée). Une modification de texte peut être abandonnée en appelant son `Cancel` méthode ou son `Dispose` (méthode).

<xref:Microsoft.VisualStudio.Text.ITextBuffer> fournit également `Insert()`, `Delete()`, et `Replace()` méthodes qui ressemblent à celles disponibles sur le <xref:Microsoft.VisualStudio.Text.ITextEdit> interface. Appelle ces a le même effet que la création d’un <xref:Microsoft.VisualStudio.Text.ITextEdit> objet, l’appel similaire et en appliquant la modification.

#### <a name="tracking-points-and-tracking-spans"></a>Points de suivi et étendues de suivi

Un <xref:Microsoft.VisualStudio.Text.ITrackingPoint> représente une position de caractère dans une mémoire tampon de texte. Si la mémoire tampon est modifiée d’une manière qui provoque la position du caractère de décalage, le point de suivi se déplace avec lui. Par exemple, si un point de suivi fait référence à la position 10 dans une mémoire tampon et cinq caractères sont insérés au début de la mémoire tampon, le point de suivi puis désigne position 15. Si une insertion se produit à précisément la position indiquée par le point de suivi, son comportement est déterminé par ses <xref:Microsoft.VisualStudio.Text.PointTrackingMode>, qui peut être `Positive` ou `Negative`. Si le mode de suivi est positif, le point de suivi fait référence au même caractère, qui est maintenant à la fin de l’insertion. Si le mode de suivi est négatif, le point de suivi fait référence au premier caractère inséré à la position d’origine. Si le caractère situé à la position qui est représenté par un point de suivi est supprimé, le point de suivi se déplace vers le premier caractère qui suit la plage supprimée. Par exemple, si un point de suivi fait référence au caractère à la position 5, et les caractères aux positions 3 à 6 sont supprimées, le point de suivi fait référence au caractère à la position 3.

Un <xref:Microsoft.VisualStudio.Text.ITrackingSpan> représente une plage de caractères au lieu de simplement une position. Son comportement est déterminé par ses <xref:Microsoft.VisualStudio.Text.SpanTrackingMode>. Si le mode de suivi span est [SpanTrackingMode.EdgeInclusive](xref:Microsoft.VisualStudio.Text.SpanTrackingMode.EdgeInclusive), l’étendue de suivi s’agrandit pour incorporer le texte inséré à ses bords. Si le mode de suivi span est [SpanTrackingMode.EdgeExclusive](xref:Microsoft.VisualStudio.Text.SpanTrackingMode.EdgeExclusive), l’étendue de suivi n’incorpore pas de texte inséré à ses bords. Toutefois, si le mode de suivi span est [SpanTrackingMode.EdgePositive](xref:Microsoft.VisualStudio.Text.SpanTrackingMode.EdgePositive), une insertion exécute un push de la position actuelle vers le début, et si le mode de suivi de l’étendue est [SpanTrackingMode.EdgeNegative](xref:Microsoft.VisualStudio.Text.SpanTrackingMode.EdgeNegative), un insertion exécute un push de la position actuelle vers la fin.

Vous pouvez obtenir la position d’un point de suivi ou l’étendue d’une étendue de suivi pour tous les instantanés de la mémoire tampon de texte auquel elles appartiennent. Points de suivi et étendues de suivi peuvent être référencées en toute sécurité à partir de n’importe quel thread.

#### <a name="content-types"></a>Types de contenu

Types de contenu sont un mécanisme permettant de définir différents types de contenu. Un type de contenu peut être un type de fichier tels que « text », « code » ou « binaire », ou un type de technologie tels que « xml », « vb » ou « c# ». Par exemple, le mot « using » est un mot clé en c# et Visual Basic, mais pas dans les autres langages de programmation. Par conséquent, la définition de ce mot clé serait limitée pour les types de contenu « c# » et « vb ».

Types de contenu sont utilisés en tant que filtre pour les ornements et d’autres éléments de l’éditeur. Plusieurs fonctionnalités de l’éditeur et les points d’extension sont définies par le type de contenu. Par exemple, la coloration du texte est différent pour les fichiers de texte brut, les fichiers XML et les fichiers de code source Visual Basic. Mémoires tampons de texte bénéficient généralement d’un type de contenu lorsqu’ils sont créés, et le type de contenu d’une mémoire tampon de texte peut être modifié.

Types de contenu peuvent multiple-hériter d’autres types de contenu. Le <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> vous permet de spécifier plusieurs types de base en tant que les parents d’un type de contenu donné.

Les développeurs peuvent définir leurs propres types de contenu et les inscrire à l’aide de la <xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService>. Plusieurs fonctionnalités de l’éditeur peuvent être définies par rapport à un type de contenu spécifique à l’aide de la <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>. Par exemple, les marges de l’éditeur, les ornements et les gestionnaires de souris peuvent être définis afin qu’ils s’appliquent uniquement à des éditeurs qui affichent les types de contenu particuliers.

### <a name="the-text-view"></a>L’affichage de texte

La partie de la vue du modèle Vue contrôleur (MVC) définit l’affichage de texte, la mise en forme de la vue, les éléments graphiques tels que la barre de défilement et le signe insertion. Tous les éléments de présentation de l’éditeur Visual Studio sont basés sur WPF.

#### <a name="text-views"></a>Affichages de texte

Le <xref:Microsoft.VisualStudio.Text.Editor.ITextView> interface est une représentation indépendante de la plateforme d’une vue de texte. Il est utilisé principalement pour afficher des documents de texte dans une fenêtre, mais il peut également être utilisé à d’autres fins, par exemple, dans une info-bulle.

L’affichage de texte fait référence à différents types de mémoires tampons de texte. Le <xref:Microsoft.VisualStudio.Text.Editor.ITextView.TextViewModel%2A> propriété fait référence à un <xref:Microsoft.VisualStudio.Text.Editor.ITextViewModel> objet qui pointe vers ces trois mémoires tampons de texte différente : la mémoire tampon de données, qui est la mémoire tampon au niveau des données supérieure, la mémoire tampon d’édition, dans lequel la modification se produit et la mémoire tampon visuelle, qui est la mémoire tampon qui est affiché dans l’affichage de texte.

Le texte est mis en forme en fonction des classifieurs qui sont attachés à la mémoire tampon de texte sous-jacente et est orné en utilisant les fournisseurs d’ornement qui sont attachés à la vue de texte lui-même.

#### <a name="the-text-view-coordinate-system"></a>Le système de coordonnées de vue de texte

Le système de coordonnées de vue de texte spécifie des positions dans l’affichage de texte. Dans ce système de coordonnées, la valeur de x 0,0 correspond et le bord gauche du texte qui est affiché, et la valeur y 0,0 correspond sur le bord supérieur du texte qui est affiché. La coordonnée x augmente de gauche à droite, et la coordonnée y augmente de haut en bas.

Une fenêtre d’affichage (la partie du texte visible dans la fenêtre texte) ne peut pas faire défiler horizontalement de la même manière comme défile verticalement. Une fenêtre d’affichage est défilé horizontalement en modifiant sa coordonnée gauche afin qu’il se déplace en ce qui concerne la surface de dessin. Toutefois, une fenêtre d’affichage peut défiler verticalement qu’en modifiant le texte affiché, ce qui provoque un <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> déclenchement d’événement.

Les distances dans le système de coordonnées correspondent aux pixels logiques. Si la surface de rendu de texte s’affiche sans une transformation de mise à l’échelle, une unité dans le système de coordonnées de rendu de texte correspond à un pixel sur l’affichage.

#### <a name="margins"></a>Marges

Le <xref:Microsoft.VisualStudio.Text.Editor.ITextViewMargin> interface représente une marge et permet de contrôler la visibilité de la marge et sa taille. Il existe quatre marges prédéfinies, qui sont nommés « Top », « Gauche », « Droite » et « Bottom » et sont attachés en haut, inférieure, gauche ou droite d’une vue. Ces marges sont des conteneurs dans lequel les autres marges peuvent être placés. L’interface définit des méthodes qui retournent la taille de la marge et la visibilité d’une marge. Les marges sont des éléments visuels qui fournissent des informations supplémentaires sur l’affichage de texte auquel ils sont attachés. Par exemple, la marge de numéro de ligne affiche les numéros de ligne pour l’affichage de texte. La marge de glyphe affiche les éléments d’interface utilisateur.

Le <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMarginProvider> interface gère la création et le positionnement des marges. Marges peuvent être classées en ce qui concerne les autres marges. Marges de priorité plus élevée sont trouve plus près de l’affichage de texte. Par exemple, s’il existe deux marges gauche, marge A et B de marge et marge B a une priorité inférieure à la marge A, B de marge apparaît à gauche de marge A.

#### <a name="the-text-view-host"></a>L’hôte d’affichage de texte

Le <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> interface contient l’affichage de texte et les ornements attenants qui accompagnent la vue, par exemple, les barres de défilement. L’hôte d’affichage de texte contient également les marges qui sont attachés à une bordure de la vue.

#### <a name="formatted-text"></a>Texte mis en forme

Le texte qui est affiché dans un affichage de texte est composé de <xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine> objets. Chaque ligne d’affichage de texte correspond à une seule ligne de texte dans l’affichage de texte. Longues lignes dans la mémoire tampon de texte sous-jacente peuvent être partiellement obscurcies (si le retour automatique n’est pas activé) ou répartis sur plusieurs lignes d’affichage de texte. Le <xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine> interface contient des méthodes et propriétés pour le mappage entre les coordonnées et les caractères, ainsi que pour les ornements qui peuvent être associés à la ligne.

<xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine> objets sont créés en utilisant un <xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource> interface. Si vous craignez simplement le texte actuellement affiché dans la vue, vous pouvez ignorer la mise en forme source. Si vous êtes intéressé par le format de texte qui n’est pas affiché dans la vue (par exemple, pour prendre en charge un couper du texte enrichi et la coller), vous pouvez utiliser <xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource> pour formater le texte dans une mémoire tampon de texte.

Un des formats de l’affichage de texte <xref:Microsoft.VisualStudio.Text.ITextSnapshotLine> à la fois.

## <a name="editor-features"></a>Fonctionnalités de l’éditeur

Les fonctionnalités de l’éditeur sont conçues pour que la définition de la fonctionnalité est distincte de son implémentation. L’éditeur inclut ces fonctionnalités :

-   Balises et les classifieurs

-   Ornements

-   Projection

-   mode Plan

-   Liaisons de souris et la clé

-   Opérations et primitives

-   IntelliSense

### <a name="tags-and-classifiers"></a>Balises et les classifieurs

Les balises sont des marqueurs qui sont associés à une étendue de texte. Ils peuvent être présentées de différentes façons, par exemple, à l’aide de la coloration du texte, des traits de soulignement, des graphiques ou les fenêtres contextuelles. Les classifieurs sont un type de balise.

Autres types de balises sont <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> pour mettre en surbrillance de texte, <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag> pour le mode plan, et <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag> pour les erreurs de compilation.

#### <a name="classification-types"></a>Types de classification

Un <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType> interface représente une classe d’équivalence, qui est une catégorie abstraite de texte. Types de classification peuvent multiple-hériter d’autres types de classification. Par exemple, classifications de langage de programmation peut inclure « keyword », « commentaire » et « identificateur », qui héritent de « code ». Les types de classification de langage naturel, citons « nom », « verbe » et « adjectif », qui héritent de « langage naturel ».

#### <a name="classifications"></a>Classifications

Une classification est une instance d’un type de classification particulier, généralement sur une étendue de texte. Un <xref:Microsoft.VisualStudio.Text.Classification.ClassificationSpan> est utilisé pour représenter une classification. Une étendue de la classification peut être considérée comme une étiquette qui couvre une étendue particulière de texte et indique au système que cette étendue de texte est d’un type de classification particulier.

#### <a name="classifiers"></a>Classifieurs

Un <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> est un mécanisme qui découpe le texte en un ensemble de classifications. Classifieurs doivent être définis pour les types de contenu spécifiques et instanciés pour les mémoires tampons de texte spécifique. Les clients doivent implémenter <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> participer de classification de texte.

#### <a name="classifier-aggregators"></a>Agrégations de classifieur

Une agrégation du classifieur est un mécanisme qui combine tous les classifieurs pour une mémoire tampon en simplement une série de classifications. Par exemple, un classifieur c# et un classifieur en langue anglaise peut créer des classifications sur un commentaire dans un fichier c#. Prenez en compte ce commentaire :

```
// This method produces a classifier
```

Un classifieur c# peut-être étiqueter l’étendue entière sous forme de commentaire, et le classifieur de langue anglaise peut classer « produit » en tant que « verbe » et « méthode » comme un « nom ». La fonction d’agrégation produit un ensemble de classifications sans chevauchement, et le type du jeu est basé sur toutes les contributions.

Une agrégation du classifieur est également un classifieur, car elle découpe le texte en un ensemble de classifications. L’agrégation du classifieur garantit également qu’il n’y a aucune classification qui se chevauche et que les classifications sont triées. Les classifieurs individuels sont libre de renvoyer n’importe quel jeu de classifications, dans n’importe quel ordre et qui se chevauchent en aucune façon.

#### <a name="classification-formatting-and-text-coloring"></a>Mise en forme de classification et la coloration du texte

Mise en forme du texte est un exemple d’une fonctionnalité qui repose sur la classification de texte. Il est utilisé par la couche de vue de texte pour déterminer l’affichage du texte dans une application. La zone de texte mise en forme dépend de WPF, mais n’est pas le cas de la définition logique de classifications.

Un format de classification est un ensemble de propriétés pour un type de classification spécifique mise en forme. Le format du parent du type de classification héritent de ces formats.

Un <xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMap> est un mappage à partir d’un type de classification à un ensemble de propriétés de mise en forme de texte. L’implémentation de la carte de format dans l’éditeur gère toutes les exportations de formats de classification.

### <a name="adornments"></a>Ornements

Ornements sont des effets graphiques qui ne sont pas directement liées à la police et la couleur des caractères dans l’affichage de texte. Par exemple, le trait de soulignement rouge ondulée qui est utilisé pour marquer le code non compilé dans de nombreux langages de programmation est un ornement incorporé et info-bulles sont les ornements contextuelles. Ornements sont dérivés de <xref:System.Windows.UIElement> et implémenter <xref:Microsoft.VisualStudio.Text.Tagging.ITag>. Deux types de balise de l’ornement spécialisés sont le <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>, pour les ornements occupent le même espace que le texte dans une vue, et le <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>, pour le trait de soulignement de trait de soulignement ondulé.

Ornements incorporées sont des graphiques qui font partie de la vue de texte mis en forme. Ils sont organisés dans les différentes couches de l’ordre de plan. Il existe trois couches intégrés, comme suit : texte, le point d’insertion et la sélection. Toutefois, les développeurs peuvent définir plusieurs couches et les placer dans l’ordre par rapport à l’autre. Les trois types d’ornements embedded sont les ornements de texte relatif (qui déplacement lorsque le texte se déplace et sont supprimés lorsque le texte est supprimé), relatifs à un affichage des ornements (dont il faut faire avec les parties non textuelles de la vue) et sous contrôle de code propriétaire ornements (les développeur doive gérer leur placement).

Ornements contextuelles sont des graphiques qui s’affichent dans une petite fenêtre au-dessus de la vue de texte, par exemple, les info-bulles.

###  <a name="projection"></a> Projection

Projection est une technique pour la construction d’un autre type de mémoire tampon de texte qui ne stocke pas réellement de texte, mais combine à la place du texte à partir d’autres mémoires tampons de texte. Par exemple, une mémoire tampon de projection peut être utilisé pour concaténer le texte à partir de deux autres mémoires tampons et présente le résultat comme s’il se trouve dans la mémoire tampon qu’une seule, ou pour masquer des parties du texte dans une mémoire tampon. Une mémoire tampon de projection peut agir comme une mémoire tampon source à une autre mémoire tampon de projection. Un jeu de mémoires tampons qui sont liés par projection peut être construit pour réorganiser le texte de différentes manières. (Un ensemble de ce type est également appelé un *graphique de mémoire tampon*.) La fonctionnalité mode plan de texte Visual Studio est implémentée à l’aide d’une mémoire tampon de projection pour masquer le texte réduit, et l’éditeur Visual Studio pour les pages ASP.NET utilise projection pour prendre en charge des langues embedded tels que Visual Basic et c#.

Un <xref:Microsoft.VisualStudio.Text.Projection.IProjectionBuffer> est créé à l’aide de <xref:Microsoft.VisualStudio.Text.Projection.IProjectionBufferFactoryService>. Une mémoire tampon de projection est représenté par une séquence ordonnée de <xref:Microsoft.VisualStudio.Text.ITrackingSpan> les objets qui sont appelées *étendues de sources*. Le contenu de ces étendues est présenté comme une séquence de caractères. Les mémoires tampons de texte à partir de laquelle les étendues de source sont dessinés sont nommés *de source de mémoires tampons*. Les clients d’une mémoire tampon de projection n’est pas ont de Sachez qu’il diffère d’une mémoire tampon de texte ordinaires.

La mémoire tampon de projection écoute les événements de modification du texte sur les mémoires tampons sources. Lorsque le texte dans une source s’étendent sur les modifications, la mémoire tampon de projection mappe les coordonnées de texte modifié à son propre coordonnées et déclenche des événements de modification de texte appropriée. Par exemple, prenez en compte les mémoires tampons sources A et B qui ont ce contenu :

```
A: ABCDE
B: vwxyz
```

Si la mémoire tampon de projection P est formée à partir de deux étendues de texte, un qui possède toutes les mémoires tampons A et un autre dont toutes les mémoires tampons B, P a le contenu suivant :

```
P: ABCDEvwxyz
```

Si la sous-chaîne `xy` est supprimé de la mémoire tampon B, puis de la mémoire tampon P déclenche un événement qui indique que les caractères aux positions 7 et 8 ont été supprimés.

La mémoire tampon de projection peut également être modifiée directement. Il propage les modifications vers les mémoires tampons source appropriée. Par exemple, si une chaîne est insérée dans la mémoire tampon P à la position 6 (la position d’origine du caractère « v »), l’insertion est propagée à la mémoire tampon B à la position 1.

Il existe des restrictions sur les étendues de source qui contribuent à une mémoire tampon de projection. Étendues de source ne peuvent pas se chevaucher ; un emplacement dans une mémoire tampon de projection ne peut pas mapper à plusieurs emplacements dans une mémoire tampon source, et un emplacement dans une mémoire tampon source ne peut pas mapper à plusieurs emplacements dans une mémoire tampon de projection. Aucun circularities ne sont autorisées dans la relation de la mémoire tampon source.

Les événements sont déclenchés lors de l’ensemble de la source met en mémoire tampon pour un change de mémoire tampon de projection et lors de l’ensemble de la source s’étend sur les modifications.
Un mémoire tampon d’élision est un type spécial de la mémoire tampon de projection. Il est principalement utilisé pour le mode plan et les opérations que développer et réduire les blocs de texte. Un mémoire tampon d’élision est basé sur simplement une mémoire tampon source, et les étendues dans la mémoire tampon d’élision doivent être le même ordre comme ils sont classés dans la mémoire tampon source.

#### <a name="the-buffer-graph"></a>Graphique de mémoire tampon

Le <xref:Microsoft.VisualStudio.Text.Projection.IBufferGraph> interface Active le mappage entre un graphique des mémoires tampons de projection. Toutes les mémoires tampons de texte et les mémoires tampons de projection sont collectés dans un graphique acyclique dirigé, comme l’arborescence de syntaxe abstraite qui est généré par un compilateur de langage. Le graphique est défini par la mémoire tampon supérieure, ce qui peut être toute mémoire tampon de texte. Graphique de mémoire tampon peut mapper à partir d’un point dans la mémoire tampon supérieure à un point dans une mémoire tampon source, ou à partir d’une étendue dans la mémoire tampon supérieure à un ensemble d’étendues dans une mémoire tampon source. De même, il peut mapper un point ou s’étendre sur à partir d’une mémoire tampon source à un point dans la mémoire tampon supérieure. Graphiques de la mémoire tampon sont créés à l’aide de la <xref:Microsoft.VisualStudio.Text.Projection.IBufferGraphFactoryService>.

#### <a name="events-and-projection-buffers"></a>Événements et les mémoires tampons de projection

Lorsqu’une mémoire tampon de projection est modifiée, les modifications sont envoyées à partir de la mémoire tampon de projection aux mémoires tampons qui en dépendent. Une fois que toutes les mémoires tampons sont modifiés, les événements de modification de mémoire tampon sont déclenchés, en commençant par la mémoire tampon plus profonde.

### <a name="outlining"></a>mode Plan

Le mode plan est la possibilité de développer ou réduire différents blocs de texte dans un affichage de texte. Le mode plan est défini comme une sorte de <xref:Microsoft.VisualStudio.Text.Tagging.ITag>, dans la même façon que les ornements sont définis. Un <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag> est une balise qui définit une zone de texte qui peut être développée ou réduite. Pour utiliser le mode plan, vous devez importer le <xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManagerService> pour obtenir un <xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManager>. Le Gestionnaire de mode plan énumère, réduit et développe les blocs différents, qui sont représentées en tant que <xref:Microsoft.VisualStudio.Text.Outlining.ICollapsible> objets et déclenche des événements en conséquence.

### <a name="mouse-bindings"></a>Liaisons de souris

Liaisons de souris lier les mouvements de souris à des commandes différentes. Liaisons de souris sont définies en utilisant un <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessorProvider>, et combinaisons de touches sont définies en utilisant un <xref:Microsoft.VisualStudio.Text.Editor.IKeyProcessorProvider>. Le <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> automatiquement instancie toutes les liaisons et les connecte à des événements de souris dans la vue.

Le <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessor> interface contient les gestionnaires d’événements de prétraitement et de post-traitement pour différents événements de souris. Pour gérer un des événements, vous pouvez remplacer certaines méthodes dans <xref:Microsoft.VisualStudio.Text.Editor.MouseProcessorBase>.

### <a name="editor-operations"></a>Opérations de l’éditeur

Opérations de l’éditeur peuvent être utilisées pour automatiser l’interaction avec l’éditeur, sous forme de scripts ou d’autres fins. Vous pouvez importer le <xref:Microsoft.VisualStudio.Text.Operations.IEditorOperationsFactoryService> aux opérations d’accès sur une donnée <xref:Microsoft.VisualStudio.Text.Editor.ITextView>. Vous pouvez ensuite utiliser ces objets pour modifier la sélection, faites défiler la vue ou déplacer le signe insertion vers différentes parties de la vue.

### <a name="intellisense"></a>IntelliSense

IntelliSense prend en charge la saisie semi-automatique des instructions, pour la signature (également appelés informations sur les paramètres), Info Express et des ampoules.

Saisie semi-automatique des instructions fournit des listes contextuelles des saisies semi-automatiques de potentiels pour les noms de méthode, les éléments XML et d’autres éléments de balisage ou de codage. En règle générale, un mouvement utilisateur appelle une session de saisie semi-automatique. La session affiche la liste des saisies semi-automatiques potentiels, et l’utilisateur peut sélectionner un ou ignorer la liste. Le <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker> est responsable de la création et en déclenchant le <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSession>. Le <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource> calcule le <xref:Microsoft.VisualStudio.Language.Intellisense.CompletionSet> des éléments de saisie semi-automatique pour la session.

## <a name="see-also"></a>Voir aussi

- [Points d’extension éditeur et le service de langage](../extensibility/language-service-and-editor-extension-points.md)
- [Importations de l’éditeur](../extensibility/editor-imports.md)