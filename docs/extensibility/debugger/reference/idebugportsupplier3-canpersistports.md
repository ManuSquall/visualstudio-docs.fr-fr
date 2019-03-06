---
title: IDebugPortSupplier3::CanPersistPorts | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier3::CanPersistPorts
helpviewer_keywords:
- IDebugPortSupplier3::CanPersistPorts
ms.assetid: 4127760c-e602-4e86-9232-457e382a52c7
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ad31d015048d8e0732c32652141b7be060628663
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56722627"
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

#### <a name="parameters"></a>Paramètres
 Aucun.

## <a name="return-value"></a>Valeur de retour
 `S_OK` Si les ports peuvent être rendus persistants ou `S_FALSE` pour indiquer que les ports ne peut pas être rendue persistante.

## <a name="remarks"></a>Notes
 Si le fournisseur de port peut conserver les ports, il doit faire lorsqu’il est détruit et les recharger lorsqu’il est instancié une fois encore.

## <a name="see-also"></a>Voir aussi
- [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)