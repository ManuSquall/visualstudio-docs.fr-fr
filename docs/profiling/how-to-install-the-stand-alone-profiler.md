---
title: "Comment&#160;: installer le profileur autonome | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "outils d'analyse des performances, installer le profileur autonome"
  - "outils de profilage, profileur autonome"
ms.assetid: cae81c95-83cd-4ab6-8a98-84ef977a2f6d
caps.latest.revision: 24
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 24
---
# Comment&#160;: installer le profileur autonome
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] fournit un profileur autonome basé sur une ligne de commande, qui peut être exécuté sans installer l'IDE [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Cette situation se produit lorsqu'un ordinateur n'a pas ou ne peut pas avoir d'environnement de développement.  Par exemple, vous ne devez pas installer d'environnement de développement sur un serveur Web de production.  
  
> [!NOTE]
>  Lorsque vous utilisez le profileur autonome pour collecter des données de performances pour un site Web ASP.NET, l'outil en ligne de commande [VSPerfASPNetCmd](../profiling/vsperfaspnetcmd.md) est recommandé sur l'outil [VSPerfCmd](../profiling/vsperfcmd.md).  
  
### Pour installer le profileur autonome  
  
1.  Repérez l'installateur de profil autonome \(vs\_profiler.exe\) sur le média d'installation [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] dans le répertoire qui inclut le chemin d'accès \\Standalone Profiler et exécutez\-le.  
  
2.  Ajoutez les chemins d'accès pour vsintr.exe et msdis150.dll au chemin d'accès système.  
  
    > [!NOTE]
    >  Dans l'installation par défaut de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], vsinstr.exe et msdis150.dll se trouvent dans \\Program Files\\Visual Studio 10\\Team Tools\\Performance Tools.  
  
3.  À l'invite de commandes, tapez **VSInstr**.  
  
    > [!NOTE]
    >  Si les informations d'utilisation pour vsinstr.exe sont affichées, tout est installé correctement.  Si un message d'erreur indique que vsinstr.exe ou une de ses dépendances est introuvable, assurez\-vous que vous avez configuré correctement vos chemins d'accès comme décrit à l'étape 2.  
  
4.  Installez le serveur de symboles en affectant la valeur **symsrv\*symsrv.dll\*c:\\localcache\*http:\/\/msdl.microsoft.com\/download\/symbols** à la variable **\_NT\_SYMBOL\_PATH**.  
  
5.  Après avoir installé votre serveur de symboles à l'aide des variables d'environnement système, exécutez les outils du profileur de ligne de commande à une nouvelle invite de commandes.  Cela permet la prise en compte des nouvelles variables d'environnement.  Dans la fenêtre d'invite de commandes, tapez la commande suivante :  
  
     **start %COMSPEC%**  
  
    > [!NOTE]
    >  Pour obtenir des instructions détaillées sur le mode d'installation du package du serveur de symboles, consultez [Comment : référencer les informations de symboles Windows](../profiling/how-to-reference-windows-symbol-information.md).  
  
6.  Utilisez l'outil [VSPerfReport](../profiling/vsperfreport.md) pour sérialiser vos symboles dans le fichier de données de profilage \(.vsp\).  Utilisez les commutateurs **VSPerfReport \/summary:all \/packsymbols**.  Si aucun symbole n'est inséré dans le fichier de données, assurez\-vous que la variable d'environnement \_NT\_SYMBOL\_PATH est définie.  
  
## Voir aussi  
 [Profilage à partir de la ligne de commande](../profiling/using-the-profiling-tools-from-the-command-line.md)   
 [Procédure pas à pas : profilage de la ligne de commande à l’aide de l’échantillonnage](../Topic/Walkthrough:%20Command-Line%20Profiling%20Using%20Sampling.md)   
 [Procédure pas à pas : profilage de la ligne de commande à l’aide de l’instrumentation](../profiling/walkthrough-command-line-profiling-using-instrumentation.md)   
 [Comment : référencer les informations de symboles Windows](../profiling/how-to-reference-windows-symbol-information.md)   
 [VSPerfReport](../profiling/vsperfreport.md)