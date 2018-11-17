---
title: Shutdown | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a1e37500-4ad1-4670-9737-3d9a20536386
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9b4ed8bc95f3d842f12a5bd0002456f71875fdb7
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51729204"
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
 -   (Facultatif) Si elle est spécifiée, l’option retourne après le nombre de secondes spécifié sans désactiver le profileur ni fermer le fichier de données.  
  
## <a name="see-also"></a>Voir aussi  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilage d’applications autonomes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilage d’applications web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilage de services](../profiling/command-line-profiling-of-services.md)



