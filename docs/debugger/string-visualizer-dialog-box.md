---
title: Visualiseur de chaîne, boîte de dialogue | Microsoft Docs
description: Affichez les chaînes avec la boîte de dialogue visualiseur de chaîne intégré pendant le débogage dans Visual Studio.
ms.date: 10/10/2018
ms.custom: contperf-fy21q4
ms.topic: reference
f1_keywords:
- vs.debug.stringviewer
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JavaScript
helpviewer_keywords:
- string visualizer
- visualizers, string
ms.assetid: 080fd8f1-72b0-461f-8451-3c84d5dc51df
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 85092f6a339fdaaa3ddaa56112cc351d8b8e9bdc
ms.sourcegitcommit: dd2fc6e03a789c044f8438096b8f112e4dba5557
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/06/2021
ms.locfileid: "108640839"
---
# <a name="string-visualizer-dialog-box"></a>Visualiseur de chaîne, boîte de dialogue

Pendant le débogage dans Visual Studio, vous pouvez afficher les chaînes avec le visualiseur de chaîne intégré. Le visualiseur de chaîne affiche des chaînes qui sont trop longues pour une fenêtre de débogage ou une info-bulle de données. Il peut également vous aider à identifier des chaînes mal formées.

Les visualiseurs de chaînes intégrés incluent des options [Text](#text-string-data), [XML](#xml-string-data), [HTML](#html-string-data)et [JSON](#json-string-data) . Vous pouvez également ouvrir des visualiseurs intégrés pour quelques autres types, tels que les objets [DataSet, DataTable et DataView](../debugger/dataset-visualizer-dialog-box.md) , à partir de la fenêtre **automatique** ou d’autres fenêtres du débogueur.

> [!NOTE]
> Si vous devez inspecter des éléments d’interface utilisateur XAML ou WPF dans un visualiseur, consultez ou [Inspectez les propriétés XAML pendant le débogage](../xaml-tools/inspect-xaml-properties-while-debugging.md) ou [comment utiliser le visualiseur de l’arborescence WPF](../debugger/how-to-use-the-wpf-tree-visualizer.md).

Pour ouvrir le visualiseur de chaîne, vous devez être suspendu pendant le débogage. Pointez sur une variable qui a une valeur de chaîne en texte brut, XML, HTML ou JSON, puis sélectionnez l’icône de loupe ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "Icône de visualiseur").

## <a name="uielement-list"></a>Liste des éléments de l'interface utilisateur

Champ **expression** affiche la variable ou l’expression sur laquelle pointe le pointage.

Champ de **valeur** affiche la valeur de chaîne. Une **valeur** vide signifie que le visualiseur choisi ne peut pas reconnaître la chaîne. Par exemple, le **Visualiseur XML** affiche une **valeur** vide pour une chaîne de texte sans balises XML, ou une chaîne JSON. Pour afficher les chaînes que le visualiseur choisi ne peut pas reconnaître, choisissez le **visualiseur de texte** à la place. Le **visualiseur de texte** affiche le texte brut.

### <a name="text-string-data"></a>Données de chaîne de texte

Le **visualiseur de texte** affiche le texte brut. Si vous avez besoin d’une mise en forme personnalisée pour une chaîne C++, créez une [visualisation Natvis](../debugger/create-custom-views-of-native-objects.md).

![Visualiseur de chaîne de texte](../debugger/media/dbg-string-visualizer-text.png "Visualiseur de chaîne de texte")

### <a name="json-string-data"></a>Données de chaîne JSON

Une chaîne JSON correcte s’apparente à l’illustration suivante dans le visualiseur JSON. Un JSON mal formé peut afficher une icône d’erreur (ou vide si non reconnu). Pour identifier l’erreur JSON, copiez et collez la chaîne dans un outil de non-peluche JSON tel que [JSLint](https://www.jslint.com/).

![Visualiseur de chaîne JSON](../debugger/media/dbg-tips-string-visualizer-json.png "Visualiseur de chaîne JSON")

### <a name="xml-string-data"></a>Données de chaîne XML

Une chaîne XML correctement formée ressemble à l’illustration suivante dans le visualiseur XML. Du code XML incorrect peut s’afficher sans les balises XML, ou vide s’il n’est pas reconnu.

![Visualiseur de chaîne XML](../debugger/media/dbg-string-visualizers-xml.png "Visualiseur de chaîne XML")

### <a name="html-string-data"></a>Données de chaîne HTML

Une chaîne HTML correcte s’affiche comme si elle était rendue dans un navigateur, comme indiqué dans l’illustration suivante. Le code HTML incorrect peut s’afficher sous forme de texte brut.

![Visualiseur de chaîne HTML](../debugger/media/dbg-string-visualizers-html.png "Visualiseur de chaîne HTML")

## <a name="see-also"></a>Voir aussi

- [Créer des visualiseurs personnalisés (C#, Visual Basic)](../debugger/create-custom-visualizers-of-data.md)
- [Visualisations de données dans Visual Studio pour Mac](/visualstudio/mac/data-visualizations)