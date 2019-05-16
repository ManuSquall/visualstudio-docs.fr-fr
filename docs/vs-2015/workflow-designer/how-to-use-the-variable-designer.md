---
title: 'Procédure : Utiliser le Concepteur de variables | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Presentation.View.DesignTimeVariable.UI
ms.assetid: 0318dfb0-bf8f-4f92-9b86-ae4c1b2161ad
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 9ebfcf53ce4d03f676930bd905baa0723c17e481
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65697091"
---
# <a name="how-to-use-the-variable-designer"></a>Procédure : Utiliser le concepteur de variables
Le concepteur de variables permet de créer des variables en vue d’une utilisation dans des scénarios de liaison de données et des instructions conditionnelles. Le concepteur est accessible en cliquant sur le **Variables** situé dans l’angle inférieur gauche de la zone de conception. Le concepteur contient une liste de variables qui s’affichent sous forme tabulaire et peuvent être triées en fonction de chacun des en-têtes de colonnes, à l’exception de la **par défaut** colonne. Chaque variable contient un nom, un type de variable, une étendue et une valeur par défaut (le cas échéant). Le nom et la valeur par défaut sont des champs de texte modifiables, et le type et l'étendue sont des zones de liste déroulante. L'étendue est l'activité qui a été sélectionnée lors de l'appel du concepteur de variables. Si une variable ne peut pas être créée dans l'étendue de la sélection, l'étendue aura comme valeur par défaut l'activité ancêtre la plus proche de la sélection qui autorise la création de variables dans son étendue. [!INCLUDE[crabout](../includes/crabout-md.md)] variables, consultez [Variables et Arguments](https://msdn.microsoft.com/library/d03dbe34-5b2e-4f21-8b57-693ee49611b8).  
  
 L'ordre de tri n'est appliqué que lorsque l'utilisateur utilise explicitement l'un des contrôles de tri, ferme et rouvre le concepteur de variables ou crée une autre variable.  
  
### <a name="to-create-a-new-variable"></a>Pour créer une variable  
  
1. Ouvrez un workflow ou une solution d'activité dans [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)].  
  
2. Sur la zone de conception, sélectionnez une activité dans votre workflow.  
  
3. Ouvrez le Concepteur de variables en cliquant sur le **Variables** situé dans l’angle inférieur gauche de la zone de conception. Le concepteur de variables s'affiche.  
  
4. Cliquez sur la ligne vide libellée **créer une Variable**. Cette opération ajoute une nouvelle ligne avec une nouvelle variable utilisant les valeurs par défaut suivantes : variablex pour le **nom** où x est un entier avec une valeur initiale 1 qui est automatiquement incrémenté pour créer des noms de variable uniques,  **Chaîne** pour le **type de Variable**, et **séquence** pour le **étendue**. Aucune valeur n’est ajoutée pour **par défaut**. Vous pouvez modifier ces valeurs à tout moment pendant le processus de conception du workflow.  
  
    > [!NOTE]
    > Pour supprimer une variable, sélectionnez la variable en cliquant dessus, puis appuyez sur la **supprimer** clé.  
  
## <a name="see-also"></a>Voir aussi  
 [L’aide du Concepteur de flux de travail](../workflow-designer/using-the-workflow-designer.md)   
 [Variables et Arguments](https://msdn.microsoft.com/library/d03dbe34-5b2e-4f21-8b57-693ee49611b8)   
 [Guide pratique pour utiliser le concepteur d’arguments](../workflow-designer/how-to-use-the-argument-designer.md)