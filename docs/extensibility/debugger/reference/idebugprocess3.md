---
title: "IDebugProcess3 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProcess3"
helpviewer_keywords: 
  - "Interface de IDebugProcess3"
ms.assetid: 7bd6b952-cf34-4e66-b8f6-d472dac3748f
caps.latest.revision: 24
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 24
---
# IDebugProcess3
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Cette interface représente un processus en cours de exécution et ses programmes.  cette interface existe comme remplacement à plusieurs méthodes dans l'interface d' [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) .  il fournit le contrôle de tous les programmes dans le processus.  
  
> [!NOTE]
>  Les méthodes d'[Continuer](../../../extensibility/debugger/reference/idebugprogram2-continue.md), d' [Exécuter](../../../extensibility/debugger/reference/idebugprogram2-execute.md), et d' [Étape](../../../extensibility/debugger/reference/idebugprogram2-step.md) sont déconseillées et ne doivent plus être utilisées.  Utilisez les méthodes correspondantes de l'interface d' `IDebugProcess3` à la place.  
  
## Syntaxe  
  
```  
IDebugProcess3 : IDebugProcess2  
```  
  
## Remarques à l'intention des implémenteurs  
 Cette interface est implémentée par un fournisseur de port pour gérer des programmes en tant que groupe.  Lorsque des programmes sont gérés en tant que groupe, vous pouvez contrôler leur exécution et générer un langage pour un évaluateur d'expression.  cette interface doit être implémentée par le fournisseur de port.  
  
## Remarques pour les appelants  
 Cette interface est appelée principalement par le gestionnaire de débogage de \(SDM\) connexion pour interagir avec un groupe de programmes identifiés dans ce processus.  
  
 Appelez [QueryInterface](/visual-cpp/atl/queryinterface) à une interface de [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) pour obtenir cette interface.  
  
## méthodes en commande de Vtable  
 En plus de les méthodes héritées d' [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md), `IDebugProcess3` implémente les méthodes suivantes.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[Continuer](../../../extensibility/debugger/reference/idebugprocess3-continue.md)|Reprend l'exécution de ou la progression via un processus.|  
|[Exécuter](../../../extensibility/debugger/reference/idebugprocess3-execute.md)|commence l'exécution d'un processus.|  
|[Étape](../../../extensibility/debugger/reference/idebugprocess3-step.md)|Pas en avant une instruction ou une instruction dans le processus.|  
|[GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md)|Obtient la raison pour laquelle le processus a été lancé pour le débogage.|  
|[SetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-sethostingprocesslanguage.md)|Définit le langage d'hébergement afin que le moteur de débogage puisse charger l'évaluateur d'expression approprié.|  
|[GetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-gethostingprocesslanguage.md)|Récupère le langage actuellement défini pour ce processus.|  
|[DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)|Les désactive modifient et continuent \(P.J.\) de ce processus.<br /><br /> Un fournisseur de port n'applique pas cette méthode \(il doit toujours retourner `E_NOTIMPL`\).|  
|[GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md)|passez l'état de P.J. pour ce processus.<br /><br /> Un fournisseur de port n'applique pas cette méthode \(il doit toujours retourner `E_NOTIMPL`\).|  
|[GetEngineFilter](../../../extensibility/debugger/reference/idebugprocess3-getenginefilter.md)|Extrait un tableau d'identificateurs uniques pour les moteurs de débogage disponibles.|  
  
## Configuration requise  
 en\-tête : Msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)