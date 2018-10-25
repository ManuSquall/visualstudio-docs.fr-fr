---
title: Interfaces de débogueur de Script actif | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- Active Script Debugger interfaces
- activdbg.h
ms.assetid: bf4750b1-4e58-442b-ab56-254e640de61d
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f260df5a23ef6b5ef6ef7253726b1fea7bc00269
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49855428"
---
# <a name="active-script-debugger-interfaces"></a>Débogueur de script actif, interfaces
Les fichiers d’en-tête activdbg.h et activdbg100.h fournissent les interfaces, les énumérations et les structures répertoriés dans cette section. Ils sont pour le débogage de script.  
  
> [!NOTE]
>  Le `IJSDebug*` interfaces et la `IEnumJsStackFrames` interface ont été apparus dans Internet Explorer 11 pour le débogage de code natif avec script. Le fichier d’en-tête pour ces interfaces est jscript9diag.h.  
  
## <a name="in-this-section"></a>Dans cette section  
 Les interfaces suivantes autoriser le débogage de linguistiquement neutre, hôte neutre :  
  
- [Constantes de débogueur de script actif, énumérations et structures](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)  
  
- [Interface IActiveScriptDebug](../../winscript/reference/iactivescriptdebug-interface.md)  
  
- [Interface IActiveScriptErrorDebug](../../winscript/reference/iactivescripterrordebug-interface.md)  
  
- [Interface IActiveScriptErrorDebug110](../../winscript/reference/iactivescripterrordebug110-interface.md)  
  
- [Interface IActiveScriptSiteDebug](../../winscript/reference/iactivescriptsitedebug-interface.md)  
  
- [Interface IActiveScriptSiteDebug32](../../winscript/reference/iactivescriptsitedebug32-interface.md)  
  
- [Interface IActiveScriptSiteDebugEx](../../winscript/reference/iactivescriptsitedebugex-interface.md)  
  
- [Interface IActiveScriptWinRTErrorDebug](../../winscript/reference/iactivescriptwinrterrordebug-interface.md)  
  
- [Interface IApplicationDebugger](../../winscript/reference/iapplicationdebugger-interface.md)  
  
- [Interface IApplicationDebuggerUI](../../winscript/reference/iapplicationdebuggerui-interface.md)  
  
- [Interface IDebugApplication](../../winscript/reference/idebugapplication-interface.md)  
  
- [Interface IDebugApplication110](../../winscript/reference/idebugapplication110-interface.md)  
  
- [Interface IDebugApplicationNode](../../winscript/reference/idebugapplicationnode-interface.md)  
  
- [Interface IDebugApplicationNode100](../../winscript/reference/idebugapplicationnode100-interface.md)  
  
- [Interface IDebugApplicationNodeEvents](../../winscript/reference/idebugapplicationnodeevents-interface.md)  
  
- [Interface IDebugApplicationThread](../../winscript/reference/idebugapplicationthread-interface.md)  
  
- [Interface IDebugApplicationThread110](../../winscript/reference/idebugapplicationthread110-interface.md)  
  
- [IDebugApplicationThreadEvents110 Interface](../../winscript/reference/idebugapplicationthreadevents110-interface.md)  
  
- [Interface IDebugAsyncOperation](../../winscript/reference/idebugasyncoperation-interface.md)  
  
- [Interface IDebugAsyncOperationCallBack](../../winscript/reference/idebugasyncoperationcallback-interface.md)  
  
- [Interface IDebugCodeContext](../../winscript/reference/idebugcodecontext-interface.md)  
  
- [Interface IDebugCookie](../../winscript/reference/idebugcookie-interface.md)  
  
- [Interface IDebugDocument](../../winscript/reference/idebugdocument-interface.md)  
  
- [Interface IDebugDocumentContext](../../winscript/reference/idebugdocumentcontext-interface.md)  
  
- [Interface IDebugDocumentHelper](../../winscript/reference/idebugdocumenthelper-interface.md)  
  
- [Interface IDebugDocumentHost](../../winscript/reference/idebugdocumenthost-interface.md)  
  
- [Interface IDebugDocumentInfo](../../winscript/reference/idebugdocumentinfo-interface.md)  
  
- [Interface IDebugDocumentProvider](../../winscript/reference/idebugdocumentprovider-interface.md)  
  
- [Interface IDebugDocumentText](../../winscript/reference/idebugdocumenttext-interface.md)  
  
- [Interface IDebugDocumentTextAuthor](../../winscript/reference/idebugdocumenttextauthor-interface.md)  
  
- [Interface IDebugDocumentTextEvents](../../winscript/reference/idebugdocumenttextevents-interface.md)  
  
- [Interface IDebugDocumentTextExternalAuthor](../../winscript/reference/idebugdocumenttextexternalauthor-interface.md)  
  
- [Interface IDebugExpression](../../winscript/reference/idebugexpression-interface.md)  
  
- [Interface IDebugExpressionCallBack](../../winscript/reference/idebugexpressioncallback-interface.md)  
  
- [Interface IDebugExpressionContext](../../winscript/reference/idebugexpressioncontext-interface.md)  
  
- [Interface IDebugFormatter](../../winscript/reference/idebugformatter-interface.md)  
  
- [Interface IDebugHelper](../../winscript/reference/idebughelper-interface.md)  
  
- [Interface IDebugSessionProvider](../../winscript/reference/idebugsessionprovider-interface.md)  
  
- [Interface IDebugSessionProviderEx](../../winscript/reference/idebugsessionproviderex-interface.md)  
  
- [Interface IDebugStackFrame](../../winscript/reference/idebugstackframe-interface.md)  
  
- [Interface IDebugStackFrameSniffer](../../winscript/reference/idebugstackframesniffer-interface.md)  
  
- [Interface IDebugStackFrameSnifferEx](../../winscript/reference/idebugstackframesnifferex-interface.md)  
  
- [Interface IDebugSyncOperation](../../winscript/reference/idebugsyncoperation-interface.md)  
  
- [Interface IDebugThreadCall](../../winscript/reference/idebugthreadcall-interface.md)  
  
- [Interface IEnumDebugApplicationNodes](../../winscript/reference/ienumdebugapplicationnodes-interface.md)  
  
- [Interface IEnumDebugCodeContexts](../../winscript/reference/ienumdebugcodecontexts-interface.md)  
  
- [Interface IEnumDebugExpressionContexts](../../winscript/reference/ienumdebugexpressioncontexts-interface.md)  
  
- [Interface IEnumDebugStackFrames](../../winscript/reference/ienumdebugstackframes-interface.md)  
  
- [Interface IEnumJsStackFrames](../../winscript/reference/ienumjsstackframes-interface.md)  
  
- [Interface IEnumRemoteDebugApplications](../../winscript/reference/ienumremotedebugapplications-interface.md)  
  
- [Interface IEnumRemoteDebugApplicationThreads](../../winscript/reference/ienumremotedebugapplicationthreads-interface.md)  
  
- [Interface IJsDebug](../../winscript/reference/ijsdebug-interface.md)  
  
- [Interface IJsDebugBreakPoint](../../winscript/reference/ijsdebugbreakpoint-interface.md)  
  
- [Interface IJsDebugDataTarget](../../winscript/reference/ijsdebugdatatarget-interface.md)  
  
- [Interface IJsDebugFrame](../../winscript/reference/ijsdebugframe-interface.md)  
  
- [Interface IJsDebugProcess](../../winscript/reference/ijsdebugprocess-interface.md)  
  
- [Interface IJsDebugProperty](../../winscript/reference/ijsdebugproperty-interface.md)  
  
- [Interface IJsDebugStackWalker](../../winscript/reference/ijsdebugstackwalker-interface.md)  
  
- [Interface IJsEnumDebugProperty](../../winscript/reference/ijsenumdebugproperty-interface.md)  
  
- [Interface IMachineDebugManager](../../winscript/reference/imachinedebugmanager-interface.md)  
  
- [Interface IMachineDebugManagerCookie](../../winscript/reference/imachinedebugmanagercookie-interface.md)  
  
- [Interface IMachineDebugManagerEvents](../../winscript/reference/imachinedebugmanagerevents-interface.md)  
  
- [Interface IProcessDebugManager](../../winscript/reference/iprocessdebugmanager-interface.md)  
  
- [Interface IProvideExpressionContexts](../../winscript/reference/iprovideexpressioncontexts-interface.md)  
  
- [Interface IRemoteDebugApplication](../../winscript/reference/iremotedebugapplication-interface.md)  
  
- [Interface IRemoteDebugApplication110](../../winscript/reference/iremotedebugapplication110-interface.md)  
  
- [Interface IRemoteDebugApplicationEx](../../winscript/reference/iremotedebugapplicationex-interface.md)  
  
- [Interface IRemoteDebugApplicationEvents](../../winscript/reference/iremotedebugapplicationevents-interface.md)  
  
- [Interface IRemoteDebugApplicationThread](../../winscript/reference/iremotedebugapplicationthread-interface.md)  
  
- [Interface IRemoteDebugApplicationThreadEx](../../winscript/reference/iremotedebugapplicationthreadex-interface.md)  
  
- [Interface ISetNextStatement](../../winscript/reference/isetnextstatement-interface.md)  
  
- [Interface ISimpleConnectionPoint](../../winscript/reference/isimpleconnectionpoint-interface.md)  
  
- [Interface IWebAppDiagnosticsSetup](../../winscript/reference/iwebappdiagnosticssetup-interface.md)  
  
- [Interface IWebAppDiagnosticsObjectInitialization](../../winscript/reference/iwebappdiagnosticsobjectinitialization-interface.md)  
  
  La section suivante répertorie les constantes, les énumérations et les structures utilisées pour le débogage :  
  
- [Constantes de débogueur de script actif, énumérations et structures](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Présentation du débogage de script actif](../../winscript/active-script-debugging-overview.md)