---
title: "IDebugProgram2::EnumCodeContexts | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgram2::EnumCodeContexts"
helpviewer_keywords: 
  - "IDebugProgram2::EnumCodeContexts"
ms.assetid: 478e06a2-07bb-4841-8887-deab0f42ebd0
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProgram2::EnumCodeContexts
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

extrait une liste des contextes de code pour une position donnée dans un fichier source.  
  
## Syntaxe  
  
```cpp#  
HRESULT EnumCodeContexts(   
   IDebugDocumentPosition2*  pDocPos,  
   IEnumDebugCodeContexts2** ppEnum  
);  
```  
  
```c#  
int EnumCodeContexts(   
   IDebugDocumentPosition2     pDocPos,  
   out IEnumDebugCodeContexts2 ppEnum  
);  
```  
  
#### Paramètres  
 `pDocPos`  
 \[in\]  Un objet d' [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md) représentant une position abstraite dans un fichier source connu à l'IDE.  
  
 `ppEnum`  
 \[out\]  Retourne un objet d' [IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md) qui contient une liste des contextes de code.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 Cette méthode permet au gestionnaire ou à l'IDE \(SDM\) de débogage de session pour mapper une position de fichier source dans une position du code.  Plusieurs contexte de code est retourné si la source génère plusieurs blocs de code \(par exemple, les modèles C\+\+\).  
  
## Voir aussi  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)   
 [IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)