---
title: IDebugCoreServer3::GetServerFriendlyName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::GetServerFriendlyName
helpviewer_keywords:
- IDebugCoreServer3::GetServerFriendlyName
ms.assetid: 7035b904-b3d7-4d9b-98d9-65714b8a8b9f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f70e8301b6a44397d351345fe3cb8fe0c3d3426e
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63414028"
---
# <a name="idebugcoreserver3getserverfriendlyname"></a>IDebugCoreServer3::GetServerFriendlyName
Récupère un nom convivial pour le serveur.

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

#### <a name="parameters"></a>Paramètres
 `pbstrName`

 [out] Retourne un nom convivial pour le serveur.

> [!NOTE]
> L’appelant est chargé de libérer la chaîne.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne le code d’erreur.

## <a name="remarks"></a>Notes
 Pour les serveurs de l’utilisateur a lancé, le nom retourné par cette méthode est le nom complet du serveur. Pour les serveurs d’auto-lancé, le nom est que de l’ordinateur, le serveur s’exécute sur.

 Pour un nom orientée sur la machine, appelez le [GetServerName](../../../extensibility/debugger/reference/idebugcoreserver3-getservername.md) (méthode).

## <a name="see-also"></a>Voir aussi
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
- [GetServerName](../../../extensibility/debugger/reference/idebugcoreserver3-getservername.md)