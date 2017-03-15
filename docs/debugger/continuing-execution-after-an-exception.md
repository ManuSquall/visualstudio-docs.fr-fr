---
title: "Poursuite de l&#39;ex&#233;cution &#224; la suite d&#39;une exception | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
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
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "débogueur, exceptions"
  - "gestion des exceptions, continuer l'exécution après"
  - "Exceptions (boîte de dialogue)"
  - "exceptions, continuer l'exécution après"
  - "exécution, continuer après une exception"
  - "code managé, gestion des exceptions"
  - "exceptions managées, continuer l'exécution après"
  - "exécution d'un programme"
  - "programmes, exécuter"
  - "threads (Visual Studio), continuer l'exécution après des exceptions"
ms.assetid: 6fe97aac-2131-4615-bd92-d3afee741558
caps.latest.revision: 25
caps.handback.revision: 25
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Poursuite de l&#39;ex&#233;cution &#224; la suite d&#39;une exception
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Lorsque le débogueur arrête l'exécution à cause d'une exception, une boîte de dialogue apparaît.  En Visual Basic ou C\#, vous visualisez la boîte de dialogue [Exception Assistant](../Topic/Exception%20Assistant.md) par défaut.  Pour C\+\+, vous voyez la boîte de dialogue **Exception** antérieure.  Si vous utilisez Visual Basic ou C\# mais que vous avez désactivé l'**Assistant Exception** dans la boîte de dialogue **Options**, vous voyez s'afficher la boîte de dialogue **Exception**.  
  
 Lorsque la boîte de dialogue **Assistant Exception** ou **Exception** apparaît, vous pouvez essayer de résoudre le problème qui a provoqué l'exception.  
  
## Code managé  
 Dans le code managé, il est possible de poursuivre l'exécution dans le même thread à la suite d'une exception non gérée.  L'**Assistant Exception** déroule la pile des appels jusqu'au point où l'exception a été levée.  
  
## Code natif  
 En C\/C\+\+ natif, vous avez deux options :  
  
-   Vous pouvez cliquer sur **Arrêter** et essayer de résoudre le problème.  En mode arrêt, vous pouvez dérouler la pile des appels en cliquant avec le bouton droit sur un frame dans la fenêtre **Pile des appels**, puis en sélectionnant **Dérouler sur ce frame** dans le menu contextuel.  Lorsque vous continuez à déboguer, la boîte de dialogue **Exception** réapparaît si vous n'avez pas résolu le problème.  Sinon, la boîte de dialogue **Exception** ne réapparaît pas.  
  
-   Vous pouvez cliquer sur **Continuer** pour poursuivre l'exécution sans essayer de résoudre le problème.  La boîte de dialogue **Exception** réapparaît.  
  
## Code mixte  
 Si une exception non gérée se produit durant le débogage d'un code mixte natif et managé, les contraintes du système d'exploitation empêchent le déroulement de la pile des appels.  Si vous essayez de rembobiner la pile des appels via le menu contextuel, un message d'erreur explique que le débogueur ne peut pas dérouler à partir d'une exception non gérée lors du débogage de code mixte.  
  
## Voir aussi  
 [Gestion des exceptions avec le débogueur](../debugger/managing-exceptions-with-the-debugger.md)