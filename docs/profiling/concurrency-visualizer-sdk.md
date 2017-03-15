---
title: "Kit de d&#233;veloppement logiciel (SDK) du visualiseur concurrentiel | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.cv.sdk.about"
ms.assetid: 4b22cdf9-59b1-4c88-a6d8-1644a4a11e08
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Kit de d&#233;veloppement logiciel (SDK) du visualiseur concurrentiel
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Vous pouvez instrumenter votre code source en utilisant le Kit de développement logiciel Visualiseur Concurrentiel pour afficher des informations supplémentaires dans le visualiseur d'accès concurrentiel.  Vous pouvez associer des informations supplémentaires avec les phases et des événements dans votre code.  Ces visualisations supplémentaires sont appelés *jetons*.  Pour une introduction sur le sujet, consultez [lntroduction au Concurrency Visualizer SDK](http://go.microsoft.com/fwlink/?LinkId=235405).  
  
## Propriétés  
 Les balises, les étendues, et les messages ont chacun deux propriétés : catégorie et importance.  Dans la boîte de dialogue [Paramètres avancés](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md), vous pouvez utiliser ces propriétés pour filtrer l'ensemble des jetons affichées.  En outre, ces propriétés affectent la représentation visuelle des jetons.  Par exemple, la taille des balises est utilisée pour représenter l'importance.  En outre, la couleur est utilisée pour indiquer la catégorie.  
  
## Utilisation de base  
 Le Visualiseur concurrentiel expose un fournisseur par défaut que vous pouvez utiliser pour générer des jetons.  Le fournisseur est déjà enregistré avec le Visualiseur concurrentiel et vous rien à faire d'autres pour inciter l'affichage des jetons dans l'interface utilisateur.  
  
### Visual Basic et C\#  
 En C\#, Visual Basic, et tout autre code managé, utilisez le fournisseur par défaut en appelant <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.Markers>.  Il expose quatre fonctions pour générer des jetons : <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.Markers.WriteFlag%2A>, <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.Markers.EnterSpan%2A>, <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.Markers.WriteMessage%2A>, et <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.Markers.WriteAlert%2A>.  Il y a plusieurs surcharges de ces fonctions, selon que vous souhaitez utiliser des valeurs par défaut pour les propriétés.  La surcharge la plus simple prend un seul paramètre de chaîne de caractères qui spécifie la description de l'événement.  La description s'affiche dans les rapports de Visualiseur concurrentiel.  
  
##### Pour ajouter la prise en charge du Kit de développement logiciel en C\# ou à un projet Visual Basic  
  
1.  Dans la barre de menus, sélectionnez **Analyser**, **Visualiseur concurrentiel**, **Ajouter le SDK au projet**.  
  
2.  Sélectionnez le projet dans lequel vous souhaitez accéder au Kit de développement logiciel puis choisissez le bouton **Ajouter le SDK au projet sélectionné**.  
  
3.  Ajoutez les importations ou l'instruction using à votre code.  
  
    ```c#  
    using Microsoft.ConcurrencyVisualizer.Instrumentation;  
    ```  
  
    ```vb  
    Imports Microsoft.ConcurrencyVisualizer.Instrumentation  
    ```  
  
### C\+\+  
 En C\+\+, créez un objet [marker\_series, classe](../profiling/marker-series-class.md) et utilisez\-le pour appeler des fonctions.  La classe `marker_series` expose trois fonctions pour générer des jetons, [marker\_series::write\_flag, méthode](../profiling/marker-series-write-flag-method.md), [marker\_series::write\_message, méthode](../profiling/marker-series-write-message-method.md), et [marker\_series::write\_alert, méthode](../profiling/marker-series-write-alert-method.md).  
  
##### Pour ajouter la prise en charge du Kit de développement logiciel en c\+\+ ou C projet  
  
1.  Dans la barre de menus, sélectionnez **Analyser**, **Visualiseur concurrentiel**, **Ajouter le SDK au projet**.  
  
2.  Sélectionnez le projet dans lequel vous souhaitez accéder au Kit de développement logiciel puis choisissez le bouton **Ajouter le SDK au projet sélectionné**.  
  
3.  Pour C\+\+, incluez `cvmarkersobj.h`.  Pour C, incluez `cvmarkers.h`.  
  
4.  Ajoutez une instruction using à votre code.  
  
    ```  
    using namespace Concurrency::diagnostic;  
    ```  
  
5.  Créez un objet `marker_series` et passez\-lui le constructeur `span`.  
  
    ```cpp  
  
    marker_series mySeries;  
    span s(mySeries, _T("Span description"));  
  
    ```  
  
## Utilisation personnalisée  
 Pour les scénarios avancés, le Kit de développement logiciel Visualiseur Concurrentiel expose plus de contrôle.  Deux concepts principaux sont associés à des scénarios plus avancés : fournisseurs de jeton et séries de jeton.  Les fournisseurs de jeton sont différents des fournisseurs ETW \(chacun a un GUID différent\).  Les séries de jetons sont les canaux séquentiels des événements qui sont générés par un fournisseur.  Vous pouvez l'utiliser pour organiser les événements qui sont générés par un fournisseur de jeton.  
  
#### Pour utiliser un fournisseur de jeton dans un projet C\# ou Visual Basic  
  
1.  Créez un objet <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.MarkerWriter>.  Le constructeur prend un GUID.  
  
2.  Pour enregistrer le fournisseur, ouvrez la boîte de dialogue [Paramètres avancés](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) du Visualiseur concurrentiel.  Sélectionnez l'onglet **Jetons** puis choisissez le bouton **Ajouter un nouveau fournisseur**.  Dans la boîte de dialogue [Paramètres avancés](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md), entrez un GUID qui a été utilisée pour créer le fournisseur et une description du fournisseur.  
  
#### Pour utiliser un fournisseur de jeton dans un projet C\+\+ ou C  
  
1.  Utilisez la fonction `CvInitProvider` pour initialiser un PCV\_PROVIDER.  Le constructeur prend un GUID\* et un PCV\_PROVIDER\*.  
  
2.  Pour enregistrer le fournisseur, ouvrez la boîte de dialogue [Paramètres avancés](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md).  Sélectionnez l'onglet **Jetons** puis choisissez le bouton **Ajouter un nouveau fournisseur**.  Dans cette boîte de dialogue, entrez GUID qui a été utilisé pour créer le fournisseur et une description du fournisseur.  
  
#### Pour utiliser la série d'un jeton dans un projet C\# ou Visual Basic  
  
1.  Pour utiliser un nouvel <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.MarkerSeries>, créez\-le d'abord à l'aide d'un objet <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.MarkerWriter>, et générez ensuite les événements de jeton directement à partir de la nouvelle série.  
  
    ```c#  
    MarkerSeries series1 = myMarkerWriter.CreateMarkerSeries(″Series 1″);  
    series1.WriteFlag(″My flag″);  
    ```  
  
    ```vb  
    Dim series1 As New myMarkerWriter.CreateMarkerSeries(″Series 1″)  
    series1.WriteFlag(″My flag″)  
    ```  
  
#### Pour utiliser la série d'un jeton dans un projet C\+\+  
  
1.  Créez un objet `marker_series`.  Vous pouvez générer des événements de cette nouvelle série.  
  
    ```scr  
    marker_series series;  
    series.write_flag(_T("Hello world!"));  
    ```  
  
#### Pour utiliser la série d'un jeton dans un projet C  
  
1.  Utilisez la fonction `CvCreateMarkerSeries` pour créer un PCV\_MARKERSERIES.  
  
    ```cpp  
    PCV_MARKERSERIES series;  
    CvCreatemarkerSeries(myProvider, _T("My Series"), &series);  
    CvWriteFlag(series, _T("Writing a flag"));  
    ```  
  
## Rubriques connexes  
  
|Titre|Description|  
|-----------|-----------------|  
|[Référence de bibliothèque C\+\+](../profiling/cpp-library-reference.md)|Décrit l'API du Visualiseur concurrentiel pour C\+\+.|  
|[Informations de référence sur la bibliothèque C](../profiling/c-library-reference.md)|Décrit l'API du Visualiseur concurrentiel pour C.|  
|<xref:Microsoft.ConcurrencyVisualizer.Instrumentation>|Décrit l'API du Visualiseur concurrentiel pour le code managé.|  
|[Visualiseur concurrence](../profiling/concurrency-visualizer.md)|Informations de référence pour les vues et rapports des fichiers de données de profilage générés à l'aide de la méthode de concurrence et comprenant des données d'exécution de thread.|