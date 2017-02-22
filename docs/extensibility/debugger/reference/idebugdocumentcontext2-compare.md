---
title: "IDebugDocumentContext2::Compare | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDocumentContext2::Compare"
helpviewer_keywords: 
  - "IDebugDocumentContext2::Compare"
ms.assetid: 2327b1ba-52d0-42fb-a01e-63cb4b332d2f
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugDocumentContext2::Compare
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Compare ce contexte de document vers un tableau donné de contextes de document.  
  
## Syntaxe  
  
```cpp#  
HRESULT Compare(   
   DOCCONTEXT_COMPARE       compare,  
   IDebugDocumentContext2** rgpDocContextSet,  
   DWORD                    dwDocContextSetLen,  
   DWORD*                   pdwDocContext  
);  
```  
  
```c#  
int Compare(   
   enum_ DOCCONTEXT_COMPARE compare,  
   IDebugDocumentContext2[] rgpDocContextSet,  
   uint                     dwDocContextSetLen,  
   out uint                 pdwDocContext  
);  
```  
  
#### Paramètres  
 `compare`  
 \[in\]  une valeur de l'énumération de [DOCCONTEXT\_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md) qui spécifie le type de comparaison.  
  
 `rgpDocContextSet`  
 \[in\]  Un tableau d'objets d' [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) qui représentent des contextes de document comparés.  
  
 `dwDocContextSetLen`  
 \[in\]  La longueur du tableau de contextes de document à comparer.  
  
 `pdwDocContext`  
 \[out\]  Retourne l'index dans le tableau d' `rgpDocContextSet` du premier contexte de document qui satisfait la comparaison.  
  
## Valeur de retour  
 Retourne `S_OK` si une correspondance a été trouvée.  Retourne `S_FALSE` si aucune correspondance n'a été trouvée.  Sinon, retourne un code d'erreur.  
  
## Notes  
 Les objets d' [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) passés dans le tableau doivent être implémentés par le même moteur de débogage qui implémente l'objet d' `IDebugDocumentContext2` est invité ; sinon, la comparaison est pas valide.  
  
## Voir aussi  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [DOCCONTEXT\_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md)