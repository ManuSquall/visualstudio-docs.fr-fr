---
title: IDebugPortSupplierDescription2 - France Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPortSupplierDescription2 interface
ms.assetid: dd19b9d6-0703-44b3-9498-cedffa0ce5b7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 69853e34788a2f24afe183dfbb7070e48f14aa46
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724358"
---
# <a name="idebugportsupplierdescription2"></a>IDebugPortSupplierDescription2
Permet [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] à l’interface utilisateur d’afficher du texte à l’intérieur de la section **Informations sur** les transports de la boîte de dialogue Attach **to Process.**

## <a name="syntax"></a>Syntaxe

```
IDebugPortSupplierDescription2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Cette interface est mise en œuvre par les fournisseurs portuaires.

## <a name="methods"></a>Méthodes
 Le tableau suivant montre `IDebugPortSupplierDescription2`les méthodes de .

|Méthode|Description|
|------------|-----------------|
|[GetDescription (en)](../../../extensibility/debugger/reference/idebugportsupplierdescription2-getdescription.md)|Récupère les métadonnées de description et de description pour le fournisseur du port.|

## <a name="requirements"></a>Spécifications
 En-tête: Msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll
