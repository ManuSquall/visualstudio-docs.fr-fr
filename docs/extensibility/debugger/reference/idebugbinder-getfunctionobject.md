---
title: IDebugBinder::GetFunctionObject | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugBinder::GetFunctionObject
helpviewer_keywords: IDebugBinder::GetFunctionObject method
ms.assetid: 8fb789df-8f30-420d-8ca5-bb496a6738f1
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 8c46de6a59e8ad0f5bba1b6b1c88b69681e74a2b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="idebugbindergetfunctionobject"></a>IDebugBinder::GetFunctionObject
Cette méthode obtient un [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) objet utilisé pour créer des paramètres de fonction.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetFunctionObject(   
   IDebugFunctionObject **ppFunction  
);  
```  
  
```csharp  
int GetFunctionObject(  
   out IDebugFunctionObject ppFunction  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppFunction`  
 [out] Retourne le [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) interface qui permet de créer des paramètres de fonction.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne S_OK ; Sinon, retourne un code d’erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)