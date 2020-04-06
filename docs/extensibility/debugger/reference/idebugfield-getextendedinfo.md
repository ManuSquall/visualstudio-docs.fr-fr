---
title: IDebugField::GetExtendedInfo (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::GetExtendedInfo
helpviewer_keywords:
- IDebugField::GetExtendedInfo method
ms.assetid: 46c0dd4d-4fd5-4efd-a908-71e4248e8e8d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: dc414dd57e86149e38d7c85d11252eb93efced51
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728868"
---
# <a name="idebugfieldgetextendedinfo"></a>IDebugField::GetExtendedInfo
Cette méthode reçoit des informations étendues sur un champ.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetExtendedInfo( 
   REFGUID guidExtendedInfo,
   BYTE**  prgBuffer,
   DWORD*  pdwLen
);
```

```csharp
int GetExtendedInfo(
   ref Guid guidExtendedInfo,
   IntPtr[] prgBuffer,
   ref uint pdwLen
);
```

## <a name="parameters"></a>Paramètres
`guidExtendedInfo`\
[dans] Sélectionne les informations à retourner. Les valeurs autorisées sont :

|Valeur|Description|
|-----------|-----------------|
|`guidConstantValue`|La valeur comme une séquence d’octets.|
|`guidConstantType`|Le type comme une signature de type.|

`prgBuffer`\
[out] Retourne l’information étendue.

`pdwLen`\
[dans, dehors] Retourne la taille de l’information étendue, dans les octets.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Actuellement, cette méthode ne renvoie que le type ou la valeur d’une constante. L’appelant doit libérer le `prgBuffer` tampon retourné `CoTaskMemFree` en appelant la fonction <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A> de COM (C) ou (C).

## <a name="see-also"></a>Voir aussi
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
