---
description: Cette méthode obtient les utilitaires d’ordinateur pour un serveur.
title: 'IDebugCoreServer2 :: GetMachineUtilities_V7 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer2::GetMachineUtilities_V7
helpviewer_keywords:
- IDebugCoreServer2::GetMachineUtilities_V7
ms.assetid: 64c1f08f-853b-4498-9810-29791581ef2f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 26d2c042c6f4a08acb7efc558bbc86021b16587e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105077952"
---
# <a name="idebugcoreserver2getmachineutilities_v7"></a>IDebugCoreServer2::GetMachineUtilities_V7
Cette méthode obtient les utilitaires d’ordinateur pour un serveur.

> [!NOTE]
> Cette méthode est obsolète : n’utilisez pas ( [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] retourne toujours `E_NOTIMPL` la valeur si cette méthode est appelée). Elle est conservée pour des raisons historiques.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetMachineUtilities_V7(
   IDebugMDMUtil2_V7** ppUtil
);
```

```csharp
int GetMachineUtilities_V7(
   out IDebugMDMUtil2_V7 ppUtil
);
```

## <a name="parameters"></a>Paramètres
`ppUtil`\
à Retourne une `IDebugMDMUtil2_V7` interface qui représente les informations sur les utilitaires de l’ordinateur.

## <a name="return-value"></a>Valeur renvoyée
 Retourne toujours `E_NOTIMPL` , indiquant que la méthode n’est pas implémentée.

## <a name="remarks"></a>Notes
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] retourne toujours `E_NOTIMPL` la valeur si cette méthode est appelée.

## <a name="see-also"></a>Voir aussi
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
