---
title: 'Le Concepteur de flux de travail - Comment : définir et utiliser des délégués d’activité'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
ms.assetid: c68e42ad-3ec0-4c2d-b104-fe36c6d83b5e
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 73bf61c845b0124a8350f61c161ded1cf0c80043
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31979566"
---
# <a name="how-to-define-and-consume-activity-delegates-in-the-workflow-designer"></a>Procédure : définir et utiliser des délégués d'activité dans le Concepteur de flux de travail

.NET framework 4.5 inclut un nouveau Concepteur d’out-of-box pour le <xref:System.Activities.Statements.InvokeDelegate> activité. Ce concepteur peut être utilisé pour assigner des délégués à l'activité qui dérive de <xref:System.Activities.ActivityDelegate>, telle que <xref:System.Activities.ActivityAction> ou <xref:System.Activities.ActivityFunc%601>.

## <a name="define-an-activity-delegate"></a>Définir un délégué d'activité

1.  Dans Visual Studio, sélectionnez **fichier**, **nouveau**, **projet**. Sélectionnez le **Workflow** nœud sur la gauche et le **Application Console de Workflow** modèle situé à droite. Nommez le projet (le cas échéant) et cliquez sur **Ok**.

2.  Avec le bouton droit sur le projet dans **l’Explorateur de solutions** et sélectionnez **ajouter**, **un nouvel élément...** . Sélectionnez le **Workflow** nœud sur la gauche et le **activité** modèle situé à droite. Nommez la nouvelle activité **MyForEach.xaml** et cliquez sur **Ok**. L'activité s'ouvre dans le concepteur de workflow.

3.  Dans le Concepteur de flux de travail, cliquez sur le **Arguments** onglet.

4.  Cliquez sur **créer un Argument**. Nommez le nouvel argument **éléments**.

5.  Dans le **type d’Argument** colonne, sélectionnez **tableau de [T]**.

6.  Dans l’Explorateur de types, sélectionnez **objet**. Click **Ok**.

7.  Cliquez sur **créer un Argument** à nouveau. Nommez le nouvel argument **corps**. Dans le **Direction** colonne pour le nouvel argument, sélectionnez **propriété**.

8.  Dans la colonne de Type d’Argument, sélectionnez **rechercher des types...**

9. Dans l’Explorateur de types, entrez **ActivityAction** dans les **nom de Type** champ. Sélectionnez **ActivityAction\<T >** dans l’arborescence. Sélectionnez **objet** dans le menu déroulant qui s’affiche pour affecter le type **ActivityAction\<objet >** à l’argument.

10. Faites glisser un <xref:System.Activities.Statements.While> activité à partir de la **flux de contrôle** section de la boîte à outils vers l’aire du concepteur.

11. Sélectionnez le <xref:System.Activities.Statements.While> activité, puis sélectionnez le **Variables** onglet.

12. Sélectionnez **créer la Variable**. Nommez la nouvelle variable **Index**.

13. Dans le **le type de Variable** colonne, sélectionnez **Int32**. Laissez le **étendue** en tant que **pendant**et le **par défaut** colonne vide.

14. Définir le **Condition** propriété de la <xref:System.Activities.Statements.While> activité **index < Items.Length ;**.

15. Faites glisser un <xref:System.Activities.Statements.InvokeDelegate> activité à partir de la **Primitives** section de la boîte à outils vers la **corps** de la <xref:System.Activities.Statements.While> activité.

16. Sélectionnez **corps** dans la liste déroulante délégué.

17. Dans le **propriétés** grille pour la <xref:System.Activities.Statements.InvokeDelegate> activité, cliquez sur le **...**  situé dans le **Arguments de délégué** propriété.

18. Dans le **valeur** colonne de l’argument nommé **Argument**, entrez **Items [Index]**. Cliquez sur **Ok** pour fermer la **DelegateArguments** boîte de dialogue.

19. Faites glisser une activité <xref:System.Activities.Statements.Assign> sur la ligne horizontale sous l'activité <xref:System.Activities.Statements.InvokeDelegate>. Le <xref:System.Activities.Statements.Assign> activité est créée et une <xref:System.Activities.Statements.Sequence> activité est créée automatiquement pour contenir les deux activités dans le **corps** section de la **MyForEach** activité. La séquence est nécessaire, car le **corps** section peut uniquement contenir une seule activité. Création automatique d’une nouvelle <xref:System.Activities.Statements.Sequence> activité est une nouveauté de .NET Framework 4.5.

20. Définir le **à** propriété de la <xref:System.Activities.Statements.Assign> activité **index**. Définir le **valeur** propriété de la **affecter** activité **index + 1**.

 Personnalisé **MyForEach** activité appelle maintenant une activité arbitraire une fois pour chaque valeur passée dans celle-ci via la **éléments** collection avec les valeurs de la collection comme entrées de l’activité.

## <a name="use-the-custom-activity-in-a-workflow"></a>Utiliser l'activité personnalisée dans un workflow

1.  Générez le projet en appuyant sur **Ctrl + Maj + B**.

2.  Dans **l’Explorateur de solutions**, ouvrez **Workflow1.xaml** dans le concepteur.

3.  Faites glisser un **MyForEach** activité à partir de la boîte à outils vers l’aire du concepteur. L'activité se trouve dans une section de la boîte à outils avec le même nom que le projet.

4.  Définir le **éléments** propriété de la **MyForEach** activité **new Object [] {1, « abc »}**.

5.  Faites glisser un <xref:System.Activities.Statements.WriteLine> activité à partir de la **Primitives** section de la boîte à outils vers la **Delegate : Body** section de la **MyForEach** activité.

6.  Définir le **texte** propriété de la <xref:System.Activities.Statements.WriteLine> activité **argument.ToString ()**.

Lorsque le flux de travail est exécutée, la console affiche les informations suivantes :

**1**
**abc**