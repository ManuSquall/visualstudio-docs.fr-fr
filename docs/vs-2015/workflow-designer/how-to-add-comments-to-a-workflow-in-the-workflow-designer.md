---
title: 'Procédure : Ajouter des commentaires à un flux de travail dans le Concepteur de flux de travail | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Presentation.Annotations.Annotation.UI
- Annotation
ms.assetid: 9aa0e8d6-8129-4438-8389-d460611581a7
caps.latest.revision: 7
author: steved0x
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 507bb70539019646f57f0aa9267573429d3fa202
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63433563"
---
# <a name="how-to-add-comments-to-a-workflow-in-the-workflow-designer"></a>Procédure : Ajouter des commentaires à un workflow dans le concepteur de workflow
Pour faciliter la création de workflows de plus grande taille et plus complexes, [!INCLUDE[net_v45](../includes/net-v45-md.md)] permet au développeur d'ajouter des annotations aux types suivants d'élément dans le concepteur :  
  
- <xref:System.Activities.Activity>  
  
- <xref:System.Activities.Statements.State>  
  
- <xref:System.Activities.Statements.Transition>  
  
- Classes dérivées de <xref:System.Activities.Statements.FlowNode>.  
  
- <xref:System.Activities.Variable>  
  
- <xref:System.Activities.Argument>  
  
> [!IMPORTANT]
> Le contenu d'une annotation est stocké sous forme de texte brut dans le fichier XAML associé au workflow, et peut être par d'autres utilisateurs. Évitez d'entrer des informations sensibles dans une annotation.  
  
### <a name="adding-an-annotation-to-an-activity-in-the-designer"></a>Ajout d'une annotation à une activité dans le concepteur  
  
1. Dans le Concepteur de flux de travail, cliquez sur un élément dans le Concepteur de workflow et sélectionnez **Annotations**, **ajouter une Annotation**.  
  
2. Ajoutez le texte de l'annotation dans l'espace disponible.  
  
3. L'élément affiche une icône d'annotation. Lorsque vous placez le pointeur sur l'icône d'annotation, le texte de l'annotation s'affiche.  
  
     ![Séquence d’activité avec annotation](../workflow-designer/media/annotation.png "Annotation")  
  
### <a name="displaying-an-annotation-in-an-activitys-designer"></a>Afficher une annotation dans le concepteur d'une activité  
  
1. Avec un concepteur d’activités qui a une annotation affichée en dehors de l’activité, cliquez sur le **Pin** icône dans l’ornement d’annotation.  
  
2. L'annotation est affichée dans le concepteur de l'activité. Dans la capture d'écran ci-dessous, l'annotation « Démarrage de l'activité dans le workflow » s'affiche dans le concepteur de l'activité.  
  
     ![Annotation affichée dans le Concepteur d’activités](../workflow-designer/media/annotationindesigner.png "AnnotationInDesigner")  
  
3. Pour afficher l’annotation en dehors du Concepteur de l’activité, placez le curseur sur la zone d’annotation dans le Concepteur de l’activité et cliquez sur le **Unpin** icône  
  
     ![Annotation affichée en dehors d’un concepteur d’activités](../workflow-designer/media/annotationoutsidedesigner.png "AnnotationOutsideDesigner")  
  
### <a name="showing-or-hiding-all-annotations"></a>Affichage ou masquage de toutes les annotations  
  
1. Cliquez avec le bouton droit sur une activité qui a une annotation. Sélectionnez **Annotations**, **afficher toutes les Annotations**.  
  
2. Toutes les annotations sont affichées dans les concepteurs de l'activité.  
  
3. Pour afficher toutes les annotations en dehors des concepteurs de l’activité, cliquez sur l’activité et sélectionnez **Annotations**, **masquer toutes les Annotations**.  
  
### <a name="editing-or-deleting-an-annotation-for-an-activity"></a>Modification ou suppression d'une annotation pour une activité  
  
1. Cliquez avec le bouton droit sur une activité qui a une annotation.  
  
2. Sélectionnez **Annotations**, **modifier une Annotation** ou **supprimer l’Annotation**.  
  
3. L'annotation est ouverte pour modification ou supprimée.  
  
4. Pour supprimer toutes les annotations à la fois, cliquez sur le Concepteur de workflow et sélectionnez **Annotation**, **supprimer toutes les Annotations**.  
  
### <a name="adding-editing-and-deleting-an-annotation-for-a-variable-or-argument"></a>Ajout, modification et suppression d'une annotation pour une variable ou un argument  
  
1. Cliquez avec le bouton droit sur une variable ou un argument et sélectionnez Ajouter une annotation.  
  
2. Entrez le texte de l'annotation. La variable ou l'argument affiche une icône d'annotation.  
  
3. Cliquez avec le bouton droit sur une variable ou un argument qui a une annotation. Sélectionnez Modifier une annotation.  
  
4. L'annotation est ouverte pour modification.  
  
5. Cliquez avec le bouton droit sur une variable ou un argument qui a une annotation. Sélectionnez Supprimer l'annotation.  
  
6. L'annotation sera supprimée.