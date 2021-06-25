---
title: Visualiseur de type et visionneuse personnalisée | Microsoft Docs
description: En savoir plus sur les composants de visualiseur de type et les visionneuses personnalisées, qui affichent les données dans un format spécifique, et les différences entre eux.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], custom viewer
- debugging [Debugging SDK], type visualizer
ms.assetid: fd3691e6-9c78-4767-846f-43f85ada4375
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c18bb49c740362d42a4a54bf52f6998629acb0c0
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904420"
---
# <a name="type-visualizer-and-custom-viewer"></a>Visualiseur de type et visionneuse personnalisée
Un visualiseur de type est un composant qui affiche un élément de données dans un format spécifique. Le format est entièrement destiné aux personnes qui implémentent le visualiseur, qu’il s’agit de l’utilisateur final ou d’un fournisseur tiers de visualiseurs.

 Une visionneuse personnalisée est la partie d’un évaluateur d’expression personnalisé qui affiche un élément de données dans un format spécifique. Ce format est entièrement destiné à l’implémenteur de la visionneuse personnalisée, ce qui signifie que le format est destiné à l’implémenteur de l’évaluateur d’expression (EE).

## <a name="support-for-type-visualizers-in-an-expression-evaluator"></a>Prise en charge des visualiseurs de type dans un évaluateur d’expression
 Un EE prend en charge les visualiseurs de type en prenant en charge un ensemble d’interfaces accessibles aux visualiseurs : des interfaces telles que [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md) et [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md). Toutefois, EE n’est pas responsable de l’implémentation du visualiseur de type lui-même : l’EE permet simplement aux visualiseurs externes d’accéder à ses informations de type. Ces visualiseurs peuvent être livrés avec le EE et installés à l’emplacement approprié dans Visual Studio, fournis par un autre fournisseur tiers ou même par l’utilisateur final.

## <a name="support-for-custom-viewers-in-an-expression-evaluator"></a>Prise en charge des visionneuses personnalisées dans un évaluateur d’expression
 Un EE peut également prendre en charge des visionneuses personnalisées dans lesquelles EE lui-même fournit le code pour afficher le type de données. Une visionneuse personnalisée implémente l’interface [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md) , qui gère toutes les tâches liées à l’affichage des données dans le format souhaité. la visionneuse dispose d’un contrôle total sur l’affichage et peut même permettre la modification des données. Les visionneuses personnalisées fournies par EE sont fournies avec le EE lorsque le produit est expédié.

## <a name="see-also"></a>Voir aussi
- [Composants du débogueur](../../extensibility/debugger/debugger-components.md)
- [Évaluateur d’expression](../../extensibility/debugger/expression-evaluator.md)
- [Moteur de débogage](../../extensibility/debugger/debug-engine.md)
- [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)
- [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)
- [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)
