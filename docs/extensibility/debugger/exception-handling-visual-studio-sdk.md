---
title: "Gestion des exceptions (Kit de d&#233;veloppement logiciel Visual Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "débogage [Debugging SDK], gestion des exceptions"
ms.assetid: 7279dc16-db14-482c-86b8-7b3da5a581d2
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# Gestion des exceptions (Kit de d&#233;veloppement logiciel Visual Studio)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Les éléments suivants décrivent le processus qui se produit lorsque les exceptions sont levées.  
  
## Processus de gestion des exceptions  
  
1.  Lorsqu'une exception est levée premier, mais avant qu'elle est gérée par le gestionnaire d'exceptions dans le programme débogué, le moteur de \(DE\) débogage envoie [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) au gestionnaire de débogage de session \(SDM\) en tant qu'événement arrêtant.  `IDebugExceptionEvent2` est envoyé si seuls les paramètres pour l'exception \(spécifiée dans la boîte de dialogue exceptions dans le package de débogage\) spécifier que l'utilisateur souhaite que sur des notifications des exceptions de première chance.  
  
2.  Le SDM appelle [IDebugExceptionEvent2 : : GetException](../Topic/IDebugExceptionEvent2::GetException.md) pour obtenir la propriété de l'exception.  
  
3.  Le package de débogage appelle [IDebugExceptionEvent2 : : CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) pour déterminer les options de présenter à l'utilisateur.  
  
4.  Le package de débogage demande à l'utilisateur comment gérer l'exception en ouvrant une boîte de dialogue d'exception de première\-chance.  
  
5.  si l'utilisateur choisit de continuer, le SDM appelle [IDebugExceptionEvent2 : : CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md).  
  
    -   Si la méthode retourne S\_OK, appelle [IDebugExceptionEvent2 : : PassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-passtodebuggee.md).  
  
         ou  
  
         Si la méthode retourne S\_FALSE, le programme débogué est donné seconde chance de gérer l'exception.  
  
6.  Si le programme débogué n'a aucun gestionnaire d'une exception de seconde chance, le De envoie `IDebugExceptionEvent2` au SDM comme **EVENT\_SYNCHRONIZATION\_STOP**.  
  
7.  Le package de débogage demande à l'utilisateur comment gérer l'exception en ouvrant une boîte de dialogue d'exception de première\-chance.  
  
8.  Le package de débogage appelle [IDebugExceptionEvent2 : : CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) pour déterminer les options de présenter à l'utilisateur.  
  
9. Le package de débogage demande à l'utilisateur comment gérer l'exception en ouvrant une boîte de dialogue de seconde chance d'exception.  
  
10. Si la méthode retourne S\_OK, appelle `IDebugExceptionEvent2::PassToDebuggee`.  
  
## Voir aussi  
 [Appeler les événements de débogueur](../../extensibility/debugger/calling-debugger-events.md)