---
title: Interface IDebugApplication | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplication interface
ms.assetid: 5dfa941b-4cd9-46fa-a230-3f41df9ea205
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b3483bea94d7a53fabf3f552df97a681307b885c
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54349723"
---
# <a name="idebugapplication-interface"></a>IDebugApplication, interface
Expose des méthodes de débogage non distant pour une utilisation par les hôtes et les moteurs de langage.  
  
 Outre les méthodes héritées de `IRemoteDebugApplication`, le `IDebugApplication` interface expose les méthodes suivantes.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|------------|-----------------|  
|[IDebugApplication::SetName](../../winscript/reference/idebugapplication-setname.md)|Définit le nom de l’application.|  
|[IDebugApplication::StepOutComplete](../../winscript/reference/idebugapplication-stepoutcomplete.md)|Notifie le Gestionnaire de débogage de processus qu’un moteur de langage en mode de pas à pas est sur le point de retourner à son appelant.|  
|[IDebugApplication::DebugOutput](../../winscript/reference/idebugapplication-debugoutput.md)|Provoque la chaîne donnée à afficher par l’IDE de débogueur.|  
|[IDebugApplication::StartDebugSession](../../winscript/reference/idebugapplication-startdebugsession.md)|Démarre l’IDE de débogueur par défaut et attache une session de débogage de cette application, si un n’est pas déjà attaché.|  
|[IDebugApplication::HandleBreakPoint](../../winscript/reference/idebugapplication-handlebreakpoint.md)|Provoque le blocage du thread actuel et envoie une notification du point d’arrêt à l’IDE de débogueur.|  
|[IDebugApplication::Close](../../winscript/reference/idebugapplication-close.md)|Provoque cette application pour libérer toutes les références et entrer dans un état inactif.|  
|[IDebugApplication::GetBreakFlags](../../winscript/reference/idebugapplication-getbreakflags.md)|Retourne les indicateurs d’arrêt en cours pour l’application.|  
|[IDebugApplication::GetCurrentThread](../../winscript/reference/idebugapplication-getcurrentthread.md)|Retourne le thread associé au thread en cours d’exécution.|  
|[IDebugApplication::CreateAsyncDebugOperation](../../winscript/reference/idebugapplication-createasyncdebugoperation.md)|Fournit un accès asynchrone à une opération de débogage synchrone donnée.|  
|[IDebugApplication::AddStackFrameSniffer](../../winscript/reference/idebugapplication-addstackframesniffer.md)|Ajoute un fournisseur d’énumérateur de frame de pile pour cette application.|  
|[IDebugApplication::RemoveStackFrameSniffer](../../winscript/reference/idebugapplication-removestackframesniffer.md)|Supprime un fournisseur d’énumérateur de frame de pile de cette application.|  
|[IDebugApplication::QueryCurrentThreadIsDebuggerThread](../../winscript/reference/idebugapplication-querycurrentthreadisdebuggerthread.md)|Détermine si le thread en cours d’exécution actuel est le thread de débogueur.|  
|[IDebugApplication::SynchronousCallInDebuggerThread](../../winscript/reference/idebugapplication-synchronouscallindebuggerthread.md)|Fournit un mécanisme pour que l’appelant exécuter du code dans le thread de débogueur.|  
|[IDebugApplication::CreateApplicationNode](../../winscript/reference/idebugapplication-createapplicationnode.md)|Crée un nouveau nœud d’application qui est associé à un fournisseur de document spécifique.|  
|[IDebugApplication::FireDebuggerEvent](../../winscript/reference/idebugapplication-firedebuggerevent.md)|Déclenche un événement générique pour le débogueur `IApplicationDebugger` interface.|  
|[IDebugApplication::HandleRuntimeError](../../winscript/reference/idebugapplication-handleruntimeerror.md)|Provoque le blocage du thread actuel et envoie une notification de l’erreur à l’IDE de débogueur.|  
|[IDebugApplication::FCanJitDebug](../../winscript/reference/idebugapplication-fcanjitdebug.md)|Détermine si un débogueur de (JIT) juste-à-temps est inscrit.|  
|[IDebugApplication::FIsAutoJitDebugEnabled](../../winscript/reference/idebugapplication-fisautojitdebugenabled.md)|Détermine si un débogueur JIT est inscrit auprès des hôtes stupides automatique-debug.|  
|[IDebugApplication::AddGlobalExpressionContextProvider](../../winscript/reference/idebugapplication-addglobalexpressioncontextprovider.md)|Ajoute un fournisseur de contexte d’expression globale à cette application.|  
|[IDebugApplication::RemoveGlobalExpressionContextProvider](../../winscript/reference/idebugapplication-removeglobalexpressioncontextprovider.md)|Supprime un fournisseur de contexte d’expression globale de cette application.|