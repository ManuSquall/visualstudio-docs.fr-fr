---
title: "Nœuds du concepteur Shader | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f5192fbd-c78f-40a8-a4d4-443209610268
caps.latest.revision: 6
author: "BrianPeek"
ms.author: "brpeek"
manager: "ghogen"
caps.handback.revision: 6
---
# Nœuds du concepteur Shader
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Les éléments de cette section de la documentation contiennent des informations sur les différents nœuds du concepteur Shader pour créer des effets graphiques.  
  
## Nœuds et types de nœuds  
 Le concepteur Shader représente des effets visuels sous forme de graphique.  Ces graphiques sont générés à partir de nœuds spécifiquement sélectionnés et connectés de façon précise afin d'obtenir l'effet prévu.  Chaque nœud représente une information ou une fonction mathématique, et les connexions entre elles représentent le flux d'informations dans le graphique pour produire le résultat.  Le concepteur Shader fournit six types de nœuds différents \(filtres, nœuds de texture, paramètres, constantes, nœuds d'utilitaire et nœuds de mathématiques\). Plusieurs nœuds individuels appartiennent à chaque type.  Ces nœuds et types de nœuds sont décrits dans les autres articles dans cette section. Consultez les liens à la fin de ce document.  
  
## Structure de nœuds  
 Tous les nœuds sont composés d'une combinaison d'éléments communs.  Chaque nœud a au moins un terminal de sortie sur son côté droit \(sauf le nœud de couleur final, qui représente la sortie du nuanceur\).  Les nœuds qui représentent des calculs ou des échantillonneurs de texture ont des terminaux d'entrée sur leur côté gauche, mais les nœuds qui représentent les informations n'ont aucun terminal d'entrée.  Les terminaux de sortie sont connectés aux terminaux d'entrée pour déplacer des informations d'un nœud vers un autre.  
  
### Promotion des entrées  
 Comme le Concepteur Shader doit finalement générer le code source HLSL afin que l'effet puisse être utilisé dans un jeu ou une application, les nœuds du Concepteur Shader sont soumis aux règles de la promotion de type utilisées par HLSL.  Comme le matériel graphique s'exécute principalement sur des valeurs à virgule flottante, une promotion de type entre différents types, par exemple, entre `int` et `float`, ou entre `float` et `double` est rare.  Au lieu de cela, étant donné que le matériel graphique utilise la même opération simultanée sur plusieurs informations, un type différent de promotion peut se produire dans lequel le nombre le plus court d'entrées est rallongé pour le faire correspondre à la taille de l'entrée la plus longue.  La façon à laquelle il est rallongé dépend du type de l'entrée, et également de l'exécution elle\-même :  
  
-   **Si le plus petit type est une valeur scalaire, alors :**  
  
     La valeur scalaire est répliquée dans un vecteur dont la taille est égale à l'entrée plus grande.  Par exemple, l'entrée scalaire 5.0 devient le vecteur \(5.0, 5.0, 5.0\) lorsque la plus grande entrée de l'opération est un vecteur à trois éléments, indépendamment des caractéristiques de l'opération.  
  
-   **Si le plus petit type est un vecteur et que l'opération relève d'une multiplication \(\*, \/, %, etc.\), alors :**  
  
     La valeur du vecteur est copiée dans les éléments de début d'un vecteur dont la taille est égale à l'entrée la plus grande, et les éléments de fin sont définis sur 1,0.  Par exemple, l'entrée vectorielle \(5.0, 5.0\) devient le vecteur \(5.0, 5.0, 1.0, 1.0\) lorsqu'il est multiplié par un vecteur à quatre éléments.  Cela permet de conserver le troisième et le quatrième élément de la sortie à l'aide de l'identité multiplicative, 1.0.  
  
-   **Si le plus petit type est un vecteur et que l'opération relève d'une addition \(\+, \-, etc.\), alors :**  
  
     La valeur du vecteur est copiée dans les éléments de début d'un vecteur dont la taille est égale à l'entrée la plus grande, et les éléments de fin sont définis sur 0,0.  Par exemple, l'entrée vectorielle \(5.0, 5.0\) devient le vecteur \(5.0, 5.0, 0.0, 0.0\) lorsqu'il est ajouté à un vecteur à quatre éléments.  Cela permet de conserver le troisième et le quatrième élément de la sortie à l'aide de l'identité cumulative, 0.0.  
  
## Rubriques connexes  
  
|Titre|Description|  
|-----------|-----------------|  
|[Nœuds constants](../designers/constant-nodes.md)|Décrit les nœuds que vous pouvez utiliser pour représenter des valeurs littérales et des informations d'état de vertex interpolées dans les calculs de nuanceurs.  Comme l'état de vertex est interpolé, et est donc différent pour chaque pixel, chaque instance du nuanceur de pixels reçoit une version différente de la constante.|  
|[Nœuds de paramètre](../designers/parameter-nodes.md)|Décrit les nœuds que vous pouvez utiliser pour représenter la position de l'appareil\-photo, les propriétés matérielles, les paramètres d'éclairage et d'autres informations d'état sur les applications, dans les calculs de nuanceurs.|  
|[Nœuds de texture](../designers/texture-nodes.md)|Décrit les nœuds permettant d'échantillonner différents types de texture, ainsi que des géométries, et de produire ou de transformer des coordonnées de texture avec des techniques courantes.|  
|[Nœuds mathématiques](../designers/math-nodes.md)|Décrit les nœuds que vous pouvez utiliser pour effectuer des opérations d'algèbre, de logique, de trigonométrie et d'autres opérations mathématiques qui correspondent directement aux instructions HLSL.|  
|[Nœuds utilitaires](../designers/utility-nodes.md)|Décrit les nœuds que vous pouvez utiliser pour exécuter des calculs d'éclairage courants et d'autres types d'opérations qui ne correspondent pas directement aux instructions HLSL.|  
|[Nœuds de filtre](../designers/filter-nodes.md)|Décrit les nœuds que vous pouvez utiliser pour effectuer le filtrage de la texture et le filtrage des couleurs.|