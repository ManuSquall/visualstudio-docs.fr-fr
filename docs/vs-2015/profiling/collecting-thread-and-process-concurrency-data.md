---
title: Collecte de données de concurrence de threads et de processus | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- concurrency profiling method
- Profiling Tools, concurrency method
ms.assetid: fa03d381-a9ee-408c-876d-05111e29225b
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cf8a9de5f2a7e520a745fab81197016d6e1bd15d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62568189"
---
# <a name="collecting-thread-and-process-concurrency-data"></a>Collecte de données de concurrence de threads et de processus
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La méthode de profilage d’accès concurrentiel des outils de profilage [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] permet de collecter des données de conflit de ressources comprenant des informations sur chaque événement de synchronisation en raison duquel une fonction de l’application profilée doit attendre l’accès à une ressource.  
  
 **Configuration requise**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
  Vous pouvez spécifier la méthode de profilage d’accès concurrentiel à l’aide de l’une des procédures suivantes :  
  
- Dans la première page de l’Assistant Profilage, cliquez sur **Concurrence**.  
  
- Dans la page **Général** de la boîte de dialogue Propriétés de la session de performance, cliquez sur **Concurrence**.  
  
- Dans la barre d’outils de **l’Explorateur de performances**, dans la liste **Méthode**, cliquez sur **Concurrence**.  
  
## <a name="common-tasks"></a>Tâches courantes  
 Vous pouvez spécifier des options supplémentaires dans la boîte de dialogue des _pages de propriétés_**session de performance** . Pour ouvrir la boîte de dialogue :  
  
- Dans **Explorateur de performances**, cliquez avec le bouton droit sur le nom de la session de performance, puis cliquez sur **Propriétés**.  
  
  Les tâches du tableau suivant décrivent les options que vous pouvez spécifier dans la boîte de dialogue _Session de performance_**Pages de propriétés** quand vous effectuez un profilage à l’aide de la méthode d’accès concurrentiel.  
  
|Tâche|Contenu associé|  
|----------|---------------------|  
|Dans la page **Général**, spécifiez les détails d’affectation de noms pour le fichier de données de profilage (.vsp) généré.|-   [Procédure : définir les options de nom de fichier de données de performances](../profiling/how-to-set-performance-data-file-name-options.md)|  
|Si votre solution de code contient plusieurs projets .exe, dans la page **Lancer**, spécifiez l’application à démarrer.|-   [Comment : spécifier le binaire à démarrer](../profiling/how-to-specify-the-binary-to-start.md)|  
|Dans la page **Interaction de couche** , ajoutez les données d’appel ADO.NET à l’exécution du profilage.|-   [Collecte des données d’interaction de couche](../profiling/collecting-tier-interaction-data.md)|  
|Dans la page **Compteurs Windows** , spécifiez un ou plusieurs compteurs de performance de système d’exploitation à ajouter aux données de profilage en tant que marques.|-   [Guide pratique pour collecter les données des compteurs Windows](../profiling/how-to-collect-windows-counter-data.md)|  
|Dans la page **avancé** , spécifiez la version du .NET Framework au moment de l’exécution pour le profilage si vos modules d’application utilisent plusieurs versions. Par défaut, la première version chargée est profilée.|-   [Comment : spécifier le Runtime .NET Framework](../profiling/how-to-specify-the-dotnet-framework-runtime.md)|
