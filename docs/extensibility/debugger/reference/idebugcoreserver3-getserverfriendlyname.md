---
title: IDebugCoreServer3:GetServerFriendlyName (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::GetServerFriendlyName
helpviewer_keywords:
- IDebugCoreServer3::GetServerFriendlyName
ms.assetid: 7035b904-b3d7-4d9b-98d9-65714b8a8b9f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: eec30783041a1240d8f85815c06f4ca60729a484
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732882"
---
# <a name="idebugcoreserver3getserverfriendlyname"></a>IDebugCoreServer3::GetServerFriendlyName
Récupère un nom amical pour le serveur.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetServerFriendlyName(
   BSTR* pbstrName
);
```

```csharp
int GetServerFriendlyName(
   out string pbstrName
);
```

## <a name="parameters"></a>Paramètres
`pbstrName`\
[out] Retourne un nom amical pour le serveur.

> [!NOTE]
> L’appelant est responsable de la libération de la chaîne.

## <a name="return-value"></a>Valeur de retour
 En cas `S_OK`de succès, les retours; autrement, renvoie le code d’erreur.

## <a name="remarks"></a>Notes
 Pour les serveurs lancés par l’utilisateur, le nom retourné par cette méthode est le nom complet du serveur. Pour les serveurs lancés automatiquement, le nom est celui de la machine sur laquelle le serveur fonctionne.

 Pour un nom orienté vers la machine, appelez la méthode [GetServerName.](../../../extensibility/debugger/reference/idebugcoreserver3-getservername.md)

## <a name="see-also"></a>Voir aussi
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
- [GetServerName (en)](../../../extensibility/debugger/reference/idebugcoreserver3-getservername.md)
