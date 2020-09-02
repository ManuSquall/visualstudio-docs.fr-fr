---
title: Récupérer des éléments de modèle UML à partir de IDataObject | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML API, copy and paste
ms.assetid: e0b9cec8-3b93-4a24-8bd3-3e086501d387
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 66b4ffc312af89aa5852a1f4dad62fd328176df3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72666074"
---
# <a name="get-uml-model-elements-from-idataobject"></a>Obtenir des éléments de modèle UML à partir de l'interface IDataObject
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Quand l'utilisateur fait glisser des éléments à partir d'une source quelconque vers un diagramme, les éléments déplacés sont encodés dans un `System.Windows.Forms.IDataObject`. L'encodage dépend du type d'objet source. Le fragment suivant montre comment extraire les éléments quand la source est un diagramme UML.

> [!NOTE]
> La plupart des opérations que vous devez effectuer sur les modèles UML peuvent être effectuées à l’aide des types définis dans les assemblys **Microsoft. VisualStudio. Uml. interfaces** et **Microsoft. VisualStudio. ArchitectureTools. Extensibility**. Pour cela, vous devez utiliser des classes qui font partie de l'implémentation des outils de modélisation UML. Par exemple, `ShapeElement` dans ce fragment n'est pas identique à `IShape` en langage UML. Pour réduire le risque de mettre le modèle et les diagrammes UML dans un état incohérent, il est préférable d'éviter d'utiliser les méthodes sur ces classes d'implémentation, sauf s'il n'existe aucune alternative.

## <a name="code-sample"></a>Exemple de code
 Votre projet doit référencer les [!INCLUDE[TLA2#tla_net](../includes/tla2sharptla-net-md.md)] assemblys suivants :

 **Microsoft.VisualStudio.Modeling.Sdk.[version]**

 **Microsoft.VisualStudio.Modeling.Sdk.Diagrams.[version]**

 **System.Windows.Forms**

```
using Microsoft.VisualStudio.Modeling;
  // for ElementGroupPrototype
using Microsoft.VisualStudio.Modeling.Diagrams;
  // for ShapeElement, DiagramDragEventArgs, DiagramPointEventArgs
… 
  /// <summary>
  /// Retrieves UML IElements from drag arguments.
  /// Works for drags from UML diagrams.
  /// </summary>
  private IEnumerable<IElement> GetModelElementsFromDragEvent
                  (DiagramDragEventArgs dragEvent)
  {
     //ElementGroupPrototype is the container for
     //dragged and copied elements and toolbox items.
     ElementGroupPrototype prototype =
        dragEvent.Data.
        GetData(typeof(ElementGroupPrototype))
                     as ElementGroupPrototype;
     // Locate the originals in the implementation store.
     IElementDirectory implementationDirectory =
        dragEvent.DiagramClientView.Diagram.Store.ElementDirectory;

     return  prototype.ProtoElements.Select(
       prototypeElement =>
       {
          ModelElement element = implementationDirectory
                .FindElement(prototypeElement.ElementId);
          ShapeElement shapeElement = element as ShapeElement;
          if (shapeElement != null)
          {
            // Dragged from a diagram.
            return shapeElement.ModelElement as IElement;
          }
          else
          {
            // Dragged from UML Model Explorer.
            return element as IElement;
          }
        });
    }
```

 Pour plus d’informations sur `ElementGroupPrototype` et le `Store` dans lequel les outils de modélisation UML sont implémentés, consultez [Modeling SDK for Visual Studio-specific Language-Specific Languages (en anglais)](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md).

## <a name="see-also"></a>Voir aussi
 [Programmation à l’aide de l’API UML](../modeling/programming-with-the-uml-api.md) [définition d’une commande de menu sur un diagramme de modélisation](../modeling/define-a-menu-command-on-a-modeling-diagram.md)
