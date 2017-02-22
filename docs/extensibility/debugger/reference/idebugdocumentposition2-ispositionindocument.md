---
title: "IDebugDocumentPosition2::IsPositionInDocument | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDocumentPosition2::IsPositionInDocument"
helpviewer_keywords: 
  - "IDebugDocumentPosition2::IsPositionInDocument"
ms.assetid: d5cf57cb-b93b-4e1d-bec9-185f4fe8668d
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugDocumentPosition2::IsPositionInDocument
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

détermine si la position de document est contenue dans le document donné.  
  
## Syntaxe  
  
```cpp#  
HRESULT IsPositionInDocument(   
   IDebugDocument2* pDoc  
);  
```  
  
```c#  
int IsPositionInDocument(   
   IDebugDocument2 pDoc  
);  
```  
  
#### Paramètres  
 `pDoc`  
 \[in\]  L'objet d' [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) qui représente le candidat contenant des documents.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 Cette méthode est utilisée essentiellement dans des points d'arrêt dans les interfaces d' [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) .  Comme des documents sont chargés, la position du point d'arrêt est appelé pour déterminer si le document contient cette position.  
  
## Voir aussi  
 [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)   
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)