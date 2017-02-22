---
title: "VSPerf | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b5854e62-279e-4850-bfeb-0c6ef82f4805
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# VSPerf
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Utilisez l'outil de ligne de commande **VsPerf** :  
  
1.  Les fenêtres de profil stockent les applications de ligne de commande lorsque Visual Studio n'est pas installé sur le périphérique.  
  
2.  Profilez les Applications de Bureau Windows 8 et les applications Windows Server 2012 à l'aide de la méthode de profilage de l'échantillonnage.  
  
 Pour plus d'informations sur vos options de profilage, consultez [Profilage d'applications Windows 8 et Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
##  <a name="BKMK_In_this_topic"></a> Dans cette rubrique  
 Cette rubrique décrit les options que vous pouvez utiliser avec l'outil de ligne de commande de `vsperf.exe`.  La rubrique contient les sections suivantes :  
  
 [Applications de Windows Store seulement](#BKMK_windows_store_apps_only)  
  
 [Applications de Bureau Windows 8 et Applications Windows Server 2012 seulement](#BKMK_Windows_8_classic_applications_and_Windows_Server_2012_applications_only)  
  
 [Toutes les applications](#BKMK_All_applications)  
  
##  <a name="BKMK_windows_store_apps_only"></a> Applications de Windows Store seulement  
 Ces options s'appliquent uniquement aux applications du Windows Store  
  
|||  
|-|-|  
|**\/app:{AppName}**|Démarre le Générateur de profils et attend l'application spécifiée à partir du menu Démarrer<br /><br /> Exécutez `vsperf /listapps` pour afficher le nom de l'application et le PackageFullName des applications installées.|  
|**\/package:{PackageFullName}**|Démarre le Générateur de profils et attend l'application spécifiée à partir du menu Démarrer<br /><br /> Exécutez `vsperf /listapps` pour afficher le nom de l'application et le PackageFullName des applications installées.|  
|**\/js**|Requis pour profiler les applications JavaScript.<br /><br /> Regrouper des données de performances des applications JavaScript.<br /><br /> Utilisez uniquement avec \/package ou \/attach.|  
|**\/noclr**|Optionnel.  Ne collecte pas des données CLR.<br /><br /> Utilisez uniquement avec \/package ou \/attach.<br /><br /> Optimisation, aucun symbole géré ne sera résolu.|  
|**\/listapps**|Liste les noms des applications installées et PakageFullNames.|  
  
##  <a name="BKMK_Windows_8_classic_applications_and_Windows_Server_2012_applications_only"></a> Applications de Bureau Windows 8 et Applications Windows Server 2012 seulement  
 Ces options ne fonctionnent pas pour les applications du Windows Store.  
  
|||  
|-|-|  
|**\/launch:{Executable}**|Démarre et commence le profilage de l'exécutable spécifié.|  
|**\/args:{ExecutableArguments}**|Spécifie les arguments de ligne de commande pour passer la cible **\/launch**.|  
|**\/console**|Exécute la cible **\/launch** dans une nouvelle fenêtre de commande.|  
  
##  <a name="BKMK_All_applications"></a> Toutes les applications  
 Ces options s'appliquent à toute application Windows 8 ou application Windows Server 2012.  
  
|||  
|-|-|  
|**\/attach:{PID&#124;ProcessName}\[,PID&#124;ProcessName\]...**|Collecte des données à partir des processus spécifiés.<br /><br /> Utilisez le Gestionnaire des tâches pour afficher l'ID de processus \(PID\) et traiter des noms des applications en cours de exécution.|  
|**\/file:{ReportName}**|Optionnel.  Spécifie le fichier de sortie \(remplace un fichier existant\).<br /><br /> Utilisez uniquement avec \/package ou \/attach.|  
|**\/pause**|Collecte de données de pause.|  
|**\/resume**|Collecte de données de synthèse.|  
|**\/stop**|Arrête la collecte des données et les processus cibles.|  
|**\/detach**|Arrête la collecte des données, mais poursuivre l'exécution des processus cibles.|  
|**\/status**|Afficher l'état du Générateur de profils.|  
  
## Voir aussi  
 [Profilage d'applications Windows 8 et Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)   
 [Profilage à partir de la ligne de commande](../profiling/using-the-profiling-tools-from-the-command-line.md)