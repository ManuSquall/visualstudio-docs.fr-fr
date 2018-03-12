---
title: "Comment : utiliser le Concepteur de variables | Documents Microsoft"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Presentation.View.DesignTimeVariable.UI
ms.assetid: 0318dfb0-bf8f-4f92-9b86-ae4c1b2161ad
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: d23307cc40084cdd455b6aaf8eee8ce675d8656d
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2018
---
# <a name="how-to-use-the-variable-designer"></a>Procédure : utiliser le concepteur de variables
Le concepteur de variables permet de créer des variables en vue d’une utilisation dans des scénarios de liaison de données et des instructions conditionnelles. Le concepteur est accessible en cliquant sur le **Variables** situé dans l’angle inférieur gauche de la zone de conception. Le concepteur contient une liste de variables qui apparaissent dans une forme tabulaire et peuvent être triées en fonction de chacun des en-têtes de colonnes, à l’exception de la **par défaut** colonne. Chaque variable contient un nom, un type de variable, une étendue et une valeur par défaut (le cas échéant). Le nom et la valeur par défaut sont des champs de texte modifiables, et le type et l'étendue sont des zones de liste déroulante. L'étendue est l'activité qui a été sélectionnée lors de l'appel du concepteur de variables. Si une variable ne peut pas être créée dans l'étendue de la sélection, l'étendue aura comme valeur par défaut l'activité ancêtre la plus proche de la sélection qui autorise la création de variables dans son étendue. Pour plus d’informations, consultez [Variables et arguments (.NET)](/dotnet/framework/windows-workflow-foundation/variables-and-arguments).

 L'ordre de tri n'est appliqué que lorsque l'utilisateur utilise explicitement l'un des contrôles de tri, ferme et rouvre le concepteur de variables ou crée une autre variable.

### <a name="to-create-a-new-variable"></a>Pour créer une variable

1.  Ouvrez un workflow ou une solution d'activité dans [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].

2.  Sur la zone de conception, sélectionnez une activité dans votre workflow.

3.  Ouvrez le Concepteur de variables en cliquant sur le **Variables** situé dans l’angle inférieur gauche de la zone de conception. Le concepteur de variables s'affiche.

4.  Cliquez sur la ligne vide libellée **créer une Variable**. Cela ajoutera une nouvelle ligne avec une nouvelle variable utilisant les valeurs par défaut suivantes : variablex pour le **nom** où x est un entier avec une valeur initiale 1 qui est incrémenté automatiquement pour créer des noms de variable uniques,  **Chaîne** pour le **le type de Variable**, et **séquence** pour le **étendue**. Aucune valeur n’est ajoutée pour **par défaut**. Vous pouvez modifier ces valeurs à tout moment pendant le processus de conception du workflow.

    > [!NOTE]
    > Pour supprimer une variable, sélectionnez la variable en cliquant dessus et appuyez sur la **supprimer** clé.

## <a name="see-also"></a>Voir aussi

- [Utilisation du Concepteur de flux de travail](../workflow-designer/using-the-workflow-designer.md)
- [Variables et arguments](/dotnet/framework/windows-workflow-foundation/variables-and-arguments)
- [Guide pratique pour utiliser le Concepteur d’arguments](../workflow-designer/how-to-use-the-argument-designer.md)