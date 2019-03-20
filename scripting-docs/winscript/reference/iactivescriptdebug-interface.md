---
title: Interface IActiveScriptDebug | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptDebug interface
ms.assetid: e3e28cba-ee08-4a52-973a-b74be488c348
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6341b5c3763d6e4c836b3bdc0539552fcbe7f980
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58151022"
---
# <a name="iactivescriptdebug-interface"></a>IActiveScriptDebug, interface
Implémenté par les moteurs de script que prise en charge le débogage. En règle générale, un objet qui implémente le `IActiveScriptDebug` interface également implémente le `IActiveScript` interface. Si c’est le cas, appelez le `IActiveScript::QueryInterface` méthode pour obtenir le `IActiveScriptDebug` interface.  
  
 Le `IActiveScriptDebug` interface fournit les moyens pour :  
  
- Hôtes intelligents de reprendre la gestion des documents.  
  
- Gestionnaire de débogage de processus pour synchroniser le débogage de plusieurs moteurs de script.  
  
  Outre les méthodes héritées de `IUnknown`, le `IActiveScriptDebug` interface expose les méthodes suivantes.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|------------|-----------------|  
|[IActiveScriptDebug::GetScriptTextAttributes](../../winscript/reference/iactivescriptdebug-getscripttextattributes.md)|Retourne les attributs de texte pour un bloc de texte du script arbitraire.|  
|[IActiveScriptDebug::GetScriptletTextAttributes](../../winscript/reference/iactivescriptdebug-getscriptlettextattributes.md)|Retourne les attributs de texte pour un scriptlet arbitraire.|  
|[IActiveScriptDebug::EnumCodeContextsOfPosition](../../winscript/reference/iactivescriptdebug-enumcodecontextsofposition.md)|Délègue à `IDebugDocumentContext::EnumCodeContexts`.|