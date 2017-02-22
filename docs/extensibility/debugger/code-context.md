---
title: "Contexte de code | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "débogage [Debugging SDK], contextes"
ms.assetid: 65e4d37a-086b-426e-9394-a3534967fd59
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# Contexte de code
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] débogage, **un contexte de code**:  
  
-   Fournit une abstraction d'une position dans le code connu au moteur de débogage \(DE\).  pour la plupart des architectures à l'exécution aujourd'hui, un contexte de code peut être considéré comme une adresse dans le flux d'instructions d'un programme.  Pour les langues non traditionnels, où le code ne peut être représenté par l'instruction, un contexte de code peut être représenté par d'autres moyens.  
  
-   Décrit la position actuelle dans le flux d'exécution du programme en cours de débogage.  
  
-   Existe uniquement lorsqu'un programme a arrêté par un point d'arrêt.  
  
-   a un contexte de document associé.  
  
-   est implémenté par une interface d' [IDebugCodeContext2](../../extensibility/debugger/reference/idebugcodecontext2.md) .  
  
## Voir aussi  
 [Contexte de document](../../extensibility/debugger/document-context.md)   
 [Contextes de débogueur](../../extensibility/debugger/debugger-contexts.md)