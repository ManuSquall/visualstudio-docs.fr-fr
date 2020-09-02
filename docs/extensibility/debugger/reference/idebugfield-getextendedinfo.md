---
title: 'IDebugField :: GetExtendedInfo | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80728868"
---
# <a name="idebugfieldgetextendedinfo"></a>IDebugField::GetExtendedInfo
Cette méthode obtient des informations étendues sur un champ.

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
dans Sélectionne les informations à retourner. Les valeurs autorisées sont :

|Valeur|Description|
|-----------|-----------------|
|`guidConstantValue`|Valeur sous la forme d’une séquence d’octets.|
|`guidConstantType`|Type comme une signature de type.|

`prgBuffer`\
à Retourne les informations étendues.

`pdwLen`\
[in, out] Retourne la taille des informations étendues, en octets.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Actuellement, cette méthode retourne uniquement le type ou la valeur d’une constante. L’appelant doit libérer la mémoire tampon retournée dans `prgBuffer` en appelant la fonction de com `CoTaskMemFree` (C++) ou <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A> (C#).

## <a name="see-also"></a>Voir aussi
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
