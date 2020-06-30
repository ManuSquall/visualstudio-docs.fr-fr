---
title: Définition des options générales d’une session de performances | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.property.general
ms.assetid: 6b60bd1b-2198-4261-b84e-9b2d8494a992
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c3bb57e2c8c5dd156fd5c96994eeb843569954af
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544948"
---
# <a name="setting-general-performance-session-options"></a>Définition des options générales d'une session de performance
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez définir la méthode de collecte et les conventions de nommage des noms de données pour une session de performances des Outils de profilage [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] dans la page **Général** de la boîte de dialogue des propriétés de la session de performances. Pour ouvrir cette boîte de dialogue depuis **l’Explorateur de performances**, cliquez avec le bouton droit sur la session de performances, puis cliquez sur **Propriétés**.  
  
 **Configuration requise**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
## <a name="choosing-data-collection-methods"></a>Choix des méthodes de collecte des données  
 Vous définissez la méthode de collecte de base en sélectionnant une des options sous **Collecte du profilage**. Les options sont décrites dans le tableau suivant :  
  
|Option|Description|  
|-|-|  
|**Échantillonnage**. La méthode d’échantillonnage collecte des informations de profilage à intervalles réguliers. Cette méthode est pratique pour détecter les problèmes d’utilisation du processeur ; il s’agit de la méthode recommandée pour commencer la plupart des investigations sur les performances.|-   [Collecte de statistiques de performances à l’aide de l’échantillonnage](../profiling/collecting-performance-statistics-by-using-sampling.md)|  
|**Instrumentation**. La méthode d’instrumentation injecte du code de profilage dans une copie d’un module, qui enregistre chaque entrée, sortie et appel de fonction des fonctions du module pendant une exécution du profilage. Cette méthode permet de collecter des informations de temporisation détaillées à propos d’une partie précise de votre code. Elle vous aide à comprendre l’impact des opérations d’entrée et de sortie sur les performances de l’application.|-   [Collecte de données de temporisation détaillées à l’aide de l’instrumentation](../profiling/collecting-detailed-timing-data-by-using-instrumentation.md)|  
|**Accès concurrentiel**. La méthode d’accès concurrentiel collecte des données pour chaque événement qui bloque l’exécution de votre code, par exemple quand un thread attend la libération d’un verrou d’accès à une ressource d’application. Cette méthode est utile pour l’analyse des applications multithread.|-   [Collecte de données de concurrence de threads et de processus](../profiling/collecting-thread-and-process-concurrency-data.md)|  
  
 Vous pouvez collecter des données de mémoire .NET en utilisant les méthodes d’échantillonnage ou d’instrumentation. Vous sélectionnez le type de données sous **Profilage de mémoire .NET**.  
  
|Options|Article|  
|-|-|  
|**Collectez les informations d’allocation d’objets .NET**. Par défaut, les données incluent le nombre et la taille des objets alloués. Cochez ou décochez cette case pour activer ou désactiver la collecte de données mémoire .NET.<br /><br /> **Collecter aussi les informations de durée de vie des objets .NET**. Cochez cette case pour inclure des données sur les générations de garbage collection qui ont été utilisées pour récupérer les objets en mémoire.|-   [Collecte de données liées à l’allocation et à la durée de vie de la mémoire .NET](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)|  
  
 Une page de session de profilage apparaît quand vous commencez à profiler une application, où vous pouvez suspendre, reprendre et arrêter le profilage.  
  
 ![Page de session de profilage](../profiling/media/prof-profilingsessionpage.png "PROF_ProfilingSessionPage")  
  
## <a name="setting-profiling-data-file-options"></a>Définition des options du fichier de données de profilage  
  
|Option|Article|  
|-|-|  
|**Rapport**. Par défaut, le nom du fichier de données de profilage (.vsp) est le nom de l’application profilée ; ce fichier se trouve dans le dossier de la solution ou du projet. Une chaîne de date est également ajoutée au nom ; en outre, un numéro incrémenté est ajouté aux fichiers de données qui sans cela auraient des noms en doublon. Vous pouvez modifier ces options.|-   [Procédure : définir les options de nom de fichier de données de performances](../profiling/how-to-set-performance-data-file-name-options.md)|
