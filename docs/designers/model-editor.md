---
title: Éditeur de modèle
description: Apprenez à utiliser l’éditeur de modèle Visual Studio pour afficher, créer et modifier des modèles 3D à partir de modèles 3D de toutes pièces ou plus complexes créés par des outils de modélisation.
ms.custom: SEO-VS-2020
ms.date: 04/12/2018
ms.topic: conceptual
f1_keywords:
- vs.graphics.designer.3dscene
- vs.graphics.modelviewer
ms.assetid: 5edf1a30-9307-43c3-9b8b-831217be0104
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d9a9ccebb82c9a47ca1ea5ab780a033870316cd8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99904198"
---
# <a name="model-editor"></a>Éditeur de modèle

Ce document explique comment utiliser l' **éditeur de modèle** Visual Studio pour afficher, créer et modifier des modèles 3D.

Vous pouvez utiliser **l’Éditeur de modèle** pour créer des modèles 3D de base à partir de zéro, ou pour afficher et modifier des modèles 3D plus complexes, créés à l’aide d’outils de modélisation 3D riches en fonctionnalités.

## <a name="supported-formats"></a>Formats pris en charge

L' **éditeur de modèle** prend en charge plusieurs formats de modèle 3D qui sont utilisés dans le développement d’applications DirectX :

|Nom de format|Extension de fichier|Opérations prises en charge (Afficher, Modifier, Créer)|
|-----------------| - | - |
|Fichier d'échange AutoDesk FBX|*. FBX*|Afficher, Modifier, Créer|
|Fichier Collada DAE|*.dae*|Afficher, Modifier (Les modifications apportées aux fichiers Collada DAE sont enregistrées au format FBX.)|
|Fichier OBJ|*. obj*|Afficher, Modifier (Les modifications apportées aux fichiers OBJ sont enregistrées au format FBX.)|

## <a name="get-started"></a>Commencer

Cette section explique comment ajouter un modèle 3D à un projet C++ Visual Studio et donne d’autres informations de base pour commencer.

> [!NOTE]
> L’intégration de la génération automatique d’éléments graphiques comme les scènes 3D (fichiers .fbx) n’est prise en charge que pour les projets C++.

### <a name="to-add-a-3d-model-to-your-project"></a>Pour ajouter un modèle 3D à votre projet

1. Vérifiez que le composant Visual Studio dont vous avez besoin pour travailler avec les graphismes est installé. Il s’appelle **Éditeurs d’images et de modèles 3D**.

   Pour l’installer, ouvrez Visual Studio installer en sélectionnant **Outils**  >  **afficher les outils et fonctionnalités** dans la barre de menus, puis sélectionnez l’onglet **composants individuels** . Sélectionnez le composant **éditeurs d’images et de modèles 3D** sous la catégorie **jeux et graphismes** , puis sélectionnez **modifier**.

   ![Composant Éditeurs d’images et de modèles 3D](media/image-3d-model-editors-component.png)

   L’installation du composant commence.

2. Dans **l’Explorateur de solutions**, ouvrez le menu contextuel du projet C++ auquel vous voulez ajouter l’image, puis choisissez **Ajouter** > **Nouvel élément**.

3. Dans la boîte de dialogue **Ajouter un nouvel élément**, sous la catégorie **Graphisme**, sélectionnez **Scène 3D (.fbx)**.

   ![Boîte de dialogue Ajouter un nouvel élément avec une scène 3D sélectionnée](media/add-new-3d-scene.png)

   > [!NOTE]
   > Si la catégorie **Graphismes** n’apparaît pas dans la boîte de dialogue **Ajouter un nouvel élément** alors que le composant **Éditeurs d’images et de modèles 3D** est installé, cela signifie que les éléments graphiques ne sont pas pris en charge pour votre type de projet.

4. Entrez le **Nom** du fichier de modèle, puis sélectionnez **Ajouter**.

### <a name="axis-orientation"></a>Orientation d'axe

Visual Studio prend en charge chaque orientation de l’axe 3D et charge les informations d’orientation d’axe à partir des formats de fichier de modèle qui les prennent en charge. Si aucune orientation d’axe n’est spécifiée, Visual Studio utilise le système de coordonnées droitier par défaut. **L’indicateur d’axe** montre l’orientation d’axe actuelle dans le coin inférieur droit de l’aire de conception. Dans **l’indicateur d’axe**, le rouge représente l’axe x, le vert représente l’axe y et le bleu représente l’axe z.

### <a name="begin-your-3d-model"></a>Commencer votre modèle 3D

Dans l’éditeur de modèle, chaque nouvel objet commence toujours comme l’une des formes 3D de base (ou *primitives*) intégrées à l’éditeur de modèle. Pour créer des objets nouveaux uniques, vous devez ajouter une primitive à la scène, puis modifier sa forme en modifiant ses sommets. Pour des formes complexes, vous pouvez ajouter des sommets en utilisant l'extrusion ou la subdivision, puis les modifier. Pour plus d’informations sur la façon d’ajouter un objet primitif à votre scène, consultez [Créer et importer des objets 3D](#Adding3DObjects). Pour plus d’informations sur la façon d’ajouter des sommets à un objet, consultez [Modifier des objets](#ModifyingObjects).

## <a name="work-with-the-model-editor"></a>Utilisation de l’éditeur de modèle

Les sections suivantes expliquent comment l’éditeur de modèle pour travailler avec des modèles 3D.

### <a name="model-editor-toolbars"></a>Barres d'outils de l'éditeur de modèle

Les barres d’outils de l’éditeur de modèle contiennent des commandes qui vous aident à utiliser les modèles 3D.

Les commandes qui affectent l’état de l’éditeur de modèle se trouvent dans la barre d’outils **Mode de l’éditeur de modèle**, dans la fenêtre principale de Visual Studio. Les outils de modélisation et les commandes scriptées se trouvent dans la barre d’outils **Éditeur de modèle** dans l’aire de conception de l’éditeur de modèle.

Voici la barre d’outils **Mode de l’éditeur de modèle** :

![Barre d'outils modale de la visionneuse de modèles.](../designers/media/digit-mre-modal-toolbar.png)

Le tableau ci-dessous décrit les éléments de la barre d’outils **Mode de l’éditeur de modèle**, répertoriés dans l’ordre où ils figurent, de gauche à droite.

|Élément de la barre d'outils|Description|
|------------------|-----------------|
|**Select**|Permet de sélectionner des points, des arêtes, des faces ou des objets dans la scène, en fonction du mode de sélection actif.|
|**Panoramique**|Permet de déplacer une scène 3D par rapport au cadre de la fenêtre. Pour effectuer un mouvement panoramique, sélectionnez un point dans la scène et déplacez-le.<br /><br /> En mode **sélection** , vous pouvez appuyer sur la **touche Ctrl** et la maintenir enfoncée pour activer temporairement le mode **panoramique** .|
|**Zoom**|Permet l'affichage d'une scène avec plus ou moins de détails par rapport au cadre de la fenêtre. En mode **Zoom**, sélectionnez un point dans la scène et déplacez-le vers la droite ou le bas pour effectuer un zoom avant, ou vers la gauche ou le haut pour effectuer un zoom arrière.<br /><br /> En mode **sélection** , vous pouvez effectuer un zoom avant ou arrière à l’aide de la roulette de la souris tout en maintenant la **touche Ctrl** enfoncée.|
|**Orbite**|Positionne la vue sur un chemin circulaire autour de l'objet sélectionné. Si aucun objet n'est sélectionné, le chemin est centré sur l'origine de la scène. **Remarque :** Ce mode n’a aucun effet quand la projection **Orthographique** est activée.|
|**Locale universelle**|Lorsque cet élément est activé, les transformations appliquées à l'objet sélectionné se produisent dans l'espace universel. Sinon, les transformations appliquées à l'objet sélectionné se produisent dans l'espace local.|
|**Mode pivot**|Lorsque cet élément est activé, les transformations affectent l’emplacement et l’orientation du *point pivot* de l’objet sélectionné (le point pivot définit le Centre des opérations de translation, de mise à l’échelle et de rotation.) Sinon, les transformations affectent l’emplacement et l’orientation de la géométrie de l’objet, par rapport au point pivot.|
|**Verrouiller l'axe X**|Limite la manipulation des objets à l'axe X. S'applique uniquement lorsque vous utilisez la partie centrale du widget du manipulateur.|
|**Verrouiller l’axe Y**|Limite la manipulation des objets à l'axe Y. S'applique uniquement lorsque vous utilisez la partie centrale du widget du manipulateur.|
|**Verrouiller l’axe Z**|Limite la manipulation des objets à l'axe Z. S'applique uniquement lorsque vous utilisez la partie centrale du widget du manipulateur.|
|**Cadrer sur l’objet**|Cadre la vue sur l'objet sélectionné afin qu'il se trouve au centre de la vue.|
|**Visualiser**|Définit l'orientation de la vue. Les orientations possibles sont les suivantes :<br /><br /> **Front**<br /> Positionne la vue en face de la scène.<br /><br /> **Précédent**<br /> Positionne la vue derrière la scène.<br /><br /> **Left**<br /> Positionne la vue à gauche de la scène.<br /><br /> **Right**<br /> Positionne la vue à droite de la scène.<br /><br /> **Top**<br /> Positionne la vue au-dessus de la scène.<br /><br /> **Bas**<br /> Positionne la vue au-dessous de la scène. **Remarque :** Il s’agit de la seule façon de modifier la direction de la vue quand la projection **Orthographique** est activée.|
|**Projection**|Définit le type de projection utilisé pour dessiner la scène. Les projections possibles sont les suivantes :<br /><br /> **Perspective**<br /> Dans la projection en perspective, les objets éloignés du point de vue apparaissent de taille réduite et convergent finalement vers un point à l'horizon.<br /><br /> **Orthographique**<br /> Dans la projection orthographique, les objets apparaissent de même taille, quelle que soit leur distance par rapport au point de vue. Aucune convergence n'est affichée. Quand la projection **Orthographique** est activée, vous ne pouvez pas utiliser le mode **Orbite** pour positionner la vue.|
|**Style de dessin**|Définit la façon dont les objets de la scène sont affichés. Les styles disponibles sont les suivants :<br /><br /> **Maquette**<br /> Si cette option est activée, les objets sont affichés sous forme de maquettes.<br /><br /> **Superposer**<br /> Si cette option est activée, les objets sont affichés au moyen d'une fusion additive. Vous pouvez l'utiliser pour visualiser le degré de superposition obtenu dans la scène.<br /><br /> **Ombrage constant**<br /> Si cette option est activée, les objets sont affichés à l'aide d'un modèle d'éclairage élémentaire à ombrage constant. Vous pouvez l'utiliser pour afficher les faces d'un objet plus facilement.<br /><br /> Si aucune de ces options n'est activée, chaque objet est affiché en fonction du matériau qui lui est appliqué.|
|**Mode de rendu en temps réel**|Quand le rendu en temps réel est activé, Visual Studio redessine l’aire de conception, même quand aucune action utilisateur n’est effectuée. Ce mode est utile lorsque vous travaillez avec des nuanceurs qui évoluent avec le temps.|
|**Activer/Désactiver la grille**|Lorsque cet élément est activé, une grille s'affiche. Dans le cas contraire, la grille ne s'affiche pas.|
|**Boîte à outils**|Affiche ou masque la **Boîte à outils**.|
|**Structure du document**|Affiche ou masque la fenêtre **Structure du document**.|
|**Propriétés**|Affiche ou masque la fenêtre **Propriétés**.|
|**Avancée**|Contient des commandes et des options avancées.<br /><br /> **Moteurs graphiques**<br /><br /> **Afficher avec D3D11**<br /> Utilise Direct3D 11 pour afficher l'aire de conception de l'éditeur de modèle.<br /><br /> **Afficher avec D3D11WARP**<br /> Utilise la plateforme WARP (Windows Advanced Rasterization Platform) Direct3D 11 pour afficher l'aire de conception de l'éditeur de modèle.<br /><br /> **Gestion des scènes**<br /><br /> **Importer**<br /> Importe des objets dans la scène actuelle depuis un autre fichier de modèle 3D.<br /><br /> **Attacher au parent**<br /> Définit le premier objet parmi les objets sélectionnés comme parent des autres objets sélectionnés.<br /><br /> **Détacher du parent**<br /> Détache l'objet sélectionné de son parent. L’objet sélectionné devient un *objet racine* dans la scène. Un objet racine ne possède pas d'objet parent.<br /><br /> **Créer un groupe**<br /> Regroupe les objets sélectionnés en tant qu'objets frères.<br /><br /> **Fusionner les objets**<br /> Associe les objets sélectionnés en un seul objet.<br /><br /> **Créer un objet à partir de la sélection de polygones**<br /> Supprime les faces sélectionnées à partir de l'objet actif et ajoute à la scène un nouvel objet qui contient ces faces.<br /><br /> **outils**<br /><br /> **Retourner l’enroulement de polygone**<br /> Retourne les polygones sélectionnés afin que l'ordre d'enroulement et la normale de surface soient inversés.<br /><br /> **Supprimer toutes les animations**<br /> Supprime les données d'animation des objets.<br /><br /> **Effectuer une triangulation**<br /> Convertit l'objet sélectionné en triangles.<br /><br /> **Visualiser**<br /><br /> Élimination face arrière<br /> Active ou désactive l'élimination face arrière.<br /><br /> **Fréquence d’images**<br /> Affiche la fréquence d'images dans l'angle supérieur droit de l'aire de conception. La fréquence d'images est le nombre d'images dessinées par seconde.<br /><br /> Cette option est utile lorsque vous activez l’option **Mode de rendu en temps réel**.<br /><br /> **Afficher tout**<br /> Affiche tous les objets de la scène. Réinitialise la propriété **Masqué** de chaque objet sur **False**.<br /><br /> **Afficher les normales de face**<br /> Affiche la normale de chaque face.<br /><br /> **Afficher les matériaux manquants**<br /> Affiche une texture spéciale sur les objets auxquels aucun matériau n'est assigné.<br /><br /> **Afficher le pivot**<br /> Active ou désactive l’affichage d’un marqueur d’axe 3D au point pivot de la sélection active.<br /><br /> **Afficher les nœuds d’espace réservé**<br /> Affiche les nœuds d'espace réservé. Un nœud d'espace réservé est créé lorsque vous regroupez des objets.<br /><br /> **Afficher les normales des sommets**<br /> Affiche la normale de chaque sommet. **Conseil :** Vous pouvez choisir le bouton **Scripts** pour réexécuter le dernier script.|

Voici la barre d’outils **Éditeur de modèle** :

![Barre d'outils de la visionneuse de modèles](../designers/media/digit-mre-toolbar.png)

Le prochain tableau décrit les éléments de la barre d’outils **Éditeur de modèle**, répertoriés dans l’ordre où ils figurent, de haut en bas.

|Élément de la barre d'outils|Description|
|------------------|-----------------|
|**Translate**|Déplace la sélection.|
|**Mettre à l'échelle**|Modifie la taille de la sélection.|
|**Faire pivoter**|Fait pivoter la sélection.|
|**Sélectionner le point**|Définit le **Mode de sélection** pour sélectionner des points spécifiques sur un objet.|
|**Sélectionner un bord**|Définit le **Mode de sélection** pour sélectionner une arête (segment reliant deux sommets) sur un objet.|
|**Sélectionner la face**|Définit le **Mode de sélection** pour sélectionner une face d’un objet.|
|**Sélectionner un objet**|Définit le **Mode de sélection** pour sélectionner un objet entier.|
|**Extruder**|Crée une face supplémentaire et la connecte à la face sélectionnée.|
|**Subdiviser**|Divise chaque face sélectionnée en plusieurs faces. Pour créer de nouvelles faces, de nouveaux sommets sont ajoutés (un au centre de la face d'origine et l'autre au milieu de chaque arête), puis joints aux sommets d'origine. Le nombre de faces ajoutées est égal au nombre d'arêtes de la face d'origine.|

### <a name="control-the-view"></a>Contrôler la vue

La scène 3D est affichée en fonction de la vue, qui peut être considérée comme une caméra virtuelle qui a une position et une orientation. Pour modifier la position et l’orientation, utilisez les contrôles d’affichage de la barre d’outils **Mode de l’éditeur de modèle**.

Le tableau ci-dessous décrit les principaux contrôles d'affichage.

|Contrôle d'affichage|Description|
|------------------|-----------------|
|**Panoramique**|Permet de déplacer une scène 3D par rapport au cadre de la fenêtre. Pour effectuer un mouvement panoramique, sélectionnez un point dans la scène et déplacez-le.<br /><br /> En mode **sélection** , vous pouvez appuyer sur la **touche Ctrl** et la maintenir enfoncée pour activer temporairement le mode **panoramique** .|
|**Zoom**|Permet l'affichage d'une scène avec plus ou moins de détails par rapport au cadre de la fenêtre. En mode **Zoom**, sélectionnez un point dans la scène et déplacez-le vers la droite ou le bas pour effectuer un zoom avant, ou vers la gauche ou le haut pour effectuer un zoom arrière.<br /><br /> En mode **sélection** , vous pouvez effectuer un zoom avant ou arrière à l’aide de la roulette de la souris tout en maintenant la **touche Ctrl** enfoncée.|
|**Orbite**|Positionne la vue sur un chemin circulaire autour de l'objet sélectionné. Si aucun objet n'est sélectionné, le chemin est centré sur l'origine de la scène. **Remarque :** Ce mode n’a aucun effet quand la projection **Orthographique** est activée.|
|**Cadrer sur l’objet**|Cadre la vue sur l'objet sélectionné afin qu'il se trouve au centre de la vue.|

La vue est générée par la caméra virtuelle, mais elle est également définie par une projection. La projection définit la façon dont les formes et les objets de la vue sont traduits en pixels sur l'aire de conception. Dans la barre d’outils **Éditeur de modèle**, vous pouvez choisir une projection en **Perspective** ou **Orthographique**.

|Projection|Description|
|----------------|-----------------|
|**Perspective**|Dans la projection en perspective, les objets éloignés du point de vue apparaissent de taille réduite et convergent finalement vers un point à l'horizon.|
|**Orthographique**|Dans la projection orthographique, les objets apparaissent de même taille, quelle que soit leur distance par rapport au point de vue. Aucune convergence n'est affichée. Quand la projection **Orthographique** est activée, vous ne pouvez pas utiliser le mode **Orbite** pour positionner la vue arbitrairement.|

Il peut être utile d’afficher une scène 3D à partir d’une position et d’un angle connus, par exemple pour comparer deux scènes similaires. Pour ce scénario, l'éditeur de modèle fournit plusieurs vues prédéfinies. Pour utiliser une vue prédéfinie, dans la barre d’outils **Mode de l’éditeur de modèle**, choisissez **Affichage**, puis la vue prédéfinie de votre choix (avant, arrière, gauche, droite, haut ou bas). Dans ces vues, la caméra virtuelle regarde directement l'origine de la scène. Par exemple, si vous choisissez **Afficher le haut**, la caméra virtuelle regarde l’origine de la scène d’un point situé directement au-dessus de l’origine.

### <a name="view-additional-geometry-details"></a>Afficher des détails géométriques supplémentaires

Pour mieux comprendre un objet ou une scène 3D, vous pouvez afficher des détails géométriques supplémentaires, comme les normales aux sommets, les normales aux faces, les points pivot de la sélection active, ainsi que d’autres détails. Pour les activer ou les désactiver, dans la barre d’outils **Éditeur de modèle**, choisissez **Scripts** > **Affichage**, puis celui de votre choix.

### <a name="create-and-import-3d-objects"></a>Créer et importer des objets 3D <a name="Adding3DObjects"></a>

Pour ajouter une forme 3D prédéfinie à la scène, dans la **Boîte à outils**, sélectionnez celle de votre choix, puis déplacez-la dans l’aire de conception. Les nouvelles formes sont placées à l'origine de la scène. L’éditeur de modèle propose sept formes : **Cône**, **Cube**, **Cylindre**, **Disque**, **Plan**, **Sphère** et **Théière (Teapot)**.

Pour importer un objet 3D à partir d’un fichier, dans la barre d’outils **Éditeur de modèle**, choisissez **Avancé** > **Gestion des scènes** > **Importer** >, puis spécifiez le fichier à importer.

### <a name="transform-objects"></a>objets Transform

Vous pouvez *transformer* un objet en modifiant ses propriétés **Rotation**, **Échelle** et **Translation**. La *rotation* oriente un objet en appliquant des rotations successives autour de l’axe X, de l’axe Y et de l’axe Z, définies par son point pivot. Chaque spécification de rotation possède trois composants (x, y et z, dans cet ordre) et les composants sont spécifiés en degrés. La **mise à l’échelle** permet de redimensionner un objet en l’étirant selon un facteur donné dans un ou plusieurs axes centrés sur son point pivot. La *translation* localise un objet dans un espace tridimensionnel par rapport à son parent plutôt qu’à son point pivot.

Vous pouvez transformer un objet à l'aide des outils de modélisation ou en définissant des propriétés.

#### <a name="transform-an-object-by-using-modeling-tools"></a>Transformer un objet à l'aide d’outils de modélisation

1. En mode **Sélectionner**, sélectionnez l’objet que vous voulez transformer. Une superposition de maquette indique que l'objet est sélectionné.

2. Dans la barre d’outils **Éditeur de modèle**, choisissez l’outil **Translater**, **Redimensionner** ou **Faire pivoter**. Un manipulateur de translation, de mise à l'échelle ou de rotation s'affiche pour l'objet sélectionné.

3. Utilisez le manipulateur pour effectuer la transformation. Pour les transformations de translation et de mise à l'échelle, le manipulateur est un indicateur d'axe. Vous pouvez modifier un axe à la fois ou tous les axes simultanément à l'aide du cube blanc au centre de l'indicateur. Pour la rotation, le manipulateur est une sphère constituée de cercles identifiés par des couleurs qui correspondent à l'axe X (rouge), à l'axe Y (vert) et à l'axe Z (bleu). Vous devez modifier chaque axe individuellement pour créer la rotation souhaitée.

#### <a name="transform-an-object-by-setting-its-properties"></a>Transformer un objet en définissant ses propriétés

1. En mode **Sélectionner**, sélectionnez l’objet que vous voulez transformer. Une superposition de maquette indique que l'objet est sélectionné.

2. Dans la fenêtre **Propriétés**, spécifiez les valeurs des propriétés **Rotation**, **Échelle** et **Translation**.

    > [!IMPORTANT]
    > Pour la propriété **Rotation**, spécifiez le degré de rotation autour de chacun des trois axes. Les rotations sont appliquées dans l'ordre. Par conséquent, veillez à planifier une rotation, en considérant d'abord la rotation autour de l'axe X, autour de l'axe Y, puis de l'axe Z.

Les outils de modélisation vous permettent de créer rapidement des transformations, mais avec peu de précision. La définition des propriétés de l'objet vous permet de spécifier des transformations avec précision, mais plus lentement. Nous vous recommandons d'utiliser les outils de modélisation pour vous « rapprocher » des transformations que vous souhaitez effectuer, puis d'affiner le réglage des valeurs des propriétés.

Si vous ne souhaitez pas utiliser les manipulateurs, vous pouvez activer le mode avec formes libres. Dans la barre d’outils **Éditeur de modèle**, choisissez **Scripts** > **Outils** > **Manipulation de formes libres** pour activer (ou désactiver) le mode forme libre. En mode avec formes libres, vous pouvez commencer une manipulation à un point quelconque de l'aire de conception au lieu d'un point sur le manipulateur. En mode avec formes libres, vous pouvez limiter les modifications à certains axes en verrouillant ceux que vous ne souhaitez pas modifier. Dans la barre d’outils **Mode de l’éditeur de modèle**, choisissez une combinaison quelconque des boutons **Verrouiller l’axe X**, **Verrouiller l’axe Y** et **Verrouiller l’axe Z**.

Il peut être utile d'utiliser l'alignement sur la grille pour travailler avec les objets. Dans la barre d’outils **Mode de l’éditeur de modèle**, choisissez **Aligner** pour activer ou (désactiver) l’alignement sur la grille. Lorsque l'alignement sur la grille est activé, les transformations de translation, de rotation et de mise à l'échelle sont limitées aux incréments prédéfinis.

### <a name="work-with-the-pivot-point"></a>Utiliser le point pivot

Le point pivot d'un objet définit son centre de rotation et sa mise à l'échelle. Vous pouvez modifier le point pivot d'un objet pour changer la manière dont il est affecté par les transformations de rotation et de mise à l'échelle. Dans la barre d’outils **Mode de l’éditeur de modèle**, choisissez **Mode Pivot** pour activer (ou désactiver) le mode Pivot. Lorsque le mode Pivot est activé, un petit indicateur d'axe apparaît au niveau du point pivot de l'objet sélectionné. Vous pouvez alors utiliser les outils **Translation** et **Rotation** pour manipuler le point pivot.

Pour obtenir une démonstration qui montre comment utiliser le point pivot, consultez [Comment : modifier le point pivot d’un modèle 3D](../designers/how-to-modify-the-pivot-point-of-a-3-d-model.md).

### <a name="world-and-local-modes"></a>Modes local et universel

La translation et la rotation peuvent être réalisées dans le système de coordonnées local (ou *cadre de référence local*) de l’objet ou dans le système de coordonnées universel (ou *cadre de référence universel*). Le cadre de référence mondial est indépendant de la rotation de l'objet. Le mode local est l'option par défaut. Pour activer (ou désactiver) le mode universel, dans la barre d’outils **Mode de l’éditeur de modèle**, choisissez le bouton **WorldLocal**.

### <a name="modify-objects"></a>Modifier des objets <a name="ModifyingObjects"></a>

Vous pouvez modifier la forme d’un objet 3D en déplaçant ou en supprimant ses sommets, ses arêtes ou ses faces. Par défaut, l’éditeur de modèle est en *mode objet*, ce qui vous permet de sélectionner et de transformer des objets entiers. Pour sélectionner des points, des arêtes ou des faces, choisissez le mode de sélection approprié. Dans la barre d’outils **Mode de l’éditeur de modèle**, choisissez **Modes de sélection**, puis le mode voulu.

Vous pouvez créer des sommets supplémentaires par extrusion ou subdivision. L'extrusion reproduit les sommets d'une face (ensemble coplanaire de sommets) qui restent connectés par les sommets dupliqués. La subdivision ajoute des sommets pour créer plusieurs faces là où il y en avait déjà une. Pour créer de nouvelles faces, de nouveaux sommets sont ajoutés (un au centre de la face d'origine et l'autre au milieu de chaque arête), puis joints aux sommets d'origine. Le nombre de faces ajoutées est égal au nombre d'arêtes de la face d'origine. Dans les deux cas, vous pouvez translater, faire pivoter et redimensionner les nouveaux sommets pour modifier la géométrie de l'objet.

#### <a name="to-extrude-a-face-from-an-object"></a>Pour extruder une face d'un objet

1. En mode de sélection de face, sélectionnez la face à extruder.

2. Dans la barre d’outils **Éditeur de modèle**, choisissez **Scripts** > **Outils** > **Extruder**.

#### <a name="to-subdivide-faces"></a>Pour subdiviser des faces

1. En mode de sélection de face, sélectionnez les faces à subdiviser. Comme la subdivision crée de nouvelles données d'arêtes, la subdivision simultanée de toutes les faces fournit des résultats plus cohérents lorsque les faces sont adjacentes.

2. Dans la barre d’outils **Éditeur de modèle**, choisissez **Scripts** > **Outils** > **Subdiviser**.

Vous pouvez également effectuer une triangulation sur des faces, fusionner des objets et convertir des sélections de polygones en objets nouveaux. La triangulation crée des arêtes supplémentaires de telle sorte qu'une face non triangulaire est convertie en un nombre optimal de triangles. Toutefois, aucun détail géométrique supplémentaire n'est fourni. La fusion associe les objets sélectionnés en un seul objet. De nouveaux objets peuvent être créés à partir d'une sélection de polygones.

#### <a name="triangulate-a-face"></a>Effectuer une triangulation sur une face

1. En mode de sélection de face, sélectionnez la face pour laquelle créer une triangulation.

2. Dans la barre d’outils **Éditeur de modèle**, choisissez **Scripts** > **Outils** > **Effectuer une triangulation**.

#### <a name="merge-objects"></a>Fusionner des objets

1. En mode de sélection d'objet, sélectionnez les objets à fusionner.

2. Dans la barre d’outils **Éditeur de modèle**, choisissez **Scripts** > **Outils** > **Fusionner les objets**.

#### <a name="create-an-object-from-a-polygon-selection"></a>Créer un objet à partir d'une sélection de polygones

1. En mode de sélection de face, sélectionnez les faces à partir desquelles créer un nouvel objet.

2. Dans la barre d’outils **Éditeur de modèle**, choisissez **Scripts** > **Outils** > **Créer un objet à partir de la sélection de polygones**.

### <a name="work-with-materials-and-shaders"></a>Utiliser des matériaux et des nuanceurs

L'apparence d'un objet est déterminée par l'interaction de l'éclairage dans la scène et le matériau constituant l'objet. Les matériaux sont définis par des propriétés qui décrivent comment la surface réagit à différents types de lumière, ainsi que par un programme de nuanceur qui calcule la couleur finale de chaque pixel de la surface de l'objet en fonction des données d'éclairage, des cartes de texture, des cartes de normale et d'autres données.

L'éditeur de modèle propose les matériaux par défaut suivants :

|Matériau|Description|
|--------------|-----------------|
|**Non éclairé**|Affiche une surface sans éclairage simulé.|
|**Lambert**|Affiche une surface avec une simulation d'éclairage ambiant et un éclairage diffus.|
|**Phong**|Affiche une surface avec une simulation d'éclairage ambiant, un éclairage diffus et des surbrillances spéculaires.|

Chacun de ces matériaux applique une texture unique à la surface d'un objet. Vous pouvez définir une texture différente pour chaque objet qui utilise le matériau.

Pour modifier la façon dont un objet particulier réagit aux différentes sources de lumière dans la scène, vous pouvez modifier les propriétés d'éclairage du matériau indépendamment des autres objets qui utilisent ce matériau. Le tableau ci-dessous décrit les propriétés d'éclairage courantes :

|Propriété d'éclairage|Description|
| - |-----------------|
|**Ambiant**|Décrit comment la surface est affectée par l'éclairage ambiant.|
|**Diffus**|Décrit comment la surface est affectée par les lumières directionnelles et ponctuelles.|
|**Émissif**|Décrit comment la surface émet de la lumière, indépendamment des autres éclairages.|
|**Spéculaire**|Décrit comment la surface réfléchit les lumières directionnelles et ponctuelles.|
|**Puissance spéculaire**|Décrit l'amplitude et l'intensité des surbrillances spéculaires.|

Selon ce qu'un matériau prend en charge, vous pouvez modifier ses propriétés d'éclairage, ses textures et d'autres données. En mode **Sélectionner**, sélectionnez l’objet dont vous souhaitez modifier le matériau puis, dans la fenêtre **Propriétés**, modifiez les propriétés **Matériau ambiant**, **Matériau diffus**, **Matériau émissif**, **Matériau spéculaire** ou **Puissance spéculaire du matériau**, ou toute autre propriété disponible. Un matériau peut exposer jusqu’à huit textures, dont les propriétés sont nommées séquentiellement de **Texture1** à **Texture8**.

Pour supprimer tous les matériaux d’un objet, dans la barre d’outils **Éditeur de modèle**, choisissez **Scripts** > **Matériaux** > **Supprimer les matériaux**.

Vous pouvez utiliser le **concepteur Shader** pour créer des matériaux de nuanceur personnalisés et les appliquer à des objets de votre scène 3D. Pour plus d’informations sur la façon de créer des matériaux de nuanceur personnalisés, consultez [Concepteur Shader](../designers/shader-designer.md). Pour plus d’informations sur l’application d’un matériau de nuanceur personnalisé à un objet, consultez [Comment : appliquer un nuanceur à un modèle 3D](../designers/how-to-apply-a-shader-to-a-3-d-model.md).

### <a name="scene-management"></a>Gestion des scènes

Vous pouvez gérer les scènes sous la forme d'une hiérarchie d'objets. Lorsque plusieurs objets sont organisés hiérarchiquement, toute translation, mise à l'échelle ou rotation d'un nœud parent affecte également ses enfants. Cela est utile lorsque vous souhaitez construire des objets ou des scènes complexes à partir d'objets plus élémentaires.

Vous pouvez utiliser la fenêtre **Structure du document** pour afficher la hiérarchie de la scène et sélectionner les nœuds de la scène. Quand vous sélectionnez un nœud dans la structure, vous pouvez utiliser la fenêtre **Propriétés** pour modifier ses propriétés.

Vous pouvez construire une hiérarchie d'objets en définissant l'un d'eux comme le parent des autres ou en les regroupant comme frères sous un nœud d'espace réservé qui agit en tant que parent.

#### <a name="create-a-hierarchy-that-has-a-parent-object"></a>Créer une hiérarchie avec objet parent

1. En mode **Sélectionner**, sélectionnez deux objets ou plus. Le premier objet sélectionné sera l'objet parent.

2. Dans la barre d’outils **Éditeur de modèle**, choisissez **Scripts** > **Gestion des scènes** > **Attacher au parent**.

#### <a name="create-a-hierarchy-of-sibling-objects"></a>Créer une hiérarchie d'objets frères

1. En mode **Sélectionner**, sélectionnez deux objets ou plus. Un objet d'espace réservé est créé et devient leur objet parent.

2. Dans la barre d’outils **Éditeur de modèle**, choisissez **Scripts** > **Gestion des scènes** > **Créer un groupe**.

L'éditeur de modèle utilise une maquette blanche pour identifier le premier objet sélectionné, qui devient le parent. Les autres objets de la sélection ont une maquette bleue. Par défaut, les nœuds de l'espace réservé ne sont pas affichés. Pour afficher les nœuds d’espace réservé, dans la barre d’outils **Éditeur de modèle**, choisissez **Scripts** > **Gestion des scènes** > **Afficher les nœuds d’espace réservé**. Vous pouvez utiliser les nœuds de l'espace réservé de la même façon que les objets n'étant pas des espaces réservés.

Pour supprimer l’association parent-enfant entre deux objets, sélectionnez l’objet enfant puis, dans la barre d’outils **Éditeur de modèle**, choisissez **Scripts** > **Gestion des scènes** > **Détacher du parent**. Lorsque vous détachez le parent d'un objet enfant, l'objet enfant devient un objet racine dans la scène.

## <a name="keyboard-shortcuts"></a>Raccourcis clavier

|Commande|Raccourcis clavier|
|-------------| - |
|Passer en mode **Sélection**|**CTRL** + **G**, **CTRL** + **Q**<br /><br /> **S**|
|Passer en mode **Zoom**|**CTRL** + **G**, **CTRL** + **Z**<br /><br /> **Z**|
|Passer en mode **Panoramique**|**CTRL** + **G**, **CTRL** + **P**<br /><br /> **DK**|
|Tout sélectionner|**CTRL** + **Un**|
|Supprimer la sélection actuelle|**Supprimer**|
|Annuler la sélection actuelle|**Séquence d’échappement** (**Échap**)|
|Faire un zoom avant|**Roulette de la souris vers l’avant**<br /><br /> **CTRL** + **Roulette de la souris vers l’avant**<br /><br /> **MAJ** + **Roulette de la souris vers l’avant**<br /><br /> **CTRL** + **PG PRÉC**<br /><br /> Signe plus ( **+** )|
|Faire un zoom arrière|**Roulette de la souris vers l’arrière**<br /><br /> **CTRL** + **Roulette de la souris** vers l’arrière<br /><br /> **MAJ** + **Roulette de la souris** vers l’arrière<br /><br /> **CTRL** + **PG SUIV**<br /><br /> Signe moins ( **-** )|
|Mouvement panoramique de la caméra vers le haut|**Pg suiv**|
|Mouvement panoramique de la caméra vers le bas|**Pg préc**|
|Mouvement panoramique de la caméra vers la gauche|**Roulette de la souris vers la gauche**<br /><br /> **CTRL** + **PG SUIV**|
|Mouvement panoramique de la caméra vers la droite|**Roulette de la souris vers la droite**<br /><br /> **CTRL** + **PG SUIV**|
|Afficher le haut du modèle|**CTRL** + **L**, **CTRL** + **T**<br /><br /> **T**|
|Afficher le bas du modèle|**CTRL** + **L**, **CTRL** + **U**|
|Afficher le côté gauche du modèle|**CTRL** + **L**, **CTRL** + **l**|
|Afficher le côté droit du modèle|**CTRL** + **L**, **CTRL** + **R**|
|Afficher l'avant du modèle|**CTRL** + **L**, **CTRL** + **F**|
|Afficher l'arrière du modèle|**CTRL** + **L**, **CTRL** + **B**|
|Cadrer la fenêtre sur l'objet|**F**|
|Activer/Désactiver le mode Maquette|**CTRL** + **L**, **CTRL** + **W**|
|Activer/Désactiver l'alignement sur la grille|**CTRL** + **G**, **CTRL** + **N**|
|Activer/Désactiver le mode Pivot|**CTRL** + **G**, **CTRL** + **V**|
|Activer/Désactiver la restriction de l'axe X|**CTRL** + **L**, **CTRL** + **X**|
|Activer/Désactiver la restriction de l'axe Y|**CTRL** + **L**, **CTRL** + **Y**|
|Activer/Désactiver la restriction de l'axe Z|**CTRL** + **L**, **CTRL** + **Z**|
|Passer en mode de translation|**CTRL** + **G**, **CTRL** + **W**<br /><br /> **W**|
|Passer en mode de mise à l'échelle|**CTRL** + **G**, **CTRL** + **E**<br /><br /> **E**|
|Passer en mode de rotation|**CTRL** + **G**, **CTRL** + **R**<br /><br /> **R**|
|Passer en mode de sélection de point|**CTRL** + **L**, **CTRL** + **1**|
|Passer en mode de sélection d'arête|**CTRL** + **L**, **CTRL** + **2**|
|Passer en mode de sélection de face|**CTRL** + **L**, **CTRL** + **3**|
|Passer en mode de sélection d'objet|**CTRL** + **L**, **CTRL** + **4**|
|Passer en mode Orbite (caméra)|**CTRL** + **G**, **CTRL** + **O**|
|Sélectionner l'objet suivant dans la scène|**Tab**|
|Sélectionner l'objet précédent dans la scène|**MAJ** + **Onglet**|
|Manipuler l'objet sélectionné en fonction de l'outil actif|**Touches de direction**|
|Désactiver le manipulateur actuel|**Q**|
|Faire pivoter la caméra|**ALT** + **Faire glisser** avec le bouton gauche de la souris|

## <a name="related-topics"></a>Rubriques connexes

|Titre|Description|
|-----------|-----------------|
|[Utilisation des ressources 3D pour les jeux et les applications](../designers/working-with-3-d-assets-for-games-and-apps.md)|Fournit une vue d’ensemble des outils Visual Studio que vous pouvez utiliser pour travailler sur des composants graphiques, comme des textures et des images, des modèles 3D et des effets de nuanceur.|
|[Éditeur d’images](../designers/image-editor.md)|Décrit comment utiliser l’éditeur d’images Visual Studio pour travailler avec des textures et des images.|
|[Concepteur Shader](../designers/shader-designer.md)|Explique comment utiliser le concepteur Shader de Visual Studio pour travailler avec des nuanceurs.|
