---
title: "IProcessDebugManager, interface | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IProcessDebugManager (interface)"
ms.assetid: b6ecb2bd-a4d1-4857-9232-036c154d0cb1
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IProcessDebugManager, interface
L'interface principale au processus de débogage le gestionnaire.  Cette interface peut créer, ajouter, supprimer ou une application virtuelle d'un processus.  Elle peut énumérer des frames de pile et les threads d'application.  
  
 Outre les méthodes héritées de `IUnknown`, l'interface `IProcessDebugManager` expose les méthodes suivantes.  
  
## Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|-------------|-----------------|  
|[IProcessDebugManager::CreateApplication](../../winscript/reference/iprocessdebugmanager-createapplication.md)|Crée un débogage l'objet application pour cette application.|  
|[IProcessDebugManager::GetDefaultApplication](../../winscript/reference/iprocessdebugmanager-getdefaultapplication.md)|Retourne un objet par défaut d'application pour le processus actuel.|  
|[IProcessDebugManager::AddApplication](../../winscript/reference/iprocessdebugmanager-addapplication.md)|Ajoute une application sur l'ordinateur de débogage la liste du gestionnaire d'applications actives.|  
|[IProcessDebugManager::RemoveApplication](../../winscript/reference/iprocessdebugmanager-removeapplication.md)|Supprime une application de la liste d'application active.|  
|[IProcessDebugManager::CreateDebugDocumentHelper](../../winscript/reference/iprocessdebugmanager-createdebugdocumenthelper.md)|Crée un débogage du programme d'assistance de le document pour cette application.|