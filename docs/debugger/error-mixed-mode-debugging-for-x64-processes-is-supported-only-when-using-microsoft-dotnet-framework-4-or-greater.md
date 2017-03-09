---
title: "Erreur&#160;: Le d&#233;bogage en mode mixte des processus x64 est pris en charge uniquement lorsque vous utilisez Microsoft .NET Framework&#160;4 ou version ult&#233;rieure | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.error.interop_unsupported_x64"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: e4b0216c-7006-4832-883f-08e982ba8d3f
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Erreur&#160;: Le d&#233;bogage en mode mixte des processus x64 est pris en charge uniquement lorsque vous utilisez Microsoft .NET Framework&#160;4 ou version ult&#233;rieure
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Pour déboguer du code natif et managé mixte dans un processus 64 bits, vous devez disposer du [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] version 4.  Le débogage en mode mixte de processus 64 bits avec les versions de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] antérieures à la version 4 n'est pas pris en charge.  
  
### Pour corriger cette erreur  
  
-   Effectuez l'une des opérations suivantes :  
  
    -   Effectuez une mise à niveau du [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] vers la version 4.  
  
    -   Générez une version 32 bits de votre application pour le débogage.  
  
## Voir aussi  
 [Configurer les outils de contrôle à distance sur le périphérique](../Topic/Set%20Up%20the%20Remote%20Tools%20on%20the%20Device.md)