---
title: "D&#233;bogage et processus d&#39;h&#233;bergement | Microsoft Docs"
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
  - "déboguer (Visual Studio), processus d'hébergement"
  - "processus d'hébergement"
ms.assetid: d0f0b9a6-2a6e-463d-b6ea-9518ee727933
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# D&#233;bogage et processus d&#39;h&#233;bergement
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Le processus d'hébergement Visual Studio améliore la performance de débogueur et active de nouvelles fonctions de débogage, telles que le débogage de confiance partielle et l'évaluation d'une expression au moment du design. Vous pouvez désactiver le processus d’hébergement, le cas échéant. Pour plus d’informations, consultez [Comment : désactiver le processus d'hébergement](../ide/how-to-disable-the-hosting-process.md). Les sections suivantes décrivent certaines des différences entre le débogage avec et sans le processus d’hébergement.  
  
## Débogage de confiance partielle et sécurité ClickOnce  
 Le débogage de confiance partielle requiert le processus d'hébergement. Si vous désactivez le processus d’hébergement, le débogage de confiance partielle ne fonctionnera pas, même si la sécurité de confiance partielle est activée dans la page **Sécurité** de **Propriétés du projet**. Pour plus d’informations, consultez [Comment : désactiver le processus d'hébergement](../ide/how-to-disable-the-hosting-process.md) et [Comment : déboguer une application de confiance partielle](../debugger/how-to-debug-a-partial-trust-application.md).  
  
## Évaluation de l’expression au moment du design  
 L'expression au moment du design utilise toujours le processus d'hébergement. La désactivation du processus d'hébergement dans **Propriétés du projet** désactive l'évaluation d'une expression au moment du design pour les projets Bibliothèque de classes. Pour d'autres types de projet, l'évaluation d'une expression au moment du design n'est pas désactivée. À la place, Visual Studio démarre le fichier exécutable réel et l'utilise pour l'évaluation au moment du design sans le processus d'hébergement. Cette différence peut produire des résultats différents.  
  
## Différences AppDomain.CurrentDomain.FriendlyName  
 `AppDomain.CurrentDomain.FriendlyName` retourne des résultats différents selon que le processus d'hébergement est activé ou non. Si vous appelez `AppDomain.CurrentDomain.FriendlyName` avec le processus d’hébergement activé, il retourne *nom\_application*`.vhost.exe`. Si vous l’appelez avec le processus d’hébergement désactivé, il retourne *nom\_application*`.exe`.  
  
## Différences Assembly.GetCallingAssembly\(\).FullName  
 `Assembly.GetCallingAssembly().FullName` retourne des résultats différents selon que le processus d'hébergement est activé ou non. Si vous appelez `Assembly.GetCallingAssembly().FullName` avec le processus d’hébergement activé, il retourne `mscorlib`. Si vous appelez `Assembly.GetCallingAssembly().FullName` avec le processus d’hébergement désactivé, il retourne le nom d’application.  
  
## Voir aussi  
 [Processus d'hébergement \(vshost.exe\)](../ide/hosting-process-vshost-exe.md)   
 [Comment : déboguer une application de confiance partielle](../debugger/how-to-debug-a-partial-trust-application.md)   
 [Comment : désactiver le processus d'hébergement](../ide/how-to-disable-the-hosting-process.md)