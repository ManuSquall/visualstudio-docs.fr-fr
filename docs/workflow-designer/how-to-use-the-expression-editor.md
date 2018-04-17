---
title: 'Comment : utiliser l’éditeur d’expressions | Documents Microsoft'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Presentation.View.ExpressionTextBox.UI
ms.assetid: b5f961dd-6dda-41a9-9cae-0383d479ef3d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f9873d341238f3278779277d70da6df56f29f721
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-use-the-expression-editor"></a>Procédure : utiliser l'éditeur d'expressions
L’éditeur d’Expression est un contrôle du Concepteur de flux de travail Windows qui est utilisé dans de nombreuses activités de flux de travail comme un moyen d’entrer et évaluer ces expressions. Il fournit une expérience d’édition IDE complète, comprenant, entre autres fonctionnalités, IntelliSense, la colorisation, ParamInfo et les tildes d’erreur. Le compilateur valide l'expression après sa saisie. Si l'expression n'est pas valide, une icône d'erreur s'affiche. Vous pouvez également ouvrir l’éditeur comme un **l’éditeur d’Expression** boîte de dialogue.

 Les expressions sont des valeurs littérales ou du code [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] liés à des arguments ou des propriétés. Elles contiennent des éléments de valeur (par exemple, des variables, des constantes, des littéraux ou des propriétés) combinés avec des opérations afin de produire une nouvelle valeur. Les expressions sont écrites à l'aide de la syntaxe VB.NET même si l'application se trouve dans un programme utilisant C#. Cela signifie que les majuscules ne sont pas, la comparaison est effectuée à l’aide un seul égal (« = ») au lieu de (« == »), les opérateurs booléens sont les mots « et » et « ou » au lieu des symboles « & & » et «&#124;&#124;», et **Nothing**  est utilisé à la place de **null**. Pour plus d’informations sur les expressions et opérateurs dans [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] et pour obtenir des exemples, consultez [opérateurs et Expressions en Visual Basic](http://go.microsoft.com/fwlink/?LinkId=186818).

 Le **l’éditeur d’Expression** se comporte comme suit :

-   Si le focus n'est pas sur l'éditeur d'expressions, celui-ci a l'apparence d'un contrôle TextBlock normal.

-   Lorsque le focus se trouve sur l'éditeur d'expressions, celui-ci adopte l'apparence et le comportement du contrôle de l'éditeur d'expressions. Lorsqu'il perd le focus, il reprend l'apparence d'un TextBlock classique.

-   Si vous placez le focus sur l'éditeur d'expressions dans un Workflow Designer réhébergé, il se comporte comme un contrôle TextBox. Lorsque le Workflow Designer réhébergé perd le focus, l'éditeur d'expressions reprend l'apparence d'un TextBlock normal.

> [!NOTE]
> IntelliSense pour l'éditeur d'expressions est uniquement disponible dans [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)]. Qu'il soit exécuté dans [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] ou réhébergé, le compilateur valide l'expression une fois qu'elle a été entrée et l'éditeur d'expressions affiche une icône d'erreur si l'expression n'est pas valide.

### <a name="using-the-expression-editor"></a>Utilisation de l'éditeur d'expressions

1.  Dans [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)], ouvrez un projet de flux de travail nouveau ou existant.

2.  Par exemple, ajoutez l'activité <xref:System.Activities.Statements.Assign> à votre flux de travail.

    > [!NOTE]
    > Plusieurs activités de flux de travail ont des éditeurs d'expressions. Des TextBlocks d'expression s'affichent également dans le concepteur de variables, le concepteur d'arguments et le concepteur d'arguments dynamique. L'activité <xref:System.Activities.Statements.Assign> est utilisée à titre d'exemple.

3.  Cliquez sur l'éditeur d'expressions à gauche dans le concepteur d'activités pour l'activité <xref:System.Activities.Statements.Assign>.

     Les chaînes en filigrane grises  **\<à >** et  **\<entrer une Expression VB >** est des chaînes de texte de la valeur par défaut pour les éditeurs d’expressions dans le <xref:System.Activities.Statements.Assign> activité.

4.  Entrez votre expression. Si vous entrez une chaîne, n'oubliez pas de l'entourer de guillemets. Si vous choisissez de lier l'argument Expression à une variable, n'utilisez pas de guillemets.

     Lorsque vous avez fini, sélectionnez une région ou une zone en dehors de l'éditeur d'expressions pour déplacer le focus vers une autre partie du concepteur. Le compilateur valide alors l'expression, comme décrit précédemment.

     Un autre manière d'entrer/modifier une expression consiste à cliquer sur les points de suspension en regard du nom de propriété dans la grille des propriétés. Cela ouvre le **l’éditeur d’Expression** en tant que boîte de dialogue.

## <a name="see-also"></a>Voir aussi

- <xref:System.Activities.Presentation.View.ExpressionTextBox>