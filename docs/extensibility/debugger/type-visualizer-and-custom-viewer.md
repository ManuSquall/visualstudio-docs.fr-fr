---
title: Type du visualiseur et la visionneuse personnalisée | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], custom viewer
- debugging [Debugging SDK], type visualizer
ms.assetid: fd3691e6-9c78-4767-846f-43f85ada4375
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 219632bce50b6942d46e4061a3c7eaf8f70adfd5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62864240"
---
# <a name="type-visualizer-and-custom-viewer"></a>Visualiseur de type et visionneuse personnalisée
Un visualiseur de type est un composant qui affiche un élément de données dans un format spécifique. Le format est entièrement jusqu'à qui implémente le visualiseur, soit l’utilisateur final ou un fournisseur tiers de visualiseurs.

 Une visionneuse personnalisée est la partie d’un évaluateur d’expression personnalisée qui affiche un élément de données dans un format spécifique. Ce format est entièrement à l’implémenteur de la visionneuse personnalisée, ce qui signifie que le format est à l’implémenteur de l’évaluateur d’expression (EE).

## <a name="support-for-type-visualizers-in-an-expression-evaluator"></a>Prise en charge des visualiseurs de type dans un évaluateur d’expression
 Un EE prend en charge les visualiseurs de type en prenant en charge un ensemble d’interfaces accessibles aux visualiseurs : interfaces telles que [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md) et [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md). Toutefois, le EE n’est pas chargé d’implémenter le visualiseur de type lui-même : le EE permet simplement visualiseurs externes d’accéder à ses informations de type. Ces visualiseurs peuvent être expédiés, ainsi que le EE et installés dans l’emplacement approprié dans Visual Studio, fourni par un autre fournisseur tiers ou même par l’utilisateur final.

## <a name="support-for-custom-viewers-in-an-expression-evaluator"></a>Prise en charge des visionneuses personnalisées dans un évaluateur d’expression
 Un EE peut également gérer les visionneuses personnalisées dans laquelle le EE lui-même fournit le code pour afficher le type de données. Une visionneuse personnalisée implémente la [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md) interface, qui gère tous les droits d’afficher les données dans le format est souhaitée ; la visionneuse a un contrôle total sur l’affichage et peut même laisser les données modifiables. Les visionneuses personnalisées fournies par le EE sont fournis avec le EE lorsque le produit est expédié.

## <a name="see-also"></a>Voir aussi
- [Composants du débogueur](../../extensibility/debugger/debugger-components.md)
- [Évaluateur d’expression](../../extensibility/debugger/expression-evaluator.md)
- [Moteur de débogage](../../extensibility/debugger/debug-engine.md)
- [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)
- [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)
- [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)