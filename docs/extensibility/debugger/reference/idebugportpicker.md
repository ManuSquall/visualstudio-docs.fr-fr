---
title: IDebugPortPicker - France Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPortPicker interface
ms.assetid: 8b7f6685-a3c5-4355-b706-c1b574f6ff84
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 554ac24d7148f0d5de07779f35376b28b7ff7b07
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724835"
---
# <a name="idebugportpicker"></a>IDebugPortPicker
Représente une interface utilisateur personnalisée pour la sélection du port.

## <a name="syntax"></a>Syntaxe

```
IDebugPortPicker : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Cette interface est mise en œuvre par les fournisseurs portuaires. Un fournisseur de ports définit son cueilleur de ports en `metricPortPickerCLSID` l’exposant comme un CLSID et en pointant la mesure vers le CLSID exposé.

## <a name="methods"></a>Méthodes
 Le tableau suivant montre `IDebugPortPicker`les méthodes de .

|Méthode|Description|
|------------|-----------------|
|[DisplayPortPicker](../../../extensibility/debugger/reference/idebugportpicker-displayportpicker.md)|Affiche la boîte de dialogue spécifiée qui permet à l’utilisateur de sélectionner un port.|
|[SetSite](../../../extensibility/debugger/reference/idebugportpicker-setsite.md)|Définit le fournisseur de services.|

## <a name="requirements"></a>Spécifications
 En-tête: Msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll
