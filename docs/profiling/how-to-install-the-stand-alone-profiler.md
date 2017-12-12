---
title: Guide pratique pour installer le profileur autonome | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- performance tools, installing stand-alone profiler
- profiling tools, stand-alone profiler
ms.assetid: cae81c95-83cd-4ab6-8a98-84ef977a2f6d
caps.latest.revision: "24"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0799a5da2b1596c79a57a6960283c62fca709a8a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-install-the-stand-alone-profiler"></a>Guide pratique pour installer le profileur autonome
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] fournit un profileur autonome basé sur la ligne de commande qui peut être exécuté sans installer l’IDE [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Cette situation se produit quand un environnement de développement n’est pas ou ne peut pas être installé sur un ordinateur. Par exemple, vous ne devez pas installer un environnement de développement sur un serveur web de production.  
  
> [!NOTE]
>  Quand vous utilisez le profileur autonome pour collecter des données de performances pour un site web ASP.NET, l’outil en ligne de commande [VSPerfASPNetCmd](../profiling/vsperfaspnetcmd.md) est préférable à l’outil [VSPerfCmd](../profiling/vsperfcmd.md).  
  
### <a name="to-install-the-stand-alone-profiler"></a>Pour installer le profileur autonome  
  
1.  Recherchez le programme d’installation du profileur autonome (vs_profiler.exe) sur le support d’installation de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] dans le répertoire qui inclut le chemin \Standalone Profiler et exécutez-le.  
  
2.  Ajoutez les chemins pour vsintr.exe et msdis150.dll au chemin du système.  
  
    > [!NOTE]
    >  Dans l’installation par défaut de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], vsinstr.exe et msdis150.dll se trouvent dans \Program Files\Visual Studio 10\Team Tools\Performance Tools.  
  
3.  À l’invite de commandes, entrez **VSInstr**.  
  
    > [!NOTE]
    >  Si les informations d’utilisation pour vsinstr.exe s’affichent, c’est que tout est configuré correctement. Si vous voyez une erreur indiquant que vsinstr.exe ou une de ses dépendances est introuvable, vérifiez que vos chemins sont correctement configurés, comme décrit à l’étape 2.  
  
4.  Configurez le serveur de symboles en définissant votre variable **_NT_SYMBOL_PATH** sur **symsrv\*symsrv.dll\*c:\localcache\*http://msdl.microsoft.com/download/symbols**  
  
5.  Après avoir configuré votre serveur de symboles avec les variables d’environnement système, exécutez les outils du profileur en ligne de commande à une nouvelle invite de commandes. Les nouvelles variables d’environnement sont ainsi prises en compte. Dans la fenêtre d’invite de commandes, tapez la commande suivante :  
  
     **start %COMSPEC%**  
  
    > [!NOTE]
    >  Pour obtenir des instructions détaillées sur la façon de configurer le package du serveur de symboles, consultez [Guide pratique pour référencer les informations de symboles Windows](../profiling/how-to-reference-windows-symbol-information.md).  
  
6.  Utilisez l’outil [VSPerfReport](../profiling/vsperfreport.md) pour sérialiser vos symboles dans le fichier de profilage de données (.vsp). Utilisez les commutateurs **VSPerfReport /summary:all /packsymbols**. Si aucun symbole n’est inséré dans votre fichier de données, vérifiez que la variable d’environnement _NT_SYMBOL_PATH est définie.  
  
## <a name="see-also"></a>Voir aussi  
 [Profilage à partir de la ligne de commande](../profiling/using-the-profiling-tools-from-the-command-line.md)   
 [Procédure pas à pas : profilage de la ligne de commande à l’aide de l’échantillonnage](../profiling/walkthrough-command-line-profiling-using-sampling.md)   
 [Procédure pas à pas : profilage de la ligne de commande à l’aide de l’instrumentation](../profiling/walkthrough-command-line-profiling-using-instrumentation.md)   
 [Guide pratique pour référencer les informations de symboles Windows](../profiling/how-to-reference-windows-symbol-information.md)   
 [VSPerfReport](../profiling/vsperfreport.md)