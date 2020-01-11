---
title: 'Comment : utiliser l’éditeur d’expressions | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Presentation.View.ExpressionTextBox.UI
ms.assetid: b5f961dd-6dda-41a9-9cae-0383d479ef3d
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 54099bc5c0f249cdb3697715d153a94a596ac344
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75849230"
---
# <a name="how-to-use-the-expression-editor"></a>Procédure : utiliser l'éditeur d'expressions
L'éditeur d'expressions est un contrôle de [!INCLUDE[wfd1](../includes/wfd1-md.md)] utilisé dans de nombreuses activités de flux de travail pour entrer et évaluer des expressions. Il fournit une expérience d’édition IDE complète, comprenant, entre autres fonctionnalités, IntelliSense, la colorisation, ParamInfo et les tildes d’erreur. Le compilateur valide l'expression après sa saisie. Si l'expression n'est pas valide, une icône d'erreur s'affiche. L’éditeur peut également être ouvert en tant que boîte de dialogue **éditeur d’expressions** .

 Les expressions sont des valeurs littérales ou du code [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] liés à des arguments ou des propriétés. Elles contiennent des éléments de valeur (par exemple, des variables, des constantes, des littéraux ou des propriétés) combinés avec des opérations afin de produire une nouvelle valeur. Les expressions sont écrites à l'aide de la syntaxe VB.NET même si l'application se trouve dans un programme utilisant C#. Cela signifie que la mise en majuscules n’a pas d’importance. la comparaison est effectuée à l’aide d’un signe égal (« = ») au lieu de (« = = »), les opérateurs booléens sont les mots « and » et « or&#124;&#124;» au lieu des symboles « & & » et «», et **rien** n’est utilisé à la place de **null**. Pour plus d’informations sur les expressions et les opérateurs dans [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] et pour obtenir des exemples, consultez [opérateurs et expressions dans Visual Basic](https://msdn.microsoft.com/library/a1w3te48(VS.100).aspx).

 L' **éditeur d’expressions** se comporte comme suit :

- Si le focus n'est pas sur l'éditeur d'expressions, celui-ci a l'apparence d'un contrôle TextBlock normal.

- Lorsque le focus se trouve sur l'éditeur d'expressions, celui-ci adopte l'apparence et le comportement du contrôle de l'éditeur d'expressions. Lorsqu'il perd le focus, il reprend l'apparence d'un TextBlock classique.

- Si vous placez le focus sur l'éditeur d'expressions dans un Workflow Designer réhébergé, il se comporte comme un contrôle TextBox. Lorsque le Workflow Designer réhébergé perd le focus, l'éditeur d'expressions reprend l'apparence d'un TextBlock normal.

> [!NOTE]
> IntelliSense pour l'éditeur d'expressions est uniquement disponible dans [!INCLUDE[vs2010](../includes/vs2010-md.md)]. Qu'il soit exécuté dans [!INCLUDE[vs2010](../includes/vs2010-md.md)] ou réhébergé, le compilateur valide l'expression une fois qu'elle a été entrée et l'éditeur d'expressions affiche une icône d'erreur si l'expression n'est pas valide.

### <a name="using-the-expression-editor"></a>Utilisation de l'éditeur d'expressions

1. Dans [!INCLUDE[vs2010](../includes/vs2010-md.md)], ouvrez un projet de flux de travail nouveau ou existant.

2. Par exemple, ajoutez l'activité <xref:System.Activities.Statements.Assign> à votre flux de travail.

    > [!NOTE]
    > Plusieurs activités de flux de travail ont des éditeurs d'expressions. Des TextBlocks d’expression s’affichent également dans le concepteur de variables, le concepteur d’arguments et le concepteur d’arguments dynamique. L'activité <xref:System.Activities.Statements.Assign> est utilisée à titre d'exemple.

3. Cliquez sur l'éditeur d'expressions à gauche dans le concepteur d'activités pour l'activité <xref:System.Activities.Statements.Assign>.

     Les chaînes en filigrane gris **\<pour >** et **\<entrer une expression VB >** sont les chaînes de texte par défaut pour les éditeurs d’expressions dans l’activité <xref:System.Activities.Statements.Assign>.

4. Entrez votre expression. Si vous entrez une chaîne, n'oubliez pas de l'entourer de guillemets. Si vous choisissez de lier l’argument Expression à une variable, n’utilisez pas de guillemets.

     Lorsque vous avez fini, sélectionnez une région ou une zone en dehors de l'éditeur d'expressions pour déplacer le focus vers une autre partie du concepteur. Le compilateur valide alors l'expression, comme décrit précédemment.

     Un autre manière d'entrer/modifier une expression consiste à cliquer sur les points de suspension en regard du nom de propriété dans la grille des propriétés. Cette opération ouvre l' **éditeur d’expressions** comme boîte de dialogue.

## <a name="see-also"></a>Voir aussi
 <xref:System.Activities.Presentation.View.ExpressionTextBox>
