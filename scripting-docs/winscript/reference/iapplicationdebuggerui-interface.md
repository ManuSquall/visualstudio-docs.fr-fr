---
title: "IApplicationDebuggerUI, interface | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IApplicationDebuggerUI (interface)"
ms.assetid: b8828817-ca24-4012-802c-7dcaeea65dc8
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IApplicationDebuggerUI, interface
Implémentée par l'environnement de développement intégré \(IDE\) de débogueur \(en plus de `IApplicationDebugger`\) pour donner à un composant externe plus de contrôle de l'interface utilisateur \(UI\) du débogueur.  
  
 Outre les méthodes héritées de `IUnknown`, l'interface `IApplicationDebuggerUI` expose les méthodes suivantes.  
  
## Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|-------------|-----------------|  
|[IApplicationDebuggerUI::BringDocumentToTop](../../winscript/reference/iapplicationdebuggerui-bringdocumenttotop.md)|Apporte la fenêtre contenant le spécifié de débogage le document vers le haut dans l'interface utilisateur du débogueur.|  
|[IApplicationDebuggerUI::BringDocumentContextToTop](../../winscript/reference/iapplicationdebuggerui-bringdocumentcontexttotop.md)|Apporte la fenêtre contenant le contexte de document donné en haut de l'interface utilisateur du débogueur et fait défiler la fenêtre au contexte.|