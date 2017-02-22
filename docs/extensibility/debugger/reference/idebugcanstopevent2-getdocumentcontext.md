---
title: "IDebugCanStopEvent2::GetDocumentContext | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugCanStopEvent2::GetDocumentContext"
helpviewer_keywords: 
  - "IDebugCanStopEvent2::GetDocumentContext"
ms.assetid: 936a6c4e-30c5-4c7e-9ad5-910cc605a4b5
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugCanStopEvent2::GetDocumentContext
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

obtient le contexte de document qui décrit l'emplacement de cet événement.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetDocumentContext (   
   IDebugDocumentContext2** ppDocCxt  
);  
```  
  
```c#  
int GetDocumentContext (   
   out IDebugDocumentContext2 ppDocCxt  
);  
```  
  
#### Paramètres  
 `ppDocCxt`  
 \[out\]  Retourne l'interface d' [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) qui représente une position dans un document de fichier source correspondant à l'emplacement actuel du code.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 En général, le contexte de document peut être considéré comme un emplacement dans un fichier source.  
  
 pour obtenir le contexte de code, qui est orienté vers l'instruction de code, appelez la méthode d' [GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md) .  
  
## Voir aussi  
 [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)   
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)