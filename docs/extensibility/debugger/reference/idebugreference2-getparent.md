---
title: IDebugReference2::GetParent | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2::GetParent
helpviewer_keywords:
- IDebugReference2::GetParent
ms.assetid: e3061665-ad3e-4c1b-b33f-82755fa21be3
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 985a9b15c61099548ace4ba20d8ea2706506fc17
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56697635"
---
# <a name="idebugreference2getparent"></a>IDebugReference2::GetParent
Obtient la référence parente d’une référence. Réservé à un usage ultérieur.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetParent ( 
   IDebugReference2** ppParent
);
```

```csharp
int GetParent ( 
   out IDebugReference2 ppParent
);
```

#### <a name="parameters"></a>Paramètres
 `ppParent`

 [out] Retourne un [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) objet qui représente le parent de cette propriété.

## <a name="return-value"></a>Valeur de retour
 Retourne toujours `E_NOTIMPL`.

## <a name="see-also"></a>Voir aussi
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)