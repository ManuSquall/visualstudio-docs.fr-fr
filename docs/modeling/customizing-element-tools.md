---
title: Personnalisation des outils d'élément
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: bb5a43224ff94e0e5115265383bff578031793bc
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54936305"
---
# <a name="customizing-element-tools"></a>Personnalisation des outils d'élément
Dans certaines définitions DSL, vous représenter un concept unique en tant que groupe d’éléments. Par exemple, si vous créez un modèle dans lequel un composant possède un ensemble fixe de ports, vous souhaitez toujours les ports doit être créé en même temps que son composant parent. Par conséquent, vous devez personnaliser l’outil de création d’élément pour qu’il crée un groupe d’éléments au lieu d’un. Pour ce faire, vous pouvez personnaliser la façon dont l’outil de création de l’élément est initialisé.

 Vous pouvez également remplacer ce qui se passe lorsque vous faites glisser l’outil sur le diagramme ou un élément.

## <a name="customizing-the-content-of-an-element-tool"></a>Personnaliser le contenu d’un outil d’élément
 Chaque outil d’élément stocke une instance d’un <xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype> (EGP), qui contient une version sérialisée d’un ou plusieurs éléments de modèle et des liens. Par défaut, l’EGP d’un outil d’élément contient une instance de la classe que vous spécifiez pour l’outil. Vous pouvez le modifier en remplaçant *Votre_langage*`ToolboxHelper.CreateElementToolPrototype`. Cette méthode est appelée lors du chargement du package DSL.

 Un paramètre de la méthode est l’ID de la classe que vous avez spécifié dans la définition DSL. Lorsque la méthode est appelée avec la classe qui vous intéresse, vous pouvez ajouter des éléments supplémentaires dans l’EGP.

 L’EGP doit inclure l’incorporation d’un élément principal des liens vers des éléments auxiliaires. Il peut également inclure des liens de référence.

 L’exemple suivant crée un élément principal et deux éléments incorporés. La classe principale est appelée résistance, et il a deux relations d’incorporation pour les éléments nommés Terminal Server. Les propriétés du rôle incorporation sont nommées Terminal1 et Terminal2, et les deux ont une multiplicité de 1..1.

```csharp
using Microsoft.VisualStudio.Modeling; ...
public partial class CircuitDiagramToolboxHelper
{
  protected override ElementGroupPrototype    CreateElementToolPrototype(Store store, Guid domainClassId)
  {
    // A case for each tool to customize:
    if (domainClassId == Resistor.DomainClassId)
    {
      // Set up the prototype elements and links:
      Resistor resistor = new Resistor(store);
      resistor.Terminal1 = new Terminal(store);
      resistor.Terminal2 = new Terminal(store);
      resistor.Terminal1.Name = "T1"; // embedding
      resistor.Terminal2.Name = "T2"; // embedding
      // We could also set up reference links.

      // Create an element group prototype for the toolbox:
      ElementGroup egp = new ElementGroup(store.DefaultPartition);
      egp.AddGraph(resistor, true);
      // We do not have to explicitly include embedded children.
      return egp.CreatePrototype();
    }
    // Element tools for other classes:
    else
      return base.CreateElementToolPrototype(store, domainClassId);
  }
}
```

## <a name="see-also"></a>Voir aussi

- [Personnalisation de la création et du mouvement des éléments](../modeling/customizing-element-creation-and-movement.md)