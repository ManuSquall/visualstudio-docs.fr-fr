---
title: 'Procédure : Utiliser le Concepteur d’arguments | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Presentation.View.ArgumentDesigner.UI
- System.Activities.Presentation.View.DesignTimeArgument.UI
ms.assetid: 64813fd5-1ea1-499a-98b4-ab2a44b7ee5e
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: a244379bfebcf58d76ba726d4f6a84bcdfa7d1df
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65696273"
---
# <a name="how-to-use-the-argument-designer"></a>Procédure : Utiliser le concepteur d’arguments
Par rapport aux versions précédentes du [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], le concepteur d'arguments permet aux données de circuler plus facilement à l'intérieur et à l'extérieur d'une activité. Le concepteur est accessible en cliquant sur le **Arguments** situé dans l’angle inférieur gauche de la zone de conception. Le concepteur contient une liste d’arguments qui s’affichent sous forme tabulaire et peuvent être triées en fonction de chacun des en-têtes de colonnes, à l’exception de la **valeur par défaut** colonne. Chaque argument contient une direction Entrée, Sortie, Entrée-Sortie ou Propriété, un type et une valeur d’expression par défaut (le cas échéant). Le nom et la valeur d'expression par défaut sont des champs de texte modifiables ; le type et la direction sont des zones de liste déroulante. [!INCLUDE[crabout](../includes/crabout-md.md)] arguments, consultez [Variables et Arguments](https://msdn.microsoft.com/library/d03dbe34-5b2e-4f21-8b57-693ee49611b8).  
  
### <a name="to-create-a-new-argument"></a>Pour créer un argument  
  
1. Ouvrez un workflow ou une solution d'activité dans [!INCLUDE[vs2010](../includes/vs2010-md.md)].  
  
2. Ouvrez le Concepteur d’arguments en cliquant sur le **Arguments** situé dans l’angle inférieur gauche de la zone de conception. Le concepteur d’arguments s’affiche.  
  
3. Cliquez sur la ligne vide libellée **créer un Argument**. Cette opération ajoute une nouvelle ligne avec un nouvel argument utilisant les valeurs par défaut suivantes : argumentx pour le **nom** où x est un entier avec une valeur initiale 1 qui est automatiquement incrémenté pour créer des noms d’argument unique, **dans**  pour le **Direction**, et **chaîne** pour le **type d’Argument**. Aucune valeur n’est ajoutée pour **valeur par défaut**. Vous pouvez modifier ces valeurs à tout moment pendant le processus de conception du workflow.  
  
    > [!NOTE]
    > Pour supprimer un argument, sélectionnez l’argument en cliquant dessus, puis appuyez sur la **supprimer** clé.  
  
## <a name="see-also"></a>Voir aussi  
 [L’aide du Concepteur de flux de travail](../workflow-designer/using-the-workflow-designer.md)   
 [Variables et arguments](https://msdn.microsoft.com/library/d03dbe34-5b2e-4f21-8b57-693ee49611b8)