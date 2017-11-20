---
title: IDebugObject2::GetICorDebugValue | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugObject2::GetICorDebugValue
helpviewer_keywords: IDebugObject2::GetICorDebugValue method
ms.assetid: bcd4355d-3fbe-483f-bb23-a44348323c6a
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6b1d1c05b6156cb38222eeedb287de4b3fc52b18
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugobject2geticordebugvalue"></a>IDebugObject2::GetICorDebugValue
Obtient un objet de code managé qui représente la valeur associée à cet objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetICorDebugValue(  
   IUnknown** ppUnk  
);  
```  
  
```csharp  
int GetICorDebugValue(  
   out object ppUnk  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppUnk`  
 [out] `IUnknown` interface qui représente cet alias. Cette interface peut être interrogée pour la `ICorDebugValue` interface.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne S_OK ; Sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Remarques  
 Le `ICorDebugValue` objet est une interface de Common Language Runtime qui représente une valeur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)