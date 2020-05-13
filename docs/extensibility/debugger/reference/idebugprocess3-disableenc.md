---
title: IDebugProcess3::DisableENC - France Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::DisableENC
helpviewer_keywords:
- IDebugProcess3::DisableENC
ms.assetid: cffdbdac-4d76-4aeb-aa55-5d0410db99f1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5b39bb448501bacd5ab458b7e61bb1a5044bc8a3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723732"
---
# <a name="idebugprocess3disableenc"></a>IDebugProcess3::DisableENC
Cette méthode désactive explicitement Edit and Continue sur ce processus (et tous les programmes qu’il contient). Un fournisseur de port `E_NOTIMPL`personnalisé doit toujours revenir .

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
[dans] Une valeur de l’énumération [EncUnavailableReason.](../../../extensibility/debugger/reference/encunavailablereason.md)

## <a name="return-value"></a>Valeur de retour
 En cas `S_OK`de succès, les retours; autrement, renvoie le code d’erreur.

> [!NOTE]
> Un fournisseur de port `E_NOTIMPL`personnalisé doit toujours revenir .

## <a name="remarks"></a>Notes
 Une fois que Edit and Continue est désactivé pour un processus, il ne peut être réintraitré qu’en redémarrant le processus.

## <a name="see-also"></a>Voir aussi
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md)
