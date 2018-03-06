---
title: "Guide pratique pour spécifier le runtime .NET Framework | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Profiling Tools, .NET Framework versions
- .NET Framework versions,profililng
ms.assetid: d39f3579-719a-4f47-a97d-5b4232fe4c64
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: a060315c17dfc351aaa3cba5fec52fdcfc3f9b0c
ms.sourcegitcommit: 36ab8429333b31f03992a9fe8fc669db8e09c968
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2018
---
# <a name="how-to-specify-the-net-framework-runtime"></a>Guide pratique pour spécifier le runtime .NET Framework

Avec la version de [!INCLUDE[net_v40_long](../code-quality/includes/net_v40_long_md.md)], les applications peuvent être composées de modules conçus à l’aide de versions différentes du runtime [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. Par défaut, les Outils de profilage de Visual Studio profilent le premier runtime chargé par l’application. Vous pouvez spécifier le runtime à profiler quand vous démarrez une application avec le profileur et quand vous attachez le profileur à une application en cours d’exécution.

## <a name="to-specify-the-net-framework-run-time-to-profile-when-starting-an-application-with-the-profiler"></a>Pour spécifier le runtime .NET Framework à profiler lors du démarrage d’une application avec le profileur

1. Dans l’**Explorateur de performances**, cliquez avec le bouton droit sur la session de performance, cliquez sur **Propriétés**, puis cliquez sur **Avancées**.

     La zone de liste **Version CLR cible** affiche **Automatique** et les versions du runtime [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] installées sur l’ordinateur.

2. Effectuez l’une des opérations suivantes :

    - Cliquez sur la version du CLR que vous voulez profiler.

    - Cliquez sur **Automatique** pour profiler la première version chargée par l’application.

## <a name="to-specify-the-net-framework-run-time-to-profile-when-attaching-the-profiler-to-an-application"></a>Pour spécifier le runtime .NET Framework à profiler quand vous attachez le profileur à une application

1. Dans le menu Analyser, pointez sur Profileur, puis cliquez sur Attacher/Détacher.

2. Dans la boîte de dialogue Attacher le profileur au processus, cliquez sur le processus à profiler.

     La zone de liste **Version CLR cible** affiche **Automatique** et les versions du runtime [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] installées sur l’ordinateur.

3. Effectuez l’une des opérations suivantes :

    - Cliquez sur la version du CLR que vous voulez profiler.

    - Cliquez sur **Automatique** pour profiler la version chargée quand le profileur est attaché à l’application.