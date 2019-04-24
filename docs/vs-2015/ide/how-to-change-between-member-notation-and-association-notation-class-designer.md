---
title: 'Procédure : Changer entre Notation membre et Association (Concepteur de classes) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- notation, member
- association notation
- member notation
- notation, association
ms.assetid: 65881c5a-d251-4a36-ad0d-73d088436092
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 864edc3666164ac05d8155fd001d83c5bf515a6d
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60093291"
---
# <a name="how-to-change-between-member-notation-and-association-notation-class-designer"></a>Procédure : Changer la notation entre les membres et les associations (Concepteur de classes)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dans le Concepteur de classes, vous pouvez modifier la façon dont le diagramme de classes représente une relation d’association entre deux types, en passant de la notation membre à la notation association et vice versa. Les membres affichés sous forme de lignes d’association fournissent souvent une visualisation utile pour comprendre la relation entre les types.  
  
> [!NOTE]
>  Les relations d’association peuvent être représentées en tant que champ ou propriété de membre. Pour que vous puissiez passer de la notation membre à la notation association, un type doit avoir un membre d’un autre type. Pour que vous puissiez passer de la notation association à la notation membre, les deux types doivent être connectés par une ligne d’association. Pour plus d'informations, voir [Procédure : Créer des Associations entre Types (Concepteur de classes)](../ide/how-to-create-associations-between-types-class-designer.md). Si votre projet contient plusieurs diagrammes de classes, les modifications que vous apportez à la façon dont un diagramme affiche les relations d’association n’affectent que ce diagramme. Pour modifier la façon dont un autre diagramme affiche les relations d’association, ouvrez ou affichez le diagramme et effectuez les étapes suivantes.  
  
### <a name="to-change-member-notation-to-association-notation"></a>Pour passer de la notation membre à la notation association  
  
1. Depuis le nœud de projet affiché dans l’Explorateur de solutions, ouvrez le fichier du diagramme de classes (.cd).  
  
2. Dans la forme de type sur le diagramme de classes, cliquez avec le bouton droit sur le champ ou propriété de membre représentant l’association, puis choisissez **Afficher en tant qu’association**.  
  
    > [!TIP]
    >  Si aucun champ ou propriété n’est visible dans la forme de type, les compartiments de la forme peuvent être réduits. Pour développer la forme de type, double-cliquez sur le nom du compartiment ou cliquez avec le bouton droit sur la forme de type et choisissez **Développer**.  
  
     Le membre disparaît du compartiment dans la forme de type et une ligne d’association s’affiche pour connecter les deux types. La ligne d’association est étiquetée avec le nom de la propriété ou du champ.  
  
### <a name="to-change-association-notation-to-member-notation"></a>Pour passer de la notation association à la notation membre  
  
- Sur le diagramme de classes, cliquez avec le bouton droit sur la ligne d’association, puis choisissez **Afficher en tant que propriété** ou **Afficher en tant que champ** selon le cas.  
  
     La ligne d’association disparaît, et la propriété s’affiche dans le compartiment approprié au sein de sa forme de type sur le diagramme.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour Créer un héritage entre les Types (Concepteur de classes)](../ide/how-to-create-inheritance-between-types-class-designer.md)   
 [Guide pratique pour Afficher l’héritage entre les Types (Concepteur de classes)](../ide/how-to-view-inheritance-between-types-class-designer.md)   
 [Affichage des types et relations (Concepteur de classes)](../ide/viewing-types-and-relationships-class-designer.md)   
 [Guide pratique pour visualiser une association de collections (Concepteur de classes)](../ide/how-to-visualize-a-collection-association-class-designer.md)
