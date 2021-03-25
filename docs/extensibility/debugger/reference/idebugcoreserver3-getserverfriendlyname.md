---
description: Récupère un nom convivial pour le serveur.
title: 'IDebugCoreServer3 :: GetServerFriendlyName | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::GetServerFriendlyName
helpviewer_keywords:
- IDebugCoreServer3::GetServerFriendlyName
ms.assetid: 7035b904-b3d7-4d9b-98d9-65714b8a8b9f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 72e281c6e40f8aea558ef600b531e59a3b26a5c3
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105094131"
---
# <a name="idebugcoreserver3getserverfriendlyname"></a>IDebugCoreServer3::GetServerFriendlyName
Récupère un nom convivial pour le serveur.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetServerFriendlyName(
   BSTR* pbstrName
);
```

```csharp
int GetServerFriendlyName(
   out string pbstrName
);
```

## <a name="parameters"></a>Paramètres
`pbstrName`\
à Retourne un nom convivial pour le serveur.

> [!NOTE]
> L’appelant est responsable de la libération de la chaîne.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` ; sinon, retourne le code d’erreur.

## <a name="remarks"></a>Notes
 Pour les serveurs lancés par l’utilisateur, le nom retourné par cette méthode est le nom complet du serveur. Pour les serveurs lancés automatiquement, le nom est celui de l’ordinateur sur lequel le serveur est en cours d’exécution.

 Pour un nom orienté ordinateur, appelez la méthode [getServerName](../../../extensibility/debugger/reference/idebugcoreserver3-getservername.md) .

## <a name="see-also"></a>Voir aussi
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
- [GetServerName](../../../extensibility/debugger/reference/idebugcoreserver3-getservername.md)
