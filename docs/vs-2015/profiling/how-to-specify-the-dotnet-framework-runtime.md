---
title: Guide pratique pour spécifier le runtime .NET Framework | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Profiling Tools, .NET Framework versions
- .NET Framework versions,profililng
ms.assetid: d39f3579-719a-4f47-a97d-5b4232fe4c64
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 25d7d9e63f5ab5581960f08d32f920b24f2f9906
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47494797"
---
# <a name="how-to-specify-the-net-framework-runtime"></a>Guide pratique pour spécifier le runtime .NET Framework
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [Comment : spécifier le Runtime .NET Framework](https://docs.microsoft.com/visualstudio/profiling/how-to-specify-the-dotnet-framework-runtime).  
  
Avec la version de [!INCLUDE[net_v40_long](../includes/net-v40-long-md.md)], les applications peuvent être composées de modules conçus à l’aide de versions différentes du runtime [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]. Par défaut, les outils de profilage [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] profilent le premier runtime chargé par l’application. Vous pouvez spécifier le runtime à profiler quand vous démarrez une application avec le profileur et quand vous attachez le profileur à une application en cours d’exécution.  
  
 **Spécifications**  
  
-   [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
### <a name="to-specify-the-net-framework-run-time-to-profile-when-starting-an-application-with-the-profiler"></a>Pour spécifier le runtime .NET Framework à profiler lors du démarrage d’une application avec le profileur  
  
1.  Dans l’**Explorateur de performances**, cliquez avec le bouton droit sur la session de performance, cliquez sur **Propriétés**, puis cliquez sur **Avancées**.  
  
     La zone de liste **Version CLR cible** affiche **Automatique** et les versions du runtime [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] installées sur l’ordinateur.  
  
2.  Effectuez l’une des opérations suivantes :  
  
    -   Cliquez sur la version du CLR que vous voulez profiler.  
  
    -   Cliquez sur **Automatique** pour profiler la première version chargée par l’application.  
  
### <a name="to-specify-the-net-framework-run-time-to-profile-when-attaching-the-profiler-to-an-application"></a>Pour spécifier le runtime .NET Framework à profiler quand vous attachez le profileur à une application  
  
1.  Dans le menu Analyser, pointez sur Profileur, puis cliquez sur Attacher/Détacher.  
  
2.  Dans la boîte de dialogue Attacher le profileur au processus, cliquez sur le processus à profiler.  
  
     La zone de liste **Version CLR cible** affiche **Automatique** et les versions du runtime [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] installées sur l’ordinateur.  
  
3.  Effectuez l’une des opérations suivantes :  
  
    -   Cliquez sur la version du CLR que vous voulez profiler.  
  
    -   Cliquez sur **Automatique** pour profiler la version chargée quand le profileur est attaché à l’application.



