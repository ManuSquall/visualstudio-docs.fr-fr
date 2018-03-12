---
title: VSPerf | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b5854e62-279e-4850-bfeb-0c6ef82f4805
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: ea6214987e12b8c5cf7e563b666822989d3a7015
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="vsperf"></a>VSPerf
Utilisez l’outil en ligne de commande **VsPerf** pour :  
  
1.  Profiler des applications UWP à partir de la ligne de commande quand Visual Studio n’est pas installé sur l’appareil.  
  
2.  Profiler des applications de bureau Windows 8 et des applications Windows Server 2012 à l’aide de la méthode de profilage par échantillonnage.  
  
 Pour plus d’informations sur les options de profilage, consultez [Outils d’analyse des performances sur les applications Windows 8 et Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
##  <a name="BKMK_In_this_topic"></a> Dans cette rubrique  
 Cette rubrique décrit les options que vous pouvez utiliser avec l’outil en ligne de commande `vsperf.exe`. La rubrique contient les sections suivantes :  
  
 [Applications UWP uniquement](#BKMK_windows_store_apps_only)  
  
 [Applications de bureau Windows 8 et applications Windows Server 2012 uniquement](#BKMK_Windows_8_classic_applications_and_Windows_Server_2012_applications_only)  
  
 [Toutes les applications](#BKMK_All_applications)  
  
##  <a name="BKMK_windows_store_apps_only"></a> Applications UWP uniquement  
 Ces options s’appliquent uniquement aux applications UWP.  
  
|||  
|-|-|  
|**/app:{nom_application}**|Démarre le profileur et attend que l’application spécifiée soit lancée à partir du menu Démarrer.<br /><br /> Exécutez `vsperf /listapps` pour afficher le nom d’application et le nom complet du package des applications installées.|  
|**/package:{nom complet du package}**|Démarre le profileur et attend que l’application spécifiée soit lancée à partir du menu Démarrer.<br /><br /> Exécutez `vsperf /listapps` pour afficher le nom d’application et le nom complet du package des applications installées.|  
|**/js**|Obligatoire pour le profilage d’applications JavaScript.<br /><br /> Collecte les données de performances à partir des applications JavaScript.<br /><br /> Utilisez uniquement avec /package ou /attach.|  
|**/noclr**|Facultatif. Ne collecte pas de données CLR.<br /><br /> Utilisez uniquement avec /package ou /attach.<br /><br /> Optimisation ; aucune résolution de symbole managé.|  
|**/listapps**|Liste les noms et les noms complets de packages des applications installées.|  
  
##  <a name="BKMK_Windows_8_classic_applications_and_Windows_Server_2012_applications_only"></a> Applications de bureau Windows 8 et applications Windows Server 2012 uniquement  
 Ces options ne fonctionnent pas sur les applications UWP.  
  
|||  
|-|-|  
|**/launch:{exécutable}**|Démarre et commence le profilage du fichier exécutable spécifié.|  
|**/args:{arguments_exécutable}**|Spécifie les arguments de ligne de commande à passer à la cible de **/launch**.|  
|**/console**|Exécute la cible **/launch** dans une nouvelle fenêtre de commande.|  
  
##  <a name="BKMK_All_applications"></a>Toutes les applications  
 Ces options s’appliquent à toutes les applications Windows 8 ou Windows Server 2012.  
  
|||  
|-|-|  
|**/attach:{PID&#124;nom_processus}[,PID&#124;nom_processus]...**|Collecte les données des processus spécifiés.<br /><br /> Utilisez le Gestionnaire des tâches pour afficher l’ID de processus (PID) et les noms de processus des applications en cours d’exécution.|  
|**/file:{nom_rapport}**|Facultatif. Spécifie le fichier de sortie (écrase le fichier existant).<br /><br /> Utilisez uniquement avec /package ou /attach.|  
|**/pause**|Suspendre la collecte de données.|  
|**/resume**|Reprendre la collecte de données.|  
|**/stop**|Arrêter la collecte de données et terminer les processus cibles.|  
|**/detach**|Arrêter la collecte de données, sans interrompre l’exécution des processus cibles.|  
|**/status**|Afficher l’état du profileur.|  
  
## <a name="see-also"></a>Voir aussi  
 [Outils d’analyse des performances sur les applications Windows 8 et Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)   
 [Profilage à partir de la ligne de commande](../profiling/using-the-profiling-tools-from-the-command-line.md)