---
title: "Avertissements li&#233;s &#224; la fiabilit&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.codeanalysis.reliabilityrules"
helpviewer_keywords: 
  - "fiabilité, avertissements"
  - "avertissements liés à la fiabilité"
  - "avertissements liés à l’analyse du code managé, avertissements liés à la fiabilité"
ms.assetid: 77886846-10a2-4585-968a-7eb60ebe07e8
caps.latest.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 21
---
# Avertissements li&#233;s &#224; la fiabilit&#233;
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Les avertissements liés à la fiabilité assurent la fiabilité des bibliothèques et des applications, notamment une exploitation adaptée des threads et de la mémoire.  
  
## Dans cette section  
  
|Règle|Description|  
|-----------|-----------------|  
|[CA2000 : Supprimez les objets avant d'être hors de portée](../code-quality/ca2000-dispose-objects-before-losing-scope.md)|Sachant qu'un événement exceptionnel peut se produire et empêcher l'exécution du finaliseur d'un objet, ce dernier doit plutôt être supprimé explicitement avant que toutes les références à lui soient hors de portée.|  
|[CA2001 : Évitez d'appeler des méthodes susceptibles de poser des problèmes](../Topic/CA2001:%20Avoid%20calling%20problematic%20methods.md)|Un membre appelle une méthode potentiellement dangereuse ou problématique.|  
|[CA2002 : Ne définissez pas un verrou sur des objets à identité faible](../Topic/CA2002:%20Do%20not%20lock%20on%20objects%20with%20weak%20identity.md)|Un objet est dit d'identité faible lorsqu'il est accessible directement au\-delà des limites d'un domaine d'application.  Un thread qui essaie d'acquérir un verrou sur un objet qui affiche une identité faible peut être bloqué par un deuxième thread dans un domaine d'application différent qui dispose d'un verrou sur le même objet.|  
|[CA2003 : Ne traitez pas les fibres comme des threads](../code-quality/ca2003-do-not-treat-fibers-as-threads.md)|Un thread managé est traité comme un thread Win32.|  
|[CA2004 : Supprimez les appels à GC.KeepAlive](../Topic/CA2004:%20Remove%20calls%20to%20GC.KeepAlive.md)|Si vous envisagez d'utiliser SafeHandle, supprimez tous les appels à GC.KeepAlive \(objet\).  Dans ce cas, les classes ne requièrent pas d'appel à GC.KeepAlive, en supposant qu'elles ne disposent pas d'un finaliseur, mais dépendent de SafeHandle pour finaliser le handle du système d'exploitation à leur place.|  
|[CA2006 : Utilisez SafeHandle pour encapsuler les ressources natives](../code-quality/ca2006-use-safehandle-to-encapsulate-native-resources.md)|L'utilisation de IntPtr dans du code managé peut être le signe d'un problème potentiel de sécurité et de fiabilité.  Toute utilisation de IntPtr doit être passée en revue pour déterminer s'il est nécessaire de recourir à un SafeHandle ou une technologie similaire à la place.|