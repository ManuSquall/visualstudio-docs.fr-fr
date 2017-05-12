---
title: "IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp"
ms.assetid: 30975973-acb1-48f4-8266-5e097a57db22
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp
Cette méthode Co\- crée la classe dont l'ID vous passez dans avec `rclsid` à l'aide de `dwClsContext`.  C'est similaire à la façon dont [IRemoteDebugApplication::CreateInstanceAtApplication](../../winscript/reference/iremotedebugapplication-createinstanceatapplication.md) s'exécute, sauf que dans le cas de `CreateObjectWithSiteAtWebApp` l'objet est créé de façon asynchrone sur le thread d'interface utilisateur de l'application Web.  L'objet spécifié par l'ID de classe doit implémenter [IWebAppDiagnosticsObjectInitialization \(interface\)](../../winscript/reference/iwebappdiagnosticsobjectinitialization-interface.md).  Une fois que l'objet créé, [IWebAppDiagnosticsObjectInitialization::Initialize](../../winscript/reference/iwebappdiagnosticsobjectinitialization-initialize.md) est appelé avec une référence au PDM débogage de l'application et le paramètre d' `hPassToObject` d' `CreateObjectWithSiteAtWebApp`.  Vous pouvez utiliser cette méthode pour passer à l'application un handle vers un canal anonyme avec [DuplicateHandle](http://go.microsoft.com/fwlink/?LinkId=232450)lequel vous avez copié.  
  
> [!IMPORTANT]
>  [IWebAppDiagnosticsSetup \(interface\)](../../winscript/reference/iwebappdiagnosticssetup-interface.md) est implémenté par PDM v11.0 et supérieur.  Trouvé dans activdbg100.h.  
  
## Syntaxe  
  
```cpp  
HRESULT CreateObjectWithSiteAtWebApp(  
        [in] REFCLSID rclsid,   
        [in] DWORD dwClsContext,   
        [in] REFIID riid,   
        [in] DWORD_PTR hPassToObject  
        );  
  
```  
  
#### Paramètres  
 `rclsid`  
 L'ID de classe de la classe à créer.  
  
 `dwClsContext`  
 Le contexte dans lequel le code s'exécute.  Dans la plupart des cas c'est CLSCTX\_INPROC\_SERVER.  
  
 `riid`  
 Non utilisé.  
  
 `hPassToObject`  
 Une valeur qui est passée à l'objet une fois qu'il sera créée sur le thread d'interface utilisateur, si l'objet implémente [IWebAppDiagnosticsObjectInitialization \(interface\)](../../winscript/reference/iwebappdiagnosticsobjectinitialization-interface.md).