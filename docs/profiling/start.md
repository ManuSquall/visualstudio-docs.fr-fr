---
title: "D&#233;marrer | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b85d0fe9-f67a-4b7c-8d48-7eecf3f2dfe9
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# D&#233;marrer
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'option **Start** est une option VSPerfCmd.exe qui initialise le profileur afin qu'il utilise la méthode de profilage spécifiée.  
  
## Syntaxe  
  
```  
VSPerfCmd.exe /Start:Method /Output:FileName [Options]  
```  
  
#### Paramètres  
 `Method`  
 Doit être l'un des mots\-clés suivants :  
  
-   **TRACE** \- Spécifie la méthode d'instrumentation.  
  
-   **SAMPLE**\- Spécifie la méthode d'échantillonnage.  
  
-   **COVERAGE**\- Spécifie la couverture du code.  
  
-   **CONCURRENCY** \- Spécifie la méthode de conflit de ressources.  
  
## Options requises  
 L'option **Output** doit être spécifiée quand **Start** est spécifié sur la ligne de commande.  
  
 **Output:** `filename`  
 Spécifie le nom du fichier de sortie.  
  
## Options exclusives  
 Les options suivantes peuvent être uniquement être utilisées avec l'option **Start** sur une ligne de commande.  
  
 **CrossSession**&#124;**CS**  
 Active le profilage interprocessus.  Les noms d'option **CrossSession** et **CS** sont tous les deux pris en charge.  
  
 **User:**\[`domain\`\]`username`  
 Autorise l'accès client à l'analyseur à partir du compte spécifié.  
  
 **WinCounter:** `Path` \[**Automark**:`n`\]  
 **WinCounter** spécifie un compteur de performances Windows à inclure comme marque dans le fichier de données de profilage.  **AutoMark** spécifie l'intervalle en millisecondes entre les collections du fichier de données.  
  
## Options non valides  
 Les options suivantes ne peuvent pas être utilisées avec l'option **Start** sur une ligne de commande.  
  
 **Status**  
 **Status** s'applique aux processus en cours de profilage.  Il répertorie les processus et les threads, ainsi que l'état de leur profil actuel \(Activé\/Désactivé\).  Par exemple, si un processus est arrêté, **Status** n'indiquera pas ceci dans le rapport.  **Status** affichera que le processus est profilé ou pas.  
  
 **Shutdown**\[**:**`Timeout`\]  
 Désactive le profileur.  
  
## Exemple  
 L'exemple suivant montre comment utiliser l'option VSPerfCmd.exe **Start** pour initialiser le profileur.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe  
```  
  
## Voir aussi  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilage d’applications autonomes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilage d’applications web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilage de services](../profiling/command-line-profiling-of-services.md)