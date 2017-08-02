---
title: "Navigateur d&#39;utilisation | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.cv.performance.utilizationnavigator"
ms.assetid: 522a981a-37ef-4cdd-a04c-f1e7525a2aab
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Navigateur d&#39;utilisation
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Vous pouvez utiliser le navigateur de l'utilisation du Visualiseur concurrentiel pour sélectionner un intervalle de temps dans une trace.  Le Visualiseur concurrentiel affiche l'utilisation des cœur de l'UC par le processus cible au fil du temps.  Cela facilite l'examen des modèles d'utilisation de l'UC et permet également la comparaison entre les données d'utilisation et les données dans d'autres vues.  Le navigateur d'utilisation apparaît en haut de chaque vue dans le visualiseur d'accès concurrentiel.  L'illustration suivante montre le navigateur d'utilisation.  
  
 ![Navigateur d'utilisation indiquant la période sélectionnée](~/docs/profiling/media/cvutilizationnavigator.png "CVUtilizationNavigator")  
Navigateur d'utilisation et un délai sélectionné  
  
 Dans l'illustration, la plage sélectionnée est défini par un rectangle rouge, appelé *curseur de défilement*.  
  
 Voici comment vous pouvez utiliser le navigateur de l'utilisation pour manipuler la plage horaire affichée :  
  
-   Vous pouvez filtrer en faisant glisser le curseur gauche ou à droite. \(Clavier : Déplacez le focus à curseur de défilement et appuyez sur la touche de direction gauche ou droit.\)  
  
-   Vous pouvez modifier l'étendue de la plage en faisant glisser l'un des handles. \(Clavier : Déplacez le focus à un handle puis appuyez sur la touche de direction gauche ou droit.\)  
  
 Si vous modifiez l'intervalle à l'aide d'un contrôle de zoom différent du Visualiseur concurrentiel, le navigateur d'utilisation met à jour pour refléter la modification.