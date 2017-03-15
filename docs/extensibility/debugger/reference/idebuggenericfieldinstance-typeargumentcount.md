---
title: "IDebugGenericFieldInstance::TypeArgumentCount | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "TypeArgumentCount"
  - "IDebugGenericFieldInstance::TypeArgumentCount"
ms.assetid: e662c5ea-a5c1-478e-a268-5980dadffcd1
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugGenericFieldInstance::TypeArgumentCount
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Retourne le nombre de type des arguments de paramètre pour cette instance.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT TypeArgumentCount(  
   ULONG32* pcArgs  
);  
```  
  
```c#  
int TypeArgumentCount(  
   ref uint pcArgs  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pcArgs`  
 [dans, out] Nombre d’arguments de paramètre de type pour cette instance.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; Sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Remarques  
 Par exemple, si liste \< int>, cette méthode retourne 1 et, si liste \< int, float2 > cette méthode renvoie la valeur 2. Cette méthode retourne 0 s’il n’existe aucun argument de type.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugGenericFieldInstance](../../../extensibility/debugger/reference/idebuggenericfieldinstance.md)