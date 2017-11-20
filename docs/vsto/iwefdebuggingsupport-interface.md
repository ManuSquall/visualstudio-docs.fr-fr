---
title: Iwefdebuggingsupport, Interface | Documents Microsoft
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
ms.assetid: 0bd1c6a6-67a5-4478-b942-8b937b28f723
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7768465f46e5344b88da9006a7de2396e3b75ba6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="iwefdebuggingsupport-interface"></a>IWefDebuggingSupport, interface
  Implémentée par un environnement de débogage, tels que Visual Studio, pour faciliter le débogage des applications pour Office. L’application Office, telles que Word ou Excel, obtient cette interface à partir de Visual Studio, puis appelle les méthodes sur l’interface à certains points durant la session de débogage.  
  
## <a name="syntax"></a>Syntaxe  
  
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
  
## <a name="methods"></a>Méthodes  
 Le tableau suivant répertorie les méthodes que l’iwefdebuggingsupport, interface définit.  
  
|Nom|Description|  
|----------|-----------------|  
|[GetAutoInsertExtensions, méthode](../vsto/getautoinsertextensions-method.md)|Obtient des informations sur les applications pour Office qui doivent être insérés automatiquement pendant le débogage.|  
|[SetWefProcessId, méthode](../vsto/setwefprocessid-method.md)|Fournit l’identificateur de processus qui s’exécutera le contenu Web Extensions Framework (WEF).|  
  
  