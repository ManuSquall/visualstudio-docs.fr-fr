---
title: "IDebugDocumentTextEvents2::onRemoveText | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDocumentTextEvents2::OnRemoveText"
helpviewer_keywords: 
  - "IDebugDocumentTextEvents2::onRemoveText"
ms.assetid: 1ebeabb2-52a1-4ccc-83cd-9ae7c3541783
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugDocumentTextEvents2::onRemoveText
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

informe le package de débogage que le texte a été supprimé du document.  
  
## Syntaxe  
  
```cpp#  
HRESULT onRemoveText(   
   TEXT_POSITION pos,  
   DWORD         dwNumToRemove  
);  
```  
  
```c#  
int onRemoveText(   
   enum_TEXT_POSITION pos,  
   uint               dwNumToRemove  
);  
```  
  
#### Paramètres  
 `pos`  
 \[in\]  Une structure de [TEXT\_POSITION](../../../extensibility/debugger/reference/text-position.md) qui indique où il a été supprimé.  
  
 `dwNumToRemove`  
 \[in\]  Spécifie le nombre de caractères de texte qui ont été supprimés.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)   
 [TEXT\_POSITION](../../../extensibility/debugger/reference/text-position.md)