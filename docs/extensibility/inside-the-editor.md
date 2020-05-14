---
title: Dans l’éditeur
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
ms.openlocfilehash: bba0b5192df53b6ec837b0030c7b236bf8e08dea
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710327"
---
# <a name="inside-the-editor"></a>À l’intérieur de l’éditeur

L’éditeur est composé de plusieurs sous-systèmes différents, qui sont conçus pour garder le modèle de texte de l’éditeur séparé de la vue du texte et l’interface utilisateur.

Ces sections décrivent différents aspects de l’éditeur :

- [Aperçu des sous-systèmes](../extensibility/inside-the-editor.md#overview-of-the-subsystems)

- [Le modèle de texte](../extensibility/inside-the-editor.md#the-text-model)

- [La vue du texte](../extensibility/inside-the-editor.md#the-text-view)

Ces sections décrivent les caractéristiques de l’éditeur :

- [Tags et classificateurs](../extensibility/inside-the-editor.md#tags-and-classifiers)

- [Ornements](../extensibility/inside-the-editor.md#adornments)

- [Projection](../extensibility/inside-the-editor.md#projection)

- [mode Plan](../extensibility/inside-the-editor.md#outlining)

- [Fixations de souris](../extensibility/inside-the-editor.md#mouse-bindings)

- [Opérations de rédacteur en chef](../extensibility/inside-the-editor.md#editor-operations)

- [IntelliSense](../extensibility/inside-the-editor.md#intellisense)

## <a name="overview-of-the-subsystems"></a>Aperçu des sous-systèmes

### <a name="text-model-subsystem"></a>Sous-système de modèle de texte

Le sous-système du modèle de texte est chargé de représenter le texte et de permettre sa manipulation. Le sous-système du <xref:Microsoft.VisualStudio.Text.ITextBuffer> modèle de texte contient l’interface, qui décrit la séquence des caractères qui doit être affichée par l’éditeur. Ce texte peut être modifié, suivi et manipulé autrement de plusieurs façons. Le modèle de texte fournit également des types pour les aspects suivants :

- Un service qui associe le texte avec des fichiers, et gère la lecture et l’écriture dans le système de fichiers.

- Un service de différenciation qui trouve les différences minimales entre deux séquences d’objets.

- Un système pour décrire le texte dans un tampon en termes de sous-ensembles du texte dans d’autres tampons.

Le sous-système du modèle de texte est exempt de concepts d’interface utilisateur (interface utilisateur). Par exemple, il n’est pas responsable du formatage de texte ou de la mise en page du texte, et il n’a aucune connaissance des ornements visuels qui peuvent être associés au texte.

Les types publics du sous-système du modèle de texte sont contenus dans *Microsoft.VisualStudio.Text.Data.dll* et *Microsoft.VisualStudio.CoreUtility.dll*, qui ne dépendent que de la bibliothèque de la classe de base .NET Framework et du Cadre d’exténuabilité gérée (MEF).

### <a name="text-view-subsystem"></a>Sous-système de vue de texte

Le sous-système de vue de texte est responsable du formatage et de l’affichage du texte. Les types de ce sous-système sont divisés en deux couches, selon que les types s’appuient sur Windows Presentation Foundation (WPF). Les types les <xref:Microsoft.VisualStudio.Text.Editor.ITextView> <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>plus importants sont et , qui contrôlent l’ensemble des lignes de texte qui doivent être affichés, et aussi le caret, la sélection, et les installations pour orner le texte en utilisant des éléments wPF UI. Ce sous-système fournit également des marges autour de la zone d’affichage du texte. Ces marges peuvent être prolongées et peuvent contenir différents types de contenu et d’effets visuels. Des exemples de marges sont les affichages de numéros de ligne et les barres de défilement.

Les types publics du sous-système de vue de texte sont contenus dans *Microsoft.VisualStudio.Text.UI.dll* et *Microsoft.VisualStudio.Text.UI.Wpf.dll*. La première assemblée contient les éléments indépendants de la plate-forme, et le second contient les éléments spécifiques au WPF.

### <a name="classification-subsystem"></a>Sous-système de classification

Le sous-système de classification est chargé de déterminer les propriétés de police pour le texte. Un classificateur divise le texte en différentes classes, par exemple, "mot-clé" ou "commentaire". La carte du format de classification relie ces classes aux propriétés de police réelles, par exemple, "Blue Consolas 10 pt". Ces informations sont utilisées par la vue textuelle lorsqu’elles formate et rendent du texte. Le marquage, qui est décrit plus en détail plus tard dans ce sujet, permet d’associer les données à des travées de texte.

Les types publics du sous-système de classification sont contenus dans Microsoft.VisualStudio.Text.Logic.dll, et ils interagissent avec les aspects visuels de la classification, qui sont contenus dans Microsoft.VisualStudio.Text.UI.Wpf.dll.

### <a name="operations-subsystem"></a>Sous-système d’opérations

Le sous-système d’opérations définit le comportement de l’éditeur. Il fournit la mise en œuvre pour les commandes d’éditeurs Visual Studio et le système de défaire.

## <a name="a-closer-look-at-the-text-model-and-the-text-view"></a>Un examen plus attentif du modèle de texte et de la vue du texte

### <a name="the-text-model"></a>Le modèle de texte

Le sous-système du modèle de texte se compose de différents groupes de types de texte. Il s’agit notamment du tampon texte, des instantanés texte et des travées de texte.

#### <a name="text-buffers-and-text-snapshots"></a>Tampons de texte et instantanés texte

L’interface <xref:Microsoft.VisualStudio.Text.ITextBuffer> représente une séquence de caractères Unicode qui sont codés en utilisant UTF-16, qui est l’encodage utilisé par le `String` type dans le cadre .NET. Un tampon de texte peut être persisté comme un document de système de fichiers, mais ce n’est pas nécessaire.

Le <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService> est utilisé pour créer un tampon de texte vide, ou <xref:System.IO.TextReader>un tampon de texte qui est initialisé à partir d’une chaîne ou de . Le tampon de texte peut être persisté au système de fichier comme un <xref:Microsoft.VisualStudio.Text.ITextDocument>.

N’importe quel thread peut modifier le tampon de <xref:Microsoft.VisualStudio.Text.ITextBuffer.TakeThreadOwnership%2A>texte jusqu’à ce qu’un thread prenne la propriété du tampon de texte en appelant . Après cela, seul ce thread peut effectuer des modifications.

Un tampon de texte peut passer par de nombreuses versions au cours de sa vie. Une nouvelle version est générée chaque fois que le <xref:Microsoft.VisualStudio.Text.ITextSnapshot> tampon est modifié, et un immuable représente le contenu de cette version du tampon. Étant donné que les instantanés de texte sont immuables, vous pouvez accéder à un instantané de texte sur n’importe quel thread, sans restrictions, même si le tampon texte qu’il représente continue de changer.

#### <a name="text-snapshots-and-text-snapshot-lines"></a>Instantanés de texte et lignes d’instantané de texte

Vous pouvez afficher le contenu d’un instantané de texte comme une séquence de caractères ou comme une séquence de lignes. Les caractères et les lignes sont tous deux indexés à partir de zéro. Un instantané de texte vide contient zéro caractère et une ligne vide. Une ligne est délimitée par toute séquence de caractères unicode valide, ou par le début ou la fin du tampon. Les caractères de rupture de ligne sont explicitement représentés dans l’instantané de texte, et les ruptures de ligne dans un instantané de texte n’ont pas toutes à être les mêmes.

> [!NOTE]
> Pour plus d’informations sur les personnages de line-break dans l’éditeur Visual Studio, voir [Encodages et sauts de ligne](../ide/encodings-and-line-breaks.md).

Une ligne de texte est <xref:Microsoft.VisualStudio.Text.ITextSnapshotLine> représentée par un objet, qui peut être obtenu à partir d’un instantané de texte pour un numéro de ligne particulier ou pour une position de caractère particulière.

#### <a name="snapshotpoints-snapshotspans-and-normalizedsnapshotspancollections"></a>SnapshotPoints, SnapshotSpans et NormalizedSnapshotSpanCollections

A <xref:Microsoft.VisualStudio.Text.SnapshotPoint> représente une position de personnage dans un instantané. La position est garantie de se situer entre zéro et la longueur de l’instantané. A <xref:Microsoft.VisualStudio.Text.SnapshotSpan> représente une durée de texte dans un instantané. Sa position de fin est garantie de se situer entre zéro et la longueur de l’instantané. Il <xref:Microsoft.VisualStudio.Text.NormalizedSnapshotSpanCollection> s’agit <xref:Microsoft.VisualStudio.Text.SnapshotSpan> d’un ensemble d’objets du même instantané.

#### <a name="spans-and-normalizedspancollections"></a>Spans et NormalizedSpanCollections

A <xref:Microsoft.VisualStudio.Text.Span> représente un intervalle qui peut être appliqué à une durée de texte dans un instantané de texte. Les positions d’instantané sont basées à zéro, de sorte que les travées peuvent commencer à n’importe quelle position, y compris zéro. La `End` propriété d’une travée `Start` est égale `Length` à la somme de sa propriété et de sa propriété. A `Span` n’inclut pas le caractère `End` qui est indexé par la propriété. Par exemple, une portée qui a Le démarrage 5 et la longueur 3 a la fin 8, et elle inclut les caractères aux positions 5, 6 et 7. La notation pour cette portée est [5..8).

Deux travées se croisent si elles ont des positions en commun, y compris la position de fin. Par conséquent, l’intersection de [3, 5) et [2, 7) est [3, 5) et l’intersection de [3, 5) et [5, 7) est [5, 5). (Remarquez que [5, 5) est une travée vide.)

Deux travées se chevauchent si elles ont des positions en commun, à l’exception de la position de fin. Une travée vide ne chevauche jamais aucune autre portée, et le chevauchement de deux travées n’est jamais vide.

A <xref:Microsoft.VisualStudio.Text.NormalizedSpanCollection> est une liste de travées dans l’ordre des propriétés Start des travées. Dans la liste, les travées qui se chevauchent ou attent sont fusionnées. Par exemple, compte tenu de l’ensemble des travées [5,9), [0,1), [3,6) et [9,10), la liste normalisée des travées est [0,1), [3,10).

#### <a name="itextedit-textversion-and-text-change-notifications"></a>ITextEdit, TextVersion, et notifications de modification de texte

Le contenu d’un tampon de <xref:Microsoft.VisualStudio.Text.ITextEdit> texte peut être modifié à l’aide d’un objet. La création d’un tel `CreateEdit()` objet <xref:Microsoft.VisualStudio.Text.ITextBuffer>(en utilisant l’une des méthodes de ) commence une transaction de texte qui se compose de modifications de texte. Chaque modification est un remplacement d’une certaine durée de texte dans le tampon par une chaîne. Les coordonnées et le contenu de chaque modification sont exprimés par rapport à l’instantané du tampon lorsque la transaction a été commencée. L’objet <xref:Microsoft.VisualStudio.Text.ITextEdit> ajuste les coordonnées des modifications qui sont affectées par d’autres modifications dans la même transaction.

Par exemple, considérez un tampon de texte qui contient cette chaîne :

```
abcdefghij
```

Appliquer une transaction qui contient deux modifications, une modification qui remplace la portée à `X` [2..4) en utilisant le personnage et une `Y`deuxième modification qui remplace la portée à [6..9) en utilisant le personnage . Le résultat est ce tampon:

```
abXefYj
```

Les coordonnées de la deuxième modification ont été calculées en ce qui concerne le contenu du tampon au début de la transaction, avant que la première modification ne soit appliquée.

Les modifications apportées au <xref:Microsoft.VisualStudio.Text.ITextEdit> tampon prennent effet `Apply()` lorsque l’objet est commis en appelant sa méthode. S’il y a eu au moins <xref:Microsoft.VisualStudio.Text.ITextVersion> un montage <xref:Microsoft.VisualStudio.Text.ITextSnapshot> non vide, `Changed` un nouveau est créé, un nouveau est créé et un événement est soulevé. Chaque version texte a un instantané de texte différent. Un instantané de texte représente l’état complet du tampon de texte après une transaction de modification, mais une version textuelle ne décrit que les modifications d’un instantané à l’autre. En général, les instantanés de texte sont destinés à être utilisés une fois et puis jetés, tandis que les versions textuelles doivent rester en vie pendant un certain temps.

Une version texte <xref:Microsoft.VisualStudio.Text.INormalizedTextChangeCollection>contient un . Cette collection décrit les modifications qui, lorsqu’elles sont appliquées à l’instantané, produisent l’instantané suivant. Chaque <xref:Microsoft.VisualStudio.Text.ITextChange> dans la collection contient la position de caractère de la modification, la chaîne remplacée, et la chaîne de remplacement. La corde remplacée est vide pour une insertion de base, et la chaîne de remplacement est vide pour une suppression de base. La collection normalisée `null` est toujours pour la version la plus récente du tampon de texte.

Un <xref:Microsoft.VisualStudio.Text.ITextEdit> seul objet peut être instantané pour un tampon de texte à tout moment, et toutes les modifications de texte doivent être effectuées sur le thread qui possède le tampon de texte (si la propriété a été revendiquée). Une modification de texte peut `Cancel` être `Dispose` abandonnée en appelant sa méthode ou sa méthode.

<xref:Microsoft.VisualStudio.Text.ITextBuffer>fournit `Insert()`également `Delete()`, `Replace()` , et les <xref:Microsoft.VisualStudio.Text.ITextEdit> méthodes qui ressemblent à celles trouvées sur l’interface. Les appeler a le même <xref:Microsoft.VisualStudio.Text.ITextEdit> effet que la création d’un objet, faire l’appel similaire, puis l’application de la modification.

#### <a name="tracking-points-and-tracking-spans"></a>Points de suivi et traque

Un <xref:Microsoft.VisualStudio.Text.ITrackingPoint> représente une position de caractère dans un tampon de texte. Si le tampon est modifié d’une manière qui provoque le changement de position du personnage, le point de suivi change avec lui. Par exemple, si un point de suivi se réfère à la position 10 dans un tampon, et cinq caractères sont insérés au début du tampon, le point de suivi se réfère alors à la position 15. Si une insertion se produit précisément à la position dénotée <xref:Microsoft.VisualStudio.Text.PointTrackingMode>par le point `Positive` `Negative`de suivi, son comportement est déterminé par son , qui peut être soit ou . Si le mode de suivi est positif, le point de suivi se réfère au même caractère, qui est maintenant à la fin de l’insertion. Si le mode de suivi est négatif, le point de suivi se réfère au premier personnage inséré à la position d’origine. Si le personnage à la position représentée par un point de suivi est supprimé, le point de suivi passe au premier personnage qui suit la plage supprimée. Par exemple, si un point de suivi se réfère au personnage à la position 5, et que les caractères des positions 3 à 6 sont supprimés, le point de suivi se réfère au personnage à la position 3.

Un <xref:Microsoft.VisualStudio.Text.ITrackingSpan> représente une gamme de caractères au lieu d’une seule position. Son comportement est <xref:Microsoft.VisualStudio.Text.SpanTrackingMode>déterminé par son . Si le mode de suivi de la travée est [SpanTrackingMode.EdgeInclusive](xref:Microsoft.VisualStudio.Text.SpanTrackingMode.EdgeInclusive), la traque se développe pour incorporer le texte inséré à ses bords. Si le mode de suivi de la travée est [SpanTrackingMode.EdgeExclusive](xref:Microsoft.VisualStudio.Text.SpanTrackingMode.EdgeExclusive), la traque n’intègre pas le texte inséré à ses bords. Cependant, si le mode de suivi de la travée est [SpanTrackingMode.EdgePositive](xref:Microsoft.VisualStudio.Text.SpanTrackingMode.EdgePositive), une insertion pousse la position actuelle vers le début, et si le mode de suivi de la traque est [SpanTrackingMode.EdgeNegative](xref:Microsoft.VisualStudio.Text.SpanTrackingMode.EdgeNegative), une insertion pousse la position actuelle vers la fin.

Vous pouvez obtenir la position d’un point de suivi ou la durée d’une traque pour tout instantané du tampon de texte auquel ils appartiennent. Les points de suivi et les travées de suivi peuvent être référencés en toute sécurité à partir de n’importe quel thread.

#### <a name="content-types"></a>Types de contenu

Les types de contenu sont un mécanisme permettant de définir différents types de contenu. Un type de contenu peut être un type de fichier tel que «texte», «code», ou «binaire», ou un type de technologie tel que «xml», «vb», ou «c». Par exemple, le mot « utilisation » est un mot clé dans les deux C et Visual Basic, mais pas dans d’autres langages de programmation. Par conséquent, la définition de ce mot clé se limiterait aux types de contenu « c » et « vb ».

Les types de contenu sont utilisés comme filtre pour les parures et autres éléments de l’éditeur. De nombreuses fonctionnalités d’éditeur et points d’extension sont définis par type de contenu. Par exemple, la coloration de texte est différente pour les fichiers texte simple, les fichiers XML et les fichiers de code source Visual Basic. Les tampons de texte sont généralement attribués un type de contenu lorsqu’ils sont créés, et le type de contenu d’un tampon de texte peut être modifié.

Les types de contenu peuvent hériter plusieurs fois d’autres types de contenu. Le <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> vous permet de spécifier plusieurs types de base en tant que parents d’un type de contenu donné.

Les développeurs peuvent définir leurs propres types <xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService>de contenu et les enregistrer en utilisant le . De nombreuses fonctionnalités de l’éditeur peuvent être <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>définies en ce qui concerne un type de contenu spécifique en utilisant le . Par exemple, les marges des éditeurs, les parures et les poignées de souris peuvent être définies de sorte qu’elles ne s’appliquent qu’aux éditeurs qui affichent des types de contenu particuliers.

### <a name="the-text-view"></a>La vue du texte

La partie vue du modèle de contrôleur de vue (MVC) définit la vue de texte, le formatage de la vue, les éléments graphiques tels que la barre de défilement, et le caret. Tous les éléments de présentation de l’éditeur Visual Studio sont basés sur WPF.

#### <a name="text-views"></a>Vues textuelles

L’interface <xref:Microsoft.VisualStudio.Text.Editor.ITextView> est une représentation indépendante d’une plate-forme d’une vue de texte. Il est principalement utilisé pour afficher des documents texte dans une fenêtre, mais il peut également être utilisé à d’autres fins, par exemple, dans un tooltip.

La vue de texte fait référence à différents types de tampons de texte. La <xref:Microsoft.VisualStudio.Text.Editor.ITextView.TextViewModel%2A> propriété se <xref:Microsoft.VisualStudio.Text.Editor.ITextViewModel> réfère à un objet qui pointe vers ces trois tampons de texte différents: le tampon de données, qui est le tampon de niveau de données supérieur, le tampon de modification, dans lequel l’édition se produit, et le tampon visuel, qui est le tampon qui est affiché dans la vue du texte.

Le texte est formaté en fonction des classificateurs qui sont attachés au tampon de texte sous-jacent, et est orné en utilisant les fournisseurs de parures qui sont attachés à la vue de texte elle-même.

#### <a name="the-text-view-coordinate-system"></a>Le système de coordination de la vue de texte

Le système de coordination de l’affichage du texte spécifie les positions dans la vue du texte. Dans ce système de coordonnées, la valeur x 0.0 correspond au bord gauche du texte affiché, et la valeur y 0.0 correspond au bord supérieur du texte affiché. La coordonnées x augmente de gauche à droite, et la coordonnées y augmente de haut en bas.

Un viewport (la partie du texte visible dans la fenêtre de texte) ne peut pas être défilé de la même manière horizontalement qu’il est défiché verticalement. Un viewport est défiché horizontalement en changeant sa coordonnées gauche de sorte qu’il se déplace par rapport à la surface de dessin. Cependant, un viewport ne peut être défilé verticalement qu’en modifiant le texte rendu, ce qui provoque un <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> événement à soulever.

Les distances dans le système de coordonnées correspondent à des pixels logiques. Si la surface de rendu du texte est affichée sans une transformation à l’échelle, alors une unité dans le système de coordination du rendu du texte correspond à un pixel sur l’écran.

#### <a name="margins"></a>Marges

L’interface <xref:Microsoft.VisualStudio.Text.Editor.ITextViewMargin> représente une marge et permet de contrôler la visibilité de la marge et de sa taille. Il y a quatre marges prédéfinies, qui sont nommées "Top", "Gauche", "Droite" et "Bottom" et sont attachées au bord supérieur, inférieur, gauche ou droit d’une vue. Ces marges sont des conteneurs dans lesquels d’autres marges peuvent être placées. L’interface définit les méthodes qui renvoient la taille de la marge et la visibilité d’une marge. Les marges sont des éléments visuels qui fournissent des informations supplémentaires sur la vue de texte à laquelle elles sont attachées. Par exemple, la marge de numéro de ligne affiche les numéros de ligne pour la vue textuelle. La marge de glyphe affiche des éléments d’interface utilisateur.

L’interface <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMarginProvider> gère la création et le placement des marges. Les marges peuvent être commandées par rapport à d’autres marges. Les marges prioritaires sont situées plus près de la vue du texte. Par exemple, s’il y a deux marges gauches, la marge A et la marge B, et la marge B a une priorité inférieure à la marge A, la marge B apparaît à gauche de la marge A.

#### <a name="the-text-view-host"></a>L’hôte de vue de texte

L’interface <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> contient la vue de texte et toutes les décorations attenantes qui accompagnent la vue, par exemple, défilent les barres. L’hôte de vue de texte contient également des marges qui sont attachées à une bordure de la vue.

#### <a name="formatted-text"></a>Texte mis en forme

Le texte affiché dans une vue <xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine> textuelle est composé d’objets. Chaque ligne de vue de texte correspond à une seule ligne de texte dans la vue de texte. Les longues lignes du tampon de texte sous-jacent peuvent être partiellement obscurcies (si l’emballage des mots n’est pas activé) ou en plusieurs lignes de vue textuelle. L’interface <xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine> contient des méthodes et des propriétés pour la cartographie entre les coordonnées et les caractères, et pour les ornements qui peuvent être associés à la ligne.

<xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine>objets sont créés <xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource> à l’aide d’une interface. Si vous êtes simplement préoccupé par le texte qui est actuellement affiché dans la vue, vous pouvez ignorer la source de formatage. Si vous êtes intéressé par le format de texte qui n’est pas affiché dans la vue <xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource> (par exemple, pour prendre en charge une coupe et une pâte à texte riche), vous pouvez utiliser pour formater le texte dans un tampon de texte.

La vue textuelle <xref:Microsoft.VisualStudio.Text.ITextSnapshotLine> est une à la fois.

## <a name="editor-features"></a>Fonctionnalités de l’éditeur

Les caractéristiques de l’éditeur sont conçues de sorte que la définition de la fonctionnalité est distincte de sa mise en œuvre. L’éditeur comprend ces fonctionnalités:

- Tags et classificateurs

- Ornements

- Projection

- mode Plan

- Souris et fixations clés

- Opérations et primitifs

- IntelliSense

### <a name="tags-and-classifiers"></a>Tags et classificateurs

Les balises sont des marqueurs associés à une durée de texte. Ils peuvent être présentés de différentes manières, par exemple, en utilisant la coloration de texte, souligne, graphiques, ou pop-ups. Les classificateurs sont une sorte d’étiquette.

D’autres types <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> d’étiquettes sont pour la mise en évidence du texte, <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag> pour la description, et <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag> pour compiler des erreurs.

#### <a name="classification-types"></a>Types de classification

Une <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType> interface représente une classe d’équivalence, qui est une catégorie abstraite de texte. Les types de classification peuvent hériter plusieurs fois d’autres types de classification. Par exemple, les classifications linguistiques de programmation peuvent inclure « mot-clé », « commentaire » et « identifiant », qui héritent tous du « code ». Les types de classification des langues naturelles peuvent inclure le « nom », le « verbe » et l'« adjectif », qui héritent tous du « langage naturel ».

#### <a name="classifications"></a>Classifications

Une classification est un exemple d’un type de classification particulier, généralement sur une durée de texte. A <xref:Microsoft.VisualStudio.Text.Classification.ClassificationSpan> est utilisé pour représenter une classification. Une durée de classification peut être considérée comme une étiquette qui couvre une durée particulière de texte et indique au système que cette durée de texte est d’un type de classification particulier.

#### <a name="classifiers"></a>Classificateurs

Un <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> mécanisme qui divise le texte en un ensemble de classifications. Les classificateurs doivent être définis pour des types de contenu spécifiques et instantanés pour des tampons texte spécifiques. Les clients <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> doivent mettre en œuvre pour participer à la classification des textes.

#### <a name="classifier-aggregators"></a>Agrégateurs de classificateurs

Un agrégateur de classificateur est un mécanisme qui combine tous les classificateurs pour un tampon de texte en un seul ensemble de classifications. Par exemple, un classificateur de cmD et un classificateur de langue anglaise peuvent créer des classifications sur un commentaire dans un fichier C. Considérez ce commentaire:

```
// This method produces a classifier
```

Un classificateur Cmd peut étiqueter l’ensemble de la travée comme un commentaire, et le classificateur de langue anglaise peut classer « produit » comme un « verbe » et une « méthode » comme un « nom ». L’agrégateur produit un ensemble de classifications non-overlapping, et le type de l’ensemble est basé sur toutes les contributions.

Un agrégateur de classificateur est également un classificateur parce qu’il casse le texte en un ensemble de classifications. L’agrégateur de classificateur s’assure également qu’il n’y a pas de classifications qui se chevauchent et que les classifications sont triées. Les classificateurs individuels sont libres de retourner n’importe quel ensemble de classifications, dans n’importe quel ordre, et se chevauchent de quelque façon que ce soit.

#### <a name="classification-formatting-and-text-coloring"></a>Formatage de classification et coloration de texte

Le formatage de texte est un exemple d’une fonctionnalité qui est construite sur la classification de texte. Il est utilisé par la couche de vue de texte pour déterminer l’affichage du texte dans une application. La zone de formatage de texte dépend de WPF, mais la définition logique des classifications ne fonctionne pas.

Un format de classification est un ensemble de propriétés de formatage pour un type de classification spécifique. Ces formats héritent du format du parent du type de classification.

Une <xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMap> carte est d’un type de classification à un ensemble de propriétés de formatage de texte. La mise en œuvre de la carte de format dans l’éditeur gère toutes les exportations de formats de classification.

### <a name="adornments"></a>Ornements

Les ornements sont des effets graphiques qui ne sont pas directement liés à la police et la couleur des caractères dans la vue de texte. Par exemple, le squiggle rouge soulignent qui est utilisé pour marquer le code non compilateur dans de nombreux langages de programmation est une parure intégrée, et les outils sont des ornements pop-up. Les ornements sont <xref:System.Windows.UIElement> dérivés <xref:Microsoft.VisualStudio.Text.Tagging.ITag>et implémentent. Deux types spécialisés d’étiquette <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>d’ornement sont les , pour les ornements qui occupent <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>le même espace que le texte dans une vue, et le , pour le soulignement de squiggle.

Les ornements intégrés sont des graphiques qui font partie de la vue de texte formatée. Ils sont organisés en différentes couches Z-ordre. Il y a trois couches intégrées, comme suit : le texte, le caret et la sélection. Cependant, les développeurs peuvent définir plus de couches et les mettre en ordre les uns par rapport aux autres. Les trois types d’ornements intégrés sont des parures textuelles relatives (qui se déplacent lorsque le texte se déplace, et sont supprimés lorsque le texte est supprimé), les ornements de vue relatif (qui ont à voir avec les parties non-texte de la vue), et les ornements contrôlés par le propriétaire (le développeur doit gérer leur placement).

Les ornements pop-up sont des graphiques qui apparaissent dans une petite fenêtre au-dessus de la vue de texte, par exemple, des outils.

### <a name="projection"></a><a name="projection"></a>Projection

La projection est une technique pour construire un autre type de tampon de texte qui ne stocke pas réellement le texte, mais combine plutôt le texte d’autres tampons de texte. Par exemple, un tampon de projection peut être utilisé pour concatener le texte à partir de deux autres tampons et présenter le résultat comme s’il se trouve dans un seul tampon, ou pour cacher des parties du texte dans un tampon. Un tampon de projection peut servir de tampon source à un autre tampon de projection. Un ensemble de tampons qui sont liés par projection peut être construit pour réorganiser le texte de différentes façons. (Un tel ensemble est également connu sous le nom de *graphique tampon*.) La fonction de description de texte visual Studio est implémentée à l’aide d’un tampon de projection pour masquer le texte effondré, et l’éditeur visual Studio pour ASP.NET pages utilise la projection pour prendre en charge les langues embarquées telles que Visual Basic et C.

Un <xref:Microsoft.VisualStudio.Text.Projection.IProjectionBuffer> est créé <xref:Microsoft.VisualStudio.Text.Projection.IProjectionBufferFactoryService>en utilisant . Un tampon de projection est représenté <xref:Microsoft.VisualStudio.Text.ITrackingSpan> par une séquence ordonnée d’objets qui sont connus sous le nom *de sources.* Le contenu de ces travées est présenté comme une séquence de personnages. Les tampons de texte à partir desquels les travées de source sont tirées sont *nommés tampons source*. Les clients d’un tampon de projection n’ont pas à savoir qu’il diffère d’un tampon texte ordinaire.

Le tampon de projection écoute les événements de changement de texte sur les tampons source. Lorsque le texte d’une portée source change, le tampon de projection cartographie les coordonnées du texte modifié à ses propres coordonnées et soulève les événements appropriés de changement de texte. Par exemple, considérez les tampons de source A et B qui ont ces contenus :

```
A: ABCDE
B: vwxyz
```

Si le tampon de projection P est formé à partir de deux travées de texte, l’une qui a toute la zone tampon A et l’autre qui a tout de tampon B, alors P a le contenu suivant:

```
P: ABCDEvwxyz
```

Si le sous-cordon `xy` est supprimé du tampon B, alors tampon P soulève un événement qui indique que les caractères aux positions 7 et 8 ont été supprimés.

Le tampon de projection peut également être modifié directement. Il propage les modifications aux tampons source appropriés. Par exemple, si une chaîne est insérée dans le tampon P à la position 6 (la position originale du personnage "v"), l’insertion est propagée pour tampon B à la position 1.

Il y a des restrictions sur les travées sources qui contribuent à un tampon de projection. Les travées de source peuvent ne pas se chevaucher; un emplacement dans un tampon de projection ne peut pas cartographier à plus d’un endroit dans n’importe quel tampon source, et un emplacement dans un tampon source ne peut pas cartographier à plus d’un endroit dans un tampon de projection. Aucune circulaire n’est autorisée dans la relation tampon source.

Les événements sont soulevés lorsque l’ensemble de tampons de source pour un tampon de projection change et lorsque l’ensemble de la source s’étend change.
Un tampon d’élision est un type spécial de tampon de projection. Il est principalement utilisé pour la mise en ligne et pour les opérations qui élargissent et s’effondrent blocs de texte. Un tampon d’élision est basé sur un seul tampon source, et les travées dans le tampon d’élision doivent être commandées de la même façon qu’elles sont commandées dans le tampon source.

#### <a name="the-buffer-graph"></a>Le graphique tampon

L’interface <xref:Microsoft.VisualStudio.Text.Projection.IBufferGraph> permet de cartographier un graphique de tampons de projection. Tous les tampons de texte et les tampons de projection sont collectés dans un graphique acyclique dirigé, un peu comme l’arbre syntaxe abstrait qui est produit par un compilateur de langue. Le graphique est défini par le tampon supérieur, qui peut être n’importe quel tampon de texte. Le graphique tampon peut cartographier à partir d’un point dans le tampon supérieur à un point dans un tampon source, ou d’une portée dans le tampon supérieur à un ensemble de travées dans un tampon source. De même, il peut cartographier un point ou une portée à partir d’un tampon source à un point dans le tampon supérieur. Graphiques tampons sont <xref:Microsoft.VisualStudio.Text.Projection.IBufferGraphFactoryService>créés en utilisant le .

#### <a name="events-and-projection-buffers"></a>Événements et tampons de projection

Lorsqu’un tampon de projection est modifié, les modifications sont envoyées du tampon de projection aux tampons qui en dépendent. Une fois que tous les tampons sont modifiés, les événements de changement de tampon sont soulevés, en commençant par le tampon le plus profond.

### <a name="outlining"></a>mode Plan

L’affichage est la capacité d’élargir ou d’effondrer différents blocs de texte dans une vue de texte. L’énoncé est défini comme <xref:Microsoft.VisualStudio.Text.Tagging.ITag>une sorte de , de la même manière que les ornements sont définis. A <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag> est une étiquette qui définit une région de texte qui peut être élargie ou effondrée. Pour utiliser la description, vous <xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManagerService> devez <xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManager>importer le pour obtenir un . Le gestionnaire décrivant énumère, s’effondre, et élargit les différents blocs, <xref:Microsoft.VisualStudio.Text.Outlining.ICollapsible> qui sont représentés comme des objets, et soulève des événements en conséquence.

### <a name="mouse-bindings"></a>Fixations de souris

Les fixations de souris relient les mouvements de souris à différentes commandes. Les fixations de souris <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessorProvider>sont définies par l’utilisation d’un , et les liaisons clés sont définies en utilisant un <xref:Microsoft.VisualStudio.Text.Editor.IKeyProcessorProvider>. L’instantanéise <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> automatiquement toutes les liaisons et les relie aux événements de souris dans la vue.

L’interface <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessor> contient des gestionnaires d’événements avant le processus et après le processus pour différents événements de souris. Pour gérer l’un des événements, vous pouvez <xref:Microsoft.VisualStudio.Text.Editor.MouseProcessorBase>passer outre à certaines des méthodes dans .

### <a name="editor-operations"></a>Opérations de rédacteur en chef

Les opérations de l’éditeur peuvent être utilisées pour automatiser l’interaction avec l’éditeur, pour le script ou d’autres fins. Vous pouvez <xref:Microsoft.VisualStudio.Text.Operations.IEditorOperationsFactoryService> importer les opérations <xref:Microsoft.VisualStudio.Text.Editor.ITextView>d’accès à un compte . Vous pouvez ensuite utiliser ces objets pour modifier la sélection, faire défiler la vue ou déplacer le caret vers différentes parties de la vue.

### <a name="intellisense"></a>IntelliSense

IntelliSense prend en charge l’achèvement des relevés, l’aide à la signature (également connue sous le nom d’info paramètres), Quick Info et les ampoules.

L’achèvement de l’énoncé fournit des listes contextuées d’achèvements potentiels pour les noms de méthode, les éléments XML et d’autres éléments de codage ou de balisage. En général, un geste de l’utilisateur invoque une session d’achèvement. La session affiche la liste des achèvements potentiels, et l’utilisateur peut en sélectionner un ou rejeter la liste. Le <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker> est responsable de la <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSession>création et le déclenchement de la . Le <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource> calcul des <xref:Microsoft.VisualStudio.Language.Intellisense.CompletionSet> éléments d’achèvement pour la session.

## <a name="see-also"></a>Voir aussi

- [Service linguistique et points d’extension de l’éditeur](../extensibility/language-service-and-editor-extension-points.md)
- [Importations de rédacteurs](../extensibility/editor-imports.md)
