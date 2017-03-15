---
title: "DA0029&#160;: version&#160;CLR non prise en&#160;charge | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.29"
  - "vs.performance.rules.DA0029"
helpviewer_keywords: 
  - "vs.performance.29"
  - "vs.performance.DA0029"
  - "vs.performance.rules.DA0029"
ms.assetid: 76247259-c6f3-44c4-b3f9-d8dac16b5e0d
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# DA0029&#160;: version&#160;CLR non prise en&#160;charge
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|ID de la règle|DA0029|  
|Catégorie|Utilisation des outils de profilage|  
|Méthode de profilage|Profilage à partir de la ligne de commande|  
|Message|Une version CLR non prise en charge a été détectée lors de la collection.  Les symboles managés peuvent ne pas être résolus correctement.|  
|Type de règle|Informations.|  
  
## Cause  
 Vous essayez de profiler une application qui utilise le [!INCLUDE[net_v11_long](../profiling/includes/net_v11_long_md.md)] qui n'est pas pris en charge par les outils de profilage.  
  
## Description de la règle  
 Cet avertissement se produit car les outils de profilage ne pourront pas résoudre les symboles du code managé exécuté dans l'application.  Les outils de profilage ne peuvent pas résoudre les symboles de code managé pour les applications qui exécutent le [!INCLUDE[net_v11_long](../profiling/includes/net_v11_long_md.md)].  
  
## Comment corriger les violations  
 Aucun