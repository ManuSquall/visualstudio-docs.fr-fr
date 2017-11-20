---
title: IProcessDebugManager (Interface) | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IProcessDebugManager interface
ms.assetid: b6ecb2bd-a4d1-4857-9232-036c154d0cb1
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 26c97fda6fc8657164e22d51eb041017a6239d98
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="iprocessdebugmanager-interface"></a>IProcessDebugManager, interface
Interface principale pour le Gestionnaire de processus de débogage. Cette interface peut créer, ajouter ou supprimer une application virtuelle à partir d’un processus. Il peut énumérer les frames de pile et les threads d’application.  
  
 Outre les méthodes héritées de `IUnknown`, le `IProcessDebugManager` interface expose les méthodes suivantes.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|------------|-----------------|  
|[IProcessDebugManager::CreateApplication](../../winscript/reference/iprocessdebugmanager-createapplication.md)|Crée un nouvel objet d’application de débogage pour cette application.|  
|[IProcessDebugManager::GetDefaultApplication](../../winscript/reference/iprocessdebugmanager-getdefaultapplication.md)|Retourne un objet d’application par défaut pour le processus actuel.|  
|[IProcessDebugManager::AddApplication](../../winscript/reference/iprocessdebugmanager-addapplication.md)|Ajoute une application sur la machine debug liste du Gestionnaire d’applications en cours d’exécution.|  
|[IProcessDebugManager::RemoveApplication](../../winscript/reference/iprocessdebugmanager-removeapplication.md)|Supprime une application en cours d’exécution la liste des applications.|  
|[IProcessDebugManager::CreateDebugDocumentHelper](../../winscript/reference/iprocessdebugmanager-createdebugdocumenthelper.md)|Crée un nouveau programme d’assistance de document debug pour cette application.|