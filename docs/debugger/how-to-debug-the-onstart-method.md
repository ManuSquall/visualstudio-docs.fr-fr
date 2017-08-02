---
title: "Comment&#160;: d&#233;boguer la m&#233;thode OnStart | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
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
  - "OnStart (méthode)"
  - "déboguer [Visual Studio], services Windows"
  - "déboguer du code managé, méthode OnStart"
  - "déboguer des applications de service Windows, méthode onStart"
  - "applications de service Windows, déboguer"
ms.assetid: b06b5d65-424b-490f-bf58-97583cd7006a
caps.latest.revision: 16
caps.handback.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Comment&#160;: d&#233;boguer la m&#233;thode OnStart
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Vous pouvez déboguer un service Windows en le démarrant et en attachant le débogueur au processus de service. Pour plus d'informations, consultez [How to: Debug Windows Service Applications](../Topic/How%20to:%20Debug%20Windows%20Service%20Applications.md). Toutefois, pour déboguer la méthode <xref:System.ServiceProcess.ServiceBase.OnStart%2A?displayProperty=fullName> d’un service Windows, vous devez lancer le débogueur à l’intérieur de la méthode.  
  
1.  Ajoutez un appel à <xref:System.Diagnostics.Debugger.Launch%2A> au début de la méthode `OnStart()`.  
  
    ```c#  
    protected override void OnStart(string[] args)  
    {  
        System.Diagnostics.Debugger.Launch();  
     }  
    ```  
  
2.  Démarrez le service \(avec `net start` ou à partir de la fenêtre **Services**\).  
  
     Une boîte de dialogue similaire à celle ci\-dessous doit s’afficher :  
  
     ![OnStartDebug](../debugger/media/onstartdebug.png "OnStartDebug")  
  
3.  Sélectionnez **Oui, déboguer \<nom\_service\>**.  
  
4.  Dans la fenêtre du débogueur juste\-à\-temps, sélectionnez la version de Visual Studio à utiliser pour le débogage.  
  
     ![JustInTimeDebugger](~/debugger/media/justintimedebugger.png "JustInTimeDebugger")  
  
5.  Une nouvelle instance de Visual Studio démarre, mais son exécution s’arrête à la méthode `Debugger.Launch()`.  
  
## Voir aussi  
 [Sécurité du débogueur](../debugger/debugger-security.md)   
 [Débogage du code managé](../debugger/debugging-managed-code.md)