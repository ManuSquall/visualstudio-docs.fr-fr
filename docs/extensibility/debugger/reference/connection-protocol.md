---
title: CONNECTION_PROTOCOL Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CONNECTION_PROTOCOL
helpviewer_keywords:
- CONNECTION_PROTOCOL enumeration
ms.assetid: 99df5865-8b36-486d-9f4c-d10ae2bc688a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 29ac287462149a20f52a1affdeab7fa6b8333711
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737652"
---
# <a name="connection_protocol"></a>CONNECTION_PROTOCOL
Indique le protocole utilisé pour communiquer entre un serveur de débogé et le paquet de débog (DE).

## <a name="syntax"></a>Syntaxe

```cpp
typedef enum tagCONNECTION_PROTOCOL {
    CONNECTION_NONE    = 0,
    CONNECTION_UNKNOWN = 1,
    CONNECTION_LOCAL   = 2,
    CONNECTION_PIPE    = 3,
    CONNECTION_TCPIP   = 4,
    CONNECTION_HTTP    = 5,
    CONNECTION_OTHER   = 6
} CONNECTION_PROTOCOL;
```

```csharp
public enum CONNECTION_PROTOCOL {
    CONNECTION_NONE    = 0,
    CONNECTION_UNKNOWN = 1,
    CONNECTION_LOCAL   = 2,
    CONNECTION_PIPE    = 3,
    CONNECTION_TCPIP   = 4,
    CONNECTION_HTTP    = 5,
    CONNECTION_OTHER   = 6
};
```

## <a name="fields"></a>Champs
`CONNECTION_NONE`\
Aucune connexion n’a été faite à un serveur.

`CONNECTION_UNKNOWN`\
Une connexion a été faite, mais elle est d’un type inconnu.

`CONNECTION_LOCAL`\
La connexion est à un serveur local.

`CONNECTION_PIPE`\
La connexion se fait par un tuyau nommé.

`CONNECTION_TCPIP`\
Connexion utilise TCP/ IP.

`CONNECTION_HTTP`\
Connexion utilise HTTP (via un serveur Web).

`CONNECTION_OTHER`\
Un autre type de connexion a été établi (cette valeur n’est pas actuellement utilisée).

## <a name="remarks"></a>Notes
Ces valeurs sont revenues de la méthode [GetConnectionProtocol.](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md)

## <a name="requirements"></a>Spécifications
En-tête: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetConnectionProtocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md)
