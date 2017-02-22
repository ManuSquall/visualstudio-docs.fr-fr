---
title: "Lancer | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f81bde5c-3394-4b79-a315-c2f6491689b3
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Lancer
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'option **Launch** démarre le profileur à l'aide de la méthode d'échantillonnage et démarre également l'application spécifiée.  
  
 Pour utiliser l'option **Launch**, vous devez spécifier la méthode **Sample** dans l'option **Start**.  
  
## Syntaxe  
  
```  
VSPerfCmd.exe /Launch:AppName [Options]  
```  
  
#### Paramètres  
 `AppName`  
 Nom de l'application à lancer.  Les chemins d'accès complets et partiels du répertoire actif sont pris en charge.  
  
## Options valides  
 Les options VSPerfCmd suivantes peuvent être combinées avec l'option **Launch** sur une même ligne de commande.  
  
 **Start:** `Method`  
 Initialise la session de profileur en ligne de commande et définit la méthode de profilage spécifiée.  
  
 **GlobalOn**et**GlobalOff**  
 Reprend \(**GlobalOn**\) ou interrompt \(**GlobalOff**\) le profilage, mais ne met pas fin à la session de profilage.  
  
 **ProcessOn:** `PID` et **ProcessOff** :`PID`  
 Reprend \(**ProcessOn**\) ou interrompt \(**ProcessOff**\) le profilage pour le processus spécifié.  
  
 **TargetCLR**  
 Spécifie la version du .NET Framework Common Language Runtime \(CLR\) à profiler lorsque plusieurs versions sont chargées dans une session de profilage.  Par défaut, la première version chargée est profilée.  
  
## Options exclusives  
 Les options suivantes peuvent uniquement être utilisées avec l'option **Launch**.  
  
 **Console**  
 Lance l'application en ligne de commande spécifiée dans une nouvelle fenêtre.  
  
 **Args:** `ArgList`  
 Spécifie la liste d'arguments à passer à l'application.  
  
 **LineOff**  
 Désactive la collecte des données de profilage au niveau ligne.  
  
## Options d'échantillonnage  
 L'une des options d'intervalle d'échantillonnage suivantes peut être spécifiée sur la ligne de commande **Launch**.  L'intervalle d'échantillonnage par défaut est de 10 000 000 cycles d'horloge du processeur.  
  
 **Timer**\[**:**`Cycles`\]**PF**\[**:**`Events`\]**Sys**\[**:**`Events`\]**Counter**\[**:**`Name`,`Reload`,`FriendlyName`\]**GC**\[:**allocation**&#124;**lifetime**\]  
 Spécifie le nombre et le type d'intervalle d'échantillonnage.  
  
-   **Timer**\- Échantillonne tous les cycles d'horloge processeur non interrompus `Cycles`.  Si `Cycles` n'est pas spécifié, 10 000 000 cycles sont utilisés.  
  
-   **PF** \- Échantillonne chaque défaut de page `Events`.  Si `Events` n'est pas spécifié, 10 défauts de page.  
  
-   **Sys** \- Échantillonne chaque appel `Events` au système d'exploitation.  Si `Events` n'est pas spécifié, 10 appels système sont utilisés.  
  
-   **Counter** \- Échantillonne le nombre `Reload` du compteur de performance de l'UC spécifié par `Name`.  `FriendlyName` peut éventuellement spécifier une chaîne à utiliser comme en\-tête de colonne dans les rapports du profileur.  
  
-   **GC** \- Collecte les données de mémoire .NET.  Par défaut \(**allocation**\), les données sont collectées à chaque événement d'allocation de mémoire.  Lorsque le paramètre **lifetime** est spécifié, des données sont également collectées à chaque événement de garbage collection.  
  
## Exemple  
 Cet exemple présente l'utilisation de **Launch** pour démarrer une application.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe  
```  
  
## Voir aussi  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilage d’applications autonomes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilage d’applications web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilage de services](../profiling/command-line-profiling-of-services.md)