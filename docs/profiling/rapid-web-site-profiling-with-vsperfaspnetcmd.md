---
title: Profilage de site web rapide avec VSPerfASPNETCmd | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- proflilng tools,VSPerfASPNETCmd
- VSPerfASPNETCmd
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: dd26d5b17d6dbd2e2c1dbacb1a23d81ffe733fdf
ms.sourcegitcommit: 36ab8429333b31f03992a9fe8fc669db8e09c968
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2018
---
# <a name="rapid-web-site-profiling-with-vsperfaspnetcmd"></a>Profilage de site web rapide avec VSPerfASPNETCmd

L’outil en ligne de commande **VSPerfASPNETCmd** vous permet de profiler facilement des applications web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]. Par rapport à l’outil en ligne de commande [VSPerfCmd](../profiling/vsperfcmd.md), cet outil comporte moins d’options et ne nécessite ni configuration de variables d’environnement, ni redémarrage de l’ordinateur. L’utilisation de **VSPerfASPNETCmd** est la méthode recommandée pour le profilage avec le profileur autonome. Pour plus d’informations, consultez [Guide pratique pour installer le profileur autonome](../profiling/how-to-install-the-stand-alone-profiler.md).

> [!NOTE]
> Les fonctionnalités de sécurité renforcée de Windows 8 et Windows Server 2012 ont imposé des changements importants dans la façon dont le profileur Visual Studio collecte les données sur ces plateformes. Les applications UWP nécessitent aussi de nouvelles techniques de collecte. Consultez [Outils d’analyse des performances sur les applications Windows 8 et Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

 Dans certains scénarios, comme la collecte des données d’accès concurrentiel, ou la suspension et reprise du profilage, **VSPerfCmd** est la méthode de profilage recommandée.

> [!NOTE]
> Les outils en ligne de commande des outils de profilage se trouvent dans le sous-répertoire \Team Tools\Performance Tools du répertoire d’installation Visual Studio. Sur les ordinateurs 64 bits, utilisez l’outil VSPerfASPNETCmd qui se trouve dans le répertoire 32 bits \Team Tools\Performance Tools. Pour utiliser les outils en ligne de commande du profileur, vous devez ajouter le chemin des outils à la variable d’environnement PATH dans la fenêtre d’invite de commandes ou bien l’ajouter à la commande elle-même. Pour plus d’informations, consultez [Spécification du chemin d’accès aux outils en ligne de commande](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).

## <a name="profiling-an-aspnet-application"></a>Profiler une application ASP.NET

Pour profiler une application web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], tapez une des commandes décrites dans les sections suivantes. Votre site web est démarré et le profileur commence à collecter des données. Utilisez votre application, puis fermez le navigateur. Pour arrêter le profilage, appuyez sur la touche Entrée dans la fenêtre d’invite de commandes.

> [!NOTE]
> Par défaut, l’invite de commandes ne réapparaît pas après une commande **vsperfaspnetcmd**. Vous pouvez utiliser l’option **/nowait** pour forcer le retour de l’invite de commandes. Consultez [Utilisation de l’option /NoWait](#UsingNoWait).

## <a name="to-collect-application-statistics-by-using-the-sampling-method"></a>Pour collecter des statistiques d’application à l’aide de la méthode d’échantillonnage
 L’échantillonnage est la méthode de profilage par défaut de l’outil **VSPerfASPNETCmd** et il n’est pas nécessaire de le spécifier sur la ligne de commande. La ligne de commande suivante collecte les statistiques de l’application web spécifiée :

 **vsperfaspnetcmd**  *URL_site_web*

## <a name="to-collect-detailed-timing-data-by-using-the-instrumentation-method"></a>Pour collecter les données de minutage détaillées en utilisant la méthode d’instrumentation

Utilisez la ligne de commande suivante pour collecter les données de minutage détaillées pour une application web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] compilée dynamiquement :

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
> Pour collecter des données de profilage d’interaction de couche (TIP), vous pouvez utiliser n’importe quelle édition de Visual Studio. Cependant, ces données ne sont consultables que dans Visual Studio Enterprise.
>
> Pour collecter des données TIP sur Windows 8 ou Windows Server 2012, vous devez utiliser l’option d’instrumentation (**/trace**).

Pour collecter les données d’interaction de couche avec les données d’échantillonnage :

**vsperfaspnetcmd /tip** `websiteUrl`

Pour collecter les données d’interaction de couche avec les données d’instrumentation :

**vsperfaspnetcmd /trace /tip** *URL_site_web*

Pour collecter les données d’interaction de couche avec les données de mémoire .NET :

**vsperfaspnetcmd /memory**[**:lifetime**] **/tip***websiteUrl*

## <a name="UsingNoWait"></a> Utilisation de l’option /NoWait

Par défaut, l’invite de commandes ne réapparaît pas après une commande **vsperfaspnetcmd**. Vous pouvez utiliser l’option de syntaxe suivante pour forcer le retour de l’invite de commandes. Vous pouvez alors effectuer d’autres opérations dans la fenêtre d’invite de commandes. Pour terminer le profilage, utilisez l’option **/shutdown** dans une commande **vsperfaspnetcmd** distincte.

Pour démarrer le profilage :

**vsperfaspnetcmd** [*/Options*] **/nowait***websiteUrl*

Pour terminer le profilage :

**vsperfaspnetcmd /shutdown** *URL_site_web*

## <a name="additional-options"></a>Options supplémentaires

Vous pouvez ajouter les options suivantes aux commandes répertoriées plus haut dans cette section, excepté la commande **vsperfaspnetcmd /shutdown**.

|Option|Description|
|------------|-----------------|
|**/Output:** `VspFile`|Par défaut, le fichier (.vsp) de données de profilage est créé dans le répertoire actif avec le nom de fichier **PerformanceReport.vsp**. Utilisez l’option /output pour spécifier un autre emplacement, le nom du fichier ou les deux.|
|**/PackSymbols:Off**|Par défaut, VsPerfASPNETCmd incorpore des symboles (noms des fonctions et des paramètres, etc.) dans le fichier .vsp. L’incorporation des symboles peut rendre le fichier de données de profilage très volumineux. Si vous devez accéder aux fichiers .pdb qui contiennent les symboles quand vous analysez les données, utilisez l’option /packsymbols:off pour désactiver l’incorporation des symboles.|
