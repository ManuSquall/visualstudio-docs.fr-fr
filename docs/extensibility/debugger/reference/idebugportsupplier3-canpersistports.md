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
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 570409a114acbf19697b0eb3ef3e5496fdfde93a
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105071972"
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
