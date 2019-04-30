---
title: Interface IActiveScriptSiteDebug32 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 03f42217-303d-46e7-9792-61a5ab95252c
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: e7937311e01274570e34bd639a0dc5f68206a3aa
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62992446"
---
# <a name="iactivescriptsitedebug32-interface"></a>IActiveScriptSiteDebug32 Interface
Implémentent des hôtes intelligents le `IActiveScriptSiteDebug32` interface pour effectuer la gestion des documents et participer au débogage. Le `IActiveScriptSite` objet fournit généralement une implémentation de la `IActiveScriptSiteDebug32` interface. Si cette opération est effectuée, appelez le `IActiveScriptSite::QueryInterface` méthode pour obtenir le `IActiveScriptSiteDebug32` interface.  
  
 Outre les méthodes héritées de `IUnknown`, le `IActiveScriptSiteDebug32` interface expose les méthodes suivantes.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|------------|-----------------|  
|[IActiveScriptSiteDebug32::GetApplication](../../winscript/reference/iactivescriptsitedebug32-getapplication.md)|Retourne l’objet d’application de débogage associé à ce site de script.|  
|[IActiveScriptSiteDebug32::GetDocumentContextFromPosition](../../winscript/reference/iactivescriptsitedebug32-getdocumentcontextfromposition.md)|Utilisé par le moteur de langage pour déléguer `IDebugCodeContext::GetSourceContext`.|