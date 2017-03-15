---
title: "PF | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cdc0a094-a986-4629-bd1c-dd5fdca323dc
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# PF
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'option VSPerfCmd.exe **PF** affecte à l'événement de profilage échantillonné la valeur correspondant au nombre de défauts de page, et modifie éventuellement le nombre de défauts de page dans un intervalle d'échantillonnage sur une valeur autre que la valeur par défaut de 10.  
  
> [!NOTE]
>  PF ne peut pas être utilisé sur les systèmes 64 bits.  
  
 **Remarque**  
 **PF** n'est pas pris en charge sur les ordinateurs 64 bits. **PF** peut uniquement être utilisé dans une ligne de commande qui contient également l'option **Launch** ou **Attach**.  
  
 Par défaut, la valeur de l'événement d'échantillonnage correspond aux cycles d'horloge du processeur non interrompus et l'intervalle d'échantillonnage a la valeur 10 000 000.  Les options **Timer**, **PF**, **Sys** et **Counter** vous permettent de définir l'événement d'échantillonnage et l'intervalle d'échantillonnage.  L'option **GC** collecte les données de mémoire .NET à chaque événement d'allocation et de garbage collection.  Une seule de ces options peut être spécifiée sur une ligne de commande.  
  
 L'événement d'échantillonnage et l'intervalle d'échantillonnage peuvent être définis uniquement dans la première ligne de commande qui contient une option **Launch** ou **Attach**.  
  
## Syntaxe  
  
```  
VSPerfCmd.exe {/Launch:AppName|/Attach:PID} /PF[:Events] [Options]  
```  
  
#### Paramètres  
 `Events`  
 Valeur entière qui spécifie le nombre d'événements de défaut de page dans un intervalle d'échantillonnage.  Si `Events` n'est pas spécifié, l'intervalle a la valeur 10.  
  
## Options requises  
 L'option **PF** peut être spécifiée uniquement sur une ligne de commande qui contient l'une des options suivantes.  
  
 **Launch:** `AppName`  
 Démarre le profileur et l'application spécifiée par AppName.  
  
 **Attach:** `PID`  
 Attache le profileur au processus spécifié par AppName.  
  
## Options non valides  
 Les options suivantes ne peuvent pas être spécifiées sur la même ligne de commande que **PF**.  
  
 **Timer**\[**:**`Cycles`\]  
 Affecte à l'événement d'échantillonnage les cycles d'horloge du processeur et affecte éventuellement à l'intervalle d'échantillonnage la valeur `Cycles`.  L'intervalle de minuterie par défaut est 10 000 000.  
  
 **Sys**\[**:**`Events`\]  
 Affecte à l'événement d'échantillonnage la valeur correspondant aux appels de l'application profilée au noyau de système d'exploitation \(syscalls\) et affecte éventuellement à l'intervalle d'échantillonnage la valeur `Events`.  L'intervalle SYS par défaut est 10.  
  
 **Counter:** `Name`\[`,Reload`\[`,FriendlyName`\]\]  
 Affecte à l'événement d'échantillonnage le compteur de performance de l'UC spécifié par `Name` et affecte `Reload` à l'intervalle d'échantillonnage.  
  
 **GC**\[**:**{**Allocation**&#124;**Lifetime**}\]  
 Collecte les données de la mémoire .NET.  Par défaut \(**Allocation**\), les données sont collectées à chaque événement d'allocation de mémoire.  Lorsque le paramètre **Lifetime** est spécifié, des données sont également collectées à chaque événement de garbage collection.  
  
## Exemple  
 Cet exemple montre comment affecter à l'événement d'échantillonnage de profilage la valeur correspondant aux défauts de page et comment affecter à l'intervalle d'échantillonnage la valeur 20 défauts de page.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /PF:20  
```  
  
## Voir aussi  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilage d’applications autonomes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilage d’applications web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilage de services](../profiling/command-line-profiling-of-services.md)