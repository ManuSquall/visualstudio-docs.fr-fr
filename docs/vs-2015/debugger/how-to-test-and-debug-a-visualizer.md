---
title: 'Procédure : Tester et déboguer un visualiseur | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- visualizers, testing
- visualizers, debugging
- debugging [Visual Studio], visualizers
ms.assetid: 5cc12ce8-c819-48e4-b487-98d403001b28
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d19fa9b1859e97b115ca0799520456c102fecac9
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58953274"
---
# <a name="how-to-test-and-debug-a-visualizer"></a>Procédure : tester et déboguer un visualiseur
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Après avoir écrit un visualiseur, vous devez le déboguer et le tester.  
  
 Une façon de tester un visualiseur consiste à l'installer dans Visual Studio et de l'appeler d'une fenêtre du débogueur. (Consultez [Guide pratique pour installer un visualiseur](../debugger/how-to-install-a-visualizer.md).) Si vous procédez ainsi, vous devez utiliser une deuxième instance de Visual Studio pour attacher et déboguer le visualiseur, qui s'exécute dans la première instance du débogueur.  
  
 Une façon plus facile de déboguer un visualiseur consiste à exécuter ce dernier à partir d'un pilote de test. Les API du visualiseur facilitent la création de ce type de pilote appelé *hôte de développement de visualiseur*.  
  
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
  
     Pour obtenir un exemple plus complet, consultez [procédure pas à pas : Écriture d’un visualiseur en C# ](../debugger/walkthrough-writing-a-visualizer-in-csharp.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Procédure pas à pas : Écriture d’un visualiseur en C#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)   
 [Guide pratique pour installer un visualiseur](../debugger/how-to-install-a-visualizer.md)   
 [Créer des visualiseurs personnalisés](../debugger/create-custom-visualizers-of-data.md)
