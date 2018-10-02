---
title: CrossSession | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b9fcb9c3-7903-478c-9b7c-dbd94092fcba
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4c4306f89b41639ba70e581ed6b3b4ce70089c01
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2018
ms.locfileid: "47590798"
---
# <a name="crosssession"></a>CrossSession
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [CrossSession](https://docs.microsoft.com/visualstudio/profiling/crosssession).  
  
L’option **CrossSession** de VSPerfCmd.exe permet au profileur de collecter des données à partir de n’importe quelle session de console. L’option **CrossSession** doit être utilisée avec l’option **Start**.  
  
 Vous pouvez utiliser l’abréviation **CS** à la place de **CrossSession**.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
VSPerfCmd.exe /Start:Method /CrossSession [Options]  
```  
  
#### <a name="parameters"></a>Paramètres  
 Aucun.  
  
## <a name="valid-options"></a>Options valides  
 Pour activer le profilage dans une autre session, l’option **CrossSession** doit être spécifiée avec l’option **Start**. L’option **CrossSession** doit également être spécifiée dans toutes les commandes **VSPerfCmd Attach** et **Detach** suivantes.  
  
 **Start:** `Method`  
 L’option **Start** initialise le profileur avec la méthode de profilage spécifiée.  
  
 **Attach:** _PID_[**,**_PID_]  
 Démarre le profilage des processus spécifiés.  
  
 **Detach**[**:**_PID_[,_PID_]]  
 Arrête le profilage des processus spécifiés.  
  
## <a name="example"></a>Exemple  
 Dans cet exemple, l’option **CrossSession** est utilisée pour attacher à une application qui a été démarrée dans une autre session de console.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /CrossSession  
VSPerfCmd.exe /Attach:12345 /CS  
```  
  
## <a name="see-also"></a>Voir aussi  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilage d’applications autonomes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilage d’applications web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilage de services](../profiling/command-line-profiling-of-services.md)



