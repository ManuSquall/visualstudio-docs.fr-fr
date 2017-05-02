---
title: "D&#233;bogueur de script actif, interfaces | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "Débogueur de script actif (interfaces)"
  - "activdbg.h"
ms.assetid: bf4750b1-4e58-442b-ab56-254e640de61d
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# D&#233;bogueur de script actif, interfaces
Les fichiers d'en\-tête d'activdbg.h et d'activdbg100.h fournissent des interfaces, des énumérations, et les structures répertoriées dans cette section.  Ils sont pour déboguer le script.  
  
> [!NOTE]
>  Les interfaces d'`IJSDebug*` et l'interface `IEnumJsStackFrames` étaient des premières libérées dans Internet Explorer 11 pour le débogage de code natif avec le script.  Le fichier d'en\-tête pour ces interfaces est jscript9diag.h.  
  
## Dans cette section  
 Les interfaces suivantes permettent le débogage indépendant du langage et hôte neutre :  
  
-   [Débogueur de script actif, constantes, énumérations et structures](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)  
  
-   [IActiveScriptDebug, interface](../../winscript/reference/iactivescriptdebug-interface.md)  
  
-   [IActiveScriptErrorDebug, interface](../../winscript/reference/iactivescripterrordebug-interface.md)  
  
-   [IActiveScriptErrorDebug110 \(interface\)](../../winscript/reference/iactivescripterrordebug110-interface.md)  
  
-   [IActiveScriptSiteDebug, interface](../../winscript/reference/iactivescriptsitedebug-interface.md)  
  
-   [IActiveScriptSiteDebugEx \(interface\)](../../winscript/reference/iactivescriptsitedebugex-interface.md)  
  
-   [IActiveScriptWinRTErrorDebug \(interface\)](../../winscript/reference/iactivescriptwinrterrordebug-interface.md)  
  
-   [IApplicationDebugger, interface](../../winscript/reference/iapplicationdebugger-interface.md)  
  
-   [IApplicationDebuggerUI, interface](../../winscript/reference/iapplicationdebuggerui-interface.md)  
  
-   [IDebugApplication, interface](../../winscript/reference/idebugapplication-interface.md)  
  
-   [IDebugApplication110 \(interface\)](../../winscript/reference/idebugapplication110-interface.md)  
  
-   [IDebugApplicationNode, interface](../../winscript/reference/idebugapplicationnode-interface.md)  
  
-   [IDebugApplicationNode100 \(interface\)](../../winscript/reference/idebugapplicationnode100-interface.md)  
  
-   [IDebugApplicationNodeEvents, interface](../../winscript/reference/idebugapplicationnodeevents-interface.md)  
  
-   [IDebugApplicationThread, interface](../../winscript/reference/idebugapplicationthread-interface.md)  
  
-   [IDebugApplicationThread110 \(interface\)](../../winscript/reference/idebugapplicationthread110-interface.md)  
  
-   [IDebugApplicationThreadEvents110 \(interface\)](../../winscript/reference/idebugapplicationthreadevents110-interface.md)  
  
-   [IDebugAsyncOperation, interface](../../winscript/reference/idebugasyncoperation-interface.md)  
  
-   [IDebugAsyncOperationCallBack, interface](../../winscript/reference/idebugasyncoperationcallback-interface.md)  
  
-   [IDebugCodeContext, interface](../../winscript/reference/idebugcodecontext-interface.md)  
  
-   [IDebugCookie, interface](../../winscript/reference/idebugcookie-interface.md)  
  
-   [IDebugDocument, interface](../../winscript/reference/idebugdocument-interface.md)  
  
-   [IDebugDocumentContext, interface](../../winscript/reference/idebugdocumentcontext-interface.md)  
  
-   [IDebugDocumentHelper, interface](../../winscript/reference/idebugdocumenthelper-interface.md)  
  
-   [IDebugDocumentHost, interface](../../winscript/reference/idebugdocumenthost-interface.md)  
  
-   [IDebugDocumentInfo, interface](../../winscript/reference/idebugdocumentinfo-interface.md)  
  
-   [IDebugDocumentProvider, interface](../../winscript/reference/idebugdocumentprovider-interface.md)  
  
-   [IDebugDocumentText, interface](../../winscript/reference/idebugdocumenttext-interface.md)  
  
-   [IDebugDocumentTextAuthor, interface](../../winscript/reference/idebugdocumenttextauthor-interface.md)  
  
-   [IDebugDocumentTextEvents, interface](../../winscript/reference/idebugdocumenttextevents-interface.md)  
  
-   [IDebugDocumentTextExternalAuthor, interface](../../winscript/reference/idebugdocumenttextexternalauthor-interface.md)  
  
-   [IDebugExpression, interface](../../winscript/reference/idebugexpression-interface.md)  
  
-   [IDebugExpressionCallBack, interface](../../winscript/reference/idebugexpressioncallback-interface.md)  
  
-   [IDebugExpressionContext, interface](../../winscript/reference/idebugexpressioncontext-interface.md)  
  
-   [IDebugFormatter, interface](../../winscript/reference/idebugformatter-interface.md)  
  
-   [IDebugHelper, interface](../../winscript/reference/idebughelper-interface.md)  
  
-   [IDebugSessionProvider, interface](../../winscript/reference/idebugsessionprovider-interface.md)  
  
-   [IDebugSessionProviderEx, interface](../../winscript/reference/idebugsessionproviderex-interface.md)  
  
-   [IDebugStackFrame, interface](../../winscript/reference/idebugstackframe-interface.md)  
  
-   [IDebugStackFrameSniffer, interface](../../winscript/reference/idebugstackframesniffer-interface.md)  
  
-   [IDebugStackFrameSnifferEx, interface](../../winscript/reference/idebugstackframesnifferex-interface.md)  
  
-   [IDebugSyncOperation, interface](../../winscript/reference/idebugsyncoperation-interface.md)  
  
-   [IDebugThreadCall, interface](../../winscript/reference/idebugthreadcall-interface.md)  
  
-   [IEnumDebugApplicationNodes, interface](../../winscript/reference/ienumdebugapplicationnodes-interface.md)  
  
-   [IEnumDebugCodeContexts, interface](../../winscript/reference/ienumdebugcodecontexts-interface.md)  
  
-   [IEnumDebugExpressionContexts, interface](../../winscript/reference/ienumdebugexpressioncontexts-interface.md)  
  
-   [IEnumDebugStackFrames, interface](../../winscript/reference/ienumdebugstackframes-interface.md)  
  
-   [IEnumJsStackFrames, interface](../../winscript/reference/ienumjsstackframes-interface.md)  
  
-   [IEnumRemoteDebugApplications, interface](../../winscript/reference/ienumremotedebugapplications-interface.md)  
  
-   [IEnumRemoteDebugApplicationThreads, interface](../../winscript/reference/ienumremotedebugapplicationthreads-interface.md)  
  
-   [IJsDebug, interface](../../winscript/reference/ijsdebug-interface.md)  
  
-   [IJsDebugBreakPoint, interface](../../winscript/reference/ijsdebugbreakpoint-interface.md)  
  
-   [IJsDebugDataTarget, interface](../../winscript/reference/ijsdebugdatatarget-interface.md)  
  
-   [IJsDebugFrame, interface](../../winscript/reference/ijsdebugframe-interface.md)  
  
-   [IJsDebugProcess, interface](../../winscript/reference/ijsdebugprocess-interface.md)  
  
-   [IJsDebugProperty, interface](../../winscript/reference/ijsdebugproperty-interface.md)  
  
-   [IJsDebugStackWalker, interface](../../winscript/reference/ijsdebugstackwalker-interface.md)  
  
-   [IJsEnumDebugProperty, interface](../../winscript/reference/ijsenumdebugproperty-interface.md)  
  
-   [IMachineDebugManager, interface](../../winscript/reference/imachinedebugmanager-interface.md)  
  
-   [IMachineDebugManagerCookie, interface](../../winscript/reference/imachinedebugmanagercookie-interface.md)  
  
-   [IMachineDebugManagerEvents, interface](../../winscript/reference/imachinedebugmanagerevents-interface.md)  
  
-   [IProcessDebugManager, interface](../../winscript/reference/iprocessdebugmanager-interface.md)  
  
-   [IProvideExpressionContexts, interface](../../winscript/reference/iprovideexpressioncontexts-interface.md)  
  
-   [IRemoteDebugApplication, interface](../../winscript/reference/iremotedebugapplication-interface.md)  
  
-   [IRemoteDebugApplication110 \(interface\)](../../winscript/reference/iremotedebugapplication110-interface.md)  
  
-   [IRemoteDebugApplicationEx \(interface\)](../../winscript/reference/iremotedebugapplicationex-interface.md)  
  
-   [IRemoteDebugApplicationEvents, interface](../../winscript/reference/iremotedebugapplicationevents-interface.md)  
  
-   [IRemoteDebugApplicationThread, interface](../../winscript/reference/iremotedebugapplicationthread-interface.md)  
  
-   [IRemoteDebugApplicationThreadEx \(interface\)](../../winscript/reference/iremotedebugapplicationthreadex-interface.md)  
  
-   [ISetNextStatement, interface](../../winscript/reference/isetnextstatement-interface.md)  
  
-   [ISimpleConnectionPoint, interface](../../winscript/reference/isimpleconnectionpoint-interface.md)  
  
-   [IWebAppDiagnosticsSetup \(interface\)](../../winscript/reference/iwebappdiagnosticssetup-interface.md)  
  
-   [IWebAppDiagnosticsObjectInitialization \(interface\)](../../winscript/reference/iwebappdiagnosticsobjectinitialization-interface.md)  
  
 La section suivante répertorie des constantes, des énumérations, et les structures utilisées pour le débogage :  
  
-   [Débogueur de script actif, constantes, énumérations et structures](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)  
  
## Voir aussi  
 [Débogage de script actif, présentation](../../winscript/active-script-debugging-overview.md)