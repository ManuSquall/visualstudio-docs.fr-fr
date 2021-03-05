---
description: Cette méthode détermine si le fournisseur de ports peut conserver les ports (en les écrivant sur le disque) entre les appels du débogueur.
title: 'IDebugPortSupplier3 :: CanPersistPorts | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier3::CanPersistPorts
helpviewer_keywords:
- IDebugPortSupplier3::CanPersistPorts
ms.assetid: 4127760c-e602-4e86-9232-457e382a52c7
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 092f6e372d8f98e731ad90a7d261fe015d019656
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102172007"
---
# <a name="idebugportsupplier3canpersistports"></a>IDebugPortSupplier3::CanPersistPorts
Cette méthode détermine si le fournisseur de ports peut conserver les ports (en les écrivant sur le disque) entre les appels du débogueur.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT CanPersistPorts();
```

```csharp
int CanPersistPorts();
```

## <a name="parameters"></a>Paramètres
 Aucun.

## <a name="return-value"></a>Valeur renvoyée
 `S_OK` Si les ports peuvent être persistants ou `S_FALSE` pour indiquer que les ports ne peuvent pas être persistants.

## <a name="remarks"></a>Notes
 Si le fournisseur de port peut conserver les ports, il doit le faire lorsqu’il est détruit, puis les recharger lorsqu’il est à nouveau instancié.

## <a name="see-also"></a>Voir aussi
- [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)
