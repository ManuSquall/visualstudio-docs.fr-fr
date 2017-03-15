---
title: "IDebugEnumField::GetStringFromValue | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEnumField::GetStringFromValue"
helpviewer_keywords: 
  - "IDebugEnumField::GetStringFromValue (méthode)"
ms.assetid: 5f95fd0c-fdce-497f-9f54-2ad8749494e9
caps.latest.revision: 5
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 5
---
# IDebugEnumField::GetStringFromValue
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Cette méthode extrait le nom de la constante d'énumération données sa valeur.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetStringFromValue(  
   ULONGLONG value,  
   BSTR*     pbstrValue  
);  
```  
  
```c#  
int GetStringFromValue(  
   ulong      value,  
   out string pbstrValue  
);  
```  
  
#### Paramètres  
 `value`  
 \[in\]  La valeur pour laquelle obtenir le nom de la constante d'énumération.  
  
 `pbstrValue`  
 \[out\]  Retourne le nom de la constante d'énumération.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, la `S_FALSE` si la valeur n'a pas de nom associé, ou retourne un code d'erreur.  
  
## Notes  
 S'il existe plusieurs nom associé à la même valeur, le prénom définies dans l'énumération est retourné.  
  
## Voir aussi  
 [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)