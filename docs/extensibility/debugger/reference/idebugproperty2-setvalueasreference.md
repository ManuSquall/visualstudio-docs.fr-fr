---
title: "IDebugProperty2::SetValueAsReference | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProperty2::SetValueAsReference"
helpviewer_keywords: 
  - "IDebugProperty2::SetValueAsReference (méthode)"
ms.assetid: 341b1b89-4ab8-4e1c-abe2-fb955df5c6b0
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugProperty2::SetValueAsReference
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

définit la valeur de cette propriété à la valeur de la référence donnée.  
  
## Syntaxe  
  
```cpp#  
HRESULT SetValueAsReference(  
   IDebugReference2** rgpArgs,  
   DWORD              dwArgCount,  
   IDebugReference2*  pValue,  
   DWORD              dwTimeout  
);  
```  
  
```c#  
int SetValueAsReference(  
   IDebugReference2[] rgpArgs,  
   uint               dwArgCount,  
   IDebugReference2   pValue,  
   uint               dwTimeout  
);  
```  
  
#### Paramètres  
 `rgpArgs`  
 \[in\]  Un tableau des arguments à passer à l'accesseur Set de propriété de code managé.  Si l'accesseur Set de propriété ne prend pas d'arguments et si cet objet d' [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) ne fait pas référence à un tel accesseur Set de propriété, `rgpArgs` doit être une valeur NULL.  ce paramètre est en général une valeur NULL.  
  
 `dwArgCount`  
 \[in\]  Le nombre d'arguments dans le tableau d' `rgpArgs` .  
  
 `pValue`  
 \[in\]  Une référence, sous la forme d'un objet d' [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) , la valeur à l'utilisation de définir cette propriété.  
  
 `dwTimeout`  
 \[in\]  Combien de temps prendre pour définir la valeur, en millisecondes.  une valeur typique est `INFINITE`.  Cela affecte la durée que toute estimation possible peut prendre.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon retourne un code d'erreur, en général un des éléments suivants :  
  
|Erreur|Description|  
|------------|-----------------|  
|`E_SETVALUEASREFERENCE_NOTSUPPORTED`|définir la valeur d'une référence n'est pas pris en charge.|  
|`E_SETVALUE_VALUE_CANNOT_BE_SET`|La valeur ne peut pas être définie, car cette propriété fait référence à une méthode.|  
|`E_SETVALUE_VALUE_IS_READONLY`|la valeur est en lecture seule et ne peut pas être définie.|  
|`E_NOTIMPL`|Cette méthode n'est pas implémentée.|  
  
## Voir aussi  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)