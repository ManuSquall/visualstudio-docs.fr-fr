---
title: "IDebugDocumentTextEvents2::onUpdateDocumentAttributes | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDocumentTextEvents2::OnUpdateDocumentAttributes"
helpviewer_keywords: 
  - "IDebugDocumentTextEvents2::onUpdateDocumentAttributes"
ms.assetid: 31b7d151-9ce2-438e-b405-f8cc46b9f537
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugDocumentTextEvents2::onUpdateDocumentAttributes
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Informe le récepteur de l'événement que les attributs de document a été mis à jour.  
  
## Syntaxe  
  
```cpp#  
HRESULT onUpdateDocumentAttributes(   
   TEXT_DOC_ATTR_2 textdocattr  
);  
```  
  
```c#  
int onUpdateDocumentAttributes(   
   enum_TEXT_DOC_ATTR_2 textdocattr  
);  
```  
  
#### Paramètres  
 `textdocattr`  
 \[in\]  Une combinaison des indicateurs d'énumération de [TEXT\_DOC\_ATTR\_2](../../../extensibility/debugger/reference/text-doc-attr-2.md) qui spécifie les attributs mis à jour du document.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)   
 [TEXT\_DOC\_ATTR\_2](../../../extensibility/debugger/reference/text-doc-attr-2.md)