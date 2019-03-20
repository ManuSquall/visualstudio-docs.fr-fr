---
title: Interface IDispError | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 2c67ff6e458f8350ef36a8a454e017b3ce6ea114
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58144925"
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