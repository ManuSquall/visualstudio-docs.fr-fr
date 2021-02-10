---
title: 'IDebugThread2 :: EnumFrameInfo | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::EnumFrameInfo
helpviewer_keywords:
- IDebugThread2::EnumFrameInfo
ms.assetid: 17914a71-10ea-4b6f-8982-e364f87dca53
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a254de60995eb5e7902eda80cf50c4af227a756f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99940278"
---
# <a name="idebugthread2enumframeinfo"></a>IDebugThread2::EnumFrameInfo
Récupère une liste des frames de pile pour ce thread.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT EnumFrameInfo ( 
   FRAMEINFO_FLAGS        dwFieldSpec,
   UINT                   nRadix,
   IEnumDebugFrameInfo2** ppEnum
);
```

```csharp
int EnumFrameInfo ( 
   enum_FRAMEINFO_FLAGS     dwFieldSpec,
   uint                     nRadix,
   out IEnumDebugFrameInfo2 ppEnum
);
```

## <a name="parameters"></a>Paramètres
`dwFieldSpec`\
dans Combinaison d’indicateurs de l’énumération [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md) qui spécifie les champs des structures [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) à remplir. Spécifiez l' `FIF_FUNCNAME_FORMAT` indicateur pour mettre en forme le nom de fonction en une seule chaîne.

`nRadix`\
dans Base utilisée pour mettre en forme les informations numériques dans l’énumérateur.

`ppEnum`\
à Retourne un objet [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md) qui contient une liste de structures [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) décrivant le frame de pile.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Les frames du thread sont énumérés dans l’ordre, avec l’image actuelle énumérée en premier et la trame la plus ancienne énumérée en dernier.

## <a name="see-also"></a>Voir aussi
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)
- [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)
- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)
