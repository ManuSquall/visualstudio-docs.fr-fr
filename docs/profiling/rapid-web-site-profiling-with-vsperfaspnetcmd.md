---
title: "Profilage de site Web rapide avec VSPerfASPNETCmd | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "outils de profilage, VSPerfASPNETCmd"
  - "VSPerfASPNETCmd"
ms.assetid: 9a9d62a6-549a-45ac-a948-76eb98586ac5
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# Profilage de site Web rapide avec VSPerfASPNETCmd
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'outil en ligne de commande **VSPerfASPNETCmd** vous permet de profiler facilement des applications Web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].  En comparaison avec l'outil en ligne de commande [VSPerfCmd](../profiling/vsperfcmd.md), les options sont réduites, aucune variable d'environnement ne doit être définie et le redémarrage de l'ordinateur n'est pas obligatoire.  **VSPerfASPNETCmd** est la méthode recommandée pour le profilage avec le profileur autonome.  Pour plus d'informations, consultez [Comment : installer le profileur autonome](../profiling/how-to-install-the-stand-alone-profiler.md).  
  
> [!NOTE]
>  Les fonctionnalités de sécurité renforcée dans Windows 8 et Windows Server 2012 nécessitaient d'importantes modifications de la manière dont le profileur Visual Studio collecte des données sur ces plateformes.  Les applications Windows Store requièrent également de nouvelles techniques de collecte.  Consultez [Profilage d'applications Windows 8 et Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
 Dans certains scénarios, tels que la collecte de données d'accès concurrentiel ou la suspension et la reprise de profilage, **VSPerfCmd** est la méthode de profilage par défaut.  
  
> [!NOTE]
>  Les outils en ligne de commande des outils de profilage se trouvent dans le sous\-répertoire \\Team Tools\\Performance Tools du répertoire d'installation de [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] s  Sur les ordinateurs 64 bits, utilisez l'outil VSPerfASPNETCmd situé dans le répertoire 32 bits \\Team Tools\\Performance Tools.  Pour utiliser les outils en ligne de commande du profileur, vous devez ajouter le chemin d'accès des outils à la variable d'environnement PATH de la fenêtre Invite de commandes ou l'ajouter à la commande elle\-même.  Pour plus d'informations, consultez [Spécification du chemin d'accès aux outils en ligne de commande](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
  
## Profilage d'une application ASP.NET  
 Pour profiler une application Web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], tapez l'une des commandes décrites dans les sections suivantes.  Le site Web est démarré et le profileur commence à collecter des données.  Testez votre application, puis fermez le navigateur.  Pour arrêter le profilage, appuyez sur la touche Entrée dans la fenêtre d'invite de commandes.  
  
> [!NOTE]
>  Par défaut, l'invite de commandes n'est pas retournée après une commande **vsperfaspnetcmd**.  Vous pouvez utiliser l'option **\/nowait** pour forcer le retour de l'invite de commandes.  See [Utilisation de l'option /NoWait](#UsingNoWait).  
  
## Pour collecter des statistiques d'application à l'aide de la méthode d'échantillonnage  
 L'échantillonnage est la méthode de profilage par défaut de l'outil **VSPerfASPNETCmd** et ne doit pas être nécessairement spécifié sur la ligne de commande.  La ligne de commande suivante collecte les statistiques à partir de l'application Web spécifiée :  
  
 **vsperfaspnetcmd**  *websiteUrl*  
  
## Pour collecter des données de minutage détaillées à l'aide de la méthode d'instrumentation  
 Utilisez la ligne de commande suivante pour collecter des données de minutage détaillées à partir d'une application Web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] compilée de façon dynamique :  
  
 **vsperfaspnetcmd \/trace**  *websiteUrl*  
  
 Si vous souhaitez profiler des fichiers .dll compilés statiquement dans votre application Web, vous devez instrumenter les fichiers à l'aide de l'outil en ligne de commande [VSInstr](../profiling/vsinstr.md).  La commande \/trace de vsperfaspnetcmd inclura les données des fichiers instrumentés.  
  
## Pour collecter les données de la mémoire .NET  
 L'option **\/Memory** permet de collecter des données sur l'allocation des objets dans la mémoire .NET et peut collecter des données sur la durée de vie de ces objets.  La collecte de données d'allocation est le mode par défaut de l'option de données **\/Memory** et ne doit pas être nécessairement spécifiée sur la ligne de commande.  
  
 **vsperfaspnetcmd \/memory** *websiteUrl*  
  
 Utilisez le paramètre **Lifetime** pour collecter les données de durée de vie de l'objet en plus des données d'allocation :  
  
 **vsperfaspnetcmd \/memory:lifetime** *websiteUrl*  
  
 Vous pouvez également utiliser l'option **\/Trace** pour inclure des informations de minutage détaillées avec les données de mémoire .NET :  
  
 **vsperfaspnetcmd \/memory**\[**:lifetime**\] **\/trace** `websiteUrl`  
  
## Pour collecter les données d'interaction de couche  
  
> [!WARNING]
>  Les données de profilage d'interaction de couche \(TIP\) peuvent être collectées à l'aide de [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], ou [!INCLUDE[vs_pro_current_short](../profiling/includes/vs_pro_current_short_md.md)].  Toutefois, les données de profilage d'interaction de couche peuvent être affichées uniquement dans [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)] et [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)].  
>   
>  Pour recueillir des données TIP sur windows 8 ou sur Windows Server 2012, vous devez utiliser l'option d'instrumentation \(**\/trace**\).  
  
 Pour collecter les données d'interaction de couche avec les données d'échantillonnage :  
  
 **vsperfaspnetcmd \/tip** `websiteUrl`  
  
 Pour collecter les données d'interaction de couche avec les données d'instrumentation :  
  
 **vsperfaspnetcmd \/trace \/tip** *websiteUrl*  
  
 Pour collecter les données d'interaction de couche avec les données de mémoire .NET :  
  
 **vsperfaspnetcmd \/memory**\[**:lifetime**\] **\/tip** *websiteUrl*  
  
##  <a name="UsingNoWait"></a> Utilisation de l'option \/NoWait  
 Par défaut, l'invite de commandes n'est pas retournée après une commande **vsperfaspnetcmd**.  Vous pouvez utiliser l'option de syntaxe suivante pour forcer le retour de l'invite de commandes.  Vous pouvez exécuter ensuite d'autres opérations dans la fenêtre d'invite de commandes.  Pour terminer le profilage, utilisez l'option **\/shutdown** dans une commande **vsperfaspnetcmd** séparée.  
  
 Pour commencer le profilage :  
  
 **vsperfaspnetcmd** \[*\/Options*\] **\/nowait** *websiteUrl*  
  
 Pour terminer le profilage :  
  
 **vsperfaspnetcmd \/shutdown** *websiteUrl*  
  
## Options supplémentaires  
 Vous pouvez ajouter l'une des options suivantes aux commandes répertoriées précédemment dans cette section, à l'exception de la commande **vsperfaspnetcmd \/shutdown**.  
  
|Option|Description|  
|------------|-----------------|  
|**\/Output:** `VspFile`|Par défaut, le fichier de données de profilage \(.vsp\) est créé dans le répertoire actif avec le nom de fichier **PerformanceReport.vsp**.  Utilisez l'option \/output pour spécifier un autre emplacement, nom de fichier, ou les deux.|  
|**\/PackSymbols:Off**|Par défaut, VsPerfASPNETCmd incorpore des symboles \(noms de fonction et de paramètre, etc\) dans le fichier .vsp.  L'incorporation des symboles peut générer un fichier de données de profilage très volumineux.  Si vous avez accès aux fichiers .pdb qui contiennent les symboles lorsque vous analysez les données, utilisez l'option \/packsymbols:off pour désactiver l'incorporation des symboles.|