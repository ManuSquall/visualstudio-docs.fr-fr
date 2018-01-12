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
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 7b132c51e12d553bcd6e722e87c8aeee96be5e5c
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2018
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
  
|Name|Description|  
|----------|-----------------|  
|[GetAutoInsertExtensions, méthode](../vsto/getautoinsertextensions-method.md)|Obtient des informations sur les applications pour Office qui doivent être insérés automatiquement pendant le débogage.|  
|[SetWefProcessId, méthode](../vsto/setwefprocessid-method.md)|Fournit l’identificateur de processus qui s’exécutera le contenu Web Extensions Framework (WEF).|  
  
  