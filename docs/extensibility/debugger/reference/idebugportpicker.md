---
title: "IDebugPortPicker | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Interface de IDebugPortPicker"
ms.assetid: 8b7f6685-a3c5-4355-b706-c1b574f6ff84
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugPortPicker
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Représente une interface utilisateur personnalisé pour sélectionner le port.  
  
## Syntaxe  
  
```  
IDebugPortPicker : IUnknown  
```  
  
## Remarques à l'intention des implémenteurs  
 Cette interface est implémentée par les fournisseurs de port.  Un fournisseur de port définit leur sélecteur de port en l'exposant comme CLSID et en pointant `metricPortPickerCLSID` métriques à le CLSID exposé.  
  
## Méthodes  
 Le tableau suivant répertorie les méthodes d' `IDebugPortPicker`.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[DisplayPortPicker](../../../extensibility/debugger/reference/idebugportpicker-displayportpicker.md)|Affiche la boîte de dialogue spécifiée qui permet à l'utilisateur de sélectionner un port.|  
|[SetSite](../../../extensibility/debugger/reference/idebugportpicker-setsite.md)|définit le fournisseur de services.|  
  
## Configuration requise  
 en\-tête : Msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll