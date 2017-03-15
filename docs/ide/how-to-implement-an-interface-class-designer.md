---
title: "How to: Implement an Interface (Class Designer) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "interfaces [Visual Studio], implementing"
  - "interfaces [Visual Studio]"
ms.assetid: 81d2cf46-7f60-448c-83e3-1d16bb88ca36
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 16
---
# How to: Implement an Interface (Class Designer)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Dans le Concepteur de classes, vous pouvez implémenter une interface sur le diagramme de classes en le connectant à une classe qui fournit le code pour les méthodes d'interface.  Le Concepteur de classes génère une implémentation d'interface et affiche la relation entre l'interface et la classe comme relation d'héritage.  Vous pouvez implémenter une interface en dessinant une ligne d'héritage entre l'interface et la classe ou en faisant glisser l'interface depuis l'Affichage de classes.  
  
> [!TIP]
>  Vous pouvez créer des interfaces de la même façon que vous créez d'autres types.  Si l'interface existe mais n'apparaît pas sur le diagramme de classes, affichez\-la d'abord.  Pour plus d'informations, consultez [How to: Create Types by using Class Designer](../ide/how-to-create-types-by-using-class-designer.md) et [How to: View Existing Types \(Class Designer\)](../Topic/How%20to:%20View%20Existing%20Types%20\(Class%20Designer\).md).  
  
### Pour implémenter une interface en traçant une ligne d'héritage  
  
1.  Sur le diagramme de classes, affichez l'interface et la classe qui l'implémentera.  
  
2.  Tracez une ligne d'héritage entre la classe et l'interface.  
  
     Un symbole d'interface \(lollipop\) apparaît, attaché à la classe, et une étiquette avec le nom de l'interface identifie la relation d'héritage.  Visual Studio génère des stubs pour tous les membres d'interface.  
  
 Pour plus d'informations, consultez [How to: Create Inheritance Between Types \(Class Designer\)](../ide/how-to-create-inheritance-between-types-class-designer.md).  
  
### Pour implémenter une interface à partir de la fenêtre Affichage de classes  
  
1.  Sur le diagramme de classes, affichez la classe choisie pour implémenter l'interface.  
  
2.  Ouvrez l'Affichage de classes et recherchez l'interface.  
  
    > [!TIP]
    >  Si l'Affichage de classes n'est pas ouvert, ouvrez\-le depuis le menu **Affichage**.  Pour plus d'informations sur l'Affichage de classes, consultez [Viewing Classes and Their Members](http://msdn.microsoft.com/fr-fr/71e9e8f3-261a-4e0c-87bf-5ec48b8bf333).  
  
3.  Faites glisser le nœud d'interface vers la forme de classe sur le diagramme.  
  
     Un symbole d'interface \(lollipop\) apparaît, attaché à la classe, et une étiquette avec le nom de l'interface identifie la relation d'héritage.  Visual Studio génère des stubs pour tous les membres d'interface ; à ce stade, l'interface est implémentée.  
  
## Voir aussi  
 [How to: Create Types by using Class Designer](../ide/how-to-create-types-by-using-class-designer.md)   
 [How to: View Existing Types \(Class Designer\)](../Topic/How%20to:%20View%20Existing%20Types%20\(Class%20Designer\).md)   
 [How to: Create Inheritance Between Types \(Class Designer\)](../ide/how-to-create-inheritance-between-types-class-designer.md)   
 [Refactoring Classes and Types \(Class Designer\)](../ide/refactoring-classes-and-types-class-designer.md)