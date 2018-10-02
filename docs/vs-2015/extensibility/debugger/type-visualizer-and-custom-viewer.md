---
title: Type du visualiseur et la visionneuse personnalisée | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], custom viewer
- debugging [Debugging SDK], type visualizer
ms.assetid: fd3691e6-9c78-4767-846f-43f85ada4375
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d347e7b18722aa8f8901abac3966150b3dca97cf
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47495516"
---
# <a name="type-visualizer-and-custom-viewer"></a>Visualiseur de type et visionneuse personnalisée
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [visualiseur de Type et Visionneuse de personnalisé](https://docs.microsoft.com/visualstudio/extensibility/debugger/type-visualizer-and-custom-viewer).  
  
Un visualiseur de type est un composant qui affiche un élément de données dans un format très spécifique. Ce format est entièrement à l’implémenteur du visualiseur, qu’il s’agisse de l’utilisateur final ou un fournisseur tiers de visualiseurs.  
  
 Une visionneuse personnalisée est la partie d’un évaluateur d’expression personnalisée qui affiche un élément de données dans un format très spécifique. Ce format est entièrement à l’implémenteur de la visionneuse personnalisée, ce qui signifie que le format est à l’implémenteur de l’évaluateur d’expression (EE).  
  
## <a name="support-for-type-visualizers-in-an-expression-evaluator"></a>Prise en charge des visualiseurs de Type dans un évaluateur d’Expression  
 Un EE peut prendre en charge les visualiseurs de type en prenant en charge un ensemble d’interfaces accessibles aux visualiseurs : interfaces telles que [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md) et [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md). Notez, cependant, que le EE n’est pas chargé d’implémenter le visualiseur de type lui-même : le EE permet simplement visualiseurs externes d’accéder à ses informations de type. Ces visualiseurs peuvent être expédiés, ainsi que le EE et installés dans l’emplacement approprié dans Visual Studio, fourni par un autre fournisseur tiers ou même par l’utilisateur final.  
  
## <a name="support-for-custom-viewers-in-an-expression-evaluator"></a>Prise en charge des visionneuses personnalisées dans un évaluateur d’Expression  
 Un EE peut également gérer les visionneuses personnalisées dans laquelle le EE lui-même fournit le code pour afficher le type de données. Une visionneuse personnalisée implémente la [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md) interface, qui gère tous les droits d’afficher les données dans le format est souhaitée ; a un contrôle total sur l’affichage de la visionneuse et peut même permettre les modification des données. Les visionneuses personnalisées fournies par le EE sont fournis avec le EE lorsque le produit est expédié.  
  
## <a name="see-also"></a>Voir aussi  
 [Composants du débogueur](../../extensibility/debugger/debugger-components.md)   
 [Évaluateur d’expression](../../extensibility/debugger/expression-evaluator.md)   
 [Moteur de débogage](../../extensibility/debugger/debug-engine.md)   
 [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)   
 [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)   
 [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)

