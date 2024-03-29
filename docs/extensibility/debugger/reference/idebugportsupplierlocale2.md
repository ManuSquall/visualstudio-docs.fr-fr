---
description: Fournit la prise en charge des paramètres régionaux pour un fournisseur de port.
title: IDebugPortSupplierLocale2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPortSupplierLocale2 interface
ms.assetid: 910e7220-da2a-4339-9fff-9fb1bad3c28c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: da7c08363d07e577d11259b8633aa15ac3cd0eb0
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105071764"
---
# <a name="idebugportsupplierlocale2"></a>IDebugPortSupplierLocale2
Fournit la prise en charge des paramètres régionaux pour un fournisseur de port.

## <a name="syntax"></a>Syntaxe

```
IDebugPortSupplierLocale2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Un fournisseur de port personnalisé implémente cette interface pour définir les paramètres régionaux.

## <a name="methods"></a>Méthodes
 Le tableau suivant présente les méthodes de **IDebugPortSupplierLocale2**.

|Méthode|Description|
|------------|-----------------|
|[SetLocale](../../../extensibility/debugger/reference/idebugportsupplierlocale2-setlocale.md)|Définit les paramètres régionaux pour le fournisseur de port.|

## <a name="requirements"></a>Spécifications
 En-tête : Portpriv. h

 Espace de noms : Microsoft. VisualStudio. Debugger. Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
- [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)
