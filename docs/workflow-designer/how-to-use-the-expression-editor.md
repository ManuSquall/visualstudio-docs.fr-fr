---
title: 'Concepteur de flux de travail - Comment : Utiliser l’éditeur d’expressions'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- System.Activities.Presentation.View.ExpressionTextBox.UI
ms.assetid: b5f961dd-6dda-41a9-9cae-0383d479ef3d
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ce46f1db900aa5c37b49a1cc228290d7d99d29a2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62949537"
---
# <a name="how-to-use-the-expression-editor"></a>Procédure : Utiliser l’éditeur d’expressions

L’éditeur d’Expression est un contrôle de Concepteur de Workflow qui est utilisé dans de nombreuses activités de flux de travail pour entrer et évaluer des expressions. L’éditeur d’Expression fournit un IDE à part entière, modification de l’expérience, notamment IntelliSense, la colorisation, paraminfo et les tildes d’erreur, entre autres fonctionnalités. Le compilateur valide l’expression après sa saisie. Si l'expression n'est pas valide, une icône d'erreur s'affiche. L’éditeur peut également être ouvert comme un **Éditeur d’Expression** boîte de dialogue.

Les expressions sont des valeurs littérales ou du code Visual Basic liés à des arguments ou des propriétés. Elles contiennent des éléments de valeur (par exemple, variables, constantes, littéraux, propriétés) combinés à des opérations afin de produire une nouvelle valeur. Les expressions sont écrites à l'aide de la syntaxe VB.NET même si l'application se trouve dans un programme utilisant C#. Cela signifie que les majuscules ne sont pas, la comparaison est effectuée à l’aide d’une seule égale signer (« = » au lieu de « == »), les opérateurs booléens sont les mots « et » et « or » au lieu des symboles » & & » et « || », et **rien** est utilisé au lieu de **null**. Pour plus d’informations sur les expressions et opérateurs en Visual Basic et pour obtenir des exemples, consultez [opérateurs et expressions en Visual Basic](/previous-versions/visualstudio/visual-studio-2010/a1w3te48(v=vs.100)).

Le **Éditeur d’Expression** se comporte comme suit :

- Si le focus n'est pas sur l'éditeur d'expressions, celui-ci a l'apparence d'un contrôle TextBlock normal.

- Lorsque le focus se trouve sur l'éditeur d'expressions, celui-ci adopte l'apparence et le comportement du contrôle de l'éditeur d'expressions. Lorsqu’il perd le focus, l’éditeur d’Expression ressemble à un TextBlock normal à nouveau.

- Si vous placez le focus sur l'éditeur d'expressions dans un Workflow Designer réhébergé, il se comporte comme un contrôle TextBox. Lorsque le Workflow Designer réhébergé perd le focus, l'éditeur d'expressions reprend l'apparence d'un TextBlock normal.

> [!NOTE]
> IntelliSense pour l’éditeur d’expressions est disponible uniquement dans Visual Studio. Dans Visual Studio et réhébergé, le compilateur valide l’expression après sa saisie et de l’éditeur d’expressions affiche une icône d’erreur si l’expression n’est pas valide.

## <a name="use-the-expression-editor"></a>Utiliser l’éditeur d’expressions

1. Dans Visual Studio, ouvrez un projet de flux de travail nouveau ou existant.

2. Par exemple, ajoutez l'activité <xref:System.Activities.Statements.Assign> à votre flux de travail.

    > [!NOTE]
    > Plusieurs activités de flux de travail ont des éditeurs d'expressions. Des TextBlocks d’expression s’affichent également dans le concepteur de variables, le concepteur d’arguments et le concepteur d’arguments dynamique. L'activité <xref:System.Activities.Statements.Assign> est utilisée à titre d'exemple.

3. Cliquez sur l'éditeur d'expressions à gauche dans le concepteur d'activités pour l'activité <xref:System.Activities.Statements.Assign>.

     Les chaînes en filigrane grises  **\<à >** et  **\<entrer une Expression VB >** est des chaînes de texte de la valeur par défaut pour les éditeurs d’expressions dans le <xref:System.Activities.Statements.Assign> activité.

4. Entrez votre expression. Si vous entrez une chaîne, n'oubliez pas de l'entourer de guillemets. Si vous choisissez de lier l’argument Expression à une variable, n’utilisez pas de guillemets.

     Lorsque vous avez terminé, sélectionnez une région ou une zone en dehors de l’éditeur d’expressions pour déplacer le focus vers une autre partie du concepteur. Un décalage le focus d’indique au compilateur de valider l’expression, comme décrit précédemment.

     Une autre façon pour entrer ou modifier une expression consiste à cliquer sur les points de suspension en regard du nom de propriété dans la grille des propriétés. Cliquez sur le bouton de sélection ouvre le **Éditeur d’Expression** comme une boîte de dialogue.

## <a name="see-also"></a>Voir aussi

- <xref:System.Activities.Presentation.View.ExpressionTextBox>