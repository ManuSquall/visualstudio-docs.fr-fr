---
title: IDebugObject::IsEqual | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugObject::IsEqual
helpviewer_keywords:
- IDebugObject::IsEqual method
ms.assetid: 4b76e663-ef2e-41ff-9be1-bf26d666a34a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b801594c4e3dd1edb04ae0d29dfe6c814fa4a094
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54954447"
---
# <a name="idebugobjectisequal"></a>IDebugObject::IsEqual
Compare un objet avec cet objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT IsEqual(   
   IDebugObject* pObject,  
   BOOL*         pfIsEqual  
);  
```  
  
```csharp  
int IsEqual(  
   IDebugObject pObject,  
   out int      pfIsEqual  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pObject`  
 [in] Un [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) objet représentant l’objet à comparer à.  
  
 `pfIsEqual`  
 [out] Retourne zéro (`TRUE`) si les valeurs des objets sont égaux ; sinon, retourne la valeur zéro (`FALSE`).  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne S_OK ; Sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 En règle générale, cette méthode peut comparer les adresses des valeurs représentées par le `pObject` paramètre et cela [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) objet ; si les adresses sont identiques, les objets peuvent être considérées comme égales.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)