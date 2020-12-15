---
title: Dans l’éditeur
description: En savoir plus sur les sous-systèmes et les fonctionnalités de l’éditeur. Vous pouvez étendre les fonctionnalités de l’éditeur Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - architecture
ms.assetid: 822cbb8d-7ab4-40ee-bd12-44016ebcce81
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 14193c0806c4b45f721ee97b101969de8437448d
ms.sourcegitcommit: 19061b61759ce8e3b083a0e01a858e5435580b3e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97487528"
---
# <a name="inside-the-editor"></a>Dans l’éditeur

L’éditeur est composé de plusieurs sous-systèmes différents, conçus pour conserver le modèle de texte de l’éditeur distinct de l’affichage de texte et de l’interface utilisateur.

Ces sections décrivent les différents aspects de l’éditeur :

- [Vue d’ensemble des sous-systèmes](../extensibility/inside-the-editor.md#overview-of-the-subsystems)

- [Modèle de texte](../extensibility/inside-the-editor.md#the-text-model)

- [Affichage de texte](../extensibility/inside-the-editor.md#the-text-view)

Ces sections décrivent les fonctionnalités de l’éditeur :

- [Balises et classifieurs](../extensibility/inside-the-editor.md#tags-and-classifiers)

- [Ornements](../extensibility/inside-the-editor.md#adornments)

- [Projection](../extensibility/inside-the-editor.md#projection)

- [mode Plan](../extensibility/inside-the-editor.md#outlining)

- [Liaisons de la souris](../extensibility/inside-the-editor.md#mouse-bindings)

- [Opérations de l’éditeur](../extensibility/inside-the-editor.md#editor-operations)

- [IntelliSense](../extensibility/inside-the-editor.md#intellisense)

## <a name="overview-of-the-subsystems"></a>Vue d’ensemble des sous-systèmes

### <a name="text-model-subsystem"></a>Sous-système de modèle de texte

Le sous-système de modèle de texte est responsable de la représentation du texte et de l’activation de sa manipulation. Le sous-système de modèle de texte contient l' <xref:Microsoft.VisualStudio.Text.ITextBuffer> interface, qui décrit la séquence de caractères qui doit être affichée par l’éditeur. Ce texte peut être modifié, suivi et manipulé de nombreuses façons. Le modèle de texte fournit également des types pour les aspects suivants :

- Service qui associe du texte à des fichiers et gère la lecture et l’écriture dans le système de fichiers.

- Service de différenciation qui recherche les différences minimales entre deux séquences d’objets.

- Système pour décrire le texte dans une mémoire tampon en termes de sous-ensembles du texte dans d’autres mémoires tampons.

Le sous-système de modèle de texte est exempt de concepts de l’interface utilisateur. Par exemple, il n’est pas responsable de la mise en forme du texte ou de la disposition du texte, et il n’a aucune connaissance des ornements visuels qui peuvent être associés au texte.

Les types publics du sous-système de modèle de texte sont contenus dans *Microsoft.VisualStudio.Text.Data.dll* et *Microsoft.VisualStudio.CoreUtility.dll*, qui dépendent uniquement de la bibliothèque de classes de base .NET Framework et de l’Managed Extensibility Framework (MEF).

### <a name="text-view-subsystem"></a>Sous-système d’affichage de texte

Le sous-système d’affichage de texte est responsable de la mise en forme et de l’affichage du texte. Les types de ce sous-système sont divisés en deux couches, selon que les types reposent sur Windows Presentation Foundation (WPF). Les types les plus importants sont <xref:Microsoft.VisualStudio.Text.Editor.ITextView> et <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView> , qui contrôlent le jeu de lignes de texte à afficher, ainsi que le signe insertion, la sélection et les fonctionnalités pour orner le texte à l’aide d’éléments d’interface utilisateur WPF. Ce sous-système fournit également des marges autour de la zone d’affichage de texte. Ces marges peuvent être étendues et peuvent contenir différents types de contenu et d’effets visuels. Les affichages de numéros de ligne et les barres de défilement sont des exemples de marges.

Les types publics du sous-système d’affichage de texte sont contenus dans *Microsoft.VisualStudio.Text.UI.dll* et *Microsoft.VisualStudio.Text.UI.Wpf.dll*. Le premier assembly contient les éléments indépendants de la plateforme, tandis que le second contient les éléments spécifiques à WPF.

### <a name="classification-subsystem"></a>Sous-système de classification

Le sous-système de classification est chargé de déterminer les propriétés de police du texte. Un classifieur divise le texte en différentes classes, par exemple « keyword » ou « comment ». La carte de format de classification associe ces classes à des propriétés de police réelles, par exemple, « Blue consolas 10 PT ». Ces informations sont utilisées par l’affichage de texte lorsqu’il met en forme et restitue le texte. Le balisage, qui est décrit plus en détail plus loin dans cette rubrique, permet aux données d’être associées à des étendues de texte.

Les types publics du sous-système de classification sont contenus dans Microsoft.VisualStudio.Text.Logic.dll, et ils interagissent avec les aspects visuels de la classification, qui sont contenus dans Microsoft.VisualStudio.Text.UI.Wpf.dll.

### <a name="operations-subsystem"></a>Sous-système d’opérations

Le sous-système Operations définit le comportement de l’éditeur. Il fournit l’implémentation pour les commandes de l’éditeur Visual Studio et le système d’annulation.

## <a name="a-closer-look-at-the-text-model-and-the-text-view"></a>Examen plus approfondi du modèle de texte et de la vue de texte

### <a name="the-text-model"></a>Modèle de texte

Le sous-système de modèle de texte se compose de différents regroupements de types de texte. Il s’agit notamment de la mémoire tampon de texte, des instantanés de texte et des étendues de texte.

#### <a name="text-buffers-and-text-snapshots"></a>Mémoires tampons de texte et instantanés de texte

L' <xref:Microsoft.VisualStudio.Text.ITextBuffer> interface représente une séquence de caractères Unicode qui sont encodés à l’aide d’UTF-16, qui est l’encodage utilisé par le `String` type dans la .NET Framework. Une mémoire tampon de texte peut être conservée sous la forme d’un document de système de fichiers, mais cela n’est pas obligatoire.

<xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>Est utilisé pour créer une mémoire tampon de texte vide ou une mémoire tampon de texte qui est initialisée à partir d’une chaîne ou de <xref:System.IO.TextReader> . La mémoire tampon de texte peut être rendue persistante dans le système de fichiers en tant que <xref:Microsoft.VisualStudio.Text.ITextDocument> .

Tout thread peut modifier la mémoire tampon de texte jusqu’à ce qu’un thread prenne possession de la mémoire tampon de texte en appelant <xref:Microsoft.VisualStudio.Text.ITextBuffer.TakeThreadOwnership%2A> . Après cela, seul ce thread peut effectuer des modifications.

Une mémoire tampon de texte peut traverser de nombreuses versions pendant sa durée de vie. Une nouvelle version est générée chaque fois que la mémoire tampon est modifiée et une immuable <xref:Microsoft.VisualStudio.Text.ITextSnapshot> représente le contenu de cette version de la mémoire tampon. Étant donné que les instantanés de texte sont immuables, vous pouvez accéder à un instantané de texte sur n’importe quel thread, sans restrictions, même si la mémoire tampon de texte qu’il représente continue à changer.

#### <a name="text-snapshots-and-text-snapshot-lines"></a>Instantanés de texte et lignes d’instantanés de texte

Vous pouvez afficher le contenu d’un instantané de texte sous la forme d’une séquence de caractères ou d’une séquence de lignes. Les caractères et les lignes sont indexés à la fois à partir de zéro. Un instantané de texte vide ne contient aucun caractère et une ligne vide. Une ligne est délimitée par une séquence de caractères de saut de ligne Unicode valide ou par le début ou la fin de la mémoire tampon. Les caractères de saut de ligne sont explicitement représentés dans l’instantané de texte, et les sauts de ligne dans un instantané de texte ne doivent pas nécessairement être identiques.

> [!NOTE]
> Pour plus d’informations sur les caractères de saut de ligne dans l’éditeur Visual Studio, consultez [encodages et sauts de ligne](../ide/encodings-and-line-breaks.md).

Une ligne de texte est représentée par un <xref:Microsoft.VisualStudio.Text.ITextSnapshotLine> objet, qui peut être obtenu à partir d’un instantané de texte pour un numéro de ligne particulier ou pour une position de caractère particulière.

#### <a name="snapshotpoints-snapshotspans-and-normalizedsnapshotspancollections"></a>SnapshotPoints, SnapshotSpans et NormalizedSnapshotSpanCollections

Un <xref:Microsoft.VisualStudio.Text.SnapshotPoint> représente une position de caractère dans un instantané. La position est garantie de se situer entre zéro et la longueur de l’instantané. Un <xref:Microsoft.VisualStudio.Text.SnapshotSpan> représente une étendue de texte dans un instantané. Sa position de fin est garantie de se situer entre zéro et la longueur de l’instantané. Le <xref:Microsoft.VisualStudio.Text.NormalizedSnapshotSpanCollection> se compose d’un ensemble d' <xref:Microsoft.VisualStudio.Text.SnapshotSpan> objets provenant du même instantané.

#### <a name="spans-and-normalizedspancollections"></a>Étendues et NormalizedSpanCollections

Un <xref:Microsoft.VisualStudio.Text.Span> représente un intervalle qui peut être appliqué à une étendue de texte dans un instantané de texte. Les positions des instantanés sont de base zéro, de sorte que les étendues peuvent commencer à n’importe quelle position, y compris zéro. La `End` propriété d’une étendue est égale à la somme de sa `Start` propriété et de sa `Length` propriété. `Span`N’inclut pas le caractère indexé par la `End` propriété. Par exemple, une étendue qui a Start = 5 et Length = 3 a end = 8, et inclut les caractères aux positions 5, 6 et 7. La notation de cette étendue est [5.. 8).

Deux étendues se croisent si elles ont des positions en commun, y compris la position de fin. Par conséquent, l’intersection de [3, 5) et [2, 7) est [3, 5) et l’intersection de [3, 5) et [5, 7] est [5, 5). (Notez que [5, 5) est une étendue vide.)

Deux étendues se chevauchent si elles ont des positions en commun, à l’exception de la position de fin. Une étendue vide ne chevauche jamais d’autres étendues, et le chevauchement de deux étendues n’est jamais vide.

Un <xref:Microsoft.VisualStudio.Text.NormalizedSpanCollection> est une liste d’étendues dans l’ordre des propriétés de démarrage des étendues. Dans la liste, les étendues chevauchées ou contiguës sont fusionnées. Par exemple, étant donné le jeu d’étendues [5.. 9), [0.. 1], [3.. 6) et [9.. 10), la liste normalisée des étendues est [0.. 1], [3.. 10].

#### <a name="itextedit-textversion-and-text-change-notifications"></a>Notifications de modification de ITextEdit, TextVersion et Text

Le contenu d’une mémoire tampon de texte peut être modifié à l’aide d’un <xref:Microsoft.VisualStudio.Text.ITextEdit> objet. La création d’un tel objet (à l’aide de l’une des `CreateEdit()` méthodes de <xref:Microsoft.VisualStudio.Text.ITextBuffer> ) démarre une transaction texte qui se compose de modifications de texte. Chaque modification est un remplacement d’une plage de texte dans la mémoire tampon par une chaîne. Les coordonnées et le contenu de chaque modification sont exprimés en fonction de l’instantané de la mémoire tampon lors du démarrage de la transaction. L' <xref:Microsoft.VisualStudio.Text.ITextEdit> objet ajuste les coordonnées des modifications affectées par d’autres modifications dans la même transaction.

Par exemple, considérez une mémoire tampon de texte qui contient cette chaîne :

```
abcdefghij
```

Appliquez une transaction qui contient deux modifications, une modification qui remplace l’étendue à [2.. 4) à l’aide du caractère `X` et d’une deuxième modification qui remplace l’étendue à [6.. 9) par le caractère `Y` . Le résultat est le suivant :

```
abXefYj
```

Les coordonnées de la deuxième modification ont été calculées par rapport au contenu de la mémoire tampon au début de la transaction, avant l’application de la première modification.

Les modifications apportées à la mémoire tampon prennent effet lorsque l' <xref:Microsoft.VisualStudio.Text.ITextEdit> objet est validé en appelant sa `Apply()` méthode. Si au moins une modification n’est pas vide, une nouvelle <xref:Microsoft.VisualStudio.Text.ITextVersion> est créée, un nouveau <xref:Microsoft.VisualStudio.Text.ITextSnapshot> est créé et un `Changed` événement est déclenché. Chaque version texte possède un instantané de texte différent. Un instantané de texte représente l’état complet de la mémoire tampon de texte après une transaction de modification, mais une version de texte décrit uniquement les modifications d’un instantané à la suivante. En général, les instantanés de texte sont censés être utilisés une seule fois, puis ignorés, tandis que les versions de texte doivent rester actives pendant un certain temps.

Une version texte contient un <xref:Microsoft.VisualStudio.Text.INormalizedTextChangeCollection> . Cette collection décrit les modifications qui, lorsqu’elles sont appliquées à l’instantané, produisent l’instantané suivant. Chaque <xref:Microsoft.VisualStudio.Text.ITextChange> dans la collection contient la position de caractère de la modification, la chaîne remplacée et la chaîne de remplacement. La chaîne remplacée est vide pour une insertion de base, et la chaîne de remplacement est vide pour une suppression de base. La collection normalisée est toujours `null` pour la version la plus récente de la mémoire tampon de texte.

Un seul <xref:Microsoft.VisualStudio.Text.ITextEdit> objet peut être instancié pour une mémoire tampon de texte à tout moment, et toutes les modifications de texte doivent être effectuées sur le thread qui possède la mémoire tampon de texte (si la propriété a été revendiquée). Une modification de texte peut être abandonnée en appelant sa `Cancel` méthode ou sa `Dispose` méthode.

<xref:Microsoft.VisualStudio.Text.ITextBuffer> fournit également `Insert()` des `Delete()` méthodes, et `Replace()` qui ressemblent à celles trouvées sur l' <xref:Microsoft.VisualStudio.Text.ITextEdit> interface. L’appel de celles-ci a le même effet que la création d’un <xref:Microsoft.VisualStudio.Text.ITextEdit> objet, l’appel similaire, puis l’application de la modification.

#### <a name="tracking-points-and-tracking-spans"></a>Points de suivi et étendues de suivi

Un <xref:Microsoft.VisualStudio.Text.ITrackingPoint> représente une position de caractère dans une mémoire tampon de texte. Si la mémoire tampon est modifiée d’une manière qui provoque le décalage de la position du caractère, le point de suivi le décale. Par exemple, si un point de suivi fait référence à la position 10 dans une mémoire tampon et que cinq caractères sont insérés au début de la mémoire tampon, le point de suivi fait alors référence à la position 15. Si une insertion se produit précisément à la position notée par le point de suivi, son comportement est déterminé par son <xref:Microsoft.VisualStudio.Text.PointTrackingMode> , qui peut être `Positive` ou `Negative` . Si le mode de suivi est positif, le point de suivi fait référence au même caractère, qui est maintenant à la fin de l’insertion. Si le mode de suivi est négatif, le point de suivi fait référence au premier caractère inséré à la position d’origine. Si le caractère situé à la position représentée par un point de suivi est supprimé, le point de suivi se déplace vers le premier caractère qui suit la plage supprimée. Par exemple, si un point de suivi fait référence au caractère situé à la position 5 et que les caractères situés aux positions 3 à 6 sont supprimés, le point de suivi fait référence au caractère situé à la position 3.

Un <xref:Microsoft.VisualStudio.Text.ITrackingSpan> représente une plage de caractères au lieu d’une seule position. Son comportement est déterminé par son <xref:Microsoft.VisualStudio.Text.SpanTrackingMode> . Si le mode de suivi d’étendue est [SpanTrackingMode. EdgeInclusive](xref:Microsoft.VisualStudio.Text.SpanTrackingMode.EdgeInclusive), l’étendue de suivi augmente pour incorporer le texte inséré à ses bords. Si le mode de suivi d’étendue est [SpanTrackingMode. EdgeExclusive](xref:Microsoft.VisualStudio.Text.SpanTrackingMode.EdgeExclusive), l’étendue de suivi n’incorpore pas de texte inséré à ses bords. Toutefois, si le mode de suivi span est [SpanTrackingMode. EdgePositive](xref:Microsoft.VisualStudio.Text.SpanTrackingMode.EdgePositive), une insertion pousse la position actuelle vers le début, et si le mode de suivi span est [SpanTrackingMode. EdgeNegative](xref:Microsoft.VisualStudio.Text.SpanTrackingMode.EdgeNegative), une insertion pousse la position actuelle vers la fin.

Vous pouvez obtenir la position d’un point de suivi ou l’étendue d’une étendue de suivi pour tout instantané de la mémoire tampon de texte à laquelle ils appartiennent. Les points de suivi et les étendues de suivi peuvent être référencés en toute sécurité à partir de n’importe quel thread.

#### <a name="content-types"></a>Types de contenu

Les types de contenu sont un mécanisme permettant de définir différents types de contenu. Un type de contenu peut être un type de fichier tel que « Text », « code » ou « Binary », ou un type de technologie tel que « XML », « vb » ou « c# ». Par exemple, le mot « using » est un mot clé en C# et Visual Basic, mais pas dans d’autres langages de programmation. Par conséquent, la définition de ce mot clé est limitée aux types de contenu « c# » et « VB ».

Les types de contenu sont utilisés comme filtre pour les ornements et d’autres éléments de l’éditeur. De nombreuses fonctionnalités et points d’extension de l’éditeur sont définis par type de contenu. Par exemple, la coloration du texte est différente pour les fichiers texte bruts, les fichiers XML et les fichiers de code source Visual Basic. Les mémoires tampons de texte reçoivent généralement un type de contenu lors de leur création, et le type de contenu d’une mémoire tampon de texte peut être modifié.

Les types de contenu peuvent hériter de plusieurs types de contenu. <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition>Vous permet de spécifier plusieurs types de base comme parents d’un type de contenu donné.

Les développeurs peuvent définir leurs propres types de contenu et les inscrire à l’aide du <xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService> . De nombreuses fonctionnalités de l’éditeur peuvent être définies par rapport à un type de contenu spécifique à l’aide du <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> . Par exemple, les marges, les ornements et les gestionnaires de souris de l’éditeur peuvent être définis de sorte qu’ils s’appliquent uniquement aux éditeurs qui affichent des types de contenu particuliers.

### <a name="the-text-view"></a>Affichage de texte

La partie vue du modèle MVC (Model View Controller) définit l’affichage de texte, la mise en forme de la vue, les éléments graphiques tels que la barre de défilement et le signe insertion. Tous les éléments de présentation de l’éditeur Visual Studio sont basés sur WPF.

#### <a name="text-views"></a>Affichages de texte

L' <xref:Microsoft.VisualStudio.Text.Editor.ITextView> interface est une représentation indépendante de la plateforme d’un affichage de texte. Il est principalement utilisé pour afficher des documents texte dans une fenêtre, mais il peut également être utilisé à d’autres fins, par exemple dans une info-bulle.

L’affichage de texte fait référence à différents genres de mémoires tampons de texte. La <xref:Microsoft.VisualStudio.Text.Editor.ITextView.TextViewModel%2A> propriété fait référence à un <xref:Microsoft.VisualStudio.Text.Editor.ITextViewModel> objet qui pointe vers ces trois mémoires tampons de texte différentes : la mémoire tampon de données, qui est la mémoire tampon de niveau de données la plus haute, la mémoire tampon d’édition dans laquelle la modification se produit et la mémoire tampon visuelle, qui est la mémoire tampon affichée dans l’affichage de texte.

Le texte est mis en forme en fonction des classifieurs attachés à la mémoire tampon de texte sous-jacente et est orné à l’aide des fournisseurs d’ornements attachés à l’affichage de texte lui-même.

#### <a name="the-text-view-coordinate-system"></a>Système de coordonnées d’affichage de texte

Le système de coordonnées d’affichage de texte spécifie des positions dans l’affichage de texte. Dans ce système de coordonnées, la valeur x 0,0 correspond au bord gauche du texte affiché, tandis que la valeur y 0,0 correspond au bord supérieur du texte affiché. La coordonnée x augmente de gauche à droite, et la coordonnée y s’incrémente de haut en bas.

Il n’est pas possible de faire défiler une fenêtre d’affichage (partie du texte visible dans la fenêtre de texte) de la même manière horizontale qu’en faisant défiler verticalement. Un Viewport défile horizontalement en modifiant sa coordonnée gauche afin qu’il se déplace par rapport à la surface de dessin. Toutefois, il est possible de faire défiler verticalement un Viewport uniquement en modifiant le texte rendu, ce qui entraîne le <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> déclenchement d’un événement.

Les distances dans le système de coordonnées correspondent aux pixels logiques. Si la surface de rendu du texte s’affiche sans transformation de mise à l’échelle, une unité dans le système de coordonnées d’affichage du texte correspond à un pixel sur l’affichage.

#### <a name="margins"></a>Marges

L' <xref:Microsoft.VisualStudio.Text.Editor.ITextViewMargin> interface représente une marge et permet de contrôler la visibilité de la marge et sa taille. Quatre marges prédéfinies, appelées « Top », « Left », « Right » et « Bottom », sont attachées au bord supérieur, inférieur, gauche ou droit d’une vue. Ces marges sont des conteneurs dans lesquels d’autres marges peuvent être placées. L’interface définit des méthodes qui retournent la taille de la marge et la visibilité d’une marge. Les marges sont des éléments visuels qui fournissent des informations supplémentaires sur la vue de texte à laquelle elles sont jointes. Par exemple, la marge de nombre de lignes affiche des numéros de ligne pour l’affichage de texte. La marge de glyphe affiche des éléments d’interface utilisateur.

L' <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMarginProvider> interface gère la création et l’emplacement des marges. Les marges peuvent être classées par rapport à d’autres marges. Les marges de priorité supérieure sont situées plus près de l’affichage de texte. Par exemple, s’il y a deux marges gauches, les marges A et B, et la marge B a une priorité inférieure à la marge A, la marge B apparaît à gauche de la marge A.

#### <a name="the-text-view-host"></a>Hôte d’affichage de texte

L' <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> interface contient l’affichage de texte et les décorations contiguës qui accompagnent la vue, par exemple, les barres de défilement. L’hôte d’affichage de texte contient également des marges attachées à une bordure de la vue.

#### <a name="formatted-text"></a>Texte mis en forme

Le texte affiché dans une vue de texte est composé d' <xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine> objets. Chaque ligne de vue de texte correspond à une ligne de texte dans l’affichage de texte. Les longues lignes de la mémoire tampon de texte sous-jacente peuvent être partiellement masquées (si le retour automatique à la ligne n’est pas activé) ou être divisées en plusieurs lignes de vue de texte. L' <xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine> interface contient des méthodes et des propriétés pour le mappage entre les coordonnées et les caractères, et pour les ornements qui peuvent être associés à la ligne.

<xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine> les objets sont créés à l’aide d’une <xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource> interface. Si vous vous intéressez uniquement au texte actuellement affiché dans la vue, vous pouvez ignorer la source de mise en forme. Si le format de texte qui n’est pas affiché dans la vue vous intéresse (par exemple, pour prendre en charge une copie et un collage de texte enrichi), vous pouvez utiliser <xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource> pour mettre en forme le texte dans une mémoire tampon de texte.

Le format de l’affichage de texte est un <xref:Microsoft.VisualStudio.Text.ITextSnapshotLine> à la fois.

## <a name="editor-features"></a>Fonctionnalités de l’éditeur

Les fonctionnalités de l’éditeur sont conçues pour que la définition de la fonctionnalité soit distincte de son implémentation. L’éditeur comprend les fonctionnalités suivantes :

- Balises et classifieurs

- Ornements

- Projection

- mode Plan

- Combinaisons de touches et de souris

- Opérations et Primitives

- IntelliSense

### <a name="tags-and-classifiers"></a>Balises et classifieurs

Les balises sont des marqueurs qui sont associés à une étendue de texte. Elles peuvent être présentées de différentes façons, par exemple en utilisant des couleurs de texte, des soulignements, des graphiques ou des fenêtres contextuelles. Les classifieurs représentent un type de balise.

D’autres types de balises sont <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> pour la mise en surbrillance du texte, <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag> pour le mode plan et <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag> pour les erreurs de compilation.

#### <a name="classification-types"></a>Types de classification

Une <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType> interface représente une classe d’équivalence, qui est une catégorie abstraite de texte. Les types de classification peuvent hériter de plusieurs types de classification. Par exemple, les classifications de langage de programmation peuvent inclure « Keyword », « comment » et « identifier », qui héritent toutes de « code ». Les types de classifications de langage naturel peuvent inclure « substantif », « Verb » et « adjectif », qui héritent tous de « Natural Language ».

#### <a name="classifications"></a>Classifications

Une classification est une instance d’un type de classification particulier, généralement sur une étendue de texte. Un <xref:Microsoft.VisualStudio.Text.Classification.ClassificationSpan> est utilisé pour représenter une classification. Une étendue de classification peut être considérée comme une étiquette qui couvre une étendue de texte particulière et indique au système que cette étendue de texte est d’un type de classification particulier.

#### <a name="classifiers"></a>Classifieurs

Un <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> est un mécanisme qui divise le texte en un ensemble de classifications. Les classifieurs doivent être définis pour des types de contenu spécifiques et instanciés pour des mémoires tampons de texte spécifiques. Les clients doivent implémenter <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> pour participer à la classification de texte.

#### <a name="classifier-aggregators"></a>Agrégateurs de classifieur

Une agrégation de classifieur est un mécanisme qui combine tous les classifieurs d’une mémoire tampon de texte en un seul jeu de classifications. Par exemple, un classifieur C# et un classifieur de langue anglaise peuvent créer des classifications sur un commentaire dans un fichier C#. Considérez ce commentaire :

```
// This method produces a classifier
```

Un classifieur C# peut étiqueter l’étendue entière en tant que commentaire, et le classifieur de langue anglaise peut classer « produit » comme « verbe » et « méthode » comme « substantif ». L’agrégateur produit un ensemble de classifications qui ne se chevauchent pas et le type de l’ensemble est basé sur toutes les contributions.

Un agrégateur de classifieur est également un classifieur, car il divise le texte en un ensemble de classifications. L’agrégation de classifieur vérifie également qu’il n’y a aucune classification qui se chevauche et que les classifications sont triées. Les classifieurs individuels sont libres de retourner tout ensemble de classifications, dans n’importe quel ordre, et de se chevaucher de quelque manière que ce soit.

#### <a name="classification-formatting-and-text-coloring"></a>Mise en forme de la classification et coloration du texte

La mise en forme du texte est un exemple de fonctionnalité basée sur la classification de texte. Elle est utilisée par la couche d’affichage de texte pour déterminer l’affichage du texte dans une application. La zone de mise en forme du texte dépend de WPF, mais pas de la définition logique des classifications.

Un format de classification est un ensemble de propriétés de mise en forme pour un type de classification spécifique. Ces formats héritent du format du parent du type de classification.

Un <xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMap> est un mappage d’un type de classification à un ensemble de propriétés de mise en forme de texte. L’implémentation de la carte de mise en forme dans l’éditeur gère toutes les exportations des formats de classification.

### <a name="adornments"></a>Ornements

Les ornements sont des effets graphiques qui ne sont pas directement liés à la police et à la couleur des caractères de l’affichage de texte. Par exemple, le trait de soulignement en tilde rouge qui est utilisé pour marquer du code non compilé dans de nombreux langages de programmation est un ornement incorporé, et les info-bulles sont des ornements contextuels. Les ornements sont dérivés de <xref:System.Windows.UIElement> et implémentent <xref:Microsoft.VisualStudio.Text.Tagging.ITag> . Les deux types spécialisés de balise d’ornement sont <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag> , pour les ornements qui occupent le même espace que le texte d’une vue, et le <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag> , pour le trait de soulignement en tilde.

Les ornements incorporés sont des graphiques qui font partie de la vue de texte mise en forme. Ils sont organisés dans différentes couches d’ordre de plan. Il existe trois couches intégrées, comme suit : texte, signe insertion et sélection. Toutefois, les développeurs peuvent définir plus de couches et les placer dans l’ordre des uns avec les autres. Les trois types d’ornements incorporés sont des ornements relatifs au texte (qui se déplacent lorsque le texte se déplace et sont supprimés lors de la suppression du texte), des ornements relatifs à la vue (qui doivent être associés à des parties non textuelles de la vue) et des ornements contrôlés par le propriétaire (le développeur doit gérer leur positionnement).

Les ornements contextuels sont des graphiques qui s’affichent dans une petite fenêtre au-dessus de l’affichage de texte, par exemple, des info-bulles.

### <a name="projection"></a><a name="projection"></a> Projection

La projection est une technique permettant de construire un type différent de mémoire tampon de texte qui ne stocke pas réellement de texte, mais combine le texte d’autres mémoires tampons de texte. Par exemple, une mémoire tampon de projection peut être utilisée pour concaténer le texte de deux autres mémoires tampons et présenter le résultat comme s’il s’agissait d’une seule mémoire tampon, ou pour masquer des parties du texte dans une mémoire tampon. Une mémoire tampon de projection peut agir comme une mémoire tampon source pour une autre mémoire tampon de projection. Un ensemble de mémoires tampons liées par projection peut être construit pour réorganiser le texte de différentes façons. (Un tel ensemble est également appelé graphique de *mémoire tampon*.) La fonctionnalité de mode plan de texte de Visual Studio est implémentée à l’aide d’une mémoire tampon de projection pour masquer le texte réduit, et l’éditeur Visual Studio pour les pages ASP.NET utilise la projection pour prendre en charge des langages incorporés tels que Visual Basic et C#.

Un <xref:Microsoft.VisualStudio.Text.Projection.IProjectionBuffer> est créé à l’aide de <xref:Microsoft.VisualStudio.Text.Projection.IProjectionBufferFactoryService> . Une mémoire tampon de projection est représentée par une séquence ordonnée d' <xref:Microsoft.VisualStudio.Text.ITrackingSpan> objets qui sont appelés *étendues de source*. Le contenu de ces étendues est présenté sous la forme d’une séquence de caractères. Les mémoires tampons de texte à partir desquelles les étendues sources sont dessinées sont des *mémoires tampons sources* nommées. Les clients d’une mémoire tampon de projection n’ont pas besoin de savoir qu’ils diffèrent d’une mémoire tampon de texte ordinaire.

La mémoire tampon de projection écoute les événements de modification de texte sur les mémoires tampons sources. Lorsque le texte d’une étendue source change, la mémoire tampon de projection mappe les coordonnées de texte modifiées à ses propres coordonnées et déclenche des événements de modification de texte appropriés. Par exemple, considérez les mémoires tampons sources A et B qui ont le contenu suivant :

```
A: ABCDE
B: vwxyz
```

Si la mémoire tampon de projection P est formée à partir de deux étendues de texte, une qui a la totalité de la mémoire tampon a et l’autre qui a la totalité de la mémoire tampon B, P a le contenu suivant :

```
P: ABCDEvwxyz
```

Si la sous-chaîne `xy` est supprimée de la mémoire tampon B, la mémoire tampon P déclenche un événement qui indique que les caractères aux positions 7 et 8 ont été supprimés.

La mémoire tampon de projection peut également être modifiée directement. Il propage les modifications aux mémoires tampons sources appropriées. Par exemple, si une chaîne est insérée dans la mémoire tampon P à la position 6 (position d’origine du caractère « v »), l’insertion est propagée vers la mémoire tampon B à la position 1.

Il existe des restrictions sur les étendues de source qui contribuent à une mémoire tampon de projection. Les étendues de source peuvent ne pas se chevaucher ; un emplacement dans une mémoire tampon de projection ne peut pas être mappé à plusieurs emplacements dans une mémoire tampon source, et un emplacement dans une mémoire tampon source ne peut pas être mappé à plusieurs emplacements dans une mémoire tampon de projection. Aucune circularité n’est autorisée dans la relation de mémoire tampon source.

Les événements sont déclenchés lorsque l’ensemble de mémoires tampons sources pour une mémoire tampon de projection change et lorsque le jeu d’étendues de la source change.
Une mémoire tampon d’élision est un type spécial de mémoire tampon de projection. Il est principalement utilisé pour le mode plan et pour les opérations qui développent et réduisent des blocs de texte. Une mémoire tampon d’élision est basée sur une seule mémoire tampon source, et les étendues de la mémoire tampon d’élision doivent être ordonnées de la même façon qu’elles sont ordonnées dans la mémoire tampon source.

#### <a name="the-buffer-graph"></a>Graphique de mémoire tampon

L' <xref:Microsoft.VisualStudio.Text.Projection.IBufferGraph> interface active le mappage sur un graphique de mémoires tampons de projection. Toutes les mémoires tampons de texte et mémoires tampons de projection sont collectées dans un graphique acycliques dirigé, de façon similaire à l’arborescence de syntaxe abstraite générée par un compilateur de langage. Le graphique est défini par la mémoire tampon supérieure, qui peut être n’importe quelle mémoire tampon de texte. Le graphique de mémoire tampon peut être mappé d’un point de la mémoire tampon supérieure à un point d’une mémoire tampon source, ou d’une étendue dans la mémoire tampon supérieure à un ensemble d’étendues dans une mémoire tampon source. De même, il peut mapper un point ou une étendue d’une mémoire tampon source à un point dans la mémoire tampon supérieure. Les graphiques de mémoire tampon sont créés à l’aide du <xref:Microsoft.VisualStudio.Text.Projection.IBufferGraphFactoryService> .

#### <a name="events-and-projection-buffers"></a>Mémoires tampons d’événements et de projection

Lorsqu’une mémoire tampon de projection est modifiée, les modifications sont envoyées de la mémoire tampon de projection aux mémoires tampons qui en dépendent. Une fois que toutes les mémoires tampons ont été modifiées, les événements de modification de mémoire tampon sont déclenchés, en commençant par la mémoire tampon la plus profonde.

### <a name="outlining"></a>mode Plan

Le mode plan permet de développer ou de réduire différents blocs de texte dans une vue de texte. Le mode plan est défini comme un type de <xref:Microsoft.VisualStudio.Text.Tagging.ITag> , de la même façon que les ornements sont définis. Un <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag> est une balise qui définit une zone de texte qui peut être développée ou réduite. Pour utiliser le mode plan, vous devez importer le <xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManagerService> pour récupérer un <xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManager> . Le gestionnaire de mode plan énumère, réduit et développe les différents blocs, représentés sous forme d' <xref:Microsoft.VisualStudio.Text.Outlining.ICollapsible> objets, et déclenche les événements en conséquence.

### <a name="mouse-bindings"></a>Liaisons de la souris

Les liaisons de la souris lient les mouvements de la souris à différentes commandes. Les liaisons de souris sont définies à l’aide d’un <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessorProvider> , et les combinaisons de touches sont définies à l’aide d’un <xref:Microsoft.VisualStudio.Text.Editor.IKeyProcessorProvider> . <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost>Instancie automatiquement toutes les liaisons et les connecte aux événements de souris dans la vue.

L' <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessor> interface contient des gestionnaires d’événements de prétraitement et de prétraitement pour différents événements de souris. Pour gérer l’un des événements, vous pouvez substituer certaines des méthodes dans <xref:Microsoft.VisualStudio.Text.Editor.MouseProcessorBase> .

### <a name="editor-operations"></a>Opérations de l’éditeur

Les opérations de l’éditeur peuvent être utilisées pour automatiser l’interaction avec l’éditeur, à des fins de script ou à d’autres fins. Vous pouvez importer le <xref:Microsoft.VisualStudio.Text.Operations.IEditorOperationsFactoryService> pour accéder aux opérations sur un donné <xref:Microsoft.VisualStudio.Text.Editor.ITextView> . Vous pouvez ensuite utiliser ces objets pour modifier la sélection, faire défiler la vue ou placer le signe insertion sur différentes parties de la vue.

### <a name="intellisense"></a>IntelliSense

IntelliSense prend en charge la saisie semi-automatique des instructions, l’aide sur la signature (également appelée informations sur les paramètres), info Express et ampoules.

La saisie semi-automatique des instructions fournit des listes contextuelles d’achèvement potentiel pour les noms de méthode, les éléments XML et d’autres éléments de codage ou de balisage. En général, un mouvement utilisateur appelle une session de saisie semi-automatique. La session affiche la liste des saisies semi-automatiques potentielles et l’utilisateur peut en sélectionner un ou faire disparaître la liste. La <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker> est chargée de créer et de déclencher le <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSession> . <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource>Calcule le <xref:Microsoft.VisualStudio.Language.Intellisense.CompletionSet> des éléments de saisie semi-automatique pour la session.

## <a name="see-also"></a>Voir aussi

- [Points d’extension du service de langage et de l’éditeur](../extensibility/language-service-and-editor-extension-points.md)
- [Importations de l’éditeur](../extensibility/editor-imports.md)
