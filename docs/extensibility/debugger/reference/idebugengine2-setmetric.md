---
description: Cette méthode définit une valeur de Registre appelée métrique.
title: 'IDebugEngine2 :: SetMetric | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2:::SetMetric
helpviewer_keywords:
- IDebugEngine2:::SetMetric
ms.assetid: dcda4972-c32e-4693-a0e1-25d5c58b9782
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 129067ab94c433b7c4b09e29c65d75df98ce6b68
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102153883"
---
# <a name="idebugengine2setmetric"></a>IDebugEngine2::SetMetric
Cette méthode définit une valeur de Registre appelée métrique.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT SetMetric(
   LPCOLESTR pszMetric,
   VARIANT   varValue
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
dans Nom de la mesure.

`varValue`\
dans Spécifie la valeur de la métrique.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Une métrique est une valeur de Registre utilisée pour modifier le comportement d’un moteur de débogage ou pour annoncer les fonctionnalités prises en charge. Cette méthode peut transférer l’appel à la forme appropriée des [applications auxiliaires du kit de développement logiciel (SDK) pour](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) la fonction de débogage `SetMetric` .

## <a name="see-also"></a>Voir aussi
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [Programmes d’assistance SDK pour le débogage](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
