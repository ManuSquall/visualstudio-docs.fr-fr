---
title: 'Comment : tester et déboguer un visualiseur | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6189abf72a8459618a83a4e5b12d5c3edb1b6a52
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-test-and-debug-a-visualizer"></a>Comment : tester et déboguer un visualiseur
Après avoir écrit un visualiseur, vous devez le déboguer et le tester.  
  
 Une façon de tester un visualiseur consiste à l'installer dans Visual Studio et de l'appeler d'une fenêtre du débogueur. (Consultez [Comment : installer un visualiseur](../debugger/how-to-install-a-visualizer.md).) Si vous procédez ainsi, vous devez utiliser une deuxième instance de Visual Studio pour attacher et déboguer le visualiseur, qui s'exécute dans la première instance du débogueur.  
  
 Une façon plus facile de déboguer un visualiseur consiste à exécuter ce dernier à partir d'un pilote de test. Les API du visualiseur facilitent la création de ce type de pilote est appelée la *hôte de développement de visualiseur*.  
  
### <a name="to-create-a-visualizer-development-host"></a>Pour créer un hôte de développement de visualiseur  
  
1.  Dans votre classe côté débogueur, incluez une méthode statique qui crée un objet <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerDevelopmentHost> et appelle sa méthode Show :  
  
    ```  
    public static void TestShowVisualizer(object objectToVisualize)  
    {  
       VisualizerDevelopmentHost myHost = new VisualizerDevelopmentHost(objectToVisualize, typeof(DebuggerSide));  
       myHost.ShowVisualizer();  
    }  
    ```  
  
     Les paramètres utilisés pour construire l'hôte sont l'objet de données qui sera affiché dans le visualiseur (`objectToVisualize`) et le type de la classe côté débogueur.  
  
2.  Ajoutez l'instruction suivante pour appeler `TestShowVisualizer`. Si vous avez créé votre visualiseur dans une bibliothèque de classes, vous devez créer un fichier exécutable pour appeler la bibliothèque de classes et placer l'instruction suivante dans votre fichier exécutable :  
  
    ```  
    DebuggerSide.TestShowVisualizer(myString);  
    ```  
  
     Pour obtenir un exemple plus complet, consultez [procédure pas à pas : écriture d’un visualiseur en c#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Procédure pas à pas : Écriture d’un visualiseur en c#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)   
 [Comment : installer un visualiseur](../debugger/how-to-install-a-visualizer.md)   
 [Créer des visualiseurs personnalisés](../debugger/create-custom-visualizers-of-data.md)