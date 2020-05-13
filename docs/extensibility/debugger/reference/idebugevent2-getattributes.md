---
title: IDebugEvent2:GetAttributes Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEvent2::GetAttributes
helpviewer_keywords:
- IDebugEvent2::GetAttributes
ms.assetid: 2ac5b5fb-da17-43f7-811a-313f677e60d7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ffc3fc1b7988401611190fdf09e8041bf0dc5b1a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729945"
---
# <a name="idebugevent2getattributes"></a>IDebugEvent2::GetAttributes
Obtient les attributs pour cet événement de débogé.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetAttribute( 
   DWORD* pdwAttrib
);
```

```csharp
int GetAttribute( 
   out uint pdwAttrib
);
```

## <a name="parameters"></a>Paramètres
`pdwAttrib`\
[out] Une combinaison de drapeaux de l’énumération [EVENTATTRIBUTES.](../../../extensibility/debugger/reference/eventattributes.md)

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 [L’interface IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) est commune à tous les événements. Cette méthode décrit le type d’événement; par exemple, est l’événement synchrone ou asynchrone et est-ce un événement d’arrêt.

## <a name="see-also"></a>Voir aussi
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md)
