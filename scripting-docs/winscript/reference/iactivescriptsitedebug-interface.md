---
title: Interface IActiveScriptSiteDebug | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 339325686d2a98e34c6e9f96056612769a9e110e
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54348306"
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