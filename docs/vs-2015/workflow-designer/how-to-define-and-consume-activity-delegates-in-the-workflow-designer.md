---
title: 'Comment : définir et utiliser des délégués d’activité dans le Concepteur de flux de travail | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: c68e42ad-3ec0-4c2d-b104-fe36c6d83b5e
caps.latest.revision: 3
author: steved0x
ms.author: gewarren
manager: erikre
ms.openlocfilehash: f99816153870884f868a6b229068bdc281408337
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49865490"
---
# <a name="how-to-define-and-consume-activity-delegates-in-the-workflow-designer"></a>Procédure : définir et utiliser des délégués d'activité dans le Concepteur de flux de travail
[!INCLUDE[net_v45](../includes/net-v45-md.md)] inclut un nouveau concepteur prêt à l'emploi pour l'activité <xref:System.Activities.Statements.InvokeDelegate>. Ce concepteur peut être utilisé pour assigner des délégués à l'activité qui dérive de <xref:System.Activities.ActivityDelegate>, telle que <xref:System.Activities.ActivityAction> ou <xref:System.Activities.ActivityFunc%601>.  
  
### <a name="define-an-activity-delegate"></a>Définir un délégué d'activité  
  
1. Dans [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)], sélectionnez **fichier**, **New**, **projet**. Sélectionnez le **Workflow** nœud sur la gauche et le **Application Console de Workflow** modèle sur la droite. Nommez le projet (le cas échéant) et cliquez sur **Ok**.  
  
2. Avec le bouton droit sur le projet dans **l’Explorateur de solutions** et sélectionnez **ajouter**, **un nouvel élément...** . Sélectionnez le **Workflow** nœud sur la gauche et le **activité** modèle sur la droite. Nommez la nouvelle activité **MyForEach.xaml** et cliquez sur **Ok**. L'activité s'ouvre dans le concepteur de workflow.  
  
3. Dans le Concepteur de flux de travail, cliquez sur le **Arguments** onglet.  
  
4. Cliquez sur **créer un Argument**. Nommez le nouvel argument **éléments**.  
  
5. Dans le **type d’Argument** colonne, sélectionnez **tableau de [T]**.  
  
6. Dans l’Explorateur de types, sélectionnez **objet**. Cliquez sur **Ok**.  
  
7. Cliquez sur **créer un Argument** à nouveau. Nommez le nouvel argument **corps**. Dans le **Direction** colonne pour le nouvel argument, sélectionnez **propriété**.  
  
8. Dans la colonne de Type d’Argument, sélectionnez **rechercher des types...**  
  
9. Dans l’Explorateur de types, entrez **ActivityAction** dans le **nom de Type** champ. Sélectionnez **ActivityAction\<T >** dans l’arborescence. Sélectionnez **objet** dans la liste déroulante qui s’affiche pour affecter le type **ActivityAction\<objet >** à l’argument.  
  
10. Faites glisser un <xref:System.Activities.Statements.While> activité à partir de la **flux de contrôle** section de la boîte à outils vers l’aire du concepteur.  
  
11. Sélectionnez le <xref:System.Activities.Statements.While> activité, puis sélectionnez le **Variables** onglet.  
  
12. Sélectionnez **créer la Variable**. Nommez la nouvelle variable **Index**.  
  
13. Dans le **type de Variable** colonne, sélectionnez **Int32**. Laissez le **étendue** comme **tandis que**et le **par défaut** colonne vide.  
  
14. Définir le **Condition** propriété de la <xref:System.Activities.Statements.While> activité **index < Items.Length ;**.  
  
15. Faites glisser un <xref:System.Activities.Statements.InvokeDelegate> activité à partir de la **Primitives** section de la boîte à outils vers le **corps** de la <xref:System.Activities.Statements.While> activité.  
  
16. Sélectionnez **corps** dans la liste déroulante délégué.  
  
17. Dans le **propriétés** grille pour la <xref:System.Activities.Statements.InvokeDelegate> activité, cliquez sur le **...** bouton dans le **Arguments délégués** propriété.  
  
18. Dans le **valeur** colonne de l’argument nommé **Argument**, entrez **Items [Index]**. Cliquez sur **Ok** pour fermer la **DelegateArguments** boîte de dialogue.  
  
19. Faites glisser une activité <xref:System.Activities.Statements.Assign> sur la ligne horizontale sous l'activité <xref:System.Activities.Statements.InvokeDelegate>. Le <xref:System.Activities.Statements.Assign> activité est créée et un <xref:System.Activities.Statements.Sequence> activité est créée automatiquement pour contenir les deux activités dans le **corps** section de la **MyForEach** activité. La séquence est nécessaire, car le **corps** section peut contenir uniquement une seule activité. La fonctionnalité de création automatique d’une nouvelle activité <xref:System.Activities.Statements.Sequence> est une nouveauté du [!INCLUDE[net_v45](../includes/net-v45-md.md)].  
  
20. Définir le **à** propriété de la <xref:System.Activities.Statements.Assign> activité **index**. Définir le **valeur** propriété de la **affecter** activité **index + 1**.  
  
    Personnalisé **MyForEach** activité appelle maintenant une activité arbitraire une fois pour chaque valeur passée dans celle-ci via la **éléments** collection avec les valeurs dans la collection en tant qu’entrées pour l’activité.  
  
### <a name="use-the-custom-activity-in-a-workflow"></a>Utiliser l'activité personnalisée dans un workflow  
  
1. Générez le projet en appuyant sur **Ctrl + Maj + B**.  
  
2. Dans **l’Explorateur de solutions**, ouvrez **Workflow1.xaml** dans le concepteur.  
  
3. Faites glisser un **MyForEach** activité à partir de la boîte à outils vers l’aire du concepteur. L'activité se trouve dans une section de la boîte à outils avec le même nom que le projet.  
  
4. Définir le **éléments** propriété de la **MyForEach** activité **new Object [] {1, « abc »}**.  
  
5. Faites glisser un <xref:System.Activities.Statements.WriteLine> activité à partir de la **Primitives** section de la boîte à outils vers le **Delegate : Body** section de la **MyForEach** activité.  
  
6. Définir le **texte** propriété de la <xref:System.Activities.Statements.WriteLine> activité **argument.ToString ()**.  
  
   Lorsque le workflow s'exécute, la console affiche ce qui suit :  
  
   **1**   
   **abc**