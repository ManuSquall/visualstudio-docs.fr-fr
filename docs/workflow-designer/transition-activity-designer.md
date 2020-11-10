---
title: Concepteur d’activités Concepteur de flux de travail-transition
description: Découvrez comment vous pouvez utiliser le concepteur d’activités de transition pour configurer une transition entre deux États.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Transition.UI
ms.assetid: f6e8b5cc-7fb8-4699-9703-f3c9fc7cc316
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
author: TerryGLee
ms.openlocfilehash: cedc9c7b6f402ad3f5f2c40e21c29e2a0d1ad2e6
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94433724"
---
# <a name="transition-activity-designer"></a>Concepteur d'activités de transition

<xref:System.Activities.Statements.Transition> représente la transition entre deux états.

## <a name="using-the-transition-activity-designer"></a>Utilisation du concepteur d'activités Transition

Le concepteur d'activités de transition vous permet de configurer une transition entre deux états.

### <a name="transition-properties-in-the-workflow-designer"></a>Propriétés de transition dans le concepteur de workflow

Le tableau suivant indique les propriétés  <xref:System.Activities.Statements.Transition> qui peuvent être définies à l'aide du concepteur de workflow et explique comment elles sont utilisées dans le concepteur.

|Nom de la propriété|Obligatoire|Usage|
|-|--------------|-|
|<xref:System.Activities.Statements.Transition.DisplayName%2A>|Faux|Spécifie le nom convivial du concepteur d'activités <xref:System.Activities.Statements.Transition>. La valeur par défaut est **T1**. La valeur peut être modifiée dans la grille des propriétés, dans l'en-tête du concepteur de transition développé et dans l'en-tête de la section d'action du concepteur de transition développé. <xref:System.Activities.Activity.DisplayName%2A> est utilisé dans l'exploration à l'aide de la barre de navigation qui est affichée en haut du concepteur de workflow.<br /><br /> Bien que la propriété <xref:System.Activities.Activity.DisplayName%2A> ne soit pas strictement obligatoire, il est recommandé d'en utiliser une.|
|<xref:System.Activities.Statements.Transition.Condition%2A>|Faux|S’il est présent, spécifie une expression qui doit avoir la **valeur true** avant que le contrôle soit passé à l’état de destination. Cette condition peut être modifiée dans la grille des propriétés et dans le concepteur de transition développé. Plusieurs conditions dans une transition partagée sont évaluées dans l'ordre dans lequel elles apparaissent dans le concepteur de transition. **Remarque :**  Notez que si le <xref:System.Activities.Statements.Transition.Condition%2A> d’une transition prend la **valeur false** (ou que toutes les conditions d’une transition de déclencheur partagée ont la **valeur false** ), la transition n’aura pas lieu et tous les déclencheurs de toutes les transitions de l’État seront replanifiés. Dans ce didacticiel, cette situation ne peut pas se produire en raison de la façon dont les conditions sont configurées (il existe des actions spécifiques lorsque l'estimation est correcte ou incorrecte).|
|**Source**|Vrai|Indique l'état d'origine de la transition. Cliquez sur le nom de l’état source pour faire basculer l’affichage du concepteur vers une vue développée de cet état. Cette valeur est définie lorsque la transition est créée et ne peut pas être modifiée.|
|<xref:System.Activities.Statements.Transition.Trigger%2A>|Faux|Spécifie l'activité dont l'achèvement initialise la transition. Pour définir cette activité, faites glisser une activité de la **boîte à outils** et déposez-la dans la section **déclencheur** de la transition.|
|<xref:System.Activities.Statements.Transition.Action%2A>|Faux|Spécifie l’activité qui est exécutée lorsque l’activité de déclencheur est terminée et <xref:System.Activities.Statements.Transition.Condition%2A> , le cas échéant, prend la **valeur true**. Cette activité est exécutée lors de la transition vers l'état de destination, après l'exécution de l'activité <xref:System.Activities.Statements.State.Exit%2A> pour l'état source, le cas échéant. Lorsque le concepteur de transition est développé, cette valeur peut être définie en faisant glisser une activité de la **boîte à outils** et en la déposant dans la section **action** de la transition. Il peut y avoir plusieurs actions pour une transition unique. Les différentes actions peuvent être développées et contractées, et peuvent être classées en cliquant sur la flèche haut ou bas qui apparaît sur l’action lorsqu’il existe plusieurs actions dans une transition.|
|**Destination**|Vrai|Indique l'état auquel la machine à états passe une fois la transition terminée. Cela correspond à la propriété <xref:System.Activities.Statements.Transition.To%2A> de la transition du modèle objet. Cliquez sur le nom de l'état de destination pour faire basculer l'affichage du concepteur vers une vue développée de cet état. Cette valeur est définie lorsque la transition est créée et peut être modifiée en faisant glisser la flèche qui connecte la transition à l'état de destination dans le concepteur.|

### <a name="creating-transitions"></a>Créer des transitions

Les transitions sont créées en faisant glisser une ligne d’un état à un autre, ou en déposant un état sur les triangles qui s’affichent lorsqu’un état est déplacé sur un autre état. Pour créer une transition en faisant glisser, pointez la souris sur le bord de l'état source, et faites glisser une ligne de l'état source vers l'état de destination. Pour créer une transition par dépôt, faites glisser l’état de destination et pointez sur l’état source, puis déposez-le sur l’un des quatre triangles qui apparaissent autour de l’état source. L’état de destination peut être un nouvel État déplacé à partir de la **boîte à outils** ou un état existant déplacé du concepteur de Workflow.

> [!NOTE]
> Un seul état dans une machine à états peut contenir jusqu'à 76 transitions créées à l'aide du concepteur de workflow. Le nombre maximal de transitions d'un état pour les workflows créés en dehors du concepteur est limité uniquement par les ressources système.

Les transitions partagées de déclencheur sont le jeu de transitions qui partagent le même événement déclencheur. Un déclencheur partagé permet la progression conditionnelle à un état de destination en fonction de l'évaluation de l'expressions configurée pour plusieurs transitions qui partagent un événement déclencheur commun. Pour ajouter des actions supplémentaires à une transition et créer une transition partagée, cliquez sur le cercle qui indique le début de la transition souhaitée et faites-le glisser vers l'état souhaité. La nouvelle transition partagera le même déclencheur que la transition d'origine, mais elle aura une condition et une action uniques. Des transitions partagées peuvent également être créées à partir du concepteur de transition en cliquant sur **Ajouter une transition de déclencheur partagée** en bas du concepteur de transition, puis en sélectionnant l’État cible souhaité dans la liste déroulante **États disponibles pour la connexion** .

## <a name="see-also"></a>Voir aussi

- [StateMachine](../workflow-designer/statemachine-activity-designer.md)
- [FinalState](../workflow-designer/finalstate-activity-designer.md)
- [State](../workflow-designer/state-activity-designer.md)
