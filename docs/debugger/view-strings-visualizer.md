---
title: Afficher des chaînes dans un visualiseur de chaîne | Microsoft Docs
ms.date: 04/08/2019
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JavaScript
helpviewer_keywords:
- string visualizer
- visualizers, string
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 33e1cbd4b1c754498d7e2bd6c354e874ae8cdad5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72450394"
---
# <a name="view-strings-in-a-string-visualizer-in-visual-studio"></a>Afficher des chaînes dans un visualiseur de chaîne dans Visual Studio

Pendant le débogage dans Visual Studio, vous pouvez afficher les chaînes avec le visualiseur de chaîne intégré. Le visualiseur de chaîne affiche des chaînes qui sont trop longues pour une fenêtre de débogage ou une info-bulle de données. Il peut également vous aider à identifier des chaînes mal formées.

Le visualiseur de chaîne intégré comprend des options de texte brut, XML, HTML et JSON. Vous pouvez également ouvrir des visualiseurs intégrés pour quelques autres types, tels que les objets [DataSet, DataTable et DataView](../debugger/dataset-visualizer-dialog-box.md) , à partir de la fenêtre **automatique** ou d’autres fenêtres du débogueur.

> [!NOTE]
> Si vous devez inspecter des éléments d’interface utilisateur XAML ou WPF dans un visualiseur, consultez ou [Inspectez les propriétés XAML pendant le débogage](../xaml-tools/inspect-xaml-properties-while-debugging.md) ou [comment utiliser le visualiseur de l’arborescence WPF](../debugger/how-to-use-the-wpf-tree-visualizer.md).

## <a name="open-a-string-visualizer"></a>Ouvrir un visualiseur de chaîne

Pour ouvrir le visualiseur de chaîne, vous devez être suspendu pendant le débogage. Pointez sur une variable qui a une valeur de chaîne en texte brut, XML, HTML ou JSON, puis sélectionnez l’icône de loupe ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "Icône de visualiseur").

![Ouvrir un visualiseur de chaîne](../debugger/media/dbg-tips-string-visualizers.png "Visualiseur de chaîne ouvert")

## <a name="view-string-visualizer-data"></a>Afficher les données du visualiseur de chaîne

Dans la fenêtre du visualiseur de chaîne, le champ **expression** affiche la variable ou l’expression sur laquelle vous pointez et le champ **valeur** affiche la valeur de chaîne.

Une **valeur** vide signifie que le visualiseur choisi ne peut pas reconnaître la chaîne. Par exemple, le **Visualiseur XML** affiche une **valeur** vide pour une chaîne de texte sans balises XML, ou une chaîne JSON.

Pour afficher les chaînes que le visualiseur choisi ne peut pas reconnaître, choisissez le **visualiseur de texte**. Le **visualiseur de texte** affiche le texte brut.

### <a name="view-json-string-data"></a>Afficher les données de chaîne JSON

Une chaîne JSON correcte s’apparente à l’illustration suivante dans le visualiseur JSON. Un JSON mal formé peut afficher une icône d’erreur (ou vide si non reconnu). Pour identifier l’erreur JSON, copiez et collez la chaîne dans un outil de non-peluche JSON tel que [JSLint](https://www.jslint.com/).

![Visualiseur de chaîne JSON](../debugger/media/dbg-tips-string-visualizer-json.png "Visualiseur de chaîne JSON")

### <a name="view-xml-string-data"></a>Afficher les données de chaîne XML

Une chaîne XML correctement formée ressemble à l’illustration suivante dans le visualiseur XML. Du code XML incorrect peut s’afficher sans les balises XML, ou vide s’il n’est pas reconnu.

![Visualiseur de chaîne XML](../debugger/media/dbg-string-visualizers-xml.png "Visualiseur de chaîne XML")

### <a name="view-html-string-data"></a>Afficher les données de chaîne HTML

Une chaîne HTML correcte s’affiche comme si elle était rendue dans un navigateur, comme indiqué dans l’illustration suivante. Le code HTML incorrect peut s’afficher sous forme de texte brut.

![Visualiseur de chaîne HTML](../debugger/media/dbg-string-visualizers-html.png "Visualiseur de chaîne HTML")

## <a name="see-also"></a>Voir aussi

- [Créer des visualiseurs personnalisés (C#, Visual Basic)](../debugger/create-custom-visualizers-of-data.md)
- [Visualisations de données dans Visual Studio pour Mac](/visualstudio/mac/data-visualizations)