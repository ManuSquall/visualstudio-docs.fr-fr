---
title: IDebugBinder::ResolveDynamicType | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugBinder::ResolveDynamicType
helpviewer_keywords: IDebugBinder::ResolveDynamicType method
ms.assetid: 2c36ef92-5b44-4cfd-988e-54a2e5a6710c
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3dcd4b946e5b8c2d4cd7c3d77c77140e66699cef
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugbinderresolvedynamictype"></a>IDebugBinder::ResolveDynamicType
Cette méthode retourne le type exact d’une variable.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT ResolveDynamicType (  
   IDebugDynamicField *pDynamic,  
   IDebugField       **ppResolved  
);  
```  
  
```csharp  
int ResolveDynamicType(  
   IDebugDynamicField pDynamic,   
   out IDebugField    ppResolved  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pDynamic`  
 [in] Un [IDebugDynamicField](../../../extensibility/debugger/reference/idebugdynamicfield.md) représentant un type d’une variable.  
  
 `ppResolved`  
 [out] Retourne un [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) en donnant des informations spécifiques sur le type de variable.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [IDebugDynamicField](../../../extensibility/debugger/reference/idebugdynamicfield.md)