---
title: Afficher les chaînes dans un visualiseur de chaîne | Documents Microsoft
ms.custom: ''
ms.date: 07/11/2017
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.stringviewer
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
helpviewer_keywords:
- string visualizer
- visualizers, string
ms.assetid: 080fd8f1-72b0-461f-8451-3c84d5dc51df
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a3a0575b02422bf83dd560d3eae5724b0a50d3f3
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31476973"
---
# <a name="view-strings-in-a-string-visualizer-in-visual-studio"></a>Afficher les chaînes dans un visualiseur de chaîne dans Visual Studio
Pendant le débogage, vous pouvez ouvrir un visualiseur de chaîne à afficher les chaînes qui sont trop longs à afficher dans une fenêtre d’info-bulle ou le débogueur de données. Dans de nombreux scénarios, le visualiseur peut vous aider à identifier des chaînes incorrect.

Les visualiseurs standard de chaîne intégrées incluent du texte brut, XML, HTML et JSON. Pour d’autres types, tels que les objets WPF qui s’affichent dans le débogueur windows comme la **automatique** fenêtre, vous pouvez également ouvrir des visualiseurs.

## <a name="open-a-string-visualizer"></a>Ouvrir un visualiseur de chaîne

Pour afficher un texte brut, la chaîne JSON, HTML ou XML, cliquez sur l’icône de loupe ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "icône de visualiseur") tout en pointant sur une variable qui contient une valeur de chaîne. Vous devez être suspendu dans le débogueur pour afficher l’icône de loupe.

![Ouvrir un visualiseur de chaîne](../debugger/media/dbg-tips-string-visualizers.png "OpenStringVisualizer")

## <a name="view-string-data"></a>Afficher les données de chaîne

Le **Expression** champ dans le visualiseur de chaîne indique la variable actuelle ou l’expression que vous dessus dans le débogueur.

Le **valeur** champ affiche la valeur de chaîne. Le visualiseur de texte affiche le texte brut.

Une valeur vide **valeur** indique que le visualiseur spécifique ne peut pas reconnaître le type de chaîne. Par exemple, le visualiseur XML présente une valeur vide **valeur** pour la chaîne mise en forme une chaîne de texte simple (avec aucune balise XML) ou JSON. Si vous avez besoin afficher une chaîne non reconnaissable dans un visualiseur, utilisez le visualiseur de texte.

### <a name="view-json-string-data"></a>Afficher les données de chaîne JSON

Une chaîne JSON correcte sera identique à l’illustration suivante dans le visualiseur JSON. JSON incorrect peut afficher une icône d’erreur (ou vide si non reconnu).

![Visualiseur de chaîne JSON](../debugger/media/dbg-tips-string-visualizer-json.png "visualiseur de chaîne JSON")

### <a name="view-xml-string-data"></a>Afficher les données de chaîne XML

Il ressemble à une chaîne XML bien formée à l’illustration suivante dans le visualiseur XML. Code XML incorrect peut s’afficher sans les balises XML (ou vide si non reconnu).

![Visualiseur de chaîne XML](../debugger/media/dbg-string-visualizers-xml.png "visualiseur de chaîne XML")

### <a name="view-html-string-data"></a>Données de chaîne d’affichage HTML

Une chaîne au format HTML bien formée est semblable à la vue que vous verriez si la chaîne est rendue dans un navigateur, comme indiqué dans l’illustration suivante. HTML incorrect peut s’afficher sous forme de texte brut.

![Visualiseur de chaîne au format HTML](../debugger/media/dbg-string-visualizers-html.png "visualiseur de chaîne au format HTML")

## <a name="see-also"></a>Voir aussi  
 [Créer des visualiseurs personnalisés (c#, Visual Basic)](../debugger/create-custom-visualizers-of-data.md)