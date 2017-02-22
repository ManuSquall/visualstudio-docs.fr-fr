---
title: "IDebugProgram2::GetENCUpdate | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgram2::GetENCUpdate"
helpviewer_keywords: 
  - "IDebugProgram2::GetENCUpdate"
ms.assetid: 9832aac8-6320-4fd8-91dd-2a0852febb00
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# IDebugProgram2::GetENCUpdate
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Cette méthode extrait la modification et continue la mise à jour \(P.J.\) pour ce programme.  Un moteur de débogage personnalisé retourne toujours `E_NOTIMPL`.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetENCUpdate(   
   IUnknown** ppUpdate  
);  
```  
  
```c#  
int GetENCUpdate(  
   out object ppUpdate  
);  
```  
  
#### Paramètres  
 `ppUpdate`  
 \[out\]  Retourne une interface interne qui peut être utilisée pour mettre à jour ce programme.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
> [!NOTE]
>  Un moteur de débogage personnalisé doit toujours retourner `E_NOTIMPL`.  
  
## Voir aussi  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)