---
title: VSPerf | Microsoft Docs
description: Découvrez comment utiliser l’outil en ligne de commande VsPerf pour profiler des applications UWP à partir de la ligne de commande quand Visual Studio n’est pas installé sur l’appareil.
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: b5854e62-279e-4850-bfeb-0c6ef82f4805
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 4b3d95422d3b4232d7a628f2054c7db2aa94dd6b
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2021
ms.locfileid: "98723073"
---
# <a name="vsperf"></a>VSPerf
Utilisez l’outil en ligne de commande **VsPerf** pour :

1. Profiler des applications UWP à partir de la ligne de commande quand Visual Studio n’est pas installé sur l’appareil.

2. Profiler des applications de bureau Windows 8 et des applications Windows Server 2012 à l’aide de la méthode de profilage par échantillonnage.

   Pour plus d’informations sur les options de profilage, consultez [Outils d’analyse des performances sur les applications Windows 8 et Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="uwp-apps-only"></a>Applications UWP uniquement
 Ces options s’appliquent uniquement aux applications UWP.

|Option|Description|
|-|-|
|**/app:{nom_application}**|Démarre le profileur et attend que l’application spécifiée soit lancée à partir du menu Démarrer.<br /><br /> Exécutez `vsperf /listapps` pour afficher le nom d’application et le nom complet du package des applications installées.|
|**/package:{nom complet du package}**|Démarre le profileur et attend que l’application spécifiée soit lancée à partir du menu Démarrer.<br /><br /> Exécutez `vsperf /listapps` pour afficher le nom d’application et le nom complet du package des applications installées.|
|**/js**|Obligatoire pour le profilage d’applications JavaScript.<br /><br /> Collecte les données de performances à partir des applications JavaScript.<br /><br /> Utilisez uniquement avec /package ou /attach.|
|**/noclr**|Optionnel. Ne collecte pas de données CLR.<br /><br /> Utilisez uniquement avec /package ou /attach.<br /><br /> Optimisation ; aucune résolution de symbole managé.|
|**/listapps**|Liste les noms et les noms complets de packages des applications installées.|

## <a name="windows-8-desktop-applications-and-windows-server-2012-applications-only"></a>Applications de bureau Windows 8 et applications Windows Server 2012 uniquement
 Ces options ne fonctionnent pas sur les applications UWP.

|Option|Description|
|-|-|
|**/launch:{exécutable}**|Démarre et commence le profilage du fichier exécutable spécifié.|
|**/args:{arguments_exécutable}**|Spécifie les arguments de ligne de commande à passer à la cible de **/launch**.|
|**/Console**|Exécute la cible **/launch** dans une nouvelle fenêtre de commande.|

## <a name="all-applications"></a>Toutes les applications
 Ces options s’appliquent à toutes les applications Windows 8 ou Windows Server 2012.

|Option|Description|
|-|-|
|**/attach:{PID&#124;nom_processus}[,PID&#124;nom_processus]...**|Collecte les données des processus spécifiés.<br /><br /> Utilisez le Gestionnaire des tâches pour afficher l’ID de processus (PID) et les noms de processus des applications en cours d’exécution.|
|**/file:{nom_rapport}**|Optionnel. Spécifie le fichier de sortie (écrase le fichier existant).<br /><br /> Utilisez uniquement avec /package ou /attach.|
|**/pause**|Suspendre la collecte de données.|
|**/RESUME**|Reprendre la collecte de données.|
|**/Stop**|Arrêter la collecte de données et terminer les processus cibles.|
|**/Detach**|Arrêter la collecte de données, sans interrompre l’exécution des processus cibles.|
|**/Status**|Afficher l’état du profileur.|

## <a name="see-also"></a>Voir aussi
- [Outils d’analyse des performances sur les applications Windows 8 et Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)
- [Profiler à partir de la ligne de commande](../profiling/using-the-profiling-tools-from-the-command-line.md)
