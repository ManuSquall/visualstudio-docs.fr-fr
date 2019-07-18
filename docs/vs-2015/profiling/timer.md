---
title: Timer | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 1971868e-89fa-4452-8ee7-76e4daf31b66
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1e5f6c6db903b3ecced2ac3ebc4aaa0a3e60910c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68145501"
---
# <a name="timer"></a>Minuterie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L’option **Timer** de VSPerfCmd.exe définit l’événement de profilage qui est échantillonné aux cycles d’horloge du processeur et change éventuellement le nombre de cycles dans un intervalle d’échantillonnage (la valeur par défaut est 10 000 000). Sur un processeur d'1 GHz (un gigahertz), 10 000 000 de cycles d'horloge correspondent environ à 100 échantillons par seconde. Vous pouvez spécifier au minimum 50 000 cycles.  
  
 **Timer** peut être utilisé seulement quand vous utilisez la méthode de profilage par échantillonnage, et seulement sur une ligne de commande qui contient aussi l’option **Launch** ou **Attach**.  
  
 Par défaut, l'événement d'échantillonnage du profileur est défini sur les cycles d'horloge du processeur et l'intervalle d'échantillonnage est défini sur 10 000 000. Les options **Timer**, **PF**, **Sys** et **Counter** vous permettent de définir l’événement d’échantillonnage et l’intervalle d’échantillonnage. L’option **GC** collecte les données de mémoire .NET à chaque événement d’allocation et de garbage collection. Vous ne pouvez spécifier qu'une seule de ces options sur une ligne de commande.  
  
 Vous pouvez définir l’événement d’échantillonnage et l’intervalle d’échantillonnage seulement sur la première ligne de commande qui contient une option **Launch** ou **Attach**.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
VSPerfCmd.exe {/Launch:AppName|/Attach:PID} /Timer[:Cycles] [Options]  
```  
  
#### <a name="parameters"></a>Paramètres  
 `Cycles`  
 Valeur entière qui spécifie le nombre de cycles d'horloge du processeur dans un intervalle d'échantillonnage. Si `Cycles` n'est pas spécifié, l'intervalle prend la valeur 10 000 000. Spécifiez la valeur sans espace.  
  
## <a name="required-options"></a>Options obligatoires  
 Vous pouvez spécifier **Timer** seulement sur une ligne de commande qui contient une des options suivantes.  
  
 **Launch :** `AppName`  
 Démarre le profileur et l'application spécifiée par `AppName`.  
  
 **Attach:** `PID`  
 Attache le profileur au processus spécifié par l'ID de processus (`PID`).  
  
## <a name="invalid-options"></a>Options non valides  
 Vous ne pouvez pas spécifier les options suivantes sur la même ligne de commande que **Timer**.  
  
 **PF**[ **:** `Events`]  
 Définit l'événement d'échantillonnage sur les défauts de page et définit éventuellement l'intervalle d'échantillonnage sur `Events`. L'intervalle de défaut de page par défaut est 10.  
  
 **Sys**[ **:** `Events`]  
 Définit l'événement d'échantillonnage sur les appels du système d'exploitation et définit éventuellement l'intervalle d'échantillonnage sur `Events`. L'intervalle Sys par défaut est 10.  
  
 **Counter**[ **:** `Name,Reload,FriendlyName`]  
 Définit l'événement d'échantillonnage sur le compteur de performance d'UC spécifié par `Name` et définit l'intervalle d'échantillonnage sur `Reload`.  
  
 **GC**[ **:** {**Allocation**&#124;**Lifetime**}]  
 Recueille des données de mémoire .NET. Par défaut (**Allocation**), les données sont collectées à chaque événement d’allocation mémoire. Quand le paramètre **Lifetime** est spécifié, les données sont aussi collectées à chaque événement de garbage collection.  
  
## <a name="example"></a>Exemples  
 Cet exemple illustre comment définir l'intervalle d'échantillonnage du profileur sur 1 000 000 de cycles du processeur.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /Timer:1000000  
```  
  
## <a name="see-also"></a>Voir aussi  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilage d’applications autonomes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilage d’applications web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilage de services](../profiling/command-line-profiling-of-services.md)
