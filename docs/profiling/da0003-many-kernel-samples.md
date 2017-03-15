---
title: "DA0003&#160;: Nombreux &#233;chantillons de noyau | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.rules.DA0003"
  - "vs.performance.DA0003"
  - "vs.performance.3"
  - "vs.performance.rules.DAManyKernelSamples"
ms.assetid: c1f46f77-eb95-42e5-b340-d86bc9de41b4
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# DA0003&#160;: Nombreux &#233;chantillons de noyau
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|ID de la règle|DA0003|  
|Catégorie|Utilisation des outils de profilage|  
|Méthodes de profilage|Échantillonnage|  
|Message|Le mode Noyau comporte une proportion élevée d'échantillons.  Cela peut indiquer une activité d'E\/S importante ou de nombreux changements de contexte.  Profilez de nouveau votre application en mode Instrumentation.|  
|Type de règle|Information|  
  
## Cause  
 Une proportion significative des exemples de pile d'appels collectés pour l'application s'exécutait en mode noyau.  Envisagez de profiler votre application à l'aide d'une autre méthode de profilage.  
  
## Description de la règle  
 Dans Windows, le code peut être exécuté en Mode noyau ou en Mode utilisateur. \(Le mode noyau est également appelé le mode privilégié.\) Seul le code système de niveau inférieur, tel qu'un pilote de périphérique, s'exécute en Mode noyau.  Une application en mode utilisateur peut passer en mode noyau pour exécuter des opérations d'E\/S, pour attendre des primitives de synchronisation de threads ou de processus ou pour passer des appels système.  
  
 L'échantillonnage est très efficace lorsque vous profilez des applications qui passent la plupart de leur temps à travailler en mode utilisateur.  Le nombre des exemples rassemblés lorsque l'application s'exécutait en mode noyau peut indiquer des opérations d'E\/S fréquentes ou peut indiquer que des changements de contexte ont lieu.  Aucune de ces opérations ne peut être étudiée à l'aide de la méthode d'échantillonnage.  Si trop d'échantillons en mode noyau sont pris, les données d'échantillonnage peuvent ne pas contenir assez d'échantillons en Mode utilisateur pour que ce soit statistiquement significatif.  
  
## Comment corriger les violations  
 Envisagez de profiler votre application à nouveau à l'aide d'une des options suivantes :  
  
-   Profilez à l'aide de la méthode d'instrumentation.  
  
-   Augmentez le taux d'échantillonnage pour essayer de collecter plus d'échantillons en Mode utilisateur.