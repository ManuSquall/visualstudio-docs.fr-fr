---
description: Cette méthode désactive explicitement modifier & Continuer sur ce processus (et tous les programmes qu’il contient).
title: IDebugProcess3 ::D isableENC | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::DisableENC
helpviewer_keywords:
- IDebugProcess3::DisableENC
ms.assetid: cffdbdac-4d76-4aeb-aa55-5d0410db99f1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7f9c4a1e05cf7d4a98489daf0c2ee3377d54f417
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105081618"
---
# <a name="idebugprocess3disableenc"></a>IDebugProcess3::DisableENC
Cette méthode désactive explicitement modifier & Continuer sur ce processus (et tous les programmes qu’il contient). Un fournisseur de port personnalisé doit toujours retourner `E_NOTIMPL` .

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT DisableENC(
   EncUnavailableReason reason
);
```

```csharp
   EncUnavailableReason reason
);
```

## <a name="parameters"></a>Paramètres
`reason`\
dans Valeur de l’énumération [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md) .

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` ; sinon, retourne le code d’erreur.

> [!NOTE]
> Un fournisseur de port personnalisé doit toujours retourner `E_NOTIMPL` .

## <a name="remarks"></a>Notes
 Une fois que modifier & Continuer est désactivé pour un processus, il peut être réactivé uniquement en redémarrant le processus.

## <a name="see-also"></a>Voir aussi
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md)
