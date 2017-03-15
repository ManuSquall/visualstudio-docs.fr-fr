---
title: "Nœuds constants | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2c798a50-a2d7-459b-9879-ad4ad8290c9b
caps.latest.revision: 11
author: "BrianPeek"
ms.author: "brpeek"
manager: "ghogen"
caps.handback.revision: 11
---
# Nœuds constants
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Dans le Concepteur Shader, les nœuds constants représentent les valeurs littérales et les attributs de vertex interpolés dans les calculs du nuanceur de pixels.  Comme les attributs des sommets sont interpolées, et sont donc différents pour chaque pixel, chaque instance du nuanceur de pixels reçoit une version différente de la constante.  Cela attribue à chaque pixel une apparence unique.  
  
## Interpolation des attributs des sommets  
 L'image d'une scène 3D dans un jeu ou une application est effectuée en transformant mathématiquement un certain nombre d'objets, définis par les vertex, les attributs de vertex et les définitions de primitives, dans les pixels affichés à l'écran.  Toutes les informations nécessaires pour donner à un pixel son apparence unique sont fournies par le biais des attributs de sommet, qui sont fusionnés ensemble en fonction de la proximité du pixel avec les différents sommets qui composent sa *primitive*.  Une primitive est un élément de rendu de base ; autrement dit, une forme simple telle qu'un point, une ligne ou un triangle.  Un pixel qui est très proche d'un des sommets reçoit des constantes qui sont presque identiques à ce sommet, mais un pixel espacé de façon uniforme entre tous les sommets d'une primitive reçoit des constantes correspondant à la moyenne de ces sommets.  En programmation graphique, les constantes que les pixels reçoivent sont dites *interpolées*.  Le fait de fournir des constantes aux pixels de cette manière produit une très bonne qualité visuelle et réduit en même temps considérablement la bande passante nécessaire et l'encombrement de la mémoire.  
  
 Bien que chaque instance du nuanceur de pixels ne reçoive qu'un seul jeu de valeurs de constante et ne puisse pas modifier ces valeurs, les différentes instances du nuanceur de pixels reçoivent des jeux de constante différents.  Cette conception permet à un programme de nuanceur de produire une sortie de couleur différente pour chaque pixel de la primitive.  
  
## Référence à une constante de nœud  
  
|Nœud|Détails|Propriétés|  
|----------|-------------|----------------|  
|**Vecteur d'appareil photo**|Vecteur qui s'étend du pixel actuel jusqu'à l'appareil photo dans l'espace universel.<br /><br /> Vous pouvez l'utiliser pour calculer les reflets dans l'espace universel.<br /><br /> **Sortie**<br /><br /> `Output`: `float3`<br /> Vecteur du pixel actuel jusqu'à l'appareil photo.|Aucun|  
|**Constante de couleur**|Valeur de couleur de constante.<br /><br /> **Sortie**<br /><br /> `Output`: `float4`<br /> Valeur de la couleur.|**Sortie**<br /> Valeur de la couleur.|  
|**Constante**|Valeur scalaire de constante.<br /><br /> **Sortie**<br /><br /> `Output`: `float`<br /> Valeur scalaire.|**Sortie**<br /> Valeur scalaire.|  
|**Constante 2D**|Constante de vecteur à deux composants.<br /><br /> **Sortie**<br /><br /> `Output`: `float2`<br /> Valeur vectorielle.|**Sortie**<br /> Valeur vectorielle.|  
|**Constante 3D**|Constante de vecteur à trois composants.<br /><br /> **Sortie**<br /><br /> `Output`: `float3`<br /> Valeur vectorielle.|**Sortie**<br /> Valeur vectorielle.|  
|**Constante 4D**|Constante de vecteur à quatre composants.<br /><br /> **Sortie**<br /><br /> `Output`: `float4`<br /> Valeur de la couleur.|**Sortie**<br /> Valeur vectorielle.|  
|**Position normalisée**|Position du pixel actuel, exprimée sous la forme des coordonnées normalisées du périphérique.<br /><br /> Les valeurs des coordonnées x et y sont comprises dans la plage \[\- 1, 1\], la valeur de la coordonnée z est comprise dans la plage \[0, 1\] et le composant w contient la valeur de profondeur du point dans l'espace d'affichage. w n'est pas normalisé.<br /><br /> **Sortie**<br /><br /> `Output`: `float4`<br /> Position du pixel actuel.|Aucun|  
|**Couleur du point**|Couleur diffuse du pixel actuel, qui est une combinaison de la couleur diffuse du matériel et des attributs de couleur du vertex.<br /><br /> **Sortie**<br /><br /> `Output`: `float4`<br /> Couleur diffuse du pixel actuel.|Aucun|  
|**Profondeur de point**|Profondeur du pixel actuel dans l'espace d'affichage.<br /><br /> **Sortie**<br /><br /> `Output`: `float`<br /> Profondeur du pixel actuel.|Aucun|  
|**Profondeur de point normalisée**|Profondeur du pixel actuel, exprimée sous la forme des coordonnées normalisées du périphérique.<br /><br /> La valeur du résultat est comprise dans la plage \[0, 1\].<br /><br /> **Sortie**<br /><br /> `Output`: `float`<br /> Profondeur du pixel actuel.|Aucun|  
|**Position à l'écran**|Position du pixel actuel, exprimée sous la forme des coordonnées d'écran.<br /><br /> Les coordonnées d'écran sont basés sur la fenêtre d'affichage actuelle.  Les composants x et y contiennent les coordonnées de l'écran, le composant de z contient la profondeur normalisée sur une plage de \[0, 1\] et le composant w contient la valeur de profondeur dans l'espace d'affichage.<br /><br /> **Sortie**<br /><br /> `Output`: `float4`<br /> Position du pixel actuel.|Aucun|  
|**Normale à la surface**|Vecteur normal de surface du pixel actuel dans l'espace d'objets.<br /><br /> Vous pouvez l'utiliser pour calculer les contributions de l'éclairage et les reflets dans l'espace d'objets.<br /><br /> **Sortie**<br /><br /> `Output`: `float3`<br /> Normale de surface du pixel actuel.|Aucun|  
|**Vecteur d'appareil photo de l'espace de tangente**|Vecteur qui s'étend du pixel actuel jusqu'à l'appareil photo dans l'espace tangent.<br /><br /> Vous pouvez l'utiliser pour calculer les reflets dans l'espace tangent.<br /><br /> **Sortie**<br /><br /> `Output`: `float3`<br /> Vecteur du pixel actuel jusqu'à l'appareil photo.|Aucun|  
|**Direction de la lumière de l'espace de tangente**|Vecteur qui définit la direction dans laquelle la lumière est projetée à partir d'une source lumineuse dans l'espace tangent du pixel actuel.<br /><br /> Vous pouvez l'utiliser pour calculer les contributions d'éclairage et spéculaires dans l'espace tangent.<br /><br /> **Sortie :**<br /><br /> `Output`: `float3`<br /> Vecteur du pixel actuel à une source de lumière.|Aucun|  
|**Normale universelle**|Vecteur normal de surface du pixel actuel dans l'espace universel.<br /><br /> Vous pouvez l'utiliser pour calculer les contributions de l'éclairage et les reflets dans l'espace universel.<br /><br /> **Sortie**<br /><br /> `Output`: `float3`<br /> Normale de surface du pixel actuel.|Aucun|  
|**Position universelle**|Position du pixel actuel dans l'espace universel.<br /><br /> **Sortie**<br /><br /> `Output`: `float4`<br /> Position du pixel actuel.|Aucun|