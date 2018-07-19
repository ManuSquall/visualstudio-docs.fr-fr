---
title: Iwefdebuggingsupport, interface
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 351fb69b99393a10518168f4f9b01efe1f9efaa7
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/01/2018
ms.locfileid: "34572671"
---
# <a name="iwefdebuggingsupport-interface"></a>Iwefdebuggingsupport, interface
  Implémentée par un environnement de débogage, tels que Visual Studio, pour faciliter le débogage des applications pour Office. L’application Office, telles que Word ou Excel, obtient cette interface à partir de Visual Studio, puis appelle les méthodes sur l’interface à certains points durant la session de débogage.  
  
## <a name="syntax"></a>Syntaxe  
  
```csharp 
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
|[Getautoinsertextensions, méthode](../vsto/getautoinsertextensions-method.md)|Obtient des informations sur les applications pour Office qui doivent être insérés automatiquement pendant le débogage.|  
|[Setwefprocessid, méthode](../vsto/setwefprocessid-method.md)|Fournit l’identificateur de processus qui s’exécutera le contenu Web Extensions Framework (WEF).|  
  
  