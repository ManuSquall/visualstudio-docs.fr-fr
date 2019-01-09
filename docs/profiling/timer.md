---
title: Timer | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 1971868e-89fa-4452-8ee7-76e4daf31b66
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 25dd87a682eb92b510dd22191769e488437e8486
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53870847"
---
# <a name="timer"></a>Minuterie
L’option **Timer** de *VSPerfCmd.exe* définit l’événement de profilage qui est échantillonné aux cycles d’horloge du processeur et change éventuellement le nombre de cycles dans un intervalle d’échantillonnage (la valeur par défaut étant 10 000 000). Sur un processeur d'1 GHz (un gigahertz), 10 000 000 de cycles d'horloge correspondent environ à 100 échantillons par seconde. Vous pouvez spécifier au minimum 50 000 cycles.  
  
 **Timer** peut être utilisé seulement quand vous utilisez la méthode de profilage par échantillonnage, et seulement sur une ligne de commande qui contient aussi l’option **Launch** ou **Attach**.  
  
 Par défaut, l'événement d'échantillonnage du profileur est défini sur les cycles d'horloge du processeur et l'intervalle d'échantillonnage est défini sur 10 000 000. Les options **Timer**, **PF**, **Sys** et **Counter** vous permettent de définir l’événement d’échantillonnage et l’intervalle d’échantillonnage. L’option **GC** collecte les données de mémoire .NET à chaque événement d’allocation et de garbage collection. Vous ne pouvez spécifier qu'une seule de ces options sur une ligne de commande.  
  
 Vous pouvez définir l’événement d’échantillonnage et l’intervalle d’échantillonnage seulement sur la première ligne de commande qui contient une option **Launch** ou **Attach**.  
  
## <a name="syntax"></a>Syntaxe  
  
```cmd  
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
  
 **PF**[**:**`Events`]  
 Définit l'événement d'échantillonnage sur les défauts de page et définit éventuellement l'intervalle d'échantillonnage sur `Events`. L'intervalle de défaut de page par défaut est 10.  
  
 **Sys**[**:**`Events`]  
 Définit l'événement d'échantillonnage sur les appels du système d'exploitation et définit éventuellement l'intervalle d'échantillonnage sur `Events`. L'intervalle Sys par défaut est 10.  
  
 **Counter**[**:**`Name,Reload,FriendlyName`]  
 Définit l'événement d'échantillonnage sur le compteur de performance d'UC spécifié par `Name` et définit l'intervalle d'échantillonnage sur `Reload`.  
  
 **GC**[**:**{**Allocation**&#124;**Lifetime**}]  
 Recueille des données de mémoire .NET. Par défaut (**Allocation**), les données sont collectées à chaque événement d’allocation mémoire. Quand le paramètre **Lifetime** est spécifié, les données sont aussi collectées à chaque événement de garbage collection.  
  
## <a name="example"></a>Exemple  
 Cet exemple illustre comment définir l'intervalle d'échantillonnage du profileur sur 1 000 000 de cycles du processeur.  
  
```cmd  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /Timer:1000000  
```  
  
## <a name="see-also"></a>Voir aussi  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profiler des applications autonomes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profiler des applications web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profiler des services](../profiling/command-line-profiling-of-services.md)