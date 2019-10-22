---
title: IActiveScript | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScript interface
ms.assetid: d8acee11-7f0d-4999-b97a-66774af16f71
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7a33db2bcbcb356a508fec2e6bc5449a899a1299
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577237"
---
# <a name="iactivescript"></a>IActiveScript
Fournit les méthodes nécessaires pour initialiser le moteur de script. Le moteur de script doit implémenter l’interface `IActiveScript`.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|------------|-----------------|  
|[IActiveScript::SetScriptSite](../../winscript/reference/iactivescript-setscriptsite.md)|Informe le moteur de script du site [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) fourni par l’hôte.|  
|[IActiveScript::GetScriptSite](../../winscript/reference/iactivescript-getscriptsite.md)|Récupère l’objet de site associé au moteur de script Windows.|  
|[IActiveScript::SetScriptState](../../winscript/reference/iactivescript-setscriptstate.md)|Place le moteur de script dans l’état spécifié.|  
|[IActiveScript::GetScriptState](../../winscript/reference/iactivescript-getscriptstate.md)|Récupère l’état actuel du moteur de script.|  
|[IActiveScript::Close](../../winscript/reference/iactivescript-close.md)|Fait en sorte que le moteur de script abandonne tout script actuellement chargé, perd son état et libère tous les pointeurs d’interface qu’il possède vers d’autres objets, ce qui permet d’entrer dans un état fermé.|  
|[IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md)|Ajoute le nom d’un élément de niveau racine à l’espace de noms du moteur de script.|  
|[IActiveScript::AddTypeLib](../../winscript/reference/iactivescript-addtypelib.md)|Ajoute une bibliothèque de types à l’espace de noms pour le script.|  
|[IActiveScript::GetScriptDispatch](../../winscript/reference/iactivescript-getscriptdispatch.md)|Récupère l’interface `IDispatch` pour le script en cours d’exécution.|  
|[IActiveScript::GetCurrentScriptThreadID](../../winscript/reference/iactivescript-getcurrentscriptthreadid.md)|Récupère un identificateur défini par le moteur de script pour le thread en cours d’exécution.|  
|[IActiveScript::GetScriptThreadID](../../winscript/reference/iactivescript-getscriptthreadid.md)|Récupère un identificateur défini par le moteur de script pour le thread associé au thread Microsoft Win32 donné.|  
|[IActiveScript::GetScriptThreadState](../../winscript/reference/iactivescript-getscriptthreadstate.md)|Récupère l’état actuel d’un thread de script.|  
|[IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)|Interrompt l’exécution d’un thread de script en cours d’exécution.|  
|[IActiveScript::Clone](../../winscript/reference/iactivescript-clone.md)|Clone le moteur de script actuel (moins tout état d’exécution en cours), en retournant un moteur de script chargé qui n’a pas de site dans le thread actuel.|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence d’interfaces de script Windows](../../winscript/reference/windows-script-interfaces-reference.md)