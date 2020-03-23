---
title: Images et icônes pour Visual Studio (fr) Microsoft Docs
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: f410325e-9cf2-4f39-b6d7-b672121c2691
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1e449fb30bd95319a46d1db50da63778f6800a70
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79303196"
---
# <a name="images-and-icons-for-visual-studio"></a>Images et icônes pour Visual Studio
## <a name="image-use-in-visual-studio"></a><a name="BKMK_ImageUseInVisualStudio"></a>Utilisation de l’image dans Visual Studio
 Avant de créer des œuvres d’art, envisagez d’utiliser les plus de 1 000 images de la [Visual Studio Image Library](https://www.microsoft.com/download/details.aspx?id=35825).

### <a name="types-of-images"></a>Types d’images

- **Icônes**. De petites images qui apparaissent dans les commandes, les hiérarchies, les modèles, et ainsi de suite. La taille par défaut de l’icône utilisée dans Visual Studio est un 16x16 PNG. Les icônes produites par le service d’image génèrent automatiquement le format XAML pour le support HDPI.

    > [!NOTE]
    > Bien que les images soient utilisées dans le système de menu, vous ne devez pas créer une icône pour chaque commande. Consultez [menus et commandes pour Visual Studio pour](../../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md) voir si votre commande doit obtenir une icône.

- **Vignettes.** Images utilisées dans la zone d’aperçu d’un dialogue, comme le dialogue du nouveau projet.

- **Dialog images.** Images qui apparaissent dans les dialogues ou les sorciers, que ce soit sous forme de graphiques descriptifs ou d’indicateurs de messages. Utilisez rarement et seulement si nécessaire pour illustrer un concept difficile ou attirer l’attention de l’utilisateur (alerte, avertissement).

- **Images animées.** Utilisé dans les indicateurs de progrès, les barres d’état et les dialogues d’opération.

- **Curseurs.** Utilisé pour indiquer si une opération est autorisée à utiliser la souris, où un objet peut être abandonné, et ainsi de suite.

## <a name="icon-design"></a><a name="BKMK_IconDesign"></a>Conception d’icône

### <a name="overview"></a>Vue d’ensemble
 Visual Studio utilise des icônes de style moderne, qui ont une géométrie propre et un équilibre 50/50 de positif / négatif (lumière / obscurité), et utiliser des métaphores directes et compréhensibles. Les points cruciaux de conception d’icônes se concentrent autour de la clarté, de la simplification et du contexte.

- **Clarté :** concentrez-vous sur la métaphore centrale qui donne à une icône son sens et son individualité.

- **Simplification:** réduire l’icône à son sens de base - faire passer le thème avec juste l’élément nécessaire (s) et pas de fioritures.

- **Contexte :** considérez tous les aspects du rôle d’une icône lors du développement de concepts, ce qui est crucial pour décider quels éléments constituent la métaphore centrale de l’icône.

  Avec les icônes, il ya un certain nombre de points de conception à éviter:

- N’utilisez pas d’icônes qui signifient des éléments d’interface utilisateur sauf le cas échéant. Choisissez une approche plus abstraite ou symbolique lorsque l’élément d’assurance-chômage n’est ni commun, ni évident, ni unique.

- N’oubliez pas les éléments communs comme les documents, les dossiers, les flèches et la loupe. Utilisez ces éléments uniquement lorsqu’ils sont essentiels au sens de l’icône. Par exemple, la loupe orientée vers le droit ne doit indiquer que la recherche, la navigation et la recherche.

- Bien que certains éléments d’icônes hérités maintiennent l’utilisation de la perspective, ne créez pas de nouvelles icônes avec perspective à moins que l’élément manque de clarté sans elle.

- Ne pas entasser trop d’informations dans une icône. Une image simple qui peut être facilement reconnue ou apprise comme un symbole reconnaissable est beaucoup plus utile qu’une image trop complexe. Une icône ne peut pas raconter toute l’histoire.

### <a name="icon-creation"></a>Création d’icônes

#### <a name="concept-development"></a>Développement de concepts
 Visual Studio a au sein de son interface utilisateur une grande variété de types d’icônes. Considérez attentivement le type d’icône pendant le développement. N’utilisez pas d’objets d’interface utilisateur peu clairs ou rares pour vos éléments d’icône. Optez pour le symbolique dans ces cas, comme avec l’icône Smart Tag. Notez que le sens de l’étiquette abstraite à gauche est plus évident que la vague version basée sur l’interface utilisateur à droite :

|||
|-|-|
|**Utilisation correcte de l’imagerie symbolique**|**Utilisation incorrecte de l’imagerie symbolique**|
|![Icône d’étiquette active correcte](../../extensibility/ux-guidelines/media/0404-01_smarttagcorrect.png "0404-01_SmartTagCorrect")|![Icône de balise active incorrecte](../../extensibility/ux-guidelines/media/0404-02_smarttagincorrect.png "0404-02_SmartTagIncorrect")|

 Il y a des cas où les éléments d’interface utilisateur standard et facilement reconnaissables fonctionnent bien pour les icônes. Add Window en est un exemple :

|||
|-|-|
|**Élément correct de l’interface utilisateur dans une icône**|**Élément incorrect de l’interface utilisateur dans une icône**|
|![Icône d'ajout de fenêtre correcte](../../extensibility/ux-guidelines/media/0404-03_addwindowcorrect.png "0404-03_AddWindowCorrect")|![Icône d'ajout de fenêtre incorrecte](../../extensibility/ux-guidelines/media/0404-04_addwindowincorrect.png "0404-04_AddWindowIncorrect")|

 N’utilisez pas un document comme élément de base à moins qu’il ne soit essentiel au sens de l’icône. Sans l’élément document sur Add Document (ci-dessous), le sens est perdu, alors qu’avec Rafraîchir l’élément document n’est pas nécessaire pour communiquer le sens.

|||
|-|-|
|**Utilisation correcte de l’icône de document**|**Utilisation incorrecte de l’icône de document**|
|![Icône de document correcte](../../extensibility/ux-guidelines/media/0404-05_documenticoncorrect.png "0404-05_DocumentIconCorrect")|![Icône de document incorrecte](../../extensibility/ux-guidelines/media/0404-06_documenticonincorrect.png "0404-06_DocumentIconIncorrect")|

 Le concept de "show" doit être représenté par l’icône qui illustre le mieux ce qui est montré, comme avec l’exemple Show All Files. Une métaphore de l’objectif peut être utilisée pour indiquer le concept de « vue » si nécessaire, comme avec l’exemple Resource View.

|||
|-|-|
|**"Show"**|**"Voir"**|
|![Afficher l'icône](../../extensibility/ux-guidelines/media/0404-07_show.png "0404-07_Show")|![Icône d'affichage](../../extensibility/ux-guidelines/media/0404-08_view.png "0404-08_View")|

 L’icône de loupe orientée vers le droit ne devrait représenter que Search, Find et Browse. La variante orientée vers la gauche avec le signe plus ou moins signe devrait représenter seulement zoom avant / zoom.

|||
|-|-|
|**"Recherche"**|**"Zoom"**|
|![Icône de recherche](../../extensibility/ux-guidelines/media/0404-09_search.png "0404-09_Search")|![Icône de zoom](../../extensibility/ux-guidelines/media/0404-10_zoom.png "0404-10_Zoom")|

 Dans les vues des arbres, n’utilisez pas à la fois l’icône du dossier et un modificateur. Lorsqu’il est disponible, n’utilisez que le modificateur.

|||
|-|-|
|**Graphismes corrects de vue d’arbre**|**Icônes incorrectes de vue d’arbre**|
|![L’icône correcte de vue d’arbre &#40;1&#41;](../../extensibility/ux-guidelines/media/0404-11_treeviewcorrect1.png "0404-11_TreeViewCorrect1") ![Icône correcte de vue d’arbre &#40;2&#41;](../../extensibility/ux-guidelines/media/0404-12_treeviewcorrect2.png "0404-12_TreeViewCorrect2")|![Icône incorrecte de vue d’arbre &#40;1&#41;](../../extensibility/ux-guidelines/media/0404-13_treeviewincorrect1.png "0404-13_TreeViewIncorrect1") ![icône incorrecte de vue d’arbre &#40;2&#41;](../../extensibility/ux-guidelines/media/0404-14_treeviewincorrect2.png "0404-14_TreeViewIncorrect2")|

### <a name="style-details"></a>Détails de style

#### <a name="layout"></a>Disposition
 Stack éléments comme indiqué pour les icônes 16x16 standard:

 ![Pile de disposition pour les icônes 16x16](../../extensibility/ux-guidelines/media/0404-15_layoutstack.png "0404-15_LayoutStack")<br />Pile de disposition pour les icônes 16x16

 Les éléments de notification d’état sont mieux utilisés comme icônes autonomes. Il existe cependant des contextes dans lesquels une notification doit être empilée sur l’élément de base, comme avec l’icône Task Complete :

 ![Notifications autonome dans Visual Studio](../../extensibility/ux-guidelines/media/0404-16_standalonenotificationicons.png "0404-16_StandaloneNotificationIcons")<br />Icônes de notification autonomes

 ![Icône de tâche terminée](../../extensibility/ux-guidelines/media/0404-17_taskcomplete.png "0404-17_TaskComplete")<br />Icône complète de tâche

 Les icônes de projet sont généralement des fichiers .ico qui contiennent plusieurs tailles. La plupart des icônes 16x16 contiennent les mêmes éléments. Les versions 32x32 ont plus de détails, y compris le type de projet le cas échéant.

 ![Icônes de projet dans Visual Studio](../../extensibility/ux-guidelines/media/0404-18_iconprojectthreesizes.png "0404-18_IconProjectThreeSizes")<br />VB Windows Control Library Project Icônes, 16x16 et 32x32

 Centrez une icône dans son cadre de pixel. Si cela n’est pas possible, alignez l’icône vers le haut et/ou la droite du cadre.

 ![Icône centrée dans le frame de pixels](../../extensibility/ux-guidelines/media/0404-19_iconcentered.png "0404-19_IconCentered")<br />Icône centrée dans le frame de pixels

 ![Icône alignée sur le bord supérieur droit du frame de pixels](../../extensibility/ux-guidelines/media/0404-20_icontopright.png "0404-20_IconTopRight")<br />Icône alignée en haut à droite du cadre

 ![Icône centrée et alignée sur le bord supérieur du frame de pixels](../../extensibility/ux-guidelines/media/0404-21_icontopalign.png "0404-21_IconTopAlign")<br />Icône centrée et alignée vers le haut du cadre

 Pour atteindre l’alignement et l’équilibre idéaux, évitez d’obstruer l’élément de base de l’icône avec des glyphes d’action. Placez le glyphe près du haut à gauche de l’élément de base. Lors de l’ajout d’un élément supplémentaire, considérez l’alignement et l’équilibre de l’icône.

|||
|-|-|
|**Alignement et équilibre corrects**|**Alignement et équilibre incorrects**|
|![Alignement et équilibre des icônes corrects](../../extensibility/ux-guidelines/media/0404-22_alignbalancecorrect.png "0404-22_AlignBalanceCorrect")|![Alignement et équilibre des icônes incorrects](../../extensibility/ux-guidelines/media/0404-23_alignbalanceincorrect.png "0404-23_AlignBalanceIncorrect")|

 Assurer la parité de taille pour les icônes qui partagent des éléments et sont utilisées dans les ensembles. Notez que dans le jumelage incorrect, le cercle et la flèche sont surdimensionnés et ne correspondent pas.

|||
|-|-|
|**Parité de taille correcte**|**Parité de taille incorrecte**|
|![Taille et parité des icônes correctes](../../extensibility/ux-guidelines/media/0404-24_sizeparitycorrect.png "0404-24_SizeParityCorrect")|![Taille et parité des icônes incorrectes](../../extensibility/ux-guidelines/media/0404-25_sizeparityincorrect.png "0404-25_SizeParityIncorrect")|

 Utilisez des poids cohérents en ligne et visuelle. Évaluez la façon dont l’icône que vous construisez se compare à d’autres icônes en utilisant une comparaison côte à côte. N’utilisez jamais l’ensemble du cadre 16x16, utilisez 15x15 ou plus petit. Le rapport négatif/positif (obscurité/lumière) devrait être de 50/50.

|||
|-|-|
|**Ratio négatif/positif correct**|**Ratio négatif/positif incorrect**|
|![Poids visuel correct pour les icônes &#40;1&#41;](../../extensibility/ux-guidelines/media/0404-26_visualweightcorrect1.png "0404-26_VisualWeightCorrect1")<br /><br /> ![Poids visuel correct pour les icônes &#40;2&#41;](../../extensibility/ux-guidelines/media/0404-27_visualweightcorrect2.png "0404-27_VisualWeightCorrect2")<br /><br /> ![Poids visuel correct pour les icônes &#40;3&#41;](../../extensibility/ux-guidelines/media/0404-28_visualweightcorrect3.png "0404-28_VisualWeightCorrect3")|![Épaisseur visuelle incorrecte pour les icônes](../../extensibility/ux-guidelines/media/0404-29_visualweightincorrect.png "0404-29_VisualWeightIncorrect")|

 Utilisez des formes simples et comparables et des angles complémentaires pour construire vos éléments sans sacrifier l’intégrité de l’élément. Utilisez des angles de 45 ou 90 degrés dans la mesure du possible.

 ![Angles des icônes corrects](../../extensibility/ux-guidelines/media/0404-30_iconanglescorrect.png "0404-30_IconAnglesCorrect")

#### <a name="perspective"></a>Perspective
 Gardez l’icône claire et compréhensible. Utilisez la perspective et une source lumineuse seulement si nécessaire. Bien que l’utilisation de la perspective sur les éléments de l’icône doit être évitée, certains éléments sont méconnaissables sans elle. Dans de tels cas, une perspective stylisée communique la clarté de l’élément.

 ![Perspective à 3 points](../../extensibility/ux-guidelines/media/0404-31_3pointperspective.png "0404-31_3PointPerspective")<br />Perspective à 3 points

 ![Perspective à 1 point](../../extensibility/ux-guidelines/media/0404-32_1pointperspective.png "0404-32_1PointPerspective")<br />Perspective à 1 point

 La plupart des éléments doivent être orientés ou inclinés vers la droite :

 ![Icônes avec angle droit](../../extensibility/ux-guidelines/media/0404-33_angledright.png "0404-33_AngledRight")

 Utilisez des sources lumineuses uniquement lors de l’ajout de clarté nécessaire à un objet.

|||
|-|-|
|**Source de lumière correcte**|**Source de lumière incorrecte**|
|![Sources de lumière correctes pour les icônes](../../extensibility/ux-guidelines/media/0404-34_lightsourcescorrect.png "0404-34_LightSourcesCorrect")|![Sources de lumière incorrectes pour les icônes](../../extensibility/ux-guidelines/media/0404-35_lightsourcesincorrect.png "0404-35_LightSourcesIncorrect")|

 Utilisez des contours uniquement pour améliorer la lisibilité ou pour mieux communiquer la métaphore. Le solde négatif positif (lumière foncée) devrait être de 50/50.

|||
|-|-|
|**Utilisation correcte des contours**|**Utilisation incorrecte des contours**|
|![Plans corrects](../../extensibility/ux-guidelines/media/0404-36_outlinescorrect.png "0404-36_OutlinesCorrect")|![Plans incorrects](../../extensibility/ux-guidelines/media/0404-37_outlinesincorrect.png "0404-37_OutlinesIncorrect")|

#### <a name="icon-types"></a>Types d’icônes
 **Les** icônes shell et de barre de commande ne sont pas plus de trois des éléments suivants : une base, un modificateur, une action ou un statut.

 ![Exemples d’icônes de barre de coquille et de commande](../../extensibility/ux-guidelines/media/0404-38_shellicons.png "0404-38_ShellIcons")<br />Exemples d’icônes de barre de coquille et de commande

 **Les** icônes de barre de commande de fenêtre d’outil ne sont pas plus de trois des éléments suivants : une base, un modificateur, une action, ou un statut.

 ![Exemples d’icônes de barre de commande de fenêtre d’outil](../../extensibility/ux-guidelines/media/0404-39_toolwindowcommandbaricons.png "0404-39_ToolWindowCommandBarIcons")<br />Exemples d’icônes de barre de commande de fenêtre d’outil

 Les icônes **de désambiguateur** de vue d’arbre ne sont pas plus de trois des éléments suivants : une base, un modificateur, une action, ou un statut.

 ![Exemples d’icônes de désambiguateur de vue d’arbre](../../extensibility/ux-guidelines/media/0404-40_treeviewicons.png "0404-40_TreeViewIcons")<br />Exemples d’icônes de désambiguateur de vue d’arbre

 Les icônes **de la taxonomie de la valeur basée sur l’État** existent dans les états suivants : handicapés actifs, actifs et inactivs.

 ![Exemples d’icônes de la taxonomie de la valeur basée sur l’État](../../extensibility/ux-guidelines/media/0404-41_statebasedtaxonomy.png "0404-41_StateBasedTaxonomy")<br />Exemples d’icônes de la taxonomie de la valeur basée sur l’État

 Les icônes **IntelliSense** ne sont pas plus de trois des éléments suivants : une base, un modificateur et un statut.

 ![Exemples d’icônes IntelliSense](../../extensibility/ux-guidelines/media/0404-42_intellisenseicons.png "0404-42_IntelliSenseIcons")<br />Exemples d’icônes IntelliSense

 Les petites icônes **de projet (16x16)** ne doivent pas avoir plus de deux éléments : une base et un modificateur.

 ![Exemples de petites icônes de projet (16x16) icônes](../../extensibility/ux-guidelines/media/0404-43_16x16project1.png "0404-43_16x16Project1") ![du projet 16x16 &#40;2&#41;'icône](../../extensibility/ux-guidelines/media/0404-44_16x16project2.png "0404-44_16x16Project2") du projet ![16x16 &#40;3&#41;](../../extensibility/ux-guidelines/media/0404-45_16x16project3.png "0404-45_16x16Project3")<br />Exemples de petites icônes de projet (16x16)

 Les grandes icônes **du projet (32x32)** ne sont pas plus de quatre des éléments suivants : une base, un à deux modificateurs et une superposition linguistique.

 ![Exemples de grandes icônes de projet (32x32)](../../extensibility/ux-guidelines/media/0404-46_32x32project.png "0404-46_32x32Project")<br />Exemples de grandes icônes de projet (32x32)

### <a name="production-details"></a>Détails de production
 Tous les nouveaux éléments d’interface utilisateur devraient être créés à l’aide de Windows Presentation Foundation (WPF) et toutes les nouvelles icônes pour WPF devraient être en format PNG 32 bits. La PNG 24 bits est un format hérité qui ne prend pas en charge la transparence et n’est donc pas recommandé pour les icônes.

 Enregistrer la résolution à 96 DPI.

#### <a name="file-types"></a>Types de fichier

- **PNG 32 bits :** le format préféré pour les icônes. Un format de fichier de compression de données sans perte qui peut stocker une seule image raster (pixel). Les fichiers PNG 32 bits prennent en charge la transparence alpha-canal, la correction gamma et l’entrelacement.

- **BMP 32 bits :** pour les contrôles non-WPF. Aussi appelé XP ou haute couleur, BMP 32 bits est un format d’image RGB / A, une image en couleur réelle avec une transparence alpha-canal. Le canal alpha est une couche de transparence désignée dans Adobe Photoshop qui est ensuite enregistrée dans la bitmap comme un canal de couleur supplémentaire (quatrième). Un fond noir est ajouté pendant la production d’œuvres d’art à tous les fichiers BMP 32 bits pour fournir un indice visuel rapide sur la profondeur de couleur. Ce fond noir représente la zone à masquer dans l’interface utilisateur.

- **ICO 32 bits :** pour les icônes du projet et l’élément d’ajout. Tous les fichiers ICO sont 32 bits de couleur réelle avec la transparence alpha-canal (RGB/A). Parce que les fichiers ICO peuvent stocker plusieurs tailles et profondeurs de couleur, les icônes Vista sont souvent dans un format ICO contenant 16x16, 32x32, 48x48, et 256x256 tailles d’images. Afin d’afficher correctement dans Windows Explorer, les fichiers ICO doivent être enregistrés vers le bas à 24 bits et 8 bits profondeurs de couleur pour chaque taille d’image.

- **XAML:** pour les surfaces de conception et les adorateurs Windows. Les icônes XAML sont des fichiers d’images vectoriels qui prennent en charge la mise à l’échelle, la rotation, le classement et la transparence. Ils ne sont pas communs dans Visual Studio aujourd’hui, mais sont de plus en plus populaires en raison de leur flexibilité.

- **SVG**

- **BMP 24 bits :** pour le bar de commande Visual Studio. Un format d’image RGB de couleur réelle, BMP 24 bits est une convention d’icône qui crée une couche de transparence en utilisant magenta (R-255, G-0, B-255) comme une clé de couleur pour une couche de transparence knock-out. Dans un BMP 24 bits, toutes les surfaces magenta sont affichées en utilisant la couleur de fond.

- **GIF 24 bits :** pour le bar de commande Visual Studio. Un format d’image RGB de couleur réelle qui prend en charge la transparence. Les fichiers GIF sont souvent utilisés dans les illustrations De Wizard et les animations GIF.

### <a name="icon-construction"></a>Construction d’icônes
 La plus petite taille d’icône dans Visual Studio est 16x16. Le plus grand dans l’utilisation commune est 32x32. Gardez à l’esprit de ne pas remplir l’ensemble du cadre 16x16, 24x24 ou 32x32 lors de la conception d’une icône. La construction d’icônes uniformes et lisibles est essentielle à la reconnaissance de l’utilisateur. Adhérez aux points suivants lors de la construction d’icônes.

- Les icônes doivent être claires, compréhensibles et cohérentes.

- Il est préférable d’utiliser les éléments de notification d’état comme des icônes simples et de ne pas les empiler sur un élément de base d’icône. Dans certains contextes, l’interface utilisateur peut exiger que l’élément de statut soit associé à un élément de base.

- Les icônes de projet sont généralement des fichiers .ico qui contiennent plusieurs tailles. Seules les icônes 16x16, 24x24 et 32x32 sont mises à jour. La plupart des icônes 16x16 et 24x24 contiendront les mêmes éléments. Les icônes 32x32 contiennent plus de détails, y compris le type de langage du projet le cas échéant.

- Pour les icônes 32x32, les éléments de base ont généralement un poids de ligne de 2 pixels. Un poids de ligne de 1 ou 2 pixels peut être utilisé pour les éléments de détail. Utilisez votre meilleur jugement pour déterminer lequel est le plus approprié.

- Avoir au moins un espacement de 1 pixel entre les éléments pour les icônes 16x16 et 24x24. Pour les icônes 32x32, utilisez un espacement de 2 pixels entre les éléments et entre le modificateur et l’élément de base.

  ![Espacement d’éléments pour les icônes de taille 16x16, 24x24 et 32x32](../../extensibility/ux-guidelines/media/0404-47_elementspacing.png "0404-47_ElementSpacing")<br />Espacement d’éléments pour les icônes de taille 16x16, 24x24 et 32x32

#### <a name="color-and-accessibility"></a>Couleur et accessibilité
 Les directives de conformité Visual Studio exigent que toutes les icônes du produit passent les exigences d’accessibilité pour la couleur et le contraste. Ceci est réalisé par l’inversion d’icône, et quand vous concevez, vous devez être conscient qu’ils seront inversés programmatiquement dans le produit.

 Pour plus d’informations sur l’utilisation de la couleur dans les icônes Visual Studio, voir [Utiliser la couleur dans les images](../../extensibility/ux-guidelines/images-and-icons-for-visual-studio.md#BKMK_UsingColorInImages).

## <a name="using-color-in-images"></a><a name="BKMK_UsingColorInImages"></a>Utilisation de la couleur dans les images

### <a name="overview"></a>Vue d’ensemble
 Les icônes de Visual Studio sont principalement monochromes. La couleur est réservée pour transmettre des informations spécifiques et jamais pour la décoration. La couleur est utilisée:

- pour indiquer une action

- pour alerter l’utilisateur d’une notification d’état

- désigner l’affiliation linguistique

- pour différencier les éléments au sein d’IntelliSense

### <a name="accessibility"></a>Accessibilité
 Les directives de conformité Visual Studio exigent que toutes les icônes vérifiées dans le produit passent les exigences d’accessibilité pour la couleur et le contraste. Les couleurs de la palette de langage visuel ont été testées et répondent à ces exigences.

#### <a name="color-inversion-for-dark-themes"></a>Inversion de couleur pour les thèmes sombres
 Afin de faire apparaître les icônes avec le rapport de contraste correct dans le thème sombre Visual Studio, une inversion est appliquée programmatiquement. Les couleurs de ce guide ont été choisies en partie pour qu’elles s’inversent correctement. Limitez votre utilisation de la couleur à cette palette, ou vous obtiendrez des résultats imprévisibles lorsque l’inversion est appliquée.

 ![Exemples d’icônes qui ont eu leurs couleurs inversées](../../extensibility/ux-guidelines/media/0405-01_darkthemeinversion.png "0405-01_DarkThemeInversion")<br />Exemples d’icônes qui ont eu leurs couleurs inversées

### <a name="base-palette"></a>Palette de base
 Toutes les icônes standard contiennent trois couleurs de base. Les icônes ne contiennent pas de gradients ou d’ombres de chute, à une ou deux exceptions près pour les icônes à outils 3D.

|Usage|Nom|Valeur (thème léger)|Swatch| Exemple|
|-----------|----------|---------------------------|------------|-------------|
|Contexte/Dark|VS BG|424242 / 66,66,66|![Échantillon 424242](../../extensibility/ux-guidelines/media/0405_424242.png "0405_424242")|![Exemple de palette de base](../../extensibility/ux-guidelines/media/0405-02_basepaletteexample.png "0405-02_BasePaletteExample")|
|Au premier plan/Lumière|VS FG|F0EFF1 / 240 239 241|![Échantillon F0EFF1](../../extensibility/ux-guidelines/media/0405_f0eff1.png "0405_F0EFF1")||
|Contour|VS Out|F6F6F6 / 246 246 246|![Échantillon F6F6F6](../../extensibility/ux-guidelines/media/0405_f6f6f6.png "0405_F6F6F6")||

 En plus des couleurs de base, chaque icône peut contenir une couleur supplémentaire de la palette étendue.

### <a name="extended-palette"></a>Palette étendue

#### <a name="action-modifiers"></a>Modifier d’action
 Les quatre couleurs ci-dessous indiquent les types d’actions requises par les modificateurs d’action :

|Usage|Nom|Valeur (tous les thèmes)|Swatch|
|-----------|----------|--------------------------|------------|
|Positive|VS Action Vert|388A34 / 56 138,52|![Échantillon 388A34](../../extensibility/ux-guidelines/media/0405_388a34.png "0405_388A34")|
|Negative|VS Action Rouge|A1260D / 161,38,13|![Échantillon A1260D](../../extensibility/ux-guidelines/media/0405_a1260d.png "0405_A1260D")|
|Neutre|VS Action Bleu|00539C / 0,83 156|![Échantillon 00539C](../../extensibility/ux-guidelines/media/0405_00539c.png "0405_00539C")|
|Créer/Nouveau|VS Action Orange|C27D1A / 194 156,26|![Échantillon C27D1A](../../extensibility/ux-guidelines/media/0405_c27d1a.png "0405_C27D1A")|

##### <a name="examples"></a>Exemples
 Green est utilisé pour des modificateurs d’action positifs comme « Ajouter », « Courir », « Jouer » et « Valider ».

|||||
|-|-|-|-|
|![Icône d'exécution](../../extensibility/ux-guidelines/media/0405-03_actionmodifierrun.png "0405-03_ActionModifierRun")<br />Exécuter|![Icône Exécuter la requête](../../extensibility/ux-guidelines/media/0405-04_executequery.png "0405-04_ExecuteQuery")<br />Exécuter la requête|![Icône Lire toutes les étapes](../../extensibility/ux-guidelines/media/0405-05_playallsteps.png "0405-05_PlayAllSteps")<br />Jouer toutes les étapes|![Icône Ajouter le contrôle](../../extensibility/ux-guidelines/media/0405-06_addcontrol.png "0405-06_AddControl")<br />Ajouter le contrôle|

 Le rouge est utilisé pour les modificateurs d’action négative comme «Supprimer», «Stop», «Annuler» et «Fermer».

|||||
|-|-|-|-|
|![Icône Supprimer la relation](../../extensibility/ux-guidelines/media/0405-07_deleterelationship.png "0405-07_DeleteRelationship")<br />Supprimer une relation|![Icône Supprimer la colonne](../../extensibility/ux-guidelines/media/0405-08_deletecolumn.png "0405-08_DeleteColumn")<br />Supprimer la colonne|![Icône Arrêter la requête](../../extensibility/ux-guidelines/media/0405-09_stopquery.png "0405-09_StopQuery")<br />Arrêtez la requête|![Icône de connexion en mode hors connexion](../../extensibility/ux-guidelines/media/0405-10_connectionoffline.png "0405-10_ConnectionOffline")<br />Connexion Hors ligne|

 Le bleu est appliqué aux modificateurs d’action neutres le plus souvent représentés comme des flèches, comme « Open », « Next », « Previous », « Import » et « Export ».

|||||
|-|-|-|-|
|![Icône Atteindre le champ](../../extensibility/ux-guidelines/media/0405-11_gotofield.png "0405-11_GoToField")<br />Aller au champ|![Vérification&#45;en icône](../../extensibility/ux-guidelines/media/0405-12_batchedcheckin.png "0405-12_BatchedCheckIn")<br />Enregistrement en lots|![Icône de l'éditeur d'adresse](../../extensibility/ux-guidelines/media/0405-13_addresseditor.png "0405-13_AddressEditor")<br />Rédacteur d’adresse|![Icône de l'éditeur d'associations](../../extensibility/ux-guidelines/media/0405-14_associationeditor.png "0405-14_AssociationEditor")<br />Rédacteur en chef de l’association|

 L’or noir est principalement utilisé pour le « nouveau » modificateur.

|||||
|-|-|-|-|
|![Icône de nouveau projet](../../extensibility/ux-guidelines/media/0405-15_newproject.png "0405-15_NewProject")<br />Nouveau projet|![Icône de création d'un graphique](../../extensibility/ux-guidelines/media/0405-16_createnewgraph.png "0405-16_CreateNewGraph")<br />Créer un nouveau graphique|![Icône de nouveau test unitaire](../../extensibility/ux-guidelines/media/0405-17_newunittest.png "0405-17_NewUnitTest")<br />Nouveau test d’unité|![Icône de nouvel élément de liste](../../extensibility/ux-guidelines/media/0405-18_newlistitem.png "0405-18_NewListItem")<br />Nouvel article de liste|

#### <a name="special-cases"></a>Cas particuliers
 Dans des cas particuliers, un modificateur d’action coloré peut être utilisé indépendamment comme une icône autonome. La couleur utilisée pour l’icône reflète les actions auxquelles l’icône est associée. Cette utilisation est limitée à un petit sous-ensemble d’icônes, y compris:

||||||
|-|-|-|-|-|
|![Icône d'exécution](../../extensibility/ux-guidelines/media/0405-03_actionmodifierrun.png "0405-03_ActionModifierRun")<br />Exécuter|![Icône Arrêter](../../extensibility/ux-guidelines/media/0405-19_stop.png "0405-19_Stop")<br />Arrêter|![Supprimer l’icône](../../extensibility/ux-guidelines/media/0405-20_delete.png "0405-20_Delete")<br />DELETE|![Icône Enregistrer](../../extensibility/ux-guidelines/media/0405-21_save.png "0405-21_Save")<br />Enregistrer|![Icône Naviguer vers l'arrière](../../extensibility/ux-guidelines/media/0405-22_navigateback.png "0405-22_NavigateBack")<br />Naviguer vers l'arrière|

### <a name="code-hierarchy-palette"></a>Palette de hiérarchie de code

#### <a name="folder"></a>Dossier

|Usage|Nom|Valeur (tous les thèmes)|Swatch| Exemple|
|-----------|----------|--------------------------|------------|-------------|
|Dossiers|Dossier|DCB67A / 220 182 122|![Échantillon DCB67A](../../extensibility/ux-guidelines/media/0405_dcb67a.png "0405_DCB67A")|![Icône de couleur de dossier](../../extensibility/ux-guidelines/media/0405-23_foldercolor.png "0405-23_FolderColor")|

#### <a name="visual-studio-languages"></a>Langage Visual Studio
 Chacune des langues ou plates-formes courantes disponibles dans Visual Studio a une couleur associée. Ces couleurs sont utilisées sur l’icône de base, ou sur les modificateurs de langage qui apparaissent dans le coin supérieur droit des icônes composées.

|Usage|Nom|Valeur (tous les thèmes)|Swatch|
|-----------|----------|--------------------------|------------|
|ASP, HTML, WPF|ASP HTML WPF Bleu|0095D7 / 0,149,215|![Échantillon 0095D7](../../extensibility/ux-guidelines/media/0405_0096d7.png "0405_0096D7")|
|C++|RPC Purple|9B4F96 / 155 79 150|![Échantillon 9B4F96](../../extensibility/ux-guidelines/media/0405_9b4f96.png "0405_9B4F96")|
|C#|CS Green (VS Action Green)|388A34 / 56 138,52|![Échantillon 388A34](../../extensibility/ux-guidelines/media/0405_388a34.png "0405_388A34")|
|CSS|CSS Rouge|BD1E2D / 189,30,45|![Échantillon BD1E2D](../../extensibility/ux-guidelines/media/0405_bd1e2d.png "0405_BD1E2D")|
|F#|FS pourpre|672878 / 103,40,120|![Échantillon 672878](../../extensibility/ux-guidelines/media/0405_672878.png "0405_672878")|
|JavaScript|JS Orange|F16421 / 241 100,33|![Échantillon F16421](../../extensibility/ux-guidelines/media/0405_f16421.png "0405_F16421")|
|VB|VB Blue (VS Action Blue)|00539C / 0,83 156|![Échantillon 00539C](../../extensibility/ux-guidelines/media/0405_00539c.png "0405_00539C")|
|TypeScript|TS Orange|E04C06 / 224,76,6|![Échantillon E04C06](../../extensibility/ux-guidelines/media/0405_e04c06.png "0405_E04C06")|
|Python|PY Vert|879636 / 135,150,54|![Échantillon 879636](../../extensibility/ux-guidelines/media/0405_879636.png "0405_879636")|

##### <a name="examples-of-icons-with-language-modifiers"></a>Exemples d’icônes avec modificateurs de langage

|||||||
|-|-|-|-|-|-|
|![Icône Visual Basic](../../extensibility/ux-guidelines/media/0405-25_vb.png "0405-25_VB")<br />VB|![Icône C&#35;](../../extensibility/ux-guidelines/media/0405-26_csharp.png "0405-26_CSharp")<br />C#|![C&#43;&#43; 'icône](../../extensibility/ux-guidelines/media/0405-27_cplusplus.png "0405-27_CPlusPlus")<br />C++|![Icône F&#35;](../../extensibility/ux-guidelines/media/0405-28_fsharp.png "0405-28_FSharp")<br />F#|![Icône JavaScript](../../extensibility/ux-guidelines/media/0405-29_javascript.png "0405-29_JavaScript")<br />JavaScript|![Icône Python](../../extensibility/ux-guidelines/media/0405-30_python.png "0405-30_Python")<br />Python|
|![Icône HTML](../../extensibility/ux-guidelines/media/0405-31_html.png "0405-31_HTML")<br />HTML|![Icône WPF](../../extensibility/ux-guidelines/media/0405-32_wpf.png "0405-32_WPF")<br />WPF|![Icône ASP](../../extensibility/ux-guidelines/media/0405-33_asp.png "0405-33_ASP")<br />ASP|![Icône CSS](../../extensibility/ux-guidelines/media/0405-34_css.png "0405-34_CSS")<br />CSS|![Icône TypeScript](../../extensibility/ux-guidelines/media/0405-35_typescript.png "0405-35_TypeScript")<br />TypeScript||

#### <a name="intellisense"></a>IntelliSense
 Les icônes IntelliSense utilisent une palette de couleurs exclusive. Ces couleurs sont utilisées pour aider les utilisateurs à distinguer rapidement entre les différents éléments de la liste de popup IntelliSense.

|Usage|Nom|Valeur (tous les thèmes)|Swatch|
|-----------|----------|--------------------------|------------|
|Classe, Événement|VS Action Orange|C27D1A / 194 125,26|![Échantillon C27D1A](../../extensibility/ux-guidelines/media/0405_c27d1a.png "0405_C27D1A")|
|Méthode d’extension, Méthode, Module, Délégué|VS Action Violet|652D90 / 101,45,144|![Échantillon 652D90](../../extensibility/ux-guidelines/media/0405_652d90.png "0405_652D90")|
|Champ, Enum Item, Macro, Structure, Union Value Type, Opérateur, Interface|VS Action Bleu|00539C / 0,83 156|![Échantillon 00539C](../../extensibility/ux-guidelines/media/0405_00539c.png "0405_00539C")|
|Object|VS Action Vert|388A34 / 56 138,52|![Échantillon 388A34](../../extensibility/ux-guidelines/media/0405_388a34.png "0405_388A34")|
|Constante, Exception, Enum Item, Carte, Article de carte, Namespace, Template, Définition de type|Contexte (VS BG)|424242 / 66,66,66|![Échantillon 424242](../../extensibility/ux-guidelines/media/0405_424242.png "0405_424242")|

##### <a name="examples-of-intellisense-icons"></a>Exemples d’icônes IntelliSense

||||||
|-|-|-|-|-|
|![Icône de classe IntelliSense](../../extensibility/ux-guidelines/media/0405-36_intellisenseclass.png "0405-36_IntelliSenseClass")<br />Classe|![Icône d'événement privé IntelliSense](../../extensibility/ux-guidelines/media/0405-37_intellisenseprivateevent.png "0405-37_IntelliSensePrivateEvent")<br />Événement privé|![Icône de délégué IntelliSense](../../extensibility/ux-guidelines/media/0405-38_intellisensedelegate.png "0405-38_IntelliSenseDelegate")<br />Déléguer|![Icône friend de méthode IntelliSense](../../extensibility/ux-guidelines/media/0405-39_intellisensemethodfriend.png "0405-39_IntelliSenseMethodFriend")<br />Ami de méthode|![Icône de champ](../../extensibility/ux-guidelines/media/0405-40_field.png "0405-40_Field")<br />Champ|
|![Icône d'élément enum protégé IntelliSense](../../extensibility/ux-guidelines/media/0405-41_intellisenseprotectedenumitem.png "0405-41_IntelliSenseProtectedEnumItem")<br />Article Enum protégé|![Icône d'objet IntelliSense](../../extensibility/ux-guidelines/media/0405-42_intellisenseobject.png "0405-42_IntelliSenseObject")<br />Object|![Icône de modèle IntelliSense](../../extensibility/ux-guidelines/media/0405-43_intellisensetemplate.png "0405-43_IntelliSenseTemplate")<br />Modèle|![Icône de raccourci d'exception IntelliSense](../../extensibility/ux-guidelines/media/0405-44_intellisenseexceptionshortcut.png "0405-44_IntelliSenseExceptionShortcut")<br />Shortcut d’exception||

### <a name="notifications"></a>Notifications
 Les notifications dans Visual Studio sont utilisées pour indiquer l’état. La palette de notification utilise les quatre couleurs suivantes, ainsi que les options de remplissage au premier plan noir ou blanc, pour définir les notifications avec les niveaux de statut suivants.

|Usage|Nom|Valeur (tous les thèmes)|Swatch|
|-----------|----------|--------------------------|------------|
|Statut: neutre|Notification Blue (VS Blue)|1BA1E2 / 27 161 226|![Échantillon 1BA1E2](../../extensibility/ux-guidelines/media/0405_1ba1e2.png "0405_1BA1E2")|
|Statut: positif|Notification verte (VS Green)|339933 / 51,153,51|![Échantillon 339933](../../extensibility/ux-guidelines/media/0405_339933.png "0405_339933")|
|Statut: négatif|Notification Rouge (VS Red)|E51400 / 229,20,0|![Échantillon E51400](../../extensibility/ux-guidelines/media/0405_e51400.png "0405_E51400")|
|Statut: avertissement|Notification Jaune (VS Orange)|FFCC00 / 255 204,0|![Échantillon FFCC00](../../extensibility/ux-guidelines/media/0405_ffcc00.png "0405_FFCC00")|
|Remplissage au premier plan|Notification Noire (Noir)|000000 / 0,0,0|![Swatch &#35;000000](../../extensibility/ux-guidelines/media/0405_000000.png "0405_000000")|
|Remplissage au premier plan|Notification Blanche (Blanc)|FFFFFF / 255 255 255|![Échantillon FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|

#### <a name="examples-of-notification-icons"></a>Exemples d’icônes de notification

|||||
|-|-|-|-|
|![Icône Alerte](../../extensibility/ux-guidelines/media/0405-45_alert.png "0405-45_Alert")<br />Alerte|![Icône d'avertissement](../../extensibility/ux-guidelines/media/0405-48_warning.png "0405-48_Warning")<br />Avertissement|![Icône Terminé](../../extensibility/ux-guidelines/media/0405-46_complete.png "0405-46_Complete")<br />Terminé|![Icône Arrêter](../../extensibility/ux-guidelines/media/0405-47_stop.png "0405-47_Stop")<br />Arrêter|

### <a name="visual-studio-online"></a>Visual Studio Online
 En général, Visual Studio Online se compose de fonctionnalités hébergées dans un navigateur. La couleur varie dans différents environnements, mais le style reste le même.

|Groupe|Usage|Nom|Valeur (tous les thèmes)|Swatch|
|-----------|-----------|----------|--------------------------|------------|
|TFS|Arrière-plan|TFSO BG|656565/ 101, 101, 101|![Échantillon 656565](../../extensibility/ux-guidelines/media/0405_656565.png "0405_656565")|
|TFS|Contour|TFSO OUT|FFFFFF / 255, 255, 255|![Échantillon FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|
|Napa|Arrière-plan|White|FFFFFF / 255, 255, 255|![Échantillon FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|
|Monaco|Arrière-plan|White|FFFFFF / 255, 255, 255|![Échantillon FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|
|F12|Arrière-plan|White|FFFFFF / 255, 255, 255|![Échantillon FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|
|F12|Normal|F12 Grey_Primary|555555 / 85, 85, 85|![Échantillon 555555](../../extensibility/ux-guidelines/media/0405_555555.png "0405_555555")|
|F12|Pointage|F12 Blue_Hover|2279BF / 34 121 191|![Échantillon 2279BF](../../extensibility/ux-guidelines/media/0405_2279bf.png "0405_2279BF")|
|F12|Désactivé|F12 LtGrey_Disabled|ABABAC / 171 171 172|![Échantillon ABABAC](../../extensibility/ux-guidelines/media/0405_ababac.png "0405_ABABAC")|
|F12|Fond de planer|Bg de vol stationnaire|D9EBF7 / 217 235 247|![Échantillon D9EBF7](../../extensibility/ux-guidelines/media/0405_d9ebf7.png "0405_D9EBF7")|
|F12|Fond pressé|Bg pressé|B2D7F0 / 178 215 240|![Échantillon B2D7F0](../../extensibility/ux-guidelines/media/0405_b2d7f0.png "0405_B2D7F0")|
|F12|Contour|VS OUT|F6F6F6 / 246 246 246|![Échantillon F6F6F6](../../extensibility/ux-guidelines/media/0405_f6f6f6.png "0405_F6F6F6")|
|F12|Information|Information|00BCF2 / 0 188 242|![Échantillon 00BCF2](../../extensibility/ux-guidelines/media/0405_00bcf2.png "0405_00BCF2")|
|F12|Avertissement|Avertissement|F28300 / 242 131,0|![Échantillon F28300](../../extensibility/ux-guidelines/media/0405_f28300.png "0405_F28300")|
|F12|Erreur / Négatif|Error_Negative|E81123 / 232,17,35|![Échantillon E81123](../../extensibility/ux-guidelines/media/0405_e81123.png "0405_E81123")|
|F12|Démarrer / Positif|Start_Positive|009E49 / 0,158,73|![Échantillon 009E49](../../extensibility/ux-guidelines/media/0405_009e49.png "0405_009E49")|
|F12|Type de rupture|Type de rupture|9B4F96 / 155 79 150|![Échantillon 9B4F96](../../extensibility/ux-guidelines/media/0405_9b4f96.png "0405_9B4F96")|
|F12|Marque de l’événement|Marque de l’événement|A51F00 / 165,31,0|![Échantillon A51F00](../../extensibility/ux-guidelines/media/0405_a51f00.png "0405_A51F00")|
|F12|Marque utilisateur|Marque utilisateur|F16220 / 241,98,32|![Échantillon F16220](../../extensibility/ux-guidelines/media/0405_f16220.png "0405_F16220")|

#### <a name="examples-of-visual-studio-online-icons"></a>Exemples d’icônes Visual Studio Online

|TFS en ligne||||
|----------------|-|-|-|
|![Icône de l’équipe TFS en ligne](../../extensibility/ux-guidelines/media/0405-49_tfsonlineteam.png "0405-49_TFSOnlineTeam")<br />Équipe en ligne|![Icône d'informations TFS](../../extensibility/ux-guidelines/media/0405-50_tfsinformation.png "0405-50_TFSInformation")<br />Information|![Icône de l'historique TFS](../../extensibility/ux-guidelines/media/0405-51_tfshistory.png "0405-51_TFSHistory")<br />Historique|![Icône de branche TFS](../../extensibility/ux-guidelines/media/0405-52_tfsbranch.png "0405-52_TFSBranch")<br />Branche|

|Napa||||
|----------|-|-|-|
|![Icône de contenu Napa](../../extensibility/ux-guidelines/media/0405-53_napacontent.png "0405-53_NapaContent")<br />Contenu|![Icône de courrier de bureau Napa](../../extensibility/ux-guidelines/media/0405-54_napaofficemail.png "0405-54_NapaOfficeMail")<br />Courrier de bureau|![Icône Napa SharePoint](../../extensibility/ux-guidelines/media/0405-55_napasharepoint.png "0405-55_NapaSharePoint")<br />SharePoint|![Icône de volet de tâches Napa](../../extensibility/ux-guidelines/media/0405-56_napataskpane.png "0405-56_NapaTaskPane")<br />Volet des tâches|

|Monaco||||
|------------|-|-|-|
|![Icône de fichiers Monaco](../../extensibility/ux-guidelines/media/0405-57_monacofiles.png "0405-57_MonacoFiles")<br />Fichiers|![Icône Git Monaco](../../extensibility/ux-guidelines/media/0405-58_monacogit.png "0405-58_MonacoGit")<br />Git|![Icône de recherche Monaco](../../extensibility/ux-guidelines/media/0405-59_monacosearch.png "0405-59_MonacoSearch")<br />Recherche|![Icône de texte Monaco](../../extensibility/ux-guidelines/media/0405-60_monacotext.png "0405-60_MonacoText")<br />Texte|

|F12|||
|---------|-|-|
|![Icône de code automatique F12](../../extensibility/ux-guidelines/media/0405-61_f12prettycode.png "0405-61_F12PrettyCode")<br />Pretty Code|![Icône d'avertissement F12](../../extensibility/ux-guidelines/media/0405-62_f12warning.png "0405-62_F12Warning")<br />Avertissement|![Icône Émuler F12](../../extensibility/ux-guidelines/media/0405-63_f12emulate.png "0405-63_F12Emulate")<br />Émuler|