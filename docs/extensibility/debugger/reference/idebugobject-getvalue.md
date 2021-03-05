---
description: Obtient la valeur de l’objet sous la forme d’une série d’octets consécutive.
title: 'IDebugObject :: GetValue | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::GetValue
helpviewer_keywords:
- IDebugObject::GetValue method
ms.assetid: eec6051e-8ecb-49fa-bdd4-dd786f211692
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 63e07ccfbcf2117363ed3e2096d5f0bb4bcac806
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102150443"
---
# <a name="idebugobjectgetvalue"></a>IDebugObject::GetValue
Obtient la valeur de l’objet sous la forme d’une série d’octets consécutive.

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
[in, out] Tableau qui est rempli avec une série consécutive d’octets représentant la valeur de l’objet.

`nSize`\
dans Nombre maximal d’octets à extraire.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne S_OK ; Sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 [Obtient](../../../extensibility/debugger/reference/idebugobject-getsize.md) le nombre total d’octets de valeur qui peuvent être récupérés en appelant la méthode de recherche.

## <a name="see-also"></a>Voir aussi
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
