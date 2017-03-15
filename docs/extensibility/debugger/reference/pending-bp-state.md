---
title: "PENDING_BP_STATE | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "PENDING_BP_STATE"
helpviewer_keywords: 
  - "Énumération de PENDING_BP_STATE"
ms.assetid: ac04ad72-fa92-4a15-ade2-0d0bbbadfc7f
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# PENDING_BP_STATE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Spécifie l'état d'un point d'arrêt en attente \(un point d'arrêt qui n'a pas encore été lié\).  
  
## Syntaxe  
  
```cpp#  
enum enum_PENDING_BP_STATE {   
   PBPS_NONE     = 0x0000,  
   PBPS_DELETED  = 0x0001,  
   PBPS_DISABLED = 0x0002,  
   PBPS_ENABLED  = 0x0003  
};  
typedef DWORD PENDING_BP_STATE;  
```  
  
```c#  
public enum enum_PENDING_BP_STATE {   
   PBPS_NONE     = 0x0000,  
   PBPS_DELETED  = 0x0001,  
   PBPS_DISABLED = 0x0002,  
   PBPS_ENABLED  = 0x0003  
};  
```  
  
## Membres  
 PBPS\_NONE  
 L'espace réservé à zéro.  cette valeur n'est jamais retournée.  
  
 PBPS\_DELETED  
 indique que le point d'arrêt en attente a été supprimé.  
  
 PBPS\_DISABLED  
 indique que le point d'arrêt en attente est désactivé.  
  
 PBPS\_ENABLED  
 indique que le point d'arrêt en attente est activé.  
  
## Notes  
 utilisation en tant que membre d' `state` de la structure de [PENDING\_BP\_STATE\_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md) .  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [PENDING\_BP\_STATE\_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md)