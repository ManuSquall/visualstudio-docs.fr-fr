---
title: 'IDebugStackFrame2 :: GetInfo | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame2::GetInfo
helpviewer_keywords:
- IDebugStackFrame2::GetInfo
ms.assetid: 19c6870b-b94e-453c-bf19-82ce95b79d26
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 161796827507cf40f7ac7124ae3376d4252fb3d6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99837526"
---
# <a name="idebugstackframe2getinfo"></a>IDebugStackFrame2::GetInfo
Obtient une description du frame de pile.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetInfo ( 
   FRAMEINFO_FLAGS dwFieldSpec,
   UINT            nRadix,
   FRAMEINFO*      pFrameInfo
);
```

```csharp
int GetInfo ( 
   enum_FRAMEINFO_FLAGS dwFieldSpec,
   uint                 nRadix,
   FRAMEINFO[]          pFrameInfo
);
```

## <a name="parameters"></a>Paramètres
`dwFieldSpec`\
dans Combinaison d’indicateurs de l’énumération [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md) qui spécifie les champs du `pFrameInfo` paramètre à remplir.

`nRadix`\
dans Base à utiliser pour mettre en forme les informations numériques.

`pFrameInfo`\
à Structure [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) remplie avec la description du frame de pile.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="see-also"></a>Voir aussi
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)
- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)
