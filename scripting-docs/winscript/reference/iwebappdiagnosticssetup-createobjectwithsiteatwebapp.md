---
title: 'IWebAppDiagnosticsSetup :: CreateObjectWithSiteAtWebApp | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp
ms.assetid: 30975973-acb1-48f4-8266-5e097a57db22
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 253b995c200566868ac9ccc06b259e0a152e1676
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72984608"
---
# <a name="iwebappdiagnosticssetupcreateobjectwithsiteatwebapp"></a>IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp
Cette méthode co-crée la classe dont vous transmettez l’ID avec `rclsid` à l’aide de l' `dwClsContext`. Cela est similaire à la façon dont [IRemoteDebugApplication :: CreateInstanceAtApplication](../../winscript/reference/iremotedebugapplication-createinstanceatapplication.md) fonctionne, sauf que dans le cas de `CreateObjectWithSiteAtWebApp` l’objet est créé de façon asynchrone sur le thread d’interface utilisateur de l’application Web. L’objet spécifié par l’ID de classe doit implémenter l' [interface IWebAppDiagnosticsObjectInitialization](../../winscript/reference/iwebappdiagnosticsobjectinitialization-interface.md). Une fois l’objet créé, [IWebAppDiagnosticsObjectInitialization :: Initialize](../../winscript/reference/iwebappdiagnosticsobjectinitialization-initialize.md) est appelé avec une référence à l’application de débogage PDM et au paramètre `hPassToObject` de `CreateObjectWithSiteAtWebApp`. Vous pouvez utiliser cette méthode pour transmettre à l’application un handle vers un canal anonyme que vous avez copié à l’aide de [DuplicateHandle](/windows/win32/api/handleapi/nf-handleapi-duplicatehandle).  
  
> [!IMPORTANT]
> L' [interface IWebAppDiagnosticsSetup](../../winscript/reference/iwebappdiagnosticssetup-interface.md) est implémentée par PDM v 11.0 et ultérieur. Trouvée dans activdbg100.h.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CreateObjectWithSiteAtWebApp(        [in] REFCLSID rclsid,         [in] DWORD dwClsContext,         [in] REFIID riid,         [in] DWORD_PTR hPassToObject        );  
```  
  
#### <a name="parameters"></a>Paramètres  
 `rclsid`  
 ID de classe de la classe à créer.  
  
 `dwClsContext`  
 Contexte dans lequel le code s’exécutera. Dans la plupart des cas, il s’agit de CLSCTX_INPROC_SERVER.  
  
 `riid`  
 Non utilisé.  
  
 `hPassToObject`  
 Valeur qui est passée à l’objet une fois qu’il a été créé sur le thread d’interface utilisateur, si l’objet implémente l' [interface IWebAppDiagnosticsObjectInitialization](../../winscript/reference/iwebappdiagnosticsobjectinitialization-interface.md).