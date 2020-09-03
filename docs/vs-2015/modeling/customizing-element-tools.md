---
title: Personnalisation des outils d’élément | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 6dac48b6-db68-4bcd-8aa2-422c2ad5d28b
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b6b35bbb0592f7ec9f8defcd9d78dbba5a6a47a5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72655020"
---
# <a name="customizing-element-tools"></a>Personnalisation des outils d'élément
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dans certaines définitions DSL, vous représentez un concept unique sous la forme d’un groupe d’éléments. Par exemple, si vous créez un modèle dans lequel un composant a un ensemble fixe de ports, vous souhaitez toujours que les ports soient créés en même temps que leur composant parent. Par conséquent, vous devez personnaliser l’outil de création d’élément afin qu’il crée un groupe d’éléments au lieu d’un seul. Pour ce faire, vous pouvez personnaliser la façon dont l’outil de création d’élément est initialisé.

 Vous pouvez également remplacer ce qui se passe lorsque l’outil est glissé sur le diagramme ou sur un élément.

## <a name="customizing-the-content-of-an-element-tool"></a>Personnalisation du contenu d’un outil d’élément
 Chaque outil d’élément stocke une instance d’un <xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype> (EGP), qui contient une version sérialisée d’un ou plusieurs éléments de modèle et liens. Par défaut, le EGP d’un outil d’élément contient une instance de la classe que vous spécifiez pour l’outil. Vous pouvez modifier cela en remplaçant *YourLanguage* `ToolboxHelper.CreateElementToolPrototype` . Cette méthode est appelée lorsque le package DSL est chargé.

 Un paramètre de la méthode est l’ID de la classe que vous avez spécifié dans la définition DSL. Lorsque la méthode est appelée avec la classe qui vous intéresse, vous pouvez ajouter des éléments supplémentaires dans le EGP.

 Le EGP doit inclure des liens d’incorporation d’un élément principal aux éléments de la filiale. Il peut également inclure des liens de référence.

 L’exemple suivant crée un élément principal et deux éléments incorporés. La classe principale est appelée résistance et a deux relations d’incorporation aux éléments nommés terminal. Les propriétés du rôle d’incorporation sont nommées Terminal1 et Terminal2, et les deux ont une multiplicité de 1.. 1.

```
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
 [Personnalisation de la création et du mouvement des éléments](../modeling/customizing-element-creation-and-movement.md)
