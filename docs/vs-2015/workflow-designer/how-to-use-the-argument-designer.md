---
title: 'Comment : utiliser le concepteur d’arguments | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Presentation.View.ArgumentDesigner.UI
- System.Activities.Presentation.View.DesignTimeArgument.UI
ms.assetid: 64813fd5-1ea1-499a-98b4-ab2a44b7ee5e
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a436d33bbb7c791f3f192357fded779fa77d148d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72659111"
---
# <a name="how-to-use-the-argument-designer"></a>Procédure : utiliser le concepteur d’arguments
Par rapport aux versions précédentes du [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], le concepteur d'arguments permet aux données de circuler plus facilement à l'intérieur et à l'extérieur d'une activité. Pour accéder au concepteur, cliquez sur le bouton **arguments** situé dans l’angle inférieur gauche de la zone de conception. Le concepteur contient une liste d’arguments qui s’affichent sous forme de tableau et peuvent être triés par chacun des en-têtes de colonne, à l’exception de la colonne de **valeur par défaut** . Chaque argument contient une direction Entrée, Sortie, Entrée-Sortie ou Propriété, un type et une valeur d’expression par défaut (le cas échéant). Le nom et la valeur d'expression par défaut sont des champs de texte modifiables ; le type et la direction sont des zones de liste déroulante. [!INCLUDE[crabout](../includes/crabout-md.md)] les arguments, consultez [variables et arguments](https://msdn.microsoft.com/library/d03dbe34-5b2e-4f21-8b57-693ee49611b8).

### <a name="to-create-a-new-argument"></a>Pour créer un argument

1. Ouvrez un workflow ou une solution d'activité dans [!INCLUDE[vs2010](../includes/vs2010-md.md)].

2. Ouvrez le concepteur d’arguments en cliquant sur le bouton **arguments** dans le coin inférieur gauche de la zone de conception. Le concepteur d’arguments s’affiche.

3. Cliquez sur la ligne vide intitulée **créer un argument**. Cette opération ajoute une nouvelle ligne avec un nouvel argument en utilisant les valeurs par défaut suivantes : argumentx comme pour le **nom** où x est un entier avec une valeur initiale de 1 qui est automatiquement incrémentée pour créer des noms d’arguments uniques, **dans** pour la **direction**et **chaîne** pour le **type d’argument**. Aucune valeur n’est ajoutée pour la **valeur par défaut**. Vous pouvez modifier ces valeurs à tout moment pendant le processus de conception du workflow.

    > [!NOTE]
    > Pour supprimer un argument, sélectionnez l’argument en cliquant dessus, puis appuyez sur la touche **Suppr** .

## <a name="see-also"></a>Voir aussi
 [Utilisation des](../workflow-designer/using-the-workflow-designer.md) [variables et des arguments](https://msdn.microsoft.com/library/d03dbe34-5b2e-4f21-8b57-693ee49611b8) concepteur de flux de travail