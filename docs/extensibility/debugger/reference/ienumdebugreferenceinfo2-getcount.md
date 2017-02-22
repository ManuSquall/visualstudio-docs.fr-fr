---
title: "IEnumDebugReferenceInfo2::GetCount | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugReferenceInfo2::GetCount"
helpviewer_keywords: 
  - "IEnumDebugReferenceInfo2::GetCount"
ms.assetid: e62706e0-d2cd-48fb-8fdf-444463c651ab
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IEnumDebugReferenceInfo2::GetCount
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Retourne le nombre d'éléments dans l'énumération.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetCount(  
   ULONG* pcelt  
);  
```  
  
```c#  
int GetCount(  
   out uint pcelt  
);  
```  
  
#### Paramètres  
 `pcelt`  
 \[out\]  Retourne le nombre d'éléments dans l'énumération.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 Cette méthode ne fait pas partie de l'interface traditionnelles d'énumération COM qui spécifie que seuls `Next`, `Clone`, `Skip`les méthodes, et d' `Reset` doivent être implémentés.  
  
## Voir aussi  
 [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)