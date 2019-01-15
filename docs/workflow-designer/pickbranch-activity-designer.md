---
title: Concepteur de flux de travail - Concepteur d’activités PickBranch
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
f1_keywords:
- System.Activities.Statements.PickBranch.UI
ms.assetid: f523ad47-bbc0-4cda-a35c-41e67c4ba081
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 86948845f2537f0785daeebbc349292891a7a3e2
ms.sourcegitcommit: 38db86369af19e174b0aba59ba1918a5c4fe4a61
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/14/2019
ms.locfileid: "54269863"
---
# <a name="pickbranch-activity-designer"></a>Concepteur d'activités PickBranch

L’objet <xref:System.Activities.Statements.PickBranch> fournit un chemin d’accès d’exécution basé sur les événements dans une activité <xref:System.Activities.Statements.Pick> qui peut être déclenchée par un événement entrant.

## <a name="pickbranch"></a>PickBranch

Les objets <xref:System.Activities.Statements.PickBranch> sont contenus dans la collection <xref:System.Activities.Statements.Pick.Branches%2A> d'une activité <xref:System.Activities.Statements.Pick>. Chaque <xref:System.Activities.Statements.PickBranch> est contenue dans une branche de l’activité <xref:System.Activities.Statements.Pick> et peut être exécutée en raison d’un événement entrant qui sert de déclencheur. De cette façon le Concepteur de Workflow fournit la modélisation des flux de contrôle basé sur des événements. Chaque <xref:System.Activities.Statements.PickBranch> contient une propriété <xref:System.Activities.Statements.PickBranch.Trigger%2A> et une propriété <xref:System.Activities.Statements.PickBranch.Action%2A>.

### <a name="how-to-use-the-pick-activity-designer"></a>Comment utiliser le concepteur d'activités Pick

Accès le **PickBranch** concepteur dans le **flux de contrôle** catégorie de la **boîte à outils**.

Deux vide <xref:System.Activities.Statements.PickBranch> objets avec des noms d’affichage des **Branch1** et **Branch2** sont créés par défaut en tant qu’éléments d’un <xref:System.Activities.Statements.Pick> activité lorsque le **choisir** Concepteur d’activités est initialement déposé sur le Concepteur de Workflow. Ces respectifs <xref:System.Activities.Statements.PickBranch.DisplayName%2A> les valeurs de propriété peuvent être modifiées dans le **PickBranch** en-tête du concepteur ou dans le **propriétés** fenêtre pour chaque branche.

Il existe deux façons d’ajouter <xref:System.Activities.Statements.PickBranch> objets à la collection d’un <xref:System.Activities.Statements.Pick> objet : glisser -déplacer le **PickBranch** concepteur à partir de la **boîte à outils**, ou à l’aide du menu contextuel à partir de dans le **choisir** aire de conception :

- Le **PickBranch** concepteur crée un <xref:System.Activities.Statements.PickBranch> lorsqu’il est déplacé à partir de la **boîte à outils** et déposé dans une des branches d’un **choisir** Concepteur d’activités sur le Aire du Concepteur de flux de travail. Les nouveaux objets <xref:System.Activities.Statements.PickBranch> peuvent être placés dans le concepteur <xref:System.Activities.Statements.Pick> à gauche ou à droite des éléments <xref:System.Activities.Statements.PickBranch> existants déjà contenus dans la collection. Lorsque vous faites glisser un **PickBranch** concepteur sur le **choisir** concepteur avec une souris, le **choisir** concepteur utilise une bande bleu gris verticale pour indiquer l’endroit où le <xref:System.Activities.Statements.PickBranch> est ajouté pour un positionnement de souris donné.

- Avec le bouton droit **choisir** Concepteur d’activités (mais pas à l’intérieur **PickBranch** designer) pour afficher un menu contextuel et sélectionnez **créer une branche** pour ajouter un nouveau <xref:System.Activities.Statements.PickBranch>. Notez que la nouvelle <xref:System.Activities.Statements.PickBranch> est ajouté à droite d’existant <xref:System.Activities.Statements.PickBranch> des objets dans le **choisir** concepteur.

Le **PickBranch** concepteur peut être développé pour révéler le **déclencheur** et **Action** zones ou réduit en cliquant sur le double signe ^ à droite de leurs en-têtes. Modifier le <xref:System.Activities.Statements.PickBranch.Trigger%2A> et <xref:System.Activities.Statements.PickBranch.Action%2A> de chacun d’eux <xref:System.Activities.Statements.PickBranch> en déposant des activités dans le **déclencheur** et **Action** cases de leurs concepteurs.

Le <xref:System.Activities.Statements.PickBranch> des objets dans le <xref:System.Activities.Statements.Pick.Branches%2A> collection d’un <xref:System.Activities.Statements.Pick> d’objets, peuvent être réorganisées par glisser- déposer vers un nouvel emplacement dans le **choisir** concepteur. Le **choisir** concepteur utilise une bande bleu gris verticale pour indiquer l’endroit où le <xref:System.Activities.Statements.PickBranch> est ajouté pour un positionnement de souris donné.

Il existe deux façons de supprimer un objet <xref:System.Activities.Statements.PickBranch> :

- Sélectionnez le **PickBranch** concepteur et supprimez-le.
- Sélectionnez le **PickBranch** concepteur, avec le bouton droit pour afficher le menu contextuel et sélectionnez **supprimer**.

Veillez à sélectionner le **PickBranch** concepteur, car la sélection d’une des activités à l’intérieur de son **déclencheur** ou **Action** zones supprime l’une de ces activités et non le <xref:System.Activities.Statements.PickBranch> objet.

### <a name="pickbranch-properties-in-the-workflow-designer"></a>Propriétés de PickBranch dans le concepteur de workflow

Le tableau suivant présente les plus utiles <xref:System.Activities.Statements.PickBranch> propriétés et décrit comment les utiliser dans le Concepteur de flux de travail.

|Nom de la propriété|Obligatoire|Utilisation|
|-|--------------|-|
|<xref:System.Activities.Statements.PickBranch.DisplayName%2A>|False|Le nom convivial affiché dans l’en-tête de la **PickBranch** concepteur. La valeur par défaut est Branch.<br /><br /> Bien que la propriété <xref:System.Activities.Activity.DisplayName%2A> ne soit pas strictement obligatoire, il est recommandé d'en utiliser une.|
|<xref:System.Activities.Statements.PickBranch.Trigger%2A>|True|Chaque objet <xref:System.Activities.Statements.PickBranch> contient une action <xref:System.Activities.Statements.PickBranch.Trigger%2A> qui peut appeler la propriété <xref:System.Activities.Statements.PickBranch.Action%2A>.|
|<xref:System.Activities.Statements.PickBranch.Action%2A>|False|Chaque objet <xref:System.Activities.Statements.PickBranch> contient une propriété <xref:System.Activities.Statements.PickBranch.Action%2A> qui est exécutée en cas de déclenchement.|

## <a name="see-also"></a>Voir aussi

- [Flux de contrôle](../workflow-designer/control-flow-activity-designers.md)
- [Activité Pick](/dotnet/framework/windows-workflow-foundation/pick-activity)
- [Utilisation de l’activité Pick](/dotnet/framework/windows-workflow-foundation/samples/using-the-pick-activity)