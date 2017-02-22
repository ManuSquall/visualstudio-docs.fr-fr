---
title: "Comment&#160;: cr&#233;er un rapport de comparaisons du profileur &#224; partir d&#39;une invite de commandes | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 00548d16-eb5b-46f7-8a65-862f98a43831
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# Comment&#160;: cr&#233;er un rapport de comparaisons du profileur &#224; partir d&#39;une invite de commandes
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Vous pouvez créer un rapport des outils de profilage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] qui compare les données de performances de deux fichiers de données de profilage \(.VSP \/ou .VSPS\).  Le rapport affiche les différences, régressions de performance et améliorations qui sont apparues entre deux sessions de profilage.  Les valeurs dans le rapport présentent le delta, ou la modification, par rapport à la planification initiale du premier fichier que vous spécifiez.  Ce delta est calculé en déterminant la différence entre l'ancienne valeur, qui est la valeur de planification initiale, et la valeur de résultat de la nouvelle analyse.  Les comparaisons de données de profileur peuvent être basées sur les fonctions dans le code, les modules de l'application, les lignes, les pointeurs d'instruction \(IP\) et les types.  
  
 Pour répertorier les identificateurs des catégories et des champs de comparaison, tapez la ligne de commande suivante :  
  
 **VSPerfReport \/querydifftables**  *VspNomFichier1* *VspNomFichier2*  
  
 Utilisez la syntaxe d'URL suivante pour créer le rapport de comparaison :  
  
 **VSPerfReport \/diff**  `VspFileName1` *VspNomFichier2* \[**\/**`Options`\]  
  
 Vous pouvez ajouter des options, à partir du tableau suivant, à la ligne de commande **VSPerfReport \/diff** .  
  
|Option|Description|  
|------------|-----------------|  
|**DiffThreshold:**\[*Valeur*\]|Ignore la différence si la valeur est inférieure à cette valeur seuil en pourcentage.  De même, les nouvelles données affichant des valeurs inférieures à ce seuil n'apparaîtront pas.|  
|**DiffTable:** *NomTable*|Utilise ce tableau spécifique pour comparer des fichiers.  Par défaut, le tableau des fonctions est utilisé.  Spécifiez l'identificateur répertorié dans **VSPerfReport \/querydifftables**.|  
|**DiffColumn:** *ColumnName*|Utilise cette colonne spécifique pour comparer des valeurs.  Par défaut, la colonne de pourcentage d'échantillons exclusifs est utilisée.  Spécifiez l'identificateur répertorié dans **VSPerfReport \/querydifftables**.|