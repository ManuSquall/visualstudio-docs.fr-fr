---
title: CrossSession | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: b9fcb9c3-7903-478c-9b7c-dbd94092fcba
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c0dc63350b3acf89b1b226e5ebae45fdf8868fb3
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34750088"
---
# <a name="crosssession"></a>CrossSession
L’option *VSPerfCmd.exe* **CrossSession** permet au profileur de collecter des données de n’importe quelle session console. L’option **CrossSession** doit être utilisée avec l’option **Start**.  
  
 Vous pouvez utiliser l’abréviation **CS** à la place de **CrossSession**.  
  
## <a name="syntax"></a>Syntaxe  
  
```cmd  
VSPerfCmd.exe /Start:Method /CrossSession [Options]  
```  
  
#### <a name="parameters"></a>Paramètres  
 Aucun.  
  
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
  
```cmd  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /CrossSession  
VSPerfCmd.exe /Attach:12345 /CS  
```  
  
## <a name="see-also"></a>Voir aussi  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profiler des applications autonomes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profiler des applications web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profiler des services](../profiling/command-line-profiling-of-services.md)