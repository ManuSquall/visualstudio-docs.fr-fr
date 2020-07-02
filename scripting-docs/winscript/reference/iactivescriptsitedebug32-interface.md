---
title: Interface IActiveScriptSiteDebug32 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 03f42217-303d-46e7-9792-61a5ab95252c
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 2a55161f76fcd98b52ddb769c640aca0e903239b
ms.sourcegitcommit: 9a9c61ca115c22d33bb902153eb0853789c7be4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85835262"
---
# <a name="iactivescriptsitedebug32-interface"></a>Interface IActiveScriptSiteDebug32
Les hôtes intelligents implémentent l' `IActiveScriptSiteDebug32` interface pour effectuer la gestion des documents et participer au débogage. L' `IActiveScriptSite` objet fournit généralement une implémentation de l' `IActiveScriptSiteDebug32` interface. Si c’est fait, appelez la `IActiveScriptSite::QueryInterface` méthode pour obtenir l' `IActiveScriptSiteDebug32` interface.  
  
 En plus des méthodes héritées de `IUnknown` , l' `IActiveScriptSiteDebug32` interface expose les méthodes suivantes.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|------------|-----------------|  
|[IActiveScriptSiteDebug32::GetApplication](../../winscript/reference/iactivescriptsitedebug32-getapplication.md)|Retourne l’objet d’application de débogage associé à ce site de script.|  
|[IActiveScriptSiteDebug32::GetDocumentContextFromPosition](../../winscript/reference/iactivescriptsitedebug32-getdocumentcontextfromposition.md)|Utilisé par le moteur de langage pour déléguer `IDebugCodeContext::GetSourceContext` .|