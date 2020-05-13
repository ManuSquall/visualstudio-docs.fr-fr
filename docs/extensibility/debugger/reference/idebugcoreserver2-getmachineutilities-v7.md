---
title: IDebugCoreServer2::GetMachineUtilities_V7 Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer2::GetMachineUtilities_V7
helpviewer_keywords:
- IDebugCoreServer2::GetMachineUtilities_V7
ms.assetid: 64c1f08f-853b-4498-9810-29791581ef2f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 79eba6889583f1dfa482dab107ad31eaaacdbcc2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80733154"
---
# <a name="idebugcoreserver2getmachineutilities_v7"></a>IDebugCoreServer2::GetMachineUtilities_V7
Cette méthode obtient les utilitaires de la machine pour un serveur.

> [!NOTE]
> Cette méthode est obsolète :[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] ne `E_NOTIMPL` pas utiliser (retourne toujours si cette méthode est appelée). Il est conservé pour des raisons historiques.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetMachineUtilities_V7(
   IDebugMDMUtil2_V7** ppUtil
);
```

```csharp
int GetMachineUtilities_V7(
   out IDebugMDMUtil2_V7 ppUtil
);
```

## <a name="parameters"></a>Paramètres
`ppUtil`\
[out] Retourne `IDebugMDMUtil2_V7` une interface qui représente les informations sur les utilitaires de la machine.

## <a name="return-value"></a>Valeur de retour
 Retourne `E_NOTIMPL`toujours, indiquant que la méthode n’est pas implémentée.

## <a name="remarks"></a>Notes
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]retourne `E_NOTIMPL` toujours si cette méthode est appelée.

## <a name="see-also"></a>Voir aussi
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
