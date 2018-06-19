---
title: Propriétés du débogueur Android (C++) | Microsoft Docs
ms.custom: ''
ms.date: 10/23/2017
ms.technology: vs-ide-mobile
ms.topic: conceptual
ms.assetid: 789f7a1c-38b4-41d0-809b-14f4d96c8116
author: corob
ms.author: mblome
manager: douge
f1_keywords:
- VC.Project.AndroidDebugger.DebuggerType
- VC.Project.AndroidDebugger.AndroidDeviceID
- VC.Project.AndroidDebugger.PackagePath
- VC.Project.AndroidDebugger.LaunchActivity
ms.workload:
- xplat-cplusplus
ms.openlocfilehash: 7d18125c6666a8eb68becd828da36ecdab077507
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31061485"
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
