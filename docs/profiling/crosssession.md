---
title: CrossSession | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b9fcb9c3-7903-478c-9b7c-dbd94092fcba
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 196107019a43f8f76beeb55cde6a56034375b9d9
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="crosssession"></a>CrossSession
L’option **CrossSession** de VSPerfCmd.exe permet au profileur de collecter des données à partir de n’importe quelle session de console. L’option **CrossSession** doit être utilisée avec l’option **Start**.  
  
 Vous pouvez utiliser l’abréviation **CS** à la place de **CrossSession**.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
VSPerfCmd.exe /Start:Method /CrossSession [Options]  
```  
  
#### <a name="parameters"></a>Paramètres  
 None  
  
## <a name="valid-options"></a>Options valides  
 Pour activer le profilage dans une autre session, l’option **CrossSession** doit être spécifiée avec l’option **Start**. L’option **CrossSession** doit également être spécifiée dans toutes les commandes **VSPerfCmd Attach** et **Detach** suivantes.  
  
 **Start:** `Method`  
 L’option **Start** initialise le profileur avec la méthode de profilage spécifiée.  
  
 **Attach:** *PID*[**,***PID*]  
 Démarre le profilage des processus spécifiés.  
  
 **Detach**[**:***PID*[,*PID*]]  
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