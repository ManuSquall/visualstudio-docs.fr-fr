---
title: 'Comment : définir et consommer des délégués d’activité dans le Concepteur de flux de travail | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: c68e42ad-3ec0-4c2d-b104-fe36c6d83b5e
caps.latest.revision: 3
author: steved0x
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 26ba92a2ba7aa6eed471383c875104549e896804
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72603855"
---
# <a name="how-to-define-and-consume-activity-delegates-in-the-workflow-designer"></a>Procédure : définir et utiliser des délégués d'activité dans le Concepteur de flux de travail
[!INCLUDE[net_v45](../includes/net-v45-md.md)] inclut un nouveau concepteur prêt à l'emploi pour l'activité <xref:System.Activities.Statements.InvokeDelegate>. Ce concepteur peut être utilisé pour assigner des délégués à l'activité qui dérive de <xref:System.Activities.ActivityDelegate>, telle que <xref:System.Activities.ActivityAction> ou <xref:System.Activities.ActivityFunc%601>.

### <a name="define-an-activity-delegate"></a>Définir un délégué d'activité

1. Dans [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)], sélectionnez **fichier**, **nouveau**, **projet**. Sélectionnez le nœud **Workflow** à gauche, puis le modèle **application console de workflow** à droite. Nommez le projet (si vous le souhaitez), puis cliquez sur **OK**.

2. Dans **Explorateur de solutions** , cliquez avec le bouton droit sur le projet, puis sélectionnez **Ajouter**, **nouvel élément...** . Sélectionnez le nœud **flux de travail** sur la gauche, puis le modèle **activité** à droite. Nommez la nouvelle activité **MyForEach. Xaml** , puis cliquez sur **OK**. L'activité s'ouvre dans le concepteur de workflow.

3. Dans le concepteur de flux de travail, cliquez sur l’onglet **arguments** .

4. Cliquez sur **créer un argument**. Nommez les nouveaux arguments **Items**.

5. Dans la colonne **type d’argument** , sélectionnez **tableau de [T]** .

6. Dans l’Explorateur de types, sélectionnez **objet**. Cliquez sur **OK**.

7. Cliquez de nouveau sur **créer un argument** . Nommez le nouveau **corps**de l’argument. Dans la colonne **direction** du nouvel argument, sélectionnez **propriété**.

8. Dans la colonne type d’argument, sélectionnez **Rechercher les types...**

9. Dans l’Explorateur de types, entrez **ActivityAction** dans le champ **nom du type** . Sélectionnez **ActivityAction \<T >** dans l’arborescence. Sélectionnez **objet** dans la liste déroulante qui s’affiche pour affecter le type **ActivityAction \<Object >** à l’argument.

10. Faites glisser une activité <xref:System.Activities.Statements.While> de la section **Flow** de la boîte à outils vers l’aire du concepteur.

11. Sélectionnez l’activité <xref:System.Activities.Statements.While>, puis sélectionnez l’onglet **variables** .

12. Sélectionnez **créer une variable**. Nommez le nouvel **index**de variable.

13. Dans la colonne **type de variable** , sélectionnez **Int32**. Laissez l' **étendue** en tant **que while**et la colonne **par défaut** vide.

14. Affectez à la propriété **condition** de l’activité <xref:System.Activities.Statements.While> la valeur **index < Items. Length ;** .

15. Faites glisser une activité <xref:System.Activities.Statements.InvokeDelegate> de la section **primitives** de la boîte à outils vers le **corps** de l’activité <xref:System.Activities.Statements.While>.

16. Sélectionnez **Body** dans la liste déroulante du délégué.

17. Dans la grille des **Propriétés** de l’activité <xref:System.Activities.Statements.InvokeDelegate>, cliquez sur **...** dans la propriété **arguments délégués** .

18. Dans la colonne **valeur** de l' **argument nommé argument**, entrez **Items [index]** . Cliquez sur **OK** pour fermer la boîte de dialogue **DelegateArguments** .

19. Faites glisser une activité <xref:System.Activities.Statements.Assign> sur la ligne horizontale sous l'activité <xref:System.Activities.Statements.InvokeDelegate>. L’activité <xref:System.Activities.Statements.Assign> est créée, et une activité de <xref:System.Activities.Statements.Sequence> est créée automatiquement pour contenir les deux activités dans la section **Body** de l’activité **MyForEach** . La séquence est nécessaire, car la section du **corps** ne peut contenir qu’une seule activité. La fonctionnalité de création automatique d'une nouvelle activité <xref:System.Activities.Statements.Sequence> est une nouveauté du [!INCLUDE[net_v45](../includes/net-v45-md.md)].

20. Affectez la valeur **index**à la propriété **to** de l’activité <xref:System.Activities.Statements.Assign>. Affectez à la propriété **value** de l’activité **Assign** la valeur **index + 1**.

    L’activité **MyForEach** personnalisée appelle maintenant une activité arbitraire une fois pour chaque valeur qui lui est transmise via la collection **Items** , avec les valeurs de la collection comme entrées de l’activité.

### <a name="use-the-custom-activity-in-a-workflow"></a>Utiliser l'activité personnalisée dans un workflow

1. Générez le projet en appuyant sur **Ctrl + Maj + B**.

2. Dans **Explorateur de solutions**, ouvrez **Workflow1. Xaml** dans le concepteur.

3. Faites glisser une activité **MyForEach** de la boîte à outils vers l’aire du concepteur. L'activité se trouve dans une section de la boîte à outils avec le même nom que le projet.

4. Affectez la valeur **New Object [] {1, "ABC"}** à la propriété **Items** de l’activité **MyForEach** .

5. Faites glisser une activité <xref:System.Activities.Statements.WriteLine> de la section **primitives** de la boîte à outils vers la section **delegate : Body** de l’activité **MyForEach** .

6. Affectez à la propriété **Text** de l’activité <xref:System.Activities.Statements.WriteLine> la valeur **argument. ToString ()** .

   Lorsque le workflow s'exécute, la console affiche ce qui suit :

   **1** 
   **ABC**