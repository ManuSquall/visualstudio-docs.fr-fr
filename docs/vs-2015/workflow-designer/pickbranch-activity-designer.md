---
title: Concepteur d’activités PickBranch | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.PickBranch.UI
ms.assetid: f523ad47-bbc0-4cda-a35c-41e67c4ba081
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c7c70aa8282fb8f50ed6faca5bcee3177ef81e15
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672584"
---
# <a name="pickbranch-activity-designer"></a>Concepteur d'activités PickBranch
L’objet <xref:System.Activities.Statements.PickBranch> fournit un chemin d’accès d’exécution basé sur les événements dans une activité <xref:System.Activities.Statements.Pick> qui peut être déclenchée par un événement entrant.

## <a name="pickbranch"></a>PickBranch
 Les objets <xref:System.Activities.Statements.PickBranch> sont contenus dans la collection <xref:System.Activities.Statements.Pick.Branches%2A> d'une activité <xref:System.Activities.Statements.Pick>. Chaque <xref:System.Activities.Statements.PickBranch> est contenue dans une branche de l’activité <xref:System.Activities.Statements.Pick> et peut être exécutée en raison d’un événement entrant qui sert de déclencheur. De cette manière, [!INCLUDE[wfd1](../includes/wfd1-md.md)] fournit la modélisation des flux de contrôle basée sur les événements. Chaque <xref:System.Activities.Statements.PickBranch> contient une propriété <xref:System.Activities.Statements.PickBranch.Trigger%2A> et une propriété <xref:System.Activities.Statements.PickBranch.Action%2A>.

### <a name="how-to-use-the-pick-activity-designer"></a>Comment utiliser le concepteur d'activités Pick
 Le concepteur **PickBranch** se trouve dans la catégorie **Flow Control** de la **boîte à outils**, accessible en cliquant sur l’onglet **boîte à outils** dans [!INCLUDE[wfd2](../includes/wfd2-md.md)] (ou en sélectionnant **barre d’outils** dans le menu **affichage** , ou encore en appuyant sur CTRL + ALT + X).

 Deux <xref:System.Activities.Statements.PickBranch> objets vides avec les noms d’affichage **branch1** et **branch2** sont créés par défaut comme éléments d’une <xref:System.Activities.Statements.Pick> activité lorsque le concepteur d’activités **Pick** est initialement déposé sur le [!INCLUDE[wfd2](../includes/wfd2-md.md)] . Ces <xref:System.Activities.Statements.PickBranch.DisplayName%2A> valeurs de propriétés respectives peuvent être modifiées dans l’en-tête du concepteur **PickBranch** ou dans la fenêtre **Propriétés** pour chaque branche.

 Il existe deux façons d’ajouter <xref:System.Activities.Statements.PickBranch> des objets à la collection d’un <xref:System.Activities.Statements.Pick> objet : en glissant et déposant le concepteur **PickBranch** à partir de la **boîte à outils** ou en utilisant le menu contextuel à partir de l’aire de conception **Pick** :

1. Le concepteur **PickBranch** crée un <xref:System.Activities.Statements.PickBranch> lorsqu’il est déplacé de la **boîte à outils** et déposé dans l’une des branches d’un concepteur d’activités **Pick** sur l’aire de conception [!INCLUDE[wfd2](../includes/wfd2-md.md)] . Les nouveaux objets <xref:System.Activities.Statements.PickBranch> peuvent être placés dans le concepteur <xref:System.Activities.Statements.Pick> à gauche ou à droite des éléments <xref:System.Activities.Statements.PickBranch> existants déjà contenus dans la collection. Quand vous faites glisser un concepteur **PickBranch** sur le concepteur de **sélection** avec une souris, le concepteur de **sélection** utilise une bande bleu-grise verticale pour indiquer où le <xref:System.Activities.Statements.PickBranch> est ajouté pour un positionnement de souris donné.

2. Cliquez avec le bouton droit sur le concepteur d’activités **Pick** (mais pas à l’intérieur du concepteur **PickBranch** ) pour obtenir un menu contextuel et sélectionnez **créer une branche** pour ajouter un nouveau <xref:System.Activities.Statements.PickBranch> . Notez que le nouveau <xref:System.Activities.Statements.PickBranch> est ajouté à droite des <xref:System.Activities.Statements.PickBranch> objets existants dans le concepteur **Pick** .

   Le concepteur **PickBranch** peut être développé pour révéler les zones **déclencheur** et **action** ou réduit en cliquant sur les signes deux-points à droite de leurs en-têtes. Modifiez les <xref:System.Activities.Statements.PickBranch.Trigger%2A> et <xref:System.Activities.Statements.PickBranch.Action%2A> de chaque <xref:System.Activities.Statements.PickBranch> en déplaçant les activités dans le **déclencheur** et les zones d' **action** de leurs concepteurs.

   Les <xref:System.Activities.Statements.PickBranch> objets de la <xref:System.Activities.Statements.Pick.Branches%2A> collection d’un <xref:System.Activities.Statements.Pick> objet peuvent être réorganisés en les faisant glisser vers un nouvel emplacement dans le concepteur **Pick** . Le concepteur de **sélection** utilise une bande bleu-grise verticale pour indiquer où le <xref:System.Activities.Statements.PickBranch> est ajouté pour un positionnement de souris donné.

   Il existe deux façons de supprimer un objet <xref:System.Activities.Statements.PickBranch> :

3. Sélectionnez le concepteur **PickBranch** et supprimez-le.

4. Sélectionnez **PickBranch** designer, cliquez avec le bouton droit pour obtenir le menu contextuel, puis sélectionnez **supprimer**.

   Veillez à sélectionner **PickBranch** designer, car la sélection de l’une des activités à l’intérieur de ses zones **déclencheur** ou **action** par erreur supprime l’une de ces activités et non l' <xref:System.Activities.Statements.PickBranch> objet.

### <a name="pickbranch-properties-in-the-workflow-designer"></a>Propriétés de PickBranch dans le concepteur de workflow
 Le tableau suivant affiche les propriétés les plus utiles de <xref:System.Activities.Statements.PickBranch> et décrit comment les utiliser dans le [!INCLUDE[wfd2](../includes/wfd2-md.md)].

|Nom de la propriété|Obligatoire|Usage|
|-------------------|--------------|-----------|
|<xref:System.Activities.Statements.PickBranch.DisplayName%2A>|Faux|Nom convivial affiché dans l’en-tête du concepteur **PickBranch** . La valeur par défaut est Branch.<br /><br /> Bien que la propriété <xref:System.Activities.Activity.DisplayName%2A> ne soit pas strictement obligatoire, il est recommandé d'en utiliser une.|
|<xref:System.Activities.Statements.PickBranch.Trigger%2A>|Vrai|Chaque objet <xref:System.Activities.Statements.PickBranch> contient une action <xref:System.Activities.Statements.PickBranch.Trigger%2A> qui peut appeler la propriété <xref:System.Activities.Statements.PickBranch.Action%2A>.|
|<xref:System.Activities.Statements.PickBranch.Action%2A>|Faux|Chaque objet <xref:System.Activities.Statements.PickBranch> contient une propriété <xref:System.Activities.Statements.PickBranch.Action%2A> qui est exécutée en cas de déclenchement.|

## <a name="see-also"></a>Voir aussi
 [Control Flow](../workflow-designer/control-flow-activity-designers.md) [Activité de prélèvement](https://msdn.microsoft.com/library/b3e49b7f-0285-4720-8c09-11ae18f0d53e) [de workflow à l’aide de l’activité Pick](https://msdn.microsoft.com/library/b89be812-a247-4025-b0e3-ffb20db027a6)