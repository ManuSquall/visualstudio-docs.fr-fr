---
title: IDebugPortSupplier2::GetPortSupplierId | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier2::GetPortSupplierId
helpviewer_keywords:
- IDebugPortSupplier2::GetPortSupplierId
ms.assetid: 741d0829-0943-49bf-b56e-61e836043006
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e4aa51e59a693b1702de49b5c749b75fed9ec525
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/24/2019
ms.locfileid: "66204412"
---
# <a name="idebugportsupplier2getportsupplierid"></a>IDebugPortSupplier2::GetPortSupplierId
Obtient l’identificateur de fournisseur de port.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetPortSupplierId( 
   GUID* pguidPortSupplier
);
```

```csharp
HRESULT GetPortSupplierId( 
   out Guid pguidPortSupplier
);
```

## <a name="parameters"></a>Paramètres
`pguidPortSupplier`\
[out] Retourne le GUID du fournisseur de port.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.

## <a name="see-also"></a>Voir aussi
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)