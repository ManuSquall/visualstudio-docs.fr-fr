---
description: Crée une instance d’un moteur de débogage sur le serveur.
title: 'IDebugCoreServer3 :: CreateInstanceInServer | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::CreateInstanceInServer
helpviewer_keywords:
- IDebugCoreServer3::CreateInstanceInServer
ms.assetid: 76f36bae-f6ab-413c-a8a9-8808bfeba05b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3511e67300725dc46e6d0e3978b2cb034b92d84e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105058688"
---
# <a name="idebugcoreserver3createinstanceinserver"></a>IDebugCoreServer3::CreateInstanceInServer
Crée une instance d’un moteur de débogage sur le serveur.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT CreateInstanceInServer(
   LPCWSTR  szDll,
   WORD     wLangId,
   REFCLSID clsidObject,
   REFIID   riid,
   void**   ppvObject
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
dans Chemin d’accès à la dll qui implémente le CLSID spécifié dans le `clsidObject` paramètre. Si c’est le cas `NULL` , la `CoCreateInstance` fonction de com est appelée.

`wLangId`\
dans Paramètres régionaux du moteur de débogage. La valeur peut être 0 si la méthode [setlocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md) ne doit pas être appelée.

`clsidObject`\
dans CLSID du moteur de débogage à créer.

`riid`\
dans ID d’interface de l’interface spécifique à récupérer de l’objet de classe.

`ppvObject`\
[out] `IUnknown` interface de l’objet instancié. Effectuez un cast ou marshalez cet objet vers l’interface souhaitée.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="see-also"></a>Voir aussi
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
- [SetLocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md)
