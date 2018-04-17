---
title: IDebugPointerObject::SetBytes | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugPointerObject::SetBytes
helpviewer_keywords:
- IDebugPointerObject::SetBytes method
ms.assetid: 8c578b38-38d7-46f3-bb2e-8a730fccd334
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a8234117d7965c4f2e471855d39ed0c3cee1f88c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="idebugpointerobjectsetbytes"></a>IDebugPointerObject::SetBytes
Définit la valeur sur laquelle pointée à partir d’une série d’octets consécutifs.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetBytes(   
   DWORD  dwStart,  
   DWORD  dwCount,  
   BYTE*  pBytes,  
   DWORD* pdwBytes  
);  
```  
  
```csharp  
int SetBytes(  
   uint     dwStart,   
   uint     dwCount,   
   byte[]   pBytes,   
   out uint pdwBytes  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `dwStart`  
 [in] Offset, en octets, à partir du début de l’objet désigné.  
  
 `dwCount`  
 [in] Le nombre d’octets à définir.  
  
 `pBytes`  
 [in] Un tableau d’octets représentant la nouvelle valeur. Cette valeur est stockée dans l’objet, en commençant à l’offset donné.  
  
 `pdwBytes`  
 [out] Retourne que le nombre d’octets à l’origine définie.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne S_OK ; Sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Cette méthode est utilisée si le pointeur comme représenté par ce [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md) pointe vers un type primitif ou un simple tableau de types primitifs (autrement dit, un tableau qui peut être représenté par une simple séquence d’octets). Cela `IDebugPointerObject` objet ne peut pas être une référence null (il doit pointer vers une adresse en mémoire).  
  
## <a name="see-also"></a>Voir aussi  
 [GetBytes](../../../extensibility/debugger/reference/idebugpointerobject-getbytes.md)   
 [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)