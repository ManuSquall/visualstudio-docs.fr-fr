---
title: "Propriétés du débogueur Android (C++) | Microsoft Docs"
ms.custom: 
ms.date: 10/23/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 789f7a1c-38b4-41d0-809b-14f4d96c8116
author: corob
ms.author: mblome
manager: ghogen
f1_keywords:
- VC.Project.AndroidDebugger.DebuggerType
- VC.Project.AndroidDebugger.AndroidDeviceID
- VC.Project.AndroidDebugger.PackagePath
- VC.Project.AndroidDebugger.LaunchActivity
ms.openlocfilehash: a296ea142b13b9bdcda888a7f382de9eeb17a40a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="android-debugger-properties"></a>Propriétés du débogueur Android

Propriété | Description | Options
--- | ---| ---
Type de débogueur | Spécifie le type de code à déboguer. | **Natif uniquement**<br>**Java uniquement**<br>
Cible de débogage | Spécifie l’émulateur ou l’appareil à utiliser pour le débogage. Si aucun émulateur n’est en cours d’exécution, utilisez 'Android Virtual Device (AVD) Manager' pour démarrer un appareil.
Package à lancer | Spécifie l’emplacement du fichier .apk à déboguer. Choisissez cette option pour indiquer qu’un package spécifique (APK) doit démarrer quand l’application est déboguée.
Lancer une activité | L’activité Android à utiliser pour lancer l’application doit correspondre à celle utilisée dans le manifeste. Appuyez sur Appliquer pour récupérer la liste du fichier AndroidManifest.xml et la remplir dynamiquement.
Autres chemins de recherche des symboles | Chemin de recherche supplémentaire pour les symboles de débogage.
Chemins de recherche de sources Java supplémentaires | Chemins de recherche supplémentaires pour les fichiers sources Java. (S’applique seulement quand le type du débogueur est Java uniquement.)
