---
title: "IDebugPortSupplierDescription2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Interface de IDebugPortSupplierDescription2"
ms.assetid: dd19b9d6-0703-44b3-9498-cedffa0ce5b7
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugPortSupplierDescription2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Active [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] interface utilisateur du texte à l'intérieur de la section de **Les informations de transport** de la boîte de dialogue d' **Attacher au processus** .  
  
## Syntaxe  
  
```  
IDebugPortSupplierDescription2 : IUnknown  
```  
  
## Remarques à l'intention des implémenteurs  
 Cette interface est implémentée par les fournisseurs de port.  
  
## Méthodes  
 Le tableau suivant répertorie les méthodes d' `IDebugPortSupplierDescription2`.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[GetDescription](../../../extensibility/debugger/reference/idebugportsupplierdescription2-getdescription.md)|extrait la description et les métadonnées de description pour le fournisseur de port.|  
  
## Configuration requise  
 en\-tête : Msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll