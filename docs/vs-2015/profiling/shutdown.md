---
title: Shutdown | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: a1e37500-4ad1-4670-9737-3d9a20536386
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fbbbd27cfe7d720349592050419f5c73d1843c70
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60115404"
---
# <a name="shutdown"></a>Éteindre
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L’option **Shutdown** attend que les processus en cours de profilage se terminent ou se détachent, puis désactive le profileur et ferme le fichier de données de profilage. L’option **Shutdown** doit être la dernière commande d’une exécution de profilage.  
  
 Si un paramètre de délai d’expiration n’est pas spécifié, l’option **Shutdown** attend indéfiniment. Si un paramètre de délai d’attente est spécifié, l’option retourne après le nombre de secondes spécifié sans désactiver le profileur ni fermer le fichier de données.  
  
 L’option **Shutdown** doit être la seule option spécifiée sur la ligne de commande.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
VSPerfCmd.exe /Shutdown[:Timeout]  
```  
  
#### <a name="parameters"></a>Paramètres  
`Timeout`  
- (Facultatif) Si elle est spécifiée, l’option retourne après le nombre de secondes spécifié sans désactiver le profileur ni fermer le fichier de données.  
  
## <a name="see-also"></a>Voir aussi  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilage d’applications autonomes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilage d’applications web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilage de services](../profiling/command-line-profiling-of-services.md)
