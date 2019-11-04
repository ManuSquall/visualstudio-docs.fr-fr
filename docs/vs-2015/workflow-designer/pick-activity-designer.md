---
title: Concepteur d’activités Pick | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Pick.UI
ms.assetid: 642c0a47-1b47-45de-a19a-ca0606cedd7a
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: daefc48cfff2c5c73d9ecf14316777becf4d83c5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672594"
---
# <a name="pick-activity-designer"></a>Concepteur d'activités Pick
L'activité <xref:System.Activities.Statements.Pick> fournit un flux de contrôle basé sur les événements. Elle exécute l'une des différentes branches en réponse à un événement de déclenchement.

## <a name="the-pick-activity"></a>Activité Pick
 Une activité <xref:System.Activities.Statements.Pick> contient une collection d’objets <xref:System.Activities.Statements.PickBranch>, dont l’un peut être exécuté par l’activité <xref:System.Activities.Statements.Pick> en raison d’un événement entrant qui sert de déclencheur. De cette manière, [!INCLUDE[wfd1](../includes/wfd1-md.md)] fournit la modélisation des flux de contrôle basée sur les événements. Chaque <xref:System.Activities.Statements.PickBranch> contient une propriété <xref:System.Activities.Statements.PickBranch.Trigger%2A> et une propriété <xref:System.Activities.Statements.PickBranch.Action%2A>. Au début de l'exécution d'une activité <xref:System.Activities.Statements.Pick>, toutes les activités de déclencheur des éléments <xref:System.Activities.Statements.PickBranch> sont planifiées. À l'issue de la première activité, l'activité d'action correspondante est planifiée et toutes les autres activités de déclencheur sont annulées.

### <a name="how-to-use-the-pick-activity-designer"></a>Comment utiliser le concepteur d'activités Pick
 Le concepteur d’activités **Pick** se trouve dans la catégorie **Flow Control** de la **boîte à outils**, accessible en cliquant sur l’onglet **boîte à outils** dans [!INCLUDE[wfd2](../includes/wfd2-md.md)] (ou en sélectionnant **barre d’outils** dans le menu **affichage** , ou encore en appuyant sur Ctrl + Alt). + X.)

 Le concepteur d’activités **Pick** peut être déplacé de la **boîte à outils** et déposé dans l’aire de [!INCLUDE[wfd2](../includes/wfd2-md.md)], là où les concepteurs d’activités sont généralement placés, par exemple dans un concepteur d’activités **Sequence** . Une fois déposé dans [!INCLUDE[wfd2](../includes/wfd2-md.md)], il crée une activité <xref:System.Activities.Statements.Pick>, laquelle contient par défaut deux activités <xref:System.Activities.Statements.PickBranch> vides comme éléments ayant les noms complets Branch1 et Branch2. Ces valeurs de propriété de <xref:System.Activities.Statements.PickBranch.DisplayName%2A> respectives peuvent être modifiées dans l’en-tête du concepteur d’activités **PickBranch** ou dans la fenêtre **Propriétés** pour chaque branche.

 Il existe deux façons d’ajouter des <xref:System.Activities.Statements.PickBranch> des activités à la collection d’un objet <xref:System.Activities.Statements.Pick> : en faisant glisser et en déposant le concepteur **PickBranch** à partir de la **boîte à outils** ou en utilisant le menu contextuel à partir de l’aire de conception **Pick** . Pour plus d’informations, consultez la rubrique [PickBranch](../workflow-designer/pickbranch-activity-designer.md) . Notez que le seul élément qui peut être placé à l’intérieur d’un concepteur d’activités **Pick** est un concepteur d’activités **PickBranch** .

### <a name="pick-activity-properties-in-the-workflow-designer"></a>Propriétés de l'activité Pick dans le concepteur de workflow
 Le tableau suivant présente les propriétés de <xref:System.Activities.Statements.Pick> et décrit comment elles sont utilisées dans le concepteur. Ces propriétés peuvent être modifiées dans la grille des propriétés ou dans l'aire du concepteur.

|Nom de la propriété|Obligatoire|Usage|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Spécifie le nom convivial du concepteur d'activités <xref:System.Activities.Statements.Pick> dans l'en-tête. La valeur par défaut est Pick. La valeur peut être modifiée dans la grille Propriétés ou directement dans l'en-tête du concepteur d'activités.<br /><br /> Bien que la propriété <xref:System.Activities.Activity.DisplayName%2A> ne soit pas strictement obligatoire, il est recommandé d'en utiliser une.|

## <a name="see-also"></a>Voir aussi
 [Flux de contrôle](../workflow-designer/control-flow-activity-designers.md) [Activité Pick](https://msdn.microsoft.com/library/b3e49b7f-0285-4720-8c09-11ae18f0d53e) [Utilisation de l’activité Pick](https://msdn.microsoft.com/library/b89be812-a247-4025-b0e3-ffb20db027a6)