---
title: IDebugPointerField::GetDereferencedField | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugPointerField::GetDereferencedField
helpviewer_keywords: IDebugPointerField::GetDereferencedField method
ms.assetid: 8de988ab-cd79-4287-be72-3c900f2fe407
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: f881a7ad6f11b4c916dad8af184d84a434f3e510
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="idebugpointerfieldgetdereferencedfield"></a>IDebugPointerField::GetDereferencedField
Cette méthode retourne le type d’objet vers lequel pointe cet objet de pointeur.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetDereferencedField(  
   IDebugField** ppField  
);  
```  
  
```csharp  
int GetDereferencedField(  
   out IDebugField ppField  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppField`  
 [out] Retourne un [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) décrivant le type d’objet cible.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Par exemple, si le [IDebugPointerField](../../../extensibility/debugger/reference/idebugpointerfield.md) objet pointe vers un entier, le [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) type retourné par cette méthode décrit ce type d’entier.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugPointerField](../../../extensibility/debugger/reference/idebugpointerfield.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)