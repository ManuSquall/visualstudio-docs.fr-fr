---
title: IDebugObject::IsNullReference | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugObject::IsNullReference
helpviewer_keywords:
- IDebugObject::IsNullReference method
ms.assetid: 6dbfcdb0-954f-4486-8fac-7ea8d003e3a9
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 021d7d8b7c1203aab68a93efe8581f66dec698f9
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54975268"
---
# <a name="idebugobjectisnullreference"></a>IDebugObject::IsNullReference
Teste si cet objet est une référence null.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT IsNullReference(   
   BOOL* pfIsNull  
);  
```  
  
```csharp  
int IsNullReference(  
   out int pfIsNull  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pfIsNull`  
 [out] Retourne zéro (`TRUE`) si cet objet est une référence null ; sinon, retourne la valeur zéro (`FALSE`).  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne S_OK ; Sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Une référence null signifie qu’un objet vide ou un objet qui n’a pas été affecté à.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)