---
title: IDispError (Interface) | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IDispError interface
ms.assetid: 3dc7b55e-94ba-4669-b20a-1e011f2d07cf
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9f139d317db5aa00f03f8e9abd71020e5ff35b03
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="idisperror-interface"></a>IDispError, interface
Fournit des informations contextuelles détaillées.  
  
> [!NOTE]
>  Cette interface n’est pas implémentée.  
  
 Outre les méthodes héritées de `IUnknown`, le `IDispError` interface expose les méthodes suivantes.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|------------|-----------------|  
|[IDispError::QueryErrorInfo](../../winscript/reference/idisperror-queryerrorinfo.md)|Récupère un type particulier d’informations sur l’erreur.|  
|[IDispError::GetNext](../../winscript/reference/idisperror-getnext.md)|Récupère la prochaine `IDispError` objet.|  
|[IDispError::GetHresult](../../winscript/reference/idisperror-gethresult.md)|Récupère le code d’erreur à partir de la `IDispError` objet.|  
|[IDispError::GetSource](../../winscript/reference/idisperror-getsource.md)|Retourne le ProgID dépendants de la langue pour la classe ou d’une application qui a généré l’erreur.|  
|[IDispError::GetHelpInfo](../../winscript/reference/idisperror-gethelpinfo.md)|Retourne le chemin d’accès du fichier d’aide et l’ID de contexte de la rubrique qui décrit l’erreur, si possible.|  
|[IDispError::GetDescription](../../winscript/reference/idisperror-getdescription.md)|Retourne une description textuelle de l’erreur.|