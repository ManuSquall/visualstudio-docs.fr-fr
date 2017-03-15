---
title: "Profilage sur des clusters&#160;HPC (High Performance Computing) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.hpc.wizard.exeoptions"
  - "vs.performance.hpc.wizard.summary"
  - "vs.performance.hpc.wizard.startoptions"
  - "vs.performance.hpc.wizard.intro"
  - "vs.performance.hpc.property.basic"
  - "vs.performance.hpc.wizard.application"
  - "vs.performance.hpc.wizard.clusteroptions"
  - "vs.performance.hpc.property.advanced"
helpviewer_keywords: 
  - "outils de profilage, HPC"
  - "profilage HPC"
ms.assetid: 1525bbdb-27da-4088-8487-a486cee5e7b3
caps.latest.revision: 22
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 22
---
# Profilage sur des clusters&#160;HPC (High Performance Computing)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Vous pouvez profiler sur des nœuds de calcul de clusters Microsoft Windows HPC à l'aide de la méthode d'échantillonnage des outils de profilage [!INCLUDE[vsPreExt](../profiling/includes/vspreext_md.md)] ou [!INCLUDE[vsUltExt](../profiling/includes/vsultext_md.md)].  Pour plus d'informations sur HPC, consultez [Windows HPC](http://go.microsoft.com/fwlink/?LinkId=165393) sur le site web de Microsoft.  
  
## Configuration requise  
 Pour profiler sur un nœud de calcul HPC, vous devez effectuer les opérations suivantes :  
  
-   Installez Microsoft HPC Pack 2008 sur le même ordinateur que [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)].  L'ordinateur ne doit pas nécessairement faire partie du cluster HPC.  Vous pouvez installer l'application HPC depuis le [Centre de téléchargement Microsoft](http://go.microsoft.com/fwlink/?LinkID=177414).  
  
-   Installez le [!INCLUDE[net_v40_long](../profiling/includes/net_v40_long_md.md)] et la version autonome des outils de profilage sur le nœud de calcul HPC.  Les programmes d'installation pour [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] et le profileur autonome sont disponibles sur le support d'installation [!INCLUDE[vsPreShort](../code-quality/includes/vspreshort_md.md)].  **Remarque** Vous devez redémarrer le calcul après avoir installé [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] et avant que vous n'installiez les outils de profilage.  
  
 Pour installer le [!INCLUDE[net_v40_long](../profiling/includes/net_v40_long_md.md)] et les outils de profilage autonomes sur un nœud de calcul HPC actif et activer le profilage sur l'ordinateur de cluster, suivez ces étapes :  
  
1.  Ouvrez la fenêtre d'invite de commandes installée avec le HPC Pack.  
  
2.  Aux invites de commandes distinctes, tapez les commandes suivantes :  
  
    1.  `clusrun /all /scheduler:` *%HeadNode% %FxPath%* `/q /norestart`  
  
    2.  `clusrun /all /scheduler:` *%HeadNode%* `shutdown /r /t 0 /d u:4:2 /c "Microsoft .NET Framework install required restart"`  
  
    3.  `clusrun /all /scheduler:` *%HeadNode% %ProfilerPath%* `/q /norestart`  
  
|||  
|-|-|  
|*%HeadNode%*|Nom du nœud principal pour le cluster.|  
|*%FxPath%*|Chemin d'accès au programme d'installation de [!INCLUDE[net_v40_long](../profiling/includes/net_v40_long_md.md)].  Sur le média d'installation de [!INCLUDE[vsPreShort](../code-quality/includes/vspreshort_md.md)], le chemin d'accès est : WCU\\dotNetFramework\\dotNetFx40\_Full\_x86\_x64.exe|  
|*%ProfilerPath%*|Chemin d'accès à la version autonome du programme d'installation des outils de profilage.  Sur le média d'installation de [!INCLUDE[vsPreShort](../code-quality/includes/vspreshort_md.md)], le chemin d'accès est : Standalone Profiler\\x64\\vs\_profiler.exe|  
  
## Profilage sur un nœud de calcul HPC  
 Vous configurez une session de profilage en utilisant l'Assistant Performance HPC pour spécifier le cluster HPC et les informations cible.  Vous pouvez définir des options supplémentaires dans les pages de propriétés de session de performance.  Les outils de profilage déploient automatiquement les fichiers binaires cible nécessaires et démarrent le profileur et l'application HPC.  
  
#### Pour profiler sur un nœud de calcul HPC  
  
1.  Dans le menu **Analyser**, cliquez sur **Démarrer l'Assistant Performance HPC**.  Si la commande n'est pas disponible, assurez\-vous que vous disposez des composants requis répertoriés plus haut.  
  
2.  Cliquez sur **Suivant** sur la première page de l'Assistant.  
  
3.  Sur la deuxième page de l'Assistant, sélectionnez l'application que vous souhaitez profiler.  
  
    -   Pour profiler un projet actuellement ouvert dans [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)], sélectionnez l'option **Un ou plusieurs projets disponibles**, puis sélectionnez le nom du projet dans la liste.  
  
    -   Pour profiler un binaire qui ne se trouve pas dans un projet ouvert, sélectionnez l'option **Exécutable \(fichier .EXE\)**.  
  
4.  Cliquez sur **Suivant**.  
  
5.  Dans la troisième page de l'Assistant :  
  
    -   Si vous profilez un exécutable qui ne se trouve pas dans un projet ouvert, spécifiez le chemin d'accès au fichier binaire dans **Quel est le chemin d'accès complet à l'exécutable**.  
  
    -   Si vous profilez un exécutable qui ne se trouve pas dans un projet ouvert, vous pouvez spécifier tout argument de ligne de commande à passer au processus dans **Arguments de ligne de commande**.  
  
    -   Dans **Répertoire de travail distant**, spécifiez le chemin d'accès au dossier utilisé par les instances de processus sur chaque nœud de calcul.  
  
    -   Dans **Emplacement de déploiement**, spécifiez le chemin d'accès au répertoire utilisé par le serveur HPC pour organiser des images pour le déploiement.  
  
6.  Cliquez sur **Suivant**.  
  
7.  Sur la quatrième page de l'Assistant :  
  
    -   Dans la liste **Nœud principal**, cliquez sur l'ordinateur qui joue le rôle de nœud principal HPC dans l'exécution du profilage.  Le nœud principal peut être « localhost », qui vous permet de profiler sur l'ordinateur local sans nécessiter de cluster.  
  
    -   Dans la liste **Nombre de processus**, cliquez sur le nombre d'instances de l'application à exécuter.  
  
    -   Dans la liste **Options de profilage**, sélectionnez la cible de profilage.  
  
         Pour profiler un processus spécifique dans le cluster, sélectionnez l'option **Profil sur le rang**, puis sélectionnez le rang du processus dans la liste déroulante.  
  
         Pour profiler le ou les processus exécutés sur un nœud spécifique du cluster HPC, sélectionnez l'option **Profil sur le nœud**, puis choisissez le nœud dans la liste déroulante.  
  
8.  Cliquez sur **Suivant**.  
  
9. Sur la cinquième page de l'Assistant, vous pouvez choisir de démarrer immédiatement le profileur et le processus de profilage ou de démarrer le profilage ultérieurement à l'aide de l'Explorateur de performances.  
  
    -   Sélectionnez **Lancer le profilage une fois l'Assistant terminé** pour démarrer immédiatement le profilage, ou désactivez la case à cocher pour démarrer le profilage manuellement.  
  
10. Cliquez sur **Terminer**.  
  
## Définition des propriétés de profilage HPC à l'aide des pages de propriétés de session de performance  
 Vous pouvez modifier les propriétés de session de performance définies dans l'Assistant de profilage HPC sur la page Propriétés de lancement HPC de la page de propriétés de session de performance.  Vous définissez des options supplémentaires sur la page Propriétés avancées HPC.  
  
#### Pour ouvrir les pages de propriétés de session de performance  
  
1.  Si nécessaire, ouvrez le fichier session de performance \(.psess\) dans l'Explorateur de performances.  Dans le menu **Fichier**, cliquez sur **Ouvrir**, puis localisez le fichier.  
  
2.  Dans l'Explorateur de performances, cliquez avec le bouton droit sur le nom de la session de performance, puis cliquez sur **Propriétés**.  
  
3.  Dans la boîte de dialogue Pages de propriétés, utilisez l'une des méthodes suivantes :  
  
    -   Cliquez sur **Général**, puis sélectionnez **Collecter sur le cluster HPC** pour activer le profilage HPC ou désactivez la case à cocher pour désactiver le profilage HPC.  
  
    -   Cliquez sur **Propriétés de lancement HPC** pour modifier les propriétés qui démarrent l'application HPC.  
  
    -   Cliquez sur **Propriétés avancées HPC** pour définir des options supplémentaires.  
  
### Propriétés de lancement HPC  
  
|Propriété|Description|  
|---------------|-----------------|  
|**Nœud principal**|Spécifie l'ordinateur qui joue le rôle de nœud principal HPC dans l'exécution du profilage.|  
|**Nombre de processus**|Spécifie le nombre d'instances de l'application à exécuter dans l'application profilée.|  
|**Profil sur le rang**|Pour profiler un processus spécifique dans le cluster, sélectionnez l'option **Profil sur le rang**, puis sélectionnez le rang du processus dans la liste déroulante.|  
|**Profil sur le nœud**|Pour profiler le ou les processus exécutés sur un nœud spécifique du cluster HPC, sélectionnez l'option **Profil sur le nœud**, puis choisissez le nœud dans la liste déroulante.|  
|**Répertoire de travail distant**|Spécifie le chemin d'accès au dossier utilisé par les instances de processus sur chaque nœud de calcul.|  
|**Emplacement de déploiement**|Spécifie le chemin d'accès au répertoire utilisé par le serveur HPC pour organiser des images pour le déploiement.|  
  
### Propriétés avancées  
  
|Propriété|Description|  
|---------------|-----------------|  
|**Nom du projet**|Nom du projet ou de la solution [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] actuel\(le\).|  
|**Nettoyer après l'arrêt du profileur**|Avec la valeur True, supprime les binaires déployés dans le répertoire d'exécution.  Les fichiers et répertoires créés par le programme utilisateur ne sont pas supprimés dans cette étape.  Si le répertoire d'exécution et le répertoire de déploiement ont été créés par l'IDE, ce dernier tente de les supprimer mais il n'effectue aucune suppression s'ils contiennent des fichiers non déployés par l'IDE.|  
|**Fichiers supplémentaires à déployer**|Spécifie une liste de tous les fichiers supplémentaires à déployer sur le nœud de calcul séparés par des points\-virgules.  Vous pouvez cliquer sur le bouton de sélection \(**...**\) pour sélectionner plusieurs fichiers à l'aide d'une boîte de dialogue.|  
|**Commande Mpiexec**|Spécifie l'application qui démarre l'application MPI.  La valeur par défaut est **mpiexec.exe**.|  
|**Arguments Mpiexec**|Spécifie les arguments à passer à la commande mpiexec.exe.|  
|**Nœuds requis sur le cluster**|Spécifie le nombre de nœuds sur le cluster sur lequel l'application doit être exécutée.|  
|**Déployer les fichiers CRT**|Avec la valeur True, déploie le Runtime C\/C\+\+ sur le cluster.|  
|**Script de préprofilage**|Spécifie le chemin d'accès et le nom de fichier d'un script à exécuter sur l'ordinateur de développement local avant le démarrage de la session de profilage.|  
|**Arguments de script de préprofilage**|Spécifie les arguments à passer au script de préprofilage.|  
|**Script de post\-profilage**|Spécifie le chemin d'accès et le nom de fichier d'un script à exécuter sur l'ordinateur de développement local à la fin de la session de profilage.|  
|**Arguments de script de post\-profilage**|Spécifie les arguments à passer au script de post\-profilage.|