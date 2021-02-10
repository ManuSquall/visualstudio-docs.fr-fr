---
title: Définir et consommer des délégués d’activité
description: Dans Concepteur de flux de travail, Découvrez comment .NET Framework 4,5 comprend un concepteur prêt à l’emploi pour l’activité InvokeDelegate que vous pouvez utiliser pour définir et utiliser des délégués d’activité.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: c68e42ad-3ec0-4c2d-b104-fe36c6d83b5e
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
author: TerryGLee
ms.openlocfilehash: 0ce9e59eec2cc9229a5f1104d79337b26115c92a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99971620"
---
# <a name="how-to-define-and-consume-activity-delegates-in-the-workflow-designer"></a>Procédure : définir et utiliser des délégués d'activité dans le Concepteur de flux de travail

.NET Framework 4,5 comprend un concepteur prêt à l’emploi pour l' <xref:System.Activities.Statements.InvokeDelegate> activité. Ce concepteur peut être utilisé pour assigner des délégués à l'activité qui dérive de <xref:System.Activities.ActivityDelegate>, telle que <xref:System.Activities.ActivityAction> ou <xref:System.Activities.ActivityFunc%601>.

## <a name="define-an-activity-delegate"></a>Définir un délégué d'activité

1. Créez un projet d' **application console de workflow** .

   > [!NOTE]
   > Si vous ne voyez pas les modèles de projet de **flux de travail** , installez d’abord le composant **Windows Workflow Foundation** de Visual Studio. Pour obtenir des instructions détaillées, consultez [installer Windows Workflow Foundation](developing-applications-with-the-workflow-designer.md#install-windows-workflow-foundation).

3. Dans **Explorateur de solutions** , cliquez avec le bouton droit sur le projet, puis sélectionnez **Ajouter**  >  **un nouvel élément**. Sélectionnez la catégorie **flux de travail** , puis sélectionnez le modèle élément d' **activité** . Nommez la nouvelle activité **MyForEach. Xaml** , puis sélectionnez **OK**.

   L’activité s’ouvre dans le concepteur de flux de travail.

4. Dans l’Concepteur de flux de travail, cliquez sur l’onglet **arguments** .

5. Cliquez sur **Créer un argument**. Nommez les nouveaux arguments **Items**.

6. Dans la colonne **type d’argument** , sélectionnez **tableau de [T]**.

7. Dans l’Explorateur de types, sélectionnez **objet** , puis cliquez sur **OK**.

8. Cliquez de nouveau sur **créer un argument** . Nommez le nouveau **corps** de l’argument. Dans la colonne **direction** du nouvel argument, sélectionnez **propriété**.

9. Dans la colonne type d’argument, sélectionnez **Parcourir les types**

10. Dans l’Explorateur de types, entrez **ActivityAction** dans le champ **nom du type** . Sélectionnez **ActivityAction \<T>** dans l’arborescence. Sélectionnez **objet** dans la liste déroulante qui s’affiche pour affecter le type **ActivityAction \<Object>** à l’argument.

11. Faites glisser une <xref:System.Activities.Statements.While> activité de la section **Control Flow** de la boîte à outils vers l’aire du concepteur.

12. Sélectionnez l' <xref:System.Activities.Statements.While> activité, puis sélectionnez l’onglet **variables** .

13. Sélectionnez **créer une variable**. Nommez le nouvel **index** de variable.

14. Dans la colonne **type de variable** , sélectionnez **Int32**. Laissez l' **étendue** en tant **que while** et la colonne **par défaut** vide.

15. Affectez à la propriété **condition** de l’activité la valeur <xref:System.Activities.Statements.While> **index < Items. Length ;**.

16. Faites glisser une <xref:System.Activities.Statements.InvokeDelegate> activité de la section **primitives** de la boîte à outils vers le **corps** de l' <xref:System.Activities.Statements.While> activité.

17. Sélectionnez **Body** dans la liste déroulante du délégué.

18. Dans la grille des **Propriétés** de l' <xref:System.Activities.Statements.InvokeDelegate> activité, cliquez sur le bouton **...** dans la propriété **arguments délégués** .

19. Dans la colonne **valeur** de l' **argument nommé argument**, entrez **Items [index]**. Cliquez sur **OK** pour fermer la boîte de dialogue **DelegateArguments** .

20. Faites glisser une activité <xref:System.Activities.Statements.Assign> sur la ligne horizontale sous l'activité <xref:System.Activities.Statements.InvokeDelegate>. L'  <xref:System.Activities.Statements.Assign> activité est créée, et une <xref:System.Activities.Statements.Sequence> activité est créée automatiquement pour contenir les deux activités dans la section **Body** de l’activité **MyForEach** . La séquence est nécessaire, car la section du **corps** ne peut contenir qu’une seule activité. La création automatique d’une nouvelle <xref:System.Activities.Statements.Sequence> activité est une nouvelle fonctionnalité de .NET Framework 4,5.

21. Affectez la valeur index à la propriété **to** de l' <xref:System.Activities.Statements.Assign> activité.  Affectez à la propriété **value** de l’activité **Assign** la valeur **index + 1**.

    L’activité **MyForEach** personnalisée appelle une activité arbitraire une fois pour chaque valeur qui lui est transmise via la collection **Items** , avec les valeurs de la collection comme entrées de l’activité.

## <a name="use-the-custom-activity-in-a-workflow"></a>Utiliser l'activité personnalisée dans un workflow

1. Générez le projet en appuyant sur **CTRL** + **MAJ** + **B**.

2. Dans **Explorateur de solutions**, ouvrez **Workflow1. Xaml** dans le concepteur.

3. Faites glisser une activité **MyForEach** de la boîte à outils vers l’aire du concepteur. L’activité se trouve dans une section de la boîte à outils portant le même nom que le projet.

4. Affectez la valeur **New Object [] {1, "ABC"}** à la propriété **Items** de l’activité **MyForEach** .

5. Faites glisser une <xref:System.Activities.Statements.WriteLine> activité de la section **primitives** de la boîte à outils vers la section **delegate : Body** de l’activité **MyForEach** .

6. Affectez à la propriété **Text** de l’activité la valeur <xref:System.Activities.Statements.WriteLine> **argument. ToString ()**.

Lorsque le flux de travail est exécuté, la console affiche la sortie suivante :

**1** 
 **ABC**
