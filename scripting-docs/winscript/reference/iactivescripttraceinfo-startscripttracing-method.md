---
title: Iactivescripttraceinfo::startscripttracing, méthode | Documents Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 90fac5ed-ce15-49b7-a6f1-605ede6f34e2
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e999ad0d40f4d832330fee6db17b64ae9da50f08
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24724879"
---
# <a name="iactivescripttraceinfostartscripttracing-method"></a>IActiveScriptTraceInfo::StartScriptTracing, méthode
Démarre le traçage de script.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT StartScriptTracing(     [in] IActiveScriptSiteTraceInfo * pSiteTraceInfo,     [in] GUID guidContextID );   
```  
  
#### <a name="parameters"></a>Paramètres  
 `pSiteTraceInfo`  
 Pointeur vers IActiveScriptSiteTraceInfo l’hôte.  
  
 `guidContextId`  
 Le GUID du contexte.  
  
## <a name="return-value"></a>Valeur de retour  
 Les valeurs de retournés possibles pour cette méthode sont les suivants :  
  
1.  S_OK : réussite.  
  
2.  E_POINTER : `pSiteTraceInfo` est un pointeur NULL.  
  
3.  E_NOTIMPL : Non implémenté.