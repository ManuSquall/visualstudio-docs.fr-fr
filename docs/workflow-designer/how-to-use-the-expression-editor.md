---
title: 'Concepteur de flux de travail-comment : utiliser l’éditeur d’expressions'
description: Découvrez comment l’éditeur d’expressions est un contrôle de Concepteur de flux de travail que vous pouvez utiliser dans de nombreuses activités de flux de travail pour entrer et évaluer des expressions.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- System.Activities.Presentation.View.ExpressionTextBox.UI
ms.assetid: b5f961dd-6dda-41a9-9cae-0383d479ef3d
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 855326085a51ec6590bd1b3f0e1e5565c53396cb
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94437851"
---
# <a name="how-to-use-the-expression-editor"></a>Procédure : utiliser l'éditeur d'expressions

L’éditeur d’expressions est un contrôle Concepteur de flux de travail utilisé dans de nombreuses activités de flux de travail pour entrer et évaluer des expressions. L’éditeur d’expressions fournit une expérience d’édition IDE complète, notamment IntelliSense, la colorisation, ParamInfo et, les tildes d’erreur, entre autres fonctionnalités. Le compilateur valide l’expression après qu’elle a été entrée. Si l'expression n'est pas valide, une icône d'erreur s'affiche. L’éditeur peut également être ouvert en tant que boîte de dialogue **éditeur d’expressions** .

Les expressions sont des valeurs littérales ou du code Visual Basic liés à des arguments ou des propriétés. Elles contiennent des éléments de valeur (par exemple, des variables, des constantes, des littéraux, des propriétés) qui sont associés à des opérations afin de produire une nouvelle valeur. Les expressions sont écrites à l'aide de la syntaxe VB.NET même si l'application se trouve dans un programme utilisant C#. Cela signifie que la mise en majuscules n’a pas d’importance. la comparaison est effectuée à l’aide d’un seul signe égal (« = » au lieu de « = = »), les opérateurs booléens sont les mots « and » et « or » au lieu des symboles « && » et « | | », et **rien** n’est utilisé à la place de **null**. Pour plus d’informations sur les expressions et les opérateurs dans Visual Basic et pour obtenir des exemples, consultez [opérateurs et expressions dans Visual Basic](/previous-versions/visualstudio/visual-studio-2010/a1w3te48(v=vs.100)).

L' **éditeur d’expressions** se comporte comme suit :

- Si le focus n'est pas sur l'éditeur d'expressions, celui-ci a l'apparence d'un contrôle TextBlock normal.

- Lorsque le focus se trouve sur l'éditeur d'expressions, celui-ci adopte l'apparence et le comportement du contrôle de l'éditeur d'expressions. Une fois qu’elle perd le focus, l’éditeur d’expressions ressemble à nouveau à un TextBlock standard.

- Si vous placez le focus sur l'éditeur d'expressions dans un Workflow Designer réhébergé, il se comporte comme un contrôle TextBox. Lorsque le Workflow Designer réhébergé perd le focus, l'éditeur d'expressions reprend l'apparence d'un TextBlock normal.

> [!NOTE]
> IntelliSense pour l’éditeur d’expressions est uniquement disponible dans Visual Studio. Dans Visual Studio et dans les scénarios réhébergés, le compilateur valide l’expression après son entrée et l’éditeur d’expressions affiche une icône d’erreur si l’expression n’est pas valide.

## <a name="use-the-expression-editor"></a>Utiliser l’éditeur d’expressions

1. Dans Visual Studio, ouvrez un projet de flux de travail nouveau ou existant.

2. Par exemple, ajoutez l'activité <xref:System.Activities.Statements.Assign> à votre flux de travail.

    > [!NOTE]
    > Plusieurs activités de flux de travail ont des éditeurs d'expressions. Des TextBlocks d’expression s’affichent également dans le concepteur de variables, le concepteur d’arguments et le concepteur d’arguments dynamique. L'activité <xref:System.Activities.Statements.Assign> est utilisée à titre d'exemple.

3. Cliquez sur l'éditeur d'expressions à gauche dans le concepteur d'activités pour l'activité <xref:System.Activities.Statements.Assign>.

     Les chaînes de filigrane gris **\<To>** et **\<Enter a VB Expression>** sont les chaînes de texte par défaut pour les éditeurs d’expressions dans l' <xref:System.Activities.Statements.Assign> activité.

4. Entrez votre expression. Si vous entrez une chaîne, n'oubliez pas de l'entourer de guillemets. Si vous choisissez de lier l’argument Expression à une variable, n’utilisez pas de guillemets.

     Lorsque vous avez terminé, sélectionnez une région ou une zone en dehors de l’éditeur d’expressions pour déplacer le focus vers une autre partie du concepteur. Si vous décalez le focus, le compilateur valide l’expression comme décrit précédemment.

     Pour entrer ou modifier une expression, vous pouvez également cliquer sur les points de suspension en regard du nom de la propriété dans la grille des propriétés. La sélection des points de suspension ouvre l' **éditeur d’expressions** comme une boîte de dialogue.

## <a name="see-also"></a>Voir aussi

- <xref:System.Activities.Presentation.View.ExpressionTextBox>
