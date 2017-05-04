---
title: "IWefDebuggingSupport, interface | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
ms.assetid: 0bd1c6a6-67a5-4478-b942-8b937b28f723
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# IWefDebuggingSupport, interface
  Implémentée par un environnement de débogage, tel que Visual Studio, pour faciliter le débogage des applications pour Office.  L'application Office, telles que Word ou Excel, reçoit cette interface de Visual Studio puis appeler des méthodes sur l'interface à certains points pendant la session de débogage.  
  
## Syntaxe  
  
```  
[  
    uuid(ccaf1a90-ce1c-4199-9cd6-b40c5c57a671),  
    oleautomation  
]  
interface IWefDebuggingSupport : IUnknown  
{  
    HRESULT SetWefProcessId(  
        [in] DWORD dwProcessId);  
    HRESULT GetAutoInsertExtensions(  
        [out, retval] SAFEARRAY(BSTR)* psaExtensionNames);  
}  
```  
  
## Méthodes  
 Le tableau suivant répertorie les méthodes que l'interface d' IWefDebuggingSupport définit.  
  
|Nom|Description|  
|---------|-----------------|  
|[GetAutoInsertExtensions, méthode](../vsto/getautoinsertextensions-method.md)|Obtient des informations sur les applications pour Office qui doivent être insérées automatiquement pendant le débogage.|  
|[SetWefProcessId, méthode](../vsto/setwefprocessid-method.md)|Fournit l'identificateur de processus qui exécute le contenu de l'infrastructure \(WEF\) d'extensions de site Web.|  
  
  