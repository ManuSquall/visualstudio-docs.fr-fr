---
title: CANSTOP_REASON | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CANSTOP_REASON
helpviewer_keywords:
- CANSTOP_REASON enumeration
ms.assetid: 6da944eb-36cd-4a8c-8d71-544c775cfcc1
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b6756d574c36d6381b606be597ca0e54e7945763
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99874354"
---
# <a name="canstop_reason"></a>CANSTOP_REASON
Utilisé pour déterminer si un programme peut arrêter l’exécution après avoir atteint un point particulier dans l’exécution.

## <a name="syntax"></a>Syntaxe

```cpp
enum enum_CANSTOP_REASON {
    CANSTOP_ENTRYPOINT = 0x0000,
    CANSTOP_STEPIN     = 0x0001
};
typedef DWORD CANSTOP_REASON;
```

```csharp
public enum enum_CANSTOP_REASON {
    CANSTOP_ENTRYPOINT = 0x0000,
    CANSTOP_STEPIN     = 0x0001
};
```

## <a name="fields"></a>Champs
`CANSTOP_ENTRYPOINT`\
Spécifie le point d’entrée du programme donné.

`CANSTOP_STEPIN`\
Spécifie le pas à pas détaillé dans une fonction.

## <a name="remarks"></a>Remarques
Passé en tant qu’argument à la méthode [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md) pour confirmer auprès du gestionnaire de débogage de session (SDM) s’il est possible de s’arrêter après avoir atteint le point d’entrée du programme ou après avoir effectué un pas à pas détaillé dans une fonction ou une méthode.

## <a name="requirements"></a>Configuration requise
En-tête : msdbg. h

Espace de noms : Microsoft. VisualStudio. Debugger. Interop

Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)
