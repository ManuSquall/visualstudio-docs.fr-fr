---
title: "Detach | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d9d1b52c-7f28-467d-b1e0-512afc4e46c9
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Detach
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'option VSPerfCmd.exe **Detach** déconnecte le profileur des processus spécifiés ou de tous les processus si aucun n'est spécifié.  Le profilage doit avoir été initialisé à l'aide de la méthode d'échantillonnage.  
  
 Le profilage démarré avec les options **Launch** ou **Attach** peut être déconnecté avec **Detach**.  Le profileur peut être rattaché à l'aide des commandes **Attach** suivantes.  
  
 **Detach** ne ferme pas le fichier de données de profilage.  Utilisez l'option **Shutdown** pour terminer le profilage et fermer le fichier de données.  
  
> [!NOTE]
>  Si l'option **Start** a été spécifiée avec l'option **Crosssession**, tous les appels à **VSPerfCmd \/Attach** ou à **VSPerfCmd \/Detach** doivent également spécifier **Crosssession**.  
  
## Syntaxe  
  
```  
VSPerfCmd.exe /Detach[:PIDs|ProcessNames]  
```  
  
#### Paramètres  
 `PIDs|ProcessNames`  
 `PID`\- Identificateur de système numérique d'un ou plusieurs processus.  
  
 `ProcessNames` \- Nom du processus.  Si plusieurs instances du processus nommé s'exécutent, les résultats sont imprévisibles.  
  
 Séparez les processus par des virgules.  
  
 Si aucun processus n'est spécifié, le profileur est détaché de tous les processus profilés.  
  
## Options valides  
 Les options **VSPerfCmd** suivantes peuvent être combinées avec l'option **Attach** sur une ligne de commande.  
  
 **Crosssession**  
 Permet le profilage d'applications dans des sessions autres que la session ouverte.  Obligatoire si l'option **Start** a été spécifiée avec l'option **Crosssession**.  
  
## Exemple  
 Dans cet exemple, la commande **Detach** interrompt le profilage et la commande **Shutdown** ferme le fichier de données du profileur.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe  
;REM Excercise the application  
VSPerfCmd.exe /Detach  
VSPerfCmd.exe /Shutdown  
```  
  
## Voir aussi  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilage d’applications autonomes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilage d’applications web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilage de services](../profiling/command-line-profiling-of-services.md)