---
title: IWebAppDiagnosticsSetup::DiagnosticsSupported | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IWebAppDiagnosticsSetup::DiagnosticsSupported
ms.assetid: 5bbcd0d0-1460-4cf7-bbb1-f4f4a04f739a
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: df9296ac251d93105229fc0af365f6797a413f2b
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54349684"
---
# <a name="iwebappdiagnosticssetupdiagnosticssupported"></a>IWebAppDiagnosticsSetup::DiagnosticsSupported
Détermine si les diagnostics sont pris en charge sur cette application. Si [SetSite](http://go.microsoft.com/fwlink/?LinkId=232439) a été appelée sur l’objet qui implémente cette interface avec une valeur non NULL, [DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md) retourne `true`. Sinon, elle retourne `false` et d’appels vers [IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md) échouent.  
  
> [!IMPORTANT]
>  [IWebAppDiagnosticsSetup Interface](../../winscript/reference/iwebappdiagnosticssetup-interface.md) est implémentée par PDM version v11.0 et supérieures. Trouvé dans activdbg100.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT DiagnosticsSupported(        [out, retval] VARIANT_BOOL* pRetVal        );  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pRetVal`  
 Si [SetSite](http://go.microsoft.com/fwlink/?LinkId=232439) a été appelée sur l’objet qui implémente cette interface avec une valeur non NULL, [DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md) retourne `true`. Sinon, elle retourne `false`et les appels à [IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md) échouent.