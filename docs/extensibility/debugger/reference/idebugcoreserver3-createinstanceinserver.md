---
title: 'IDebugCoreServer3 :: CreateInstanceInServer | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80733018"
---
# <a name="idebugcoreserver3createinstanceinserver"></a>IDebugCoreServer3::CreateInstanceInServer
Crée une instance d’un moteur de débogage sur le serveur.

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
