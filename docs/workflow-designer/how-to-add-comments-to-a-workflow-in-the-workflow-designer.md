---
title: 'Le Concepteur de flux de travail - Comment : ajouter des commentaires à un flux de travail'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Presentation.Annotations.Annotation.UI
- Annotation
ms.assetid: 9aa0e8d6-8129-4438-8389-d460611581a7
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: ba21ba5b2ce6126d29d34f5df662e9e332359ed3
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-add-comments-to-a-workflow-in-the-workflow-designer"></a>Procédure : ajouter des commentaires à un workflow dans le Concepteur de flux de travail

Pour faciliter la création de flux de travail plus volumineux et plus complexes, .NET Framework 4.5 permet au développeur d’ajouter des annotations aux types suivants de l’élément dans le concepteur :

-   <xref:System.Activities.Activity>

-   <xref:System.Activities.Statements.State>

-   <xref:System.Activities.Statements.Transition>

-   Classes dérivées de <xref:System.Activities.Statements.FlowNode>.

-   <xref:System.Activities.Variable>

-   <xref:System.Activities.Argument>

> [!IMPORTANT]
> Le contenu d'une annotation est stocké sous forme de texte brut dans le fichier XAML associé au workflow, et peut être par d'autres utilisateurs. Évitez d'entrer des informations sensibles dans une annotation.

## <a name="adding-an-annotation-to-an-activity-in-the-designer"></a>Ajout d'une annotation à une activité dans le concepteur

1. Dans le Concepteur de flux de travail, cliquez sur un élément dans le Concepteur de workflow et sélectionnez **Annotations**, **ajouter une Annotation**.

1. Ajoutez le texte de l'annotation dans l'espace disponible.

   L’élément affiche une icône d’annotation. Vous pointez sur l’icône d’annotation affiche le texte de l’annotation.

## <a name="displaying-an-annotation-in-an-activitys-designer"></a>Afficher une annotation dans le concepteur d'une activité

1.  Un concepteur d’activités qui a une annotation affichée en dehors de l’activité, puis cliquez sur le **code confidentiel** icône dans l’ornement d’annotation.

   L’annotation s’affiche dans le Concepteur de l’activité. Dans la capture d'écran ci-dessous, l'annotation « Démarrage de l'activité dans le workflow » s'affiche dans le concepteur de l'activité.

   ![Annotation affichée dans le Concepteur d’activités](../workflow-designer/media/annotationindesigner.png "AnnotationInDesigner")

1. Pour afficher l’annotation en dehors du Concepteur de l’activité, placez le curseur sur la zone d’annotation dans le Concepteur de l’activité et cliquez sur le **détacher** icône

   ![Annotation affichée en dehors d’un concepteur d’activités](../workflow-designer/media/annotationoutsidedesigner.png "AnnotationOutsideDesigner")

## <a name="showing-or-hiding-all-annotations"></a>Affichage ou masquage de toutes les annotations

1. Cliquez avec le bouton droit sur une activité qui a une annotation. Sélectionnez **Annotations**, **afficher toutes les Annotations**.

   Toutes les annotations sont affichées dans les concepteurs de l’activité.

1. Pour afficher toutes les annotations en dehors des concepteurs de l’activité, cliquez sur l’activité et sélectionnez **Annotations**, **masquer toutes les Annotations**.

## <a name="editing-or-deleting-an-annotation-for-an-activity"></a>Modification ou suppression d'une annotation pour une activité

1. Cliquez avec le bouton droit sur une activité qui a une annotation.

1. Sélectionnez **Annotations**, **modifier une Annotation** ou **supprimer l’Annotation**.

   L’annotation est ouvert pour être modifié ou supprimée.

1. Pour supprimer toutes les annotations à la fois, cliquez sur le Concepteur de workflow et sélectionnez **Annotation**, **supprimer toutes les Annotations**.

## <a name="adding-editing-and-deleting-an-annotation-for-a-variable-or-argument"></a>Ajout, modification et suppression d’une annotation pour une variable ou un argument

1. Cliquez avec le bouton droit sur une variable ou un argument et sélectionnez Ajouter une annotation.

1. Entrez le texte de l'annotation. La variable ou l’argument affiche une icône d’annotation.

1. Cliquez avec le bouton droit sur une variable ou un argument qui a une annotation. Sélectionnez Modifier une annotation.

   L’annotation est ouvert pour modification.

1. Cliquez avec le bouton droit sur une variable ou un argument qui a une annotation. Sélectionnez Supprimer l'annotation.

   L’annotation est supprimée.