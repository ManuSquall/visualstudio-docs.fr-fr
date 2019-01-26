---
title: IDebugObject::SetValue | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugObject::SetValue
helpviewer_keywords:
- IDebugObject::SetValue method
ms.assetid: d652e09c-cdc1-4519-8116-d7c743f5679b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4ba9b3983f3d6cab2525c391153457d362d2ad05
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55038394"
---
# <a name="idebugobjectsetvalue"></a>IDebugObject::SetValue
Définit la valeur de l’objet à partir d’une série consécutive d’octets.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetValue(   
   BYTE* pValue,  
   UINT  nSize  
);  
```  
  
```csharp  
int SetValue(  
   byte[] pValue,   
   uint   nSize  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pValue`  
 [in] Un tableau d’octets représentant la nouvelle valeur.  
  
 `nSize`  
 [in] La taille de la valeur en octets.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne S_OK ; Sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Les valeurs du tableau sont copiées dans la collection [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) objet, en remplaçant toute valeur existante. La taille de la nouvelle valeur peut être supérieure ou inférieure à la valeur existante. Cela `IDebugObject` ne peut pas être une référence null.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)