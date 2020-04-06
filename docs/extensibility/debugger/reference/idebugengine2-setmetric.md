---
title: IDebugEngine2:SetMetric (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2:::SetMetric
helpviewer_keywords:
- IDebugEngine2:::SetMetric
ms.assetid: dcda4972-c32e-4693-a0e1-25d5c58b9782
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: caada8db1791d94e7a9632394cd4659bf8cec3a0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730898"
---
# <a name="idebugengine2setmetric"></a>IDebugEngine2::SetMetric
Cette méthode établit une valeur de registre connue sous le nom de mesure.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT SetMetric(
   LPCOLESTR pszMetric,
   VARIANT   varValue
);
```

```csharp
int SetMetric(
   string pszMetric,
   object varValue
);
```

## <a name="parameters"></a>Paramètres
`pszMetric`\
[dans] Le nom métrique.

`varValue`\
[dans] Spécifie la valeur métrique.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Une mesure est une valeur de registre utilisée pour modifier le comportement d’un moteur de débogé ou pour annoncer les fonctionnalités prises en charge. Cette méthode peut transmettre l’appel à la forme appropriée des aides `SetMetric` [SDK pour la fonction Debugging,](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) .

## <a name="see-also"></a>Voir aussi
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [Programmes d’assistance SDK pour le débogage](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
