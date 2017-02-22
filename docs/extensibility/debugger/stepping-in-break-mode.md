---
title: "Ex&#233;cution pas &#224; pas en Mode arr&#234;t | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "en mode arrêt, exécuter pas à pas"
  - "exécution pas à pas, en mode arrêt"
  - "débogage (débogage SDK), pas à pas en mode arrêt"
ms.assetid: b08dc8ee-6c63-4462-a097-6f525cfbb35a
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# Ex&#233;cution pas &#224; pas en Mode arr&#234;t
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Les éléments suivants décrivent le processus qui se produit lorsque le débogueur est en mode arrêt et doit exécuter le code pas \- :  
  
## Processus de progression  
  
1.  appel [IDebugProgram2 : : étape](../../extensibility/debugger/reference/idebugprogram2-step.md) avec des arguments de [STEPKIND](../../extensibility/debugger/reference/stepkind.md) et de [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) pour exécuter une étape.  
  
2.  Lorsque l'étape est terminée, envoyez [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) en tant qu'événement arrêtant.  
  
## Voir aussi  
 [Appeler les événements de débogueur](../../extensibility/debugger/calling-debugger-events.md)