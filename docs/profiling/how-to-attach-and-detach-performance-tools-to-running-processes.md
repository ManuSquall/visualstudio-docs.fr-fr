---
title: "Proc&#233;dure&#160;: attacher le profileur &#224; des processus en cours d’ex&#233;cution ou l’en d&#233;tacher | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.attach"
helpviewer_keywords: 
  - "outils de performance, attacher le processus"
  - "outils de profilage, détacher le processus"
  - "outils de profilage, attacher le processus"
  - "outils de performance, détacher le processus"
  - "profileur"
ms.assetid: 56a99c39-e7f6-4f48-ae56-04ab8e022bf7
caps.latest.revision: 30
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 30
---
# Proc&#233;dure&#160;: attacher le profileur &#224; des processus en cours d’ex&#233;cution ou l’en d&#233;tacher
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Le profileur peut être utilisé pour attacher ou détacher un processus en cours d'exécution afin de faciliter l'échantillonnage et la collecte des données de performance.  Vous pouvez utiliser cette méthode pour profiler un processus lorsque vous voulez éviter de collecter des données sur le temps de chargement de l'application ou surveiller les performances d'un processus une fois que celui\-ci a atteint un état spécifique.  
  
> [!NOTE]
>  Les étapes suivantes s'appliquent aux processus d'attachement et de détachement dans l'[!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]IDE.  Pour plus d'informations sur l'utilisation des outils de ligne de commande, consultez [Profilage à partir de la ligne de commande](../profiling/using-the-profiling-tools-from-the-command-line.md).  Pour plus d'informations sur le profilage de services, consultez [Profilage de services](../profiling/command-line-profiling-of-services.md).  
  
 Les processus disponibles pour le profilage dépendent des autorisations d'accès utilisateur définies par un administrateur de l'ordinateur.  Par exemple, un compte d'utilisateur peut avoir l'autorisation pour l'un quelconque des éléments suivants :  
  
-   Fonctionnalités de profilage avancées, lorsque l'administrateur a défini le pilote et le service à démarrer.  
  
-   Profilage d'échantillons uniquement \(utilisateurs de domaine\).  
  
-   Refus d'accès au profilage à tout le monde.  
  
 Pour plus d'informations, consultez [Profilage et sécurité Windows Vista](../profiling/profiling-and-windows-vista-security.md) et les options ADMIN de [VSPerfCmd](../profiling/vsperfcmd.md).  
  
### Pour établir un attachement à un processus en cours d'exécution  
  
1.  Dans le menu **Analyser**, pointez sur **Profileur**, puis cliquez sur **Attacher\/Détacher**.  
  
     \- ou \-  
  
     Dans l'**Explorateur de performances**, cliquez avec le bouton droit sur la session de performance, puis cliquez sur **Attacher\/Détacher**.  
  
     La boîte de dialogue **Attacher le profileur au processus** s'affiche.  
  
2.  Cliquez sur le nom du processus auquel vous voulez attacher.  
  
3.  Cliquez sur **Attacher**.  
  
### Pour détacher un processus en cours d'exécution  
  
1.  Dans le menu **Analyser**, pointez sur **Profileur**, puis cliquez sur **Attacher\/Détacher**.  
  
     \- ou \-  
  
     Dans l'**Explorateur de performances**, cliquez avec le bouton droit sur la session de performance, puis cliquez sur **Attacher\/Détacher**.  
  
     La boîte de dialogue **Attacher le profileur au processus** s'affiche.  
  
2.  Cliquez sur le nom de l'image dont vous souhaitez vous détacher.  
  
3.  Cliquez sur **Détacher**.  
  
## Voir aussi  
 [Contrôle de la collecte de données](../profiling/controlling-data-collection.md)   
 [Vue d’ensemble de la session de performance](../profiling/performance-session-overview.md)   
 [Procédure : démarrer et arrêter le profilage](../profiling/how-to-start-and-end-performance-data-collection.md)   
 [Profilage et sécurité Windows Vista](../profiling/profiling-and-windows-vista-security.md)   
 [VSPerfCmd](../profiling/vsperfcmd.md)