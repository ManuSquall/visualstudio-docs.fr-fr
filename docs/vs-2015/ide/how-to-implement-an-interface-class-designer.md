---
title: 'Procédure : Implémenter une Interface (Concepteur de classes) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- interfaces [Visual Studio], implementing
- interfaces [Visual Studio]
ms.assetid: 81d2cf46-7f60-448c-83e3-1d16bb88ca36
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: ee9289ebaeb12318ef83694f5dfb74b2930b8df1
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63416748"
---
# <a name="how-to-implement-an-interface-class-designer"></a>Procédure : implémenter une interface (Concepteur de classes)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dans le Concepteur de classes, vous pouvez implémenter une interface pour le diagramme de classes en la connectant à une classe qui fournit du code pour les méthodes d’interface. Le Concepteur de classes génère une implémentation d’interface et affiche la relation entre l’interface et la classe sous la forme d’une relation d’héritage. Vous pouvez implémenter une interface en dessinant une ligne d’héritage entre l’interface et la classe ou en faisant glisser l’interface à partir de l’Affichage de classes.  
  
> [!TIP]
> Vous pouvez créer des interfaces de la même façon que vous créez d’autres types. Si l’interface existe mais n’apparaît pas dans le diagramme de classes, affichez-la d’abord. Pour plus d'informations, voir [Procédure : Créer des Types à l’aide du Concepteur de classes](../ide/how-to-create-types-by-using-class-designer.md) et [Comment : Afficher des Types existants (Concepteur de classes)](../ide/how-to-view-existing-types-class-designer.md).  
  
### <a name="to-implement-an-interface-by-drawing-an-inheritance-line"></a>Pour implémenter une interface en dessinant une ligne d’héritage  
  
1. Sur le diagramme de classes, affichez l’interface et la classe qui implémente cette interface.  
  
2. Dessinez une ligne d’héritage entre la classe et l’interface.  
  
    Un symbole d’interface (lollipop) attaché à la classe s’affiche, et une étiquette avec le nom de l’interface identifie la relation d’héritage. Visual Studio génère des stubs pour tous les membres de l’interface.  
  
   Pour plus d'informations, voir [Procédure : Créer un héritage entre les Types (Concepteur de classes)](../ide/how-to-create-inheritance-between-types-class-designer.md).  
  
### <a name="to-implement-an-interface-from-the-class-view-window"></a>Pour implémenter une interface à partir de la fenêtre Affichage de classes  
  
1. Sur le diagramme de classes, affichez la classe choisie pour implémenter cette interface.  
  
2. Ouvrez l’Affichage de classes et recherchez l’interface.  
  
    > [!TIP]
    > Si l’Affichage de classes n’est pas ouvert, ouvrez-le depuis le menu **Affichage**. Pour plus d’informations sur l’affichage des classes, consultez [Affichage des classes et de leurs membres](http://msdn.microsoft.com/71e9e8f3-261a-4e0c-87bf-5ec48b8bf333).  
  
3. Faites glisser le nœud de l’interface vers la forme de classe sur le diagramme.  
  
     Un symbole d’interface (lollipop) attaché à la classe s’affiche, et une étiquette avec le nom de l’interface identifie la relation d’héritage. Visual Studio génère des stubs pour tous les membres de l’interface. L’interface est maintenant implémentée.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour Créer des Types à l’aide du Concepteur de classes](../ide/how-to-create-types-by-using-class-designer.md)   
 [Guide pratique pour Afficher des Types existants (Concepteur de classes)](../ide/how-to-view-existing-types-class-designer.md)   
 [Guide pratique pour Créer un héritage entre les Types (Concepteur de classes)](../ide/how-to-create-inheritance-between-types-class-designer.md)   
 [Refactorisation des classes et des types (Concepteur de classes)](../ide/refactoring-classes-and-types-class-designer.md)
