---
title: 'Ligne de commande Profiler : Application ASP.NET dynamique d’instrument, obtenir des données de synchronisation'
ms.date: 11/04/2016
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- aspnet
ms.openlocfilehash: d8270c9948efe5f9c972f2e4f0eccb035c793953
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74775455"
---
# <a name="how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-detailed-timing-data-with-the-profiler-by-using-the-command-line"></a>Guide pratique pour instrumenter une application web ASP.NET compilée dynamiquement et collecter des données temporelles détaillées avec le profileur en utilisant la ligne de commande

Cet article explique comment utiliser les outils en ligne de commande des Outils de profilage Visual Studio pour collecter des données de temporisation détaillées pour une application web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] compilée dynamiquement à l’aide de la méthode de profilage par instrumentation.

> [!NOTE]
> Pour obtenir le chemin des outils de profilage, consultez [Spécifier le chemin des outils en ligne de commande](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Les versions 64 bits et 32 bits des outils sont disponibles sur les ordinateurs 64 bits. Pour utiliser les outils en ligne de commande du profileur, vous devez ajouter le chemin des outils à la variable d’environnement PATH dans la fenêtre d’invite de commandes, ou l’ajouter à la commande.

Pour collecter des [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] données de performance à partir d’une application web, vous modifiez le fichier *web.config* de l’application cible pour permettre à l’outil [VSInstr.exe](../profiling/vsinstr.md) d’instrumenter les fichiers d’application compilés dynamiquement. Vous utilisez ensuite l’outil [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) pour définir les variables d’environnement appropriées sur le serveur Web pour activer le profilage, puis redémarrer l’ordinateur.

Démarrez le profileur, puis exécutez l’application cible. Lorsque le profileur est attaché à l’application, vous pouvez suspendre et reprendre la collecte de données. Une fois le profilage terminé, fermez l’application, fermez le processus de travail Internet Information Services (IIS), puis arrêtez le profileur. Lorsque vous avez terminé votre travail de profilage, restaurer le fichier *web.config* et le serveur Web à leurs états d’origine.

## <a name="configure-the-aspnet-web-application-and-the-web-server"></a>Pour configurer l’application web ASP.NET et le serveur web

1. Modifier le fichier *web.config* de l’application cible. Voir [comment : Modifier les fichiers web.config aux fichiers instrument et profil compilés dynamiquement ASP.NET applications Web](../profiling/how-to-modify-web-config-files-to-instrument-dynamically-compiled-aspnet-apps.md).

2. Ouvrez une fenêtre d’invite de commandes.

3. Initialisez les variables d’environnement de profilage. Tapez :

     **VSPerfClrEnv /globaltraceon**

    - **/globaltraceon** permet le profilage à l’aide de la méthode d’instrumentation.

4. Redémarrez l'ordinateur.

## <a name="run-the-profiling-session"></a>Exécuter la session de profilage

1. Ouvrez une fenêtre d’invite de commandes.

2. Démarrez le profileur. Tapez :

     **VSPerfCmd**[/start](../profiling/start.md) **:trace**[/output](../profiling/output.md) **:** `OutputFile` ]`Options`    

   - **L’option /démarrer : l’option de la trace** est parasabilitée le profileur.

   - La **/sortie:** `OutputFile` option est nécessaire avec **/démarrer**. `OutputFile`spécifie le nom et l’emplacement des données de profilage (.* vsp*) fichier.

     Vous pouvez utiliser l’une des options suivantes avec l’option **/start:trace**.

     > [!NOTE]
     > Les options **/user** et **/crosssession** sont généralement nécessaires pour les applications ASP.NET.

     | Option | Description |
     | - | - |
     | [/utilisateur](../profiling/user-vsperfcmd.md) **:**:`Domain`**\\**[ ]`UserName` | Spécifie le nom de domaine et d’utilisateur du compte propriétaire du processus de travail ASP.NET. Cette option est nécessaire si le processus s’exécute sous le compte d’un utilisateur autre que celui connecté. Le propriétaire du processus est répertorié dans la colonne **nom de l’utilisateur** sur l’onglet **Processus** de Windows Task Manager. |
     | [/croix](../profiling/crosssession.md) | Active le profilage des processus dans d’autres sessions ouvertes. Cette option est nécessaire si l’application ASP.NET s’exécute dans une autre session. L’identifiant de session est indiqué dans la colonne **d’identification de session** sur l’onglet **Processus** de Windows Task Manager. **/CS** peut être spécifié comme abréviation de **/crosssession**. |
     | [/globaloff](../profiling/globalon-and-globaloff.md) | Démarre le profileur avec la collecte de données suspendue. Utilisez [/globalon](../profiling/globalon-and-globaloff.md) pour reprendre le profilage. |
     | [/contre](../profiling/counter.md) **:**`Config` | Collecte des informations à partir du compteur de performances du processeur spécifié dans `Config`. Les informations du compteur sont ajoutées aux données collectées à chaque événement de profilage. |
     | [/wincounter](../profiling/wincounter.md) **:**`WinCounterPath` | Spécifie le compteur de performances Windows dont les données doivent être collectées au cours du profilage. |
     | [/automark](../profiling/automark.md) **:**`Interval` | À utiliser avec **/wincounter** uniquement. Spécifie le nombre de millisecondes écoulées entre les événements de collecte du compteur de performances Windows. La valeur par défaut est de 500 ms. |
     | [/événements](../profiling/events-vsperfcmd.md) **:**`Config` | Spécifie l’événement du Suivi d’événements pour Windows (ETW) qui doit être collecté au cours du profilage. Les événements ETW sont collectés dans un autre (.* etl*) fichier. |

3. Démarrez l’application web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] de manière habituelle.

## <a name="control-data-collection"></a>Contrôler la collecte des données

Pendant l’exécution de l’application cible, vous pouvez contrôler la collecte des données en démarrant et en arrêtant l’écriture des données dans le fichier de données du profileur à l’aide des options de *VSPerfCmd.exe*. Le fait de pouvoir contrôler la collecte vous permet de collecter des données pour une phase spécifique de l’exécution du programme, telle que le démarrage ou l’arrêt de l’application.

- Les paires d’options suivantes permettent de démarrer et d’arrêter la collecte des données. Spécifiez chaque option sur une ligne de commande distincte. Vous pouvez activer et désactiver la collecte de données à plusieurs reprises.

    |Option|Description|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Démarre (**/globalon**) ou arrête (**/globaloff**) la collecte des données pour tous les processus.|
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:**`PID`|Démarre (**/processon**) ou arrête (**/processoff**) la collecte des données pour le processus spécifié par l’ID de processus (`PID`).|
    |[/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [/threadoff](../profiling/threadon-and-threadoff.md) **:**`TID`|Démarre (**/threadon**) ou arrête (**/threadoff**) la collecte des données pour le thread spécifié par l’ID de thread (`TID`).|

- Vous pouvez également utiliser l’option **VSPerfCmd.exe**[/mark](../profiling/mark.md) pour insérer une marque de profilage dans le fichier de données. La commande **/mark** ajoute un identificateur, un horodatage et une chaîne de texte facultative définie par l’utilisateur. Les marques peuvent être utilisées pour filtrer les données des rapports et des vues de données du profileur.

## <a name="end-the-profiling-session"></a>Arrêter la session de profilage

Pour terminer une session de profilage, fermez l’application web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] cible, réinitialisez IIS pour arrêter le processus profilé, puis arrêtez le profileur.

1. Fermez l’application web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].

2. Fermez le processus de travail [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] en réinitialisant Internet Information Services (IIS). Tapez :

     **IISReset /stop**

3. Fermez le profileur. Tapez :

     **VSPerfCmd**  [/shutdown](../profiling/shutdown.md)

4. Redémarrez IIS. Tapez :

     **IISReset /start**

## <a name="restore-the-application-and-computer-configuration"></a>Restaurer la configuration de l’application et de l’ordinateur

Lorsque vous avez terminé tout profilage, remplacez le fichier *web.config,* effacez les variables de l’environnement de profilage et redémarrez l’ordinateur pour restaurer l’application et le serveur aux états dans lequel ils se trouvaient avant le profilage.

1. Remplacez le fichier *web.config* par une copie du fichier original.

2. Effacez les variables d’environnement de profilage. Tapez :

     **VSPerfCmd /globaloff**

3. Redémarrez l'ordinateur.

## <a name="see-also"></a>Voir aussi

[Profil ASP.NET applications](../profiling/command-line-profiling-of-aspnet-web-applications.md)
Web[Vues de données de méthode d’instrumentation](../profiling/instrumentation-method-data-views.md)
