---
title: "Personnalisation des outils de l’&#233;l&#233;ment | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6dac48b6-db68-4bcd-8aa2-422c2ad5d28b
caps.latest.revision: 6
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 6
---
# Personnalisation des outils de l’&#233;l&#233;ment
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Dans certaines définitions DSL, vous représentent un concept unique sous la forme d’un groupe d’éléments. Par exemple, si vous créez un modèle dans lequel un composant a un ensemble fixe de ports, vous souhaitez toujours les ports doit être créé en même temps que son composant parent. Par conséquent, vous devez personnaliser l’outil de création de l’élément pour qu’il crée un groupe d’éléments au lieu d’un. Pour ce faire, vous pouvez personnaliser la façon dont l’outil de création de l’élément est initialisé.  
  
 Vous pouvez également remplacer ce qui se passe lorsque l’outil est glissé sur le diagramme ou un élément.  
  
## Personnaliser le contenu d’un outil d’élément  
 Chaque outil d’élément stocke une instance d’un <xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype> \(EGP\), qui contient une version sérialisée d’un ou plusieurs éléments de modèle et des liens. Par défaut, le EGP d’un outil d’élément contient une instance de la classe que vous spécifiez pour l’outil. Vous pouvez le modifier en remplaçant *Votre\_langage*`ToolboxHelper.CreateElementToolPrototype`. Cette méthode est appelée lors du chargement du package DSL.  
  
 Un paramètre de la méthode est l’ID de la classe que vous avez spécifié dans la définition DSL. Lorsque la méthode est appelée par la classe qui vous intéresse, vous pouvez ajouter des éléments supplémentaires dans le EGP.  
  
 L’EGP doit inclure l’incorporation d’un élément principal des liens vers des éléments auxiliaires. Il peut également inclure des liens de référence.  
  
 L’exemple suivant crée un élément principal et deux éléments incorporés. La classe principale est appelée résistance et il a deux relations d’incorporation pour les éléments nommés Terminal Server. Les propriétés du rôle incorporation sont nommées Terminal1 et Terminal2, et les deux ont une multiplicité de 1.. 1.  
  
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
  
## Voir aussi  
 [Personnalisation de la création et du mouvement des éléments](../modeling/customizing-element-creation-and-movement.md)