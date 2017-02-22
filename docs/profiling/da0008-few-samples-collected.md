---
title: "DA0008&#160;: Peu d&#39;&#233;chantillons collect&#233;s | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.rules.DATooFewSamples"
  - "vs.performance.8"
  - "vs.performance.DA0008"
  - "vs.performance.rules.DA0008"
ms.assetid: 8a5b78aa-7b3d-476c-a47d-abfaff3fae7c
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# DA0008&#160;: Peu d&#39;&#233;chantillons collect&#233;s
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|ID de la règle|DA0008|  
|Catégorie|Utilisation des outils de profilage|  
|Méthode de profilage|Échantillonnage|  
|Message|Seuls quelques échantillons ont été collectés.  Considérez une exécution plus longue ou un taux d'échantillonnage plus rapide pour obtenir des résultats plus significatifs.|  
|Type de règle|Information|  
  
## Cause  
 Seuls quelques échantillons ont été collectés dans l'exécution du profilage.  
  
## Description de la règle  
 Lorsque vous utilisez la méthode d'échantillonnage, vous devez collecter un nombre d'échantillons statistiquement significatif pour être sûr que les données soient représentatives du comportement réel du programme.  Pour réduire au minimum les erreurs d'échantillonnage, vous devez essayer de collecter au moins 1000 exemples de comportement d'exécution d'instruction du programme.  Si vous ne collectez pas assez d'échantillons, les résultats peuvent être trompeurs lorsque vous analysez les données de profilage.  
  
## Comment corriger les violations  
 Envisagez de procéder au profilage sur une période d'exécution plus longue de l'application ou d'utiliser un taux d'échantillonnage plus élevé pour obtenir des résultats statistiques plus significatifs.  Pour plus d'informations sur la modification du taux d'échantillonnage dans l'IDE de Visual Studio, consultez [Comment : choisir des événements d’échantillonnage](../Topic/How%20to:%20Choose%20Sampling%20Events.md).  Pour plus d'informations sur la modification du taux d'échantillonnage lorsque vous utilisez la ligne de commande des outils de profilage, consultez [Timer](../profiling/timer.md) dans la référence [VSPerfCmd](../profiling/vsperfcmd.md).