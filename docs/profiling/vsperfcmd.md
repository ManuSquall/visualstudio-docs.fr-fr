---
title: VSPerfCmd | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- performance tools, VSPerfCmd tool
- command-line tools, VSPerfCmd tool
- command line, tools
- profiling tools,VSPerfCmd
- VSPerfCmd tool
ms.assetid: 778bc105-7643-46c4-a338-f3620e31125a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fb43d8378a884631a487259c9c5e4d9384194258
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/26/2019
ms.locfileid: "55070836"
---
# <a name="vsperfcmd"></a>VSPerfCmd
L’outil *VSPerfCmd.exe* est utilisé pour démarrer et arrêter la collecte de données de performances. Il utilise la syntaxe suivante :  
  
```cmd  
VSPerfCmd [/U] [/options]  
```  
  
 Les tableaux suivants décrivent les options de l’outil *VSPerfCmd.exe*.  
  
|Option|Description|  
|------------|-----------------|  
|**U**|La sortie redirigée de la console est écrite au format Unicode. Doit être la première option spécifiée.|  
|[Start](../profiling/start.md) **:** `mode`|Démarre le service de profilage dans le mode spécifié.|  
|[Output](../profiling/output.md) **:** `filename`|Spécifie le nom du fichier de sortie. À utiliser uniquement avec **Start**.|  
|[CrossSession&#124;CS](../profiling/crosssession.md)|Active le profilage entre des sessions Windows. À utiliser seulement avec **Start**, **Attach** ou **Launch**.|  
|[User](../profiling/user-vsperfcmd.md) **:**[`domain\`]`username`|Permet au compte spécifié d’accéder au service du profileur. À utiliser uniquement avec **Start**.|  
|[WaitStart](../profiling/waitstart.md)[**:**`n`]|Attend que le journal de collecte de données soit initialisé. Si `n` est spécifié, **VSPerfCmd** attend au plus `n` secondes. Si `n` n’est pas spécifié, **VSPerfCmd** attend indéfiniment. Ceci facilite l’utilisation de **VSPerfCmd** dans le cadre d’un traitement par lots.|  
|[Counter](../profiling/counter.md) **:** `cfg`|Quand l’exemple de méthode de profilage par échantillonnage est utilisée, spécifie un compteur d’UC et le nombre d’événements à utiliser comme intervalle d’échantillonnage. Vous ne pouvez échantillonner qu’une seule valeur de compteur.<br /><br /> Quand la méthode de profilage par instrumentation est utilisée, spécifie un compteur d’UC à collecter à chaque point d’instrumentation. À utiliser seulement avec **Start**`Trace`, **Attach** ou **Launch**.|  
|[QueryCounters](../profiling/querycounters.md)|Affiche une liste des compteurs d’UC valides pour la machine active.|  
|[WinCounter](../profiling/wincounter.md) **:** *path*|Spécifie un événement de compteur de performance Windows à inclure avec les données de marque du profil. À utiliser uniquement avec **Start**.|  
|[AutoMark](../profiling/automark.md)  **:** *n*|Spécifie l’intervalle de temps (en millisecondes) entre les événements de collecte des données du compteur de performances Windows. À utiliser avec **WinCounter**.|  
|[Events](../profiling/events-vsperfcmd.md) **:** `option`|Contrôle la collecte des événements de suivi d’événements pour Windows (ETW) spécifiés. Les données ETW sont collectées dans un fichier .*itl* qui n’est pas le fichier de données de profilage (.*vsp*).|  
|[État](../profiling/status.md)|Affiche l’état du profileur, des informations sur les processus qui sont en cours de profilage et les comptes qui sont autorisés à contrôler le profileur.|  
|[Shutdown](../profiling/shutdown.md)[**:**`n`]|Ferme le fichier de données de profilage et désactive le profileur.|  
|[GlobalOn](../profiling/globalon-and-globaloff.md)|Reprend la collecte de données après un appel à **VSPerfCmdGlobalOff**.|  
|[GlobalOff](../profiling/globalon-and-globaloff.md)|Arrête complètement la collecte de données, mais ne met pas fin à la session de profilage.|  
|[ProcessOn](../profiling/processon-and-processoff.md) **:** `pid`|Reprend la collecte de données pour le processus spécifié après la mise en suspens du profilage via un appel à **VSPerfCmdProcessOff**.|  
|[ProcessOff](../profiling/processon-and-processoff.md) **:** `pid`|Arrête la collecte de données pour le processus spécifié.|  
|[ThreadOn et ThreadOff](../profiling/threadon-and-threadoff.md) **:** *tid*|Reprend le profilage pour le processus spécifié après la mise en suspens du profilage par un appel à **VSPerfCmdThreadOff**. Utilisez **ThreadOn** seulement en cas de profilage avec la méthode d’instrumentation.|  
|[ThreadOn et ThreadOff](../profiling/threadon-and-threadoff.md) **:** *tid*|Suspend le profilage pour le thread spécifié. Utilisez **ThreadOff** seulement en cas de profilage avec la méthode d’instrumentation.|  
|[Mark](../profiling/mark.md) **:** _MarkNum_[**,**_MarkText_**]**|Insère une marque dans le fichier de données de profilage, avec un texte facultatif.|  
  
## <a name="sample-method-options"></a>Options de méthode d’échantillonnage  
 Les options suivantes sont disponibles seulement quand vous utilisez la méthode de profilage par échantillonnage.  
  
|Option|Description|  
|------------|-----------------|  
|[Launch](../profiling/launch.md) **:** *Exécutable*|Démarre l’application spécifiée et démarre le profileur.|  
|[Args](../profiling/args.md) **:** *Arguments*|Spécifie les arguments de ligne de commande à passer à l’application lancée.|  
|[Console](../profiling/console.md)|Démarre la commande spécifiée dans une nouvelle fenêtre d’invite de commandes.|  
|[Attach](../profiling/attach.md) **:** *PID*[**,**_PID_]|Démarre le profilage des processus spécifiés. Vous pouvez identifier les processus par ID de processus ou par nom de processus.|  
|[Detach](../profiling/detach.md)[**:**_PID_[,_PID_]]|Arrête le profilage des processus spécifiés. Vous pouvez identifier les processus par ID de processus ou par nom de processus. Si aucun processus n’est spécifié, le profilage est arrêté pour tous les processus.|  
|[GC](../profiling/gc-vsperfcmd.md)[**:**{**Allocation**`&#124;`**Lifetime**}]|Collecte les données d’allocation de mémoire et les données de durée de vie des objets de .NET. À utiliser seulement avec l’option **VSPerfCmdLaunch**.|  
  
### <a name="sample-interval-options"></a>Options d'intervalle d’échantillonnage  
 Les options suivantes spécifient le type et la durée des intervalles d’échantillonnage. La valeur par défaut est **Timer**. Vous pouvez également spécifier un compteur d’UC comme intervalle avec l’option **Counter**. Ces options peuvent être spécifiées seulement avec **Launch** ou avec la première option **Attach** d’une session de profilage.  
  
|Option|Description|  
|------------|-----------------|  
|[PF](../profiling/pf.md)[**:**_n_]|Échantillonne tous les n défauts de page (valeur par défaut=10).|  
|[Sys](../profiling/sys-vsperfcmd.md)[**:**_n_]|Échantillonne tous les n appels système (valeur par défaut=10).|  
|[Timer](../profiling/timer.md)[**:**_n_]|Échantillonne tous les n cycles de processeur (valeur par défaut=10 000 000).|  
  
## <a name="service-component-and-kernel-mode-device-options"></a>Options des composants de service et des périphériques en mode noyau  
 Les options Admin suivantes prennent en charge le profilage des composants de service ou les pilotes de périphérique en mode noyau. Les options Admin définissent des autorisations de profilage et contrôlent le service profilé ou le pilote de périphérique.  
  
 Les options Admin doivent être exécutées à une invite de commandes s’exécutant avec des informations d’identification d’administration.  
  
|Option|Description|  
|------------|-----------------|  
|**Admin:Security**, \<**ALLOW&#124;DENY**>, *Right*[ *Right*], \<*Utilisateur*&#124;*Groupe*>|Autorise ou refuse à l’utilisateur ou au groupe spécifié l’accès aux services de profilage.<br /><br /> `Right` peut être :<br /><br /> CrossSession : donne à l’utilisateur l’accès au service pour faire du profilage intersession.<br /><br /> SampleProfiling : donne à l’utilisateur l’accès au pilote pour activer le profilage par échantillonnage. Également utilisé pour accéder aux informations de transition du noyau lors du profilage de trace.<br /><br /> FullAccess : donne à l’utilisateur l’accès CrossSession et SampleProfiling.|  
|**Admin:Security, List**|Répertorie les états des services de profilage et les autorisations des utilisateurs.|  
|**Admin:** \<*Service*&#124;*Pilote*>\<**START**&#124;**STOP**&#124;**INSTALL**&#124;**UNINSTALL**>|Démarre, arrête, installe ou désinstalle le composant du service de profilage (service) ou le pilote de périphérique en mode noyau (driver).|  
|**Admin:** \<*Service*&#124;*Pilote*>**AutoStart**\<**ON**&#124;**OFF**>|Active ou désactive automatiquement le démarrage du service de profilage (service) ou du pilote de périphérique en mode noyau (driver) après un redémarrage.|  
  
## <a name="vsperfcmd-driver"></a>VSPerfCmd /Driver  
 L’option **VSPerfCmd /Driver** est désormais obsolète. Utilisez les options **d’administration VsPerfCmd** pour cette fonctionnalité.  
  
## <a name="see-also"></a>Voir aussi  
 [VSInstr](../profiling/vsinstr.md)   
 [VSPerfMon](../profiling/vsperfmon.md)   
 [VSPerfReport](../profiling/vsperfreport.md)