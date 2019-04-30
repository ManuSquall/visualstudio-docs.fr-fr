---
title: Interface IActiveScriptSiteDebug | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptSiteDebug interface
ms.assetid: 2557ee09-688b-4c03-a821-180c24dfa0e6
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3cd8043648586ed3c614cbb137e51d992d7ae29b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62992463"
---
# <a name="iactivescriptsitedebug-interface"></a>IActiveScriptSiteDebug, interface
Implémentent des hôtes intelligents le `IActiveScriptSiteDebug` interface pour effectuer la gestion des documents et participer au débogage. Le `IActiveScriptSite` objet fournit généralement une implémentation de la `IActiveScriptSiteDebug` interface. Si cette opération est effectuée, appelez le `IActiveScriptSite::QueryInterface` méthode pour obtenir le `IActiveScriptSiteDebug` interface.  
  
 Outre les méthodes héritées de `IUnknown`, le `IActiveScriptSiteDebug` interface expose les méthodes suivantes.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|------------|-----------------|  
|[IActiveScriptSiteDebug::GetDocumentContextFromPosition](../../winscript/reference/iactivescriptsitedebug-getdocumentcontextfromposition.md)|Utilisé par le moteur de langage pour déléguer `IDebugCodeContext::GetSourceContext`.|  
|[IActiveScriptSiteDebug::GetApplication](../../winscript/reference/iactivescriptsitedebug-getapplication.md)|Retourne l’objet d’application de débogage associé à ce site de script.|  
|[IActiveScriptSiteDebug::GetRootApplicationNode](../../winscript/reference/iactivescriptsitedebug-getrootapplicationnode.md)|Obtient le nœud d’application sous le script de documents doivent être ajoutés.|  
|[IActiveScriptSiteDebug::OnScriptErrorDebug](../../winscript/reference/iactivescriptsitedebug-onscripterrordebug.md)|Permet à un hôte intelligent déterminer comment gérer les erreurs d’exécution.|