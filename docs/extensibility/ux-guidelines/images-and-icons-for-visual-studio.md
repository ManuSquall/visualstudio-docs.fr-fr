---
title: Images et icônes pour Visual Studio | Microsoft Docs
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: f410325e-9cf2-4f39-b6d7-b672121c2691
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1e449fb30bd95319a46d1db50da63778f6800a70
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72983870"
---
# <a name="images-and-icons-for-visual-studio"></a>Images et icônes pour Visual Studio
## <a name="BKMK_ImageUseInVisualStudio"></a>Utilisation d’images dans Visual Studio
 Avant de créer des illustrations, envisagez d’utiliser les 1 000 images dans la [bibliothèque d’images Visual Studio](https://www.microsoft.com/download/details.aspx?id=35825).

### <a name="types-of-images"></a>Types d’images

- **Icônes**. Petites images qui apparaissent dans les commandes, les hiérarchies, les modèles, et ainsi de suite. La taille d’icône par défaut utilisée dans Visual Studio est un format PNG 16x16. Les icônes générées par le service d’images génèrent automatiquement le format XAML pour la prise en charge de HDPI.

    > [!NOTE]
    > Alors que les images sont utilisées dans le système de menus, vous ne devez pas créer d’icône pour chaque commande. Consultez les [menus et commandes de Visual Studio](../../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md) pour voir si votre commande doit obtenir une icône.

- **Miniatures.** Images utilisées dans la zone d’aperçu d’une boîte de dialogue, telle que la boîte de dialogue Nouveau projet.

- **Images de dialogue.** Images qui apparaissent dans les boîtes de dialogue ou les assistants, en tant que graphiques descriptifs ou indicateurs de message. Utilisez rarement et uniquement lorsque cela est nécessaire pour illustrer un concept difficile ou obtenir l’attention de l’utilisateur (alerte, avertissement).

- **Images animées.** Utilisé dans les indicateurs de progression, les barres d’État et les boîtes de dialogue d’opération.

- **Curseurs.** Permet d’indiquer si une opération est autorisée à l’aide de la souris, où un objet peut être supprimé, et ainsi de suite.

## <a name="BKMK_IconDesign"></a>Conception d’icône

### <a name="overview"></a>Vue d'ensemble
 Visual Studio utilise des icônes de style moderne, qui ont une géométrie propre et un équilibre 50/50 positif/négatif (clair/sombre), et qui utilisent des métaphores directes et compréhensibles. Icône cruciale points de conception centrer autour de la clarté, de la simplification et du contexte.

- **Clarté :** concentrez-vous sur la métaphore principale qui donne une icône de sa signification et de sa propre individualité.

- **Simplification :** réduire l’icône à sa signification principale : faites passer le thème avec uniquement les éléments nécessaires et aucun base.

- **Contexte :** tenez compte de tous les aspects du rôle d’une icône au cours du développement du concept, ce qui est essentiel lorsque vous décidez quels éléments constituent la métaphore principale de l’icône.

  Avec les icônes, il existe un certain nombre de points de conception à éviter :

- N’utilisez pas d’icônes qui indiquent des éléments d’interface utilisateur, sauf le cas échéant. Choisissez une approche plus abstraite ou symbolique lorsque l’élément d’interface utilisateur n’est ni commun, évident ni unique.

- N’abusez pas des éléments courants tels que les documents, les dossiers, les flèches et la loupe. Utilisez ces éléments uniquement lorsqu’il est essentiel de la signification de l’icône. Par exemple, la loupe de droite doit indiquer uniquement les recherches, les recherches et les recherches.

- Bien que certains éléments d’icône hérités maintiennent l’utilisation de perspective, ne créez pas de nouvelles icônes avec perspective, sauf si l’élément n’a pas de clarté.

- Ne récolter pas trop d’informations dans une icône. Une simple image qui peut être facilement reconnue ou apprise comme un symbole reconnaissable est beaucoup plus utile qu’une image trop complexe. Une icône ne peut pas indiquer la totalité du récit.

### <a name="icon-creation"></a>Création d’icône

#### <a name="concept-development"></a>Développement de concept
 Dans son interface utilisateur, Visual Studio offre un large éventail de types d’icônes. Examinez attentivement le type d’icône pendant le développement. N’utilisez pas d’objets d’interface utilisateur non clairs ou inhabituels pour vos éléments d’icône. Optez pour le symbolique dans ces cas, par exemple avec l’icône de balise active. Notez que la signification de la balise abstraite sur la gauche est plus évidente que la version vague, basée sur l’interface utilisateur, à droite :

|||
|-|-|
|**Utilisation correcte de l’image symbolique**|**Utilisation incorrecte de l’image symbolique**|
|![Icône de balise active correcte](../../extensibility/ux-guidelines/media/0404-01_smarttagcorrect.png "0404-01 _SmartTagCorrect")|![Icône de balise active incorrecte](../../extensibility/ux-guidelines/media/0404-02_smarttagincorrect.png "0404 -02 _SmartTagIncorrect")|

 Il existe des instances dans lesquelles des éléments d’interface utilisateur standard et facilement reconnaissables fonctionnent bien pour les icônes. La fenêtre Ajouter est un exemple :

|||
|-|-|
|**Corriger l’élément d’interface utilisateur dans une icône**|**Élément d’interface utilisateur incorrect dans une icône**|
|![Icône d’ajout de fenêtre correcte](../../extensibility/ux-guidelines/media/0404-03_addwindowcorrect.png "0404 -03 _AddWindowCorrect")|![Icône d’ajout de fenêtre incorrecte](../../extensibility/ux-guidelines/media/0404-04_addwindowincorrect.png "0404 -04 _AddWindowIncorrect")|

 N’utilisez pas un document comme élément de base à moins qu’il soit essentiel à la signification de l’icône. Sans l’élément document sur Ajouter un document (ci-dessous), la signification est perdue, alors que avec l’actualisation, l’élément document n’est pas nécessaire pour communiquer la signification.

|||
|-|-|
|**Utilisation correcte de l’icône de document**|**Utilisation incorrecte de l’icône de document**|
|![Icône de document correct](../../extensibility/ux-guidelines/media/0404-05_documenticoncorrect.png "0404 -05 _DocumentIconCorrect")|![Icône de document incorrecte](../../extensibility/ux-guidelines/media/0404-06_documenticonincorrect.png "0404-06 _DocumentIconIncorrect")|

 Le concept d’affichage doit être représenté par l’icône qui illustre le mieux ce qui est affiché, comme avec l’exemple afficher tous les fichiers. Une métaphore d’objectif peut être utilisée pour indiquer le concept de « vue », si nécessaire, comme avec l’exemple de Affichage des ressources.

|||
|-|-|
|**Afficher**|**Affichage**|
|![Afficher l’icône](../../extensibility/ux-guidelines/media/0404-07_show.png "0404 -07 _ afficher")|![Icône d’affichage](../../extensibility/ux-guidelines/media/0404-08_view.png "0404 -08 _View")|

 L’icône de loupe qui se trouve à droite doit représenter uniquement les recherches, les recherches et les navigations. La variante orientée vers la gauche avec le signe plus ou le signe moins doit représenter uniquement un zoom avant/arrière.

|||
|-|-|
|**Recherche**|**Focale**|
|![Icône de recherche](../../extensibility/ux-guidelines/media/0404-09_search.png "0404 -09 _ Search")|![Icône de zoom](../../extensibility/ux-guidelines/media/0404-10_zoom.png "0404 -10 _Zoom")|

 Dans les arborescences, n’utilisez pas à la fois l’icône de dossier et un modificateur. Quand elle est disponible, utilisez uniquement le modificateur.

|||
|-|-|
|**Icônes appropriées de l’arborescence**|**Icônes d’arborescence incorrectes**|
|![Icône &#40;d’arborescence correcte 1&#41; ](../../extensibility/ux-guidelines/media/0404-11_treeviewcorrect1.png "0404 -11 _TreeViewCorrect1") icône d’arborescence ![correcte &#40;2&#41; ](../../extensibility/ux-guidelines/media/0404-12_treeviewcorrect2.png "0404 12 _TreeViewCorrect2")|![&#40;Icône d’arborescence incorrecte 1&#41; ](../../extensibility/ux-guidelines/media/0404-13_treeviewincorrect1.png "0404 -13 _TreeViewIncorrect1") icône ![ &#40;d’arborescence incorrecte 2&#41; ](../../extensibility/ux-guidelines/media/0404-14_treeviewincorrect2.png "0404 -14 _TreeViewIncorrect2")|

### <a name="style-details"></a>Détails du style

#### <a name="layout"></a>Mise en page
 Empilez les éléments comme indiqué pour les icônes standard 16x16 :

 ![Pile de disposition pour les icônes 16x16](../../extensibility/ux-guidelines/media/0404-15_layoutstack.png "0404-15.0 _LayoutStack")<br />Pile de disposition pour les icônes 16x16

 Les éléments de notification d’État sont mieux utilisés comme icônes autonomes. Toutefois, il existe des contextes dans lesquels une notification doit être empilée sur l’élément de base, par exemple avec l’icône de tâche terminée :

 ![Notifications autonomes dans Visual Studio](../../extensibility/ux-guidelines/media/0404-16_standalonenotificationicons.png "0404-16 _StandaloneNotificationIcons")<br />Icônes de notification autonomes

 ![Icône tâche terminée](../../extensibility/ux-guidelines/media/0404-17_taskcomplete.png "0404 -17 _TaskComplete")<br />Icône tâche terminée

 Les icônes de projet sont généralement des fichiers. ico qui contiennent plusieurs tailles. La plupart des icônes 16x16 contiennent les mêmes éléments. Les versions 32x32 présentent davantage de détails, y compris le type de projet, le cas échéant.

 ![Icônes de projet dans Visual Studio](../../extensibility/ux-guidelines/media/0404-18_iconprojectthreesizes.png "0404 -18 _IconProjectThreeSizes")<br />Icônes de projet de bibliothèque de contrôles Windows VB, 16x16 et 32x32

 Centrer une icône dans son cadre de pixels. Si ce n’est pas possible, alignez l’icône en haut et/ou à droite du cadre.

 ![Icône centrée dans le frame de pixels](../../extensibility/ux-guidelines/media/0404-19_iconcentered.png "0404 -19 _IconCentered")<br />Icône centrée dans le frame de pixels

 ![Icône alignée en haut à droite du frame de pixel](../../extensibility/ux-guidelines/media/0404-20_icontopright.png "0404 -20 _IconTopRight")<br />Icône alignée en haut à droite du cadre

 ![Icône centrée et alignée sur le bord supérieur du frame de pixels](../../extensibility/ux-guidelines/media/0404-21_icontopalign.png "0404 -21 _IconTopAlign")<br />Icône centrée et alignée sur le bord supérieur du frame

 Pour obtenir un alignement et un équilibre idéals, évitez d’obstruer l’élément de base de l’icône avec des glyphes d’action. Placez le glyphe près de l’angle supérieur gauche de l’élément de base. Lorsque vous ajoutez un élément supplémentaire, tenez compte de l’alignement et de l’équilibre de l’icône.

|||
|-|-|
|**Alignement et équilibre corrects**|**Alignement et équilibre incorrects**|
|![Équilibre de l’icône et alignement corrects](../../extensibility/ux-guidelines/media/0404-22_alignbalancecorrect.png "0404 -22 _AlignBalanceCorrect")|![Équilibre et alignement des icônes incorrects](../../extensibility/ux-guidelines/media/0404-23_alignbalanceincorrect.png "0404 -23 _AlignBalanceIncorrect")|

 Vérifiez la parité de taille pour les icônes qui partagent des éléments et qui sont utilisées dans les jeux. Notez que dans le jumelage incorrect, le cercle et la flèche sont surdimensionnés et ne correspondent pas.

|||
|-|-|
|**Parité de taille correcte**|**Parité de taille incorrecte**|
|![Taille et parité des icônes correctes](../../extensibility/ux-guidelines/media/0404-24_sizeparitycorrect.png "0404 -24 _SizeParityCorrect")|![Taille et parité des icônes incorrectes](../../extensibility/ux-guidelines/media/0404-25_sizeparityincorrect.png "0404 -25 _SizeParityIncorrect")|

 Utilisez des pondérations courbes et visuelles cohérentes. Évaluer la façon dont l’icône que vous générez est comparée à d’autres icônes à l’aide d’une comparaison côte à côte. N’utilisez jamais la totalité de la trame 16x16, utilisez 15x15 ou une valeur inférieure. Le rapport négatif/positif (sombre-à-clair) doit être 50/50.

|||
|-|-|
|**Corriger le rapport négatif-positif**|**Rapport négatif-positif incorrect**|
|![Pondération visuelle correcte pour les &#40;icônes 1&#41;](../../extensibility/ux-guidelines/media/0404-26_visualweightcorrect1.png "0404 -26 _VisualWeightCorrect1")<br /><br /> ![Pondération visuelle correcte pour les &#40;icônes 2&#41;](../../extensibility/ux-guidelines/media/0404-27_visualweightcorrect2.png "0404 -27 _VisualWeightCorrect2 ")<br /><br /> ![Pondération visuelle correcte pour les &#40;icônes 3&#41;](../../extensibility/ux-guidelines/media/0404-28_visualweightcorrect3.png "0404 28 _VisualWeightCorrect3 ")|![Poids visuel incorrect pour les icônes](../../extensibility/ux-guidelines/media/0404-29_visualweightincorrect.png "0404 -29 _VisualWeightIncorrect")|

 Utilisez des formes et des angles complémentaires simples et comparables pour créer vos éléments sans sacrifier l’intégrité de l’élément. Utilisez des angles 45 ° ou 90 ° dans la mesure du possible.

 ![Angles d’icône corrects](../../extensibility/ux-guidelines/media/0404-30_iconanglescorrect.png "0404 -30 _IconAnglesCorrect")

#### <a name="perspective"></a>Perspective
 Laissez l’icône claire et compréhensible. Utilisez la perspective et une source de lumière uniquement lorsque cela est nécessaire. Bien qu’il soit possible d’éviter l’utilisation de la perspective sur les éléments icon, certains éléments ne peuvent pas être reconnaissables. Dans ce cas, une perspective stylisée communique la clarté de l’élément.

 ![perspective à 3 points](../../extensibility/ux-guidelines/media/0404-31_3pointperspective.png "0404 -31 _3PointPerspective")<br />Perspective à 3 points

 ![point de vue 1](../../extensibility/ux-guidelines/media/0404-32_1pointperspective.png "0404 -32 _1PointPerspective")<br />Perspective à 1 point

 La plupart des éléments doivent être orientés ou inclinés vers la droite :

 ![Icônes avec angle droit](../../extensibility/ux-guidelines/media/0404-33_angledright.png "0404 -33 _AngledRight")

 Utilisez des sources de lumière uniquement lorsque vous ajoutez la clarté nécessaire à un objet.

|||
|-|-|
|**Source de lumière correcte**|**Source de lumière incorrecte**|
|![Corriger les sources de lumière pour les icônes](../../extensibility/ux-guidelines/media/0404-34_lightsourcescorrect.png "0404 -34 _LightSourcesCorrect")|![Sources de lumière incorrectes pour les icônes](../../extensibility/ux-guidelines/media/0404-35_lightsourcesincorrect.png "0404 -35 _LightSourcesIncorrect")|

 Utilisez des contours uniquement pour améliorer la lisibilité ou mieux communiquer la métaphore. Le solde négatif positif (foncé) doit être 50/50.

|||
|-|-|
|**Utilisation correcte des plans**|**Utilisation incorrecte des plans**|
|![Corriger les contours](../../extensibility/ux-guidelines/media/0404-36_outlinescorrect.png "0404 -36 _OutlinesCorrect")|![Contours incorrects](../../extensibility/ux-guidelines/media/0404-37_outlinesincorrect.png "0404 -37 _OutlinesIncorrect")|

#### <a name="icon-types"></a>Types d’icônes
 Les icônes de l' **interpréteur de commandes et** de la barre de commandes ne comportent pas plus de trois des éléments suivants : une base, un modificateur, une action ou un État.

 ![Exemples d’icônes de Shell et de barre de commandes](../../extensibility/ux-guidelines/media/0404-38_shellicons.png "0404 -38 _ShellIcons")<br />Exemples d’icônes de Shell et de barre de commandes

 Les icônes de la barre de commandes de la **fenêtre outil** ne comportent pas plus de trois des éléments suivants : une base, un modificateur, une action ou un État.

 ![Exemples d’icônes de la barre de commandes de la fenêtre outil](../../extensibility/ux-guidelines/media/0404-39_toolwindowcommandbaricons.png "0404 -39 _ToolWindowCommandBarIcons")<br />Exemples d’icônes de la barre de commandes de la fenêtre outil

 Les icônes d' **arborescence désambiguïsateur** ne comportent pas plus de trois des éléments suivants : une base, un modificateur, une action ou un État.

 ![Exemples d’icônes désambiguïsateur en mode arborescence](../../extensibility/ux-guidelines/media/0404-40_treeviewicons.png "0404 -40 _TreeViewIcons")<br />Exemples d’icônes désambiguïsateur en mode arborescence

 Les icônes de taxonomie de la **valeur basée sur l’État** existent dans les États suivants : active, active, désactivée et inactive.

 ![Exemples d’icônes de taxonomie de valeurs basées sur l’État](../../extensibility/ux-guidelines/media/0404-41_statebasedtaxonomy.png "0404-41 _StateBasedTaxonomy")<br />Exemples d’icônes de taxonomie de valeurs basées sur l’État

 Les icônes **IntelliSense** ne comportent pas plus de trois des éléments suivants : un de base, un modificateur et un État.

 ![Exemples d’icônes IntelliSense](../../extensibility/ux-guidelines/media/0404-42_intellisenseicons.png "0404 -42 _IntelliSenseIcons")<br />Exemples d’icônes IntelliSense

 Les **petites icônes de projet (16x16)** ne doivent pas comporter plus de deux éléments : un de base et un modificateur.

 ![Exemples de petites (16x16) icônes de](../../extensibility/ux-guidelines/media/0404-43_16x16project1.png "0404 -43 _16x16Project1") projet ![16x16 icône &#40;de&#41; projet 2](../../extensibility/ux-guidelines/media/0404-44_16x16project2.png "0404 -44 _16x16Project2") ![16x16 &#40;icône&#41; de projet 3](../../extensibility/ux-guidelines/media/0404-45_16x16project3.png "0404 -45 _16x16Project3")<br />Exemples de petites icônes de projet (16x16)

 Les grandes icônes de **projet (32x32)** ne comportent pas plus de quatre des éléments suivants : une base, un à deux modificateurs et une superposition de langue.

 ![Exemples d’icônes de projet volumineuses (32x32)](../../extensibility/ux-guidelines/media/0404-46_32x32project.png "0404 -46 _32x32Project")<br />Exemples d’icônes de projet volumineuses (32x32)

### <a name="production-details"></a>Détails de la production
 Tous les nouveaux éléments d’interface utilisateur doivent être créés à l’aide d’Windows Presentation Foundation (WPF) et toutes les nouvelles icônes pour WPF doivent être au format PNG 32 bits. Le format PNG 24 bits est un format hérité qui ne prend pas en charge la transparence et n’est donc pas recommandé pour les icônes.

 Enregistrez la résolution à 96 ppp.

#### <a name="file-types"></a>Types de fichiers

- **PNG 32 bits :** format préféré pour les icônes. Format de fichier de compression de données sans perte qui peut stocker une image raster (pixel) unique. les fichiers PNG 32 bits prennent en charge la transparence de canal alpha, la correction gamma et l’entrelacement.

- **32-bit BMP :** pour les contrôles non WPF. Également appelé XP ou 65536 couleurs, 32 bits BMP est un format d’image RVB/A, une image de couleur vraie avec une transparence de canal alpha. Le canal alpha est une couche de transparence désignée dans Adobe Photoshop qui est ensuite enregistrée dans le bitmap en tant que canal de couleur supplémentaire (quatrième). Un arrière-plan noir est ajouté lors de la production d’illustrations à tous les fichiers BMP de 32 bits pour fournir une indication visuelle rapide sur la profondeur des couleurs. Cet arrière-plan noir représente la zone à masquer dans l’interface utilisateur.

- **32-bit ico :** pour les icônes de projet et ajouter un élément. Tous les fichiers ICO sont des couleurs vraies de 32 bits avec une transparence de canal alpha (RGB/A). Étant donné que les fichiers ICO peuvent stocker plusieurs tailles et profondeurs de couleurs, les icônes Vista sont souvent dans un format ICO contenant des tailles d’image de 16x16, 32x32, 48 et 256x256. Pour afficher correctement dans l’Explorateur Windows, les fichiers ICO doivent être enregistrés à des niveaux de couleurs 24 bits et 8 bits pour chaque taille d’image.

- **XAML :** pour les aires de conception et les ornements Windows. Les icônes XAML sont des fichiers image basés sur des vecteurs qui prennent en charge la mise à l’échelle, la rotation, le classement et la transparence. Ils ne sont pas courants dans Visual Studio aujourd’hui, mais deviennent plus populaires en raison de leur flexibilité.

- **SVG**

- **BMP 24 bits :** pour la barre de commandes Visual Studio. Un format d’image RVB de couleur vraies, le format BMP 24 bits est une convention d’icône qui crée une couche de transparence en utilisant le magenta (R = 255, G = 0, B = 255) comme clé de couleur pour une couche de transparence de masquage. Dans un BMP de 24 bits, toutes les surfaces magenta sont affichées à l’aide de la couleur d’arrière-plan.

- **gif 24 bits :** pour la barre de commandes Visual Studio. Format d’image RVB de couleur vraies qui prend en charge la transparence. Les fichiers GIF sont souvent utilisés dans les animations graphiques et les animations d’Assistant.

### <a name="icon-construction"></a>Construction d’icône
 La taille d’icône la plus petite dans Visual Studio est 16 x 16. La plus grande utilisation courante est 32 x 32. N’oubliez pas de remplir la totalité du frame 16x16, 24x24 ou 32x32 lors de la conception d’une icône. La création d’icônes uniformes est indispensable à la reconnaissance de l’utilisateur. Respectez les points suivants lors de la création d’icônes.

- Les icônes doivent être claires, compréhensibles et cohérentes.

- Il est préférable d’utiliser les éléments de notification d’État comme des icônes uniques et non pour les empiler sur un élément de base d’icône. Dans certains contextes, l’interface utilisateur peut nécessiter que l’élément d’État soit associé à un élément de base.

- Les icônes de projet sont généralement des fichiers. ico qui contiennent plusieurs tailles. Seules les icônes 16x16, 24x24 et 32x32 sont mises à jour. La plupart des icônes 16x16 et 24x24 contiendront les mêmes éléments. Les icônes 32x32 contiennent plus de détails, y compris le type de langage du projet, le cas échéant.

- Pour les icônes 32x32, les éléments de base ont généralement une épaisseur de trait de 2 pixels. Une épaisseur de trait de 1 ou 2 pixels peut être utilisée pour les éléments de détail. Utilisez votre meilleure jugement pour déterminer laquelle est plus appropriée.

- Avoir au moins un espacement de 1 pixel entre les éléments pour les icônes 16x16 et 24x24. Pour les icônes 32x32, utilisez un espacement de 2 pixels entre les éléments et entre le modificateur et l’élément de base.

  ![Espacement des éléments pour les icônes de taille 16x16, 24x24 et 32x32](../../extensibility/ux-guidelines/media/0404-47_elementspacing.png "0404 -47 _ElementSpacing")<br />Espacement des éléments pour les icônes de taille 16x16, 24x24 et 32x32

#### <a name="color-and-accessibility"></a>Couleur et accessibilité
 Les instructions de conformité de Visual Studio requièrent que toutes les icônes du produit respectent les exigences d’accessibilité pour la couleur et le contraste. Cela s’effectue par le biais d’une inversion d’icône et, lorsque vous concevez, vous devez être conscient qu’elles seront inversées par programmation dans le produit.

 Pour plus d’informations sur l’utilisation des couleurs dans les icônes de Visual Studio, consultez [utilisation des couleurs dans les images](../../extensibility/ux-guidelines/images-and-icons-for-visual-studio.md#BKMK_UsingColorInImages).

## <a name="BKMK_UsingColorInImages"></a>Utilisation des couleurs dans les images

### <a name="overview"></a>Vue d'ensemble
 Dans Visual Studio, les icônes sont principalement monochromatiques. La couleur est réservée pour transmettre des informations spécifiques et jamais pour la décoration. La couleur est utilisée :

- pour indiquer une action

- pour avertir l’utilisateur d’une notification d’État

- pour désigner l’affiliation de langue

- pour différencier des éléments dans IntelliSense

### <a name="accessibility"></a>Accessibilité
 Les instructions de conformité de Visual Studio requièrent que toutes les icônes vérifiées dans le produit respectent les exigences d’accessibilité pour la couleur et le contraste. Les couleurs de la palette de langues visuelles ont été testées et répondent à ces exigences.

#### <a name="color-inversion-for-dark-themes"></a>Inversion des couleurs pour les thèmes sombres
 Pour que les icônes apparaissent avec le taux de contraste correct dans le thème Visual Studio Dark, une inversion est appliquée par programmation. Les couleurs de ce guide ont été choisies en partie afin d’être inversées correctement. Limitez votre utilisation de la couleur à cette palette, sinon vous obtiendrez des résultats imprévisibles lorsque l’inversion est appliquée.

 ![Exemples d’icônes dont les couleurs ont été inversées](../../extensibility/ux-guidelines/media/0405-01_darkthemeinversion.png "0405-01 _DarkThemeInversion")<br />Exemples d’icônes dont les couleurs ont été inversées

### <a name="base-palette"></a>Palette de base
 Toutes les icônes standard contiennent trois couleurs de base. Les icônes ne contiennent pas de dégradés ou de ombres portées, avec une ou deux exceptions pour les icônes d’outils 3D.

|Utilisation|Name|Valeur (thème clair)|Echantillon|Exemple|
|-----------|----------|---------------------------|------------|-------------|
|Arrière-plan/sombre|VS BG|424242/66, 66, 66|![Échantillon 424242](../../extensibility/ux-guidelines/media/0405_424242.png "0405_424242")|![Exemple de palette de base](../../extensibility/ux-guidelines/media/0405-02_basepaletteexample.png "0405 -02 _BasePaletteExample")|
|Premier plan/clair|VS FG|F0EFF1/240 239 241|![Échantillon F0EFF1](../../extensibility/ux-guidelines/media/0405_f0eff1.png "0405_F0EFF1")||
|Contour|Différences par rapport à|F6F6F6/246 246 246|![Échantillon F6F6F6](../../extensibility/ux-guidelines/media/0405_f6f6f6.png "0405_F6F6F6")||

 Outre les couleurs de base, chaque icône peut contenir une couleur supplémentaire à partir de la palette étendue.

### <a name="extended-palette"></a>Palette étendue

#### <a name="action-modifiers"></a>Modificateurs d’action
 Les quatre couleurs ci-dessous indiquent les types d’actions requis par les modificateurs d’action :

|Utilisation|Name|Valeur (tous les thèmes)|Echantillon|
|-----------|----------|--------------------------|------------|
|Positif|CONTRE-action en vert|388A34/56138, 52|![Échantillon 388A34](../../extensibility/ux-guidelines/media/0405_388a34.png "0405_388A34")|
|Négatif|CONTRE-action rouge|A1260D/161, 38, 13|![Échantillon A1260D](../../extensibility/ux-guidelines/media/0405_a1260d.png "0405_A1260D")|
|Neutral|Bleu de l’action VS|00539C/0, 83156|![Échantillon 00539C](../../extensibility/ux-guidelines/media/0405_00539c.png "0405_00539C")|
|Créer/nouveau|Action VS orange|C27D1A/194156, 26|![Échantillon C27D1A](../../extensibility/ux-guidelines/media/0405_c27d1a.png "0405_C27D1A")|

##### <a name="examples"></a>Exemples
 Le vert est utilisé pour les modificateurs d’action positifs tels que « ajouter », « exécuter », « lire » et « valider ».

|||||
|-|-|-|-|
|![Icône d’exécution](../../extensibility/ux-guidelines/media/0405-03_actionmodifierrun.png "0405 -03 _ActionModifierRun")<br />Exécuter|![Icône d’exécution de requête](../../extensibility/ux-guidelines/media/0405-04_executequery.png "0405 -04 _ExecuteQuery")<br />Exécuter la requête|![Icône lire toutes les étapes](../../extensibility/ux-guidelines/media/0405-05_playallsteps.png "0405 -05 _PlayAllSteps")<br />Lire toutes les étapes|![Icône d’ajout de contrôle](../../extensibility/ux-guidelines/media/0405-06_addcontrol.png "0405-06 _AddControl")<br />Ajouter un contrôle|

 Le rouge est utilisé pour les modificateurs d’action négatifs tels que « supprimer », « arrêter », « annuler » et « fermer ».

|||||
|-|-|-|-|
|![Icône de suppression de relation](../../extensibility/ux-guidelines/media/0405-07_deleterelationship.png "0405 -07 _DeleteRelationship")<br />Supprimer la relation|![Icône de suppression de colonne](../../extensibility/ux-guidelines/media/0405-08_deletecolumn.png "0405 -08 _DeleteColumn")<br />Supprimer la colonne|![Icône arrêter la requête](../../extensibility/ux-guidelines/media/0405-09_stopquery.png "0405 -09 _StopQuery")<br />Arrêter la requête|![Icône connexion hors connexion](../../extensibility/ux-guidelines/media/0405-10_connectionoffline.png "0405 -10 _ConnectionOffline")<br />Connexion hors connexion|

 Le bleu est appliqué aux modificateurs d’action neutres les plus couramment représentés sous forme de flèches, comme « ouvrir », « suivant », « précédent », « importer » et « exporter ».

|||||
|-|-|-|-|
|![Icône atteindre le champ](../../extensibility/ux-guidelines/media/0405-11_gotofield.png "0405 -11 _GoToField")<br />Atteindre le champ|![Icône d’archivage&#45;par lot](../../extensibility/ux-guidelines/media/0405-12_batchedcheckin.png "0405 12 _BatchedCheckIn")<br />Archivage par lot|![Icône de l’éditeur d’adresses](../../extensibility/ux-guidelines/media/0405-13_addresseditor.png "0405 -13 _AddressEditor")<br />Éditeur d’adresses|![Icône de l’éditeur d’associations](../../extensibility/ux-guidelines/media/0405-14_associationeditor.png "0405 -14 _AssociationEditor")<br />Éditeur d’associations|

 Dark Gold est principalement utilisé pour le modificateur « new ».

|||||
|-|-|-|-|
|![Icône nouveau projet](../../extensibility/ux-guidelines/media/0405-15_newproject.png "0405-15.0 _NewProject")<br />Nouveau projet|![Icône créer un graphique](../../extensibility/ux-guidelines/media/0405-16_createnewgraph.png "0405-16 _CreateNewGraph")<br />Créer un graphique|![Icône de nouveau test unitaire](../../extensibility/ux-guidelines/media/0405-17_newunittest.png "0405 -17 _NewUnitTest")<br />Nouveau test unitaire|![Icône de nouvel élément de liste](../../extensibility/ux-guidelines/media/0405-18_newlistitem.png "0405 -18 _NewListItem")<br />Nouvel élément de liste|

#### <a name="special-cases"></a>Cas particuliers
 Dans certains cas, un modificateur d’action coloré peut être utilisé indépendamment comme icône autonome. La couleur utilisée pour l’icône reflète les actions auxquelles l’icône est associée. Cette utilisation est limitée à un petit sous-ensemble d’icônes, notamment :

||||||
|-|-|-|-|-|
|![Icône d’exécution](../../extensibility/ux-guidelines/media/0405-03_actionmodifierrun.png "0405 -03 _ActionModifierRun")<br />Exécuter|![Icône arrêter](../../extensibility/ux-guidelines/media/0405-19_stop.png "0405 -19 _Stop")<br />Arrêter|![Icône Supprimer](../../extensibility/ux-guidelines/media/0405-20_delete.png "0405 -20 _Delete")<br />Supprimer|![Icône Enregistrer](../../extensibility/ux-guidelines/media/0405-21_save.png "0405 -21 _Save")<br />Enregistrer|![Icône naviguer vers l’arrière](../../extensibility/ux-guidelines/media/0405-22_navigateback.png "0405 -22 _NavigateBack")<br />Naviguer vers l’arrière|

### <a name="code-hierarchy-palette"></a>Palette de la hiérarchie du code

#### <a name="folder"></a>Dossier

|Utilisation|Name|Valeur (tous les thèmes)|Echantillon|Exemple|
|-----------|----------|--------------------------|------------|-------------|
|Contenus|Dossier|DCB67A/220 182 122|![Échantillon DCB67A](../../extensibility/ux-guidelines/media/0405_dcb67a.png "0405_DCB67A")|![Icône de couleur de dossier](../../extensibility/ux-guidelines/media/0405-23_foldercolor.png "0405 -23 _FolderColor")|

#### <a name="visual-studio-languages"></a>Langages Visual Studio
 Chacun des langages ou plateformes courants disponibles dans Visual Studio est associé à une couleur. Ces couleurs sont utilisées sur l’icône de base, ou sur les modificateurs de langue qui s’affichent dans le coin supérieur droit d’une icône composée.

|Utilisation|Name|Valeur (tous les thèmes)|Echantillon|
|-----------|----------|--------------------------|------------|
|ASP, HTML, WPF|HTML HTML WPF Blue|0095D7/0149 215|![Échantillon 0095D7](../../extensibility/ux-guidelines/media/0405_0096d7.png "0405_0096D7")|
|C++|RPC violet|9B4F96/155, 79150|![Échantillon 9B4F96](../../extensibility/ux-guidelines/media/0405_9b4f96.png "0405_9B4F96")|
|C#|Vert CS (action VS verte)|388A34/56138, 52|![Échantillon 388A34](../../extensibility/ux-guidelines/media/0405_388a34.png "0405_388A34")|
|CSS|Rouge CSS|BD1E2D/189, 30, 45|![Échantillon BD1E2D](../../extensibility/ux-guidelines/media/0405_bd1e2d.png "0405_BD1E2D")|
|F#|FS violet|672878/103, 40120|![Échantillon 672878](../../extensibility/ux-guidelines/media/0405_672878.png "0405_672878")|
|JavaScript|JS orange|F16421/241100, 33|![Échantillon F16421](../../extensibility/ux-guidelines/media/0405_f16421.png "0405_F16421")|
|VB|Bleu VB (VS action bleue)|00539C/0, 83156|![Échantillon 00539C](../../extensibility/ux-guidelines/media/0405_00539c.png "0405_00539C")|
|TypeScript|TS orange|E04C06/224, 76, 6|![Échantillon E04C06](../../extensibility/ux-guidelines/media/0405_e04c06.png "0405_E04C06")|
|Python|Vert PY|879636/135150, 54|![Échantillon 879636](../../extensibility/ux-guidelines/media/0405_879636.png "0405_879636")|

##### <a name="examples-of-icons-with-language-modifiers"></a>Exemples d’icônes avec modificateurs de langage

|||||||
|-|-|-|-|-|-|
|![Icône Visual Basic](../../extensibility/ux-guidelines/media/0405-25_vb.png "0405 -25 _VB")<br />VB|![Icône&#35; C](../../extensibility/ux-guidelines/media/0405-26_csharp.png "0405 -26 _CSharp")<br />C#|![Icône&#43; &#43; C](../../extensibility/ux-guidelines/media/0405-27_cplusplus.png "0405 -27 _CPlusPlus")<br />C++|![Icône&#35; F](../../extensibility/ux-guidelines/media/0405-28_fsharp.png "0405 28 _FSharp")<br />F#|![Icône JavaScript](../../extensibility/ux-guidelines/media/0405-29_javascript.png "0405 -29 _JavaScript")<br />JavaScript|![Icône python](../../extensibility/ux-guidelines/media/0405-30_python.png "0405 -30 _Python")<br />Python|
|![Icône HTML](../../extensibility/ux-guidelines/media/0405-31_html.png "0405 -31 _HTML")<br />HTML|![Icône WPF](../../extensibility/ux-guidelines/media/0405-32_wpf.png "0405 -32 _WPF")<br />WPF|![Icône ASP](../../extensibility/ux-guidelines/media/0405-33_asp.png "0405 -33 _ASP")<br />ASP|![Icône CSS](../../extensibility/ux-guidelines/media/0405-34_css.png "0405 -34 _CSS")<br />CSS|![Icône de machine à écrire](../../extensibility/ux-guidelines/media/0405-35_typescript.png "0405 -35 _TypeScript")<br />TypeScript||

#### <a name="intellisense"></a>IntelliSense
 Les icônes IntelliSense utilisent une palette de couleurs exclusives. Ces couleurs permettent aux utilisateurs de faire rapidement la distinction entre les différents éléments de la liste contextuelle IntelliSense.

|Utilisation|Name|Valeur (tous les thèmes)|Echantillon|
|-----------|----------|--------------------------|------------|
|Classe, événement|Action VS orange|C27D1A/194125, 26|![Échantillon C27D1A](../../extensibility/ux-guidelines/media/0405_c27d1a.png "0405_C27D1A")|
|Méthode d’extension, méthode, module, délégué|VS action Violette|652D90/101, 45144|![Échantillon 652D90](../../extensibility/ux-guidelines/media/0405_652d90.png "0405_652D90")|
|Champ, élément enum, macro, structure, type valeur d’Union, opérateur, interface|Bleu de l’action VS|00539C/0, 83156|![Échantillon 00539C](../../extensibility/ux-guidelines/media/0405_00539c.png "0405_00539C")|
|Objet|CONTRE-action en vert|388A34/56138, 52|![Échantillon 388A34](../../extensibility/ux-guidelines/media/0405_388a34.png "0405_388A34")|
|Constante, exception, élément enum, mappage, élément de mappage, espace de noms, modèle, définition de type|Arrière-plan (VS BG)|424242/66, 66, 66|![Échantillon 424242](../../extensibility/ux-guidelines/media/0405_424242.png "0405_424242")|

##### <a name="examples-of-intellisense-icons"></a>Exemples d’icônes IntelliSense

||||||
|-|-|-|-|-|
|![Icône de classe IntelliSense](../../extensibility/ux-guidelines/media/0405-36_intellisenseclass.png "0405 -36 _IntelliSenseClass")<br />Class|![Icône d’événement privé IntelliSense](../../extensibility/ux-guidelines/media/0405-37_intellisenseprivateevent.png "0405 -37 _IntelliSensePrivateEvent")<br />Événement privé|![Icône de délégué IntelliSense](../../extensibility/ux-guidelines/media/0405-38_intellisensedelegate.png "0405 -38 _IntelliSenseDelegate")<br />délégué|![Icône Friend de la méthode IntelliSense](../../extensibility/ux-guidelines/media/0405-39_intellisensemethodfriend.png "0405 -39 _IntelliSenseMethodFriend")<br />Méthode Friend|![Icône de champ](../../extensibility/ux-guidelines/media/0405-40_field.png "0405 -40 _Field")<br />Champ|
|![Icône d’élément d’enum protégé IntelliSense](../../extensibility/ux-guidelines/media/0405-41_intellisenseprotectedenumitem.png "0405-41 _IntelliSenseProtectedEnumItem")<br />Élément d’énumération protégé|![Icône d’objet IntelliSense](../../extensibility/ux-guidelines/media/0405-42_intellisenseobject.png "0405 -42 _IntelliSenseObject")<br />Objet|![Icône de modèle IntelliSense](../../extensibility/ux-guidelines/media/0405-43_intellisensetemplate.png "0405 -43 _IntelliSenseTemplate")<br />Modèle|![Icône de raccourci d’exception IntelliSense](../../extensibility/ux-guidelines/media/0405-44_intellisenseexceptionshortcut.png "0405 -44 _IntelliSenseExceptionShortcut")<br />Raccourci d’exception||

### <a name="notifications"></a>Notifications
 Les notifications dans Visual Studio sont utilisées pour indiquer l’État. La palette de notifications utilise les quatre couleurs suivantes, ainsi que les options de remplissage de premier plan noir ou blanc, pour définir des notifications avec les niveaux d’état suivants.

|Utilisation|Name|Valeur (tous les thèmes)|Echantillon|
|-----------|----------|--------------------------|------------|
|État : neutre|Bleu de notification (VS Blue)|1BA1E2/27 161 226|![Échantillon 1BA1E2](../../extensibility/ux-guidelines/media/0405_1ba1e2.png "0405_1BA1E2")|
|État : positif|Vert de notification (VS vert)|339933/51153, 51|![Échantillon 339933](../../extensibility/ux-guidelines/media/0405_339933.png "0405_339933")|
|État : négatif|Notification rouge (VS Red)|E51400/229, 20, 0|![Échantillon E51400](../../extensibility/ux-guidelines/media/0405_e51400.png "0405_E51400")|
|État : AVERTISSEMENT|Notification jaune (VS orange)|FFCC00/255204, 0|![Échantillon FFCC00](../../extensibility/ux-guidelines/media/0405_ffcc00.png "0405_FFCC00")|
|Remplissage au premier plan|Noir sur les notifications (noir)|000000/0, 0, 0|![Nuance &#35;000000](../../extensibility/ux-guidelines/media/0405_000000.png "0405_000000")|
|Remplissage au premier plan|Blanc de notification (blanc)|FFFFFF/255 255 255|![Nuance FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|

#### <a name="examples-of-notification-icons"></a>Exemples d’icônes de notification

|||||
|-|-|-|-|
|![Icône d’alerte](../../extensibility/ux-guidelines/media/0405-45_alert.png "0405 -45 _Alert")<br />Alerte|![Icône d’avertissement](../../extensibility/ux-guidelines/media/0405-48_warning.png "0405 -48 _Warning")<br />Warning|![Icône terminer](../../extensibility/ux-guidelines/media/0405-46_complete.png "0405 -46 _Complete")<br />Terminé|![Icône arrêter](../../extensibility/ux-guidelines/media/0405-47_stop.png "0405 -47 _Stop")<br />Arrêter|

### <a name="visual-studio-online"></a>Visual Studio Online
 En général, Visual Studio Online est constitué de fonctionnalités hébergées dans un navigateur. La couleur varie dans différents environnements, mais le style reste le même.

|Regrouper|Utilisation|Name|Valeur (tous les thèmes)|Echantillon|
|-----------|-----------|----------|--------------------------|------------|
|TFS|Présentation|TFSO BG|656565/101, 101, 101|![Échantillon 656565](../../extensibility/ux-guidelines/media/0405_656565.png "0405_656565")|
|TFS|Contour|TFSO|FFFFFF/255, 255, 255|![Nuance FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|
|Napa|Présentation|ajourée|FFFFFF/255, 255, 255|![Nuance FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|
|Monaco|Présentation|ajourée|FFFFFF/255, 255, 255|![Nuance FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|
|F12|Présentation|ajourée|FFFFFF/255, 255, 255|![Nuance FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|
|F12|Normale|F12 Grey_Primary|555555/85, 85, 85|![Échantillon 555555](../../extensibility/ux-guidelines/media/0405_555555.png "0405_555555")|
|F12|Pointage|F12 Blue_Hover|2279BF/34 121 191|![Échantillon 2279BF](../../extensibility/ux-guidelines/media/0405_2279bf.png "0405_2279BF")|
|F12|Disabled|F12 LtGrey_Disabled|ABABAC/171 171 172|![Échantillon ABABAC](../../extensibility/ux-guidelines/media/0405_ababac.png "0405_ABABAC")|
|F12|Arrière-plan de survol|BG survol|D9EBF7/217 235 247|![Échantillon D9EBF7](../../extensibility/ux-guidelines/media/0405_d9ebf7.png "0405_D9EBF7")|
|F12|Arrière-plan enfoncé|A appuyé sur BG|B2D7F0/178 215 240|![Échantillon B2D7F0](../../extensibility/ux-guidelines/media/0405_b2d7f0.png "0405_B2D7F0")|
|F12|Contour|DIFFÉRENCES PAR RAPPORT À|F6F6F6/246 246 246|![Échantillon F6F6F6](../../extensibility/ux-guidelines/media/0405_f6f6f6.png "0405_F6F6F6")|
|F12|Informations|Informations|00BCF2/0188 242|![Échantillon 00BCF2](../../extensibility/ux-guidelines/media/0405_00bcf2.png "0405_00BCF2")|
|F12|Warning|Warning|F28300/242131, 0|![Échantillon F28300](../../extensibility/ux-guidelines/media/0405_f28300.png "0405_F28300")|
|F12|Erreur/négatif|Error_Negative|E81123/232, 17, 35|![Échantillon E81123](../../extensibility/ux-guidelines/media/0405_e81123.png "0405_E81123")|
|F12|Début/positif|Start_Positive|009E49/0158, 73|![Échantillon 009E49](../../extensibility/ux-guidelines/media/0405_009e49.png "0405_009E49")|
|F12|Type d’arrêt|Type d’arrêt|9B4F96/155, 79150|![Échantillon 9B4F96](../../extensibility/ux-guidelines/media/0405_9b4f96.png "0405_9B4F96")|
|F12|Marque d’événement|Marque d’événement|A51F00/165, 31, 0|![Échantillon A51F00](../../extensibility/ux-guidelines/media/0405_a51f00.png "0405_A51F00")|
|F12|Marque utilisateur|Marque utilisateur|F16220/241, 98, 32|![Échantillon F16220](../../extensibility/ux-guidelines/media/0405_f16220.png "0405_F16220")|

#### <a name="examples-of-visual-studio-online-icons"></a>Exemples d’icônes Visual Studio Online

|TFS en ligne||||
|----------------|-|-|-|
|![Icône équipe TFS Online](../../extensibility/ux-guidelines/media/0405-49_tfsonlineteam.png "0405 -49 _TFSOnlineTeam")<br />Équipe en ligne|![Icône informations TFS](../../extensibility/ux-guidelines/media/0405-50_tfsinformation.png "0405-50 _TFSInformation")<br />Informations|![Icône de l’historique TFS](../../extensibility/ux-guidelines/media/0405-51_tfshistory.png "0405 -51 _TFSHistory")<br />Historique|![Icône de branche TFS](../../extensibility/ux-guidelines/media/0405-52_tfsbranch.png "0405 -52 _TFSBranch")<br />Créer une branche|

|Napa||||
|----------|-|-|-|
|![Icône de contenu Napa](../../extensibility/ux-guidelines/media/0405-53_napacontent.png "0405 -53 _NapaContent")<br />Contenu|![Icône de Napa Office mail](../../extensibility/ux-guidelines/media/0405-54_napaofficemail.png "0405 -54 _NapaOfficeMail")<br />Messagerie Office|![Icône SharePoint de Napa](../../extensibility/ux-guidelines/media/0405-55_napasharepoint.png "0405 -55 _NapaSharePoint")<br />SharePoint|![Icône du volet de tâches Napa](../../extensibility/ux-guidelines/media/0405-56_napataskpane.png "0405 -56 _NapaTaskPane")<br />Volet des tâches|

|Monaco||||
|------------|-|-|-|
|![Icône de fichiers Monaco](../../extensibility/ux-guidelines/media/0405-57_monacofiles.png "0405 -57 _MonacoFiles")<br />Fichiers|![Icône de l’git de Monaco](../../extensibility/ux-guidelines/media/0405-58_monacogit.png "0405 -58 _MonacoGit")<br />Git|![Icône de recherche de Monaco](../../extensibility/ux-guidelines/media/0405-59_monacosearch.png "0405 -59 _MonacoSearch")<br />Rechercher|![Icône de texte Monaco](../../extensibility/ux-guidelines/media/0405-60_monacotext.png "0405 -60 _MonacoText")<br />Texte|

|F12|||
|---------|-|-|
|![Icône de code F12](../../extensibility/ux-guidelines/media/0405-61_f12prettycode.png "0405 -61 _F12PrettyCode")<br />Code Pretty|![Icône d’avertissement F12](../../extensibility/ux-guidelines/media/0405-62_f12warning.png "0405 -62 _F12Warning")<br />Warning|![Icône d’émulation F12](../../extensibility/ux-guidelines/media/0405-63_f12emulate.png "0405 -63 _F12Emulate")<br />Émuler|