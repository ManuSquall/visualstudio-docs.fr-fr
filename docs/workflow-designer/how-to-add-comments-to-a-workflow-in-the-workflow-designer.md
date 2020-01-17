---
title: 'Concepteur de flux de travail-comment : ajouter des commentaires à un flux de travail'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- System.Activities.Presentation.Annotations.Annotation.UI
- Annotation
ms.assetid: 9aa0e8d6-8129-4438-8389-d460611581a7
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
author: TerryGLee
ms.openlocfilehash: 2e8f53e162360c7a43df9f0aedda3ff6ef0e6dba
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2020
ms.locfileid: "76114420"
---
# <a name="how-to-add-comments-to-a-workflow-in-the-workflow-designer"></a>Procédure : ajouter des commentaires à un workflow dans le Concepteur de flux de travail

Pour faciliter la création de flux de travail plus volumineux et plus complexes, .NET Framework 4,5 permet au développeur d’ajouter des annotations aux types d’éléments suivants dans le concepteur :

- <xref:System.Activities.Activity>

- <xref:System.Activities.Statements.State>

- <xref:System.Activities.Statements.Transition>

- Classes dérivées de <xref:System.Activities.Statements.FlowNode>.

- <xref:System.Activities.Variable>

- <xref:System.Activities.Argument>

> [!IMPORTANT]
> Le contenu d'une annotation est stocké sous forme de texte brut dans le fichier XAML associé au workflow, et peut être par d'autres utilisateurs. Évitez d'entrer des informations sensibles dans une annotation.

## <a name="adding-an-annotation-to-an-activity-in-the-designer"></a>Ajout d'une annotation à une activité dans le concepteur

1. Dans le concepteur de flux de travail, cliquez avec le bouton droit sur un élément dans le concepteur de flux de travail et sélectionnez **Annotations**, **Ajouter une annotation**.

1. Ajoutez le texte de l'annotation dans l'espace disponible.

   L’élément affiche une icône d’annotation. Le fait de pointer sur l’icône d’annotation affiche le texte de l’annotation.

## <a name="displaying-an-annotation-in-an-activitys-designer"></a>Afficher une annotation dans le concepteur d'une activité

1. Avec un concepteur d’activités qui a une annotation qui s’affiche en dehors de l’activité, cliquez sur l’icône d' **épingle** dans l’ornement d’annotation.

   L’annotation s’affiche dans le concepteur de l’activité. Dans la capture d'écran ci-dessous, l'annotation « Démarrage de l'activité dans le workflow » s'affiche dans le concepteur de l'activité.

   ![Annotation affichée dans le concepteur d'activités](../workflow-designer/media/annotationindesigner.png)

2. Pour afficher l’annotation en dehors du concepteur de l’activité, pointez sur la zone d’annotation dans le concepteur de l’activité, puis cliquez sur l’icône de **désépingler**

   ![Annotation affichée en dehors du concepteur d’une activité](../workflow-designer/media/annotationoutsidedesigner.png)

## <a name="showing-or-hiding-all-annotations"></a>Affichage ou masquage de toutes les annotations

1. Cliquez avec le bouton droit sur une activité qui a une annotation. Sélectionnez **Annotations**, **afficher toutes les annotations**.

   Toutes les annotations sont affichées dans les concepteurs de l’activité.

1. Pour afficher toutes les annotations en dehors des concepteurs de l’activité, cliquez avec le bouton droit sur l’activité et sélectionnez **Annotations**, puis **masquez toutes les annotations**.

## <a name="editing-or-deleting-an-annotation-for-an-activity"></a>Modification ou suppression d'une annotation pour une activité

1. Cliquez avec le bouton droit sur une activité qui a une annotation.

1. Sélectionnez **Annotations**, **modifier l’annotation** ou **Supprimer l’annotation**.

   L’annotation est ouverte pour modification ou suppression.

1. Pour supprimer toutes les annotations à la fois, cliquez avec le bouton droit sur le concepteur de flux de travail et sélectionnez **annotation**, **supprimer toutes les annotations**.

## <a name="adding-editing-and-deleting-an-annotation-for-a-variable-or-argument"></a>Ajout, modification et suppression d'une annotation pour une variable ou un argument

1. Cliquez avec le bouton droit sur une variable ou un argument et sélectionnez Ajouter une annotation.

1. Entrez le texte de l'annotation. La variable ou l’argument affiche une icône d’annotation.

1. Cliquez avec le bouton droit sur une variable ou un argument qui a une annotation. Sélectionnez Modifier une annotation.

   L’annotation est ouverte pour modification.

1. Cliquez avec le bouton droit sur une variable ou un argument qui a une annotation. Sélectionnez Supprimer l'annotation.

   L’annotation est supprimée.
