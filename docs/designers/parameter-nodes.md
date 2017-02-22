---
title: "Nœuds de param&#232;tre | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: da54db0b-3a3d-48dc-858c-7ac43aa04b13
caps.latest.revision: 10
author: "BrianPeek"
ms.author: "brpeek"
manager: "ghogen"
caps.handback.revision: 10
---
# Nœuds de param&#232;tre
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Dans le Concepteur Shader, les nœuds de paramètre représentent les entrées dans le nuanceur qui sont sous le contrôle de l'application pour chaque dessin, par exemple, les propriétés matérielles, les lumières directionnelles, la position de la caméra, et le temps.  Comme vous pouvez modifier ces paramètres à chaque appel de dessin, utilisez le même shader pour donner à un objet différents aspects.  
  
## Référence du nœud de paramètre  
  
|Nœud|Détails|Propriétés|  
|----------|-------------|----------------|  
|**Position universelle d'appareil photo**|Position de l'appareil photo dans l'espace universel.<br /><br /> **Sortie :**<br /><br /> `Output`: `float4`<br /> Position de l'appareil photo.|Aucun|  
|**Direction de la lumière**|Vecteur qui définit la direction dans laquelle la lumière est projetée à partir d'une source lumineuse dans l'espace universel.<br /><br /> Vous pouvez l'utiliser pour calculer les contributions d'éclairage et spéculaires dans l'espace universel.<br /><br /> **Sortie :**<br /><br /> `Output`: `float3`<br /> Vecteur du pixel actuel à une source de lumière.|Aucun|  
|**Matériau ambiant**|Contribution de couleur diffuse du pixel actuel attribuée à l'éclairage indirect.<br /><br /> La couleur diffuse d'un pixel simule la façon dont la lumière interagit avec les surfaces rugueuses.  Vous pouvez utiliser le paramètre Matériau ambiant pour avoir une idée de la manière dont l'éclairage indirect contribue à l'aspect d'un objet dans le monde réel.<br /><br /> **Sortie :**<br /><br /> `Output`: `float4`<br /> Couleur diffuse du pixel actuel en raison de l'éclairage indirect, ambiant.|**Accès**<br /> **Public** pour que la propriété puisse être définie à partir de l'éditeur de modèle. Sinon, **Private**.<br /><br /> **Valeur**<br /> Couleur diffuse du pixel actuel en raison de l'éclairage indirect, ambiant.|  
|**Matériau diffus**|Couleur qui décrit la manière dont le pixel actuel diffuse la lumière directe.<br /><br /> La couleur diffuse d'un pixel simule la façon dont la lumière interagit avec les surfaces rugueuses.  Vous pouvez utiliser le paramètre Matériau diffus pour modifier la façon dont le pixel actuel répand un éclairage direct, c'est\-à\-dire directionnel, par point et par lumière projetée.<br /><br /> **Sortie :**<br /><br /> `Output`: `float4`<br /> Couleur qui décrit la manière dont le pixel actuel diffuse la lumière directe.|**Accès**<br /> **Public** pour que la propriété puisse être définie à partir de l'éditeur de modèle. Sinon, **Private**.<br /><br /> **Valeur**<br /> Couleur qui décrit la manière dont le pixel actuel diffuse la lumière directe.|  
|**Matériau émissif**|Contribution de couleur du pixel actuel qui est attribuée à l'éclairage qui est fournie à elle\-même.<br /><br /> Vous pouvez l'utiliser pour simuler un objet brillant ; autrement dit, un objet qui fournit sa propre lumière.  Cette lumière n'affecte pas les autres objets.<br /><br /> **Sortie :**<br /><br /> `Output`: `float4`<br /> Contribution de couleur du pixel actuel, basée sur l'auto\-éclairage.|**Accès**<br /> **Public** pour que la propriété puisse être définie à partir de l'éditeur de modèle. Sinon, **Private**.<br /><br /> **Valeur**<br /> Contribution de couleur du pixel actuel, basée sur l'auto\-éclairage.|  
|**Matériau spéculaire**|Couleur qui décrit la manière dont le pixel actuel reflète la lumière directe.<br /><br /> La couleur spéculaire d'un pixel simule l'interaction entre l'éclairage et les surfaces lisses et brillantes.  Vous pouvez utiliser le paramètre Matériau spéculaire pour modifier la façon dont le pixel actuel reflète un éclairage direct, c'est\-à\-dire directionnel, par point et par lumière projetée.<br /><br /> **Sortie :**<br /><br /> `Output`: `float4`<br /> Couleur qui décrit la manière dont le pixel actuel reflète la lumière directe.|**Accès**<br /> **Public** pour que la propriété puisse être définie à partir de l'éditeur de modèle. Sinon, **Private**.<br /><br /> **Valeur**<br /> Couleur qui décrit la manière dont le pixel actuel reflète la lumière directe.|  
|**Puissance spéculaire du matériau**|Valeur scalaire qui décrit l'intensité des surbrillances spéculaires.<br /><br /> Plus la puissance spéculaire est grande, plus les surbrillances spéculaires deviennent intenses et de grande portée.<br /><br /> **Sortie :**<br /><br /> `Output`: `float`<br /> Terme exponentiel qui décrit l'intensité des surbrillances spéculaires sur le pixel actuel.|**Accès**<br /> **Public** pour que la propriété puisse être définie à partir de l'éditeur de modèle. Sinon, **Private**.<br /><br /> **Valeur**<br /> Exposant qui définit l'intensité des surbrillances spéculaires sur le pixel actuel.|  
|**Heure normalisée**|Durée en secondes, normalisée dans la plage \[0, 1\], de sorte que lorsque la durée atteint 1, elle est réinitialisée sur 0.<br /><br /> Vous pouvez l'utiliser en tant que paramètre dans les calculs du nuanceur, par exemple pour animer les coordonnées de la texture, les valeurs de couleur ou d'autres attributs.<br /><br /> **Sortie :**<br /><br /> `Output`: `float`<br /> Durée normalisée, en secondes.|Aucun|  
|**Heure**|Durée en secondes.<br /><br /> Vous pouvez l'utiliser en tant que paramètre dans les calculs du nuanceur, par exemple pour animer les coordonnées de la texture, les valeurs de couleur ou d'autres attributs.<br /><br /> **Sortie :**<br /><br /> `Output`: `float`<br /> Durée, en secondes.|Aucun|