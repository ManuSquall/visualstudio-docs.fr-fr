---
title: Concepteur Shader
ms.date: 11/04/2016
ms.technology: vs-ide-designers
ms.topic: conceptual
f1_keywords:
- vs.graphics.designer.effectdesigner
- vs.graphics.shaderdesigner
ms.assetid: 5db09a16-b82c-4ba3-8ec9-630cdc109397
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 641db475998d62df534353824f9d58a01c8d1792
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2018
---
# <a name="shader-designer"></a>Concepteur Shader

Ce document décrit l’utilisation du concepteur de nuanceur [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pour créer, modifier et exporter des effets visuels personnalisés, appelés *nuanceurs*.

Le concepteur de nuanceur vous permet de créer des effets visuels personnalisés pour votre jeu ou votre application même si vous ne connaissez pas la programmation HLSL. Pour créer un nuanceur dans le concepteur de nuanceur, il vous suffit de le disposer sous forme de graphique. En d’autres termes, vous ajoutez à l’aire de conception des *nœuds* qui représentent des données et des opérations, avant de créer des connexions entre eux pour définir le traitement des données par ces opérations. À chaque nœud d’opération, un aperçu de l’effet jusqu’à ce point est fourni afin que vous puissiez visualiser son résultat. Les flux de données transitent via les nœuds vers un nœud final qui représente la sortie du nuanceur.

## <a name="supported-formats"></a>Formats pris en charge

Le concepteur de nuanceur prend en charge les formats de nuanceur suivants :

|Nom de format|Extension de fichier|Opérations prises en charge (afficher, modifier, exporter)|
|-----------------|--------------------|-------------------------------------------------|
|DGSL (Directed Graph Shader Language)|.dgsl|Afficher, modifier|
|Nuanceur HLSL (code source)|.hlsl|Exporter|
|Nuanceur HLSL (bytecode)|.cso|Exporter|
|En-tête C++ (tableau de bytecode HLSL)|.h|Exporter|

## <a name="get-started"></a>Bien démarrer

Cette section explique comment ajouter un nuanceur DGSL à votre projet [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] et fournit les informations de base pour commencer.

### <a name="to-add-a-dgsl-shader-to-your-project"></a>Pour ajouter un nuanceur DGSL à votre projet

1.  Dans l’**Explorateur de solutions**, ouvrez le menu contextuel du projet auquel vous souhaitez ajouter le nuanceur, puis choisissez **Ajouter**, **Nouvel élément**.

2.  Dans la boîte de dialogue **Ajouter un nouvel élément**, sous **Installé**, sélectionnez **Graphiques**, puis **Graphe de nuanceur visuel (.dgsl)**.

3.  Spécifiez le **Nom** du fichier du nuanceur, ainsi que l’**Emplacement** où vous souhaitez le créer.

4.  Choisissez le bouton **Ajouter** .

### <a name="the-default-shader"></a>Nuanceur par défaut

Chaque fois que vous créez un nuanceur DGSL, il s’agit au début d’un nuanceur minimal qui dispose simplement d’un nœud **Couleur du point**, qui est connecté au nœud **Couleur finale**. Même si ce nuanceur est complet et fonctionnel, il ne fait pas grand-chose. Par conséquent, la première étape de la création d’un nuanceur de travail consiste souvent à supprimer le nœud **Couleur du point** ou à le déconnecter du nœud **Couleur finale** pour faire de la place pour d’autres nœuds.

## <a name="work-with-the-shader-designer"></a>Utilisation du concepteur Shader

Les sections suivantes décrivent l’utilisation du concepteur de nuanceur avec des nuanceurs personnalisés.

### <a name="shader-designer-toolbars"></a>Barres d’outils du concepteur de nuanceur

Les barres d’outils du concepteur de nuanceur contiennent des commandes qui vous permettent de travailler avec des graphes de nuanceur DGSL.

Les commandes qui affectent l’état du concepteur de nuanceur se trouvent dans la barre d’outils **Mode du concepteur de nuanceur**, dans la fenêtre principale de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Les outils et commandes de conception sont situés dans la barre d’outils **Concepteur de nuanceur** de l’aire de conception du concepteur de nuanceur.

Barre d’outils **Mode du concepteur de nuanceur** :

![Barre d’outils modale du concepteur de nuanceur.](../designers/media/digit-dsd-modal-toolbar.png "Digit-DSD-Modal-Toolbar")

Ce tableau décrit les éléments de la barre d’outils **Mode du concepteur de nuanceur**, répertoriés suivant l’ordre de leur affichage, de gauche à droite.

|Élément de la barre d'outils|Description|
|------------------|-----------------|
|**Select**|Permet l’interaction avec des nœuds et des bords dans le graphique. Dans ce mode, vous pouvez sélectionner des nœuds et les déplacer ou les supprimer. Vous pouvez également créer des bords ou les couper.|
|**Panoramique**|Permet de déplacer un graphe de nuanceur par rapport au cadre de la fenêtre. Pour effectuer un mouvement panoramique, sélectionnez un point dans l’aire de conception et déplacez-le.<br /><br /> En mode **Sélection**, vous pouvez appuyer sur la touche Ctrl de façon prolongée pour activer temporairement le mode **Panoramique**.|
|**Zoom**|Permet d’afficher un graphique de nuanceur avec plus ou moins de détails par rapport au cadre de la fenêtre. En mode **Zoom**, sélectionnez un point dans l’aire de conception et déplacez-le vers la droite ou le bas pour effectuer un zoom avant, ou vers la gauche ou le haut pour effectuer un zoom arrière.<br /><br /> En mode **Sélection**, vous pouvez appuyer sur la touche Ctrl de façon prolongée pour effectuer un zoom avant ou arrière à l’aide de la roulette de la souris.|
|**Zoom pour ajuster**|Affiche le graphe de nuanceur complet dans le cadre de la fenêtre.|
|**Mode de rendu en temps réel**|Lorsque le rendu en temps réel est activé, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] redessine l'aire de conception, même lorsqu'aucune action utilisateur n'est effectuée. Ce mode est utile lorsque vous travaillez avec des nuanceurs qui évoluent avec le temps.|
|**Aperçu avec la sphère**|Si cette option est activée, un modèle de sphère est utilisé pour afficher un aperçu du nuanceur. Une seule forme d’aperçu peut être activée à la fois.|
|**Aperçu avec le cube**|Si cette option est activée, un modèle de cube est utilisé pour afficher un aperçu du nuanceur. Une seule forme d’aperçu peut être activée à la fois.|
|**Aperçu avec le cylindre**|Si cette option est activée, un modèle de cylindre est utilisé pour afficher un aperçu du nuanceur. Une seule forme d’aperçu peut être activée à la fois.|
|**Aperçu avec le cône**|Si cette option est activée, un modèle de cône est utilisé pour afficher un aperçu du nuanceur. Une seule forme d’aperçu peut être activée à la fois.|
|**Aperçu avec Teapot**|Si cette option est activée, un modèle de théière est utilisé pour afficher un aperçu du nuanceur. Une seule forme d’aperçu peut être activée à la fois.|
|**Aperçu avec le plan**|Si cette option est activée, un modèle de plan est utilisé pour afficher un aperçu du nuanceur. Une seule forme d’aperçu peut être activée à la fois.|
|**Boîte à outils**|Affiche ou masque la **Boîte à outils**.|
|**Propriétés**|Affiche ou masque la fenêtre **Propriétés**.|
|**Avancé**|Contient des commandes et des options avancées.<br /><br /> **Exporter** : permet l’exportation d’un nuanceur dans plusieurs formats.<br /><br /> **Exporter en tant que** : exporte le nuanceur soit en tant que code source HLSL ou en tant que bytecode de nuanceur compilé. Pour plus d’informations sur l’exportation des nuanceurs, consultez l’article [Comment : exporter un nuanceur](../designers/how-to-export-a-shader.md).<br /><br /> **Moteurs Graphics** : permet de sélectionner le renderer utilisé pour afficher l’aire de conception.<br /><br /> **Render with D3D11 (Afficher avec D3D11)**  : utilise Direct3D 11 pour afficher l’aire de conception du concepteur de nuanceur.<br /><br /> **Render with D3D11WARP (Afficher avec D3D11WARP)**  : utilise la plateforme WARP (Windows Advanced Rasterization Platform) D3D11 WARP pour afficher l’aire de conception du concepteur de nuanceur.<br /><br /> **Vue** : permet de sélectionner des informations supplémentaires sur le concepteur de nuanceur.<br /><br /> **Fréquence d’images** : si cette option est activée, affiche la fréquence d’images actuelle dans l’angle supérieur droit de l’aire de conception. La fréquence d'images est le nombre d'images dessinées par seconde.  Cette option est utile lorsque vous activez l’option **Mode de rendu en temps réel**.|

> [!TIP]
> Vous pouvez choisir le bouton **Avancé** pour réexécuter la dernière commande.

### <a name="work-with-nodes-and-connections"></a>Utilisation des nœuds et des connexions

Utilisez le mode **Sélection** pour ajouter, supprimer, repositionner, connecter et configurer des nœuds. Voici comment effectuer ces opérations de base :

#### <a name="to-perform-basic-operations-in-select-mode"></a>Pour effectuer des opérations de base en mode Sélection

-   Voici comment :

    -   Pour ajouter un nœud au graphique, sélectionnez-le dans la **boîte à outils**, puis déplacez-le vers l’aire de conception.

    -   Pour supprimer un nœud du graphique, sélectionnez-le, puis appuyez sur Suppr.

    -   Pour repositionner un nœud, sélectionnez-le, puis déplacez-le vers un nouvel emplacement.

    -   Pour connecter deux nœuds, déplacez un terminal de sortie d’un nœud vers un terminal d’entrée de l’autre nœud. Seuls les terminaux de type compatible peuvent être connectés. Une ligne entre les terminaux indique la connexion.

    -   Pour supprimer une connexion, dans le menu contextuel de l’un des terminaux connectés, choisissez **Rompre les liaisons**.

    -   Pour configurer les propriétés d’un nœud, sélectionnez le nœud, puis, dans la fenêtre **Propriétés**, spécifiez de nouvelles valeurs pour les propriétés.

### <a name="preview-shaders"></a>Afficher un aperçu des nuanceurs

Pour vous aider à comprendre comment un nuanceur apparaîtra dans votre application, vous pouvez configurer le mode de visualisation de l’effet. Pour estimer votre application, vous pouvez choisir l’une des formes à afficher, configurer des textures et d’autres paramètres de matériau, activer l’animation des effets à durée définie et examiner l’aperçu sous différents angles.

#### <a name="shapes"></a>Formes

Le concepteur de nuanceur comprend six formes (une sphère, un cube, un cylindre, un cône, une théière et un plan) que vous pouvez utiliser pour visualiser votre nuanceur. Selon le nuanceur, certaines formes peuvent vous donner un meilleur aperçu.

Pour choisir une forme d’aperçu, dans la barre d’outils **Mode du concepteur Shader**, choisissez la forme souhaitée.

#### <a name="textures-and-material-parameters"></a>Paramètres des textures et des matériaux
 De nombreux nuanceurs utilisent des textures et des propriétés de matériau pour produire une apparence unique pour chaque type d’objet de votre application. Pour voir à quoi votre nuanceur ressemblera dans votre application, vous pouvez définir les textures et les propriétés de matériau qui sont utilisées pour afficher l’aperçu pour qu’elles correspondent aux textures et aux paramètres que vous pouvez utiliser dans votre application.

##### <a name="to-bind-a-different-texture-to-a-texture-register-or-to-modify-other-material-parameters"></a>Pour lier une autre texture à un registre de texture ou pour modifier d’autres paramètres de matériau

1.  En mode **Sélection**, sélectionnez une zone vide de l’aire de conception. La fenêtre **Propriétés** affiche alors les propriétés globales du nuanceur.

2.  Dans la fenêtre **Propriétés**, spécifiez de nouvelles valeurs pour les propriétés de texture et de paramètre que vous souhaitez modifier.

Voici les paramètres de nuanceur que vous pouvez modifier :

|Paramètre|Propriétés|
|---------------|----------------|
|**Texture 1** - **Texture 8**|**Accès** :                             **Public** pour que la propriété puisse être définie dans l’éditeur de modèle. **Privé** dans le cas contraire.<br /><br /> **Nom de fichier** : chemin d’accès complet au fichier de texture associé à ce registre de texture.|
|**Matériau ambiant**|**Accès** :                             **Public** pour que la propriété puisse être définie dans l’éditeur de modèle. **Privé** dans le cas contraire.<br /><br /> **Valeur** : couleur diffuse du pixel actuel qui est due à l’éclairage indirect, ou ambiant.|
|**Matériau diffus**|**Accès** : **Public** pour que la propriété puisse être définie dans l’éditeur de modèle. **Privé** dans le cas contraire.<br /><br /> **Valeur** : couleur qui décrit la manière dont le pixel actuel diffuse la lumière directe.|
|**Matériau émissif**|**Accès** :                              **Public** pour que la propriété puisse être définie dans l’éditeur de modèle. **Privé** dans le cas contraire.<br /><br /> **Valeur** : contribution de couleur du pixel actuel, basée sur l’auto-éclairage.|
|**Matériau spéculaire**|**Accès** :                              **Public** pour que la propriété puisse être définie dans l’éditeur de modèle. **Privé** dans le cas contraire.<br /><br /> **Valeur** : couleur qui décrit la manière dont le pixel actuel reflète la lumière directe.|
|**Puissance spéculaire du matériau**|**Accès** :                             **Public** pour que la propriété puisse être définie dans l’éditeur de modèle. **Privé** dans le cas contraire.<br /><br /> **Valeur** : exposant qui définit l’intensité des surbrillances spéculaires sur le pixel actuel.|

#### <a name="time-based-effects"></a>Effets à durée définie

Certains nuanceurs sont pourvus d’un composant à durée définie qui anime l’effet. Pour afficher l’effet en action, l’aperçu doit être mis à jour plusieurs fois par seconde. Par défaut, l’aperçu est mis à jour uniquement lorsque le nuanceur est modifié. Pour changer ce comportement afin de pouvoir afficher les effets à durée définie, vous devez activer le rendu en temps réel.

Pour activer le rendu en temps réel, dans la barre d’outils du concepteur Shader, choisissez **Rendu en temps réel**.

#### <a name="examine-the-effect"></a>Examiner l’effet

De nombreux nuanceurs sont affectés par des variables telles que l’angle de visualisation ou la lumière directionnelle. Pour examiner la réaction de l’effet lorsque ces variables sont modifiées, vous pouvez faire pivoter la forme d’aperçu librement et observer le comportement du nuanceur.

Pour faire pivoter la forme, appuyez et maintenez enfoncée la touche **Alt**, puis sélectionnez un point quelconque dans l’aire de conception et déplacez-le.

### <a name="export-shaders"></a>Exporter des nuanceurs

Avant de pouvoir utiliser un nuanceur dans votre application, vous devez l’exporter dans un format pris en charge par DirectX.

Vous pouvez exporter des nuanceurs en tant que code source HLSL ou bytecode de nuanceur compilé. Le code source HLSL est exporté dans un fichier texte pourvu de l’extension de nom de fichier .hlsl. Le bytecode de nuanceur peut être exporté dans un fichier binaire brut pourvu de l’extension de nom de fichier .cso ou dans un fichier d’en-tête (.h) en C++, qui encode le bytecode de nuanceur dans un tableau.

Pour plus d’informations sur l’exportation des nuanceurs, consultez l’article [Comment : exporter un nuanceur](../designers/how-to-export-a-shader.md).

## <a name="keyboard-shortcuts"></a>Raccourcis clavier

|Commande|Raccourcis clavier|
|-------------|------------------------|
|Passer en mode **Sélection**|Ctrl+G, Ctrl+Q<br /><br /> S|
|Passer en mode **Zoom**|Ctrl+G, Ctrl+Z<br /><br /> Z|
|Passer en mode **Panoramique**|Ctrl+G, Ctrl+P<br /><br /> K|
|Sélectionner tout|Ctrl+A|
|Supprimer la sélection actuelle|Supprimer|
|Annuler la sélection actuelle|Échap|
|Zoom avant|Ctrl+Roulette de la souris vers l'avant<br /><br /> Signe plus (+)|
|Zoom arrière|Ctrl-Roulette de la souris vers l’arrière<br /><br /> Signe moins (-)|
|Mouvement panoramique vers le haut de l’aire de conception|Roulette de la souris vers l'arrière<br /><br /> Pg suiv|
|Mouvement panoramique vers le bas de l’aire de conception|Roulette de la souris vers l'avant<br /><br /> Pg préc|
|Mouvement panoramique vers la gauche de l’aire de conception|Maj+Roulette de la souris vers l'arrière<br /><br /> Roulette de la souris vers la gauche<br /><br /> Maj+Pg. suiv|
|Mouvement panoramique vers la droite de l’aire de conception|Maj+Roulette de la souris vers l'avant<br /><br /> Roulette de la souris vers la droite<br /><br /> Maj+Pg. préc|
|Déplacer le focus clavier vers un autre nœud|Touches de direction|
|Sélectionner le nœud ayant le focus clavier (ajoute le nœud au groupe de sélection)|Maj+Espace|
|Activer la sélection du nœud ayant le focus clavier|Ctrl+Barre d'espace|
|Activer la sélection actuelle (si aucun nœud n’est sélectionné, sélectionner le nœud ayant le focus clavier)|Barre d’espace|
|Déplacer la sélection actuelle vers le haut|Maj+Haut|
|Déplacer la sélection actuelle vers le bas|Maj+Bas|
|Déplacer la sélection actuelle vers la gauche|Maj+Gauche|
|Déplacer la sélection actuelle vers la droite|Maj+Droite|

## <a name="related-topics"></a>Rubriques connexes

|Titre|Description|
|-----------|-----------------|
|[Utilisation de composants 3D pour les jeux et les applications](../designers/working-with-3-d-assets-for-games-and-apps.md)|Présente les outils [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] que vous pouvez utiliser avec les textures et les images, les modèles 3D et les effets de nuanceur.|
|[Éditeur d’images](../designers/image-editor.md)|Explique comment utiliser l'éditeur d'images de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pour travailler avec des textures et des images.|
|[Éditeur de modèle](../designers/model-editor.md)|Décrit comment utiliser l’éditeur de modèle [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pour travailler avec des modèles 3D.|