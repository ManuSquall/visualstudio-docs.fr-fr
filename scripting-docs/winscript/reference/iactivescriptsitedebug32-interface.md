---
title: Interface de IActiveScriptSiteDebug32 | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 03f42217-303d-46e7-9792-61a5ab95252c
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: a752851aa6afd903747dc58fed79d2bc5b27e3e8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsitedebug32-interface"></a>Interface de IActiveScriptSiteDebug32
Implémentent des hôtes actifs le `IActiveScriptSiteDebug32` interface pour effectuer la gestion des documents et participer au débogage. Le `IActiveScriptSite` objet fournit généralement une implémentation de la `IActiveScriptSiteDebug32` interface. Si cette opération est effectuée, appelez le `IActiveScriptSite::QueryInterface` méthode pour obtenir le `IActiveScriptSiteDebug32` interface.  
  
 Outre les méthodes héritées de `IUnknown`, le `IActiveScriptSiteDebug32` interface expose les méthodes suivantes.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|------------|-----------------|  
|[IActiveScriptSiteDebug32::GetApplication](../../winscript/reference/iactivescriptsitedebug32-getapplication.md)|Retourne l’objet d’application de débogage associé à ce site de script.|  
|[IActiveScriptSiteDebug32::GetDocumentContextFromPosition](../../winscript/reference/iactivescriptsitedebug32-getdocumentcontextfromposition.md)|Utilisé par le moteur de langage pour déléguer `IDebugCodeContext::GetSourceContext`.|