---
title: Console | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: e825ba66-1383-46ad-8712-396bc9c14036
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e947fb28c92323f0d4d66c697c272699fc63450e
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54771054"
---
# <a name="console"></a>Console
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L’option **Console** de VSPerfCmd.exe démarre l’application spécifiée dans une nouvelle fenêtre d’invite de commandes. L’option **Console** peut être utilisée seulement avec l’option **Launch** de VSPerfCmd. Si l’application n’est pas une application en ligne de commande, **Console** n’a aucun effet.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
VSPerfCmd.exe /Launch:AppName /Console  
```  
  
#### <a name="parameters"></a>Paramètres  
 Aucun.  
  
## <a name="required-options"></a>Options obligatoires  
 Vous pouvez spécifier **Console** seulement sur une ligne de commande qui contient aussi l’option **Launch**.  
  
 **Launch :** `AppName`  
 Démarre le profileur et l'application spécifiée par `AppName`.  
  
## <a name="see-also"></a>Voir aussi  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilage d’applications autonomes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilage d’applications web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilage de services](../profiling/command-line-profiling-of-services.md)
