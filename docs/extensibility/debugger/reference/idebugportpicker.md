---
title: IDebugPortPicker | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugPortPicker interface
ms.assetid: 8b7f6685-a3c5-4355-b706-c1b574f6ff84
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7d9a5a830d6b3b0d191b5eae84bf625ffdb3b695
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31118542"
---
# <a name="idebugportpicker"></a>IDebugPortPicker
Représente une interface utilisateur personnalisée pour sélectionner le port.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugPortPicker : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes pour les implémenteurs  
 Cette interface est implémentée par les fournisseurs de port. Un fournisseur de port définit leur sélecteur de port en exposant comme CLSID et en pointant le `metricPortPickerCLSID` métrique au CLSID exposé.  
  
## <a name="methods"></a>Méthodes  
 Le tableau suivant présente les méthodes de `IDebugPortPicker`.  
  
|Méthode|Description|  
|------------|-----------------|  
|[DisplayPortPicker](../../../extensibility/debugger/reference/idebugportpicker-displayportpicker.md)|Affiche la boîte de dialogue spécifiée qui permet à l’utilisateur à sélectionner un port.|  
|[SetSite](../../../extensibility/debugger/reference/idebugportpicker-setsite.md)|Définit le fournisseur de services.|  
  
## <a name="requirements"></a>Spécifications  
 En-tête : Msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll