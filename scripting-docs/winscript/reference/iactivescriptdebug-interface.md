---
title: IActiveScriptDebug (Interface) | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IActiveScriptDebug interface
ms.assetid: e3e28cba-ee08-4a52-973a-b74be488c348
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a1e1d0c1cf51c63f1bb3fcd90ae72520da907e50
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptdebug-interface"></a>IActiveScriptDebug, interface
Implémenté par les moteurs de script que prise en charge le débogage. En règle générale, un objet qui implémente le `IActiveScriptDebug` interface également implémente la `IActiveScript` interface. Si c’est le cas, appelez le `IActiveScript::QueryInterface` méthode pour obtenir le `IActiveScriptDebug` interface.  
  
 Le `IActiveScriptDebug` interface fournit les moyens pour :  
  
-   Hôtes actifs reprendre la gestion des documents.  
  
-   Gestionnaire de processus de débogage pour synchroniser plusieurs moteurs de script de débogage.  
  
 Outre les méthodes héritées de `IUnknown`, le `IActiveScriptDebug` interface expose les méthodes suivantes.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|------------|-----------------|  
|[IActiveScriptDebug::GetScriptTextAttributes](../../winscript/reference/iactivescriptdebug-getscripttextattributes.md)|Retourne les attributs de texte pour un bloc arbitraire de texte du script.|  
|[IActiveScriptDebug::GetScriptletTextAttributes](../../winscript/reference/iactivescriptdebug-getscriptlettextattributes.md)|Retourne les attributs de texte pour un scriptlet arbitraire.|  
|[IActiveScriptDebug::EnumCodeContextsOfPosition](../../winscript/reference/iactivescriptdebug-enumcodecontextsofposition.md)|Délègue à `IDebugDocumentContext::EnumCodeContexts`.|