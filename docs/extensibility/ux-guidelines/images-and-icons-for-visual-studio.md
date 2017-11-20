---
title: "Images et des icônes pour Visual Studio | Documents Microsoft"
ms.custom: 
ms.date: 04/26/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f410325e-9cf2-4f39-b6d7-b672121c2691
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7856f8fac7e986f3e5383fa91261de39fe815a28
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="images-and-icons-for-visual-studio"></a>Images et des icônes pour Visual Studio
##  <a name="BKMK_ImageUseInVisualStudio"></a>Utilisation d’images dans Visual Studio  
 Avant de créer des illustrations, si possible, rendez l’utilisation des images de 1 000 dans la [bibliothèque d’images Visual Studio](http://www.microsoft.com/en-my/download/details.aspx?id=35825).  
  
### <a name="types-of-images"></a>Types d’images  
  
-   **Icônes**. Petites images qui apparaissent dans les commandes, des hiérarchies, des modèles et ainsi de suite. La taille d’icône par défaut utilisée dans Visual Studio est un fichier PNG 16 x 16. Génèrent des icônes générés automatiquement par le service d’images au format XAML pour la prise en charge HDPI.  
  
     **Remarque :** tandis que les images sont utilisées dans le système de menus, vous ne devez créer une icône pour chaque commande. Consultez [Menus et commandes de Visual Studio](../../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md) pour voir si votre commande doit obtenir une icône.  
  
-   **Miniatures.** Images utilisées dans la zone d’aperçu de boîte de dialogue, telles que la boîte de dialogue Nouveau projet.  
  
-   **Images de la boîte de dialogue.** Images qui apparaissent dans les boîtes de dialogue ou des Assistants, soit en tant que graphiques descriptif ou des indicateurs de message. Utilisez rarement et uniquement lorsque cela est nécessaire pour illustrer un concept difficile ou attirer l’attention de l’utilisateur (avertissement d’alerte,).  
  
-   **Images animées.** Utilisé dans les indicateurs de progression, les barres d’état et les boîtes de dialogue opération.  
  
-   **Curseurs.** Permet d’indiquer si une opération est autorisée à l’aide de la souris, où un objet peuvent être supprimées et ainsi de suite.  
  
##  <a name="BKMK_IconDesign"></a>Conception de l’icône  
  
### <a name="overview"></a>Vue d'ensemble  
 Visual Studio utilise des icônes modernes, geometry nettoyer et un équilibre entre 50/50 positive/négative (clair/sombre), et utilisent métaphores directes, compréhensibles. Conception de l’icône essentiel des points autour de clarté, de simplification et de contexte.  
  
-   **Plus de clarté :** vous concentrer sur l’idée de base qui donne une icône sa signification et la personnalité.  
  
-   **Simplification :** réduire l’icône à sa signification core - obtenir le thème entre avec simplement l’ou les éléments nécessaire et sans fioritures.  
  
-   **Contexte :** prendre en compte tous les aspects du rôle d’une icône pendant le développement du concept, qui est essentielle lorsque vous choisissez les éléments qui constituent la métaphore du cœur de l’icône.  
  
 Icônes, il existe un nombre de points de conception afin d’éviter :  
  
-   N’utilisez pas les icônes qui indiquent les éléments d’interface utilisateur, sauf lorsque cela est approprié. Choisissez une approche plus abstraite ou symbolique lorsque l’élément d’interface utilisateur est courantes, évident, ni unique.  
  
-   Utilisation abusive des éléments en commun n’aimez pas la Loupe, des flèches, des dossiers et des documents. Utilisez ces éléments uniquement lorsque cela est indispensable, ce qui signifie l’icône. Par exemple, la Loupe droite doit indiquer uniquement rechercher, parcourir et rechercher.  
  
-   Bien que certains éléments de l’icône héritée maintenir l’utilisation de la perspective, ne pas créer de nouvelles icônes avec une perspective, sauf si l’élément n’a pas de souci de clarté sans lui.  
  
-   Ne pas entasser sans cesse trop d’informations dans une icône. Une image simple qui peut être facilement reconnue ou apprise comme un symbole reconnaissable est beaucoup plus utile qu’une image trop complexe. Une icône ne peut pas indiquer tout.  
  
### <a name="icon-creation"></a>Création de l’icône  
  
#### <a name="concept-development"></a>Développement de concept  
 Visual Studio propose dans son interface utilisateur à un large éventail de types d’icônes. Étudiez attentivement le type d’icône pendant le développement. N’utilisez pas les objets de l’interface utilisateur vagues ou rares pour les éléments de l’icône. Choisir le lien symbolique dans ces cas, comme avec l’icône de balise active. Notez que la signification de la balise abstraite à gauche est plus évidente que la version de vagues, en fonction de l’interface utilisateur sur la droite :  
  
|||  
|-|-|  
|**Utilisation correcte de l’imagerie symbolique**|**Utilisation incorrecte de l’imagerie symbolique**|  
|![Icône de balise active correcte](../../extensibility/ux-guidelines/media/0404-01_smarttagcorrect.png "0404-01_SmartTagCorrect")|![Icône de balise active incorrecte](../../extensibility/ux-guidelines/media/0404-02_smarttagincorrect.png "0404-02_SmartTagIncorrect")|  
  
 Il existe des instances dans lequel les éléments d’interface utilisateur standards, facilement reconnaissables fonctionnent bien pour les icônes. Ajout de que fenêtre est un exemple :  
  
|||  
|-|-|  
|**Élément d’interface utilisateur correct dans une icône**|**Élément d’interface utilisateur incorrect dans une icône**|  
|![Icône d’ajout de fenêtre correcte](../../extensibility/ux-guidelines/media/0404-03_addwindowcorrect.png "0404-03_AddWindowCorrect")|![Icône d’ajout de fenêtre incorrecte](../../extensibility/ux-guidelines/media/0404-04_addwindowincorrect.png "0404-04_AddWindowIncorrect")|  
  
 N’utilisez pas un document comme élément de base sauf s’il est essentiel de la signification de l’icône. Sans le document élément sur Ajouter un Document (ci-dessous) la signification est perdue, tandis qu’en utilisant Actualiser l’élément de document n’est pas nécessaire de communiquer la signification.  
  
|||  
|-|-|  
|**Utilisation correcte de l’icône de document**|**Utilisation incorrecte de l’icône de document**|  
|![Icône de Document correcte](../../extensibility/ux-guidelines/media/0404-05_documenticoncorrect.png "0404-05_DocumentIconCorrect")|![Icône de Document incorrecte](../../extensibility/ux-guidelines/media/0404-06_documenticonincorrect.png "0404-06_DocumentIconIncorrect")|  
  
 Le concept de « afficher » doit être représenté par l’icône qui illustre le mieux ce qui est affiché, par exemple comme dans l’exemple d’afficher tous les fichiers. Une métaphore de l’objectif peut être utilisée pour indiquer le concept de « view », si nécessaire, comme avec l’exemple d’affichage des ressources.  
  
|||  
|-|-|  
|**« Afficher »**|**« Vue »**|  
|![Afficher l’icône de](../../extensibility/ux-guidelines/media/0404-07_show.png "0404-07_Show")|![Icône d’affichage](../../extensibility/ux-guidelines/media/0404-08_view.png "0404-08_View")|  
  
 La droite agrandissement icône de loupe doit représenter uniquement rechercher, rechercher et Parcourir. La variante de gauche avec le signe plus ou moins doit représenter uniquement le zoom avant / zoom arrière.  
  
|||  
|-|-|  
|**« Recherche »**|**« Zoom »**|  
|![Icône de recherche](../../extensibility/ux-guidelines/media/0404-09_search.png "0404-09_Search")|![Icône de zoom](../../extensibility/ux-guidelines/media/0404-10_zoom.png "0404-10_Zoom")|  
  
 Dans les vues de l’arborescence, n’utilisez pas l’icône de dossier et un modificateur. Lorsqu’il est disponible, utilisez uniquement le modificateur.  
  
|||  
|-|-|  
|**Icônes d’arborescence correcte**|**Icônes d’arborescence incorrecte**|  
|![Icône d’arborescence correcte &#40; 1 &#41; ] (../../extensibility/ux-guidelines/media/0404-11_treeviewcorrect1.png "0404-11_TreeViewCorrect1") ![corriger l’icône d’arborescence &#40; 2 &#41;] (../../extensibility/ux-guidelines/media/0404-12_treeviewcorrect2.png "0404-12_TreeViewCorrect2")|![Icône d’arborescence incorrecte &#40; 1 &#41; ] (../../extensibility/ux-guidelines/media/0404-13_treeviewincorrect1.png "0404-13_TreeViewIncorrect1") ![incorrecte icône d’arborescence &#40; 2 &#41;] (../../extensibility/ux-guidelines/media/0404-14_treeviewincorrect2.png "0404-14_TreeViewIncorrect2")|  
  
### <a name="style-details"></a>Détails de style  
  
#### <a name="layout"></a>Disposition  
 Éléments de la pile comme indiqué pour les icônes 16 x 16 standard :  
  
 ![Pile de disposition pour les icônes 16 x 16](../../extensibility/ux-guidelines/media/0404-15_layoutstack.png "0404-15_LayoutStack")<br />Pile de disposition pour les icônes 16x16
  
 Éléments de notification d’état sont mieux utilisées sous forme d’icônes d’autonome. Il existe des contextes, toutefois, dans laquelle une notification doit être empilée sur l’élément de base, comme avec l’icône de tâche terminée :  
  
 ![Notifications autonome dans Visual Studio](../../extensibility/ux-guidelines/media/0404-16_standalonenotificationicons.png "0404-16_StandaloneNotificationIcons")<br />Icônes de notification autonome
  
 ![Icône de tâche terminée](../../extensibility/ux-guidelines/media/0404-17_taskcomplete.png "0404-17_TaskComplete")<br />Icône de tâche terminée
  
 Icônes de projet sont généralement les fichiers .ico qui contiennent plusieurs tailles. La plupart des icônes 16 x 16 contiennent les mêmes éléments. Les versions de 32 x 32 ont plus de détails, notamment le type de projet, le cas échéant.  
  
 ![Icônes dans Visual Studio de projet](../../extensibility/ux-guidelines/media/0404-18_iconprojectthreesizes.png "0404-18_IconProjectThreeSizes")<br />Icônes de projet de bibliothèque de contrôles Windows VB, 16 x 16 et 32 x 32 
  
 Centre une icône dans son frame de pixels. Si ce n’est pas possible, aligner l’icône en haut et/ou à droite de l’image.  
  
 ![Icône centrée dans le frame de pixels](../../extensibility/ux-guidelines/media/0404-19_iconcentered.png "0404-19_IconCentered")<br />Icône centrée dans le frame de pixels
  
 ![Icône alignée sur supérieur droit du frame de pixels](../../extensibility/ux-guidelines/media/0404-20_icontopright.png "0404-20_IconTopRight")<br />Icône aligné en haut à droite de l’image
  
 ![Icône centrée et alignée en haut du frame de pixels](../../extensibility/ux-guidelines/media/0404-21_icontopalign.png "0404-21_IconTopAlign")<br />Icône centrée et alignée sur la partie supérieure de l’image
  
 Pour obtenir une idéale alignement et équilibre, évitez obstacle d’élément de base de l’icône glyphes de l’action. Place le glyphe vers le haut à gauche de l’élément de base. Lorsque vous ajoutez un élément supplémentaire, envisagez l’alignement et le solde de l’icône.  
  
|||  
|-|-|  
|**Solde et alignement correct**|**Solde et alignement incorrect**|  
|![Corriger l’alignement et équilibre des icônes](../../extensibility/ux-guidelines/media/0404-22_alignbalancecorrect.png "0404-22_AlignBalanceCorrect")|![Équilibre des icônes incorrects et alignement](../../extensibility/ux-guidelines/media/0404-23_alignbalanceincorrect.png "0404-23_AlignBalanceIncorrect")|  
  
 Vérifiez la parité de taille pour les icônes qui partagent des éléments et sont utilisés dans les ensembles. Notez que dans l’appariement incorrect, le cercle et flèche sont surdimensionnées et ne correspondent pas.  
  
|||  
|-|-|  
|**Parité de taille correcte**|**Parité de taille incorrecte**|  
|![Corriger la taille d’icône et la parité](../../extensibility/ux-guidelines/media/0404-24_sizeparitycorrect.png "0404-24_SizeParityCorrect")|![Taille d’icône incorrect et la parité](../../extensibility/ux-guidelines/media/0404-25_sizeparityincorrect.png "0404-25_SizeParityIncorrect")|  
  
 Utilisez ligne cohérente et poids visual. Évaluer la différence entre aux autres icônes de l’icône que vous créez à l’aide d’une comparaison côte-à-côte. Utilisez l’image 16 x 16 entière, n’utilisez jamais 15 x 15 ou plus petites. Le rapport de (dark-clair) négatif à positif doit être 50/50.  
  
|||  
|-|-|  
|**Rapport négatif à positif**|**Taux de négatif à positif incorrect**|  
|![Corriger une épaisseur visuelle pour les icônes &#40; 1 &#41; ] (../../extensibility/ux-guidelines/media/0404-26_visualweightcorrect1.png "0404-26_VisualWeightCorrect1")<br /><br /> ![Corriger une épaisseur visuelle pour les icônes &#40; 2 &#41; ] (../../extensibility/ux-guidelines/media/0404-27_visualweightcorrect2.png "0404-27_VisualWeightCorrect2")<br /><br /> ![Corriger une épaisseur visuelle pour les icônes &#40; 3 &#41; ] (../../extensibility/ux-guidelines/media/0404-28_visualweightcorrect3.png "0404-28_VisualWeightCorrect3")|![Épaisseur visuelle incorrecte pour les icônes](../../extensibility/ux-guidelines/media/0404-29_visualweightincorrect.png "0404-29_VisualWeightIncorrect")|  
  
 Utiliser des formes simples, comparables et complémentaire angles pour générer des vos éléments sans compromettre l’intégrité de l’élément. Utiliser des angles de 45 ou 90° lorsque cela est possible.  
  
 ![Corriger les angles des icônes](../../extensibility/ux-guidelines/media/0404-30_iconanglescorrect.png "0404-30_IconAnglesCorrect")  
  
#### <a name="perspective"></a>Perspective   
 Gardez à l’icône clair et faciles à comprendre. Utiliser le point de vue et une source de lumière uniquement lorsque cela est nécessaire. Bien qu’à l’aide de la perspective sur les éléments de l’icône doit être évitée, certains éléments sont non reconnaissables sans lui. Dans ce cas, une perspective stylisée communique la clarté de l’élément.  
  
 ![perspective à 3 points](../../extensibility/ux-guidelines/media/0404-31_3pointperspective.png "0404-31_3PointPerspective")<br />Perspective à 3 points
  
 ![perspective à 1 point](../../extensibility/ux-guidelines/media/0404-32_1pointperspective.png "0404-32_1PointPerspective")<br />Perspective à 1 point
  
 La plupart des éléments doit faire face au ou dirigé vers la droite :  
  
 ![Icônes avec angle droit](../../extensibility/ux-guidelines/media/0404-33_angledright.png "0404-33_AngledRight")  
  
 Utiliser des sources de lumière uniquement lorsque vous ajoutez plus de clarté nécessaire à un objet.  
  
|||  
|-|-|  
|**Source de lumière correcte**|**Source de lumière incorrecte**|  
|![Corriger les sources de lumière pour les icônes](../../extensibility/ux-guidelines/media/0404-34_lightsourcescorrect.png "0404-34_LightSourcesCorrect")|![Les sources de lumière incorrectes pour les icônes](../../extensibility/ux-guidelines/media/0404-35_lightsourcesincorrect.png "0404-35_LightSourcesIncorrect")|  
  
 Utiliser des plans uniquement pour améliorer la lisibilité ou pour mieux communiquer la métaphore du. Le solde de (dark-light) négatif une valeur positive doit être 50/50.  
  
|||  
|-|-|  
|**Utilisation correcte des plans**|**Utilisation incorrecte de contours**|  
|![Corriger les contours](../../extensibility/ux-guidelines/media/0404-36_outlinescorrect.png "0404-36_OutlinesCorrect")|![Plans incorrects](../../extensibility/ux-guidelines/media/0404-37_outlinesincorrect.png "0404-37_OutlinesIncorrect")|  
  
#### <a name="icon-types"></a>Types d’icônes  
 **Shell et de barre de commandes** icônes se composent de pas plus de trois des éléments suivants : une base, un seul modificateur, une action ou un état.  
  
 ![Exemples de shell et de barre d’icônes de commandes](../../extensibility/ux-guidelines/media/0404-38_shellicons.png "0404-38_ShellIcons")<br />Exemples de shell et de barre d’icônes de commande
  
 **Barre de commandes de fenêtre outil** icônes se composent de pas plus de trois des éléments suivants : une base, un seul modificateur, une action ou un état.  
  
 ![Exemples de fenêtre outil commande barre d’icônes](../../extensibility/ux-guidelines/media/0404-39_toolwindowcommandbaricons.png "0404-39_ToolWindowCommandBarIcons")<br />Exemples d’icônes de barre de commandes de fenêtre outil
  
 **Lever l’ambiguïté vue arborescence** icônes se composent de pas plus de trois des éléments suivants : une base, un seul modificateur, une action ou un état.  
  
 ![Exemples d’arborescence d’afficher des icônes de désambiguïsateur de](../../extensibility/ux-guidelines/media/0404-40_treeviewicons.png "0404-40_TreeViewIcons")<br />Icônes de désambiguïsateur d’afficher les exemples d’arborescence
  
 **Classification de la valeur basée sur l’état** icônes existent dans les états suivants : actif, Directory désactivée et désactivé inactif.  
  
 ![Exemples d’icônes de taxonomie basée sur l’état de la valeur](../../extensibility/ux-guidelines/media/0404-41_statebasedtaxonomy.png "0404-41_StateBasedTaxonomy")<br />Exemples d’icônes de taxonomie basée sur l’état de la valeur
  
 **IntelliSense** icônes se composent de pas plus de trois des éléments suivants : une base de plusieurs modificateurs d’et un état.  
  
 ![Exemples d’icônes IntelliSense](../../extensibility/ux-guidelines/media/0404-42_intellisenseicons.png "0404-42_IntelliSenseIcons")<br />Exemples d’icônes IntelliSense
  
 **Petit (16 x 16) projet** icônes doivent avoir pas plus de deux éléments : une base et un seul modificateur.  
  
 ![Exemples de petit (16 x 16) des icônes de projet](../../extensibility/ux-guidelines/media/0404-43_16x16project1.png "0404-43_16x16Project1") ![icône de projet 16 x 16 &#40; 2 &#41;] (../../extensibility/ux-guidelines/media/0404-44_16x16project2.png "0404-44_16x16Project2") ![icône de projet 16 x 16 &#40; 3 &#41;] (../../extensibility/ux-guidelines/media/0404-45_16x16project3.png "0404-45_16x16Project3")<br />Exemples de petites icônes de projet (16 x 16)
  
 **Grande (32 x 32) projet** icônes se composent de pas plus de quatre des éléments suivants : une base de modificateurs d’une à deux et une langue de superposition.  
  
 ![Exemples de grande taille (32 x 32) des icônes de projet](../../extensibility/ux-guidelines/media/0404-46_32x32project.png "0404-46_32x32Project")<br />Exemples de grandes icônes de projet (32 x 32)
  
### <a name="production-details"></a>Détails de la production  
 Tous les nouveaux éléments de l’interface utilisateur doivent être créés à l’aide de Windows Presentation Foundation (WPF) et toutes les nouvelles icônes pour WPF doivent être au format PNG de 32 bits. Le fichier PNG 24 bits est un format hérité qui ne prend pas en charge la transparence et n’est donc pas recommandé pour les icônes.  
  
 Enregistrer la résolution de 96 PPP.  
  
#### <a name="file-types"></a>Types de fichiers  
  
-   **32 bits PNG :** le format par défaut pour les icônes. Format de fichier de la compression sans perte de données qui peut stocker une image raster unique (pixels). fichiers PNG 32 bits prennent en charge la transparence de canal alpha, la correction gamma et l’entrelacement.  
  
-   **BMP de 32 bits :** pour les contrôles non-WPF. Également appelé XP ou couleurs, 32 bits BMP est un format d’image de RVB/A, une image de couleurs vraies avec une transparence de canal alpha. Le canal alpha est une couche de transparence désignée dans Adobe Photoshop qui est ensuite enregistré dans la bitmap comme un supplémentaire (quatrième) canal de couleur. Un arrière-plan noir est ajouté au cours de la production d’illustration à tous les fichiers de format BMP 32 bits pour fournir une indication visuelle rapide sur la profondeur de couleur. Cet arrière-plan noir représente la zone pour être masquée dans l’interface utilisateur.  
  
-   **32 bits ICO :** pour les icônes de projet et ajouter un élément. Tous les fichiers ICO sont des couleurs de 32 bits avec la transparence de canal alpha (RVB/A). Étant donné que les fichiers ICO peuvent stocker plusieurs tailles et les palettes de couleurs, Vista icônes sont souvent dans un format ICO contenant 16 x 16, 32 x 32, 48 x 48 et tailles d’image de 256 x 256. Pour afficher correctement dans l’Explorateur Windows, les fichiers ICO doivent être enregistré vers le bas à des profondeurs de couleur 24 bits et 8 bits pour chaque taille de l’image.  
  
-   **XAML :** pour les surfaces de dessin et les ornements de Windows. Icônes XAML sont des fichiers image vectorielle qui prennent en charge la mise à l’échelle, faire pivoter, classement et la transparence. Ils ne sont pas courantes dans Visual Studio aujourd'hui mais sont de plus en plus populaires en raison de leur flexibilité.  
  
-   **SVG**  
  
-   **24 bits BMP :** pour la barre de commandes de Visual Studio. Un format d’image true couleurs RVB, BMP de 24 bits est une convention d’icône qui crée une couche de transparence à l’aide à magenta (R = 255, G = 0, B = 255) en tant qu’une clé de couleur pour une couche de transparence de masquage à la sortie. Dans une image BMP 24 bits, toutes les surfaces magenta sont affichés à l’aide de la couleur d’arrière-plan.  
  
-   **24 bits GIF :** pour la barre de commandes de Visual Studio. Un true-couleur RVB format d’image qui prend en charge la transparence. Fichiers GIF sont souvent utilisés dans l’illustration de l’Assistant et les animations de GIF.  
  
### <a name="icon-construction"></a>Construction d’icône  
 La plus petite taille d’icône dans Visual Studio est de 16 x 16. Le plus grand commun utilisation est 32 x 32. Gardez à l’esprit ne pas pour remplir l’image 16 x 16, 24 x 24 ou 32 x 32 ensemble lors de la conception d’une icône. Construction de l’icône lisibles, uniform est essentielle pour la reconnaissance de l’utilisateur. Respecter les points suivants lors de la génération des icônes.  
  
-   Icônes doit être clair, faciles à comprendre et cohérente.  
  
-   Il est préférable d’utiliser les éléments de notification d’état sous forme d’icônes uniques et ne pas à s’empilent les un élément de base d’icône. Dans certains contextes, l’interface utilisateur peut nécessiter l’élément d’état pour être associé à un élément de base.  
  
-   Icônes de projet sont généralement les fichiers .ico qui contiennent plusieurs tailles. Uniquement les icônes 16 x 16, 24 x 24 et 32 x 32 sont mis à jour. La plupart des icônes de 16 x 16 et 24 x 24 contiendra les mêmes éléments. Les icônes de 32 x 32 contiennent plus de détails, notamment le type de langage de projet le cas échéant.  
  
-   Pour les icônes de 32 x 32, les éléments de base ont généralement une épaisseur de trait de 2 pixels. Une épaisseur de trait de 1 ou 2 pixels peut être utilisée pour les éléments de détail. Utilisez votre appréciation pour déterminer ce qui est plus adapté.  
  
-   Avoir au moins une 1 pixel d’espacement entre les éléments de 16 x 16 et des icônes de 24 x 24. Pour les icônes de 32 x 32, utilisez 2 pixels espacement entre les éléments et entre le modificateur et un élément de base.  
  
 ![Élément espacement pour les icônes de taille de 16 x 16, 24 x 24 et 32 x 32](../../extensibility/ux-guidelines/media/0404-47_elementspacing.png "0404-47_ElementSpacing")<br />Espacement des éléments pour les icônes de taille de 16 x 16, 24 x 24 et 32 x 32
  
#### <a name="color-and-accessibility"></a>Couleur et l’accessibilité  
 Recommandations de compatibilité de Visual Studio requièrent que toutes les icônes dans le produit conforme accessibilité aux conditions requises pour la couleur et le contraste. Ceci est possible grâce à inversion de l’icône, et lors de la conception, vous devez être conscient de que leur est inversés par programmation dans le produit.  
  
 Pour plus d’informations sur l’utilisation de couleurs dans les icônes de Visual Studio, consultez [à l’aide de la couleur dans les images](../../extensibility/ux-guidelines/images-and-icons-for-visual-studio.md#BKMK_UsingColorInImages).  
  
##  <a name="BKMK_UsingColorInImages"></a>À l’aide de la couleur dans les images  
  
### <a name="overview"></a>Vue d'ensemble  
 Icônes dans Visual Studio sont principalement monochromes. Couleur est réservée pour transmettre des informations spécifiques et jamais des ornements. Couleur est utilisée :  
  
-   pour indiquer une action  
  
-   pour avertir l’utilisateur à une notification d’état  
  
-   pour désigner l’affiliation de langage  
  
-   pour différencier les éléments dans IntelliSense  
  
### <a name="accessibility"></a>Accessibilité  
 Recommandations de compatibilité de Visual Studio requièrent que toutes les icônes vérifiées dans le test de produit les exigences d’accessibilité pour la couleur et le contraste. Couleurs de la palette de langage visual ont été testées et répondre à ces exigences.  
  
#### <a name="color-inversion-for-dark-themes"></a>Inversion des couleurs des thèmes foncés  
 Pour que les icônes apparaissent avec le contraste approprié dans le thème sombre de Visual Studio, une inversion est appliquée par programmation. Les couleurs dans ce guide ont été choisis en partie afin qu’ils inverser correctement. Limiter votre utilisation de couleur à cette palette, ou vous obtiendrez des résultats imprévisibles lors de l’inversion est appliquée.  
  
 ![Exemples d’icônes qui ont eu leurs couleurs inversées](../../extensibility/ux-guidelines/media/0405-01_darkthemeinversion.png "01_DarkThemeInversion-0405")<br />Exemples d’icônes qui ont eu leurs couleurs inversées
  
### <a name="base-palette"></a>Palette de base  
 Toutes les icônes standards contiennent trois couleurs de base. Icônes ne contient aucun des dégradés ou des ombres portées, avec une ou deux exceptions pour les icônes de l’outil de 3D.  
  
|Utilisation|Nom|Valeur (thème clair)|Échantillon|Exemple|  
|-----------|----------|---------------------------|------------|-------------|  
|Arrière-plan/foncé|VS BG|424242 / 66,66,66|![Échantillon 424242](../../extensibility/ux-guidelines/media/0405_424242.png "0405_424242")|![Exemple de palette de base](../../extensibility/ux-guidelines/media/0405-02_basepaletteexample.png "02_BasePaletteExample-0405")|  
|Premier plan/léger|FG DE VS|F0EFF1 / 240,239,241|![Échantillon F0EFF1](../../extensibility/ux-guidelines/media/0405_f0eff1.png "0405_F0EFF1")||  
|Plan|VS Out|F6F6F6 / 246,246,246|![Échantillon F6F6F6](../../extensibility/ux-guidelines/media/0405_f6f6f6.png "0405_F6F6F6")||  
  
 Outre les couleurs de base, chaque icône peut contenir une couleur supplémentaire à partir de la palette étendue.  
  
### <a name="extended-palette"></a>Palette étendue  
  
#### <a name="action-modifiers"></a>Modificateurs de l’action  
 Les quatre couleurs ci-dessous indiquent les types d’actions requises par les modificateurs de l’action :  
  
|Utilisation|Nom|Valeur (tous les thèmes)|Échantillon|  
|-----------|----------|--------------------------|------------|  
|Positif|VS Action vert|388 A 34 / 56,138,52|![Échantillon 388 a 34](../../extensibility/ux-guidelines/media/0405_388a34.png "0405_388A34")|  
|Négatif|VS Action rouge|A1260D / 161,38,13|![Échantillon A1260D](../../extensibility/ux-guidelines/media/0405_a1260d.png "0405_A1260D")|  
|Neutral|VS Action bleu|C 00539 / 0,83,156|![Échantillon 00539c](../../extensibility/ux-guidelines/media/0405_00539c.png "0405_00539C")|  
|Créer/nouveau|VS Action Orange|C27D1A / 194,156,26|![Échantillon C27D1A](../../extensibility/ux-guidelines/media/0405_c27d1a.png "0405_C27D1A")|  
  
##### <a name="examples"></a>Exemples  
 Vert est utilisée pour les modificateurs d’action positive comme « Ajouter », « Exécuter, » « Lecture » et « Valider ».  
  
|||||  
|-|-|-|-|  
|![Icône d’exécution](../../extensibility/ux-guidelines/media/0405-03_actionmodifierrun.png "03_ActionModifierRun-0405")<br />Exécuter|![Icône exécuter la requête](../../extensibility/ux-guidelines/media/0405-04_executequery.png "04_ExecuteQuery-0405")<br />Exécuter la requête|![Icône lire toutes les étapes](../../extensibility/ux-guidelines/media/0405-05_playallsteps.png "05_PlayAllSteps-0405")<br />Lire toutes les étapes|![Icône Ajouter le contrôle](../../extensibility/ux-guidelines/media/0405-06_addcontrol.png "06_AddControl-0405")<br />Ajouter le contrôle|  
  
 Rouge est utilisée pour les modificateurs d’action négatif comme « Delete », « Stop », « Annuler » et « Clôture ».  
  
|||||  
|-|-|-|-|  
|![Icône Supprimer la relation](../../extensibility/ux-guidelines/media/0405-07_deleterelationship.png "07_DeleteRelationship-0405")<br />Supprimer la relation|![Icône Supprimer la colonne](../../extensibility/ux-guidelines/media/0405-08_deletecolumn.png "08_DeleteColumn-0405")<br />Supprimer la colonne|![Icône de requête d’arrêt](../../extensibility/ux-guidelines/media/0405-09_stopquery.png "09_StopQuery-0405")<br />Arrêter la requête|![Icône de connexion en mode hors connexion](../../extensibility/ux-guidelines/media/0405-10_connectionoffline.png "10_ConnectionOffline-0405")<br />Connexion hors connexion|  
  
 Bleu est appliqué à une action neutre modificateurs plus souvent représentées par des flèches, comme « Ouvrir, » « Suivant », « Précédent », « Importer » et « Exportation ».  
  
|||||  
|-|-|-|-|  
|![Accédez à l’icône de champ](../../extensibility/ux-guidelines/media/0405-11_gotofield.png "11_GoToField-0405")<br />Accédez au champ|![Regroupés par lots de vérification &#45; icône](../../extensibility/ux-guidelines/media/0405-12_batchedcheckin.png "12_BatchedCheckIn-0405")<br />Archivage par lots|![Icône de l’éditeur adresse](../../extensibility/ux-guidelines/media/0405-13_addresseditor.png "13_AddressEditor-0405")<br />Éditeur d’adresse|![Icône de l’éditeur association](../../extensibility/ux-guidelines/media/0405-14_associationeditor.png "14_AssociationEditor-0405")<br />Éditeur d’associations|  
  
 Or foncé est principalement utilisé pour le modificateur de « Nouveau ».  
  
|||||  
|-|-|-|-|  
|![Icône de nouveau projet](../../extensibility/ux-guidelines/media/0405-15_newproject.png "15_NewProject-0405")<br />Nouveau projet|![Icône Créer un graphique](../../extensibility/ux-guidelines/media/0405-16_createnewgraph.png "16_CreateNewGraph-0405")<br />Créer un graphique|![Nouvelle icône de test unitaire](../../extensibility/ux-guidelines/media/0405-17_newunittest.png "17_NewUnitTest-0405")<br />Nouveau Test unitaire|![Icône de nouvelle liste](../../extensibility/ux-guidelines/media/0405-18_newlistitem.png "18_NewListItem-0405")<br />Nouvel élément de liste|  
  
#### <a name="special-cases"></a>Cas particuliers  
 Dans certains cas, un modificateur de couleur action peut être utilisé de façon indépendante sous forme d’icône autonome. La couleur utilisée pour l’icône reflète les actions que l’icône est associée. Cette utilisation est limitée à un petit sous-ensemble des icônes, y compris :  
  
||||||  
|-|-|-|-|-|  
|![Icône d’exécution](../../extensibility/ux-guidelines/media/0405-03_actionmodifierrun.png "03_ActionModifierRun-0405")<br />Exécuter|![Icône arrêter](../../extensibility/ux-guidelines/media/0405-19_stop.png "19_Stop-0405")<br />Arrêter|![Icône Supprimer](../../extensibility/ux-guidelines/media/0405-20_delete.png "20_Delete-0405")<br />Supprimer|![Icône Enregistrer](../../extensibility/ux-guidelines/media/0405-21_save.png "21_Save-0405")<br />Enregistrer|![Icône précédent naviguer](../../extensibility/ux-guidelines/media/0405-22_navigateback.png "22_NavigateBack-0405")<br />Naviguer vers l’arrière|  
  
### <a name="code-hierarchy-palette"></a>Palette de hiérarchie de code  
  
#### <a name="folder"></a>Dossier  
  
|Utilisation|Nom|Valeur (tous les thèmes)|Échantillon|Exemple|  
|-----------|----------|--------------------------|------------|-------------|  
|Dossiers|Dossier|DCB67A / 220,182,122|![Échantillon DCB67A](../../extensibility/ux-guidelines/media/0405_dcb67a.png "0405_DCB67A")|![Icône de couleur de dossier](../../extensibility/ux-guidelines/media/0405-23_foldercolor.png "23_FolderColor-0405")|  
  
#### <a name="visual-studio-languages"></a>Visual Studio languages  
 Chacun des langages courants ou des plateformes disponibles dans Visual Studio possède une couleur associée. Ces couleurs sont utilisées sur l’icône de base, ou sur les modificateurs de langue qui s’affichent dans le coin supérieur droit d’icônes composées.  
  
|Utilisation|Nom|Valeur (tous les thèmes)|Échantillon|  
|-----------|----------|--------------------------|------------|  
|ASP, HTML, WPF|ASP HTML WPF bleu|0095D 7 / 0,149,215|![Échantillon 0095d7](../../extensibility/ux-guidelines/media/0405_0096d7.png "0405_0096D7")|  
|C++|CPP violet|9B4F96 / 155,79,150|![Échantillon 9B4F96](../../extensibility/ux-guidelines/media/0405_9b4f96.png "0405_9B4F96")|  
|C#|CS vert (Green Action de Visual Studio)|388 A 34 / 56,138,52|![Échantillon 388 a 34](../../extensibility/ux-guidelines/media/0405_388a34.png "0405_388A34")|  
|CSS|CSS rouge|BD1E2D / 189,30,45|![Échantillon BD1E2D](../../extensibility/ux-guidelines/media/0405_bd1e2d.png "0405_BD1E2D")|  
|F#|FS violet|672878 / 103,40,120|![Échantillon 672878](../../extensibility/ux-guidelines/media/0405_672878.png "0405_672878")|  
|JavaScript|JS Orange|F16421 / 241,100,33|![Échantillon F16421](../../extensibility/ux-guidelines/media/0405_f16421.png "0405_F16421")|  
|VB|VB Blue (bleu d’Action de Visual Studio)|C 00539 / 0,83,156|![Échantillon 00539c](../../extensibility/ux-guidelines/media/0405_00539c.png "0405_00539C")|  
|TypeScript|TS Orange|E04C06 / 224,76,6|![Échantillon E04C06](../../extensibility/ux-guidelines/media/0405_e04c06.png "0405_E04C06")|  
|Python|PIER vert|879636 / 135,150,54|![Échantillon 879636](../../extensibility/ux-guidelines/media/0405_879636.png "0405_879636")|  
  
##### <a name="examples-of-icons-with-language-modifiers"></a>Exemples d’icônes avec des modificateurs de langage  
  
|||||||  
|-|-|-|-|-|-|  
|![Icône Visual Basic](../../extensibility/ux-guidelines/media/0405-25_vb.png "25_VB-0405")<br />VB|![C &#35; icône](../../extensibility/ux-guidelines/media/0405-26_csharp.png "26_CSharp-0405")<br />C#|![C &#43; &#43; icône](../../extensibility/ux-guidelines/media/0405-27_cplusplus.png "27_CPlusPlus-0405")<br />C++|![F &#35; icône](../../extensibility/ux-guidelines/media/0405-28_fsharp.png "28_FSharp-0405")<br />F#|![Icône de JavaScript](../../extensibility/ux-guidelines/media/0405-29_javascript.png "29_JavaScript-0405")<br />JavaScript|![Icône Python](../../extensibility/ux-guidelines/media/0405-30_python.png "30_Python-0405")<br />Python|  
|![Icône HTML](../../extensibility/ux-guidelines/media/0405-31_html.png "31_HTML-0405")<br />HTML|![Icône WPF](../../extensibility/ux-guidelines/media/0405-32_wpf.png "32_WPF-0405")<br />WPF|![Icône ASP](../../extensibility/ux-guidelines/media/0405-33_asp.png "33_ASP-0405")<br />ASP|![Icône CSS](../../extensibility/ux-guidelines/media/0405-34_css.png "34_CSS-0405")<br />CSS|![Icône typeScript](../../extensibility/ux-guidelines/media/0405-35_typescript.png "35_TypeScript-0405")<br />TypeScript||  
  
#### <a name="intellisense"></a>IntelliSense  
 Icônes IntelliSense utilisent une palette de couleurs exclusif. Ces couleurs sont utilisées pour aider les utilisateurs rapidement faire la distinction entre les différents éléments dans la liste contextuelle IntelliSense.  
  
|Utilisation|Nom|Valeur (tous les thèmes)|Échantillon|  
|-----------|----------|--------------------------|------------|  
|Classe d’événements|VS Action Orange|C27D1A / 194,125,26|![Échantillon C27D1A](../../extensibility/ux-guidelines/media/0405_c27d1a.png "0405_C27D1A")|  
|Méthode d’extension, méthode, Module, délégué|VS Action violet|652D 90 / 101,45,144|![Échantillon 652d90](../../extensibility/ux-guidelines/media/0405_652d90.png "0405_652D90")|  
|Champ, élément Enum, Macro, Structure, Union valeur Type, opérateur, Interface|VS Action bleu|C 00539 / 0,83,156|![Échantillon 00539c](../../extensibility/ux-guidelines/media/0405_00539c.png "0405_00539C")|  
|Objet|VS Action vert|388 A 34 / 56,138,52|![Échantillon 388 a 34](../../extensibility/ux-guidelines/media/0405_388a34.png "0405_388A34")|  
|Constante, Exception, élément Enum, carte, élément de la carte, Namespace, modèle de définition de Type|Arrière-plan (BG Visual Studio)|424242 / 66,66,66|![Échantillon 424242](../../extensibility/ux-guidelines/media/0405_424242.png "0405_424242")|  
  
##### <a name="examples-of-intellisense-icons"></a>Exemples d’icônes IntelliSense  
  
||||||  
|-|-|-|-|-|  
|![Icône de classe IntelliSense](../../extensibility/ux-guidelines/media/0405-36_intellisenseclass.png "36_IntelliSenseClass-0405")<br />Classe|![Icône d’événement privé IntelliSense](../../extensibility/ux-guidelines/media/0405-37_intellisenseprivateevent.png "37_IntelliSensePrivateEvent-0405")<br />Événements privés|![Icône de délégué IntelliSense](../../extensibility/ux-guidelines/media/0405-38_intellisensedelegate.png "38_IntelliSenseDelegate-0405")<br />Délégué|![Icône friend de méthode IntelliSense](../../extensibility/ux-guidelines/media/0405-39_intellisensemethodfriend.png "39_IntelliSenseMethodFriend-0405")<br />Méthode Friend|![Icône de champ](../../extensibility/ux-guidelines/media/0405-40_field.png "40_Field-0405")<br />Champ|  
|![IntelliSense protégé icône d’élément enum](../../extensibility/ux-guidelines/media/0405-41_intellisenseprotectedenumitem.png "41_IntelliSenseProtectedEnumItem-0405")<br />Élément Enum protégé|![Icône d’objet IntelliSense](../../extensibility/ux-guidelines/media/0405-42_intellisenseobject.png "42_IntelliSenseObject-0405")<br />Objet|![Icône de modèle IntelliSense](../../extensibility/ux-guidelines/media/0405-43_intellisensetemplate.png "43_IntelliSenseTemplate-0405")<br />Modèle|![Icône de raccourci d’exception IntelliSense](../../extensibility/ux-guidelines/media/0405-44_intellisenseexceptionshortcut.png "44_IntelliSenseExceptionShortcut-0405")<br />Raccourci d’exception||  
  
### <a name="notifications"></a>Notifications  
 Les notifications dans Visual Studio sont utilisées pour indiquer l’état. La palette de notification utilise les quatre couleurs suivantes, ainsi que les options de remplissage de premier plan ou de blocage, pour définir des notifications avec les niveaux d’état suivants.  
  
|Utilisation|Nom|Valeur (tous les thèmes)|Échantillon|  
|-----------|----------|--------------------------|------------|  
|État : neutre|Notification Blue (bleu Visual Studio)|1BA1E2 / 27,161,226|![Échantillon 1BA1E2](../../extensibility/ux-guidelines/media/0405_1ba1e2.png "0405_1BA1E2")|  
|État : positif|Notification vert (Green Visual Studio)|339933 / 51,153,51|![Échantillon 339933](../../extensibility/ux-guidelines/media/0405_339933.png "0405_339933")|  
|État : négatif|Notification rouge (VS rouge)|E51400 / 229,20,0|![Échantillon E51400](../../extensibility/ux-guidelines/media/0405_e51400.png "0405_E51400")|  
|État : avertissement|Notification jaune (VS Orange)|FFCC00 / 255,204,0|![Échantillon FFCC00](../../extensibility/ux-guidelines/media/0405_ffcc00.png "0405_FFCC00")|  
|Remplissage de premier plan|Notification noir (noir)|000000 / 0,0,0|![Échantillon &#35; 000000](../../extensibility/ux-guidelines/media/0405_000000.png "0405_000000")|  
|Remplissage de premier plan|Notification blanc (blanc)|FFFFFF / 255,255,255|![Échantillon FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|  
  
#### <a name="examples-of-notification-icons"></a>Exemples d’icônes de notification  
  
|||||  
|-|-|-|-|  
|![Icône d’alerte](../../extensibility/ux-guidelines/media/0405-45_alert.png "45_Alert-0405")<br />Alerte|![Icône d’avertissement](../../extensibility/ux-guidelines/media/0405-48_warning.png "48_Warning-0405")<br />Warning|![Icône terminée](../../extensibility/ux-guidelines/media/0405-46_complete.png "46_Complete-0405")<br />Terminé|![Icône arrêter](../../extensibility/ux-guidelines/media/0405-47_stop.png "47_Stop-0405")<br />Arrêter|  
  
### <a name="visual-studio-online"></a>Visual Studio Online  
 En règle générale, Visual Studio Online comprend des fonctionnalités hébergées dans un navigateur. La couleur varie dans des environnements différents, mais le style reste le même.  
  
|Regrouper|Utilisation|Nom|Valeur (tous les thèmes)|Échantillon|  
|-----------|-----------|----------|--------------------------|------------|  
|TFS|Présentation|TFSO BG|656565/ 101, 101, 101|![Échantillon 656565](../../extensibility/ux-guidelines/media/0405_656565.png "0405_656565")|  
|TFS|Plan|TFSO OUT|FFFFFF / 255, 255, 255|![Échantillon FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|  
|Napa|Présentation|Blanc|FFFFFF / 255, 255, 255|![Échantillon FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|  
|Monaco|Présentation|Blanc|FFFFFF / 255, 255, 255|![Échantillon FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|  
|F12|Présentation|Blanc|FFFFFF / 255, 255, 255|![Échantillon FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|  
|F12|Normale|F12 Grey_Primary|555555 / 85, 85, 85|![Échantillon 555555](../../extensibility/ux-guidelines/media/0405_555555.png "0405_555555")|  
|F12|Pointage|F12 Blue_Hover|2279BF / 34,121,191|![Échantillon 2279BF](../../extensibility/ux-guidelines/media/0405_2279bf.png "0405_2279BF")|  
|F12|Désactivé|F12 LtGrey_Disabled|ABABAC / 171,171,172|![Échantillon ABABAC](../../extensibility/ux-guidelines/media/0405_ababac.png "0405_ABABAC")|  
|F12|Placez le curseur en arrière-plan|Placez le curseur bg|D9EBF7 / 217,235,247|![Échantillon D9EBF7](../../extensibility/ux-guidelines/media/0405_d9ebf7.png "0405_D9EBF7")|  
|F12|Arrière-plan enfoncé|Bg enfoncé|B2D7F0 / 178,215,240|![Échantillon B2D7F0](../../extensibility/ux-guidelines/media/0405_b2d7f0.png "0405_B2D7F0")|  
|F12|Plan|VS OUT|F6F6F6 / 246,246,246|![Échantillon F6F6F6](../../extensibility/ux-guidelines/media/0405_f6f6f6.png "0405_F6F6F6")|  
|F12|Information|Information|00BCF2 / 0,188,242|![Échantillon 00BCF2](../../extensibility/ux-guidelines/media/0405_00bcf2.png "0405_00BCF2")|  
|F12|Warning|Warning|F28300 / 242,131,0|![Échantillon F28300](../../extensibility/ux-guidelines/media/0405_f28300.png "0405_F28300")|  
|F12|Erreur / négatif|Error_Negative|E81123 / 232,17,35|![Échantillon E81123](../../extensibility/ux-guidelines/media/0405_e81123.png "0405_E81123")|  
|F12|Démarrer / positif|Start_Positive|009E49 / 0,158,73|![Échantillon 009E49](../../extensibility/ux-guidelines/media/0405_009e49.png "0405_009E49")|  
|F12|Type de saut|Type de saut|9B4F96 / 155,79,150|![Échantillon 9B4F96](../../extensibility/ux-guidelines/media/0405_9b4f96.png "0405_9B4F96")|  
|F12|Interrogation des événements|Interrogation des événements|A51F00 / 165,31,0|![Échantillon A51F00](../../extensibility/ux-guidelines/media/0405_a51f00.png "0405_A51F00")|  
|F12|Marque utilisateur|Marque utilisateur|F16220 / 241,98,32|![Échantillon F16220](../../extensibility/ux-guidelines/media/0405_f16220.png "0405_F16220")|  
  
#### <a name="examples-of-visual-studio-online-icons"></a>Exemples d’icônes de Visual Studio Online  
  
|TFS en ligne||||  
|----------------|-|-|-|  
|![Icône d’équipe TFS en ligne](../../extensibility/ux-guidelines/media/0405-49_tfsonlineteam.png "49_TFSOnlineTeam-0405")<br />Équipe en ligne|![Icône d’information TFS](../../extensibility/ux-guidelines/media/0405-50_tfsinformation.png "50_TFSInformation-0405")<br />Information|![Icône de l’historique TFS](../../extensibility/ux-guidelines/media/0405-51_tfshistory.png "51_TFSHistory-0405")<br />Historique|![Icône de branche TFS](../../extensibility/ux-guidelines/media/0405-52_tfsbranch.png "52_TFSBranch-0405")<br />Branche|  
  
|Napa||||  
|----------|-|-|-|  
|![Icône de contenu Napa](../../extensibility/ux-guidelines/media/0405-53_napacontent.png "53_NapaContent-0405")<br />Contenu|![Icône de courrier office Napa](../../extensibility/ux-guidelines/media/0405-54_napaofficemail.png "54_NapaOfficeMail-0405")<br />Messagerie Office|![Icône Napa SharePoint](../../extensibility/ux-guidelines/media/0405-55_napasharepoint.png "55_NapaSharePoint-0405")<br />SharePoint|![Icône de volet de tâches Napa](../../extensibility/ux-guidelines/media/0405-56_napataskpane.png "56_NapaTaskPane-0405")<br />Volet de tâches|  
  
|Monaco||||  
|------------|-|-|-|  
|![Icône de fichiers Monaco](../../extensibility/ux-guidelines/media/0405-57_monacofiles.png "57_MonacoFiles-0405")<br />Fichiers|![Icône Git Monaco](../../extensibility/ux-guidelines/media/0405-58_monacogit.png "58_MonacoGit-0405")<br />Git|![Icône de recherche Monaco](../../extensibility/ux-guidelines/media/0405-59_monacosearch.png "59_MonacoSearch-0405")<br />Rechercher|![Icône de texte Monaco](../../extensibility/ux-guidelines/media/0405-60_monacotext.png "60_MonacoText-0405")<br />Texte|  
  
|F12|||  
|---------|-|-|  
|![Icône de code automatique F12](../../extensibility/ux-guidelines/media/0405-61_f12prettycode.png "61_F12PrettyCode-0405")<br />Code automatique|![Icône d’avertissement F12](../../extensibility/ux-guidelines/media/0405-62_f12warning.png "62_F12Warning-0405")<br />Warning|![Icône émuler F12](../../extensibility/ux-guidelines/media/0405-63_f12emulate.png "63_F12Emulate-0405")<br />Émuler|