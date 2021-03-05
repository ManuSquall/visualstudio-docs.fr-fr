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
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5c53abba81b02aa6125d4fa25ce16db85579ce5c
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102142659"
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
