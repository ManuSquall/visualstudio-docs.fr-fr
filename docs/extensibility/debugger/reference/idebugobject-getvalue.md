---
title: IDebugObject::GetValue | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::GetValue
helpviewer_keywords:
- IDebugObject::GetValue method
ms.assetid: eec6051e-8ecb-49fa-bdd4-dd786f211692
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8d8b55fed250b94fc02c9810eca17ec0934bf81e
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56690732"
---
# <a name="idebugobjectgetvalue"></a>IDebugObject::GetValue
Obtient la valeur de l’objet sous la forme d’une série consécutive d’octets.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetValue( 
   BYTE* pValue,
   UINT  nSize
);
```

```csharp
int GetValue(
   ref byte[] pValue,
   uint nSize
);
```

#### <a name="parameters"></a>Paramètres
 `pValue`

 [in, out] Tableau qui contient une série consécutive d’octets représentant la valeur de l’objet.

 `nSize`

 [in] Le nombre maximal d’octets à extraire.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne S_OK ; Sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 Obtenir le nombre total d’octets de valeur peuvent être extraites en appelant le [GetSize](../../../extensibility/debugger/reference/idebugobject-getsize.md) (méthode).

## <a name="see-also"></a>Voir aussi
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)