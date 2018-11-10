---
title: Conseils sur les performances | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 509d2d4f-48a5-4cdf-acad-6f7b75421303
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2933f29cb3668e12731e79151ba17480dda96ea5
ms.sourcegitcommit: bccb05b5b4e435f3c1f7c36ba342e7d4031eb398
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/06/2018
ms.locfileid: "51220553"
---
# <a name="perftips"></a>Conseils sur les performances
Les *conseils sur les performances* du débogueur et les **outils de diagnostic** intégrés au débogueur de Visual Studio vous aident à surveiller et à analyser les performances de votre application pendant le débogage.  
  
 Bien que les outils de diagnostic intégrés au débogueur constituent un excellent moyen de détecter les problèmes de performances pendant le développement, le débogueur lui-même peut avoir un impact significatif sur les performances de votre application. Pour collecter des données de performances plus précises, envisagez d'utiliser les outils de diagnostic de Visual Studio qui s'exécutent en dehors du débogueur en guise de méthode annexe pour vos investigations sur les performances. Consultez [Exécution des Outils de profilage avec ou sans débogueur](../profiling/running-profiling-tools-with-or-without-the-debugger.md).  
  
## <a name="perftips"></a>Conseils sur les performances  
 Quand le débogueur arrête l'exécution à un point d'arrêt ou lors de l'exécution pas à pas, le temps qui s'écoule entre l'arrêt et le point d'arrêt précédent apparaît sous la forme d'un conseil dans la fenêtre de l'éditeur. Pour plus d’informations, consultez [PerfTips: Performance Information at-a-glance while Debugging with Visual Studio](https://blogs.msdn.microsoft.com/devops/2014/08/18/perftips-performance-information-at-a-glance-while-debugging-with-visual-studio/).  
  
 ![Conseil sur les performances](../profiling/media/dbgdiag_perf_perftip.png "DBGDIAG_PERF_PerfTip")  
  
## <a name="diagnostics-tools-window"></a>Fenêtre Outils de diagnostic  
 Les points d’arrêt et les données chronologiques associées sont enregistrés dans la fenêtre **Outils de diagnostic**.  
  
 L’illustration suivante montre la fenêtre **Outils de diagnostic** de Visual Studio 2015 Update 1 :  
  
 ![DiagnosticTools&#45;Update1](../profiling/media/diagnostictools-update1.png "DiagnosticTools-Update1")  
  
-   La chronologie **Événements d'arrêt** marque les points d'arrêt qui ont été atteints dans la session de débogage. Cliquez sur un événement pour le sélectionner dans la liste des détails **Débogueur** .  
  
-   Le graphique **Utilisation du processeur** montre les changements dans l'utilisation du processeur pour tous ses cœurs dans la session de débogage.  
  
-   La liste **Événements** du volet des détails **Débogueur** comprend des éléments pour chaque événement d'arrêt.  
  
-   La colonne **Durée** d'un événement d'arrêt affiche le temps écoulé entre l'événement et le point d'arrêt précédent.  
  
## <a name="turn-perftips-on-or-off"></a>Activer ou désactiver les conseils sur les performances  
 Pour activer ou désactiver les conseils sur les performances :  
  
1.  Dans le menu **Déboguer** , choisissez **Options**.  
  
2.  Cochez ou décochez **Afficher les conseils sur les performances pendant le débogage**.  
  
## <a name="turn-the-diagnostic-tools-window-on-or-off"></a>Activer ou désactiver la fenêtre Outils de diagnostic  
 Pour activer ou désactiver la fenêtre Outils de diagnostic :  
  
1.  Dans le menu **Déboguer** , choisissez **Options**.  
  
2.  Cochez ou décochez **Activer les outils de diagnostic pendant le débogage**.

## <a name="see-also"></a>Voir aussi
 [Profilage dans Visual Studio](../profiling/index.md)  
 [Découvrir les outils de profilage](../profiling/profiling-feature-tour.md)
