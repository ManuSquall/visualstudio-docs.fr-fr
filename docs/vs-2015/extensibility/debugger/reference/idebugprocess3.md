---
title: IDebugProcess3 | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProcess3
helpviewer_keywords:
- IDebugProcess3 interface
ms.assetid: 7bd6b952-cf34-4e66-b8f6-d472dac3748f
caps.latest.revision: 25
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5b6c81634b89eb4c722e09a2449efbeb993fd8bf
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51753111"
---
# <a name="idebugprocess3"></a>IDebugProcess3
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Cette interface représente un processus en cours d’exécution et ses programmes. Cette interface existe sous la forme d’un remplacement pour plusieurs méthodes dans le [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) interface. Il fournit un contrôle sur tous les programmes dans le processus.  
  
> [!NOTE]
>  [Continuer](../../../extensibility/debugger/reference/idebugprogram2-continue.md), [Execute](../../../extensibility/debugger/reference/idebugprogram2-execute.md), et [étape](../../../extensibility/debugger/reference/idebugprogram2-step.md) méthodes sont déconseillés et ne doit plus être utilisés. Utilisez les méthodes correspondantes sur le `IDebugProcess3` à la place de l’interface.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugProcess3 : IDebugProcess2  
```  
  
## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs  
 Cette interface est implémentée par un fournisseur de port personnalisé pour gérer des programmes en tant que groupe. Lorsque les programmes sont gérés en tant que groupe, vous pouvez contrôler leur exécution et établir une langue pour un évaluateur d’expression. Cette interface doit être implémentée par le fournisseur de port.  
  
## <a name="notes-for-callers"></a>Notes de publication pour les appelants  
 Cette interface est appelée principalement par le Gestionnaire de session de débogage (SDM) pour interagir avec un groupe de programmes identifiée dans ce processus.  
  
 Appelez [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) sur un [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) interface pour obtenir cette interface.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Outre les méthodes héritées de [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md), `IDebugProcess3` implémente les méthodes suivantes.  
  
|Méthode|Description|  
|------------|-----------------|  
|[Continue](../../../extensibility/debugger/reference/idebugprocess3-continue.md)|Continue l’exécution d’ou en parcourant un processus.|  
|[Execute](../../../extensibility/debugger/reference/idebugprocess3-execute.md)|Commence l’exécution d’un processus.|  
|[Step](../../../extensibility/debugger/reference/idebugprocess3-step.md)|Étapes de transférer une instruction ou une instruction dans le processus.|  
|[GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md)|Obtient la raison que le processus a été lancé pour le débogage.|  
|[SetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-sethostingprocesslanguage.md)|Définit la langue d’hébergement pour que le moteur de débogage puisse charger l’évaluateur d’expression appropriée.|  
|[GetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-gethostingprocesslanguage.md)|Récupère la langue actuellement définie pour ce processus.|  
|[DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)|Désactive Modifier & Continuer (ENC) pour ce processus.<br /><br /> Un fournisseur de port personnalisé n’implémente pas cette méthode (elle doit toujours retourner `E_NOTIMPL`).|  
|[GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md)|Obtenir l’état ENC pour ce processus.<br /><br /> Un fournisseur de port personnalisé n’implémente pas cette méthode (elle doit toujours retourner `E_NOTIMPL`).|  
|[GetEngineFilter](../../../extensibility/debugger/reference/idebugprocess3-getenginefilter.md)|Récupère un tableau d’identificateurs uniques pour les moteurs de débogage disponibles.|  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : Msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces principales](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)

