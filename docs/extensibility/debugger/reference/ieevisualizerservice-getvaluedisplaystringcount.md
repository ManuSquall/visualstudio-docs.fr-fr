---
title: "IEEVisualizerService::GetValueDisplayStringCount | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IEEVisualizerService::GetValueDisplayStringCount"
  - "GetValueDisplayStringCount"
ms.assetid: d683a833-fbfb-4042-84df-6905124a268a
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IEEVisualizerService::GetValueDisplayStringCount
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Récupère le nombre de chaînes de valeur pour afficher pour la propriété ou le champ spécifié.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetValueDisplayStringCount (  
   DWORD         displayKind,   
   IDebugField * propertyOrField,   
   ULONG *       pcelt  
);  
```  
  
```c#  
int GetValueDisplayStringCount (  
   uint        displayKind,   
   IDebugField propertyOrField,   
   out ulong   pcelt  
);  
```  
  
#### Paramètres  
 `displayKind`  
 \[in\]  Valeur de l'énumération de [DisplayKind](../../../extensibility/debugger/reference/displaykind.md) .  
  
 `propertyOrField`  
 \[in\]  une interface d' [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) qui représente une propriété ou un champ.  
  
 `pcelt`  
 \[out\]  Retourne le nombre de chaînes de valeur à afficher.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)