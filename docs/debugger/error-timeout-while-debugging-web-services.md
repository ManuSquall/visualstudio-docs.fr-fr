---
title: "Erreur&#160;: d&#233;lai d&#39;attente lors du d&#233;bogage de services Web | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "débogueur, erreurs d'applications Web"
  - "services Web XML, délai d'attente lors du débogage"
ms.assetid: 4b7df112-788a-4429-9a0c-4c6dac4fb609
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Erreur&#160;: d&#233;lai d&#39;attente lors du d&#233;bogage de services Web
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Lorsque vous exécutez pas à pas un service Web XML à partir du code appelant, l'appel peut parfois dépasser le délai et, par conséquent, vous ne pouvez pas continuer le débogage.  Un message d'erreur, tel que celui\-ci, peut s'afficher.  
  
```  
An unhandled exception of type 'System.Net.WebException' occurred in   
system.Web.services.dll  
Additional information: The operation has timed-out.  
```  
  
## Solution  
 Pour éviter ce problème, attribuez une valeur infinie au délai d'attente de l'appel du service Web XML, comme dans cet exemple :  
  
```  
Service1 obj = new Service1();  
obj.TimeOut = -1; // infinite time out.  
```  
  
## Voir aussi  
 [Débogage d'applications Web : erreurs et dépannage](../debugger/debugging-web-applications-errors-and-troubleshooting.md)