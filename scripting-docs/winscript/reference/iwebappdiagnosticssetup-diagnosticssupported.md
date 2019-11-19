---
title: IWebAppDiagnosticsSetup ::D iagnosticsSupported | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: dd27e7c8759054fa2d7d67858d8d006fa9c9a152
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72984585"
---
# <a name="iwebappdiagnosticssetupdiagnosticssupported"></a>IWebAppDiagnosticsSetup::DiagnosticsSupported
Détermine si les diagnostics sont pris en charge sur cette application. Si [SetSite](/windows/win32/api/ocidl/nf-ocidl-iobjectwithsite-setsite) a été appelé sur l’objet implémentant cette interface avec une valeur non null, [DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md) retourne `true`. Si ce n’est pas le cas, elle retourne `false` et les appels à [IWebAppDiagnosticsSetup :: CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md) échouent.  
  
> [!IMPORTANT]
> L' [interface IWebAppDiagnosticsSetup](../../winscript/reference/iwebappdiagnosticssetup-interface.md) est implémentée par PDM v 11.0 et ultérieur. Trouvé dans activdbg100.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT DiagnosticsSupported(        [out, retval] VARIANT_BOOL* pRetVal        );  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pRetVal`  
 Si [SetSite](/windows/win32/api/ocidl/nf-ocidl-iobjectwithsite-setsite) a été appelé sur l’objet implémentant cette interface avec une valeur non null, [DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md) retourne `true`. Si ce n’est pas le cas, elle retourne `false`et les appels à [IWebAppDiagnosticsSetup :: CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md) échouent.