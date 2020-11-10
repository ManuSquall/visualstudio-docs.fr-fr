---
title: Concepteur d’activités Concepteur de flux de travail-PickBranch
description: Découvrez comment le concepteur d’activités PickBranch fournit un chemin d’exécution basé sur les événements dans une activité Pick qui peut être déclenchée par un événement entrant.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.PickBranch.UI
ms.assetid: f523ad47-bbc0-4cda-a35c-41e67c4ba081
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bce1cee7fad7ccff57a6911c99a9470a22b9a927
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94434231"
---
# <a name="pickbranch-activity-designer"></a>Concepteur d'activités PickBranch

L’objet <xref:System.Activities.Statements.PickBranch> fournit un chemin d’accès d’exécution basé sur les événements dans une activité <xref:System.Activities.Statements.Pick> qui peut être déclenchée par un événement entrant.

## <a name="pickbranch"></a>PickBranch

Les objets <xref:System.Activities.Statements.PickBranch> sont contenus dans la collection <xref:System.Activities.Statements.Pick.Branches%2A> d'une activité <xref:System.Activities.Statements.Pick>. Chaque <xref:System.Activities.Statements.PickBranch> est contenue dans une branche de l’activité <xref:System.Activities.Statements.Pick> et peut être exécutée en raison d’un événement entrant qui sert de déclencheur. De cette façon, le Concepteur de flux de travail fournit une modélisation de workflow basée sur les événements. Chaque <xref:System.Activities.Statements.PickBranch> contient une propriété <xref:System.Activities.Statements.PickBranch.Trigger%2A> et une propriété <xref:System.Activities.Statements.PickBranch.Action%2A>.

### <a name="how-to-use-the-pick-activity-designer"></a>Comment utiliser le concepteur d'activités Pick

Accédez à **PickBranch** Designer dans la catégorie **Flow Control** de la **boîte à outils**.

Deux <xref:System.Activities.Statements.PickBranch> objets vides avec les noms d’affichage **branch1** et **branch2** sont créés par défaut comme éléments d’une <xref:System.Activities.Statements.Pick> activité lorsque le concepteur d’activités **Pick** est initialement déposé sur la concepteur de flux de travail. Ces <xref:System.Activities.Statements.PickBranch.DisplayName%2A> valeurs de propriétés respectives peuvent être modifiées dans l’en-tête du concepteur **PickBranch** ou dans la fenêtre **Propriétés** pour chaque branche.

Il existe deux façons d’ajouter <xref:System.Activities.Statements.PickBranch> des objets à la collection d’un <xref:System.Activities.Statements.Pick> objet : en faisant glisser et en déposant le concepteur **PickBranch** à partir de la **boîte à outils** , ou en utilisant le menu contextuel à partir de l’aire de conception **Pick** :

- Le concepteur **PickBranch** crée un <xref:System.Activities.Statements.PickBranch> lorsqu’il est déplacé de la **boîte à outils** et déposé dans l’une des branches d’un concepteur d’activités **Pick** sur l’aire de concepteur de flux de travail. Les nouveaux objets <xref:System.Activities.Statements.PickBranch> peuvent être placés dans le concepteur <xref:System.Activities.Statements.Pick> à gauche ou à droite des éléments <xref:System.Activities.Statements.PickBranch> existants déjà contenus dans la collection. Quand vous faites glisser un concepteur **PickBranch** sur le concepteur de **sélection** avec une souris, le concepteur de **sélection** utilise une bande bleu-grise verticale pour indiquer où le <xref:System.Activities.Statements.PickBranch> est ajouté pour un positionnement de souris donné.

- Cliquez avec le bouton droit sur le concepteur d’activités **Pick** (mais pas à l’intérieur du concepteur **PickBranch** ) pour obtenir un menu contextuel et sélectionnez **créer une branche** pour ajouter un nouveau <xref:System.Activities.Statements.PickBranch> . Notez que le nouveau <xref:System.Activities.Statements.PickBranch> est ajouté à droite des <xref:System.Activities.Statements.PickBranch> objets existants dans le concepteur **Pick** .

Le concepteur **PickBranch** peut être développé pour révéler les zones **déclencheur** et **action** ou réduit en cliquant sur les signes deux-points à droite de leurs en-têtes. Modifiez les <xref:System.Activities.Statements.PickBranch.Trigger%2A> et <xref:System.Activities.Statements.PickBranch.Action%2A> de chaque <xref:System.Activities.Statements.PickBranch> en déplaçant les activités dans le **déclencheur** et les zones d' **action** de leurs concepteurs.

Les <xref:System.Activities.Statements.PickBranch> objets de la <xref:System.Activities.Statements.Pick.Branches%2A> collection d’un <xref:System.Activities.Statements.Pick> objet peuvent être réorganisés en les faisant glisser vers un nouvel emplacement dans le concepteur **Pick** . Le concepteur de **sélection** utilise une bande bleu-grise verticale pour indiquer où le <xref:System.Activities.Statements.PickBranch> est ajouté pour un positionnement de souris donné.

Il existe deux façons de supprimer un objet <xref:System.Activities.Statements.PickBranch> :

- Sélectionnez le concepteur **PickBranch** et supprimez-le.
- Sélectionnez **PickBranch** designer, cliquez avec le bouton droit pour obtenir le menu contextuel, puis sélectionnez **supprimer**.

Veillez à sélectionner **PickBranch** designer, car la sélection de l’une des activités à l’intérieur de ses zones **déclencheur** ou **action** par erreur supprime l’une de ces activités et non l' <xref:System.Activities.Statements.PickBranch> objet.

### <a name="pickbranch-properties-in-the-workflow-designer"></a>Propriétés de PickBranch dans le concepteur de workflow

Le tableau suivant présente les propriétés les plus utiles <xref:System.Activities.Statements.PickBranch> et décrit comment les utiliser dans le concepteur de flux de travail.

|Nom de la propriété|Obligatoire|Usage|
|-|--------------|-|
|<xref:System.Activities.Statements.PickBranch.DisplayName%2A>|Faux|Nom convivial affiché dans l’en-tête du concepteur **PickBranch** . La valeur par défaut est Branch.<br /><br /> Bien que la propriété <xref:System.Activities.Activity.DisplayName%2A> ne soit pas strictement obligatoire, il est recommandé d'en utiliser une.|
|<xref:System.Activities.Statements.PickBranch.Trigger%2A>|Vrai|Chaque objet <xref:System.Activities.Statements.PickBranch> contient une action <xref:System.Activities.Statements.PickBranch.Trigger%2A> qui peut appeler la propriété <xref:System.Activities.Statements.PickBranch.Action%2A>.|
|<xref:System.Activities.Statements.PickBranch.Action%2A>|Faux|Chaque objet <xref:System.Activities.Statements.PickBranch> contient une propriété <xref:System.Activities.Statements.PickBranch.Action%2A> qui est exécutée en cas de déclenchement.|

## <a name="see-also"></a>Voir aussi

- [Flux de contrôle](../workflow-designer/control-flow-activity-designers.md)
- [Activité Pick](/dotnet/framework/windows-workflow-foundation/pick-activity)
- [Utilisation de l’activité Pick](/dotnet/framework/windows-workflow-foundation/samples/using-the-pick-activity)