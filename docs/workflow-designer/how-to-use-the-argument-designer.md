---
title: 'Le Concepteur de flux de travail - Comment : utiliser le Concepteur d’arguments'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Presentation.View.ArgumentDesigner.UI
- System.Activities.Presentation.View.DesignTimeArgument.UI
ms.assetid: 64813fd5-1ea1-499a-98b4-ab2a44b7ee5e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b94656c7242c4bc6bc1dd1430230dac62a5322f1
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31971870"
---
# <a name="how-to-use-the-argument-designer"></a>Procédure : utiliser le concepteur d’arguments

Par rapport aux versions précédentes du .NET Framework, le Concepteur d’arguments permet facilement aux données de circuler dans et hors d’une activité. Le concepteur est accessible en cliquant sur le **Arguments** situé dans l’angle inférieur gauche de la zone de conception. Le concepteur contient une liste d’arguments qui s’affichent sous forme tabulaire et peuvent être triées en fonction de chacun des en-têtes de colonnes, à l’exception de la **valeur par défaut** colonne. Chaque argument contient une direction Entrée, Sortie, Entrée-Sortie ou Propriété, un type et une valeur d’expression par défaut (le cas échéant). Le nom et la valeur d’expression par défaut sont des champs de texte modifiables ; le type et la direction sont des zones de liste déroulante. Pour plus d’informations, consultez [Variables et arguments (.NET)](/dotnet/framework/windows-workflow-foundation/variables-and-arguments).

## <a name="to-create-a-new-argument"></a>Pour créer un argument

1.  Ouvrez une solution de workflow ou d’activité dans Visual Studio 2010.

2.  Ouvrez le Concepteur d’arguments en cliquant sur le **Arguments** situé dans l’angle inférieur gauche de la zone de conception. Le concepteur d’arguments s’affiche.

3.  Cliquez sur la ligne vide libellée **créer un Argument**. Cela ajoutera une nouvelle ligne avec un nouvel argument utilisant les valeurs par défaut suivantes : argumentx pour le **nom** où x est un entier avec une valeur initiale 1 qui est incrémenté automatiquement pour créer des noms d’argument unique **dans**  pour le **Direction**, et **chaîne** pour le **type d’Argument**. Aucune valeur n’est ajoutée pour **valeur par défaut**. Vous pouvez modifier ces valeurs à tout moment pendant le processus de conception du workflow.

    > [!NOTE]
    > Pour supprimer un argument, sélectionnez-le en cliquant dessus, puis appuyez sur la **supprimer** clé.

## <a name="see-also"></a>Voir aussi

- [Utilisation du Concepteur de flux de travail](../workflow-designer/using-the-workflow-designer.md)
- [Variables et arguments](/dotnet/framework/windows-workflow-foundation/variables-and-arguments)