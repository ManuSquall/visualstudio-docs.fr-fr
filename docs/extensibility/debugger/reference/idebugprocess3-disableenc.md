---
title: "IDebugProcess3::DisableENC | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProcess3::DisableENC"
helpviewer_keywords: 
  - "IDebugProcess3::DisableENC"
ms.assetid: cffdbdac-4d76-4aeb-aa55-5d0410db99f1
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugProcess3::DisableENC
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Cette méthode efface explicitement la modification et continue sur ce processus \(et tous les programmes qu'il contient\).  Un fournisseur de port doit toujours retourner `E_NOTIMPL`.  
  
## Syntaxe  
  
```cpp  
HRESULT DisableENC(  
   EncUnavailableReason reason  
);  
```  
  
```c#  
   EncUnavailableReason reason  
);  
```  
  
#### Paramètres  
 `reason`  
 \[in\]  une valeur de l'énumération d' [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md) .  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, le code d'erreur de retour.  
  
> [!NOTE]
>  Un fournisseur de port doit toujours retourner `E_NOTIMPL`.  
  
## Notes  
 Une fois la modification et Continue est désactivée pour un processus, il peut être réactivées uniquement en redémarrant le processus.  
  
## Voir aussi  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md)