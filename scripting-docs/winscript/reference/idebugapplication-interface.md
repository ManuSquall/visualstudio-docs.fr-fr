---
title: "IDebugApplication, interface | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugApplication (interface)"
ms.assetid: 5dfa941b-4cd9-46fa-a230-3f41df9ea205
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugApplication, interface
Expose les méthodes de débogage non distant pour une utilisation par les moteurs de langage et les hôtes.  
  
 Outre les méthodes héritées de `IRemoteDebugApplication`, l'interface `IDebugApplication` expose les méthodes suivantes.  
  
## Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|-------------|-----------------|  
|[IDebugApplication::SetName](../../winscript/reference/idebugapplication-setname.md)|Définit le nom de l'application.|  
|[IDebugApplication::StepOutComplete](../../winscript/reference/idebugapplication-stepoutcomplete.md)|Informe le processus de débogage le gestionnaire qu'un moteur de langage en mode en pas \- à \- pas est sur le point de revenir à son appelant.|  
|[IDebugApplication::DebugOutput](../../winscript/reference/idebugapplication-debugoutput.md)|Provoque la chaîne donnée d'être affichée par le débogueur IDE.|  
|[IDebugApplication::StartDebugSession](../../winscript/reference/idebugapplication-startdebugsession.md)|Démarre le débogueur par défaut l'IDE et lie une session de débogage à cette application, si une n'est pas déjà attachée.|  
|[IDebugApplication::HandleBreakPoint](../../winscript/reference/idebugapplication-handlebreakpoint.md)|Entraîne le blocage du thread actuel et envoie une notification du point d'arrêt au débogueur IDE.|  
|[IDebugApplication::Close](../../winscript/reference/idebugapplication-close.md)|Provoque cette application de libérer toutes les références et d'entrer un état inactif.|  
|[IDebugApplication::GetBreakFlags](../../winscript/reference/idebugapplication-getbreakflags.md)|Retourne les balises actuelles de l'arrêt de l'application.|  
|[IDebugApplication::GetCurrentThread](../../winscript/reference/idebugapplication-getcurrentthread.md)|Retourne le thread associé au thread en cours de exécution.|  
|[IDebugApplication::CreateAsyncDebugOperation](../../winscript/reference/idebugapplication-createasyncdebugoperation.md)|Fournit l'accès à une opération asynchrone de débogage synchrone donnée.|  
|[IDebugApplication::AddStackFrameSniffer](../../winscript/reference/idebugapplication-addstackframesniffer.md)|Ajoute un fournisseur d'énumérateur du frame de pile à cette application.|  
|[IDebugApplication::RemoveStackFrameSniffer](../../winscript/reference/idebugapplication-removestackframesniffer.md)|Supprime un fournisseur d'énumérateur du frame de pile de cette application.|  
|[IDebugApplication::QueryCurrentThreadIsDebuggerThread](../../winscript/reference/idebugapplication-querycurrentthreadisdebuggerthread.md)|Détermine si le thread en cours de exécution est le thread du débogueur.|  
|[IDebugApplication::SynchronousCallInDebuggerThread](../../winscript/reference/idebugapplication-synchronouscallindebuggerthread.md)|Fournit un mécanisme pour l'appel au code exécuté dans le thread du débogueur.|  
|[IDebugApplication::CreateApplicationNode](../../winscript/reference/idebugapplication-createapplicationnode.md)|Crée un nœud d'application qui est associé à un fournisseur de document spécifique.|  
|[IDebugApplication::FireDebuggerEvent](../../winscript/reference/idebugapplication-firedebuggerevent.md)|Déclenche un événement générique à l'interface d' `IApplicationDebugger` du débogueur.|  
|[IDebugApplication::HandleRuntimeError](../../winscript/reference/idebugapplication-handleruntimeerror.md)|Entraîne le blocage du thread actuel et envoie une notification de l'erreur au débogueur IDE.|  
|[IDebugApplication::FCanJitDebug](../../winscript/reference/idebugapplication-fcanjitdebug.md)|Détermine si un débogueur juste\-à\-temps \(\(JIT\) est enregistré.|  
|[IDebugApplication::FIsAutoJitDebugEnabled](../../winscript/reference/idebugapplication-fisautojitdebugenabled.md)|Détermine si un débogueur JIT est enregistré automatiquement pour déboguer les hôtes muets.|  
|[IDebugApplication::AddGlobalExpressionContextProvider](../../winscript/reference/idebugapplication-addglobalexpressioncontextprovider.md)|Ajoute un fournisseur global de contexte d'expression à cette application.|  
|[IDebugApplication::RemoveGlobalExpressionContextProvider](../../winscript/reference/idebugapplication-removeglobalexpressioncontextprovider.md)|Supprime un fournisseur global de contexte d'expression de cette application.|