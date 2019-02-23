---
title: IDebugPortPicker | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPortPicker interface
ms.assetid: 8b7f6685-a3c5-4355-b706-c1b574f6ff84
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 845e197b186d462b74aaf8cf3cd7218e4606dfc7
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56716543"
---
# <a name="idebugportpicker"></a>IDebugPortPicker
Représente une interface utilisateur personnalisée pour sélectionner le port.

## <a name="syntax"></a>Syntaxe

```
IDebugPortPicker : IUnknown
```

## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs
 Cette interface est implémentée par les fournisseurs de port. Un fournisseur de port définit leur sélecteur de port à exposer en tant qu’un CLSID et en pointant le `metricPortPickerCLSID` métrique au CLSID exposé.

## <a name="methods"></a>Méthodes
 Le tableau suivant présente les méthodes de `IDebugPortPicker`.

|Méthode|Description|
|------------|-----------------|
|[DisplayPortPicker](../../../extensibility/debugger/reference/idebugportpicker-displayportpicker.md)|Affiche la boîte de dialogue spécifiée qui permet à l’utilisateur de sélectionner un port.|
|[SetSite](../../../extensibility/debugger/reference/idebugportpicker-setsite.md)|Définit le fournisseur de services.|

## <a name="requirements"></a>Spécifications
 En-tête : Msdbg.h

 Espace de noms : Microsoft.VisualStudio.Debugger.Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll