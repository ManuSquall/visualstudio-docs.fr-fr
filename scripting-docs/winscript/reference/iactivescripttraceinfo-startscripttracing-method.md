---
title: Méthode IActiveScriptTraceInfo::StartScriptTracing | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 90fac5ed-ce15-49b7-a6f1-605ede6f34e2
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 824d60ef0f17012524f9d0150a90ccd9efcfb3a9
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58150957"
---
# <a name="iactivescripttraceinfostartscripttracing-method"></a>IActiveScriptTraceInfo::StartScriptTracing, méthode
Commence le traçage de script.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT StartScriptTracing(     [in] IActiveScriptSiteTraceInfo * pSiteTraceInfo,     [in] GUID guidContextID );   
```  
  
#### <a name="parameters"></a>Paramètres  
 `pSiteTraceInfo`  
 Pointeur vers IActiveScriptSiteTraceInfo l’hôte.  
  
 `guidContextId`  
 Le GUID du contexte.  
  
## <a name="return-value"></a>Valeur de retour  
 Les valeurs de retournés possibles pour cette méthode sont les suivantes :  
  
1.  S_OK: Opération réussie.  
  
2.  E_POINTER : `pSiteTraceInfo` est un pointeur NULL.  
  
3.  E_NOTIMPL : Non implémenté.