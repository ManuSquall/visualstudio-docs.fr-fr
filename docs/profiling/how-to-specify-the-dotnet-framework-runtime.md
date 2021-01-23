---
title: Spécifier le runtime .NET Framework | Microsoft Docs
description: Découvrez comment les applications peuvent être composées de modules construits à l’aide de différentes versions du .NET Framework au moment de l’exécution.
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Profiling Tools, .NET Framework versions
- .NET Framework versions,profililng
ms.assetid: d39f3579-719a-4f47-a97d-5b4232fe4c64
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: e825b456a4524653df4e8c40793f16f3d8887665
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2021
ms.locfileid: "98721825"
---
# <a name="how-to-specify-the-net-framework-runtime"></a>Guide pratique pour spécifier le runtime .NET Framework

Avec la publication de .NET Framework 4, les applications peuvent être composées de modules générés avec des versions différentes du runtime .NET Framework. Par défaut, les Outils de profilage de Visual Studio profilent le premier runtime chargé par l’application. Vous pouvez spécifier le runtime à profiler quand vous démarrez une application avec le profileur et quand vous attachez le profileur à une application en cours d’exécution.

## <a name="to-specify-the-net-framework-run-time-to-profile-when-starting-an-application-with-the-profiler"></a>Pour spécifier le runtime .NET Framework à profiler lors du démarrage d’une application avec le profileur

1. Dans l’**Explorateur de performances**, cliquez avec le bouton droit sur la session de performance, cliquez sur **Propriétés**, puis cliquez sur **Avancées**.

     La zone de liste **Version CLR cible** affiche **Automatique** et les versions du runtime .NET Framework installées sur l’ordinateur.

2. Effectuez l’une des opérations suivantes :

    - Cliquez sur la version du CLR que vous voulez profiler.

    - Cliquez sur **Automatique** pour profiler la première version chargée par l’application.

## <a name="to-specify-the-net-framework-run-time-to-profile-when-attaching-the-profiler-to-an-application"></a>Pour spécifier le runtime .NET Framework à profiler quand vous attachez le profileur à une application

1. Dans le menu **Analyser**, pointez sur **Profileur**, puis cliquez sur **Attacher/Détacher**.

2. Dans la boîte de dialogue **Attacher le profileur au processus**, cliquez sur le processus à profiler.

     La zone de liste **Version CLR cible** affiche **Automatique** et les versions du runtime .NET Framework installées sur l’ordinateur.

3. Effectuez l’une des opérations suivantes :

    - Cliquez sur la version du CLR que vous voulez profiler.

    - Cliquez sur **Automatique** pour profiler la version chargée quand le profileur est attaché à l’application.
