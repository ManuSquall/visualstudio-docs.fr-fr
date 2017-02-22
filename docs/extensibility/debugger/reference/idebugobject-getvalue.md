---
title: "IDebugObject::GetValue | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugObject::GetValue"
helpviewer_keywords: 
  - "IDebugObject::GetValue (méthode)"
ms.assetid: eec6051e-8ecb-49fa-bdd4-dd786f211692
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugObject::GetValue
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Obtient la valeur de l'objet comme une série consécutive d'octets.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetValue(   
   BYTE* pValue,  
   UINT  nSize  
);  
```  
  
```c#  
int GetValue(  
   ref byte[] pValue,   
   uint nSize  
);  
```  
  
#### Paramètres  
 `pValue`  
 \[in, out\]  Un tableau qui est effectuée avec une série consécutive d'octets représentant la valeur de l'objet.  
  
 `nSize`  
 \[in\]  Nombre maximal d'octets à récupérer.  
  
## Valeur de retour  
 En cas de réussite, retourne S\_OK ; sinon, retourne un code d'erreur.  
  
## Notes  
 Obtenez total d'octets de valeur qui peuvent être récupérés en appelant la méthode d' [GetSize](../../../extensibility/debugger/reference/idebugobject-getsize.md) .  
  
## Voir aussi  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)