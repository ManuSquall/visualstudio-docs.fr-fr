---
title: IDebugCoreServer2:GetMachineName ( Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer2::GetName
helpviewer_keywords:
- IDebugCoreServer2::GetName
ms.assetid: 693bd794-7215-4f07-8651-b57366d39953
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 238088caa3229a0e57da90baeb0ee0f791c2908a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80733133"
---
# <a name="idebugcoreserver2getmachinename"></a>IDebugCoreServer2::GetMachineName
Obtient le nom de la machine le serveur de base est en cours d’exécution sur.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetName( 
   BSTR* pbstrName
);
```

```csharp
int GetName( 
   out string pbstrName
);
```

## <a name="parameters"></a>Paramètres
`pbstrName`\
[out] Retourne une chaîne contenant le nom de la machine.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="see-also"></a>Voir aussi
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
