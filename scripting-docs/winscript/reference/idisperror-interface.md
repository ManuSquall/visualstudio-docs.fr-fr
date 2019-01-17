---
title: Interface IDispError | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDispError interface
ms.assetid: 3dc7b55e-94ba-4669-b20a-1e011f2d07cf
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b717ebfe740a9b356513bb0f15e90c629a14e147
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54345836"
---
# <a name="idisperror-interface"></a>IDispError, interface
Fournit des informations contextuelles détaillées.  
  
> [!NOTE]
>  Cette interface n’est pas implémentée.  
  
 Outre les méthodes héritées de `IUnknown`, le `IDispError` interface expose les méthodes suivantes.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|------------|-----------------|  
|[IDispError::QueryErrorInfo](../../winscript/reference/idisperror-queryerrorinfo.md)|Récupère un type particulier d’informations d’erreur.|  
|[IDispError::GetNext](../../winscript/reference/idisperror-getnext.md)|Récupère la prochaine `IDispError` objet.|  
|[IDispError::GetHresult](../../winscript/reference/idisperror-gethresult.md)|Récupère le code d’erreur à partir de la `IDispError` objet.|  
|[IDispError::GetSource](../../winscript/reference/idisperror-getsource.md)|Retourne le ProgID dépendants de la langue pour la classe ou d’une application qui a généré l’erreur.|  
|[IDispError::GetHelpInfo](../../winscript/reference/idisperror-gethelpinfo.md)|Retourne le chemin d’accès du fichier d’aide et l’ID de contexte de la rubrique qui explique l’erreur, si possible.|  
|[IDispError::GetDescription](../../winscript/reference/idisperror-getdescription.md)|Retourne une description textuelle de l’erreur.|