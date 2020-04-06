---
title: Type Visualisateur et Visualiseur personnalisé (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], custom viewer
- debugging [Debugging SDK], type visualizer
ms.assetid: fd3691e6-9c78-4767-846f-43f85ada4375
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7b8def9d28279f601ff488fca457982806629c0b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712467"
---
# <a name="type-visualizer-and-custom-viewer"></a>Type visualisateur et visualiseur personnalisé
Un visualisateur de type est un composant qui affiche un élément de données dans un format spécifique. Le format est entièrement à qui implémente le visualiseur, que ce soit l’utilisateur final ou un fournisseur tiers de visualisateurs.

 Un visualiseur personnalisé fait partie d’un évaluateur d’expression personnalisé qui affiche un élément de données dans un format spécifique. Ce format est entièrement à la hauteur de l’implémentateur du visualiseur personnalisé, ce qui signifie que le format est à la hauteur de l’implémentateur de l’évaluateur d’expression (EE).

## <a name="support-for-type-visualizers-in-an-expression-evaluator"></a>Prise en charge des visualisateurs de type dans un évaluateur d’expression
 Un EE prend en charge les visualisateurs de type en soutenant un ensemble d’interfaces accessibles aux visualisateurs : interfaces telles que [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md) et [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md). Cependant, l’EE n’est pas responsable de la mise en œuvre du visualiseur de type lui-même : l’EE permet simplement aux visualisateurs externes d’accéder à ses informations de type. Ces visualisateurs peuvent être expédiés avec l’EE et installés à l’endroit approprié dans Visual Studio, fourni par un autre fournisseur tiers ou même par l’utilisateur final.

## <a name="support-for-custom-viewers-in-an-expression-evaluator"></a>Prise en charge des téléspectateurs personnalisés dans un évaluateur d’expression
 Une EE peut également prendre en charge les téléspectateurs personnalisés dans lesquels l’EE lui-même fournit le code pour l’affichage du type de données. Un visualiseur personnalisé implémente l’interface [IDebugCustomViewer,](../../extensibility/debugger/reference/idebugcustomviewer.md) qui gère toutes les tâches de diffusion des données dans n’importe quel format souhaité; le spectateur a le plein contrôle sur l’écran et peut même laisser les données être modifiées. Tous les téléspectateurs personnalisés fournis par l’EE sont livrés avec l’EE lorsque le produit est expédié.

## <a name="see-also"></a>Voir aussi
- [Composants Debugger](../../extensibility/debugger/debugger-components.md)
- [Évaluateur d’expression](../../extensibility/debugger/expression-evaluator.md)
- [Moteur Debug](../../extensibility/debugger/debug-engine.md)
- [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)
- [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)
- [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)
