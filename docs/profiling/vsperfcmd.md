---
title: "VSPerfCmd | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ligne de commande, outils"
  - "outils en ligne de commande, VSPerfCmd (outil)"
  - "outils d'analyse des performances, VSPerfCmd (outil)"
  - "outils de profilage, VSPerfCmd"
  - "VSPerfCmd (outil)"
ms.assetid: 778bc105-7643-46c4-a338-f3620e31125a
caps.latest.revision: 49
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 49
---
# VSPerfCmd
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'outil **VSPerfCmd.exe** permet de démarrer et d'arrêter la collecte de données de performance.  Il utilise la syntaxe suivante :  
  
```  
VSPerfCmd [/U] [/options]  
```  
  
 Les tableaux ci\-dessous décrivent les options de l'outil **VSPerfCmd.exe**.  
  
|Option|Description|  
|------------|-----------------|  
|**U**|La sortie de console redirigée est écrite sous Unicode.  Doit être la première option spécifiée.|  
|[Démarrer](../profiling/start.md) **:** `mode`|Démarre le service de profilage dans le mode spécifié.|  
|[Output](../profiling/output.md) **:** `filename`|Spécifie le nom du fichier de sortie.  À n'utiliser qu'avec **Start**.|  
|[CrossSession&#124;CS](../profiling/crosssession.md)|Active le profilage dans les sessions Windows.  À n'utiliser qu'avec **Start**, **Attach** ou **Launch**.|  
|[Utilisateur](../profiling/user-vsperfcmd.md) **:**\[`domain\`\]`username`|Active l'accès du compte spécifié au service du profileur.  À n'utiliser qu'avec **Start**.|  
|[WaitStart](../profiling/waitstart.md)\[**:**`n`\]|Attend l'initialisation du journal de collecte de données.  Si `n` est spécifié, **VSPerfCmd** attendra au plus `n` secondes.  Si `n` n'est pas spécifié, **VSPerfCmd** attendra indéfiniment.  Cela facilite l'utilisation de **VSPerfCmd** dans le cadre d'un processus par lots.|  
|[Compteur](../profiling/counter.md) **:** `cfg`|En cas d'utilisation de la méthode de profilage par échantillonnage, spécifie un compteur UC et le nombre d'événements à utiliser comme intervalle d'échantillonnage.  Vous ne pouvez échantillonner qu'une seule valeur de compteur à la fois.<br /><br /> En cas d'utilisation de la méthode de profilage par instrumentation, spécifie un compteur UC à collecter à chaque point d'instrumentation.  À n'utiliser qu'avec **Start:**`Trace`, **Attach**,ou **Launch**.|  
|[QueryCounters](../profiling/querycounters.md)|Affiche une liste des compteurs UC valides pour l'ordinateur actuel.|  
|[WinCounter](../profiling/wincounter.md) **:** *path*|Spécifie un événement de compteur de performance Windows à inclure avec les données de marquage du profil.  À n'utiliser qu'avec **Start**.|  
|[AutoMark](../profiling/automark.md) **:** *n*|Spécifie l'intervalle \(en millisecondes\) entre les événements de collecte de données du compteur de performance Windows.  Utilisez avec **WinCounter**.|  
|[Événements](../profiling/events-vsperfcmd.md) **:** `option`|Contrôle la collecte des événements ETW \(Event Tracing for Windows\) spécifiés.  Les données ETW sont collectées dans un fichier .itl différent du fichier de données de profilage \(.vsp\).|  
|[Status](../profiling/status.md)|Affiche l'état du profileur, des informations sur les processus en cours de profilage et les comptes habilités à contrôler le profileur.|  
|[Shutdown](../profiling/shutdown.md)\[**:**`n`\]|Ferme le fichier de données de profilage et désactive le profileur.|  
|[GlobalOn](../profiling/globalon-and-globaloff.md)|Reprend la collecte des données après un appel à **VSPerfCmd GlobalOff**.|  
|[GlobalOff](../profiling/globalon-and-globaloff.md)|Arrête toute la collecte de données, mais ne termine pas la session de profilage.|  
|[ProcessOn](../profiling/processon-and-processoff.md) **:** `pid`|Reprend la collecte de données pour le processus spécifié après la suspension du profilage via un appel à **VSPerfCmd ProcessOff**.|  
|[ProcessOff](../profiling/processon-and-processoff.md) **:** `pid`|Arrête la collecte de données pour le processus spécifié.|  
|[ThreadOn et ThreadOff](../profiling/threadon-and-threadoff.md) **:** *tid*|Reprend le profilage du processus spécifié après la suspension du profilage via un appel à **VSPerfCmd ThreadOff**.  Utilisez **ThreadOn** seulement en cas de profilage avec la méthode d'instrumentation.|  
|[ThreadOn et ThreadOff](../profiling/threadon-and-threadoff.md) **:** *tid*|Suspend le profilage pour le thread spécifié.  Utilisez **ThreadOff** seulement en cas de profilage avec la méthode d'instrumentation.|  
|[Marque](../profiling/mark.md) **:** *MarkNum*\[**,***MarkText***\]**|Insère une marque dans le fichier de données de profilage, avec un texte facultatif.|  
  
## Options de la méthode d'échantillonnage  
 Les options suivantes sont disponibles uniquement lorsque vous utilisez la méthode de profilage par échantillonnage.  
  
|Option|Description|  
|------------|-----------------|  
|[Lancer](../profiling/launch.md) **:** *Executable*|Démarre l'application spécifiée et commence le profilage.|  
|[Args](../profiling/args.md) **:** *Arguments*|Spécifie les arguments de la ligne de commande à passer à l'application lancée.|  
|[Console](../profiling/console.md)|Démarre la commande spécifiée dans une nouvelle fenêtre d'invite de commandes.|  
|[Attach](../profiling/attach.md) **:** *PID*\[**,***PID*\]|Commence le profilage des processus spécifiés.  Les processus peuvent être identifiés par l'ID de processus ou par le nom de processus.|  
|[Detach](../profiling/detach.md)\[**:***PID*\[,*PID*\]\]|Arrête le profilage des processus spécifiés.  Les processus peuvent être identifiés par l'ID de processus ou par le nom de processus.  Si aucun processus n'est spécifié, le profilage est interrompu pour tous les processus.|  
|[GC](../profiling/gc-vsperfcmd.md)\[**:**{**Allocation** `&#124;` **Lifetime**}\]|Collecte les données liées à l'allocation de la mémoire .NET et à la durée de vie des objets.  À n'utiliser qu'avec l'option **VSPerfCmd Launch**.|  
  
### Options d'intervalle d'échantillonnage  
 Les options suivantes spécifient le type et la durée des intervalles d'échantillonnage.  La valeur par défaut est **Timer**.  Vous pouvez également spécifier un compteur UC comme intervalle à l'aide de la **Counter** option.  Ces options peuvent uniquement être spécifiées avec **Launch** ou avec la première occurrence **Attach** d'une session de profilage.  
  
|Option|Description|  
|------------|-----------------|  
|[PF](../profiling/pf.md)\[**:***n*\]|Exemples sur chaque numéro d'erreur de page \(valeur par défaut\=10\).|  
|[Sys](../profiling/sys-vsperfcmd.md)\[**:***n*\]|Exemples sur chaque numéro d'appel système \(valeur par défaut\=10\).|  
|[Timer](../profiling/timer.md)\[**:***n*\]|Échantillonnage tous les n cycles de processeur \(valeur par défaut\=10000000\).|  
  
## Options des composants du service et des périphériques en mode noyau  
 Les options Admin suivantes prennent en charge les composants du service de profilage ou les pilotes de périphériques en mode noyau.  Les options Admin définissent les autorisations de profilage et contrôlent le pilote de périphérique ou le service profilé.  
  
 Les options Admin doivent être exécutées dans une invite de commandes qui s'exécute avec les informations d'identification d'administration.  
  
|Option|Description|  
|------------|-----------------|  
|**Admin:Security** \<**ALLOW&#124;DENY**\> *Right*\[ *Right*\] \<*User*&#124;*Group*\>|Autorise ou refuse à l'utilisateur ou au groupe spécifié l'accès aux services de profilage.<br /><br /> `Right` peut être :<br /><br /> CrossSession \- accorde à l'utilisateur l'accès au service pour faire du profilage intersession.<br /><br /> SampleProfiling \- accorde à l'utilisateur l'accès au pilote pour activer le profilage d'échantillonnage.  Également utilisé pour accéder aux informations de transition du noyau au cours du profilage de trace.<br /><br /> FullAccess \- accorde à l'utilisateur l'accès à CrossSession et à SampleProfiling.|  
|**Admin:Security, List**|Répertorie l'état actuel des services de profilage ainsi que les autorisations utilisateur.|  
|**Admin:**  `` \<*Service*&#124;*Driver*\>\<**START**&#124;**STOP**&#124;**INSTALL**&#124;**UNINSTALL**\>|Démarre, arrête, installe ou désinstalle le composant du service de profilage \(service\) ou le pilote de périphérique de mode noyau \(pilote\).|  
|**Admin:**  `` \<*Service*&#124;*Driver*\>**AutoStart** `` \<**ON**&#124;**OFF**\>|Active ou désactive automatiquement le démarrage du service de profilage \(service\) ou le pilote de périphérique de mode noyau \(pilote\) après un redémarrage.|  
  
## VSPerfCmd \/Driver  
 L'option **VSPerfCmd \/Driver** est désormais obsolète.  Pour assurer cette fonctionnalité, utilisez les options **VsPerfCmd Admin**.  
  
## Voir aussi  
 [VSInstr](../profiling/vsinstr.md)   
 [VSPerfMon](../profiling/vsperfmon.md)   
 [VSPerfReport](../profiling/vsperfreport.md)