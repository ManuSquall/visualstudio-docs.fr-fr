---
title: IActiveScript | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IActiveScript interface
ms.assetid: d8acee11-7f0d-4999-b97a-66774af16f71
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 68d91a7ad91364d0c2133150d76cdb221929b16b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescript"></a>IActiveScript
Fournit les méthodes nécessaires pour initialiser le moteur de script. Le moteur de script doit implémenter la `IActiveScript` interface.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|------------|-----------------|  
|[IActiveScript::SetScriptSite](../../winscript/reference/iactivescript-setscriptsite.md)|Informe le moteur de script de la [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) site fourni par l’hôte.|  
|[IActiveScript::GetScriptSite](../../winscript/reference/iactivescript-getscriptsite.md)|Récupère l’objet de site associé au moteur de Script Windows.|  
|[IActiveScript::SetScriptState](../../winscript/reference/iactivescript-setscriptstate.md)|Place le moteur de script dans l’état spécifié.|  
|[IActiveScript::GetScriptState](../../winscript/reference/iactivescript-getscriptstate.md)|Récupère l’état actuel du moteur de script.|  
|[IActiveScript::Close](../../winscript/reference/iactivescript-close.md)|Force le moteur de script à n’importe quel script actuellement chargé d’abandon, son état est perdu et libérer les pointeurs d’interface qu’à d’autres objets, donc dans un état fermé.|  
|[IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md)|Ajoute le nom d’un élément de niveau racine pour l’espace de noms du moteur de script.|  
|[IActiveScript::AddTypeLib](../../winscript/reference/iactivescript-addtypelib.md)|Ajoute une bibliothèque de types à l’espace de noms pour le script.|  
|[IActiveScript::GetScriptDispatch](../../winscript/reference/iactivescript-getscriptdispatch.md)|Récupère le `IDispatch` interface pour le script en cours d’exécution.|  
|[IActiveScript::GetCurrentScriptThreadID](../../winscript/reference/iactivescript-getcurrentscriptthreadid.md)|Récupère un identificateur de script-moteur-définies pour le thread en cours d’exécution.|  
|[IActiveScript::GetScriptThreadID](../../winscript/reference/iactivescript-getscriptthreadid.md)|Récupère un identificateur de script-moteur-définies pour le thread associé au thread Microsoft Win32 donné.|  
|[IActiveScript::GetScriptThreadState](../../winscript/reference/iactivescript-getscriptthreadstate.md)|Récupère l’état actuel d’un thread de script.|  
|[IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)|Interrompt l’exécution d’un thread en cours d’exécution de script.|  
|[IActiveScript::Clone](../../winscript/reference/iactivescript-clone.md)|Clone le moteur de script actuel (moins de n’importe quel état d’exécution actuel), retournant un moteur de script chargé qui ne possède aucun site dans le thread actuel.|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence d’interfaces de script Windows](../../winscript/reference/windows-script-interfaces-reference.md)