---
title: Afficher les chaînes dans un visualiseur de chaîne | Microsoft Docs
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
ms.openlocfilehash: ffd19dccb69d3ae05a84ae49a280ff49c14f2809
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62930243"
---
# <a name="view-strings-in-a-string-visualizer-in-visual-studio"></a>Afficher les chaînes dans un visualiseur de chaîne dans Visual Studio

Lorsque vous déboguez dans Visual Studio, vous pouvez afficher les chaînes avec le visualiseur de chaîne intégrées. Le visualiseur de chaîne indique les chaînes qui sont trop longues pour une fenêtre d’info-bulle ou débogueur de données. Il peut également vous aider à identifier des chaînes mal formés.

Le visualiseur de chaîne intégrées inclut le texte brut, XML, HTML et JSON options. Vous pouvez également ouvrir intégrés visualiseurs pour d’autres types, tels que [DataSet, DataTable et DataView](../debugger/dataset-visualizer-dialog-box.md) objets, à partir de la **automatique** ou autres fenêtres du débogueur.

> [!NOTE]
> Si vous avez besoin inspecter les éléments XAML ou WPF UI dans un visualiseur, consultez ou [propriétés XAML inspecter pendant le débogage](../debugger/inspect-xaml-properties-while-debugging.md) ou [comment utiliser le visualiseur de l’arborescence WPF](../debugger/how-to-use-the-wpf-tree-visualizer.md).

## <a name="open-a-string-visualizer"></a>Ouvrir un visualiseur de chaîne

Pour ouvrir le visualiseur de chaîne, vous devez être suspendus pendant le débogage. Pointez sur une variable qui a un texte brut, XML, HTML ou JSON valeur de chaîne, puis sélectionnez l’icône de loupe ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "icône de visualiseur").

![Ouvrir un visualiseur de chaîne](../debugger/media/dbg-tips-string-visualizers.png "visualiseur de chaîne ouvert")

## <a name="view-string-visualizer-data"></a>Afficher les données de visualiseur de chaîne

Dans la fenêtre visualiseur de chaîne, le **Expression** champ indique la variable ou l’expression que vous pointez sur, et le **valeur** champ affiche la valeur de chaîne.

Une valeur vide **valeur** signifie que le visualiseur choisi ne peut pas reconnaître la chaîne. Par exemple, le **visualiseur XML** montre une valeur vide **valeur** pour une chaîne de texte avec les balises XML ou une chaîne JSON.

Pour afficher les chaînes qui le visualiseur choisi ne peut pas reconnaître, choisissez le **visualiseur de texte**. Le **visualiseur de texte** affiche le texte brut.

### <a name="view-json-string-data"></a>Afficher les données de chaîne JSON

Une chaîne JSON correcte est semblable à l’illustration suivante dans le visualiseur JSON. JSON incorrect peut afficher une icône d’erreur (ou est vide si non reconnu). Pour identifier l’erreur JSON, copier et coller la chaîne dans un outil de vérification (linting) JSON tels que [JSLint](https://www.jslint.com/).

![Visualiseur de chaîne JSON](../debugger/media/dbg-tips-string-visualizer-json.png "visualiseur de chaîne JSON")

### <a name="view-xml-string-data"></a>Afficher les données de chaîne XML

Une chaîne XML bien formée ressemble à l’illustration suivante dans le visualiseur XML. Code XML incorrect peut afficher sans les balises XML, ou est vide si non reconnu.

![Visualiseur de chaîne XML](../debugger/media/dbg-string-visualizers-xml.png "visualiseur de chaîne XML")

### <a name="view-html-string-data"></a>Données de chaîne d’affichage HTML

Une chaîne HTML bien formée apparaît comme s’affiché dans un navigateur, comme indiqué dans l’illustration suivante. Code HTML mal formé peut afficher en tant que texte brut.

![Visualiseur de chaîne HTML](../debugger/media/dbg-string-visualizers-html.png "visualiseur de chaîne HTML")

## <a name="see-also"></a>Voir aussi

- [Créer des visualiseurs personnalisés (c#, Visual Basic)](../debugger/create-custom-visualizers-of-data.md)
- [Visualisations de données dans Visual Studio pour Mac](/visualstudio/mac/data-visualizations)