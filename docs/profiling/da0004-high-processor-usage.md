---
title: "DA0004&#160;: Utilisation intensive du processeur | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.rules.DAHighProcessorUsage"
  - "vs.performance.rules.DA0004"
  - "vs.performance.DA0004"
  - "vs.performance.4"
ms.assetid: 2c4fb569-929e-4f1d-8c50-b590ee371351
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# DA0004&#160;: Utilisation intensive du processeur
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|ID de la règle|DA0004|  
|Catégorie|Utilisation des outils de profilage|  
|Méthodes de profilage|Instrumentation<br /><br /> Échantillonnage|  
|Message|Votre utilisation du processeur dépasse régulièrement 75 %.  Envisagez d'utiliser le mode d'échantillonnage pour les applications liées à l'UC.|  
|Type de règle|Information|  
  
 Lorsque vous profilez en utilisant les méthodes d'échantillonnage, de mémoire. NET ou de conflits de ressources, vous devez collecter au moins 10 échantillons pour déclencher cette règle.  
  
## Cause  
 L'utilisation de processeur \(UC\) était considérablement élevée dans les données de profilage collectées à l'aide de la méthode d'instrumentation.  Utilisez la méthode de profilage d'échantillonnage lors du profilage d'une application liée à l'UC.  
  
## Description de la règle  
 Pendant cette exécution du profilage, le processeur \(ou processeurs\) sont régulièrement très occupé.  L'utilisation élevée du processeur peut indiquer une application utilisant le processeur.  Les profils instrumentés ne sont pas habituellement la méthode la plus efficace pour étudier des scénarios d'utilisation d'UC.  L'échantillonnage est habituellement plus efficace lorsque vous profilez des applications qui passent beaucoup de temps à exécuter des instructions sur le processeur.  
  
## Comment corriger les violations  
 Envisagez de profiler encore votre application à l'aide de la méthode d'échantillonnage au lieu de la méthode d'instrumentation à moins que vous n'ayez besoin de minutages de fonction ou que vous soyez plus intéressé par le fonctionnement des entrées\/sorties que par les goulots d'étranglement de processeur.