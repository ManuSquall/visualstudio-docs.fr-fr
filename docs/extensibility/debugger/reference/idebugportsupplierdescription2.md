---
title: IDebugPortSupplierDescription2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPortSupplierDescription2 interface
ms.assetid: dd19b9d6-0703-44b3-9498-cedffa0ce5b7
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 3db59d4938911d0c47f0122a8727be8f1c8acd67
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99840195"
---
# <a name="idebugportsupplierdescription2"></a>IDebugPortSupplierDescription2
Permet [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] à l’interface utilisateur d’afficher du texte dans la section **informations de transport** de la boîte de dialogue **attacher au processus** .

## <a name="syntax"></a>Syntaxe

```
IDebugPortSupplierDescription2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Cette interface est implémentée par les fournisseurs de port.

## <a name="methods"></a>Méthodes
 Le tableau suivant présente les méthodes de `IDebugPortSupplierDescription2` .

|Méthode|Description|
|------------|-----------------|
|[GetDescription](../../../extensibility/debugger/reference/idebugportsupplierdescription2-getdescription.md)|Récupère la description et les métadonnées de description pour le fournisseur de port.|

## <a name="requirements"></a>Configuration requise
 En-tête : msdbg. h

 Espace de noms : Microsoft. VisualStudio. Debugger. Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll
