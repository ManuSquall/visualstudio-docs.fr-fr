---
title: Nœuds du concepteur Shader | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: f5192fbd-c78f-40a8-a4d4-443209610268
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b7526da10262003c9d086fdf1d74d065aac2d406
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72664131"
---
# <a name="shader-designer-nodes"></a>Nœuds du concepteur Shader
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Les articles de cette section de la documentation contiennent des informations sur les différents nœuds du concepteur Shader pour créer des effets graphiques.

## <a name="nodes-and-node-types"></a>Nœuds et types de nœuds
 Le concepteur Shader représente des effets visuels sous forme de graphique. Ces graphiques sont générés à partir de nœuds spécifiquement sélectionnés et connectés de façon précise afin d’obtenir l’effet prévu. Chaque nœud représente une information ou une fonction mathématique, et les connexions entre elles représentent le flux d’informations dans le graphique pour produire le résultat. Le concepteur Shader fournit six types de nœuds différents (filtres, nœuds de texture, paramètres, constantes, nœuds d’utilitaire et nœuds mathématiques). Plusieurs nœuds individuels appartiennent à chaque type. Ces nœuds et types de nœuds sont décrits dans les autres articles dans cette section. Consultez les liens à la fin de ce document.

## <a name="node-structure"></a>Structure de nœuds
 Tous les nœuds sont composés d’une combinaison d’éléments communs. Chaque nœud a au moins un terminal de sortie sur son côté droit (sauf le nœud de couleur finale, qui représente la sortie du nuanceur). Les nœuds qui représentent des calculs ou des échantillonneurs de texture ont des terminaux d’entrée sur leur côté gauche, mais les nœuds qui représentent des informations n’ont aucun terminal d’entrée. Les terminaux de sortie sont connectés aux terminaux d’entrée pour déplacer des informations d’un nœud vers un autre.

### <a name="promotion-of-inputs"></a>Promotion des entrées
 Comme le concepteur Shader doit finalement générer le code source HLSL afin que l’effet puisse être utilisé dans un jeu ou une application, les nœuds du concepteur Shader sont soumis aux règles de la promotion de type utilisées par HLSL. Comme le matériel graphique s’exécute principalement sur des valeurs à virgule flottante, une promotion de type entre différents types, par exemple entre `int` et `float` ou entre `float` et `double`, est rare. Au lieu de cela, étant donné que le matériel graphique utilise la même opération simultanée sur plusieurs informations, un type différent de promotion peut se produire dans lequel le nombre le plus court d’entrées est rallongé pour le faire correspondre à la taille de l’entrée la plus longue. La façon dont il est rallongé dépend du type de l’entrée et également de l’opération proprement dite :

- **Si le plus petit type est une valeur scalaire, alors :**

     La valeur scalaire est répliquée dans un vecteur dont la taille est égale à l’entrée la plus grande. Par exemple, l’entrée scalaire 5.0 devient le vecteur (5.0, 5.0, 5.0) quand la plus grande entrée de l’opération est un vecteur à trois éléments, indépendamment des caractéristiques de l’opération.

- **Si le plus petit type est un vecteur et que l’opération relève d’une multiplication (\*, /, %, etc.), alors :**

     La valeur du vecteur est copiée dans les éléments de début d’un vecteur dont la taille est égale à l’entrée la plus grande, et les éléments de fin sont définis sur 1.0. Par exemple, l’entrée vectorielle (5.0, 5.0) devient le vecteur (5.0, 5.0, 1.0, 1.0) lors d’une multiplication par un vecteur à quatre éléments. Cela permet de conserver le troisième et le quatrième éléments de la sortie à l’aide de l’identité de multiplication, 1.0.

- **Si le plus petit type est un vecteur et que l’opération relève d’une addition (+, -, etc.), alors :**

     La valeur du vecteur est copiée dans les éléments de début d’un vecteur dont la taille est égale à l’entrée la plus grande, et les éléments de fin sont définis sur 0.0. Par exemple, l’entrée vectorielle (5.0, 5.0) devient le vecteur (5.0, 5.0, 0.0, 0.0) lors d’un ajout à un vecteur à quatre éléments. Cela permet de conserver le troisième et le quatrième éléments de la sortie à l’aide de l’identité d’addition, 0.0.

## <a name="related-topics"></a>Rubriques connexes

|Titre|Description|
|-----------|-----------------|
|[Nœuds de constante](../designers/constant-nodes.md)|Décrit les nœuds que vous pouvez utiliser pour représenter des valeurs littérales et des informations d’état de vertex interpolées dans les calculs de nuanceurs. Comme l’état de vertex est interpolé, et donc différent pour chaque pixel, chaque instance du nuanceur de pixels reçoit une version différente de la constante.|
|[Nœuds de paramètre](../designers/parameter-nodes.md)|Décrit les nœuds que vous pouvez utiliser pour représenter la position de l’appareil-photo, les propriétés matérielles, les paramètres d’éclairage, l’heure et d’autres informations sur l’état de l’application dans les calculs de nuanceurs.|
|[Nœuds de texture](../designers/texture-nodes.md)|Décrit les nœuds que vous pouvez utiliser pour échantillonner différents types de texture, ainsi que des géométries, et pour produire ou transformer des coordonnées de texture avec des techniques courantes.|
|[Nœuds mathématiques](../designers/math-nodes.md)|Décrit les nœuds que vous pouvez utiliser pour effectuer des opérations d’algèbre, de logique, de trigonométrie, et d’autres opérations mathématiques qui correspondent directement aux instructions HLSL.|
|[Nœuds utilitaires](../designers/utility-nodes.md)|Décrit les nœuds que vous pouvez utiliser pour exécuter des calculs d’éclairage courants et d’autres opérations courantes qui ne correspondent pas directement aux instructions HLSL.|
|[Nœuds de filtre](../designers/filter-nodes.md)|Décrit les nœuds que vous pouvez utiliser pour effectuer le filtrage de la texture et le filtrage des couleurs.|
