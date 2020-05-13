---
title: IDebugPortRequest2::GetPortName ( Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortRequest2::GetPortName
helpviewer_keywords:
- IDebugPortRequest2::GetPortName
ms.assetid: 53e2a3a4-bb34-4a02-a983-6bd84ea70587
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 67121e98f2d506aa16c2b4dc3fff2ad5128fb93b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724812"
---
# <a name="idebugportrequest2getportname"></a>IDebugPortRequest2::GetPortName
Il a le nom du port.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetPortName( 
   BSTR* pbstrPortName
);
```

```csharp
int GetPortName( 
   out string pbstrPortName
);
```

## <a name="parameters"></a>Paramètres
`pbstrPortName`\
[out] Retourne le nom du port.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 [L’interface IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) est généralement transmise d’un paquet de débog (le client) à un fournisseur de port (le serveur) pour obtenir une connexion à un port. Le paquet de débogé et le fournisseur du port sont conscients des choix possibles pour le port. Si une chaîne simple peut décrire `IDebugPortRequest2::GetPortName` le port, alors la méthode a suffisamment d’informations pour faire la connexion. Dans le cas contraire, des interfaces supplémentaires peuvent être fournies `IDebugPortRequest2::QueryInterface`par le client, qui peut être obtenu par le serveur à l’aide de .

## <a name="see-also"></a>Voir aussi
- [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)
