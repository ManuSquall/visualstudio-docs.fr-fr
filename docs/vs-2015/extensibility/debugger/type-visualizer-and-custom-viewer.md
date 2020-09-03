---
title: Visualiseur de type et visionneuse personnalisée | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], custom viewer
- debugging [Debugging SDK], type visualizer
ms.assetid: fd3691e6-9c78-4767-846f-43f85ada4375
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a85be2978abe35e91096b55fba5ec5281be25fbe
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68185315"
---
# <a name="type-visualizer-and-custom-viewer"></a>Visualiseur de type et visionneuse personnalisée
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Un visualiseur de type est un composant qui affiche un élément de données dans un format très spécifique. Ce format est entièrement destiné à l’implémenteur du visualiseur, que ce soit l’utilisateur final ou un fournisseur tiers de visualiseurs.  
  
 Une visionneuse personnalisée est la partie d’un évaluateur d’expression personnalisé qui affiche un élément de données dans un format très spécifique. Ce format est entièrement destiné à l’implémenteur de la visionneuse personnalisée, ce qui signifie que le format est destiné à l’implémenteur de l’évaluateur d’expression (EE).  
  
## <a name="support-for-type-visualizers-in-an-expression-evaluator"></a>Prise en charge des visualiseurs de type dans un évaluateur d’expression  
 Un EE peut prendre en charge des visualiseurs de type en prenant en charge un ensemble d’interfaces accessibles aux visualiseurs : des interfaces telles que [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md) et [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md). Notez, toutefois, que l’EE n’est pas responsable de l’implémentation du visualiseur de type lui-même : l’EE permet simplement aux visualiseurs externes d’accéder à ses informations de type. Ces visualiseurs peuvent être livrés avec le EE et installés à l’emplacement approprié dans Visual Studio, fournis par un autre fournisseur tiers ou même par l’utilisateur final.  
  
## <a name="support-for-custom-viewers-in-an-expression-evaluator"></a>Prise en charge des visionneuses personnalisées dans un évaluateur d’expression  
 Un EE peut également prendre en charge des visionneuses personnalisées dans lesquelles EE lui-même fournit le code pour afficher le type de données. Une visionneuse personnalisée implémente l’interface [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md) , qui gère toutes les tâches liées à l’affichage des données dans le format souhaité. la visionneuse dispose d’un contrôle total sur l’affichage et peut même permettre la modification des données. Les visionneuses personnalisées fournies par EE sont fournies avec le EE lorsque le produit est expédié.  
  
## <a name="see-also"></a>Voir aussi  
 [Composants du débogueur](../../extensibility/debugger/debugger-components.md)   
 [Évaluateur d’expression](../../extensibility/debugger/expression-evaluator.md)   
 [Moteur de débogage](../../extensibility/debugger/debug-engine.md)   
 [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)   
 [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)   
 [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)
