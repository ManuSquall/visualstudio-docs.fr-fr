---
title: "Validation de donn&#233;es dans des groupes de donn&#233;es | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DataTable.ColumnChanging"
  - "System.Data.DataTable.ColumnChanging"
  - "System.Data.DataTable.RowChanging"
  - "DataTable.RowChanging"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "validation des données"
  - "validation des données, groupes de données"
  - "mise à jour de groupes de données, valider des données"
  - "valider des données, groupes de données"
ms.assetid: 79500596-1e4d-478e-a991-a636fd73a622
caps.latest.revision: 24
caps.handback.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Validation de donn&#233;es dans des groupes de donn&#233;es
La validation des données est le processus qui consiste à confirmer que les valeurs entrées dans des objets de données sont conformes aux contraintes contenues dans le schéma d'un groupe de données, ainsi qu'aux règles établies pour votre application.  Il peut être utile de valider les données avant d'envoyer des mises à jour à la base de données sous\-jacente afin de réduire les erreurs, ainsi que le nombre potentiel de boucles entre une application et la base de données.  Vous pouvez confirmer la validité des données écrites dans un groupe de données en créant des contrôles de validation dans le groupe de données lui\-même.  Le groupe de données peut vérifier les données, quelle que soit la méthode de mise à jour utilisée — directement à l'aide de contrôles dans un formulaire, dans un composant ou d'une autre manière.  Étant donné que le groupe de données fait partie de votre application, il représente un emplacement logique pour générer une validation propre à l'application \(ce qui évite d'effectuer les mêmes contrôles dans la base de données\).  
  
 L'emplacement suggéré pour l'ajout de la validation dans votre application est le fichier de classe partielle du groupe de données.  Dans [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] ou [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)], ouvrez le **Concepteur de DataSet** et double\-cliquez sur la colonne ou sur la table pour laquelle vous souhaitez créer la validation.  Cette action crée automatiquement un gestionnaire d'événements <xref:System.Data.DataTable.ColumnChanging> ou <xref:System.Data.DataTable.RowChanging>.  Pour plus d'informations, consultez [Comment : valider les données au cours des modifications de colonnes](../Topic/How%20to:%20Validate%20Data%20During%20Column%20Changes.md) ou [Comment : valider les données au cours des modifications de lignes](../Topic/How%20to:%20Validate%20Data%20During%20Row%20Changes.md).  Pour obtenir un exemple complet, consultez [Procédure pas à pas : ajout d'une validation à un groupe de données](../Topic/Walkthrough:%20Adding%20Validation%20to%20a%20Dataset.md).  
  
## Validation des données  
 Dans un groupe de données, la validation peut être effectuée :  
  
-   En créant votre validation propre à une application, capable de vérifier les données lors de la modification des valeurs dans une colonne de données individuelle.  Pour plus d'informations, consultez [Comment : valider les données au cours des modifications de colonnes](../Topic/How%20to:%20Validate%20Data%20During%20Column%20Changes.md).  
  
-   En créant votre validation propre à une application, capable de vérifier les données pendant la modification des valeurs alors que l'intégralité d'une ligne de données est modifiée.  Pour plus d'informations, consultez [Comment : valider les données au cours des modifications de lignes](../Topic/How%20to:%20Validate%20Data%20During%20Row%20Changes.md).  
  
-   En créant des clés, des contraintes uniques, etc. comme partie de la définition de schéma du groupe de données.  Pour plus d'informations sur l'incorporation de validation dans la définition de schéma, consultez [Pour contraindre une DataColumn à contenir des valeurs uniques](../Topic/How%20to:%20Add%20Columns%20to%20a%20DataTable.md#SpecifyUniqueConstraint).  
  
-   En définissant les propriétés de l'objet <xref:System.Data.DataColumn>, telles que <xref:System.Data.DataColumn.MaxLength%2A>, <xref:System.Data.DataColumn.AllowDBNull%2A> et <xref:System.Data.DataColumn.Unique%2A>.  
  
 Lorsqu'une modification est apportée à un enregistrement, plusieurs événements sont déclenchés par l'objet <xref:System.Data.DataTable> :  
  
-   Les événements <xref:System.Data.DataTable.ColumnChanging> et <xref:System.Data.DataTable.ColumnChanged> sont déclenchés pendant et après chaque modification d'une colonne individuelle.  L'événement <xref:System.Data.DataTable.ColumnChanging> est utile lorsque vous souhaitez valider les modifications dans des colonnes particulières.  Les informations relatives à la modification proposée sont passées comme argument avec l'événement.  Pour plus d'informations, consultez [Comment : valider les données au cours des modifications de colonnes](../Topic/How%20to:%20Validate%20Data%20During%20Column%20Changes.md).  
  
-   Les événements <xref:System.Data.DataTable.RowChanging> et <xref:System.Data.DataTable.RowChanged> sont déclenchés pendant et après chaque modification d'une ligne.  L'événement <xref:System.Data.DataTable.RowChanging> est un événement plus général. Il indique simplement qu'une modification est en cours dans la ligne, sans spécifier la colonne concernée.  Pour plus d'informations, consultez [Comment : valider les données au cours des modifications de lignes](../Topic/How%20to:%20Validate%20Data%20During%20Row%20Changes.md).  
  
 Par défaut, chaque modification de colonne déclenche donc quatre événements : les événements <xref:System.Data.DataTable.ColumnChanging> et <xref:System.Data.DataTable.ColumnChanged> pour la colonne particulière en cours de modification, puis les événements <xref:System.Data.DataTable.RowChanging> et <xref:System.Data.DataTable.RowChanged>.  Les événements sont déclenchés pour chacune des modifications apportées à la ligne.  
  
> [!NOTE]
>  La méthode <xref:System.Data.DataRow.BeginEdit%2A> de la ligne de données désactive les événements <xref:System.Data.DataTable.RowChanging> et <xref:System.Data.DataTable.RowChanged> après chaque modification d'une colonne individuelle.  Dans ce cas, l'événement n'est pas déclenché tant que la méthode <xref:System.Data.DataRow.EndEdit%2A> n'a pas été appelée, après quoi les événements <xref:System.Data.DataTable.RowChanging> et <xref:System.Data.DataTable.RowChanged> ne sont déclenchés qu'une fois.  Pour plus d'informations, consultez [Comment : désactiver les contraintes pendant le remplissage d'un groupe de données](../data-tools/turn-off-constraints-while-filling-a-dataset.md).  
  
 L'événement que vous choisissez dépend du niveau de granularité souhaité de l'application.  S'il vous faut intercepter une erreur dès qu'une colonne est modifiée, générez la validation en utilisant l'événement <xref:System.Data.DataTable.ColumnChanging>.  Sinon, utilisez l'événement <xref:System.Data.DataTable.RowChanging>, qui peut provoquer l'interception de plusieurs erreurs en même temps.  En outre, si vos données sont structurées de telle sorte que la validation de la valeur d'une colonne dépend du contenu d'une autre colonne, vous devez effectuer votre validation pendant un événement <xref:System.Data.DataTable.RowChanging>.  
  
 Lorsque des enregistrements sont mis à jour, l'objet <xref:System.Data.DataTable> déclenche des événements auxquels vous pouvez répondre pendant et après la réalisation des modifications.  
  
 Si votre application utilise un groupe de données typé, vous pouvez créer des gestionnaires d'événements fortement typés.  Cela entraîne l'ajout de quatre événements typés supplémentaires pour lesquels vous pouvez créer des gestionnaires : `dataTableNameRowChanging`, `dataTableNameRowChanged`, `dataTableNameRowDeleting` et `dataTableNameRowDeleted`.  Ces gestionnaires d'événements typés passent un argument comprenant les noms de colonne de votre table, ce qui facilite l'écriture et la lecture du code.  
  
## Événements de mise à jour de données  
  
|Événement|Description|  
|---------------|-----------------|  
|<xref:System.Data.DataTable.ColumnChanging>|La valeur d'une colonne est en cours de modification.  L'événement vous passe la ligne et la colonne, ainsi que la nouvelle valeur proposée.|  
|<xref:System.Data.DataTable.ColumnChanged>|La valeur d'une colonne a été modifiée.  L'événement vous passe la ligne et la colonne, ainsi que la valeur proposée.|  
|<xref:System.Data.DataTable.RowChanging>|Les modifications apportées à un objet <xref:System.Data.DataRow> sont sur le point d'être validées dans le groupe de données.  Si vous n'avez pas appelé la méthode <xref:System.Data.DataRow.BeginEdit%2A>, l'événement <xref:System.Data.DataTable.RowChanging> est déclenché pour chaque modification d'une colonne, immédiatement après le déclenchement de l'événement <xref:System.Data.DataTable.ColumnChanging>.  Si vous avez appelé la méthode <xref:System.Data.DataRow.BeginEdit%2A> avant d'effectuer les modifications, l'événement <xref:System.Data.DataTable.RowChanging> n'est déclenché que lorsque vous appelez la méthode <xref:System.Data.DataRow.EndEdit%2A>.<br /><br /> L'événement vous passe la ligne avec une valeur indiquant le type d'action \(modification, insertion, etc.\) en cours de réalisation.|  
|<xref:System.Data.DataTable.RowChanged>|Une ligne a été modifiée.  L'événement vous passe la ligne avec une valeur indiquant le type d'action \(modification, insertion, etc.\) en cours de réalisation.|  
|<xref:System.Data.DataTable.RowDeleting>|Une ligne est en cours de suppression.  L'événement vous passe la ligne avec une valeur indiquant le type d'action \(suppression\) en cours de réalisation.|  
|<xref:System.Data.DataTable.RowDeleted>|Une ligne a été supprimée.  L'événement vous passe la ligne avec une valeur indiquant le type d'action \(suppression\) en cours de réalisation.|  
  
 Les événements <xref:System.Data.DataTable.ColumnChanging>, <xref:System.Data.DataTable.RowChanging> et <xref:System.Data.DataTable.RowDeleting> sont déclenchés pendant la procédure de mise à jour.  Vous pouvez les utiliser pour valider des données ou effectuer d'autres types de traitement.  Les mises à jour étant effectuées pendant ces événements, vous pouvez annuler la mise à jour en levant une exception, ce qui interrompt les modifications.  
  
 Les événements <xref:System.Data.DataTable.ColumnChanged>, <xref:System.Data.DataTable.RowChanged> et <xref:System.Data.DataTable.RowDeleted> sont des événements de notification qui sont déclenchés lorsque la mise à jour a été effectuée correctement.  Ils vous permettent de réaliser d'autres actions à partir d'une mise à jour réussie.  
  
## Voir aussi  
 [Création et modification de Datasets typés](../data-tools/creating-and-editing-typed-datasets.md)   
 [Comment : établir une connexion à des données d'une base de données](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [Comment : valider des données dans le contrôle DataGridView Windows Forms](../Topic/How%20to:%20Validate%20Data%20in%20the%20Windows%20Forms%20DataGridView%20Control.md)   
 [Comment : afficher des icônes d'erreur pour la validation de formulaire à l'aide du composant ErrorProvider Windows Forms](../Topic/How%20to:%20Display%20Error%20Icons%20for%20Form%20Validation%20with%20the%20Windows%20Forms%20ErrorProvider%20Component.md)