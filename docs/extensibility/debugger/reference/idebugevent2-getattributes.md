---
title: IDebugEvent2::GetAttributes | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEvent2::GetAttributes
helpviewer_keywords:
- IDebugEvent2::GetAttributes
ms.assetid: 2ac5b5fb-da17-43f7-811a-313f677e60d7
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d374086ebae3546346f442f782c02a145ca18972
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/24/2019
ms.locfileid: "66199904"
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
[out] Une combinaison d’indicateurs de la [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md) énumération.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 Le [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interface est commune à tous les événements. Cette méthode décrit le type d’événement ; par exemple, est l’événement synchrone ou asynchrone et il est un événement d’arrêt.

## <a name="see-also"></a>Voir aussi
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md)