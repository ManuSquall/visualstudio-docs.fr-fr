---
title: IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp
ms.assetid: 30975973-acb1-48f4-8266-5e097a57db22
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1442297fcacb3a9464f9ea67489c91c8ab64ad78
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="iwebappdiagnosticssetupcreateobjectwithsiteatwebapp"></a>IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp
Cette méthode crée la classe dont vous passez à l’aide de l’ID `rclsid` à l’aide de la `dwClsContext`. Cela est similaire à la façon dont [IRemoteDebugApplication::CreateInstanceAtApplication](../../winscript/reference/iremotedebugapplication-createinstanceatapplication.md) fonctionne, à ceci près que dans le cas de `CreateObjectWithSiteAtWebApp` l’objet est créé de façon asynchrone sur le thread d’interface utilisateur de l’application web. L’objet spécifié par l’ID de classe doit implémenter [IWebAppDiagnosticsObjectInitialization (Interface)](../../winscript/reference/iwebappdiagnosticsobjectinitialization-interface.md). Une fois que l’objet a été créé, [IWebAppDiagnosticsObjectInitialization::Initialize](../../winscript/reference/iwebappdiagnosticsobjectinitialization-initialize.md) est appelée avec une référence à l’application de débogage PDM et `hPassToObject` paramètre de `CreateObjectWithSiteAtWebApp`. Vous pouvez utiliser cette méthode pour passer à l’application un handle à un canal anonyme que vous avez copié à l’aide de [DuplicateHandle](http://go.microsoft.com/fwlink/?LinkId=232450).  
  
> [!IMPORTANT]
>  [IWebAppDiagnosticsSetup (Interface)](../../winscript/reference/iwebappdiagnosticssetup-interface.md) est implémentée par PDM version v11.0 et supérieures. Trouvée dans activdbg100.h.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CreateObjectWithSiteAtWebApp(        [in] REFCLSID rclsid,         [in] DWORD dwClsContext,         [in] REFIID riid,         [in] DWORD_PTR hPassToObject        );  
```  
  
#### <a name="parameters"></a>Paramètres  
 `rclsid`  
 L’ID de classe de la classe à créer.  
  
 `dwClsContext`  
 Le contexte dans lequel le code sera exécuté. Dans la plupart des cas, il est CLSCTX_INPROC_SERVER.  
  
 `riid`  
 Non utilisé.  
  
 `hPassToObject`  
 Une valeur qui est passée à l’objet qui a été créé sur le thread d’interface utilisateur, si l’objet implémente [IWebAppDiagnosticsObjectInitialization (Interface)](../../winscript/reference/iwebappdiagnosticsobjectinitialization-interface.md).