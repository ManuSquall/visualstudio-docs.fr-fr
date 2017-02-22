---
title: "Pourcentage de r&#233;duction du bruit | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.cv.threads.filter"
helpviewer_keywords: 
  - "Visualiseur concurrence, Pourcentage de réduction du bruit"
ms.assetid: 1c10cd4c-2fdd-48c9-b562-a334b3b2df6c
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# Pourcentage de r&#233;duction du bruit
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Par défaut, la valeur du paramètre de pourcentage de réduction du bruit est 2.  Seules les entrées dont le pourcentage de temps inclusif est supérieur ou égal à ce paramètre sont visibles dans l'arborescence des appels.  En modifiant le paramètre, vous pouvez contrôler le nombre des entrées affichées dans l'arborescence des appels.  Par exemple, si vous redéfinissez la valeur sur 10, seules les entrées d'arborescence des appels dont le temps inclusif est supérieur ou égal à 10 % s'affichent.  En augmentant la valeur du paramètre, vous pouvez déterminer les entrées qui influent le plus sur les performances de votre processus.