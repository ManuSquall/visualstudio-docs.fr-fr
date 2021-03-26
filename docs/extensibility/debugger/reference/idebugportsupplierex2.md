---
description: Permet à un fournisseur de port de sélectionner et d’interagir avec un serveur de base.
title: IDebugPortSupplierEx2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPortSupplierEx2 interface
ms.assetid: dae0050a-a50a-4f35-bfbd-e538f537b20f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c2020f3efe2bd7562640fd44e45a10c9a3a6c767
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105071842"
---
# <a name="idebugportsupplierex2"></a>IDebugPortSupplierEx2
Permet à un fournisseur de port de sélectionner et d’interagir avec un serveur de base.

## <a name="syntax"></a>Syntaxe

```
IDebugPortSupplierEx2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Un fournisseur de port personnalisé implémente cette interface afin qu’il puisse sélectionner le serveur de base à utiliser.

## <a name="methods"></a>Méthodes
 Le tableau suivant présente les méthodes de **IDebugPortSupplierEx2**.

|Méthode|Description|
|------------|-----------------|
|[SetServer](../../../extensibility/debugger/reference/idebugportsupplierex2-setserver.md)|Définit le serveur principal pour le fournisseur de port.|

## <a name="requirements"></a>Spécifications
 En-tête : Portpriv. h

 Espace de noms : Microsoft. VisualStudio. Debugger. Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
- [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)
