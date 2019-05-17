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
ms.openlocfilehash: 5b7e3a0172a798eab9a743f446dff3d339a785b2
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63436081"
---
# <a name="iactivescript"></a>IActiveScript
Fournit les méthodes nécessaires pour initialiser le moteur de script. Le moteur de script doit implémenter le `IActiveScript` interface.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|------------|-----------------|  
|[IActiveScript::SetScriptSite](../../winscript/reference/iactivescript-setscriptsite.md)|Informe le moteur de script de la [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) site fourni par l’hôte.|  
|[IActiveScript::GetScriptSite](../../winscript/reference/iactivescript-getscriptsite.md)|Récupère l’objet de site associé avec le moteur de Script de Windows.|  
|[IActiveScript::SetScriptState](../../winscript/reference/iactivescript-setscriptstate.md)|Place le moteur de script dans l’état spécifié.|  
|[IActiveScript::GetScriptState](../../winscript/reference/iactivescript-getscriptstate.md)|Récupère l’état actuel du moteur de script.|  
|[IActiveScript::Close](../../winscript/reference/iactivescript-close.md)|Provoque le moteur de script abandonner n’importe quel script actuellement chargé, son état est perdu et libérer les pointeurs d’interface qu’à d’autres objets, donc dans un état fermé.|  
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