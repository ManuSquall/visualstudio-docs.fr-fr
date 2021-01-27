---
title: Ligne de commande du profileur-instrumentation dynamique ASP.NET application, recevoir des données de minutage
description: Découvrez comment utiliser les outils en ligne de commande Outils de profilage Visual Studio pour collecter des données de temporisation détaillées pour une application ASP.NET compilée dynamiquement.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- aspnet
ms.openlocfilehash: 318728a78e6f15d8858aa2f037b890a3bfe8aeca
ms.sourcegitcommit: 8e15b434bf5db3e0f719320ca82682df1a3da110
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/27/2021
ms.locfileid: "98883629"
---
# <a name="how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-detailed-timing-data-with-the-profiler-by-using-the-command-line"></a>Guide pratique pour instrumenter une application web ASP.NET compilée dynamiquement et collecter des données temporelles détaillées avec le profileur en utilisant la ligne de commande

Cet article explique comment utiliser les outils en ligne de commande des Outils de profilage Visual Studio pour collecter des données de temporisation détaillées pour une application web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] compilée dynamiquement à l’aide de la méthode de profilage par instrumentation.

> [!NOTE]
> Pour obtenir le chemin des outils de profilage, consultez [Spécifier le chemin des outils en ligne de commande](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Les versions 64 bits et 32 bits des outils sont disponibles sur les ordinateurs 64 bits. Pour utiliser les outils en ligne de commande du profileur, vous devez ajouter le chemin des outils à la variable d’environnement PATH dans la fenêtre d’invite de commandes, ou l’ajouter à la commande.

Pour collecter des données de performances à partir d’une [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] application Web, vous devez modifier le *web.config* fichier de l’application cible pour permettre à l’outil [VSInstr.exe](../profiling/vsinstr.md) d’instrumenter les fichiers d’application compilés dynamiquement. Utilisez ensuite l’outil [VSPerfCLREnv. cmd](../profiling/vsperfclrenv.md) pour définir les variables d’environnement appropriées sur le serveur Web pour activer le profilage, puis redémarrez l’ordinateur.

Démarrez le profileur, puis exécutez l’application cible. Lorsque le profileur est attaché à l’application, vous pouvez suspendre et reprendre la collecte de données. Une fois le profilage terminé, fermez l’application, fermez le processus de travail Internet Information Services (IIS), puis arrêtez le profileur. Une fois votre travail de profilage terminé, restaurez le fichier *web.config* et le serveur Web à leur état d’origine.

## <a name="configure-the-aspnet-web-application-and-the-web-server"></a>Pour configurer l’application web ASP.NET et le serveur web

1. Modifiez le fichier *web.config* de l’application cible. Consultez [Comment : modifier des fichiers web.config pour instrumenter et profiler des applications web ASP.net compilées dynamiquement](../profiling/how-to-modify-web-config-files-to-instrument-dynamically-compiled-aspnet-apps.md).

2. Ouvrez une fenêtre d’invite de commandes.

3. Initialisez les variables d’environnement de profilage. Tapez :

     **VSPerfClrEnv /globaltraceon**

    - **/globaltraceon** permet le profilage à l’aide de la méthode d’instrumentation.

4. Redémarrez l'ordinateur.

## <a name="run-the-profiling-session"></a>Exécuter la session de profilage

1. Ouvrez une fenêtre d’invite de commandes.

2. Démarrez le profileur. Tapez :

     **VSPerfCmd**  [/Start](../profiling/start.md) **: trace**  [/Output](../profiling/output.md) **:** `OutputFile` [ `Options` ]

   - L’option **/Start : trace** Initialise le profileur.

   - L’option **/Output :** `OutputFile` est requise avec **/Start**. `OutputFile` Spécifie le nom et l’emplacement des données de profilage (.*vsp*).

     Vous pouvez utiliser l’une des options suivantes avec l’option **/start:trace**.

     > [!NOTE]
     > Les options **/user** et **/crosssession** sont généralement nécessaires pour les applications ASP.NET.

     | Option | Description |
     | - | - |
     | [/User](../profiling/user-vsperfcmd.md) **:**[ `Domain` **\\** ]`UserName` | Spécifie le nom de domaine et d’utilisateur du compte propriétaire du processus de travail ASP.NET. Cette option est nécessaire si le processus s’exécute sous le compte d’un utilisateur autre que celui connecté. Le propriétaire du processus est listé dans la colonne **nom d’utilisateur** sous l’onglet **processus** du gestionnaire des tâches de Windows. |
     | [/CrossSession](../profiling/crosssession.md) | Active le profilage des processus dans d’autres sessions ouvertes. Cette option est nécessaire si l’application ASP.NET s’exécute dans une autre session. L’identificateur de session est indiqué dans la colonne **ID de session** sous l’onglet **processus** du gestionnaire des tâches de Windows. **/CS** peut être spécifié comme abréviation de **/crosssession**. |
     | [/globaloff](../profiling/globalon-and-globaloff.md) | Démarre le profileur avec la collecte de données suspendue. Utilisez [/globalon](../profiling/globalon-and-globaloff.md) pour reprendre le profilage. |
     | [/Counter](../profiling/counter.md) **:**`Config` | Collecte des informations à partir du compteur de performances du processeur spécifié dans `Config`. Les informations du compteur sont ajoutées aux données collectées à chaque événement de profilage. |
     | [/WinCounter](../profiling/wincounter.md) **:**`WinCounterPath` | Spécifie le compteur de performances Windows dont les données doivent être collectées au cours du profilage. |
     | [/AutoMark](../profiling/automark.md) **:**`Interval` | À utiliser avec **/wincounter** uniquement. Spécifie le nombre de millisecondes écoulées entre les événements de collecte du compteur de performances Windows. La valeur par défaut est de 500 ms. |
     | [/Events](../profiling/events-vsperfcmd.md) **:**`Config` | Spécifie l’événement du Suivi d’événements pour Windows (ETW) qui doit être collecté au cours du profilage. Les événements ETW sont collectés dans un (.*fichier ETL*). |

3. Démarrez l’application web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] de manière habituelle.

## <a name="control-data-collection"></a>Contrôler la collecte des données

Pendant l’exécution de l’application cible, vous pouvez contrôler la collecte des données en démarrant et en arrêtant l’écriture des données dans le fichier de données du profileur à l’aide des options de *VSPerfCmd.exe*. Le fait de pouvoir contrôler la collecte vous permet de collecter des données pour une phase spécifique de l’exécution du programme, telle que le démarrage ou l’arrêt de l’application.

- Les paires d’options suivantes permettent de démarrer et d’arrêter la collecte des données. Spécifiez chaque option sur une ligne de commande distincte. Vous pouvez activer et désactiver la collecte de données à plusieurs reprises.

    |Option|Description|
    |------------|-----------------|
    |[/GlobalOn/globaloff](../profiling/globalon-and-globaloff.md)|Démarre (**/globalon**) ou arrête (**/globaloff**) la collecte des données pour tous les processus.|
    |[/ProcessOn](../profiling/processon-and-processoff.md) **:** `PID` [/ProcessOff](../profiling/processon-and-processoff.md) **:**`PID`|Démarre (**/processon**) ou arrête (**/processoff**) la collecte des données pour le processus spécifié par l’ID de processus (`PID`).|
    |[/ThreadOn](../profiling/threadon-and-threadoff.md) **:** `TID` [/ThreadOff](../profiling/threadon-and-threadoff.md) **:**`TID`|Démarre (**/threadon**) ou arrête (**/threadoff**) la collecte des données pour le thread spécifié par l’ID de thread (`TID`).|

- Vous pouvez également utiliser l’option **VSPerfCmd.exe**[/mark](../profiling/mark.md) pour insérer une marque de profilage dans le fichier de données. La commande **/mark** ajoute un identificateur, un horodatage et une chaîne de texte facultative définie par l’utilisateur. Les marques peuvent être utilisées pour filtrer les données des rapports et des vues de données du profileur.

## <a name="end-the-profiling-session"></a>Arrêter la session de profilage

Pour terminer une session de profilage, fermez l’application web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] cible, réinitialisez IIS pour arrêter le processus profilé, puis arrêtez le profileur.

1. Fermez l’application web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].

2. Fermez le processus de travail [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] en réinitialisant Internet Information Services (IIS). Tapez :

     **IISReset /stop**

3. Fermez le profileur. Tapez :

     **VSPerfCmd**  [/Shutdown](../profiling/shutdown.md)

4. Redémarrez IIS. Tapez :

     **IISReset /start**

## <a name="restore-the-application-and-computer-configuration"></a>Restaurer la configuration de l’application et de l’ordinateur

Lorsque vous avez terminé tout le profilage, remplacez le fichier *web.config* , effacez les variables d’environnement de profilage, puis redémarrez l’ordinateur pour restaurer l’application et le serveur à l’État dans lequel elles se trouvaient avant le profilage.

1. Remplacez le fichier *web.config* par une copie du fichier d’origine.

2. Effacez les variables d’environnement de profilage. Tapez :

     **VSPerfCmd /globaloff**

3. Redémarrez l'ordinateur.

## <a name="see-also"></a>Voir aussi

[Profiler des applications](../profiling/command-line-profiling-of-aspnet-web-applications.md) 
 Web ASP.net [Vues de données de la méthode d’instrumentation](../profiling/instrumentation-method-data-views.md)
