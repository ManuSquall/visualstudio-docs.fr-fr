---
title: "Sys (VSPerfCmd) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 294a6f9e-b49f-4c83-b322-5ac5411b66fb
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Sys (VSPerfCmd)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'option **Sys** de VSPerfCmd.exe définit l'événement de profilage qui est échantillonné aux événements d'appel système \(appels de fonction de l'application profilée au système d'exploitation\), et éventuellement modifie le nombre d'appels système dans un intervalle d'échantillonnage à partir de la valeur par défaut, 10.  
  
 L'option **Sys** peut être utilisée uniquement dans une ligne de commande qui contient également l'option **Launch** ou **Attach**.  
  
 Par défaut, l'événement d'échantillonnage du profileur a pour valeur les cycles d'horloge du processeur et l'intervalle d'échantillonnage a la valeur 10 000 000.  Les options **Timer**, **PF**, **Sys** et **Counter** vous permettent de définir l'événement d'échantillonnage et l'intervalle d'échantillonnage.  L'option **GC** collecte les données de mémoire .NET à chaque événement d'allocation et de garbage collection.  Une seule de ces options peut être spécifiée sur une ligne de commande.  
  
 L'événement d'échantillonnage et l'intervalle d'échantillonnage peuvent être définis uniquement dans la première ligne de commande qui contient une option **Launch** ou **Attach**.  
  
## Syntaxe  
  
```  
VSPerfCmd.exe {/Launch:AppName|Attach:PID} /Sys[:Events] [Options]  
```  
  
#### Paramètres  
 `Events`  
 Valeur entière qui spécifie le nombre d'événements d'appel système dans un intervalle d'échantillonnage.  Si `Events` n'est pas spécifié, l'intervalle a la valeur 10.  
  
## Options requises  
 L'option **Sys** nécessite l'une des options suivantes.  
  
 **Launch:** `AppName`  
 Démarre le profileur et l'application spécifiés par `AppName`.  
  
 **Attach:** `PID`  
 Attache le profileur au processus spécifié par le `PID`.  
  
## Options non valides  
 Les options suivantes ne peuvent pas être spécifiées sur la même ligne de commande que **Sys**.  
  
 **PF**\[**:**`Events`\]  
 Affecte à l'événement d'échantillonnage les défauts de page et éventuellement affecte à l'intervalle d'échantillonnage la valeur `Events`.  L'intervalle PF par défaut est 10.  
  
 **Timer**\[**:**`Cycles`\]  
 Affecte à l'événement d'échantillonnage les cycles d'horloge du processeur et affecte éventuellement à l'intervalle d'échantillonnage la valeur `Cycles`.  L'intervalle de minuterie par défaut est 10 000 000.  
  
 **Counter:** `Name`\[`,Reload`\[`,FriendlyName`\]\]  
 Affecte à l'événement d'échantillonnage le compteur de performance de l'UC spécifié par `Name` et affecte `Reload` à l'intervalle d'échantillonnage.  
  
 **GC**\[**:**{**Allocation**&#124;**Lifetime**}\]  
 Collecte les données de la mémoire .NET.  Par défaut \(**Allocation**\), les données sont collectées à chaque événement d'allocation de mémoire.  Lorsque le paramètre **Lifetime** est spécifié, des données sont également collectées à chaque événement de garbage collection.  
  
## Exemple  
 Cet exemple montre comment définir l'événement d'échantillonnage du profileur sur les appels système et comment affecter 20 appels par exemple à l'intervalle d'échantillonnage.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /Sys:20  
```  
  
## Voir aussi  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilage d’applications autonomes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilage d’applications web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilage de services](../profiling/command-line-profiling-of-services.md)