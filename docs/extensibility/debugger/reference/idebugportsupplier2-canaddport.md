---
description: Vérifie qu’un fournisseur de ports peut ajouter de nouveaux ports.
title: 'IDebugPortSupplier2 :: CanAddPort | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier2::CanAddPort
helpviewer_keywords:
- IDebugPortSupplier2::CanAddPort
ms.assetid: 41f69e0a-e82c-473d-8b7a-0c40fc5730fc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ad704eda53807d344b23736d2d9b55e172c36468
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105072206"
---
# <a name="idebugportsupplier2canaddport"></a>IDebugPortSupplier2::CanAddPort
Vérifie qu’un fournisseur de ports peut ajouter de nouveaux ports.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT CanAddPort( 
   void 
);
```

```csharp
int CanAddPort();
```

## <a name="return-value"></a>Valeur de retour
 Si le port peut être ajouté, retourne `S_OK` ; sinon, retourne `S_FALSE` pour indiquer qu’aucun port ne peut être ajouté à ce fournisseur de port.

## <a name="remarks"></a>Notes
 Appelez cette méthode avant d’appeler la méthode [addport](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) , car la dernière méthode crée le port et l’ajoute, ce qui peut être une opération longue.

## <a name="see-also"></a>Voir aussi
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
- [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)
