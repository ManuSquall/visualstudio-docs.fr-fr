---
title: "Proc&#233;dure&#160;: d&#233;finir et utiliser des d&#233;l&#233;gu&#233;s d&#39;activit&#233; dans le Concepteur de flux de travail | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: c68e42ad-3ec0-4c2d-b104-fe36c6d83b5e
caps.latest.revision: 3
ms.author: "sdanie"
manager: "erikre"
caps.handback.revision: 3
---
# Proc&#233;dure&#160;: d&#233;finir et utiliser des d&#233;l&#233;gu&#233;s d&#39;activit&#233; dans le Concepteur de flux de travail
[!INCLUDE[net_v45](../ide/includes/net_v45_md.md)] inclut un nouveau concepteur de zone prêt à l'emploi pour l'activité <xref:System.Activities.Statements.InvokeDelegate>.Ce concepteur peut être utilisé pour assigner des délégués à l'activité qui dérive de <xref:System.Activities.ActivityDelegate>, telle que <xref:System.Activities.ActivityAction> ou <xref:System.Activities.ActivityFunc%601>.  
  
### Définir un délégué d'activité  
  
1.  Dans [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)], sélectionnez **Fichier**, **Nouveau**, **Projet**.Sélectionnez le nœud **Workflow** à gauche, et le modèle **Application console de workflow** à droite.Nommez le projet \(le cas échéant\) et cliquez sur **OK**.  
  
2.  Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur le projet, puis sélectionnez **Ajouter**, **Nouvel élément...**.Sélectionnez le nœud **Workflow** à gauche, et le modèle **Activité** à droite.Nommez la nouvelle activité **MyForEach.xaml** et cliquez sur **OK**.L'activité s'ouvre dans le concepteur de workflow.  
  
3.  Dans le concepteur de workflow, cliquez sur l'onglet **Arguments**.  
  
4.  Cliquez sur **Créer un argument**.Nommez le nouvel argument **Éléments**.  
  
5.  Dans la colonne **Type d'argument**, sélectionnez **Tableau de \[T\]**.  
  
6.  Dans l'Explorateur de types, sélectionnez **Objet**.Cliquez sur **Ok**.  
  
7.  Cliquez de nouveau sur **Créer un argument**.Nommez le nouvel argument **corps**.Dans la colonne **Direction** pour le nouvel argument, sélectionnez **Propriété**.  
  
8.  Dans la colonne Type d'argument, sélectionnez **Rechercher des types…**  
  
9. Dans l'Explorateur de types, entrez **ActivityAction** dans le champ **Nom de type**.Sélectionnez **ActivityAction\<T\>** dans l'arborescence.Sélectionnez **Objet** dans le menu déroulant qui s'affiche pour affecter le type **ActivityAction\<Object\>** à l'argument.  
  
10. Faites glisser une activité <xref:System.Activities.Statements.While> de la section **Flux de contrôle** de la boîte à outils vers l'aire du concepteur.  
  
11. Sélectionnez l'activité <xref:System.Activities.Statements.While> et cliquez sur l'onglet **Variables**.  
  
12. Sélectionnez **Créer une variable**.Nommez la nouvelle variable **Index**.  
  
13. Dans la colonne **Type de variable**, sélectionnez **Int32**.Conservez **Portée** comme **While**, et la colonne **Par défaut** vide.  
  
14. Affectez la valeur **index \< Items.Length;** à la propriété **Condition** de l'activité <xref:System.Activities.Statements.While>.  
  
15. Faites glisser une activité <xref:System.Activities.Statements.InvokeDelegate> de la section **Primitives** de la boîte à outils vers la section **Body** de l'activité <xref:System.Activities.Statements.While> .  
  
16. Sélectionnez **Body** dans la liste déroulante de délégué.  
  
17. Dans la grille **Propriétés** pour l'activité <xref:System.Activities.Statements.InvokeDelegate>, cliquez sur le bouton **…** dans la propriété **Delegate Arguments**.  
  
18. Dans la colonne **Valeur** de l'argument nommé **Argument**, entrez **Items\[Index\]**.Cliquez sur **OK** pour fermer la boîte de dialogue **DelegateArguments**.  
  
19. Faites glisser une activité <xref:System.Activities.Statements.Assign> sur la ligne horizontale sous l'activité <xref:System.Activities.Statements.InvokeDelegate>.L'activité <xref:System.Activities.Statements.Assign> est créée, et une activité <xref:System.Activities.Statements.Sequence> est créée automatiquement pour contenir les deux activités dans la section **Body** de l'activité **MyForEach**.La séquence est nécessaire dans la mesure où la section **Body** ne peut contenir qu'une seule activité.La fonctionnalité de création automatique d'une nouvelle activité <xref:System.Activities.Statements.Sequence> est une nouveauté du [!INCLUDE[net_v45](../ide/includes/net_v45_md.md)].  
  
20. Affectez la valeur **index** à la propriété **À** de l'activité <xref:System.Activities.Statements.Assign>.Affectez la valeur **index\+1** à la propriété **Valeur** de l'activité **Assign**.  
  
 L'activité personnalisée **MyForEach** appelle maintenant une activité arbitraire une fois pour chaque valeur passée dans celle\-ci via la collection **Items**, avec les valeurs de la collection comme entrées de l'activité.  
  
### Utiliser l'activité personnalisée dans un workflow  
  
1.  Générez le projet en appuyant sur **Ctrl\+Maj\+B**.  
  
2.  Dans l'**Explorateur de solutions**, ouvrez **Workflow1.xaml** dans le concepteur.  
  
3.  Faites glisser une activité **MyForEach** de la boîte à outils jusqu'à l'aire du concepteur.L'activité se trouve dans une section de la boîte à outils avec le même nom que le projet.  
  
4.  Définissez la propriété **Éléments** de l'activité **MyForEach** à **new Object\[\] {1, « abc »}**.  
  
5.  Faites glisser une activité <xref:System.Activities.Statements.WriteLine> de la section **Primitives** de la boîte à outils vers la section **Delegate:Body** de l'activité **MyForEach**.  
  
6.  Définissez la propriété **Texte** de l'activité <xref:System.Activities.Statements.WriteLine> à **Argument.ToString\(\)**.  
  
 Lorsque le workflow s'exécute, la console affiche ce qui suit :  
  
 **1**   
**abc**