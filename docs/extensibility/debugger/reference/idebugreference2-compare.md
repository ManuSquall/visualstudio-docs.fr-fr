---
title: "IDebugReference2::Compare | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugReference2::Compare"
helpviewer_keywords: 
  - "IDebugReference2::Compare"
ms.assetid: 3361c495-2673-4b7c-82e3-dee74e1fa58d
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugReference2::Compare
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Compare une référence à un autre.  Réservé à une utilisation future.  
  
## Syntaxe  
  
```cpp#  
HRESULT Compare (   
   REFERENCE_COMPARE dwCompare,  
   IDebugReference2* pReference  
);  
```  
  
```c#  
int Compare (   
   enum_REFERENCE_COMPARE dwCompare,  
   IDebugReference2       pReference  
);  
```  
  
#### Paramètres  
 `dwCompare`  
 \[in\]  Une valeur de l'énumération de [REFERENCE\_COMPARE](../../../extensibility/debugger/reference/reference-compare.md) à laquelle spécifie l'opération de comparaison, par exemple, égal, moins que, ou supérieur à.  
  
 `pReference`  
 \[in\]  Un objet d' [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) qui représente la référence à comparer la valeur.  
  
## Valeur de retour  
 Retourne toujours `E_NOTIMPL`.  
  
## Voir aussi  
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)   
 [REFERENCE\_COMPARE](../../../extensibility/debugger/reference/reference-compare.md)