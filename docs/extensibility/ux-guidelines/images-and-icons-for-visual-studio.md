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
ms.openlocfilehash: 0ba4a5c52bf972236914c06ec9672653fbde9cea
ms.sourcegitcommit: 748d9cd7328a30f8c80ce42198a94a4b5e869f26
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67891054"
---
# <a name="images-and-icons-for-visual-studio"></a>Images et icônes pour Visual Studio
## <a name="BKMK_ImageUseInVisualStudio"></a> Utilisation d’image dans Visual Studio
 Avant de créer une illustration, envisagez de rendre l’utilisation des images de 1 000 dans le [bibliothèque d’images Visual Studio](http://www.microsoft.com/en-my/download/details.aspx?id=35825).

### <a name="types-of-images"></a>Types d’images

- **Icônes**. Petites images qui apparaissent dans les commandes, les hiérarchies, les modèles et ainsi de suite. La taille d’icône par défaut utilisée dans Visual Studio est un fichier PNG 16 x 16. Icônes générés automatiquement par le service d’images génèrent au format XAML pour la prise en charge HDPI.

    > [!NOTE]
    > Tandis que les images sont utilisées dans le système de menus, vous ne devez pas créer une icône pour chaque commande. Consultez [Menus et commandes de Visual Studio](../../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md) pour voir si votre commande doit obtenir une icône.

- **Miniatures.** Images utilisées dans la zone d’aperçu d’une boîte de dialogue, telles que la boîte de dialogue Nouveau projet.

- **Images de la boîte de dialogue.** Images qui apparaissent dans les boîtes de dialogue ou des Assistants, soit en tant que graphiques descriptif ou des indicateurs de message. Utilisez rarement et uniquement lorsque cela est nécessaire pour illustrer un concept difficile ou l’attention de l’utilisateur (avertissement d’alerte,).

- **Images animées.** Utilisé dans les indicateurs de progression, les barres d’état et les boîtes de dialogue d’opération.

- **Curseurs.** Utilisé pour indiquer si une opération est autorisée à l’aide de la souris, où un objet peuvent être supprimées et ainsi de suite.

## <a name="BKMK_IconDesign"></a> Conception de l’icône

### <a name="overview"></a>Présentation
 Visual Studio utilise des icônes modernes, qui ont geometry propre et 50/50 solde est positif/négatif (clair/sombre) et utilisent des métaphores directs et compréhensibles. Conception de l’icône cruciales pointe se concentrent autour de plus de clarté, de simplification et de contexte.

- **Plus de clarté :** vous concentrer sur la métaphore core qui donne une icône sa signification et la personnalité.

- **Simplification :** réduire l’icône à sa signification core - obtenir le thème entre avec simplement l’ou les éléments nécessaires et sans fioritures.

- **Contexte :** prendre en compte tous les aspects du rôle d’une icône au cours du développement de concept, ce qui est essentiel lorsque vous décidez quels éléments constituent la métaphore du cœur de l’icône.

  Avec des icônes, il existe un nombre de points de conception afin d’éviter :

- N’utilisez pas les icônes qui signifient l’existence des éléments d’interface utilisateur, sauf lorsque cela est approprié. Choisissez une approche plus abstraite ou symbolique lorsque l’élément d’interface utilisateur est courantes, évidente, ni unique.

- N’abusez éléments communs tels que des documents, des dossiers, des flèches et la Loupe. Utilisez ces éléments uniquement lorsqu’il est essentiel de la signification de l’icône. Par exemple, la Loupe droite doit indiquer seulement la recherche, rechercher et trouver.

- Bien que certains éléments d’icône héritée privilégie l’utilisation de la perspective, ne pas créer de nouvelles icônes avec le point de vue, sauf si l’élément manque de clarté sans qu’il.

- Ne récolter le plus trop d’informations dans une icône. Une image simple qui peut être facilement reconnue ou classée comme un symbole reconnaissable est beaucoup plus utile que d’une image trop complexe. Une icône ne peut pas dit pas tout.

### <a name="icon-creation"></a>Création de l’icône

#### <a name="concept-development"></a>Développement de concept
 Visual Studio a, au sein de son interface utilisateur, un large éventail de types d’icônes. Étudiez attentivement le type d’icône pendant le développement. N’utilisez pas les objets de l’interface utilisateur vous semble abscons ou rares pour vos éléments de l’icône. Choisir le lien symbolique dans ces cas, comme avec l’icône de balise active. Notez que la signification de la balise abstraite sur la gauche est la plus évidente que la version de vagues, interface utilisateur basée sur la droite :

|||
|-|-|
|**Utilisation correcte des images symbolique**|**Utilisation incorrecte de l’imagerie symbolique**|
|![Icône de balise active correcte](../../extensibility/ux-guidelines/media/0404-01_smarttagcorrect.png "0404-01_SmartTagCorrect")|![Icône de balise active incorrecte](../../extensibility/ux-guidelines/media/0404-02_smarttagincorrect.png "0404-02_SmartTagIncorrect")|

 Il existe des instances dans lequel les éléments d’interface utilisateur standards, facilement reconnaissables fonctionnent bien pour les icônes. Ajout de que fenêtre est un exemple :

|||
|-|-|
|**Élément d’interface utilisateur correct dans une icône**|**Élément d’interface utilisateur incorrect dans une icône**|
|![Icône d’ajout de fenêtre correcte](../../extensibility/ux-guidelines/media/0404-03_addwindowcorrect.png "0404-03_AddWindowCorrect")|![Icône d’ajout de fenêtre incorrecte](../../extensibility/ux-guidelines/media/0404-04_addwindowincorrect.png "0404-04_AddWindowIncorrect")|

 N’utilisez pas un document comme élément de base, sauf si elle est essentielle pour la signification de l’icône. Sans le document élément sur Ajouter un Document (voir ci-dessous) la signification est perdue, tandis qu’avec l’actualisation de l’élément de document n’est pas nécessaire communiquer la signification.

|||
|-|-|
|**Utilisation correcte de l’icône de document**|**Utilisation incorrecte de l’icône de document**|
|![Icône de Document correcte](../../extensibility/ux-guidelines/media/0404-05_documenticoncorrect.png "0404-05_DocumentIconCorrect")|![Icône de Document incorrecte](../../extensibility/ux-guidelines/media/0404-06_documenticonincorrect.png "0404-06_DocumentIconIncorrect")|

 Le concept de « afficher » doit être représenté par l’icône qui illustre le mieux ce qui est affiché, par exemple comme dans l’exemple d’afficher tous les fichiers. Une métaphore de filtre peut être utilisée pour indiquer le concept de « view », si nécessaire, comme avec l’exemple d’affichage des ressources.

|||
|-|-|
|**"Show"**|**« Vue »**|
|![Afficher l’icône de](../../extensibility/ux-guidelines/media/0404-07_show.png "0404-07_Show")|![Icône d’affichage](../../extensibility/ux-guidelines/media/0404-08_view.png "0404-08_View")|

 La droite agrandissement icône de loupe doit représenter uniquement rechercher, rechercher et Parcourir. La variante de gauche avec le signe plus ou moins doit représenter uniquement le zoom avant / zoom arrière.

|||
|-|-|
|**« Recherche »**|**"Zoom"**|
|![Icône de recherche](../../extensibility/ux-guidelines/media/0404-09_search.png "0404-09_Search")|![Icône de zoom](../../extensibility/ux-guidelines/media/0404-10_zoom.png "0404-10_Zoom")|

 Dans les vues de l’arborescence, n’utilisez pas l’icône de dossier et un modificateur. Lorsqu’il est disponible, utilisez uniquement le modificateur.

|||
|-|-|
|**Icônes de vue d’arborescence correcte**|**Icônes de vue d’arborescence incorrecte**|
|![Icône d’arborescence correcte &#40;1&#41;](../../extensibility/ux-guidelines/media/0404-11_treeviewcorrect1.png "0404-11_TreeViewCorrect1") ![icône d’arborescence correcte &#40;2&#41;](../../extensibility/ux-guidelines/media/0404-12_treeviewcorrect2.png "0404-12_TreeViewCorrect2")|![Icône d’arborescence incorrecte &#40;1&#41;](../../extensibility/ux-guidelines/media/0404-13_treeviewincorrect1.png "0404-13_TreeViewIncorrect1") ![icône d’arborescence incorrecte &#40;2&#41;](../../extensibility/ux-guidelines/media/0404-14_treeviewincorrect2.png "0404-14_ TreeViewIncorrect2")|

### <a name="style-details"></a>Détails de style

#### <a name="layout"></a>Mise en page
 Éléments de la pile comme indiqué pour les icônes 16 x 16 standard :

 ![Pile de disposition pour les icônes 16 x 16](../../extensibility/ux-guidelines/media/0404-15_layoutstack.png "0404-15_LayoutStack")<br />Pile de disposition pour les icônes 16x16

 Éléments de notification d’état sont mieux utilisés sous forme d’icônes d’autonome. Il existe des contextes, toutefois, dans laquelle une notification doit être empilée sur l’élément de base, comme avec l’icône de tâche terminée :

 ![Notifications autonome dans Visual Studio](../../extensibility/ux-guidelines/media/0404-16_standalonenotificationicons.png "0404-16_StandaloneNotificationIcons")<br />Icônes de notification autonome

 ![Icône de tâche terminée](../../extensibility/ux-guidelines/media/0404-17_taskcomplete.png "0404-17_TaskComplete")<br />Icône de tâche terminée

 Icônes de projet sont généralement des fichiers .ico qui contiennent plusieurs tailles. La plupart des icônes 16 x 16 contiennent les mêmes éléments. Les versions de 32 x 32 offrent plus de détails, y compris le type de projet, le cas échéant.

 ![Projet d’icônes dans Visual Studio](../../extensibility/ux-guidelines/media/0404-18_iconprojectthreesizes.png "0404-18_IconProjectThreeSizes")<br />Icônes de projet de bibliothèque de contrôles Windows VB, 16 x 16 et 32 x 32

 Centre une icône dans le cadre de ses pixels. Si tel n’est pas possible, alignez l’icône en haut et/ou à droite de l’image.

 ![Icône centrée dans le frame de pixels](../../extensibility/ux-guidelines/media/0404-19_iconcentered.png "0404-19_IconCentered")<br />Icône centrée dans le frame de pixels

 ![Icône aligné en haut à droite du frame de pixels](../../extensibility/ux-guidelines/media/0404-20_icontopright.png "0404-20_IconTopRight")<br />Icône alignée sur la partie supérieure droite du cadre

 ![Icône centrée et alignée en haut du frame de pixels](../../extensibility/ux-guidelines/media/0404-21_icontopalign.png "0404-21_IconTopAlign")<br />Icône centrée et alignée sur le haut du frame

 Pour atteindre idéale alignement et équilibre, évitez ne bloque les éléments de base de l’icône avec des glyphes d’action. Place le glyphe en haut à gauche de l’élément de base. Lorsque vous ajoutez un élément supplémentaire, envisagez l’alignement et le solde de l’icône.

|||
|-|-|
|**Solde et alignement correct**|**Solde et alignement incorrect**|
|![Corriger l’alignement et équilibre des icônes](../../extensibility/ux-guidelines/media/0404-22_alignbalancecorrect.png "0404-22_AlignBalanceCorrect")|![Équilibre des icônes incorrectes et l’alignement](../../extensibility/ux-guidelines/media/0404-23_alignbalanceincorrect.png "0404-23_AlignBalanceIncorrect")|

 Vérifiez la parité de taille pour les icônes qui partagent des éléments et sont utilisés dans les ensembles. Notez que dans l’association incorrecte, le cercle et flèche sont trop agrandis et ne correspondent pas.

|||
|-|-|
|**Parité de taille appropriée**|**Parité de taille incorrecte**|
|![Corriger la taille d’icône et la parité](../../extensibility/ux-guidelines/media/0404-24_sizeparitycorrect.png "0404-24_SizeParityCorrect")|![Taille des icônes incorrectes et la parité](../../extensibility/ux-guidelines/media/0404-25_sizeparityincorrect.png "0404-25_SizeParityIncorrect")|

 Utiliser la ligne cohérente et poids visual. Évaluer l’icône que vous développiez le comparatif entre autres icônes à l’aide d’une comparaison côte à côte. Utilisez la trame entière de 16 x 16, n’utilisez jamais 15 x 15 ou plus petits. Le rapport de (sombre-clair) négatif à positif doit être de 50/50.

|||
|-|-|
|**Rapport négatif-positif**|**Ratio de négatif à positif incorrect**|
|![Corriger une épaisseur visuelle pour les icônes &#40;1&#41;](../../extensibility/ux-guidelines/media/0404-26_visualweightcorrect1.png "0404-26_VisualWeightCorrect1")<br /><br /> ![Corriger une épaisseur visuelle pour les icônes &#40;2&#41;](../../extensibility/ux-guidelines/media/0404-27_visualweightcorrect2.png "0404-27_VisualWeightCorrect2")<br /><br /> ![Corriger une épaisseur visuelle pour les icônes &#40;3&#41;](../../extensibility/ux-guidelines/media/0404-28_visualweightcorrect3.png "0404-28_VisualWeightCorrect3")|![Épaisseur visuelle incorrecte pour les icônes](../../extensibility/ux-guidelines/media/0404-29_visualweightincorrect.png "0404-29_VisualWeightIncorrect")|

 Utiliser des formes simples, comparables et complémentaire angles pour générer vos éléments sans sacrifier l’intégrité de l’élément. Utiliser des angles de 45 ou 90° lorsque cela est possible.

 ![Corriger les angles des icônes](../../extensibility/ux-guidelines/media/0404-30_iconanglescorrect.png "0404-30_IconAnglesCorrect")

#### <a name="perspective"></a>Perspective
 Gardez à l’icône claire et compréhensible. Utilisez le point de vue et une source de lumière uniquement lorsque cela est nécessaire. Bien que l’utilisation de perspective sur les éléments de l’icône doit être évitée, certains éléments sont non reconnaissables sans lui. Dans ce cas, une perspective stylisée communique la clarté de l’élément.

 ![perspective à 3 points](../../extensibility/ux-guidelines/media/0404-31_3pointperspective.png "0404-31_3PointPerspective")<br />Perspective à 3 points

 ![perspective à 1 point](../../extensibility/ux-guidelines/media/0404-32_1pointperspective.png "0404-32_1PointPerspective")<br />Perspective à 1 point

 La plupart des éléments doit être accessible sur ou dirigé vers la droite :

 ![Icônes avec angle droit](../../extensibility/ux-guidelines/media/0404-33_angledright.png "0404-33_AngledRight")

 Utiliser des sources de lumière uniquement lorsque vous ajoutez plus de clarté nécessaire à un objet.

|||
|-|-|
|**Source de lumière correcte**|**Source de lumière incorrecte**|
|![Corriger les sources de lumière pour les icônes](../../extensibility/ux-guidelines/media/0404-34_lightsourcescorrect.png "0404-34_LightSourcesCorrect")|![Les sources de lumière incorrectes pour les icônes](../../extensibility/ux-guidelines/media/0404-35_lightsourcesincorrect.png "0404-35_LightSourcesIncorrect")|

 Utilisez les contours uniquement pour améliorer la lisibilité ou pour mieux communiquer la métaphore. Solde négatif positif (sombre-clair) doit être 50/50.

|||
|-|-|
|**Utilisation correcte des contours**|**Utilisation incorrecte de contours**|
|![Corriger les contours](../../extensibility/ux-guidelines/media/0404-36_outlinescorrect.png "0404-36_OutlinesCorrect")|![Plans incorrects](../../extensibility/ux-guidelines/media/0404-37_outlinesincorrect.png "0404-37_OutlinesIncorrect")|

#### <a name="icon-types"></a>Types d’icônes
 **Shell et de barre de commandes** icônes se composent de pas plus de trois des éléments suivants : une base, un seul modificateur, une action ou un état.

 ![Exemples de shell et barre d’icônes de commandes](../../extensibility/ux-guidelines/media/0404-38_shellicons.png "0404-38_ShellIcons")<br />Exemples de shell et barre d’icônes de commandes

 **Barre de commandes de fenêtre outil** icônes se composent de pas plus de trois des éléments suivants : une base, un seul modificateur, une action ou un état.

 ![Exemples de fenêtre outil commande barre d’icônes](../../extensibility/ux-guidelines/media/0404-39_toolwindowcommandbaricons.png "0404-39_ToolWindowCommandBarIcons")<br />Exemples d’icônes de barre de commandes de fenêtre outil

 **Désambiguïsateur de vue d’arborescence** icônes se composent de pas plus de trois des éléments suivants : une base, un seul modificateur, une action ou un état.

 ![Exemples d’arborescence permet d’afficher les icônes de désambiguïsateur](../../extensibility/ux-guidelines/media/0404-40_treeviewicons.png "0404-40_TreeViewIcons")<br />Exemples d’arborescence permet d’afficher les icônes de désambiguïsateur

 **Taxonomie de valeur basée sur l’état** icônes existent dans les états suivants : actif, actif désactivé et désactivé inactive.

 ![Exemples d’icônes de taxonomie basée sur l’état de la valeur](../../extensibility/ux-guidelines/media/0404-41_statebasedtaxonomy.png "0404-41_StateBasedTaxonomy")<br />Exemples d’icônes de taxonomie basée sur l’état de valeur

 **IntelliSense** icônes se composent de pas plus de trois des éléments suivants : une base, un seul modificateur et un état.

 ![Exemples d’icônes d’IntelliSense](../../extensibility/ux-guidelines/media/0404-42_intellisenseicons.png "0404-42_IntelliSenseIcons")<br />Exemples d’icônes d’IntelliSense

 **Petit (16 x 16) projet** icônes doivent avoir pas plus de deux éléments : une base et un seul modificateur.

 ![Exemples de petit (16 x 16) des icônes de projet](../../extensibility/ux-guidelines/media/0404-43_16x16project1.png "0404-43_16x16Project1") ![icône de projet 16 x 16 &#40;2&#41;](../../extensibility/ux-guidelines/media/0404-44_16x16project2.png "0404-44_16x16Project2") ![icône de projet 16 x 16 &#40;3&#41;](../../extensibility/ux-guidelines/media/0404-45_16x16project3.png "0404-45_16x16Project3")<br />Exemples de petites icônes de projet (16 x 16)

 **Grand projet (32 x 32)** icônes se composent de pas plus de quatre des éléments suivants : une base, un ou deux modificateurs et un langage de superposition.

 ![Exemples de grande taille (32 x 32) des icônes de projet](../../extensibility/ux-guidelines/media/0404-46_32x32project.png "0404-46_32x32Project")<br />Exemples de grandes icônes de projet (32 x 32)

### <a name="production-details"></a>Détails de la production
 Tous les nouveaux éléments d’interface utilisateur doivent être créés à l’aide de Windows Presentation Foundation (WPF) et toutes les nouvelles icônes pour WPF doivent être au format PNG de 32 bits. Le fichier PNG sur 24 bits est un format hérité qui ne prend pas en charge la transparence et est donc pas recommandé pour les icônes.

 Enregistrer la résolution de 96 PPP.

#### <a name="file-types"></a>Types de fichiers

- **PNG 32 bits :** le format par défaut pour les icônes. Un format de fichier de la compression sans perte de données qui peut stocker une image raster unique (en pixels). fichiers PNG 32 bits prennent en charge la transparence de canal alpha, la correction gamma et l’entrelacement.

- **BMP de 32 bits :** pour les contrôles non-WPF. Également appelée XP ou des couleurs, 32 bits BMP est un format d’image de RVB/A, une image de couleurs vraies avec une transparence de canal alpha. Le canal alpha est une couche de transparence désignée dans Adobe Photoshop qui est ensuite enregistré dans l’image bitmap en tant qu’un supplémentaire (quatrième) canal de couleur. Un arrière-plan noir est ajouté lors de la production d’une illustration à tous les fichiers BMP de 32 bits pour fournir une indication visuelle rapide sur la profondeur de couleur. Cet arrière-plan noir représente la zone à être masquée dans l’interface utilisateur.

- **32 bits ICO :** pour les icônes de projet et ajouter un élément. Tous les fichiers ICO sont des couleurs de 32 bits avec transparence de canal alpha (RVB/A). Étant donné que les fichiers ICO peuvent stocker plusieurs tailles et palettes de couleurs, icônes Vista sont souvent dans un format ICO contenant 16 x 16, 32 x 32, 48 x 48 et tailles d’image de 256 x 256. Pour afficher correctement dans l’Explorateur Windows, les fichiers ICO doivent être enregistré en détail des profondeurs de couleur sur 24 bits et 8 bits pour chaque taille de l’image.

- **XAML :** pour les surfaces de dessin et les ornements de Windows. Icônes XAML sont des fichiers d’image vectorielle qui prennent en charge la mise à l’échelle, rotation, classement et la transparence. Ils ne sont pas courants dans Visual Studio dès aujourd'hui, mais plus en plus répandus en raison de leur flexibilité.

- **SVG**

- **24 bits BMP :** pour la barre de commandes de Visual Studio. Un format d’image RVB couleurs vraies, 24 bits BMP est une convention d’icône qui crée une couche de transparence à l’aide de magenta (R = 255, G = 0, B = 255) comme clé de couleur pour une couche de transparence de la véritable révolution. Dans une image BMP 24 bits, toutes les surfaces magenta sont affichés à l’aide de la couleur d’arrière-plan.

- **24 bits GIF :** pour la barre de commandes de Visual Studio. Un true-couleur RVB format d’image qui prend en charge la transparence. Fichiers GIF sont souvent utilisés dans l’illustration de l’Assistant et les animations d’image GIF.

### <a name="icon-construction"></a>Construction d’icône
 La plus petite taille d’icône dans Visual Studio est 16 x 16. Le plus grand commun utilisation est 32 x 32. N’oubliez pas ne pas pour remplir la trame entière de 16 x 16, 24 x 24 ou 32 x 32 lors de la conception d’une icône. Construction de l’icône lisibles et uniforme est essentielle pour la reconnaissance de l’utilisateur. Respecter les points suivants lors de la génération des icônes.

- Icônes doivent être clairs, compréhensible et cohérente.

- Il est préférable d’utiliser les éléments de notification d’état sous forme d’icônes uniques et non à s’empilent les un élément de base d’icône. Dans certains contextes, l’interface utilisateur peut nécessiter l’élément d’état à être associé à un élément de base.

- Icônes de projet sont généralement .ico qui contiennent plusieurs tailles. Seules les icônes 16 x 16, 24 x 24 et 32 x 32 sont en cours de mise à jour. La plupart des icônes 16 x 16 et 24 x 24 contiendra les mêmes éléments. Les icônes de 32 x 32 contiennent plus de détails, y compris le type de langage de projet le cas échéant.

- Pour les icônes de 32 x 32, les éléments de base ont généralement une épaisseur de trait de 2 pixels. Une épaisseur de trait de 1 ou 2 pixels peut être utilisée pour les éléments de détail. Utilisez votre appréciation pour déterminer ce qui est plus adapté.

- Ayant au moins un espacement de 1 pixel entre les éléments de 16 x 16 et icônes de 24 x 24. Pour les icônes de 32 x 32, utilisez 2 pixels espacement entre les éléments et entre le modificateur et un élément de base.

  ![Élément espacement pour en taille réelle des icônes 16 x 16, 24 x 24 et 32 x 32](../../extensibility/ux-guidelines/media/0404-47_elementspacing.png "0404-47_ElementSpacing")<br />Espacement d’éléments pour les icônes en taille réelle de 16 x 16, 24 x 24 et 32 x 32

#### <a name="color-and-accessibility"></a>Couleur et l’accessibilité
 Les recommandations pour la conformité de Visual Studio nécessitent que toutes les icônes dans le produit passent les exigences d’accessibilité pour la couleur et de contraste. Ceci se fait via l’inversion de l’icône, et lors de la conception, vous devez être conscient qu’ils est inversés par programmation dans le produit.

 Pour plus d’informations sur l’utilisation de la couleur des icônes de Visual Studio, consultez [à l’aide de la couleur dans les images](../../extensibility/ux-guidelines/images-and-icons-for-visual-studio.md#BKMK_UsingColorInImages).

## <a name="BKMK_UsingColorInImages"></a> À l’aide de la couleur dans les images

### <a name="overview"></a>Présentation
 Icônes dans Visual Studio sont principalement monochromes. Couleur est réservée pour transmettre des informations spécifiques et jamais pour la décoration. Couleur est utilisée :

- pour indiquer une action

- pour avertir l’utilisateur à une notification d’état

- pour désigner l’affiliation de langage

- pour différencier les éléments dans IntelliSense

### <a name="accessibility"></a>Accessibilité
 Les recommandations pour la conformité de Visual Studio nécessitent que toutes les icônes cochée dans la passe de produit les exigences d’accessibilité pour la couleur et de contraste. Couleurs de la palette du langage visual ont été testées et répondre à ces exigences.

#### <a name="color-inversion-for-dark-themes"></a>Inversion des couleurs des thèmes foncées
 Pour que les icônes apparaissent avec le rapport de contraste approprié dans le thème foncé Visual Studio, une inversion est appliquée par programmation. Les couleurs dans ce guide ont été choisies en partie afin qu’ils inversent correctement. Limiter votre utilisation des couleurs à cette palette, ou vous obtiendrez des résultats imprévisibles lors de l’inversion est appliquée.

 ![Exemples d’icônes qui ont leurs couleurs inversées](../../extensibility/ux-guidelines/media/0405-01_darkthemeinversion.png "0405-01_DarkThemeInversion")<br />Exemples d’icônes qui ont leurs couleurs inversées

### <a name="base-palette"></a>Palette de base
 Toutes les icônes standards contiennent trois couleurs de base. Icônes ne contient aucun des dégradés ou des ombres portées, avec une ou deux exceptions pour les icônes de l’outil de 3D.

|Usage|Nom|Valeur (thème clair)|Échantillon|Exemple|
|-----------|----------|---------------------------|------------|-------------|
|Arrière-plan/sombre|VS BG|424242 / 66,66,66|![Échantillon 424242](../../extensibility/ux-guidelines/media/0405_424242.png "0405_424242")|![Exemple de palette de base](../../extensibility/ux-guidelines/media/0405-02_basepaletteexample.png "0405-02_BasePaletteExample")|
|Premier plan/légère|FG DE VS|F0EFF1 / 240,239,241|![Échantillon F0EFF1](../../extensibility/ux-guidelines/media/0405_f0eff1.png "0405_F0EFF1")||
|Contour|VS Out|F6F6F6 / 246,246,246|![Échantillon F6F6F6](../../extensibility/ux-guidelines/media/0405_f6f6f6.png "0405_F6F6F6")||

 Outre les couleurs de base, chaque icône peut contenir une seule couleur supplémentaire à partir de la palette étendue.

### <a name="extended-palette"></a>Palette étendue

#### <a name="action-modifiers"></a>Modificateurs de l’action
 Les quatre couleurs ci-dessous indiquent les types d’actions requises par les modificateurs de l’action :

|Usage|Nom|Valeur (tous les thèmes)|Échantillon|
|-----------|----------|--------------------------|------------|
|Positif|VS Action vert|388A34 / 56,138,52|![Échantillon 388 a 34](../../extensibility/ux-guidelines/media/0405_388a34.png "0405_388A34")|
|Négatif|VS Action rouge|A1260D / 161,38,13|![Échantillon A1260D](../../extensibility/ux-guidelines/media/0405_a1260d.png "0405_A1260D")|
|Neutral|VS Action bleu|00539C / 0,83,156|![Échantillon 00539c](../../extensibility/ux-guidelines/media/0405_00539c.png "0405_00539C")|
|Créer/nouveau|VS Action Orange|C27D1A / 194,156,26|![Échantillon C27D1A](../../extensibility/ux-guidelines/media/0405_c27d1a.png "0405_C27D1A")|

##### <a name="examples"></a>Exemples
 Vert est utilisé pour les modificateurs de l’action positif comme « Ajouter », « Run, » « Lecture » et « Valider ».

|||||
|-|-|-|-|
|![Icône d’exécution](../../extensibility/ux-guidelines/media/0405-03_actionmodifierrun.png "0405-03_ActionModifierRun")<br />Exécuter|![Icône exécuter la requête](../../extensibility/ux-guidelines/media/0405-04_executequery.png "0405-04_ExecuteQuery")<br />Exécuter la requête|![Toutes les étapes icône de lecture](../../extensibility/ux-guidelines/media/0405-05_playallsteps.png "0405-05_PlayAllSteps")<br />Lire toutes les étapes|![Icône Ajouter le contrôle](../../extensibility/ux-guidelines/media/0405-06_addcontrol.png "0405-06_AddControl")<br />Ajouter le contrôle|

 Rouge est utilisé pour les modificateurs action négatif comme « Delete », « Stop », « Annuler » et « Fermer ».

|||||
|-|-|-|-|
|![Icône Supprimer la relation](../../extensibility/ux-guidelines/media/0405-07_deleterelationship.png "0405-07_DeleteRelationship")<br />Supprimer la relation|![Icône Supprimer la colonne](../../extensibility/ux-guidelines/media/0405-08_deletecolumn.png "0405-08_DeleteColumn")<br />Supprimer la colonne|![Icône de requête d’arrêt](../../extensibility/ux-guidelines/media/0405-09_stopquery.png "0405-09_StopQuery")<br />Arrêter la requête|![Icône de connexion hors connexion](../../extensibility/ux-guidelines/media/0405-10_connectionoffline.png "0405-10_ConnectionOffline")<br />Connexion en mode hors connexion|

 Bleu est appliqué à une action neutre modificateurs plus souvent représentées par des flèches, comme « Ouvert, » « Suivant », « Précédent », « Importer » et « Exporter ».

|||||
|-|-|-|-|
|![Accédez à l’icône de champ](../../extensibility/ux-guidelines/media/0405-11_gotofield.png "0405-11_GoToField")<br />Accédez au champ|![Traités par lot de vérification&#45;dans icône](../../extensibility/ux-guidelines/media/0405-12_batchedcheckin.png "0405-12_BatchedCheckIn")<br />Archivage par lot|![Icône de l’éditeur adresse](../../extensibility/ux-guidelines/media/0405-13_addresseditor.png "0405-13_AddressEditor")<br />Éditeur d’adresse|![Icône de l’éditeur association](../../extensibility/ux-guidelines/media/0405-14_associationeditor.png "0405-14_AssociationEditor")<br />Éditeur d’associations|

 Or foncé est principalement utilisé pour le modificateur « Nouveau ».

|||||
|-|-|-|-|
|![Icône de nouveau projet](../../extensibility/ux-guidelines/media/0405-15_newproject.png "0405-15_NewProject")<br />Nouveau projet|![Créer la nouvelle icône de graphique](../../extensibility/ux-guidelines/media/0405-16_createnewgraph.png "0405-16_CreateNewGraph")<br />Créer un graphique|![Nouvelle icône de test unitaire](../../extensibility/ux-guidelines/media/0405-17_newunittest.png "0405-17_NewUnitTest")<br />Nouveau Test unitaire|![Icône de nouvelle liste](../../extensibility/ux-guidelines/media/0405-18_newlistitem.png "0405-18_NewListItem")<br />Nouvel élément de liste|

#### <a name="special-cases"></a>Cas particuliers
 Dans certains cas, un modificateur de couleur action peut servir indépendamment sous forme d’icône autonome. La couleur utilisée pour l’icône reflète les actions que l’icône est associée. Cette utilisation est limitée à un petit sous-ensemble des icônes, y compris :

||||||
|-|-|-|-|-|
|![Icône d’exécution](../../extensibility/ux-guidelines/media/0405-03_actionmodifierrun.png "0405-03_ActionModifierRun")<br />Exécuter|![Icône arrêter](../../extensibility/ux-guidelines/media/0405-19_stop.png "0405-19_Stop")<br />Arrêter|![Icône de suppression](../../extensibility/ux-guidelines/media/0405-20_delete.png "0405-20_Delete")<br />Supprimer|![Icône Enregistrer](../../extensibility/ux-guidelines/media/0405-21_save.png "0405-21_Save")<br />Enregistrer|![Accédez icône précédent](../../extensibility/ux-guidelines/media/0405-22_navigateback.png "0405-22_NavigateBack")<br />Naviguer vers l’arrière|

### <a name="code-hierarchy-palette"></a>Palette de hiérarchie de code

#### <a name="folder"></a>Dossier

|Usage|Nom|Valeur (tous les thèmes)|Échantillon|Exemple|
|-----------|----------|--------------------------|------------|-------------|
|Dossiers|Dossier|DCB67A / 220,182,122|![Échantillon DCB67A](../../extensibility/ux-guidelines/media/0405_dcb67a.png "0405_DCB67A")|![Icône de dossier de couleur](../../extensibility/ux-guidelines/media/0405-23_foldercolor.png "0405-23_FolderColor")|

#### <a name="visual-studio-languages"></a>Langages Visual Studio
 Chacun des langages ou plateformes disponibles dans Visual Studio courants a une couleur associée. Ces couleurs sont utilisées sur l’icône de base, ou sur les modificateurs de langage qui s’affichent dans le coin supérieur droit des icônes composées.

|Usage|Name|Valeur (tous les thèmes)|Échantillon|
|-----------|----------|--------------------------|------------|
|ASP, HTML, WPF|ASP HTML WPF bleu|0095D 7 / 0,149,215|![Échantillon 0095d7](../../extensibility/ux-guidelines/media/0405_0096d7.png "0405_0096D7")|
|C++|CPP violet|9B4F96 / 155,79,150|![Swatch 9B4F96](../../extensibility/ux-guidelines/media/0405_9b4f96.png "0405_9B4F96")|
|C#|CS vert (Green d’Action Visual Studio)|388A34 / 56,138,52|![Échantillon 388 a 34](../../extensibility/ux-guidelines/media/0405_388a34.png "0405_388A34")|
|CSS|CSS rouge|BD1E2D / 189,30,45|![Échantillon BD1E2D](../../extensibility/ux-guidelines/media/0405_bd1e2d.png "0405_BD1E2D")|
|F#|FS violet|672878 / 103,40,120|![Échantillon 672878](../../extensibility/ux-guidelines/media/0405_672878.png "0405_672878")|
|JavaScript|JS Orange|F16421 / 241,100,33|![Échantillon F16421](../../extensibility/ux-guidelines/media/0405_f16421.png "0405_F16421")|
|VB|VB Blue (bleu d’Action de Visual Studio)|00539C / 0,83,156|![Échantillon 00539c](../../extensibility/ux-guidelines/media/0405_00539c.png "0405_00539C")|
|TypeScript|TS Orange|E04C06 / 224,76,6|![Échantillon E04C06](../../extensibility/ux-guidelines/media/0405_e04c06.png "0405_E04C06")|
|Python|PY vert|879636 / 135,150,54|![Échantillon 879636](../../extensibility/ux-guidelines/media/0405_879636.png "0405_879636")|

##### <a name="examples-of-icons-with-language-modifiers"></a>Exemples d’icônes avec des modificateurs de langage

|||||||
|-|-|-|-|-|-|
|![Icône de Visual Basic](../../extensibility/ux-guidelines/media/0405-25_vb.png "0405-25_VB")<br />VB|![C&#35; icône](../../extensibility/ux-guidelines/media/0405-26_csharp.png "0405-26_CSharp")<br />C#|![C&#43; &#43; icône](../../extensibility/ux-guidelines/media/0405-27_cplusplus.png "0405-27_CPlusPlus")<br />C++|![F&#35; icône](../../extensibility/ux-guidelines/media/0405-28_fsharp.png "0405-28_FSharp")<br />F#|![Icône de JavaScript](../../extensibility/ux-guidelines/media/0405-29_javascript.png "0405-29_JavaScript")<br />JavaScript|![Icône Python](../../extensibility/ux-guidelines/media/0405-30_python.png "0405-30_Python")<br />Python|
|![Icône HTML](../../extensibility/ux-guidelines/media/0405-31_html.png "0405-31_HTML")<br />HTML|![Icône WPF](../../extensibility/ux-guidelines/media/0405-32_wpf.png "0405-32_WPF")<br />WPF|![Icône ASP](../../extensibility/ux-guidelines/media/0405-33_asp.png "0405-33_ASP")<br />ASP|![Icône CSS](../../extensibility/ux-guidelines/media/0405-34_css.png "0405-34_CSS")<br />CSS|![Icône de TypeScript](../../extensibility/ux-guidelines/media/0405-35_typescript.png "0405-35_TypeScript")<br />TypeScript||

#### <a name="intellisense"></a>IntelliSense
 Icônes IntelliSense utilisent une palette de couleurs exclusif. Ces couleurs sont utilisées pour aider les utilisateurs rapidement faire la distinction entre les différents éléments dans la liste de la fenêtre contextuelle IntelliSense.

|Usage|Nom|Valeur (tous les thèmes)|Échantillon|
|-----------|----------|--------------------------|------------|
|Classe, événement|VS Action Orange|C27D1A / 194,125,26|![Échantillon C27D1A](../../extensibility/ux-guidelines/media/0405_c27d1a.png "0405_C27D1A")|
|Méthode d’extension, méthode, Module, délégué|VS Action violet|652D 90 / 101,45,144|![Échantillon 652d90](../../extensibility/ux-guidelines/media/0405_652d90.png "0405_652D90")|
|Champ élément Enum, Macro, Structure, Union valeur Type, opérateur, Interface|VS Action bleu|00539C / 0,83,156|![Échantillon 00539c](../../extensibility/ux-guidelines/media/0405_00539c.png "0405_00539C")|
|Object|VS Action vert|388A34 / 56,138,52|![Échantillon 388 a 34](../../extensibility/ux-guidelines/media/0405_388a34.png "0405_388A34")|
|Constante, Exception, élément Enum, Map, élément de la carte, Namespace, modèle, définition de Type|En arrière-plan (BG Visual Studio)|424242 / 66,66,66|![Échantillon 424242](../../extensibility/ux-guidelines/media/0405_424242.png "0405_424242")|

##### <a name="examples-of-intellisense-icons"></a>Exemples d’icônes d’IntelliSense

||||||
|-|-|-|-|-|
|![Icône de classe IntelliSense](../../extensibility/ux-guidelines/media/0405-36_intellisenseclass.png "0405-36_IntelliSenseClass")<br />Classe|![Icône d’événement privé IntelliSense](../../extensibility/ux-guidelines/media/0405-37_intellisenseprivateevent.png "0405-37_IntelliSensePrivateEvent")<br />Événement de privé|![Icône de délégué IntelliSense](../../extensibility/ux-guidelines/media/0405-38_intellisensedelegate.png "0405-38_IntelliSenseDelegate")<br />délégué|![Icône friend de méthode IntelliSense](../../extensibility/ux-guidelines/media/0405-39_intellisensemethodfriend.png "0405-39_IntelliSenseMethodFriend")<br />Méthode Friend|![Icône de champ](../../extensibility/ux-guidelines/media/0405-40_field.png "0405-40_Field")<br />Champ|
|![Icône d’élément enum protégé par l’IntelliSense](../../extensibility/ux-guidelines/media/0405-41_intellisenseprotectedenumitem.png "0405-41_IntelliSenseProtectedEnumItem")<br />Élément Enum protégé|![Icône d’objet IntelliSense](../../extensibility/ux-guidelines/media/0405-42_intellisenseobject.png "0405-42_IntelliSenseObject")<br />Object|![Icône de modèle IntelliSense](../../extensibility/ux-guidelines/media/0405-43_intellisensetemplate.png "0405-43_IntelliSenseTemplate")<br />Modèle|![Icône de raccourci d’exception IntelliSense](../../extensibility/ux-guidelines/media/0405-44_intellisenseexceptionshortcut.png "0405-44_IntelliSenseExceptionShortcut")<br />Raccourci d’exception||

### <a name="notifications"></a>Notifications
 Notifications dans Visual Studio sont utilisées pour indiquer l’état. La palette de notification utilise quatre couleurs suivantes, ainsi que les options de remplissage de premier plan ou de blocage, pour définir des notifications avec les niveaux d’état suivants.

|Usage|Nom|Valeur (tous les thèmes)|Échantillon|
|-----------|----------|--------------------------|------------|
|État : neutre|Notification Blue (bleu de Visual Studio)|1BA1E2 / 27,161,226|![Échantillon 1BA1E2](../../extensibility/ux-guidelines/media/0405_1ba1e2.png "0405_1BA1E2")|
|État : positif|Notification vert (Green Visual Studio)|339933 / 51,153,51|![Échantillon 339933](../../extensibility/ux-guidelines/media/0405_339933.png "0405_339933")|
|État : négative|Notification Red (rouge de Visual Studio)|E51400 / 229,20,0|![Échantillon E51400](../../extensibility/ux-guidelines/media/0405_e51400.png "0405_E51400")|
|État : avertissement|Notification jaune (VS Orange)|FFCC00 / 255,204,0|![Échantillon FFCC00](../../extensibility/ux-guidelines/media/0405_ffcc00.png "0405_FFCC00")|
|Remplissage de premier plan|Notification noir (noir)|000000 / 0,0,0|![Échantillon &#35;000000](../../extensibility/ux-guidelines/media/0405_000000.png "0405_000000")|
|Remplissage de premier plan|Notification blanc (blanc)|FFFFFF / 255,255,255|![Échantillon FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|

#### <a name="examples-of-notification-icons"></a>Exemples d’icônes de notification

|||||
|-|-|-|-|
|![Icône d’alerte](../../extensibility/ux-guidelines/media/0405-45_alert.png "0405-45_Alert")<br />Alerte|![Icône d’avertissement](../../extensibility/ux-guidelines/media/0405-48_warning.png "0405-48_Warning")<br />Warning|![Icône Terminer](../../extensibility/ux-guidelines/media/0405-46_complete.png "0405-46_Complete")<br />Terminé|![Icône arrêter](../../extensibility/ux-guidelines/media/0405-47_stop.png "0405-47_Stop")<br />Arrêter|

### <a name="visual-studio-online"></a>Visual Studio Online
 En général, Visual Studio Online comprend des fonctionnalités hébergées dans un navigateur. La couleur varie dans des environnements différents, mais le style est inchangée.

|Regrouper|Usage|Name|Valeur (tous les thèmes)|Échantillon|
|-----------|-----------|----------|--------------------------|------------|
|TFS|Présentation|TFSO BG|656565/ 101, 101, 101|![Échantillon 656565](../../extensibility/ux-guidelines/media/0405_656565.png "0405_656565")|
|TFS|Contour|TFSO OUT|FFFFFF / 255, 255, 255|![Échantillon FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|
|Napa|Présentation|Blanc|FFFFFF / 255, 255, 255|![Échantillon FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|
|Monaco|Présentation|Blanc|FFFFFF / 255, 255, 255|![Échantillon FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|
|F12|Présentation|Blanc|FFFFFF / 255, 255, 255|![Échantillon FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|
|F12|Normale|F12 Grey_Primary|555555 / 85, 85, 85|![Échantillon 555555](../../extensibility/ux-guidelines/media/0405_555555.png "0405_555555")|
|F12|Pointage|F12 Blue_Hover|2279BF / 34,121,191|![Échantillon 2279BF](../../extensibility/ux-guidelines/media/0405_2279bf.png "0405_2279BF")|
|F12|Désactivé|F12 LtGrey_Disabled|ABABAC / 171,171,172|![Échantillon ABABAC](../../extensibility/ux-guidelines/media/0405_ababac.png "0405_ABABAC")|
|F12|Arrière-plan de pointage|Placez le curseur bg|D9EBF7 / 217,235,247|![Échantillon D9EBF7](../../extensibility/ux-guidelines/media/0405_d9ebf7.png "0405_D9EBF7")|
|F12|D’arrière-plan appuyée|Bg appuyé|B2D7F0 / 178,215,240|![Échantillon B2D7F0](../../extensibility/ux-guidelines/media/0405_b2d7f0.png "0405_B2D7F0")|
|F12|Contour|VS OUT|F6F6F6 / 246,246,246|![Échantillon F6F6F6](../../extensibility/ux-guidelines/media/0405_f6f6f6.png "0405_F6F6F6")|
|F12|Information|Information|00BCF2 / 0,188,242|![Échantillon 00BCF2](../../extensibility/ux-guidelines/media/0405_00bcf2.png "0405_00BCF2")|
|F12|Warning|Warning|F28300 / 242,131,0|![Échantillon F28300](../../extensibility/ux-guidelines/media/0405_f28300.png "0405_F28300")|
|F12|Erreur / négatif|Error_Negative|E81123 / 232,17,35|![Échantillon E81123](../../extensibility/ux-guidelines/media/0405_e81123.png "0405_E81123")|
|F12|Démarrer / positif|Start_Positive|009E49 / 0,158,73|![Échantillon 009E49](../../extensibility/ux-guidelines/media/0405_009e49.png "0405_009E49")|
|F12|Type de saut|Type de saut|9B4F96 / 155,79,150|![Swatch 9B4F96](../../extensibility/ux-guidelines/media/0405_9b4f96.png "0405_9B4F96")|
|F12|Interrogation des événements|Interrogation des événements|A51F00 / 165,31,0|![Échantillon A51F00](../../extensibility/ux-guidelines/media/0405_a51f00.png "0405_A51F00")|
|F12|Marque utilisateur|Marque utilisateur|F16220 / 241,98,32|![Échantillon F16220](../../extensibility/ux-guidelines/media/0405_f16220.png "0405_F16220")|

#### <a name="examples-of-visual-studio-online-icons"></a>Exemples d’icônes de Visual Studio Online

|TFS en ligne||||
|----------------|-|-|-|
|![Icône d’équipe TFS en ligne](../../extensibility/ux-guidelines/media/0405-49_tfsonlineteam.png "0405-49_TFSOnlineTeam")<br />Équipe en ligne|![Icône d’information TFS](../../extensibility/ux-guidelines/media/0405-50_tfsinformation.png "0405-50_TFSInformation")<br />Information|![Icône de l’historique TFS](../../extensibility/ux-guidelines/media/0405-51_tfshistory.png "0405-51_TFSHistory")<br />Historique|![Icône de branche TFS](../../extensibility/ux-guidelines/media/0405-52_tfsbranch.png "0405-52_TFSBranch")<br />Créer une branche|

|Napa||||
|----------|-|-|-|
|![Icône de contenu Napa](../../extensibility/ux-guidelines/media/0405-53_napacontent.png "0405-53_NapaContent")<br />Contenu|![Icône de courrier office Napa](../../extensibility/ux-guidelines/media/0405-54_napaofficemail.png "0405-54_NapaOfficeMail")<br />Messagerie d’Office|![Icône Napa SharePoint](../../extensibility/ux-guidelines/media/0405-55_napasharepoint.png "0405-55_NapaSharePoint")<br />SharePoint|![Icône de volet de tâches Napa](../../extensibility/ux-guidelines/media/0405-56_napataskpane.png "0405-56_NapaTaskPane")<br />Volet de tâches|

|Monaco||||
|------------|-|-|-|
|![Icône de fichiers Monaco](../../extensibility/ux-guidelines/media/0405-57_monacofiles.png "0405-57_MonacoFiles")<br />Fichiers|![Icône Git Monaco](../../extensibility/ux-guidelines/media/0405-58_monacogit.png "0405-58_MonacoGit")<br />Git|![Icône de recherche Monaco](../../extensibility/ux-guidelines/media/0405-59_monacosearch.png "0405-59_MonacoSearch")<br />Rechercher|![Icône de texte Monaco](../../extensibility/ux-guidelines/media/0405-60_monacotext.png "0405-60_MonacoText")<br />Text|

|F12|||
|---------|-|-|
|![Icône de code automatique F12](../../extensibility/ux-guidelines/media/0405-61_f12prettycode.png "0405-61_F12PrettyCode")<br />Code automatique|![Icône d’avertissement F12](../../extensibility/ux-guidelines/media/0405-62_f12warning.png "0405-62_F12Warning")<br />Warning|![Icône émuler F12](../../extensibility/ux-guidelines/media/0405-63_f12emulate.png "0405-63_F12Emulate")<br />Émuler|