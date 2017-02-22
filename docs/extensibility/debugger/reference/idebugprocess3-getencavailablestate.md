---
title: "IDebugProcess3::GetENCAvailableState | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProcess3::GetENCAvailableState"
helpviewer_keywords: 
  - "IDebugProcess3::GetENCAvailableState"
ms.assetid: 98a5d527-8a72-476c-8e92-0bff3d97c195
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugProcess3::GetENCAvailableState
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Cette méthode extrait la modification actuelle et reprend l'état du processus.  Un fournisseur de port doit toujours retourner `E_NOTIMPL`.  
  
## Syntaxe  
  
```cpp  
HRESULT GetENCAvailableState(  
   EncUnavailableReason* pReason  
);  
```  
  
```c#  
int GetENCAvailableState(  
   EncUnavailableReason[] pReason  
);  
```  
  
#### Paramètres  
 `pReason`  
 \[out\]  une valeur de l'énumération d' [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md) .  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, le code d'erreur de retour.  
  
> [!NOTE]
>  Un fournisseur de port doit toujours retourner `E_NOTIMPL`.  
  
## Notes  
 Ce rapport peut être affecté par [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md).  
  
## Voir aussi  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)   
 [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md)