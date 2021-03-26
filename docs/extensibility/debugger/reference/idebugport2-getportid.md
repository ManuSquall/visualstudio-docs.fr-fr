---
description: Obtient l’identificateur de port.
title: 'IDebugPort2 :: GetPortId | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPort2::GetPortId
helpviewer_keywords:
- IDebugPort2::GetPortId
ms.assetid: 837cb924-c113-4224-aa86-3e02b33dfa70
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cdd740a2182ec321e5c23e09e389b139e09f75eb
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105087533"
---
# <a name="idebugport2getportid"></a>IDebugPort2::GetPortId
Obtient l’identificateur de port.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetPortId( 
   GUID* pguidPort
);
```

```csharp
int GetPortId( 
   out Guid pguidPort
);
```

## <a name="parameters"></a>Paramètres
`pguidPort`\
à Retourne le GUID qui identifie le port.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="see-also"></a>Voir aussi
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
