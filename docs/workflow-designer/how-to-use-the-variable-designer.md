---
title: 'Concepteur de flux de travail - Comment : Utiliser le concepteur de variables'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
f1_keywords:
- System.Activities.Presentation.View.DesignTimeVariable.UI
ms.assetid: 0318dfb0-bf8f-4f92-9b86-ae4c1b2161ad
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f6d50fa27111cfb7f58c39cb29e7ff34038a1b6e
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54959198"
---
# <a name="how-to-use-the-variable-designer"></a>Procédure : Utiliser le concepteur de variables

Le concepteur de variables permet de créer des variables en vue d’une utilisation dans des scénarios de liaison de données et des instructions conditionnelles. Le concepteur est accessible en cliquant sur le **Variables** situé dans l’angle inférieur gauche de la zone de conception. Le concepteur contient une liste de variables qui s’affichent sous forme tabulaire et peuvent être triées en fonction de chacun des en-têtes de colonnes, à l’exception de la **par défaut** colonne. Chaque variable contient un nom, un type de variable, une étendue et une valeur par défaut (le cas échéant). Le nom et la valeur par défaut sont des champs de texte modifiables, et le type et l'étendue sont des zones de liste déroulante. L'étendue est l'activité qui a été sélectionnée lors de l'appel du concepteur de variables. Si une variable ne peut pas être créée dans l'étendue de la sélection, l'étendue aura comme valeur par défaut l'activité ancêtre la plus proche de la sélection qui autorise la création de variables dans son étendue. Pour plus d’informations, consultez [Variables et arguments (.NET)](/dotnet/framework/windows-workflow-foundation/variables-and-arguments).

 L'ordre de tri n'est appliqué que lorsque l'utilisateur utilise explicitement l'un des contrôles de tri, ferme et rouvre le concepteur de variables ou crée une autre variable.

## <a name="to-create-a-new-variable"></a>Pour créer une variable

1.  Dans Visual Studio, ouvrez une solution de flux de travail ou d’activité.

2.  Sur la zone de conception, sélectionnez une activité dans votre workflow.

3.  Ouvrez le Concepteur de variables en cliquant sur le **Variables** situé dans l’angle inférieur gauche de la zone de conception. Le concepteur de variables s'affiche.

4.  Cliquez sur la ligne vide libellée **créer une Variable**. Cette opération ajoute une nouvelle ligne avec une nouvelle variable utilisant les valeurs par défaut suivantes : variablex pour le **nom** où x est un entier avec une valeur initiale 1 qui est automatiquement incrémenté pour créer des noms de variable uniques,  **Chaîne** pour le **type de Variable**, et **séquence** pour le **étendue**. Aucune valeur n’est ajoutée pour **par défaut**. Vous pouvez modifier ces valeurs à tout moment pendant le processus de conception du workflow.

    > [!NOTE]
    > Pour supprimer une variable, sélectionnez la variable en cliquant dessus, puis appuyez sur la **supprimer** clé.

## <a name="see-also"></a>Voir aussi

- [Utilisation du Concepteur de flux de travail](developing-applications-with-the-workflow-designer.md)
- [Variables et arguments](/dotnet/framework/windows-workflow-foundation/variables-and-arguments)
- [Guide pratique pour Utiliser le Concepteur d’arguments](../workflow-designer/how-to-use-the-argument-designer.md)