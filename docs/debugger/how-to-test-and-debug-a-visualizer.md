---
title: Tester et déboguer un visualiseur | Microsoft Docs
description: Tester et déboguer un visualiseur en l’exécutant à partir d’un pilote de test (hôte de développement du visualiseur) ou en installant dans Visual Studio et en l’appelant à partir d’une fenêtre du débogueur.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- visualizers, testing
- visualizers, debugging
- debugging [Visual Studio], visualizers
ms.assetid: 5cc12ce8-c819-48e4-b487-98d403001b28
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1326fe9731a9d938678eb9397b106ab9e71b4fd5
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/13/2021
ms.locfileid: "98150663"
---
# <a name="how-to-test-and-debug-a-visualizer"></a>Comment : tester et déboguer un visualiseur
Après avoir écrit un visualiseur, vous devez le déboguer et le tester.

Une façon de tester un visualiseur consiste à l'installer dans Visual Studio et de l'appeler d'une fenêtre du débogueur. (Consultez [Comment : installer un visualiseur](../debugger/how-to-install-a-visualizer.md).) Dans ce cas, vous devrez utiliser une deuxième instance de Visual Studio pour attacher et déboguer le visualiseur, qui s’exécute dans la première instance du débogueur.

Une façon plus facile de déboguer un visualiseur consiste à exécuter ce dernier à partir d'un pilote de test. Les API du visualiseur facilitent la création de ce type de pilote appelé *hôte de développement de visualiseur*.

### <a name="to-create-a-visualizer-development-host"></a>Pour créer un hôte de développement de visualiseur

1. Dans votre classe côté débogueur, incluez une méthode statique qui crée un objet <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerDevelopmentHost> et appelle sa méthode Show :

    ```csharp
    public static void TestShowVisualizer(object objectToVisualize)
    {
        VisualizerDevelopmentHost myHost = new VisualizerDevelopmentHost(objectToVisualize, typeof(DebuggerSide));
        myHost.ShowVisualizer();
    }
    ```

    Les paramètres utilisés pour construire l'hôte sont l'objet de données qui sera affiché dans le visualiseur (`objectToVisualize`) et le type de la classe côté débogueur.

2. Ajoutez l'instruction suivante pour appeler `TestShowVisualizer`. Si vous avez créé votre visualiseur dans une bibliothèque de classes, vous devez créer un fichier exécutable pour appeler la bibliothèque de classes et placer l'instruction suivante dans votre fichier exécutable :

    ```csharp
    DebuggerSide.TestShowVisualizer(myString);
    ```

    Pour obtenir un exemple plus complet, consultez [procédure pas à pas : écriture d’un visualiseur en C#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md).

## <a name="see-also"></a>Voir aussi
- [Procédure pas à pas : écriture d’un visualiseur en C #](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)
- [Comment : installer un visualiseur](../debugger/how-to-install-a-visualizer.md)
- [Créer des visualiseurs personnalisés](../debugger/create-custom-visualizers-of-data.md)
