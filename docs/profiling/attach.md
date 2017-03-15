---
title: "Attach | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 79614283-6733-4592-a53a-d428052271ad
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Attach
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'option VSPerfCmd.exe **Attach** commence le profilage des échantillons du processus en cours d'exécution spécifié par l'ID de processus \(PID\).  
  
 Pour utiliser l'option **Attach**, vous devez spécifier la méthode **Sample** dans l'option Start.  
  
> [!NOTE]
>  Si l'option **Start** a été spécifiée avec l'option **Crosssession**, tous les appels à **VSPerfCmd \/Attach** ou à **VSPerfCmd \/Detach** doivent également spécifier **Crosssession**.  
  
## Syntaxe  
  
```  
VSPerfCmd.exe /Attach:ProcessID [Options]  
```  
  
#### Paramètres  
 `ProcessID`  
 ID du processus \(PID\) du processus en cours d'exécution.  Le PID d'un processus en cours d'exécution est répertorié sous l'onglet Processus du Gestionnaire des tâches Windows.  
  
## Options valides  
 Les options **VSPerfCmd** suivantes peuvent être combinées avec l'option **Attach** sur une ligne de commande.  
  
 **Crosssession**  
 Permet le profilage d'applications dans des sessions autres que la session ouverte.  Obligatoire si l'option **Start** a été spécifiée avec l'option **Crosssession**.  
  
 **Start:** `Method`  
 Initialise la session de profileur en ligne de commande et définit la méthode de profilage spécifiée.  
  
 **TargetCLR**  
 Spécifie la version du .NET Framework Common Language Runtime \(CLR\) à profiler lorsque plusieurs versions sont chargées dans une session de profilage.  Par défaut, la première version chargée est profilée.  
  
 **GlobalOn GlobalOff**  
 Reprend \(**GlobalOn**\) ou interrompt \(**GlobalOff**\) le profilage, mais ne met pas fin à la session de profilage.  
  
 **ProcessOn:** `PID` **ProcessOff:** `PID`  
 Reprend \(**ProcessOn**\) ou interrompt \(**ProcessOff**\) le profilage pour le processus spécifié.  
  
## Options d'intervalle  
 L'une des options d'intervalle d'échantillonnage suivantes peut être spécifiée sur la ligne de commande Attach.  L'intervalle d'échantillonnage par défaut est de 10 000 000 cycles d'horloge du processeur.  
  
 **Timer**\[**:**`Cycles`\]**PF**\[**:**`Events`\]**Sys**\[**:**Événements\]**Counter**\[**:**`Name`,`Reload`,`FriendlyName`\]  
 Spécifie le nombre et le type de l'intervalle d'échantillonnage.  
  
-   **Timer** \- Échantillonne chaque cycle d'horloge du processeur `Cycles`.  Si `Cycles` n'est pas spécifié, 10 000 000 cycles sont utilisés.  
  
-   **PF** \- Échantillonne chaque défaut de page `Events`.  Si `Events` n'est pas spécifié, 10 défauts de page sont utilisés.  
  
-   **Sys** \- Échantillonne chaque appel `Events` au système d'exploitation.  Si `Events` n'est pas spécifié, 10 appels système sont utilisés.  
  
-   **Counter** \- Échantillonne le nombre `Reload` du compteur de performance de l'UC spécifié par `Name`.  `FriendlyName` peut éventuellement spécifier une chaîne à utiliser comme en\-tête de colonne dans les rapports du profileur.  
  
## Exemple  
 Cet exemple montre la jointure d'une instance en cours d'exécution d'une application avec l'ID de processus  12345.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Attach:12345  
```  
  
## Voir aussi  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilage d’applications autonomes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilage d’applications web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilage de services](../profiling/command-line-profiling-of-services.md)