---
title: IDebugCoreServer3::CreateInstanceInServer (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::CreateInstanceInServer
helpviewer_keywords:
- IDebugCoreServer3::CreateInstanceInServer
ms.assetid: 76f36bae-f6ab-413c-a8a9-8808bfeba05b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2346bb76fe604265a309a51f48b734fc6f2ab8d0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80733018"
---
# <a name="idebugcoreserver3createinstanceinserver"></a>IDebugCoreServer3::CreateInstanceInServer
Crée une instance d’un moteur de débogé sur le serveur.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT CreateInstanceInServer(
   LPCWSTR  szDll,
   WORD     wLangId,
   REFCLSID clsidObject,
   REFIID   riid,
   void**   ppvObject
);
```

```csharp
int CreateInstanceInServer(
   string     szDll,
   ushort     wLangID,
   ref Guid   clsidObject,
   ref Guid   riid,
   out IntPtr ppvObject
);
```

## <a name="parameters"></a>Paramètres
`szDll`\
[dans] Chemin vers la dll qui implémente `clsidObject` le CLSID spécifié dans le paramètre. Si c’est `NULL`, `CoCreateInstance` alors la fonction de COM est appelée.

`wLangId`\
[dans] Local du moteur de débogé. Cela peut être 0 si la méthode [SetLocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md) ne doit pas être appelée.

`clsidObject`\
[dans] CLSID du moteur de débogé à créer.

`riid`\
[dans] Interface ID de l’interface spécifique pour récupérer de l’objet de classe.

`ppvObject`\
[out] `IUnknown` interface de l’objet instantané. Lancer ou rassembler cet objet à l’interface désirée.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="see-also"></a>Voir aussi
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
- [SetLocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md)
