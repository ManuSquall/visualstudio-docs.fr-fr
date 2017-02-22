---
title: "IDebugCanStopEvent2::GetCodeContext | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugCanStopEvent2::GetCodeContext"
helpviewer_keywords: 
  - "IDebugCanStopEvent2::GetCodeContext"
ms.assetid: eecf08b6-f9b7-4358-941b-3a448a92ac62
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugCanStopEvent2::GetCodeContext
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

obtient le contexte de code qui décrit l'emplacement de cet événement.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetCodeContext(   
   IDebugCodeContext2** ppCodeContext  
);  
```  
  
```c#  
int GetCodeContext(   
   out IDebugCodeContext2 ppCodeContext  
);  
```  
  
#### Paramètres  
 `ppCodeContext`  
 \[out\]  Retourne l'objet d' [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) qui représente l'emplacement actuel du code.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 pour la plupart des architectures à l'exécution, un contexte de code peut être considéré comme une adresse dans un flux de données de l'exécution du programme, pointant sur une instruction spécifique.  
  
 pour obtenir le contexte de document, qui est orienté vers des lignes de code source, appelez la méthode d' [GetDocumentContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md) .  
  
## Voir aussi  
 [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [GetDocumentContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md)