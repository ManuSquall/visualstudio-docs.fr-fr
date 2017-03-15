---
title: "Profilage et s&#233;curit&#233; Windows Vista | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Outils de profilage, sécurité"
  - "outils d’analyse des performances, sécurité"
ms.assetid: 842112fc-b886-4801-8cd7-a25b314b0393
caps.latest.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 19
---
# Profilage et s&#233;curit&#233; Windows Vista
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Selon les paramètres d'autorisation d'accès utilisateur de [!INCLUDE[wiprlhext](../misc/includes/wiprlhext_md.md)] mis à disposition par l'administrateur d'un ordinateur, un utilisateur individuel peut avoir l'autorisation de profiler un processus sur cet ordinateur.  Les exemples suivants illustrent les différences possibles parmi les utilisateurs :  
  
-   Certains utilisateurs peuvent accéder aux fonctionnalités de profilage avancées lorsque l'administrateur a paramétré le pilote et le service à démarrer.  
  
-   Les utilisateurs de domaine peuvent accéder uniquement à l'exemple de profilage.  
  
-   Certains utilisateurs peuvent refuser l'accès au profilage à tous les autres utilisateurs.  
  
 Pour plus d'informations, consultez les options ADMIN dans [VSPerfCmd](../profiling/vsperfcmd.md).  
  
## Profilage intersession  
 Le *profilage intersession* est la capacité à profiler un processus qui s'exécute dans une ouverture de session différente.  Par exemple, la plupart des services s'exécutent dans la session 0 et les utilisateurs ne peuvent pas s'exécuter directement dans la session 0.  À l'aide du bouton **Attacher au processus** de la barre d'outils Explorateur de performances ou de l'option \/attach de l'outil en ligne de commande VSPerfCmd, vous pouvez profiler la plupart des processus des différentes sessions ouvertes.  
  
 Vous pouvez consulter une liste des processus disponibles en paramétrant les options de visibilité du profilage interprocessus.  Ces options sont disponibles dans la fenêtre **Attacher au processus** qui s'affiche lorsque vous cliquez sur **Attacher au processus**.  
  
-   **Afficher les processus de tous les utilisateurs**  
  
     Lorsque cette option n'est pas sélectionnée, la liste n'affiche que les processus détenus par l'utilisateur actuel.  Lorsque l'option **Afficher les processus de tous les utilisateurs** est sélectionnée, la liste affiche les processus de tous les utilisateurs.  
  
-   **Afficher les processus de toutes les sessions**  
  
     Lorsque cette option n'est pas sélectionnée, la liste affiche les processus pour la session en cours.  Lorsque cette option est sélectionnée, la liste affiche les processus de toutes les sessions.  
  
## Voir aussi  
 [Vues d'ensemble](../profiling/overviews-performance-tools.md)   
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [How to: Attach to a Running Process](http://msdn.microsoft.com/fr-fr/636d0a52-4bfd-48d2-89ad-d7b9ca4dc4f4)