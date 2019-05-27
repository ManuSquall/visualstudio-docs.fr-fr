---
title: IDebugProcess3::DisableENC | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::DisableENC
helpviewer_keywords:
- IDebugProcess3::DisableENC
ms.assetid: cffdbdac-4d76-4aeb-aa55-5d0410db99f1
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 65f79b73eaa9b97630cc3ef3e84e1ba4198835c9
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/24/2019
ms.locfileid: "66202360"
---
# <a name="idebugprocess3disableenc"></a>IDebugProcess3::DisableENC
Cette méthode explicitement désactive Modifier & Continuer sur ce processus (et tous les programmes qu’il contient). Un fournisseur de port personnalisé doit toujours retourner `E_NOTIMPL`.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT DisableENC(
   EncUnavailableReason reason
);
```

```csharp
   EncUnavailableReason reason
);
```

## <a name="parameters"></a>Paramètres
`reason`\
[in] Une valeur comprise entre le [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md) énumération.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne le code d’erreur.

> [!NOTE]
> Un fournisseur de port personnalisé doit toujours retourner `E_NOTIMPL`.

## <a name="remarks"></a>Notes
 Une fois modifier et continuer est désactivée pour un processus, il peut être réactivée uniquement en redémarrant le processus.

## <a name="see-also"></a>Voir aussi
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md)