---
title: "IDebugEnumField::GetUnderlyingSymbol | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEnumField::GetUnderlyingSymbol"
helpviewer_keywords: 
  - "IDebugEnumField::GetUnderlyingSymbol (méthode)"
ms.assetid: c3b8a117-6708-4cfd-8ffc-5f007d706bc5
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# IDebugEnumField::GetUnderlyingSymbol
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Cette méthode retourne [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) qui représente le nom de l'énumération.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetUnderlyingSymbol(  
   IDebugField** ppField  
);  
```  
  
```c#  
int GetUnderlyingSymbol(  
   out IDebugField ppField  
);  
```  
  
#### Paramètres  
 `ppField`  
 \[out\]  Retourne [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) décrivant le nom de cette énumération.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 Le nom de l'énumération contient également le type de l'énumération, qui est liée à un emplacement mémoire à l'aide de [Lier](../../../extensibility/debugger/reference/idebugbinder-bind.md).  
  
## Voir aussi  
 [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [Lier](../../../extensibility/debugger/reference/idebugbinder-bind.md)