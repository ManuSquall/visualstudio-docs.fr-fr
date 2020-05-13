---
title: IDebugObject:GetValue Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::GetValue
helpviewer_keywords:
- IDebugObject::GetValue method
ms.assetid: eec6051e-8ecb-49fa-bdd4-dd786f211692
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 45d555cbea6bf8239ef4527ba982072e17532af4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726543"
---
# <a name="idebugobjectgetvalue"></a>IDebugObject::GetValue
Obtient la valeur de l’objet comme une série consécutive d’octets.

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

## <a name="parameters"></a>Paramètres
`pValue`\
[dans, dehors] Un tableau qui est rempli d’une série consécutive d’octets représentant la valeur de l’objet.

`nSize`\
[dans] Le nombre maximum d’octets à aller chercher.

## <a name="return-value"></a>Valeur de retour
 En cas de succès, les retours S_OK; autrement, renvoie un code d’erreur.

## <a name="remarks"></a>Notes
 Obtenez le nombre total d’octets de valeur qui peuvent être récupérés en appelant la méthode [GetSize.](../../../extensibility/debugger/reference/idebugobject-getsize.md)

## <a name="see-also"></a>Voir aussi
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
