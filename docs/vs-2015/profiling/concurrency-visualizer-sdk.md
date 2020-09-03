---
title: Kit SDK du visualiseur concurrentiel | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.sdk.about
ms.assetid: 4b22cdf9-59b1-4c88-a6d8-1644a4a11e08
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ed93d852e385a6130cd37b0f66c99b4f0ab467bc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "82586801"
---
# <a name="concurrency-visualizer-sdk"></a>Kit de développement logiciel (SDK) du visualiseur concurrentiel
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez instrumenter votre code source à l’aide du kit SDK du visualiseur concurrentiel pour afficher des informations supplémentaires dans le visualiseur concurrentiel. Vous pouvez associer les données supplémentaires à des phases et à des événements de votre code. Ces visualisations supplémentaires sont appelées *marqueurs*.  Pour obtenir une introduction pas à pas, consultez [Introducing the Concurrency Visualizer SDK](https://docs.microsoft.com/archive/blogs/visualizeparallel/introducing-the-concurrency-visualizer-sdk).

## <a name="properties"></a>Propriétés
 Les indicateurs, les intervalles et les messages ont deux propriétés : la catégorie et l’importance. Dans la boîte de dialogue [Paramètres avancés](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md), vous pouvez utiliser ces propriétés pour filtrer l’affichage des marqueurs. Ces propriétés ont également un impact sur la représentation visuelle des marqueurs. Par exemple, la taille des indicateurs est utilisée pour représenter l’importance. La couleur, quant à elle, est utilisée pour indiquer la catégorie.

## <a name="basic-usage"></a>Utilisation de base
 Le visualiseur concurrentiel expose un fournisseur par défaut que vous pouvez utiliser pour générer des marqueurs. Le fournisseur est déjà inscrit avec le visualiseur concurrentiel. Aucune autre étape n’est donc nécessaire pour afficher les marqueurs dans l’interface utilisateur.

### <a name="c-and-visual-basic"></a>C# et Visual Basic

En C#, en Visual Basic et dans tout autre code managé, utilisez le fournisseur par défaut en appelant des méthodes dans la classe [Markers](/previous-versions/hh694099(v=vs.140)). Il expose quatre méthodes pour générer des marqueurs : [WriteFlag](/previous-versions/hh694185(v=vs.140)), [EnterSpan](/previous-versions/hh694205(v=vs.140)), [WriteMessage](/previous-versions/hh694161(v=vs.140))et [WriteAlert](/previous-versions/hh694180(v=vs.140)). Il existe plusieurs surcharges pour ces fonctions, selon que vous souhaitez utiliser les valeurs par défaut des propriétés.  La surcharge la plus simple accepte un seul paramètre de chaîne qui spécifie la description de l’événement. La description s’affiche dans les rapports du visualiseur concurrentiel.

#### <a name="add-sdk-support-to-a-c-or-visual-basic-project"></a>Ajout de la prise en charge du SDK à un projet C# ou Visual Basic

1. Dans la barre de menus, choisissez **Analyser**, **Visualiseur concurrentiel**, **Ajouter le SDK au projet**.

2. Sélectionnez le projet dans lequel vous souhaitez accéder au kit SDK, puis cliquez sur le bouton **Ajouter le SDK au projet sélectionné**.

3. Ajoutez une instruction imports ou using à votre code.

    ```csharp
    using Microsoft.ConcurrencyVisualizer.Instrumentation;
    ```

    ```vb
    Imports Microsoft.ConcurrencyVisualizer.Instrumentation
    ```

### <a name="c"></a>C++
 En C++, créez un objet de [classe marker_series](../profiling/marker-series-class.md) et utilisez-le pour appeler des fonctions.  La classe `marker_series` expose trois fonctions pour générer des marqueurs : la [méthode marker_series::write_flag](../profiling/marker-series-write-flag-method.md), la [méthode marker_series::write_message](../profiling/marker-series-write-message-method.md) et la [méthode marker_series::write_alert](../profiling/marker-series-write-alert-method.md).

##### <a name="to-add-sdk-support-to-a-c-or-c-project"></a>Pour ajouter la prise en charge du kit SDK à un projet C++ ou C

1. Dans la barre de menus, choisissez **Analyser**, **Visualiseur concurrentiel**, **Ajouter le SDK au projet**.

2. Sélectionnez le projet dans lequel vous souhaitez accéder au kit SDK, puis cliquez sur le bouton **Ajouter le SDK au projet sélectionné**.

3. En C++, ajoutez `cvmarkersobj.h`. En C, ajoutez `cvmarkers.h`.

4. Ajoutez une instruction using à votre code.

    ```cpp
    using namespace Concurrency::diagnostic;
    ```

5. Créez un objet `marker_series` et passez-le au constructeur `span`.

    ```cpp
    marker_series mySeries;
    span s(mySeries, _T("Span description"));
    ```

## <a name="custom-usage"></a>Utilisation personnalisée
 Pour les scénarios avancés, le kit SDK du visualiseur concurrentiel peut permettre un plus grand contrôle. Deux grands concepts sont associés aux scénarios plus avancés : les fournisseurs de marqueurs et les séries de marqueurs. Les fournisseurs de marqueurs sont différents des fournisseurs ETW (car ils ont chacun leur propre GUID). Les séries de marqueurs sont des canaux d’événements en série qui sont générés par un fournisseur. Vous pouvez les utiliser pour organiser les événements générés par un fournisseur de marqueurs.

#### <a name="to-use-a-new-marker-provider-in-a-c-or-visual-basic-project"></a>Pour utiliser un nouveau fournisseur de marqueurs dans un projet C# ou Visual Basic

1. Créez un objet [MarkerWriter](/previous-versions/hh694138(v=vs.140)). Le constructeur accepte un GUID.

2. Pour inscrire le fournisseur, ouvrez la boîte de dialogue [Paramètres avancés](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) du visualiseur concurrentiel.  Sélectionnez l’onglet **Marqueurs**, puis cliquez sur le bouton **Ajouter un nouveau fournisseur**. Dans la boîte de dialogue [Paramètres avancés](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md), entrez le GUID qui a été utilisé pour créer le fournisseur, ainsi que la description du fournisseur.

#### <a name="to-use-a-new-marker-provider-in-a-c-or-c-project"></a>Pour utiliser un nouveau fournisseur de marqueurs dans un projet C++ ou C

1. Utilisez la fonction `CvInitProvider` pour initialiser un PCV_PROVIDER. Le constructeur prend un GUID * et PCV_PROVIDER \* .

2. Pour inscrire le fournisseur, ouvrez la boîte de dialogue [Paramètres avancés](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md). Sélectionnez l’onglet **Marqueurs**, puis cliquez sur le bouton **Ajouter un nouveau fournisseur**. Dans la boîte de dialogue, entrez le GUID qui a été utilisé pour créer le fournisseur, ainsi que la description du fournisseur.

#### <a name="to-use-a-marker-series-in-a-c-or-visual-basic-project"></a>Pour utiliser une série de marqueurs dans un projet C# ou Visual Basic

1. Pour utiliser un nouveau [MarkerSeries](/previous-versions/hh694127(v=vs.140)), commencez par en créer un à l’aide d’un objet [MarkerWriter](/previous-versions/hh694138(v=vs.140)), puis générez les événements de marqueur directement à partir de la nouvelle série.

    ```csharp
    MarkerSeries series1 = myMarkerWriter.CreateMarkerSeries(″Series 1″);
    series1.WriteFlag(″My flag″);
    ```

    ```vb
    Dim series1 As New myMarkerWriter.CreateMarkerSeries(″Series 1″)
    series1.WriteFlag(″My flag″)
    ```

#### <a name="to-use-a-marker-series-in-a-c-project"></a>Pour utiliser une série de marqueurs dans un projet en C++

1. Créez un objet `marker_series`.  Vous pouvez générer des événements à partir de cette nouvelle série.

    ```scr
    marker_series series;
    series.write_flag(_T("Hello world!"));
    ```

#### <a name="to-use-a-marker-series-in-a-c-project"></a>Pour utiliser une série de marqueurs dans un projet en C

1. Utilisez la fonction `CvCreateMarkerSeries` pour créer une série PCV_MARKERSERIES.

    ```cpp
    PCV_MARKERSERIES series;
    CvCreatemarkerSeries(myProvider, _T("My Series"), &series);
    CvWriteFlag(series, _T("Writing a flag"));
    ```

## <a name="related-topics"></a>Rubriques connexes

|Titre|Description|
|-----------|-----------------|
|[Informations de référence sur la bibliothèque C++](../profiling/cpp-library-reference.md)|Décrit l’API du visualiseur concurrentiel pour le langage C++.|
|[Informations de référence sur la bibliothèque C](../profiling/c-library-reference.md)|Décrit l’API du visualiseur concurrentiel pour le langage C.|
|[Instrumentation](/previous-versions/hh694104(v=vs.140))|Décrit l’API du visualiseur concurrentiel pour le code managé.|
|[Visualiseur concurrentiel](../profiling/concurrency-visualizer.md)|Informations de référence sur les vues et rapports des fichiers de données de profilage générés à l’aide de la méthode de concurrence et qui incluent des données d’exécution des threads.|
