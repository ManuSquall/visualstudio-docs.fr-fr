---
title: "IEnumDebugFields::GetCount | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugFields::GetCount"
helpviewer_keywords: 
  - "IEnumDebugFields::GetCount (méthode)"
ms.assetid: 3f471b40-4db3-49f7-b504-58b2476eef74
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# IEnumDebugFields::GetCount
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Cette méthode retourne le nombre d'éléments dans l'énumération.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetCount(  
   [out] ULONG* pcelt  
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
 Cette méthode ne fait pas partie de l'interface traditionnelles d'énumération COM qui spécifie que seul le besoin suivant, de clone, de saut, et de remise d'être implémenté.  
  
## Voir aussi  
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)