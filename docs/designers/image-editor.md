---
title: éditeur d’images
description: Découvrez comment utiliser l’éditeur d’images de Visual Studio pour afficher et modifier les ressources de texture et d’image utilisées dans le développement d’applications DirectX.
ms.custom: SEO-VS-2020
ms.date: 08/10/2018
ms.topic: conceptual
f1_keywords:
- vs.graphics.designer.imageeditor
- vs.graphics.imageeditor
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bc01e717c30c3f633f3dcd317313452373050539
ms.sourcegitcommit: a731a9454f1fa6bd9a18746d8d62fe2e85e5ddb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2020
ms.locfileid: "93134777"
---
# <a name="image-editor"></a>éditeur d'images

Cet article explique comment utiliser l’ **éditeur d’images** de Visual Studio pour afficher et modifier les ressources de texture et d’image.

Vous pouvez utiliser l’ **éditeur d’images** pour gérer les genres de format enrichi de texture et d’image utilisés dans le développement d’applications DirectX. Cela inclut la prise en charge des formats de fichiers image et des encodages de couleurs répandus, des fonctionnalités telles que les canaux alpha et le mappage MIP, ainsi que de nombreux formats de texture très compressés tirant parti de l’accélération matérielle et pris en charge par DirectX.

## <a name="supported-formats"></a>Formats pris en charge

L’ **éditeur d’images** prend en charge les formats d’image suivants :

|Nom du format|Extension de nom de fichier|
|-----------------| - |
|Format PNG|*.png*|
|JPEG|*.jpg* , *.jpeg* , *.jpe* , *.jfif*|
|Direct Draw Surface|*.dds*|
|Format GIF|*. gif*|
|Bitmap|*.bmp* , *.dib*|
|Format TIFF (Tagged Image File Format)|*. TIF* , *. TIFF*|
|TGA (Targa)|*.tga*|

## <a name="get-started"></a>Bien démarrer

Cette section décrit comment ajouter une image à votre projet Visual Studio et comment la configurer selon vos besoins.

### <a name="add-an-image-to-your-project"></a>Ajouter une image à votre projet

1. Dans **l’Explorateur de solutions** , ouvrez le menu contextuel du projet auquel vous voulez ajouter l’image, puis choisissez **Ajouter** > **Nouvel élément** .

2. Dans la boîte de dialogue **Ajouter un nouvel élément** , sous **Installé** , sélectionnez **Graphiques** , puis sélectionnez un format de fichier approprié pour l’image.

   > [!NOTE]
   > Si vous ne voyez pas la catégorie **Graphisme** dans la boîte de dialogue **Ajouter un nouvel élément** , il peut être nécessaire d’installer le composant **Éditeurs d’images et de modèles 3D** . Fermez la boîte de dialogue, puis sélectionnez **Outils**  >  **afficher les outils et fonctionnalités** dans la barre de menus pour ouvrir la **Visual Studio installer** . Sélectionnez l’onglet **Composants individuels** , puis sélectionnez le composant **Éditeurs d’images et de modèles 3D** sous la catégorie **Jeux et graphismes** . Sélectionnez **Modifier** .
   >
   > ![Composant Éditeurs d’images et de modèles 3D](media/image-3d-model-editors-component.png)

   Pour plus d’informations sur le choix d’un format de fichier en fonction de vos exigences, consultez [Choisir le format d’image](#choose-the-image-format).

3. Spécifiez le **nom** du fichier image et l' **emplacement** où vous souhaitez qu’il soit créé.

4. Choisissez le bouton **Ajouter** .

### <a name="choose-the-image-format"></a>Choisir le format d’image

Selon la façon dont vous prévoyez d’utiliser l’image, certains formats de fichiers peuvent être plus appropriés que d’autres. Par exemple, certains formats risquent de ne pas prendre en charge une fonctionnalité dont vous avez besoin, par exemple la transparence ou un format de couleur spécifique. Certains formats risquent de ne pas fournir une compression adaptée au genre de contenu d’image que vous avez prévu.

Les informations suivantes peuvent vous aider à choisir un format d’image qui répond à vos besoins :

**Image bitmap (.bmp)**

Format de l’image bitmap. Format d’image non compressé qui prend en charge les couleurs sur 24 bits. Le format bitmap ne prend pas en charge la transparence.

**Image GIF (.gif)**

Format d’image GIF (Graphics Interchange Format). Un format d’image compressé LZW sans perte, qui prend en charge jusqu’à 256 couleurs. Inapproprié pour les photographies et les images qui ont une quantité significative de détails en couleurs, mais offre de bons taux de compression pour les images avec peu de couleurs qui présentent un degré élevé de cohérence des couleurs.

**Image JPG (.jpg)**

Format d’image JPEG (Joint Photographic Experts Group). Un format d’image très compressé avec des pertes de données, qui prend en charge les couleurs 24 bits et convient pour la compression générale d’images présentant un degré élevé de cohérence des couleurs.

**Image PNG (.png)**

Format d’image PNG (Portable Network Graphics). Un format d’image modérément compressé sans pertes de données, qui prend en charge les couleurs 24 bits et la transparence alpha. Il convient pour les images naturelles et artificielles, mais n’offre pas un taux de compression aussi bon que les formats avec pertes de données, comme JPG ou GIF.

**Image TIFF (.tif)**

Format d’image TIFF ou TIF (Tagged Image File Format). Un format d’image flexible qui prend en charge plusieurs schémas de compression.

**Texture DDS (.dds)**

Format de texture DDS (DirectDraw Surface). Un format de texture très compressé sans pertes de données, qui prend en charge les couleurs 24 bits et la transparence alpha. Son taux de compression peut atteindre 8:1. Il est basé sur la compression de texture S3, qui peut être décompressée sur le matériel graphique.

**Image TGA (.tga)**

Format d’image TGA (Truevision Graphics Adapter), également appelé Targa. Un format d’image avec compression RLE sans pertes de données, qui prend en charge les images avec mappage des couleurs (palette de couleurs) ou en couleurs directes, avec des couleurs jusqu’à 24 bits et transparence alpha. Inapproprié pour les photographies et les images qui ont une quantité significative de détails en couleurs, mais fournit de bons taux de compression pour les images qui ont de grandes surfaces de couleurs identiques.

### <a name="configure-the-image"></a>Configurer l’image

Avant de commencer à utiliser l’image que vous avez créée, vous pouvez changer sa configuration par défaut. Par exemple, vous pouvez changer ses dimensions ou le format de couleur qu’elle utilise. Pour plus d’informations sur la configuration de ces propriétés et d’autres propriétés de l’image, consultez [Propriétés de l’image](#image-properties).

> [!NOTE]
> Avant d’enregistrer votre travail, veillez à définir la propriété **Format de couleur** si vous voulez utiliser un format spécifique. Si le format de fichier prend en charge la compression, vous pouvez ajuster les paramètres de compression quand vous enregistrez le fichier pour la première fois ou quand vous choisissez **Enregistrer sous** .

## <a name="work-with-the-image-editor"></a>Utiliser l’éditeur d’images

Cette section décrit comment utiliser l' **éditeur d’images** pour modifier des textures et des images.

Les commandes qui affectent l’état de l' **éditeur d’images** se trouvent dans la barre d’outils mode de l’éditeur d' **images** avec les commandes avancées. La barre d’outils se trouve le long du bord supérieur de l’aire de conception de l' **éditeur d’images** . Les outils de dessin se trouvent dans la barre d’outils **éditeur d’images** , le long du bord le plus à gauche de l’aire de conception de l' **éditeur d’images** .

### <a name="image-editor-mode-toolbar"></a>Barre d’outils du mode de l’éditeur d’images

![Barre d’outils du mode de l’éditeur d’images dans Visual Studio](../designers/media/digit-tre-modal-toolbar.png)

Le tableau suivant décrit les éléments de la barre d’outils **Mode de l’éditeur d’images** , listés dans l’ordre où ils apparaissent, de gauche à droite :

|Élément de la barre d'outils|Description|
|------------------|-----------------|
|**Select**|Permet de sélectionner une zone rectangulaire d’une image. Après avoir sélectionné une zone, vous pouvez la couper, la copier, la déplacer, la mettre à l’échelle, la faire pivoter, la retourner ou la supprimer. Quand il existe une sélection active, les outils de dessin affectent seulement la zone sélectionnée.|
|**Sélection irrégulière**|Permet de sélectionner une zone irrégulière d’une image. Après avoir sélectionné une zone, vous pouvez la couper, la copier, la déplacer, la mettre à l’échelle, la faire pivoter, la retourner ou la supprimer. Quand il existe une sélection active, les outils de dessin affectent seulement la zone sélectionnée.|
|**Sélection « Baguette magique »**|Permet de sélectionner une région de couleur similaire dans une image. La *tolérance* , c’est-à-dire la différence maximale entre des couleurs adjacentes pour laquelle elles sont considérées comme similaires, peut être configurée pour inclure une plage plus petite ou plus large de couleurs similaires. Après avoir sélectionné une zone, vous pouvez la couper, la copier, la déplacer, la mettre à l’échelle, la faire pivoter, la retourner ou la supprimer. Quand il existe une sélection active, les outils de dessin affectent seulement la zone sélectionnée.|
|**Panoramique**|Permet de déplacer l’image par rapport au cadre de la fenêtre. En mode **Panoramique** , sélectionnez un point sur l’image et déplacez-le.<br /><br /> Vous pouvez activer temporairement le mode **Panoramique** en appuyant sur la touche **Ctrl** et en la maintenant enfoncée.|
|**Zoom**|Permet l’affichage d’une image avec plus ou moins de détails par rapport au cadre de la fenêtre. En mode **Zoom** , sélectionnez un point dans l’image et déplacez-le vers la droite ou vers le bas pour effectuer un zoom avant, ou vers la gauche ou vers le haut pour effectuer un zoom arrière.<br /><br /> Vous pouvez effectuer un zoom avant ou arrière en maintenant la **touche Ctrl** enfoncée pendant que vous utilisez la roulette de la souris ou en appuyant sur le signe plus ( **+** ) ou le signe moins ( **-** ).|
|**Zoom sur la taille réelle**|Affiche l’image en utilisant une relation 1:1 entre les pixels de l’image et les pixels de l’écran.|
|**Zoom pour ajuster**|Affiche l’image entière dans le cadre de la fenêtre.|
|**Zoom sur la largeur**|Affiche la largeur entière de l’image dans le cadre de la fenêtre.|
|**Grid**|Active ou désactive la grille qui montre les limites des pixels. Il peut être nécessaire de faire un zoom avant pour faire apparaître la grille.|
|**Afficher le niveau MIP suivant**|Active le niveau MIP supérieur suivant dans une chaîne de mappage MIP. Le niveau MIP actif est affiché dans l’aire de conception. Cet élément est disponible seulement pour les textures qui ont des niveaux MIP.|
|**Afficher le niveau MIP précédent**|Active le niveau MIP inférieur dans une chaîne de mappage MIP. Le niveau MIP actif est affiché dans l’aire de conception. Cet élément est disponible seulement pour les textures qui ont des niveaux MIP.|
|**Canal rouge**<br /><br /> **Canal vert**<br /><br /> **Canal bleu**<br /><br /> **Canal alpha**|Active ou désactive le canal de couleur spécifique. **Remarque :** En activant ou en désactivant de façon systématique des canaux de couleur, vous pouvez isoler les problèmes liés à une ou plusieurs de ces couleurs. Par exemple, vous pourrez identifier une transparence alpha incorrecte.|
|**Contexte**|Active ou désactive l’affichage de l’arrière-plan à travers les parties transparentes de l’image. Vous pouvez configurer la façon dont l’arrière-plan s’affiche en choisissant parmi les options suivantes :<br /><br /> **Damier**<br /> Utilise une couleur verte avec la couleur d’arrière-plan spécifiée pour afficher l’arrière-plan sous la forme d’un modèle de damier. Vous pouvez utiliser cette option pour rendre les parties transparentes de l’image plus apparentes.<br /><br /> Arrière-plan blanc<br /> Utilise la couleur blanc pour afficher l’arrière-plan.<br /><br /> Arrière-plan noir<br /> Utilise la couleur noir pour afficher l’arrière-plan.<br /><br /> Animer l’arrière-plan<br /> Permet de déplacer le modèle de damier lentement selon un mouvement panoramique. Vous pouvez utiliser cette option pour rendre les parties transparentes de l’image plus apparentes.|
|**Propriétés**|Affiche ou masque alternativement la fenêtre **Propriétés** .|
|**Avancée**|Contient des commandes et des options supplémentaires.<br /><br /> **Filtres**<br /><br /> Fournit plusieurs filtres d’image courants : **Noir et blanc** , **Flou** , **Éclaircir** , **Obscurcir** , **Détection des bords** , **Relief** , **Inverser les couleurs** , **Ripple** , **Ton sépia** et **Accentuer** .<br /><br /> **Moteurs graphiques**<br /><br /> **Afficher avec D3D11**<br /> Utilise Direct3D 11 pour afficher l’aire de conception de l' **éditeur d’images** .<br /><br /> **Afficher avec D3D11WARP**<br /> Utilise la plateforme de rastérisation avancée Windows (WARP) Direct3D 11 pour afficher l’aire de conception de l' **éditeur d’images** .<br /><br /> **outils**<br /><br /> **Symétrie horizontale**<br /> Transpose l’image autour de son axe horizontal (l’axe X).<br /><br /> **Symétrie verticale**<br /> Transpose l’image autour de son axe vertical (l’axe Y).<br /><br /> **Générer des mips**<br /> Génère des niveaux MIP pour une image. Si des niveaux MIP existent déjà, ils sont recréés à partir du niveau MIP le plus grand. Toutes les modifications qui ont été apportées à des niveaux MIP plus petits sont perdues. Pour enregistrer les niveaux MIP que vous avez générés, vous devez utiliser le format *.dds* pour enregistrer l’image.<br /><br /> **Visualiser**<br /><br /> **Fréquence d’images**<br /> Quand cette option est activée, elle affiche la fréquence d’images dans le coin supérieur droit de l’aire de conception. La fréquence d'images est le nombre d'images dessinées par seconde. **Conseil :** Vous pouvez choisir le bouton **Avancé** pour réexécuter la dernière commande.|

### <a name="image-editor-toolbar"></a>Barre d'outils Éditeur d'images

![Barre d'outils Éditeur d'images](../designers/media/digit-tre-toolbar.png)

Le tableau suivant décrit les éléments de la barre d’outils de l' **éditeur d’images** , qui sont répertoriés dans l’ordre dans lequel ils apparaissent de haut en bas :

|Élément de la barre d'outils|Description|
|------------------|-----------------|
|**Crayon**|Utilise la sélection de couleur active pour dessiner un trait sans lissage. Vous pouvez définir la couleur et l’épaisseur du trait dans la fenêtre **Propriétés** .|
|**Brush**|Utilise la sélection de couleur active pour dessiner un trait avec lissage. Vous pouvez définir la couleur et l’épaisseur du trait dans la fenêtre **Propriétés** .|
|**Aérographe**|Utilise la sélection active de couleur pour dessiner un trait avec lissage qui fusionne avec l’image et devient plus saturé en fonction du temps. Vous pouvez définir la couleur et l’épaisseur du trait dans la fenêtre **Propriétés** .|
|**Eyedropper**|Définit la sélection de couleur active sur la couleur du pixel sélectionné.|
|**Fill**|Utilise la sélection de couleur active pour remplir une zone de l’image. La zone affectée est définie comme le pixel où le remplissage est appliqué, ainsi que chaque pixel qui y est connecté par des pixels de la même couleur et qui est lui-même de la même couleur. Si le remplissage est appliqué dans une sélection active, la zone affectée est limitée par la sélection.<br /><br /> Par défaut, la sélection de couleur active est fusionnée avec la zone affectée de l’image en fonction de son composant alpha. Pour utiliser la sélection de couleur active afin de remplacer la zone affectée, appuyez sur la touche **MAJ** et maintenez-la enfoncée lorsque vous utilisez l’outil remplissage.|
|**Gomme**|Applique aux pixels la couleur entièrement transparente si l’image prend en charge un canal alpha. Sinon, applique aux pixels la couleur d’arrière-plan active.|
|**Ligne** , **Rectangle** , **Rectangle à coins arrondis** , **Ellipse**|Dessine une forme sur l’image. Vous pouvez définir la couleur et l’épaisseur du contour dans la fenêtre **Propriétés** .<br /><br /> Pour dessiner une primitive de largeur et de hauteur identiques, maintenez la touche **Maj** enfoncée pendant que vous dessinez.|
|**Text**|Utilise la sélection de couleur de premier plan pour dessiner du texte. La couleur d’arrière-plan est déterminée par la sélection de couleur d’arrière-plan. Pour un arrière-plan transparent, la valeur alpha de la sélection de couleur d’arrière-plan doit être 0. Quand la zone de texte est active, vous pouvez définir si le texte est dessiné avec un trait avec lissage, et vous pouvez définir la **Valeur** , la **Police** , la **Taille** et le style ( **Gras** , **Italique** ou **Souligné** ) du texte dans la fenêtre **Propriétés** . Le contenu et l’apparence du texte sont finalisés une fois que la zone de texte n’est plus active.|
|**Faire pivoter**|Fait pivoter l’image de 90 degrés dans le sens des aiguilles d’une montre.|
|**Trim**|Découpe l’image au format de la sélection active.|

### <a name="work-with-mip-levels"></a>Utiliser les niveaux MIP

Certains formats d’image, par exemple DirectDraw Surface ( *.dds* ), prennent en charge les niveaux MIP pour le niveau de détail de l’espace de texture. Pour plus d’informations sur la génération et l’utilisation des niveaux MIP, consultez [procédure : créer et modifier des niveaux MIP](../designers/how-to-create-and-modify-mip-levels.md)

### <a name="work-with-transparency"></a>Utiliser la transparence

Certains formats d’image, par exemple DirectDraw Surface ( *.dds* ), prennent en charge la transparence. Vous pouvez utiliser la transparence de plusieurs manières, en fonction de l’outil que vous utilisez. Pour spécifier le niveau de transparence pour une sélection de couleur, dans la fenêtre **Propriétés** , configurez le composant **A** (alpha) de la sélection de couleur.

Le tableau suivant indique comment les différents genres d’outil contrôlent l’application de la transparence :

|Outil|Description|
|----------|-----------------|
|**Crayon** , **Pinceau** , **Aérographe** , **Ligne** , **Rectangle** , **Rectangle à coins arrondis** , **Ellipse** , **Texte**|Pour fusionner la sélection de couleur active avec l’image, dans la fenêtre **Propriétés** , développez le groupe de propriétés **Canaux** , cochez la case **Dessiner** sur le canal **Alpha** puis dessinez normalement.<br /><br /> Pour dessiner en utilisant la sélection de couleur active et laisser telle quelle la valeur alpha de l’image, décochez la case **Dessiner** du canal **Alpha** puis dessinez normalement.|
|**Fill**|Pour fusionner la sélection de couleur active avec l’image, choisissez simplement la zone à remplir.<br /><br /> Pour utiliser la sélection de couleur active, y compris la valeur du canal alpha, pour remplacer l’image, appuyez et maintenez la **touche Maj** enfoncée, puis choisissez la zone à remplir.|

### <a name="image-properties"></a>Propriétés de l’image

Vous pouvez utiliser la fenêtre **Propriétés** pour spécifier différentes propriétés de l’image. Par exemple, vous pouvez définir les propriétés de largeur et de hauteur pour redimensionner l’image.

Le tableau suivant décrit les propriétés d’une image :

|Propriété|Description|
|--------------|-----------------|
|Largeur|Largeur de l’image.|
|Hauteur|Hauteur de l’image.|
|Bits par pixel|Nombre de bits qui représentent chaque pixel. La valeur de cette propriété dépend du **Format de couleur** de l’image.|
|Sélection transparente|**Vrai** pour fusionner la couche de la sélection avec l’image principale, en fonction de la valeur alpha de la couche de la sélection ; sinon, **Faux** . Cet élément est disponible seulement pour les images qui prennent en charge alpha.|
|Format|Format de couleur de l’image. Vous pouvez spécifier différents formats de couleur en fonction du format de l’image. Le format de couleur définit le nombre et le type des canaux de couleur qui sont inclus dans l’image, ainsi que la taille et de codage des différents canaux.|
|Niveau MIP|Niveau MIP actif. Cet élément est disponible seulement pour les textures qui ont des niveaux MIP.|
|Nombre de niveaux mip|Nombre total de niveaux MIP dans l’image. Cet élément est disponible seulement pour les textures qui ont des niveaux MIP.|
|Nombre de frames|Nombre total de trames dans l’image. Cet élément est disponible seulement pour les images qui prennent en charge les tableaux de textures.|
|Frame|Trame en cours. Seule la première trame peut être visualisée. Toutes les autres trames sont perdues quand l’image est enregistrée.|
|Nombre de secteurs de profondeur|Nombre total de secteurs de profondeur dans l’image. Cet élément est disponible seulement pour les images qui prennent en charge les textures de volume.|
|Secteur de profondeur|Secteur de profondeur actif. Seul le premier secteur peut être visualisé. Tous les autres secteurs sont perdus quand vous enregistrez l’image.|

> [!NOTE]
> Comme la propriété **Faire pivoter de** s’applique à tous les outils et à toutes les zones sélectionnées, elle apparaît toujours en bas de la fenêtre **Propriétés** en même temps que d’autres propriétés de l’outil. **Faire pivoter de** est toujours affiché, car l’image entière est implicitement sélectionnée quand il n’existe aucune autre sélection ou outil actif. Pour plus d’informations sur la propriété **pivoter par** , consultez Propriétés de l' [outil](#tool -properties).

### <a name="resize-images"></a>Redimensionner les images

Il existe deux façons de redimensionner une image. Dans les deux cas, l' **éditeur d’images** utilise l’interpolation bilinéaire pour rééchantillonner l’image.

- Dans la fenêtre **Propriétés** , spécifiez de nouvelles valeurs pour les propriétés **Largeur** et **Hauteur** .

- Sélectionnez l’image entière et utilisez les marqueurs de bordure pour redimensionner l’image.

### <a name="selected-regions"></a>Zones concernées

Les sélections effectuées dans l’ **éditeur d’images** définissent les régions actives de l’image. Les régions actives sont affectées par les outils et les transformations. Quand il existe une sélection active, les zones situées en dehors de la zone sélectionnée ne sont pas affectées par la plupart des outils et des transformations. S’il n’existe pas de sélection active, c’est l’image entière qui est active.

La plupart des outils ( **Crayon** , **Pinceau** , **Aérographe** , **Remplissage** , **Gomme** et les primitives 2D), ainsi que les transformations ( **Pivoter** , **Découper** , **Inverser les couleurs** , **Symétrie horizontale** et **Symétrie verticale** ) sont limités ou définis par la sélection active. Toutefois, certains outils ( **Compte-gouttes** et **Texte** ), ainsi que certaines transformations ( **Générer des mips** ) ne sont pas affectés par une sélection active. Ces outils se comportent toujours comme si l’image entière était la sélection active.

Quand vous sélectionnez une région, vous pouvez appuyer de façon prolongée sur la touche **Maj** pour effectuer une sélection proportionnelle (carrée). Sinon, la sélection n’est pas limitée.

#### <a name="resize-selections"></a>Redimensionner des sélections

Une fois que vous avez sélectionné une zone, vous pouvez redimensionner celle-ci ou l’image qu’elle contient en changeant la taille du marqueur de sélection. Quand vous redimensionnez la région sélectionnée, vous pouvez utiliser les touches de modification suivantes pour changer le comportement de la région sélectionnée :

**Ctrl** - Copie le contenu de la région sélectionnée avant son redimensionnement. Ceci laisse l’image d’origine intacte, alors que la copie est redimensionnée.

**Maj** - Redimensionne la région sélectionnée proportionnellement à sa taille d’origine.

**Alt** - Change la taille de la région sélectionnée. Ceci laisse l’image non modifiée.

Le tableau suivant décrit les combinaisons de touches de modification valides :

|Ctrl|Maj|Alt|Description|
|----------|-----------|---------|-----------------|
||||Redimensionne le contenu de la zone sélectionnée.|
||**Majuscule**||Redimensionne proportionnellement le contenu de la zone sélectionnée.|
|||**Appuyez**|Redimensionne la zone sélectionnée. Ceci définit une nouvelle zone de sélection.|
||**Majuscule**|**Appuyez**|Redimensionne proportionnellement la zone sélectionnée. Ceci définit une nouvelle zone de sélection.|
|**Clavier**|||Copie et redimensionne le contenu de la zone sélectionnée.|
|**Clavier**|**Majuscule**||Copie puis redimensionne proportionnellement le contenu de la zone sélectionnée.|

### <a name="tool-properties"></a>Propriétés des outils

Quand un outil est sélectionné, vous pouvez utiliser la fenêtre **Propriétés** pour spécifier des détails sur la façon dont il affecte l’image. Par exemple, vous pouvez définir l’épaisseur de l’outil **Crayon** ou la couleur de l’outil **Pinceau** .

Vous pouvez définir une couleur de premier plan et une couleur d’arrière-plan. Les deux prennent en charge un canal alpha pour fournir une opacité définie par l’utilisateur. Les paramètres s’appliquent à tous les outils. Si vous utilisez une souris, le bouton gauche de la souris correspond à la couleur de premier plan, et le bouton droit de la souris correspond à la couleur d’arrière-plan.

Le tableau suivant décrit les propriétés des outils :

|Outil|Propriétés|
|----------|----------------|
|Tous les outils et toutes les sélections|**Faire pivoter de**<br /> Définit la quantité de la rotation, en degrés, pour la sélection ou l’effet de l’outil dans le sens des aiguilles d’une montre.|
|**Crayon** , **Pinceau** , **Aérographe** , **Gomme**|**Thickness**<br /> Définit la taille de la zone affectée par l’outil.|
|**Text**|**Anticrénelage**<br /> Dessine du texte avec des contours lissés. Le texte a ainsi un aspect plus lisse.<br /><br /> **Valeur**<br /> Texte à dessiner.<br /><br /> **Police**<br /> Police utilisée pour dessiner le texte.<br /><br /> **Taille**<br /> Taille du texte.<br /><br /> **Gras**<br /> Met la police en gras.<br /><br /> **Italique**<br /> Met la police en italique.<br /><br /> **Souligné**<br /> Met la police en souligné.|
|**Primitive 2D**|**Anticrénelage**<br /> Dessine les primitives avec des contours lissés. Ceci leur donne une apparence plus lisse.<br /><br /> **Thickness**<br /> Définit l’épaisseur de la ligne qui constitue la limite de la primitive.<br /><br /> **Rayon X**<br /> (Rectangle à coins arrondis uniquement) Définit le rayon de l’arrondi pour les bords supérieur et inférieur de la primitive.<br /><br /> **Rayon Y**<br /> (Rectangle à coins arrondis uniquement) Définit le rayon de l’arrondi pour les bords gauche et droit de la primitive.|
|**Crayon** , **Pinceau** , **Aérographe** , **Primitive 2D**|**Canaux**<br /> Active ou désactive des canaux de couleur spécifiques pour l’affichage et le dessin. Si **Afficher** est défini pour un canal de couleur spécifique, ce canal est visible dans l’image ; sinon, il n’est pas visible. Si **Dessiner** est défini pour un canal de couleur spécifique, ce canal est affecté par les opérations de dessin ; sinon, il ne l’est pas.|
|**Sélection « Baguette magique »** , **Remplissage**|**Seuil**<br /> Définit la différence maximale entre des couleurs adjacentes, selon laquelle elles sont considérées comme similaires, de sorte que plus ou moins de couleurs similaires font partie de la zone affectée ou sélectionnée. Par défaut, la valeur est 32, ce qui signifie que les pixels adjacents dans 32 nuances (plus claires ou plus sombres) de la couleur d’origine sont considérés comme faisant partie de la zone.|

## <a name="keyboard-shortcuts"></a>Raccourcis clavier

|Commande|Raccourcis clavier|
|-------------| - |
|Passer en mode **Sélection**|**S**|
|Passer en mode **Zoom**|**Z**|
|Passer en mode **Panoramique**|**K**|
|Sélectionner tout|**CTRL** + **Un**|
|Supprimer la sélection actuelle|**Supprimer**|
|Annuler la sélection actuelle|**Échap** (échappement)|
|Faire un zoom avant|**CTRL** + **Roulette de la souris vers l’avant**<br /><br /> **CTRL** + **PG PRÉC**<br /><br /> Signe plus ( **+** )|
|Faire un zoom arrière|**CTRL** - **Roulette de la souris** vers l’arrière<br /><br /> **CTRL** - **PG SUIV**<br /><br /> Signe moins ( **-** )|
|Panoramique de l’image vers le haut|**Roulette de la souris vers l’arrière**<br /><br /> **Pg suiv**|
|Panoramique de l’image vers le bas|**Roulette de la souris vers l’avant**<br /><br /> **Pg préc**|
|Panoramique de l’image vers la gauche|**MAJ** + **Roulette de la souris** vers l’arrière<br /><br /> **Roulette de la souris vers la gauche**<br /><br /> **MAJ** + **PG SUIV**|
|Panoramique de l’image vers la droite|**MAJ** + **Roulette de la souris vers l’avant**<br /><br /> **Roulette de la souris vers la droite**<br /><br /> **MAJ** + **PG PRÉC**|
|Zoom sur la taille réelle|**CTRL** + **0** (zéro)|
|Adapter l’image à la fenêtre|**CTRL** + **G** , **CTRL** + **F**|
|Adapter l’image à la largeur de la fenêtre|**CTRL** + **G** , **CTRL** + **I**|
|Activer/désactiver la grille|**CTRL** + **G** , **CTRL** + **g**|
|Rogner l’image pour l’adapter à la sélection actuelle|**CTRL** + **G** , **CTRL** + **C**|
|Afficher le niveau MIP suivant (plus de détails)|**CTRL** + **G** , **CTRL** + **6**|
|Afficher le niveau MIP précédent (moins de détails)|**CTRL** + **G** , **CTRL** + **7**|
|Activer/désactiver le canal rouge|**CTRL** + **G** , **CTRL** + **1**|
|Activer/désactiver le canal vert|**CTRL** + **G** , **CTRL** + **2**|
|Activer/désactiver le canal bleu|**CTRL** + **G** , **CTRL** + **3**|
|Activer/désactiver le canal alpha (transparence)|**CTRL** + **G** , **CTRL** + **4**|
|Activer/désactiver le modèle de damier alpha|**CTRL** + **G** , **CTRL** + **B**|
|Passer à l’outil Sélection irrégulière|**L**|
|Passer à l’outil Baguette magique|**M**|
|Passer à l’outil Crayon|**P**|
|Passer à l’outil Pinceau|**B**|
|Passer à l’outil Remplissage|**F**|
|Passer à l’outil Gomme|**E**|
|Passer à l’outil Texte|**T**|
|Passer à l’outil de sélection de couleur (Pipette)|**I**|
|Déplacer la sélection active et son contenu.|Touches de **direction** .|
|Redimensionner la sélection active et son contenu.|**CTRL** + Touches de **direction**|
|Déplacer la sélection active mais pas son contenu.|**MAJ** + Touches de **direction**|
|Redimensionner la sélection active mais pas son contenu.|**MAJ** + **CTRL** + Touches de **direction**|
|Valider la couche actuelle|**Renvoi**|
|Diminuer l’épaisseur de l’outil|**[**|
|Augmenter l’épaisseur de l’outil|**]**|

## <a name="related-topics"></a>Rubriques connexes

|Titre|Description|
|-----------|-----------------|
|[Utilisation des ressources 3D pour les jeux et les applications](../designers/working-with-3-d-assets-for-games-and-apps.md)|Fournit une vue d’ensemble des outils que vous pouvez utiliser dans Visual Studio pour travailler sur des composants graphiques, comme des textures et des images, des modèles 3D et des effets de nuanceur.|
|[Éditeur de modèle](../designers/model-editor.md)|Décrit comment utiliser l’éditeur de modèle Visual Studio pour travailler avec des modèles 3D.|
|[Concepteur Shader](../designers/shader-designer.md)|Explique comment utiliser le concepteur Shader de Visual Studio pour travailler avec des nuanceurs.|
