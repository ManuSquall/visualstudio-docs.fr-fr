---
title: Interface IProcessDebugManager | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IProcessDebugManager interface
ms.assetid: b6ecb2bd-a4d1-4857-9232-036c154d0cb1
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5feb67b1a616eeaa855b27cb12ea9b3146545ebd
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54345121"
---
# <a name="iprocessdebugmanager-interface"></a>IProcessDebugManager, interface
Interface principale avec le gestionnaire de débogage de processus. Cette interface peut créer, ajouter ou supprimer une application virtuelle d’un processus. Il peut énumérer les frames de pile et les threads d’application.  
  
 Outre les méthodes héritées de `IUnknown`, le `IProcessDebugManager` interface expose les méthodes suivantes.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|------------|-----------------|  
|[IProcessDebugManager::CreateApplication](../../winscript/reference/iprocessdebugmanager-createapplication.md)|Crée un nouvel objet d’application de débogage pour cette application.|  
|[IProcessDebugManager::GetDefaultApplication](../../winscript/reference/iprocessdebugmanager-getdefaultapplication.md)|Retourne un objet d’application par défaut pour le processus actuel.|  
|[IProcessDebugManager::AddApplication](../../winscript/reference/iprocessdebugmanager-addapplication.md)|Ajoute une application à la liste du Gestionnaire de débogage de machine d’exécution des applications.|  
|[IProcessDebugManager::RemoveApplication](../../winscript/reference/iprocessdebugmanager-removeapplication.md)|Supprime une application en cours d’exécution la liste des applications.|  
|[IProcessDebugManager::CreateDebugDocumentHelper](../../winscript/reference/iprocessdebugmanager-createdebugdocumenthelper.md)|Crée une nouvelle assistance de document de débogage pour cette application.|