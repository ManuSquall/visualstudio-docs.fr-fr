---
title: 'Comment : utiliser le concepteur de variables | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Presentation.View.DesignTimeVariable.UI
ms.assetid: 0318dfb0-bf8f-4f92-9b86-ae4c1b2161ad
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4744864824da5efb238e9af1a5a12fcef79ea4ff
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72659076"
---
# <a name="how-to-use-the-variable-designer"></a>Procédure : utiliser le concepteur de variables
Le concepteur de variables permet de créer des variables en vue d’une utilisation dans des scénarios de liaison de données et des instructions conditionnelles. Pour accéder au concepteur, cliquez sur le bouton **variables** dans le coin inférieur gauche de la zone de conception. Le concepteur contient une liste de variables qui s’affichent sous forme de tableau et peuvent être triées par chacun des en-têtes de colonne, à l’exception de la colonne **par défaut** . Chaque variable contient un nom, un type de variable, une étendue et une valeur par défaut (le cas échéant). Le nom et la valeur par défaut sont des champs de texte modifiables, et le type et l'étendue sont des zones de liste déroulante. L'étendue est l'activité qui a été sélectionnée lors de l'appel du concepteur de variables. Si une variable ne peut pas être créée dans l'étendue de la sélection, l'étendue aura comme valeur par défaut l'activité ancêtre la plus proche de la sélection qui autorise la création de variables dans son étendue. [!INCLUDE[crabout](../includes/crabout-md.md)] les variables, consultez [variables et arguments](https://msdn.microsoft.com/library/d03dbe34-5b2e-4f21-8b57-693ee49611b8).

 L'ordre de tri n'est appliqué que lorsque l'utilisateur utilise explicitement l'un des contrôles de tri, ferme et rouvre le concepteur de variables ou crée une autre variable.

### <a name="to-create-a-new-variable"></a>Pour créer une variable

1. Ouvrez un workflow ou une solution d'activité dans [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)].

2. Sur la zone de conception, sélectionnez une activité dans votre workflow.

3. Ouvrez le concepteur de variables en cliquant sur le bouton **variables** dans le coin inférieur gauche de la zone de conception. Le concepteur de variables s'affiche.

4. Cliquez sur la ligne vide intitulée **créer une variable**. Cette opération ajoute une nouvelle ligne avec une nouvelle variable en utilisant les valeurs par défaut suivantes : VariableX pour le **nom** où x est un entier avec une valeur initiale de 1 qui est automatiquement incrémentée pour créer des noms de variables uniques, une **chaîne** pour le **type de variable**et une **séquence** pour l' **étendue**. Aucune valeur n’est ajoutée pour **default**. Vous pouvez modifier ces valeurs à tout moment pendant le processus de conception du workflow.

    > [!NOTE]
    > Pour supprimer une variable, sélectionnez la variable en cliquant dessus, puis appuyez sur la touche **Suppr** .

## <a name="see-also"></a>Voir aussi
 [Utilisation](../workflow-designer/using-the-workflow-designer.md) des [variables et des arguments](https://msdn.microsoft.com/library/d03dbe34-5b2e-4f21-8b57-693ee49611b8) concepteur de flux de travail [Comment : utiliser le concepteur d’arguments](../workflow-designer/how-to-use-the-argument-designer.md)