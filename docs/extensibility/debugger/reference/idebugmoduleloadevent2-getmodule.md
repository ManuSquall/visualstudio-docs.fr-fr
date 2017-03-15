---
title: "IDebugModuleLoadEvent2::GetModule | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugModuleLoadEvent2::GetModule"
helpviewer_keywords: 
  - "IDebugModuleLoadEvent2::GetModule"
ms.assetid: c86482bb-9ce5-4e63-bbe0-969b50169424
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugModuleLoadEvent2::GetModule
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Obtient le module chargé ou déchargé.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetModule(   
   IDebugModule2** pModule,  
   BSTR*           pbstrDebugMessage,  
   BOOL*           pbLoad  
);  
```  
  
```c#  
int GetModule(   
   out IDebugModule2 pModule,  
   ref string        pbstrDebugMessage,  
   ref int           pbLoad  
);  
```  
  
#### Paramètres  
 `pModule`  
 \[out\]  Retourne un objet d' [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) qui représente le module qui est chargé ou déchargé.  
  
 `pbstrDebugMessage`  
 \[in, out\]  Retourne un message facultatif décrivant cet événement.  si ce paramètre est une valeur NULL, aucun message n'est demandé.  
  
 `pbLoad`  
 \[in, out\]  Une valeur différente de zéro \(`TRUE`\) si le module charge et zéro \(`FALSE`\) si le module est déchargé.  si ce paramètre est une valeur NULL, aucun état n'est demandé.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)   
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)