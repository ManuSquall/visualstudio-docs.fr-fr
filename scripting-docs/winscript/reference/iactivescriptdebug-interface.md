---
title: Interface IActiveScriptDebug | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 0e21f4c99da886bc4907acf8b0934e1b46d57689
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49942086"
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