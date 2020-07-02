---
title: 'Concepteur de flux de travail-comment : utiliser le concepteur d’arguments'
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- System.Activities.Presentation.View.ArgumentDesigner.UI
- System.Activities.Presentation.View.DesignTimeArgument.UI
ms.assetid: 64813fd5-1ea1-499a-98b4-ab2a44b7ee5e
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6c3c0fe3de3a9ab74ed09c1be45e0d39a71a5b7c
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85817448"
---
# <a name="how-to-use-the-argument-designer"></a>Procédure : utiliser le concepteur d’arguments

Le concepteur d’arguments permet d’autoriser facilement le passage des données dans et hors d’une activité. Accédez au concepteur en cliquant sur le bouton **arguments** situé dans l’angle inférieur gauche de la zone de conception. Le concepteur contient une liste d’arguments qui s’affichent sous forme de tableau et peuvent être triés par chacun des en-têtes de colonne, à l’exception de la colonne de **valeur par défaut** . Chaque argument contient une direction Entrée, Sortie, Entrée-Sortie ou Propriété, un type et une valeur d’expression par défaut (le cas échéant). Le nom et la valeur d'expression par défaut sont des champs de texte modifiables ; le type et la direction sont des zones de liste déroulante. Pour plus d’informations, consultez [variables et arguments (.net)](/dotnet/framework/windows-workflow-foundation/variables-and-arguments).

## <a name="to-create-a-new-argument"></a>Pour créer un argument

1. Ouvrez un workflow ou une solution d’activité dans Visual Studio.

2. Ouvrez le concepteur d’arguments en cliquant sur le bouton **arguments** dans le coin inférieur gauche de la zone de conception. Le concepteur d’arguments s’affiche.

3. Cliquez sur la ligne vide intitulée **créer un argument**. Cette opération ajoute une nouvelle ligne avec un nouvel argument en utilisant les valeurs par défaut suivantes : argumentx comme pour le **nom** où x est un entier avec une valeur initiale de 1 qui est automatiquement incrémentée pour créer des noms d’arguments uniques, **dans** pour la **direction**et **chaîne** pour le **type d’argument**. Aucune valeur n’est ajoutée pour la **valeur par défaut**. Vous pouvez modifier ces valeurs à tout moment pendant le processus de conception du workflow.

    > [!NOTE]
    > Pour supprimer un argument, sélectionnez l’argument en cliquant dessus, puis appuyez sur la touche **Suppr** .

## <a name="see-also"></a>Voir aussi

- [Utilisation du Concepteur de flux de travail](developing-applications-with-the-workflow-designer.md)
- [Variables et arguments](/dotnet/framework/windows-workflow-foundation/variables-and-arguments)
