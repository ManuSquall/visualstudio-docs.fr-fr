---
title: 'Concepteur de flux de travail - Comment : Utiliser le concepteur d’arguments'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- System.Activities.Presentation.View.ArgumentDesigner.UI
- System.Activities.Presentation.View.DesignTimeArgument.UI
ms.assetid: 64813fd5-1ea1-499a-98b4-ab2a44b7ee5e
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cb4cbcb6b1310e6552dfd757a4b6347212f99cfc
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55941177"
---
# <a name="how-to-use-the-argument-designer"></a>Procédure : Utiliser le concepteur d’arguments

Par rapport aux versions précédentes du .NET Framework, le Concepteur d’arguments facilite aux données de circuler vers et depuis une activité. Le concepteur est accessible en cliquant sur le **Arguments** situé dans l’angle inférieur gauche de la zone de conception. Le concepteur contient une liste d’arguments qui s’affichent sous forme tabulaire et peuvent être triées en fonction de chacun des en-têtes de colonnes, à l’exception de la **valeur par défaut** colonne. Chaque argument contient une direction Entrée, Sortie, Entrée-Sortie ou Propriété, un type et une valeur d’expression par défaut (le cas échéant). Le nom et la valeur d’expression par défaut sont des champs de texte modifiables ; le type et la direction sont des zones de liste déroulante. Pour plus d’informations, consultez [Variables et arguments (.NET)](/dotnet/framework/windows-workflow-foundation/variables-and-arguments).

## <a name="to-create-a-new-argument"></a>Pour créer un argument

1.  Dans Visual Studio, ouvrez une solution de flux de travail ou d’activité.

2.  Ouvrez le Concepteur d’arguments en cliquant sur le **Arguments** situé dans l’angle inférieur gauche de la zone de conception. Le concepteur d’arguments s’affiche.

3.  Cliquez sur la ligne vide libellée **créer un Argument**. Cette opération ajoute une nouvelle ligne avec un nouvel argument utilisant les valeurs par défaut suivantes : argumentx pour le **nom** où x est un entier avec une valeur initiale 1 qui est automatiquement incrémenté pour créer des noms d’argument unique, **dans**  pour le **Direction**, et **chaîne** pour le **type d’Argument**. Aucune valeur n’est ajoutée pour **valeur par défaut**. Vous pouvez modifier ces valeurs à tout moment pendant le processus de conception du workflow.

    > [!NOTE]
    > Pour supprimer un argument, sélectionnez l’argument en cliquant dessus, puis appuyez sur la **supprimer** clé.

## <a name="see-also"></a>Voir aussi

- [Utilisation du Concepteur de flux de travail](developing-applications-with-the-workflow-designer.md)
- [Variables et arguments](/dotnet/framework/windows-workflow-foundation/variables-and-arguments)