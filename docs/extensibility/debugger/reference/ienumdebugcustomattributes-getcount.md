---
title: "IEnumDebugCustomAttributes::GetCount | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumCustomAttributes::GetCount"
helpviewer_keywords: 
  - "IEnumDebugCustomAttributes::GetCount"
ms.assetid: fafe826f-4ebf-4572-b2a3-d5dd2916c12f
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IEnumDebugCustomAttributes::GetCount
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

obtient le nombre d'attributs personnalisés dans un énumérateur.  
  
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
 Cette méthode ne fait pas partie de l'interface traditionnelles d'énumération COM qui spécifie que cet `Next`, `Clone`, `Skip`, et le besoin d' `Reset` à implémenter.  
  
## Voir aussi  
 [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)