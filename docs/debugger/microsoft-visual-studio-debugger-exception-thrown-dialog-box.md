---
title: "D&#233;bogueur Microsoft Visual Studio (Exception lev&#233;e), bo&#238;te de dialogue | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.exceptions.thrown"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Débogueur Microsoft Visual Studio (Exception levée) (boîte de dialogue)"
  - "gestion des exceptions, pendant le débogage"
  - "débogueur, exceptions"
  - "levée d’exceptions, pendant le débogage"
ms.assetid: 1fe98d10-c8f9-4b39-a920-99169bfd542e
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# D&#233;bogueur Microsoft Visual Studio (Exception lev&#233;e), bo&#238;te de dialogue
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Une exception s'est produite dans votre programme.  Cette boîte de dialogue indique le type d'exception levé.  Votre code doit gérer cette exception.  Pour ce faire, vous avez le choix entre les options suivantes :  
  
 **Break**  
 Autorise l'arrêt de l'exécution dans le débogueur.  Le gestionnaire d'exceptions n'est pas appelé avant l'arrêt.  Si vous poursuivez l'exécution après l'arrêt, le gestionnaire d'exceptions est appelé.  
  
 **Continue**  
 Autorise la poursuite de l'exécution en donnant au gestionnaire d'exceptions une chance de traiter cette exception.  Cette option n'est pas disponible pour certains types d'exceptions.  **Continue** autorise l'application à continuer.  Dans une application native, l'exception est de nouveau levée.  Dans une application managée, cela entraîne l'arrêt du programme ou la gestion de l'exception par une application hôte.  
  
> [!NOTE]
>  Vous ne pouvez pas continuer l'exécution à la suite de la levée d'une exception non traitée dans du code managé.  Si vous sélectionnez **Continue** dans pareil cas, le débogage s'arrêtera.  
  
 **Ignore**  
 Autorise la poursuite de l'exécution sans appeler le gestionnaire d'exceptions.  Comme le gestionnaire d'exceptions n'est pas appelé, il risque de s'ensuivre des conséquences indésirables, notamment de nouvelles exceptions et des erreurs.  Cette option n'est pas disponible pour certains types d'exceptions.  
  
## Voir aussi  
 [Gestion des exceptions avec le débogueur](../debugger/managing-exceptions-with-the-debugger.md)   
 [Meilleures pratiques pour les exceptions](../Topic/Best%20Practices%20for%20Exceptions.md)   
 [Exception Handling](/visual-cpp/windows/exception-handling-cpp-component-extensions)