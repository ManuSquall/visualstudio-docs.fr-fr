---
description: Obtient l’ID de processus du port lui-même.
title: 'IDebugPortEx2 :: GetPortProcessId | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortEx2::GetPortProcessId
helpviewer_keywords:
- IDebugPortEx2::GetPortProcessId
ms.assetid: be85be66-47e6-415f-b0ca-24599aa5f13c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ed85141cc6f127867910777ca6fb5f417326bef5
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105072518"
---
# <a name="idebugportex2getportprocessid"></a>IDebugPortEx2::GetPortProcessId
Obtient l’ID de processus du port lui-même.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetPortProcessId ( 
   DWORD* pdwProcessId
);
```

```csharp
int GetPortProcessId ( 
   out uint pdwProcessId
);
```

## <a name="parameters"></a>Paramètres
`pdwProcessId`\
à Retourne l’ID de processus physique du port lui-même.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Dans le runtime Win32, par exemple, cette méthode appelle généralement la fonction Win32 `GetCurrentProcessId` pour obtenir l’ID de processus physique.

## <a name="see-also"></a>Voir aussi
- [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)
