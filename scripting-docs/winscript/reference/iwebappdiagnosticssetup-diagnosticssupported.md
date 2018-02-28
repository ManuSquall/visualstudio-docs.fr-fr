---
title: IWebAppDiagnosticsSetup::DiagnosticsSupported | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IWebAppDiagnosticsSetup::DiagnosticsSupported
ms.assetid: 5bbcd0d0-1460-4cf7-bbb1-f4f4a04f739a
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5706d868f0096d486629c18c3d700349af92cc92
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="iwebappdiagnosticssetupdiagnosticssupported"></a>IWebAppDiagnosticsSetup::DiagnosticsSupported
Détermine si les tests de diagnostic sont pris en charge sur cette application. Si [SetSite](http://go.microsoft.com/fwlink/?LinkId=232439) a été appelée sur l’objet qui implémente cette interface avec une valeur non NULL, [DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md) retourne `true`. Si non, il retourne `false` et appelle à [IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md) échouent.  
  
> [!IMPORTANT]
>  [IWebAppDiagnosticsSetup (Interface)](../../winscript/reference/iwebappdiagnosticssetup-interface.md) est implémentée par PDM version v11.0 et supérieures. Trouvé dans activdbg100.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT DiagnosticsSupported(        [out, retval] VARIANT_BOOL* pRetVal        );  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pRetVal`  
 Si [SetSite](http://go.microsoft.com/fwlink/?LinkId=232439) a été appelée sur l’objet qui implémente cette interface avec une valeur non NULL, [DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md) retourne `true`. Si non, il retourne `false`et les appels à [IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md) échouent.