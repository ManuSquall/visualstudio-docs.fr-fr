---
title: IDebugPortRequest2::GetPortName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortRequest2::GetPortName
helpviewer_keywords:
- IDebugPortRequest2::GetPortName
ms.assetid: 53e2a3a4-bb34-4a02-a983-6bd84ea70587
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e8017237af68b3dc414dc64bf6ae077387f0a600
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66340381"
---
# <a name="idebugportrequest2getportname"></a>IDebugPortRequest2::GetPortName
Obtient le nom du port.

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
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 Le [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) interface est généralement passée à partir d’un package de débogage (le client) à un fournisseur de port (le serveur) pour obtenir une connexion à un port. Le package de débogage et le fournisseur de port connaissent les choix possibles pour le port. Si une chaîne simple peut décrire le port, puis la `IDebugPortRequest2::GetPortName` méthode possède suffisamment d’informations pour établir la connexion. Sinon, les interfaces supplémentaires peuvent être fournies par le client, ce qui peut être obtenu par le serveur à l’aide `IDebugPortRequest2::QueryInterface`.

## <a name="see-also"></a>Voir aussi
- [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)