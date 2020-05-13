---
title: IDebugEngine3:SetEngineGuid - France Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine3::SetEngineGuid
helpviewer_keywords:
- IDebugEngine3::SetEngineGuid
ms.assetid: 8bdfa05d-feb7-4d98-abac-77825a04c50f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ae151484a7c2fd5828888a8a551b710c6fda44c8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730754"
---
# <a name="idebugengine3setengineguid"></a>IDebugEngine3::SetEngineGuid
Cette méthode définit le moteur de débogé (DE) `GUID`.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT SetEngineGuid(
   GUID* guidEngine
);
```

```csharp
int SetEngineGuid(
   ref Guid guidEngine
);
```

## <a name="parameters"></a>Paramètres
`guidEngine`\
[dans] `GUID` du moteur.

## <a name="return-value"></a>Valeur de retour
 En cas `S_OK`de succès, les retours; autrement, renvoie le code d’erreur.

## <a name="see-also"></a>Voir aussi
- [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)
