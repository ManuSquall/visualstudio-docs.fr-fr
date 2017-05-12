---
title: "IDispError, interface | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDispError (interface)"
ms.assetid: 3dc7b55e-94ba-4669-b20a-1e011f2d07cf
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDispError, interface
Fournit des informations sur l'erreur contextuelles.  
  
> [!NOTE]
>  Cette interface n'est pas implémentée.  
  
 Outre les méthodes héritées de `IUnknown`, l'interface `IDispError` expose les méthodes suivantes.  
  
## Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|-------------|-----------------|  
|[IDispError::QueryErrorInfo](../../winscript/reference/idisperror-queryerrorinfo.md)|Récupère un type particulier d'informations sur l'erreur.|  
|[IDispError::GetNext](../../winscript/reference/idisperror-getnext.md)|Récupère l'objet d' `IDispError` .|  
|[IDispError::GetHresult](../../winscript/reference/idisperror-gethresult.md)|Récupère le code d'erreur de l'objet d' `IDispError` .|  
|[IDispError::GetSource](../../winscript/reference/idisperror-getsource.md)|Retourne l'identificateur programmatique dépendant du langage pour la classe ou l'application qui a déclenché l'erreur.|  
|[IDispError::GetHelpInfo](../../winscript/reference/idisperror-gethelpinfo.md)|Retourne le chemin d'accès du fichier d'aide et de l'ID de contexte de la rubrique qui décrit l'erreur, si possible.|  
|[IDispError::GetDescription](../../winscript/reference/idisperror-getdescription.md)|Retourne une description textuelle de l'erreur.|