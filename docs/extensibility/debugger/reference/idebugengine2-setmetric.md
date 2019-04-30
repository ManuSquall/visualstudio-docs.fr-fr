---
title: IDebugEngine2::SetMetric | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2:::SetMetric
helpviewer_keywords:
- IDebugEngine2:::SetMetric
ms.assetid: dcda4972-c32e-4693-a0e1-25d5c58b9782
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 325cd30a49fb636c56eebd9e6301b3999e851363
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62920874"
---
# <a name="idebugengine2setmetric"></a>IDebugEngine2::SetMetric
Cette méthode définit une valeur de Registre appelée une métrique.

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

#### <a name="parameters"></a>Paramètres
 `pszMetric`

 [in] Le nom de la mesure.

 `varValue`

 [in] Spécifie la valeur de métrique.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 Une mesure est une valeur de Registre utilisée pour modifier le comportement d’un moteur débogage ou pour publier des fonctionnalités prises en charge. Cette méthode peut transférer l’appel à la forme appropriée de la [aides SDK pour le débogage](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) (fonction), `SetMetric`.

## <a name="see-also"></a>Voir aussi
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [Aides SDK pour le débogage](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)