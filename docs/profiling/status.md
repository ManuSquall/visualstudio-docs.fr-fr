---
title: "Status | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ba656fa4-ef9d-4d8c-a3b6-739c3b5d23ae
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# Status
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'option VSPerfCmd.exe **Status** affiche des informations sur l'état du profileur et des processus en cours de profilage.  
  
 L'option **Status** doit être la seule option spécifiée sur la ligne de commande.  Le profileur doit être initialisé avec l'option VSPerfCmd.exe **Start** avant qu'un état puisse être affiché.  
  
## Syntaxe  
  
```  
VSPerfCmd.exe /Status  
```  
  
#### Paramètres  
 Aucun  
  
## Notes  
 L'option **Status** affiche les informations d'état suivantes pour le profileur.  
  
 **Output File Name**  
 Chemin d'accès et nom de fichier du fichier de données du profileur actuel.  
  
 **Collection Mode**  
 SAMPLE ou TRACE  
  
 **Maximum Processes**  
 Nombre maximal des processus pouvant être profilés simultanément et nombre de processus actuellement actifs.  
  
 **Maximum Threads**  
 Nombre maximal de threads pouvant être profilés simultanément.  
  
 **Number of Buffers**  
 Nombre de tampons de mémoire consacrés à l'écriture des données de profilage.  
  
 **Size of Buffers**  
 Taille en octets d'une zone de mémoire tampon.  
  
 L'option **Status** affiche les informations d'état suivantes pour chaque processus en cours de profilage.  
  
 **Process**  
 Nom du processus profilé.  
  
 **Process ID**  
 Identificateur système du processus.  
  
 **Num Threads**  
 Nombre de threads en cours d'exécution.  
  
 **Start\/Stop Count**  
 Nombre du profileur interne principal qui contrôle la collecte de données pour ce processus.  Ce nombre doit être égal à un pour collecter des données.  Le nombre Démarrage\/Arrêt peut être modifié par les API du profileur et les options VSPerfCmd **GlobalOn**, **GlobalOff**, **ProcessOn**, **ProcessOff**, **ThreadOn**et **ThreadOff**.  
  
 **Suspend\/Resume Count**  
 Nombre du profileur interne secondaire qui contrôle la collecte de données pour ce processus.  Le nombre doit être inférieur ou égal à zéro à pour collecter des données.  Le nombre **Suspend\/Resume** peut être modifié uniquement par les API du profileur.  
  
 **Users with access rights to monitor**  
 Répertorie les noms des utilisateurs qui ont accès au profileur.  Des utilisateurs supplémentaires peuvent être autorisés à accéder via l'option VSPerfCmd.exe **Admin**  
  
## Voir aussi  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilage d’applications autonomes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilage d’applications web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilage de services](../profiling/command-line-profiling-of-services.md)