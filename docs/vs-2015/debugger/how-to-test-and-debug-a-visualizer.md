---
title: 'Comment : tester et déboguer un visualiseur | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: 00fb749505f8bfe16c353552aa3afcb9eaaefc2d
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51723286"
---
# <a name="how-to-test-and-debug-a-visualizer"></a>Comment : tester et déboguer un visualiseur
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Après avoir écrit un visualiseur, vous devez le déboguer et le tester.  
  
 Une façon de tester un visualiseur consiste à l'installer dans Visual Studio et de l'appeler d'une fenêtre du débogueur. (Consultez [Comment : installer un visualiseur](../debugger/how-to-install-a-visualizer.md).) Si vous procédez ainsi, vous devez utiliser une deuxième instance de Visual Studio pour attacher et déboguer le visualiseur, qui s'exécute dans la première instance du débogueur.  
  
 Une façon plus facile de déboguer un visualiseur consiste à exécuter ce dernier à partir d'un pilote de test. Les API du visualiseur facilitent la création de ce type de pilote qui est appelé le *hôte de développement de visualiseur*.  
  
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



