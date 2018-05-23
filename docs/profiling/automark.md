---
title: AutoMark | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: c4de965e-0364-4f78-9936-1f509e85df74
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 922f6f40389277bed7da7b960fae341d7afe70da
ms.sourcegitcommit: eefffa7ebe339d1297cdc12f51a813e7849d7e95
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2018
---
# <a name="automark"></a>AutoMark
L’option **AutoMark** spécifie le nombre de millisecondes écoulées entre les collectes des événements des compteurs de performances logiciels Windows. Les compteurs de performances Windows sont spécifiés dans l’option **WinCounter**.  
  
 Vous ne pouvez spécifier qu’une seule option **AutoMark** sur la ligne de commande. Notez que l’intervalle d’échantillonnage de **WinCounter** spécifié par **AutoMark** est indépendant de l’intervalle d’échantillonnage principal.  
  
## <a name="syntax"></a>Syntaxe  
  
```cmd  
VSPerfCmd.exe /Start:Method /WinCounter:Path /AutoMark:Milliseconds  
```  
  
#### <a name="parameters"></a>Paramètres  
 `Milliseconds`  
 Spécifie le nombre de millisecondes écoulées entre les collectes des événements des compteurs de performances Windows.  
  
## <a name="required-options"></a>Options obligatoires  
 **WinCounter:** `Path`  
 Spécifie le compteur de performances Windows à collecter. Quand vous utilisez la méthode d’instrumentation, vous pouvez spécifier plusieurs compteurs Windows. Quand vous utilisez la méthode d’échantillonnage, vous ne pouvez spécifier qu’un seul compteur Windows. L’option **WinCounter** doit être spécifiée dans une ligne de commande qui contient l’option **Start**.  
  
## <a name="example"></a>Exemple  
 Dans cet exemple, un intervalle d’échantillonnage de 1 000 millisecondes est défini pour deux compteurs de performances Windows.  
  
```cmd  
VSPerfCmd.exe /Start:Trace /Output:TestApp.exe.vsp /WinCounter:"\Process(*)\% Processor Time" /WinCounter:"\ASP.NET\Pages/sec" /AutoMark:1000  
VSPerfCmd.exe /Launch:TestApp.exe  
```  
  
## <a name="see-also"></a>Voir aussi  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilage d’applications autonomes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilage d’applications web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilage de services](../profiling/command-line-profiling-of-services.md)