---
title: "Comment&#160;: utiliser le Kit de d&#233;veloppement logiciel des marqueurs du visualiseur concurrentiel | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 19a45032-f8a7-4137-890e-2ceeec938b8d
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Comment&#160;: utiliser le Kit de d&#233;veloppement logiciel des marqueurs du visualiseur concurrentiel
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cette rubrique montre comment utiliser le Kit de Développement de visualiseur d’accès concurrentiel pour créer des étendues et d’écrire des indicateurs, des messages et des alertes.  
  
### <a name="to-use-c"></a>Utilisation de C++  
  
1.  Ajouter la prise en charge du Kit de Développement de visualiseur d’accès concurrentiel à votre application. Pour plus d’informations, consultez [Kit de Développement de visualiseur d’accès concurrentiel](../profiling/concurrency-visualizer-sdk.md).  
  
2.  Ajouter un `include` instruction et un `using` instruction pour le Kit de développement Logiciel.  
  
    ```cpp  
  
    #include <cvmarkersobj.h>  
    using namespace Concurrency::diagnostic;  
  
    ```  
  
3.  Ajoutez du code pour créer trois étendues de la série de marqueur par défaut et d’écrire un indicateur, un message et une alerte, un pour chaque intervalle. Les méthodes pour écrire les indicateurs, les alertes et les messages sont membres de la [marker_series](../profiling/marker-series-class.md) (classe). Le constructeur de la [span](../profiling/span-class.md) classe nécessite une `marker_series` de l’objet, afin que chaque intervalle est associé à une série de marqueur spécifique. Un `span` se termine lorsqu’il est supprimé.  
  
    ```cpp  
  
    marker_series series;  
    span *flagSpan = new span(series, 1, _T("flag span"));  
    series.write_flag(_T("Here is the flag."));  
    delete flagSpan;  
  
    span *messageSpan = new span(series, 2, _T("message span"));  
    series.write_flag(_T("Here is the message."));  
    delete messageSpan;  
  
    span *alertSpan = new span(series, 3, _T("alert span"));  
    series.write_flag(_T("Here is the alert."));  
    delete alertSpan;  
  
    ```  
  
4.  Dans la barre de menus, choisissez **analyser**, **visualiseur concurrentiel**, **commence par projet actuel** pour exécuter l’application et afficher le visualiseur concurrentiel. L’illustration suivante montre les trois étendues et trois marqueurs du visualiseur concurrentiel.  
  
     ![Visualiseur concurrentiel avec 3 marqueurs et alertes](../profiling/media/cvmarkersnative.png "CvMarkersNative")  
  
5.  Ajoutez du code pour créer des séries de marqueurs supplémentaires et personnalisés en appelant le constructeur de `marker_series` qui accepte un nom de chaîne pour la série de marqueur.  
  
    ```cpp  
  
    marker_series flagSeries(_T("flag series"));  
    span *flagSeriesSpan = new span(flagSeries, 1, _T("flag span"));  
    flagSeries.write_flag(1, _T("flag"));  
    // Sleep to even out the display in the Concurrency Visualizer.  
    Sleep(50);  
    delete flagSeriesSpan;  
  
    marker_series messageSeries(_T("message series"));  
    span *messageSeriesSpan = new span(messageSeries, 1, _T("message span"));  
    messageSeries.write_message(1, _T("message"));  
    // Sleep to even out the display in the Concurrency Visualizer.  
    Sleep(50);  
    delete messageSeriesSpan;  
  
    ```  
  
6.  Démarrer le projet en cours pour afficher le visualiseur concurrentiel. Les séries de deux marqueurs s’affichent dans leurs propres couloirs dans la vue Threads. L’illustration suivante montre deux nouvelles étendues.  
  
     ![Visualiseur concurrentiel avec 3 séries de marqueurs personnalisées](../profiling/media/cvmarkerseriesnative.png "CvMarkerSeriesNative")  
  
### <a name="to-use-visual-basic-or-c"></a>Pour utiliser Visual Basic ou C#  
  
1.  Ajouter la prise en charge du Kit de Développement de visualiseur d’accès concurrentiel à votre application. Pour plus d’informations, consultez [Kit de Développement de visualiseur d’accès concurrentiel](../profiling/concurrency-visualizer-sdk.md).  
  
2.  Ajouter un `using` ou `Imports` instruction pour le Kit de développement Logiciel.  
  
    ```vb  
    Imports Microsoft.ConcurrencyVisualizer.Instrumentation  
  
    ```  
  
    ```c#  
    using Microsoft.ConcurrencyVisualizer.Instrumentation;  
    ```  
  
3.  Ajoutez du code pour créer trois étendues sur la série de marqueur par défaut et d’écrire un indicateur, un message et une alerte, un pour chaque intervalle. Vous créez un <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.Span> objet en appelant la méthode statique [EnterSpan](assetId:///EnterSpan?qualifyHint=False&autoUpgrade=True) (méthode). Pour écrire dans la série par défaut, vous utilisez les méthodes statiques d’écriture de la <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.Markers> classe.  
  
    ```vb  
  
    Dim flagSpan As Span = Markers.EnterSpan("flag span")  
    Markers.WriteFlag("Here is the flag.")  
    flagSpan.Leave()  
  
    Dim messageSpan As Span = Markers.EnterSpan("message span")  
    ' Sleep for a millisecond to even out the display in the Concurrency Visualizer.  
    System.Threading.Thread.Sleep(1)  
    Markers.WriteMessage("Here is a message")  
    messageSpan.Leave()  
  
    Dim alertSpan As Span = Markers.EnterSpan("alert span")  
    ' Sleep for a millisecond to even out the display in the Concurrency Visualizer.  
    System.Threading.Thread.Sleep(1)  
    Markers.WriteAlert("Here is an alert")  
    alertSpan.Leave()  
  
    ```  
  
    ```c#  
  
    Span flagSpan = Markers.EnterSpan("flag span");  
    Markers.WriteFlag("Here is the flag.");  
    flagSpan.Leave();  
  
    Span messageSpan = Markers.EnterSpan("message span");  
    // Sleep for a millisecond to even out the display in the Concurrency Visualizer.  
    System.Threading.Thread.Sleep(1);  
    Markers.WriteMessage("Here is a message");  
    messageSpan.Leave();  
  
    Span alertSpan = Markers.EnterSpan("alert span");  
    // Sleep for a millisecond to even out the display in the Concurrency Visualizer.  
    System.Threading.Thread.Sleep(1);  
    Markers.WriteAlert("Here is an alert");  
    alertSpan.Leave();  
    ```  
  
4.  Dans la barre de menus, choisissez **analyser**, **visualiseur concurrentiel**, **commence par projet actuel** pour exécuter l’application et afficher le visualiseur concurrentiel. L’illustration suivante montre les trois étendues et des marqueurs de trois dans la vue Threads du visualiseur d’accès concurrentiel.  
  
     ![Visualiseur concurrentiel avec marqueurs et alertes](../profiling/media/cvmarkersmanaged.png "CvMarkersManaged")  
  
5.  Ajoutez du code pour créer des séries de marqueurs de client à l’aide de la méthode statique <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.Markers.CreateMarkerSeries%2A> (méthode). Le <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.MarkerSeries> classe contient des méthodes pour la création d’étendues et l’écriture des indicateurs, des messages et des alertes.  
  
    ```vb  
  
    Dim flagSeries As MarkerSeries = Markers.DefaultWriter.CreateMarkerSeries("flag series")  
    Dim flagSeriesSpan As Span = flagSeries.EnterSpan("flag span")  
    System.Threading.Thread.Sleep(1)  
    flagSeries.WriteFlag(1, "flag")  
    System.Threading.Thread.Sleep(1)  
    flagSeriesSpan.Leave()  
  
    Dim messageSeries As MarkerSeries = Markers.DefaultWriter.CreateMarkerSeries("message series")  
    Dim messageSeriesSpan As Span = messageSeries.EnterSpan("message span")  
    messageSeries.WriteMessage("message")  
    System.Threading.Thread.Sleep(1)  
    messageSeriesSpan.Leave()  
    ```  
  
    ```c#  
  
    MarkerSeries flagSeries = Markers.DefaultWriter.CreateMarkerSeries("flag series");  
    Span flagSeriesSpan = flagSeries.EnterSpan("flag span");  
    System.Threading.Thread.Sleep(1);  
    flagSeries.WriteFlag(1, "flag");  
    System.Threading.Thread.Sleep(1);  
    flagSeriesSpan.Leave();  
  
    MarkerSeries messageSeries = Markers.DefaultWriter.CreateMarkerSeries("message series");  
    Span messageSeriesSpan = messageSeries.EnterSpan("message span");  
    messageSeries.WriteMessage("message");  
    System.Threading.Thread.Sleep(1);  
    messageSeriesSpan.Leave();  
    ```  
  
6.  Démarrer le projet en cours pour afficher le visualiseur concurrentiel. La série de trois marqueur s’affichent dans leurs propres couloirs dans la vue Threads. L’illustration suivante montre trois nouvelles étendues.  
  
     ![Visualiseur concurrentiel avec 3 séries de marqueurs personnalisées](../profiling/media/cvmarkerseriesmanaged.png "CvMarkerSeriesManaged")  
  
## <a name="see-also"></a>Voir aussi  
 [Kit de développement Logiciel de visualisation concurrentielle](../profiling/concurrency-visualizer-sdk.md)