---
title: 'IDebugEvent2 :: GetAttributes | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEvent2::GetAttributes
helpviewer_keywords:
- IDebugEvent2::GetAttributes
ms.assetid: 2ac5b5fb-da17-43f7-811a-313f677e60d7
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 64f4b404938143e5b1531798b1cded7ac6218de6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99888275"
---
# <a name="idebugevent2getattributes"></a>IDebugEvent2::GetAttributes
Obtient les attributs de cet événement de débogage.

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
à Combinaison d’indicateurs de l’énumération [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md) .

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Remarques
 L’interface [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) est commune à tous les événements. Cette méthode décrit le type d’événement. par exemple, est l’événement synchrone ou asynchrone et s’agit-il d’un événement d’arrêt.

## <a name="see-also"></a>Voir aussi
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md)
