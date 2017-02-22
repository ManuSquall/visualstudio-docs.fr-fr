---
title: "Fonctionnement des valeurs de donn&#233;es d’&#233;chantillonnage dans des outils de profilage | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "méthode de profilage par échantillonnage"
  - "outils de profilage, échantillonner"
ms.assetid: fad540a8-24b6-4ff9-91ce-e67e9a58399d
caps.latest.revision: 22
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 22
---
# Fonctionnement des valeurs de donn&#233;es d’&#233;chantillonnage dans des outils de profilage
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La méthode de profilage par *échantillonnage* des outils de profilage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] interrompt le processeur informatique à des intervalles définis et collecte la pile des appels de fonction.  Une *pile des appels* est une structure dynamique qui stocke des informations sur les fonctions exécutées sur le processeur.  
  
 **Configuration requise**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
 L'analyse du profileur détermine si le processeur exécute du code dans le processus cible.  Si le processeur n'exécute pas de code dans le processus cible, l'échantillon est ignoré.  
  
 Si le processeur exécute le code cible, le profileur incrémente le nombre d'échantillons pour chaque fonction dans la pile des appels.  Lors du prélèvement de l'échantillon, une seule fonction de la pile des appels exécute du code.  Les autres fonctions de la pile sont des parents dans la hiérarchie des appels de fonction qui attendent le retour de leurs enfants.  
  
 Pour l'événement d'échantillon, le profileur incrémente le nombre d'échantillons *exclusifs* de la fonction qui exécute actuellement ses instructions.  Étant donné qu'un échantillon exclusif fait également partie du nombre total d'échantillons \(*inclusifs*\) de la fonction, le nombre d'échantillons inclusifs de la fonction actuellement active est également incrémenté.  
  
 Le profileur incrémente le nombre d'échantillons inclusifs de toutes les autres fonctions dans la pile des appels.  
  
## Échantillons inclusifs  
 Nombre total d'échantillons collectés lors de l'exécution de la fonction cible.  
  
 Ce total inclut les échantillons collectés lors de l'exécution directe du code de fonction, ainsi que ceux collectés lors de l'exécution des fonctions enfants appelées par la fonction cible.  
  
## Échantillons exclusifs  
 Nombre d'échantillons collectés lors de l'exécution directe des instructions de la fonction cible.  
  
 Les échantillons exclusifs n'incluent pas les échantillons collectés lors de l'exécution des fonctions appelées par la fonction cible.  
  
## Pourcentage inclusif  
 Pourcentage du nombre total des échantillons inclusifs lors de l'exécution du profilage qui sont des échantillons inclusifs de la fonction ou de la plage de données.  
  
## Pourcentage exclusif  
 Pourcentage du nombre total des échantillons exclusifs lors de l'exécution du profilage qui sont des échantillons exclusifs de la fonction ou de la plage de données.  
  
## Voir aussi  
 [Comment : choisir des méthodes de collection](../profiling/how-to-choose-collection-methods.md)   
 [Analyse des données des outils de profilage](../profiling/analyzing-performance-tools-data.md)