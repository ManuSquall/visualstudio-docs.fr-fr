---
title: Paramètres avancés, boîte de dialogue (visualiseur concurrentiel) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.settings
ms.assetid: bb3d90aa-5f08-4953-9be0-be6cea11633d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e0cde5d1ddd5dabfd42a6a7d31284736e24fa302
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2018
---
# <a name="advanced-settings-dialog-box-concurrency-visualizer"></a>Paramètres avancés, boîte de dialogue (visualiseur concurrentiel)
La boîte de dialogue **Paramètres avancés** du visualiseur concurrentiel vous permet de contrôler la façon dont les traces sont collectées.  La boîte de dialogue comprend des onglets pour les symboles, « Uniquement mon code », la mise en mémoire tampon, le filtrage, les événements du CLR, les marqueurs, les fournisseurs et les fichiers.  
  
## <a name="symbols"></a>Symboles  
 Le visualiseur concurrentiel utilise les mêmes paramètres de symboles que le débogueur Visual Studio. Le visualiseur concurrentiel utilise les paramètres pour résoudre les piles d’appels associées aux données de performance.  Quand il traite des traces, le visualiseur concurrentiel accède aux serveurs de symboles spécifiés dans la page des paramètres.  Si ces données sont accessibles sur un réseau, le traitement des traces ralentit.  Pour réduire la durée nécessaire à la résolution des symboles, vous pouvez les mettre en cache localement. Si les symboles ont été téléchargés, Visual Studio les charge à partir du cache local.  
  
## <a name="just-my-code"></a>Uniquement mon code  
 Par défaut, « Uniquement mon code » regroupe l’ensemble des fichiers .exe et .dll associés à la solution active dans Visual Studio. Le Visualiseur concurrentiel évalue cet ensemble de fichiers quand vous utilisez la fonctionnalité « Uniquement mon code » pour filtrer les piles des appels. Sous l’onglet Uniquement mon code, vous pouvez ajouter des répertoires qui contiennent les fichiers .exe ou .dll aux emplacements qu’utilise le visualiseur concurrentiel pour « Uniquement mon code ».  
  
 Les chemins des fichiers .exe et .dll sont stockés dans le fichier de trace quand la trace est collectée.  La modification de ce paramètre n’affecte pas les traces déjà collectées.  
  
## <a name="buffering"></a>Mise en mémoire tampon  
 Le visualiseur concurrentiel utilise le suivi d’événements pour Windows (ETW) quand il collecte une trace.  ETW utilise plusieurs mémoires tampons quand il stocke des événements.  Les paramètres de mémoire tampon ETW par défaut peuvent ne pas être optimaux dans tous les cas. Ils peuvent même provoquer des problèmes tels que la perte d’événements dans certaines situations.  Vous pouvez utiliser l’onglet Mise en mémoire tampon pour configurer les paramètres de mémoire tampon ETW. Pour plus d’informations, consultez [Traçage d’événements](http://go.microsoft.com/fwlink/?LinkId=234579) et [Structure d’EVENT_TRACE_PROPERTIES](http://go.microsoft.com/fwlink/?LinkId=234580).  
  
## <a name="filter"></a>Filtre  
 Sous l’onglet Filtre, vous pouvez sélectionner le jeu d’événements collecté par le visualiseur concurrentiel. La sélection d’un sous-ensemble d’événements limite les types de données qui s’affichent dans les rapports, réduit la taille de chaque trace et accélère le traitement des traces.  
  
### <a name="clr-events"></a>Événements CLR  
 Les événements générés par le Common Langage Runtime (CLR) permettent au visualiseur concurrentiel de résoudre les piles d’appels managées.  Si vous désactivez la collecte d’événements du CLR, la taille de la trace est réduite, mais certaines piles d’appels ne sont pas résolues.  Il peut donc arriver que certaines activités de thread de l’UC ne soient pas correctement catégorisées.  
  
### <a name="collect-for-native-processes"></a>Collecter les processus natifs  
 Par défaut, les événements du CLR sont collectés uniquement quand un processus managé est profilé car ils ne sont normalement pas nécessaires pour les processus natifs.  Dans certains cas (par exemple, quand un processus natif héberge le CLR), vous devrez peut-être collecter les événements du CLR pour un processus natif.  Si tel est le cas, cochez la case **Collecter les processus natifs**.  
  
### <a name="disable-rundown-events"></a>Désactiver les événements d’arrêt  
 Le CLR génère des événements de deux fournisseurs : runtime et rundown.  Si vous souhaitez collecter les événements du runtime du CLR sans toutefois collecter les événements d’arrêt, cochez la case **Désactiver les événements d’arrêt**.  Cela permet de réduire la taille du fichier de trace généré par la collection, mais il est possible que certaines piles ne soient pas résolues. Pour plus d’informations, consultez [Fournisseurs ETW du CLR](/dotnet/framework/performance/clr-etw-providers).  
  
### <a name="sample-events"></a>Échantillonner les événements  
 Vous pouvez utiliser des événements d’échantillon pour collecter les piles des appels associées à l’exécution de threads. Ces événements sont collectés environ une fois par milliseconde pour les threads qui s’exécutent dans le processus actif. Si vous désactivez la collecte d’événements d’échantillon, vous réduisez la taille de la trace collectée, mais vous ne pouvez pas afficher les piles des appels associées à l’exécution de threads.  
  
### <a name="gpu-events"></a>Événements GPU  
 Les événements GPU sont des événements générés par DirectX. Si vous désactivez la collecte d’événements GPU, vous réduisez la taille de la trace collectée, mais vous ne pouvez pas afficher l’activité GPU dans la vue Utilisation, ni l’activité Moteur DirectX dans la vue Threads.  
  
### <a name="file-io-events"></a>Événements d'E/S de fichier  
 Les événements d’E/S de fichier représentent les accès au disque pour le compte du processus actuel.  Si vous désactivez les événements d’E/S de fichier, vous réduisez la taille de la trace, mais la vue Threads ne signale aucune information sur les canaux de disque ou des opérations de disque.  
  
## <a name="markers"></a>Markers  
 Sous l’onglet Marqueurs, vous pouvez configurer l’ensemble des fournisseurs ETW affichés comme Marqueurs dans le visualiseur concurrentiel.  Vous pouvez également filtrer la collection de marqueurs selon le niveau d’importance et la catégorie ETW.  Si vous utilisez le [kit SDK du visualiseur concurrentiel](../profiling/concurrency-visualizer-sdk.md) et votre propre fournisseur de marqueurs, vous pouvez l’inscrire ici pour qu’il apparaisse dans la vue Threads.  
  
### <a name="adding-a-new-provider"></a>Ajouter un nouveau fournisseur  
 Si votre code utilise le [SDK du visualiseur concurrentiel](../profiling/concurrency-visualizer-sdk.md) ou génère des événements ETW qui respectent la convention <xref:System.Diagnostics.Tracing.EventSource>, vous pouvez afficher ces événements dans le visualiseur concurrentiel en les inscrivant dans cette boîte de dialogue.  
  
 Dans le champ Nom, entrez un nom qui décrit les types d’événements générés par le fournisseur.  Dans le champ de GUID, entrez le GUID associé à ce fournisseur. (Un GUID est associé à chaque fournisseur ETW.)  
  
 Vous pouvez éventuellement indiquer si vous souhaitez filtrer les événements de ce fournisseur selon la catégorie ou le niveau d’importance.  Vous pouvez utiliser le champ Catégorie pour filtrer les événements en fonction des catégories du kit SDK du visualiseur concurrentiel.  Pour cela, entrez une chaîne délimitée par des virgules de catégories ou de plages de catégories.  Cela permet de spécifier les catégories d’événements dans le fournisseur actif à afficher.  Si vous ajoutez un fournisseur <xref:System.Diagnostics.Tracing.EventSource>, vous pouvez utiliser le champ Catégorie pour filtrer les événements par mot clé ETW.  Étant donné que le mot clé est un masque de bits, vous pouvez utiliser une chaîne d’entiers délimitée par des virgules pour spécifier les bits définis dans le masque. Par exemple, « 1,2 » définit les premier et deuxième bits, ce qui se traduit par 6 au format décimal.  
  
 Vous pouvez utiliser la liste de niveaux d’importance pour filtrer les événements qui ont une importance ou un niveau ETW inférieur à la valeur spécifiée.  
  
### <a name="configuring-an-existing-provider"></a>Configuration d’un fournisseur existant  
 Pour modifier les paramètres associés à un fournisseur existant, sélectionnez-le dans la liste, puis choisissez le bouton **Modifier le fournisseur**.  Vous pouvez modifier le nom, le GUID et les paramètres de filtrage.  
  
### <a name="filter-marker-data-out-of-concurrency-visualizer-reports"></a>Exclure les données de marqueur des rapports du visualiseur concurrentiel  
 Si vous ne voulez pas que les données d’un fournisseur particulier s’affichent dans les futures traces, décochez la case située à coté du fournisseur à supprimer.  
  
## <a name="files"></a>Fichiers  
 Sous l’onglet **Fichiers**, vous pouvez spécifier le répertoire dans lequel les fichiers de trace sont stockés chaque fois qu’une trace est collectée.  Le visualiseur concurrentiel génère quatre fichiers pour chaque trace qu’il collecte :  
  
-   Un fichier ETL (Event Trace Log) en mode noyau (*.kernel.etl)  
  
-   Un fichier ETL (Event Trace Log) en mode utilisateur (*.user.etl)  
  
-   Un fichier de données Visualiseur concurrentiel (*.CVData)  
  
-   Un fichier de trace Visualiseur concurrentiel (*.CVTrace)  
  
 Les deux fichiers ETL stockent les données de trace brutes, et les deux fichiers du visualiseur concurrentiel stockent les données gérées.  Les fichiers ETL bruts ne sont généralement pas utilisés après le traitement d’une trace.  Pour réduire la quantité de données de trace stockées sur votre disque, cochez la case **Supprimer les fichiers ETL (Event Trace Log) après l’analyse**.  
  
## <a name="see-also"></a>Voir aussi  
 [Uniquement mon code](../profiling/just-my-code-threads-view.md)   
 [Marqueurs du visualiseur concurrentiel](../profiling/concurrency-visualizer-markers.md)