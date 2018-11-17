---
title: Profilage sur des clusters HPC (High Performance Computing) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.hpc.wizard.exeoptions
- vs.performance.hpc.wizard.summary
- vs.performance.hpc.wizard.startoptions
- vs.performance.hpc.wizard.intro
- vs.performance.hpc.property.basic
- vs.performance.hpc.wizard.application
- vs.performance.hpc.wizard.clusteroptions
- vs.performance.hpc.property.advanced
helpviewer_keywords:
- profililng tools,HPC
- HPC profiling
ms.assetid: 1525bbdb-27da-4088-8487-a486cee5e7b3
caps.latest.revision: 27
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f6b0838a7fb3db86290647fadec9ca3572cbdf90
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51809153"
---
# <a name="profiling-on-hpc-high-performance-computing-clusters"></a>Profilage sur des clusters HPC (High Performance Computing)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez profiler sur des nœuds de calcul de clusters Microsoft Windows HPC à l’aide de la méthode d’échantillonnage des outils de profilage [!INCLUDE[vsPreExt](../includes/vspreext-md.md)] ou [!INCLUDE[vsUltExt](../includes/vsultext-md.md)]. Pour plus d’informations sur HPC, consultez [Windows HPC](http://go.microsoft.com/fwlink/?LinkId=165393) sur le site web de Microsoft.  
  
## <a name="prerequisites"></a>Prérequis  
 Pour effectuer un profilage sur un nœud de calcul HPC, vous devez effectuer les opérations suivantes :  
  
- Installez Microsoft HPC Pack 2008 sur le même ordinateur que [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)]. L’ordinateur ne doit pas nécessairement faire partie du cluster HPC. Vous pouvez installer HPC Pack à partir du [Centre de téléchargement Microsoft ](http://go.microsoft.com/fwlink/?LinkID=177414).  
  
- Installez [!INCLUDE[net_v40_long](../includes/net-v40-long-md.md)] et la version autonome des outils de profilage sur le nœud de calcul HPC. Les programmes d’installation de [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] et du profileur autonome sont tous les deux disponibles sur le support d’installation de [!INCLUDE[vsPreShort](../includes/vspreshort-md.md)]. **Remarque** : Vous devez redémarrer l’ordinateur après avoir installé [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] et avant d’installer les outils de profilage.  
  
  Pour installer [!INCLUDE[net_v40_long](../includes/net-v40-long-md.md)] et les outils de profilage autonomes sur un calcul nœud HPC actif et activer le profilage sur l’ordinateur en cluster, effectuez les étapes suivantes :  
  
1.  Ouvrez la fenêtre d’invite de commandes installée avec HPC Pack.  
  
2.  Dans des invites de commandes distinctes, tapez les commandes suivantes :  
  
    1.  `clusrun /all /scheduler:` *%HeadNode% %FxPath%* `/q /norestart`  
  
    2.  `clusrun /all /scheduler:` *%HeadNode%* `shutdown /r /t 0 /d u:4:2 /c "Microsoft .NET Framework install required restart"`  
  
    3.  `clusrun /all /scheduler:` *%HeadNode% %ProfilerPath%* `/q /norestart`  
  
|||  
|-|-|  
|*%HeadNode%*|Nom du nœud principal du cluster.|  
|*%FxPath%*|Chemin du programme d’installation de [!INCLUDE[net_v40_long](../includes/net-v40-long-md.md)]. Sur le support d’installation de [!INCLUDE[vsPreShort](../includes/vspreshort-md.md)], le chemin est le suivant : WCU\dotNetFramework\dotNetFx40_Full_x86_x64.exe|  
|*%ProfilerPath%*|Chemin de la version autonome du programme d’installation des outils de profilage. Sur le média d’installation de [!INCLUDE[vsPreShort](../includes/vspreshort-md.md)], le chemin est le suivant : Standalone Profiler\x64\vs_profiler.exe|  
  
## <a name="profiling-on-an-hpc-compute-node"></a>Profilage sur un nœud de calcul HPC  
 Pour configurer une session de profilage, spécifiez le cluster HPC et les informations cibles à l’aide de l’Assistant Performance HPC. Vous pouvez définir des options supplémentaires dans les pages de propriétés de session de performance. Les outils de profilage déploient automatiquement les fichiers binaires cibles nécessaires. Ils démarrent également le profileur et l’application HPC.  
  
#### <a name="to-profile-on-an-hpc-compute-node"></a>Pour effectuer un profilage sur un nœud de calcul HPC  
  
1.  Dans le menu **Analyser**, cliquez sur **Démarrer l’Assistant Performance HPC**. Si la commande n’est pas disponible, vérifiez que vous disposez des prérequis répertoriés ci-dessus.  
  
2.  Cliquez sur **Suivant** dans la première page de l’Assistant.  
  
3.  Dans la deuxième page de l’Assistant, sélectionnez l’application que vous voulez profiler.  
  
    -   Pour profiler un projet actuellement ouvert dans [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)], sélectionnez l’option **Un ou plusieurs projets disponibles**, puis sélectionnez le nom du projet dans la liste.  
  
    -   Pour profiler un fichier binaire qui ne se trouve pas dans un projet ouvert, sélectionnez l’option **Exécutable (fichier .EXE)**.  
  
4.  Cliquez sur **Suivant**.  
  
5.  Dans la troisième page de l’Assistant :  
  
    -   Si vous profilez un exécutable qui ne se trouve pas dans un projet ouvert, spécifiez le chemin du fichier binaire dans **Quel est le chemin d’accès complet à l’exécutable**.  
  
    -   Si vous profilez un exécutable qui ne se trouve pas dans un projet ouvert, vous pouvez spécifier tout argument de ligne de commande à passer au processus dans **Arguments de ligne de commande**.  
  
    -   Dans **Répertoire de travail distant**, spécifiez le chemin du dossier utilisé par les instances de processus sur chacun des nœuds de calcul.  
  
    -   Dans **Emplacement de déploiement**, spécifiez le chemin du répertoire utilisé par le serveur HPC pour organiser des images pour le déploiement.  
  
6.  Cliquez sur **Suivant**.  
  
7.  Dans la quatrième page de l’Assistant :  
  
    -   Dans la liste **Nœud principal**, cliquez sur l’ordinateur qui joue le rôle du nœud principal HPC dans l’exécution du profilage. Le nœud principal peut être « localhost », ce qui vous permet d’effectuer le profilage sur l’ordinateur local sans avoir besoin d’un cluster.  
  
    -   Dans la liste **Nombre de processus**, cliquez sur le nombre d’instances de l’application à exécuter.  
  
    -   Dans la liste **Options de profilage**, sélectionnez la cible de profilage.  
  
         Pour profiler un processus spécifique dans le cluster, sélectionnez l’option **Profil sur le rang**, puis sélectionnez le rang du processus dans la liste déroulante.  
  
         Pour profiler le ou les processus exécutés sur un nœud spécifique du cluster HPC, sélectionnez l’option **Profil sur le nœud**, puis sélectionnez le nœud dans la liste déroulante.  
  
8.  Cliquez sur **Next**.  
  
9. Dans la cinquième page de l’Assistant, vous pouvez choisir de démarrer immédiatement le profileur et le processus de profilage, ou de démarrer le profilage ultérieurement à l’aide de l’Explorateur de performances.  
  
    -   Cochez la case **Lancer le profilage une fois l’Assistant terminé** pour démarrer immédiatement le profilage, ou décochez-la pour démarrer le profilage manuellement.  
  
10. Cliquez sur **Terminer**.  
  
## <a name="setting-hpc-profiling-properties-by-using-performance-session-property-pages"></a>Définition des propriétés de profilage HPC à l’aide des pages de propriétés d’une session de performance  
 Pour modifier les propriétés de session de performance définies dans l’Assistant de profilage HPC, utilisez la page Propriétés de lancement HPC de la page de propriétés de session de performance. Vous définissez des options supplémentaires dans la page Propriétés avancées HPC.  
  
#### <a name="to-open-the-performance-session-property-pages"></a>Pour ouvrir les pages de propriétés de session de performance  
  
1.  Si nécessaire, ouvrez le fichier de session de performance (.psess) dans l’Explorateur de performances. Dans le menu **Fichier**, cliquez sur **Ouvrir**, puis recherchez le fichier.  
  
2.  Dans l’Explorateur de performances, cliquez avec le bouton droit sur le nom de la session de performance, puis cliquez sur **Propriétés**.  
  
3.  Dans la boîte de dialogue Pages de propriétés, utilisez l’une des méthodes suivantes :  
  
    -   Cliquez sur **Général**, puis cochez la case à cocher **Collecter sur le cluster HPC** pour activer le profilage HPC ou décochez-la pour désactiver le profilage HPC.  
  
    -   Cliquez sur **Propriétés de lancement HPC** pour modifier les propriétés qui démarrent l’application HPC.  
  
    -   Cliquez sur **Propriétés avancées HPC** pour définir des options supplémentaires.  
  
### <a name="hpc-launch-properties"></a>Propriétés de lancement HPC  
  
|Propriété|Description|  
|--------------|-----------------|  
|**Nœud principal**|Spécifie l’ordinateur qui joue le rôle du nœud principal HPC dans l’exécution du profilage.|  
|**Nombre de processus**|Spécifie le nombre d’instances de l’application à exécuter dans l’application profilée.|  
|**Profil sur le rang**|Pour profiler un processus spécifique dans le cluster, sélectionnez l’option **Profil sur le rang**, puis sélectionnez le rang du processus dans la liste déroulante.|  
|**Profil sur le nœud**|Pour profiler le ou les processus exécutés sur un nœud spécifique du cluster HPC, sélectionnez l’option **Profil sur le nœud**, puis sélectionnez le nœud dans la liste déroulante.|  
|**Répertoire de travail distant**|Spécifie le chemin du dossier utilisé par les instances de processus sur chacun des nœuds de calcul.|  
|**Emplacement de déploiement**|Spécifie le chemin du répertoire utilisé par le serveur HPC pour organiser des images pour le déploiement.|  
  
### <a name="advanced-properties"></a>Propriétés avancées  
  
|Propriété|Description|  
|--------------|-----------------|  
|**Nom du projet**|Nom du projet ou de la solution [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] actuels.|  
|**Nettoyer après l’arrêt du profileur**|Quand la valeur est true, supprime les fichiers binaires déployés dans le répertoire d’exécution. Les fichiers et répertoires créés par le programme utilisateur ne sont pas supprimés au cours de cette étape. Si le répertoire d’exécution et le répertoire de déploiement ont été créés par l’IDE, ce dernier tente de les supprimer. Cependant, il n’effectue aucune suppression si ces répertoires contiennent des fichiers qu’il n’a pas déployés.|  
|**Fichiers supplémentaires à déployer**|Spécifie une liste séparée par des points-virgules de tous les fichiers supplémentaires à déployer sur le nœud de calcul. Vous pouvez cliquer sur le bouton de sélection (**...** ) pour sélectionner plusieurs fichiers à l’aide d’une boîte de dialogue.|  
|**Commande Mpiexec**|Spécifie l’application qui démarre l’application MPI. La valeur par défaut est **mpiexec.exe**.|  
|**Arguments Mpiexec**|Spécifie les arguments à passer à la commande mpiexec.exe.|  
|**Nœuds demandés sur le cluster**|Spécifie le nombre de nœuds sur le cluster sur lequel l’application doit être exécutée.|  
|**Déployer les fichiers CRT**|Si la valeur est true, déploie le Runtime C/C++ sur le cluster.|  
|**Script de préprofilage**|Spécifie le chemin et le nom de fichier d’un script à exécuter sur l’ordinateur de développement local avant le démarrage de la session de profilage.|  
|**Arguments de script de préprofilage**|Spécifie les arguments à passer au script de préprofilage.|  
|**Script de post-profilage**|Spécifie le chemin et le nom de fichier d’un script à exécuter sur l’ordinateur de développement local à la fin de la session de profilage.|  
|**Arguments de script de post-profilage**|Spécifie les arguments à passer au script de post-profilage.|



