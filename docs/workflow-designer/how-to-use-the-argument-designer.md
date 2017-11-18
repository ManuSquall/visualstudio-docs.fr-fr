---
title: "Comment : utiliser le Concepteur d’arguments | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- System.Activities.Presentation.View.ArgumentDesigner.UI
- System.Activities.Presentation.View.DesignTimeArgument.UI
ms.assetid: 64813fd5-1ea1-499a-98b4-ab2a44b7ee5e
caps.latest.revision: "16"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5093e5561140a0ebff57da1f7c21a8954ee58bb3
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-use-the-argument-designer"></a>Procédure : utiliser le concepteur d’arguments
Par rapport aux versions précédentes du [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], le concepteur d'arguments permet aux données de circuler plus facilement à l'intérieur et à l'extérieur d'une activité. Le concepteur est accessible en cliquant sur le **Arguments** situé dans l’angle inférieur gauche de la zone de conception. Le concepteur contient une liste d’arguments qui s’affichent sous forme tabulaire et peuvent être triées en fonction de chacun des en-têtes de colonnes, à l’exception de la **valeur par défaut** colonne. Chaque argument contient une direction Entrée, Sortie, Entrée-Sortie ou Propriété, un type et une valeur d’expression par défaut (le cas échéant). Le nom et la valeur d’expression par défaut sont des champs de texte modifiables ; le type et la direction sont des zones de liste déroulante. [! INCLURE[crabout sur](/dotnet/framework/windows-workflow-foundation/variables-and-arguments).  
  
### <a name="to-create-a-new-argument"></a>Pour créer un argument  
  
1.  Ouvrez un workflow ou une solution d'activité dans [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)].  
  
2.  Ouvrez le Concepteur d’arguments en cliquant sur le **Arguments** situé dans l’angle inférieur gauche de la zone de conception. Le concepteur d’arguments s’affiche.  
  
3.  Cliquez sur la ligne vide libellée **créer un Argument**. Cela ajoutera une nouvelle ligne avec un nouvel argument utilisant les valeurs par défaut suivantes : argumentx pour le **nom** où x est un entier avec une valeur initiale 1 qui est incrémenté automatiquement pour créer des noms d’argument unique **dans**  pour le **Direction**, et **chaîne** pour le **type d’Argument**. Aucune valeur n’est ajoutée pour **valeur par défaut**. Vous pouvez modifier ces valeurs à tout moment pendant le processus de conception du workflow.  
  
    > [!NOTE]
    >  Pour supprimer un argument, sélectionnez-le en cliquant dessus, puis appuyez sur la **supprimer** clé.  
  
## <a name="see-also"></a>Voir aussi  
 [L’aide du Concepteur de flux de travail](../workflow-designer/using-the-workflow-designer.md)   
 [Variables et arguments](/dotnet/framework/windows-workflow-foundation/variables-and-arguments)