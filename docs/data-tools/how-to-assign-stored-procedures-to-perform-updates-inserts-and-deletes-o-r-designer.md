---
title: "Proc&#233;dure&#160;: assigner des proc&#233;dures stock&#233;es pour effectuer des mises &#224; jour, des insertions et des suppressions (Concepteur O/R) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e88224ab-ff61-4a3a-b6b8-6f3694546cac
caps.latest.revision: 2
caps.handback.revision: 2
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Proc&#233;dure&#160;: assigner des proc&#233;dures stock&#233;es pour effectuer des mises &#224; jour, des insertions et des suppressions (Concepteur O/R)
Les procédures stockées peuvent être ajoutées au Concepteur O\/R et être exécutées comme méthodes <xref:System.Data.Linq.DataContext> typiques.Elles peuvent également être utilisées pour substituer le comportement au moment de l'exécution par défaut de [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] qui effectue des insertions, des mises à jour et des suppressions lorsque les modifications sont enregistrées à partir de classes d'entité dans une base de données \(par exemple, lors de l'appel de la méthode <xref:System.Data.Linq.DataContext.SubmitChanges%2A> \).  
  
> [!NOTE]
>  Si votre procédure stockée retourne des valeurs qui doivent être renvoyées au client \(par exemple, les valeurs sont calculées dans la procédure stockée\), créez des paramètres de sortie dans vos procédures stockées.Si vous ne pouvez pas utiliser de paramètres de sortie, écrivez une implémentation de méthode partielle au lieu de vous fier aux substitutions générées par le Concepteur O\/R.Les membres mappés aux valeurs générées par base de données doivent avoir les valeurs appropriées lorsque les opérations INSERT ou UPDATE se sont correctement achevées.Pour plus d'informations, consultez [Responsabilités du développeur en matière de substitution du comportement par défaut](../Topic/Responsibilities%20of%20the%20Developer%20In%20Overriding%20Default%20Behavior.md).  
  
> [!NOTE]
>  [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] gère automatiquement les valeurs générées par une base de données pour les colonnes identity \(incrémentation automatique\), rowguidcol \(GUID généré par la base de données\) et timestamp.Les valeurs générées par une base de données dans les autres types de colonne entraînent une valeur null de manière inopinée.Pour retourner les valeurs générées par une base de données, vous devez affecter la valeur `true` à <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> et l'une des valeurs suivantes à <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A> : <xref:System.Data.Linq.Mapping.AutoSync>, <xref:System.Data.Linq.Mapping.AutoSync> ou <xref:System.Data.Linq.Mapping.AutoSync>.  
  
## Configuration du comportement de mise à jour d'une classe d'entité  
 Par défaut, la logique de mise à jour d'une base de données \(insertions, mises à jour et suppressions\) avec les modifications apportées aux données dans les classes de l'entité [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] est fournie par le runtime [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)].Le runtime crée les instructions par défaut, \(insertion, mise à jour et suppression\) basées sur le schéma de la table \(les définitions de colonne et les informations de clé primaire\).Si vous ne souhaitez pas utiliser le comportement par défaut, vous pouvez configurer le comportement de mise à jour et désigner des procédures stockées spécifiques pour exécuter les instructions d'insertion, de mise à jour et de suppression nécessaires à la gestion des données de votre table. Vous pouvez également le faire lorsque le comportement par défaut n'est pas généré, par exemple lorsque vos classes d'entité mappent aux vues.En outre, vous pouvez substituer le comportement de mise à jour par défaut lorsque la base de données nécessite un accès aux tables à l'aide de procédures stockées.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### Pour assigner des procédures stockées afin de substituer le comportement par défaut d'une classe d'entité  
  
1.  Ouvrez le fichier **LINQ to SQL** dans le concepteur.\(Double\-cliquez sur le fichier .dbml dans l'**Explorateur de solutions**.\)  
  
2.  Dans l'**Explorateur de serveurs**\/**Explorateur de bases de données**, développez **Procédures stockées** et localisez les procédures stockées à utiliser pour l'insertion, la mise à jour et\/ou la suppression de la classe d'entité.  
  
3.  Faites glisser la procédure stockée vers le Concepteur O\/R.  
  
     La procédure stockée est ajoutée au volet de méthodes comme méthode <xref:System.Data.Linq.DataContext>.Pour plus d'informations, consultez [Méthodes DataContext \(Concepteur O\/R\)](../data-tools/datacontext-methods-o-r-designer.md).  
  
4.  Sélectionnez la classe d'entité pour laquelle vous souhaitez utiliser la procédure stockée afin d'effectuer des mises à jour.  
  
5.  Dans la fenêtre **Propriétés**, sélectionnez la commande à substituer \(**Insert**, **Update** ou **Delete**\).  
  
6.  Cliquez sur les points de suspension \(…\) à côté de l'option **Utiliser le runtime** pour ouvrir la boîte de dialogue **Configurer le comportement**.  
  
7.  Sélectionnez **Personnaliser**.  
  
8.  Sélectionnez la procédure stockée requise dans la liste **Personnaliser**.  
  
9. Inspectez la liste d'**Arguments de méthode** et de **Propriétés de classe** pour vérifier que les **Arguments de méthode** mappent aux **Propriétés de classe** appropriées.Mappez les arguments de méthode d'origine \(Original\_*ArgumentName*\) aux propriétés d'origine \(*PropertyName* \(Original\)\) pour les commandes de mise à jour et de suppression.  
  
    > [!NOTE]
    >  Par défaut, les arguments de méthode sont mappés à des propriétés de classe lorsque les noms correspondent.Si les noms de propriété ont été modifiés et ne correspondent plus entre la table et la classe d'entité, vous devrez peut\-être sélectionner la propriété de classe équivalente à mapper si le Concepteur O\/R ne peut pas déterminer le mappage correct.  
  
10. Cliquez sur **OK** ou **Appliquer**.  
  
    > [!NOTE]
    >  Vous pouvez continuer à configurer le comportement de chaque combinaison classe\/comportement tant que vous cliquez sur **Appliquer** après chaque modification.Si vous modifiez la classe ou le comportement avant de cliquer sur **Appliquer**, une boîte de dialogue d'avertissement s'affiche pour vous donner la possibilité d'appliquer toutes les modifications.  
  
     Pour rétablir l'utilisation de la logique runtime par défaut pour les mises à jour, cliquez sur les points de suspension à côté de la commande Insert, Update ou Delete dans la fenêtre **Propriétés**, puis sélectionnez **Utiliser le runtime** dans la boîte de dialogue **Configurer le comportement**.  
  
## Voir aussi  
 [Concepteur Objet\/Relationnel \(Concepteur O\/R\)](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [Méthodes DataContext \(Concepteur O\/R\)](../data-tools/datacontext-methods-o-r-designer.md)   
 [Procédure pas à pas : création de classes LINQ to SQL \(Concepteur O\/R\)](../Topic/Walkthrough:%20Creating%20LINQ%20to%20SQL%20Classes%20\(O-R%20Designer\).md)   
 [Procédure pas à pas : création de procédures stockées de mise à jour pour la table Customers de Northwind](../data-tools/walkthrough-creating-update-stored-procedures-for-the-northwind-customers-table.md)   
 [LINQ à SQL](../Topic/LINQ%20to%20SQL.md)   
 [Opérations d'insertion, de mise à jour et de suppression](../Topic/Insert,%20Update,%20and%20Delete%20Operations.md)