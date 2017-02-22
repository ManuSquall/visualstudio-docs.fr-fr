---
title: "Visualiseur de type et de la visionneuse personnalis&#233;e | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "débogage de visionneuse personnalisée [Debugging SDK],"
  - "visualiseur de type débogage [Debugging SDK],"
ms.assetid: fd3691e6-9c78-4767-846f-43f85ada4375
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# Visualiseur de type et de la visionneuse personnalis&#233;e
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

un visualiseur de type est un composant qui affiche une partie de données dans un format très spécifique.  Ce format est entièrement jusqu'à l'implémenteur du visualiseur, qu'elles touchent l'utilisateur final ou un tiers fournisseur les visualiseurs.  
  
 une visionneuse personnalisée est la partie d'un évaluateur d'expression personnalisé qui affiche une partie de données dans un format très spécifique.  Ce format est entièrement jusqu'à l'implémenteur de la visionneuse personnalisée, ce qui signifie que le format appartient à l'implémenteur de l'évaluateur d'expression \(EE\).  
  
## Prise en charge des visualiseurs de type dans un évaluateur d'expression  
 L'évaluateur d'expression peut prendre en charge les visualiseurs de type en prenant en charge un jeu d'interfaces accessibles aux visualiseurs : interfaces telles que [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md) et [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md).  Notez, cependant, que l'évaluateur d'expression n'est pas chargée d'implémenter le visualiseur de type lui\-même : l'évaluateur d'expression permet simplement l'accès externe de visualiseurs à ses informations de type.  De tels visualiseurs peuvent être fournis avec l'évaluateur d'expression et être installés à l'emplacement approprié dans Visual Studio, fournies par un autre fournisseur tiers ou même par l'utilisateur final.  
  
## Prise en charge des visionneuses personnalisées d'un évaluateur d'expression  
 L'évaluateur d'expression peut également prendre en charge les visionneuses personnalisées dans lesquelles l'évaluateur d'expression elle\-même fournit le code pour afficher le type de données.  Une visionneuse personnalisée implémente l'interface d' [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md) , dans lequel gère toutes les fonctions d'afficher les données format auquel est souhaité ; la visionneuse dispose d'un contrôle total sur l'affichage et peut même prendre en charge la modification des données.  Toutes les visionneuses personnalisées fournies par l'évaluateur d'expression s'accompagnent l'évaluateur d'expression lorsque le produit est fourni.  
  
## Voir aussi  
 [Composants du débogueur](../../extensibility/debugger/debugger-components.md)   
 [Évaluateur d'expression](../../extensibility/debugger/expression-evaluator.md)   
 [Moteur de débogage](../../extensibility/debugger/debug-engine.md)   
 [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)   
 [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)   
 [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)