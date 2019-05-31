---
title: IDebugPortSupplier3::CanPersistPorts | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier3::CanPersistPorts
helpviewer_keywords:
- IDebugPortSupplier3::CanPersistPorts
ms.assetid: 4127760c-e602-4e86-9232-457e382a52c7
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 11bc6e21e8b70a5bd95c001f4173a7da3f3fe4be
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66340072"
---
# <a name="idebugportsupplier3canpersistports"></a>IDebugPortSupplier3::CanPersistPorts
Cette méthode détermine si le fournisseur de port peut conserver les ports (en les écrivant sur le disque) entre les appels du débogueur.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT CanPersistPorts();
```

```csharp
int CanPersistPorts();
```

## <a name="parameters"></a>Paramètres
 Aucun.

## <a name="return-value"></a>Valeur de retour
 `S_OK` Si les ports peuvent être rendus persistants ou `S_FALSE` pour indiquer que les ports ne peut pas être rendue persistante.

## <a name="remarks"></a>Notes
 Si le fournisseur de port peut conserver les ports, il doit faire lorsqu’il est détruit et les recharger lorsqu’il est instancié une fois encore.

## <a name="see-also"></a>Voir aussi
- [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)