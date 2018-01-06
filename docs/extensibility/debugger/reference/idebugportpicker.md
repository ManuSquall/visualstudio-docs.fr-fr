---
title: IDebugPortPicker | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IDebugPortPicker interface
ms.assetid: 8b7f6685-a3c5-4355-b706-c1b574f6ff84
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 61973b6b9d7c62e8276f46443d0b9520419d3934
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
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
  
## <a name="requirements"></a>Configuration requise  
 En-tête : Msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll