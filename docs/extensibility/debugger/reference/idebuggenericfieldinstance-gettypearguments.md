---
title: "IDebugGenericFieldInstance::GetTypeArguments | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "GetTypeArguments"
  - "IDebugGenericFieldInstance::GetTypeArguments"
ms.assetid: 6e7e0f95-181a-4805-adb3-c2407de0ab93
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugGenericFieldInstance::GetTypeArguments
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Récupère les arguments de paramètre de type pour cette instance.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetTypeArguments(  
   ULONG32       cArgs,  
   IDebugField** ppArgs,  
   ULONG32*      pcArgs  
);  
```  
  
```c#  
int GetTypeArguments(  
   uint              cArgs,  
   out IDebugField[] ppArgs,  
   ref uint          pcArgs  
);  
```  
  
#### Paramètres  
 `cArgs`  
 \[in\]  Nombre de paramètres de type.  
  
 `ppArgs`  
 \[out\]  Retourne un tableau de paramètres de type.  
  
 `pcArgs`  
 \[in, out\]  Nombre de membres de la matrice d' `ppArgs` .  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IDebugGenericFieldInstance](../../../extensibility/debugger/reference/idebuggenericfieldinstance.md)