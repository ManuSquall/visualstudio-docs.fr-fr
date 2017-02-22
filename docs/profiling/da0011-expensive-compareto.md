---
title: "DA0011&#160;: CompareTo co&#251;teux | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.DA0011"
  - "vs.performance.rules.DAExpensiveCompareTo"
  - "vs.performance.11"
  - "vs.performance.rules.DA0011"
ms.assetid: 239a381d-0d97-4367-8668-746c93f5af2c
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# DA0011&#160;: CompareTo co&#251;teux
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|ID de la règle|DA0011|  
|Catégorie|Utilisation du .NET Framework|  
|Méthodes de profilage|Échantillonnage<br /><br /> Mémoire .NET|  
|Message|Les fonctions CompareTo ne doivent pas être coûteuses et ne doivent pas allouer de mémoire.  Réduisez la complexité de la fonction CompareTo si possible.|  
|Type de règle|Avertissement|  
  
## Cause  
 La méthode CompareTo du type est coûteuse ou alloue de la mémoire.  
  
## Description de la règle  
 Les méthodes CompareTo doivent être efficaces et ne doivent pas allouer de mémoire.  
  
## Comment corriger les violations  
 Réduisez la complexité de la méthode CompareTo.