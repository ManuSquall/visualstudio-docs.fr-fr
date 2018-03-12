---
title: IDebugApplication (Interface) | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IDebugApplication interface
ms.assetid: 5dfa941b-4cd9-46fa-a230-3f41df9ea205
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 07964292785634212099a0bfcf8174ebb55e8713
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplication-interface"></a>IDebugApplication, interface
Expose les méthodes de débogage non distant pour une utilisation par les ordinateurs hôtes et les moteurs de langue.  
  
 Outre les méthodes héritées de `IRemoteDebugApplication`, le `IDebugApplication` interface expose les méthodes suivantes.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|------------|-----------------|  
|[IDebugApplication::SetName](../../winscript/reference/idebugapplication-setname.md)|Définit le nom de l’application.|  
|[IDebugApplication::StepOutComplete](../../winscript/reference/idebugapplication-stepoutcomplete.md)|Notifie le Gestionnaire de processus de débogage qu’un moteur de langue en mode de pas à pas est sur le point de retourner à son appelant.|  
|[IDebugApplication::DebugOutput](../../winscript/reference/idebugapplication-debugoutput.md)|Provoque la chaîne donnée à afficher par le débogueur IDE.|  
|[IDebugApplication::StartDebugSession](../../winscript/reference/idebugapplication-startdebugsession.md)|Démarre le débogueur par défaut IDE et l’attache une session de débogage de cette application, si un n’est pas déjà attaché.|  
|[IDebugApplication::HandleBreakPoint](../../winscript/reference/idebugapplication-handlebreakpoint.md)|Provoque le blocage du thread actuel et envoie une notification du point d’arrêt dans le débogueur IDE.|  
|[IDebugApplication::Close](../../winscript/reference/idebugapplication-close.md)|Provoque cette application pour libérer toutes les références et d’entrer dans un état inactif.|  
|[IDebugApplication::GetBreakFlags](../../winscript/reference/idebugapplication-getbreakflags.md)|Retourne les indicateurs d’arrêt en cours pour l’application.|  
|[IDebugApplication::GetCurrentThread](../../winscript/reference/idebugapplication-getcurrentthread.md)|Retourne le thread associé au thread en cours d’exécution.|  
|[IDebugApplication::CreateAsyncDebugOperation](../../winscript/reference/idebugapplication-createasyncdebugoperation.md)|Fournit l’accès asynchrone à une opération de débogage synchrone donné.|  
|[IDebugApplication::AddStackFrameSniffer](../../winscript/reference/idebugapplication-addstackframesniffer.md)|Ajoute un fournisseur d’énumérateur de frame de pile pour cette application.|  
|[IDebugApplication::RemoveStackFrameSniffer](../../winscript/reference/idebugapplication-removestackframesniffer.md)|Supprime un fournisseur d’énumérateur de frame de pile de cette application.|  
|[IDebugApplication::QueryCurrentThreadIsDebuggerThread](../../winscript/reference/idebugapplication-querycurrentthreadisdebuggerthread.md)|Détermine si le thread en cours d’exécution actuel est le thread de débogueur.|  
|[IDebugApplication::SynchronousCallInDebuggerThread](../../winscript/reference/idebugapplication-synchronouscallindebuggerthread.md)|Fournit un mécanisme exécuter du code dans le thread de débogueur à l’appelant.|  
|[IDebugApplication::CreateApplicationNode](../../winscript/reference/idebugapplication-createapplicationnode.md)|Crée un nouveau nœud d’application qui est associé à un fournisseur de document spécifique.|  
|[IDebugApplication::FireDebuggerEvent](../../winscript/reference/idebugapplication-firedebuggerevent.md)|Déclenche un événement générique du débogueur `IApplicationDebugger` interface.|  
|[IDebugApplication::HandleRuntimeError](../../winscript/reference/idebugapplication-handleruntimeerror.md)|Provoque le blocage du thread actuel et envoie une notification de l’erreur à l’IDE de débogueur.|  
|[IDebugApplication::FCanJitDebug](../../winscript/reference/idebugapplication-fcanjitdebug.md)|Détermine si un débogueur de (JIT) juste-à-temps est inscrite.|  
|[IDebugApplication::FIsAutoJitDebugEnabled](../../winscript/reference/idebugapplication-fisautojitdebugenabled.md)|Détermine si un débogueur JIT est inscrit dans auto-debug des hôtes passifs.|  
|[IDebugApplication::AddGlobalExpressionContextProvider](../../winscript/reference/idebugapplication-addglobalexpressioncontextprovider.md)|Ajoute un fournisseur de contexte expression globale de cette application.|  
|[IDebugApplication::RemoveGlobalExpressionContextProvider](../../winscript/reference/idebugapplication-removeglobalexpressioncontextprovider.md)|Supprime un fournisseur de contexte expression globale de cette application.|