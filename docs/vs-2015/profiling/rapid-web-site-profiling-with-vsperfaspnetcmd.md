---
title: Profilage de site web rapide avec VSPerfASPNETCmd | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- proflilng tools,VSPerfASPNETCmd
- VSPerfASPNETCmd
ms.assetid: 9a9d62a6-549a-45ac-a948-76eb98586ac5
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 80acb5030c61bd986bfbd2a5f2b383ac37a25a0c
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51760013"
---
# <a name="rapid-web-site-profiling-with-vsperfaspnetcmd"></a>Profilage de site web rapide avec VSPerfASPNETCmd
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L’outil en ligne de commande **VSPerfASPNETCmd** vous permet de profiler facilement des applications web [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]. Par rapport à l’outil en ligne de commande [VSPerfCmd](../profiling/vsperfcmd.md), cet outil comporte moins d’options et ne nécessite ni configuration de variables d’environnement, ni redémarrage de l’ordinateur. L’utilisation de **VSPerfASPNETCmd** est la méthode recommandée pour le profilage avec le profileur autonome. Pour plus d’informations, consultez [Guide pratique pour installer le profileur autonome](../profiling/how-to-install-the-stand-alone-profiler.md).  
  
> [!NOTE]
>  Les fonctionnalités de sécurité renforcée de Windows 8 et Windows Server 2012 ont imposé des changements importants dans la façon dont le profileur Visual Studio collecte les données sur ces plateformes. Les applications Windows Store demandent aussi de nouvelles techniques de collecte. Consultez [Outils d’analyse des performances sur les applications Windows 8 et Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
 Dans certains scénarios, comme la collecte des données d’accès concurrentiel, ou la suspension et reprise du profilage, **VSPerfCmd** est la méthode de profilage recommandée.  
  
> [!NOTE]
>  Les outils en ligne de commande des outils de profilage se trouvent dans le sous-répertoire \Team Tools\Performance Tools du répertoire d’installation de [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]. Sur les ordinateurs 64 bits, utilisez l’outil VSPerfASPNETCmd qui se trouve dans le répertoire 32 bits \Team Tools\Performance Tools. Pour utiliser les outils en ligne de commande du profileur, vous devez ajouter le chemin des outils à la variable d’environnement PATH dans la fenêtre d’invite de commandes ou bien l’ajouter à la commande elle-même. Pour plus d’informations, consultez [Spécification du chemin d’accès aux outils en ligne de commande](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
  
## <a name="profiling-an-aspnet-application"></a>Profilage d’une application ASP.NET  
 Pour profiler une application web [!INCLUDE[vstecasp](../includes/vstecasp-md.md)], tapez une des commandes décrites dans les sections suivantes. Votre site web est démarré et le profileur commence à collecter des données. Utilisez votre application, puis fermez le navigateur. Pour arrêter le profilage, appuyez sur la touche Entrée dans la fenêtre d’invite de commandes.  
  
> [!NOTE]
>  Par défaut, l’invite de commandes ne réapparaît pas après une commande **vsperfaspnetcmd**. Vous pouvez utiliser l’option **/nowait** pour forcer le retour de l’invite de commandes. Consultez [Utilisation de l’option /NoWait](#UsingNoWait).  
  
## <a name="to-collect-application-statistics-by-using-the-sampling-method"></a>Pour collecter des statistiques d’application à l’aide de la méthode d’échantillonnage  
 L’échantillonnage est la méthode de profilage par défaut de l’outil **VSPerfASPNETCmd** et il n’est pas nécessaire de le spécifier sur la ligne de commande. La ligne de commande suivante collecte les statistiques de l’application web spécifiée :  
  
 **vsperfaspnetcmd**  *URL_site_web*  
  
## <a name="to-collect-detailed-timing-data-by-using-the-instrumentation-method"></a>Pour collecter les données de minutage détaillées en utilisant la méthode d’instrumentation  
 Utilisez la ligne de commande suivante pour collecter les données de minutage détaillées pour une application web [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] compilée dynamiquement :  
  
 **vsperfaspnetcmd /trace**  *URL_site_web*  
  
 Si vous voulez profiler des fichiers .dll compilés statiquement dans votre application web, vous devez instrumenter les fichiers à l’aide de l’outil en ligne de commande [VSInstr](../profiling/vsinstr.md). La commande vsperfaspnetcmd /trace inclut alors les données des fichiers instrumentés.  
  
## <a name="to-collect-net-memory-data"></a>Pour collecter des données de mémoire .NET  
 L’option **mémoire/mémoire** collecte les données relatives à l’allocation d’objets dans la mémoire .NET et peut collecter des données sur la durée de vie de ces objets. La collecte des données d’allocation est le mode par défaut de l’option de données **/Memory** et il n’est pas nécessaire de la spécifier sur la ligne de commande.  
  
 **vsperfaspnetcmd /memory** *URL_site_web*  
  
 Utilisez le paramètre **lifetime** pour collecter les données de durée de vie des objets en plus des données d’allocation :  
  
 **vsperfaspnetcmd /memory:lifetime** *URL_site_web*  
  
 Vous pouvez également utiliser l’option **/Trace** pour inclure les informations de minutage détaillées avec les données de mémoire .NET :  
  
 **vsperfaspnetcmd /memory**[**:lifetime**] **/trace**`websiteUrl`  
  
## <a name="to-collect-tier-interaction-data"></a>Pour collecter les données d’interaction de couche  
  
> [!WARNING]
>  Les données de profilage d’interaction de couche peuvent être collectées en utilisant [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] ou [!INCLUDE[vs_pro_current_short](../includes/vs-pro-current-short-md.md)]. Cependant, les données de profilage d’interaction de couche ne peuvent être affichées que dans [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)] et [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)].  
>   
>  Pour collecter des données TIP sur Windows 8 ou Windows Server 2012, vous devez utiliser l’option d’instrumentation (**/trace**).  
  
 Pour collecter les données d’interaction de couche avec les données d’échantillonnage :  
  
 **vsperfaspnetcmd /tip** `websiteUrl`  
  
 Pour collecter les données d’interaction de couche avec les données d’instrumentation :  
  
 **vsperfaspnetcmd /trace /tip** *URL_site_web*  
  
 Pour collecter les données d’interaction de couche avec les données de mémoire .NET :  
  
 **vsperfaspnetcmd /memory**[**:lifetime**] **/tip**_URL_site_web_  
  
##  <a name="UsingNoWait"></a> Utilisation de l’option /NoWait  
 Par défaut, l’invite de commandes ne réapparaît pas après une commande **vsperfaspnetcmd**. Vous pouvez utiliser l’option de syntaxe suivante pour forcer le retour de l’invite de commandes. Vous pouvez alors effectuer d’autres opérations dans la fenêtre d’invite de commandes. Pour terminer le profilage, utilisez l’option **/shutdown** dans une commande **vsperfaspnetcmd** distincte.  
  
 Pour démarrer le profilage :  
  
 **vsperfaspnetcmd** [*/Options*] **/nowait**_URL_site_web_  
  
 Pour terminer le profilage :  
  
 **vsperfaspnetcmd /shutdown** *URL_site_web*  
  
## <a name="additional-options"></a>Options supplémentaires  
 Vous pouvez ajouter les options suivantes aux commandes répertoriées plus haut dans cette section, excepté la commande **vsperfaspnetcmd /shutdown**.  
  
|Option|Description|  
|------------|-----------------|  
|**/Output:** `VspFile`|Par défaut, le fichier (.vsp) de données de profilage est créé dans le répertoire actif avec le nom de fichier **PerformanceReport.vsp**. Utilisez l’option /output pour spécifier un autre emplacement, le nom du fichier ou les deux.|  
|**/PackSymbols:Off**|Par défaut, VsPerfASPNETCmd incorpore des symboles (noms des fonctions et des paramètres, etc.) dans le fichier .vsp. L’incorporation des symboles peut rendre le fichier de données de profilage très volumineux. Si vous devez accéder aux fichiers .pdb qui contiennent les symboles quand vous analysez les données, utilisez l’option /packsymbols:off pour désactiver l’incorporation des symboles.|



