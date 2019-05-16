---
title: Valider des données dans les jeux de données | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
f1_keywords:
- DataTable.ColumnChanging
- System.Data.DataTable.ColumnChanging
- System.Data.DataTable.RowChanging
- DataTable.RowChanging
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data validation, datasets
- data validation
- validating data, datasets
- updating datasets, validating data
ms.assetid: 79500596-1e4d-478e-a991-a636fd73a622
caps.latest.revision: 27
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 2a6993d241f49261131ffad76dc50534ac8e1591
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65694879"
---
# <a name="validate-data-in-datasets"></a>Valider les données dans des datasets
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Validation des données est le processus consistant à confirmer que les valeurs entrées dans des objets de données sont conformes aux contraintes de schéma d’un jeu de données. Le processus de validation vérifie également que ces valeurs sont les suivantes les règles qui ont été établies pour votre application. Il est conseillé de valider les données avant d’envoyer des mises à jour la base de données sous-jacente. Cela réduit les erreurs, ainsi que le nombre potentiel d’allers-retours entre une application et la base de données.  
  
 Vous pouvez vérifier que les données sont écrites dans un jeu de données sont valides en créant des contrôles de validation dans le jeu de données. Le jeu de données peut vérifier les données quelle que soit la façon dont la mise à jour est effectuée, que ce soit directement par les contrôles dans un formulaire, au sein d’un composant, ou par d’autres moyens. Étant donné que le jeu de données fait partie de votre application (contrairement à la base de données principale), il est un emplacement logique pour générer une validation spécifique à l’application.  
  
 Le meilleur endroit pour ajouter une validation à votre application est dans un fichier de classe partielle du jeu de données. Dans [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ou [!INCLUDE[csprcs](../includes/csprcs-md.md)], ouvrez le **Concepteur de Dataset** et double-cliquez sur la colonne ou la table pour laquelle vous souhaitez créer la validation. Cette action crée automatiquement un <xref:System.Data.DataTable.ColumnChanging> ou <xref:System.Data.DataTable.RowChanging> Gestionnaire d’événements. Pour plus d'informations, voir [Procédure : Valider les données lors de la modification de colonne](https://msdn.microsoft.com/library/a2680600-67b6-4a40-a77e-b5bc638281c5) ou [Comment : Valider les données lors de la modification de la ligne](https://msdn.microsoft.com/library/afc03c77-dfed-4302-9376-929400468ecc). Pour obtenir un exemple complet, consultez [procédure pas à pas : Ajout d’une Validation à un Dataset](https://msdn.microsoft.com/library/09351fab-d670-45e3-b53a-a944eff717e7).  
  
## <a name="validate-data"></a>Valider des données  
 Validation au sein d’un jeu de données est possible de plusieurs manières :  
  
- En créant votre propre validation spécifique à l’application qui peut vérifier les valeurs dans une colonne de données lors de la modification.  Pour plus d'informations, voir [Procédure : Valider les données lors de la modification de la colonne](https://msdn.microsoft.com/library/a2680600-67b6-4a40-a77e-b5bc638281c5).  
  
- En créant votre propre validation spécifique à l’application peut vérifier les données aux valeurs un ensemble de données lors de la ligne change. Pour plus d'informations, voir [Procédure : Valider les données lors de la modification de la ligne](https://msdn.microsoft.com/library/afc03c77-dfed-4302-9376-929400468ecc).  
  
- En créant des clés, des contraintes uniques, et ainsi de suite dans le cadre de la définition de schéma du jeu de données. Pour plus d’informations sur l’incorporation de validation dans la définition de schéma, consultez [contraindre un DataColumn pour contenir des valeurs uniques](https://msdn.microsoft.com/library/8ca21f77-b99a-47a7-a656-7cfd7a1bd9df).  
  
- En définissant les propriétés de la <xref:System.Data.DataColumn> l’objet, tel que <xref:System.Data.DataColumn.MaxLength%2A>, <xref:System.Data.DataColumn.AllowDBNull%2A>, et <xref:System.Data.DataColumn.Unique%2A>.  
  
  Plusieurs événements sont déclenchés par le <xref:System.Data.DataTable> lorsqu’une modification est apportée à un enregistrement de l’objet :  
  
- Le <xref:System.Data.DataTable.ColumnChanging> et <xref:System.Data.DataTable.ColumnChanged> sont déclenchés pendant et après chaque modification apportée à une colonne individuelle. Le <xref:System.Data.DataTable.ColumnChanging> événement est utile lorsque vous souhaitez valider les modifications apportées dans des colonnes spécifiques. Plus d’informations sur la modification proposée sont passés en tant qu’argument à l’événement. Pour plus d'informations, voir [Procédure : Valider les données lors de la modification de la colonne](https://msdn.microsoft.com/library/a2680600-67b6-4a40-a77e-b5bc638281c5).  
  
- Le <xref:System.Data.DataTable.RowChanging> et <xref:System.Data.DataTable.RowChanged> sont déclenchés pendant et après chaque modification d’une ligne. Le <xref:System.Data.DataTable.RowChanging> événement est plus général. Il indique qu’une modification se produit quelque part dans la ligne, mais vous ne savez pas quelle colonne a changé. Pour plus d'informations, voir [Procédure : Valider les données lors de la modification de la ligne](https://msdn.microsoft.com/library/afc03c77-dfed-4302-9376-929400468ecc).  
  
  Par défaut, chaque modification apportée à une colonne déclenche donc quatre événements. La première est la <xref:System.Data.DataTable.ColumnChanging> et <xref:System.Data.DataTable.ColumnChanged> événements pour la colonne qui est en cours de modification. Viennent ensuite les <xref:System.Data.DataTable.RowChanging> et <xref:System.Data.DataTable.RowChanged> événements. Si plusieurs modifications sont en cours apportées à la ligne, les événements sont déclenchés pour chaque modification.  
  
> [!NOTE]
> La ligne de données <xref:System.Data.DataRow.BeginEdit%2A> méthode désactive le <xref:System.Data.DataTable.RowChanging> et <xref:System.Data.DataTable.RowChanged> événements après chaque modification de colonne individuelle. Dans ce cas, l’événement n’est pas déclenché jusqu'à ce que le <xref:System.Data.DataRow.EndEdit%2A> méthode a été appelée, lorsque le <xref:System.Data.DataTable.RowChanging> et <xref:System.Data.DataTable.RowChanged> sont déclenchés qu’une seule fois. Pour plus d’informations, consultez [désactiver les contraintes pendant le remplissage d’un jeu de données](../data-tools/turn-off-constraints-while-filling-a-dataset.md).  
  
 L’événement que vous choisissez dépend du degré de granularité que vous souhaitez la validation. S’il est important que vous interceptez une erreur immédiatement lors d’une colonne change, validation de la génération à l’aide de la <xref:System.Data.DataTable.ColumnChanging> événement. Sinon, utilisez le <xref:System.Data.DataTable.RowChanging> événement, ce qui peut entraîner l’interception de plusieurs erreurs en même temps. En outre, si vos données sont structurées de sorte que la valeur d’une colonne est validée en fonction du contenu d’une autre colonne, puis effectuer votre validation pendant la <xref:System.Data.DataTable.RowChanging> événement.  
  
 Lorsque les enregistrements sont mis à jour, le <xref:System.Data.DataTable> objet déclenche des événements que vous pouvez répondre aux modifications se produisent et lorsque des modifications sont apportées.  
  
 Si votre application utilise un dataset typé, vous pouvez créer des gestionnaires d’événements fortement typés. Cette opération ajoute quatre événements typés supplémentaires que vous pouvez créer des gestionnaires pour : `dataTableNameRowChanging`, `dataTableNameRowChanged`, `dataTableNameRowDeleting`, et `dataTableNameRowDeleted`. Ces gestionnaires d’événements typés passent un argument qui inclut les noms de colonnes de votre table qui facilitent le code écrire et lire.  
  
## <a name="data-update-events"></a>Événements de mise à jour de données  
  
|Événement|Description|  
|-----------|-----------------|  
|<xref:System.Data.DataTable.ColumnChanging>|La valeur dans une colonne est en cours de modification. L’événement passe la ligne et colonne, ainsi que la nouvelle valeur proposée.|  
|<xref:System.Data.DataTable.ColumnChanged>|La valeur dans une colonne a été modifiée. L’événement passe la ligne et colonne, ainsi que la valeur proposée.|  
|<xref:System.Data.DataTable.RowChanging>|Les modifications qui ont été apportées à un <xref:System.Data.DataRow> objet sont sur le point d’être validées dans le jeu de données. Si vous n’avez pas appelé la <xref:System.Data.DataRow.BeginEdit%2A> (méthode), le <xref:System.Data.DataTable.RowChanging> événement est déclenché pour chaque modification apportée à une colonne immédiatement après le <xref:System.Data.DataTable.ColumnChanging> événement a été déclenché. Si vous avez appelé <xref:System.Data.DataRow.BeginEdit%2A> avant d’apporter des modifications, la <xref:System.Data.DataTable.RowChanging> événement est déclenché uniquement lorsque vous appelez le <xref:System.Data.DataRow.EndEdit%2A> (méthode).<br /><br /> L’événement passe la ligne, ainsi qu’une valeur qui indique le type d’action (modification, insertion et ainsi de suite) est en cours d’exécution.|  
|<xref:System.Data.DataTable.RowChanged>|Une ligne a été modifiée. L’événement passe la ligne, ainsi qu’une valeur qui indique le type d’action (modification, insertion et ainsi de suite) est en cours d’exécution.|  
|<xref:System.Data.DataTable.RowDeleting>|Une ligne est en cours de suppression. L’événement passe la ligne, ainsi qu’une valeur qui indique le type d’action (delete) est en cours d’exécution.|  
|<xref:System.Data.DataTable.RowDeleted>|Une ligne a été supprimée. L’événement passe la ligne, ainsi qu’une valeur qui indique le type d’action (delete) est en cours d’exécution.|  
  
 Le <xref:System.Data.DataTable.ColumnChanging>, <xref:System.Data.DataTable.RowChanging>, et <xref:System.Data.DataTable.RowDeleting> événements sont déclenchés pendant le processus de mise à jour. Vous pouvez utiliser ces événements pour valider les données ou effectuer d’autres types de traitement. Étant donné que la mise à jour est en cours pendant ces événements, vous pouvez l’annuler en levant une exception, ce qui empêche la mise à jour à partir de finition.  
  
 Le <xref:System.Data.DataTable.ColumnChanged>, <xref:System.Data.DataTable.RowChanged> et <xref:System.Data.DataTable.RowDeleted> événements sont des événements de notification qui sont déclenchés lorsque la mise à jour est terminée avec succès. Ces événements sont utiles lorsque vous souhaitez effectuer d’autres actions selon une mise à jour réussie.  
  
## <a name="validate-data-during-column-changes"></a>Valider les données lors de la modification de colonne  
  
> [!NOTE]
> Le **Concepteur de Dataset** crée une classe partielle dans laquelle le contrôle logique peut être ajoutée à un jeu de données. Le jeu de données généré par le concepteur ne supprimer ou modifier le code dans la classe partielle.  
  
 Vous pouvez valider des données lorsque la valeur dans une colonne de données change en réponse à la <xref:System.Data.DataTable.ColumnChanging> événement. Lorsque déclenché, cet événement passe un argument d’événement (<xref:System.Data.DataColumnChangeEventArgs.ProposedValue%2A>) qui contient la valeur proposée pour la colonne actuelle. En fonction du contenu de `e.ProposedValue`, vous pouvez :  
  
- Acceptez la valeur proposée en ne rien faire.  
  
- Refuser la valeur proposée en définissant l’erreur de colonne (<xref:System.Data.DataRow.SetColumnError%2A>) à partir de gestionnaire d’événements de modification de colonne.  
  
- Vous pouvez également utiliser un <xref:System.Windows.Forms.ErrorProvider> contrôle pour afficher un message d’erreur à l’utilisateur. Pour plus d’informations, consultez [du composant ErrorProvider](https://msdn.microsoft.com/library/c0f2e231-c5c9-413d-a507-75af2db499b6).  
  
  La validation peut également être effectuée pendant la <xref:System.Data.DataTable.RowChanging> événement. Pour plus d'informations, voir [Procédure : Valider les données lors de la modification de la ligne](https://msdn.microsoft.com/library/afc03c77-dfed-4302-9376-929400468ecc).  
  
## <a name="validate-data-during-row-changes"></a>Valider les données lors de la modification de ligne  
 Vous pouvez écrire du code pour vérifier que chaque colonne que vous voulez valider contient des données qui répondent aux exigences de votre application. Cela en définissant la colonne pour indiquer qu’il contient une erreur si une valeur proposée est inacceptable. Les exemples suivants définissent une erreur de colonne lorsque la `Quantity` colonne est inférieur ou égal à 0. Les gestionnaires d’événements de modification de ligne doivent se présenter comme les exemples suivants.  
  
#### <a name="to-validate-data-when-a-row-changes-visual-basic"></a>Pour valider des données lorsqu’une ligne change (Visual Basic)  
  
1. Ouvrez votre dataset dans le **Concepteur de DataSet**. Pour plus d'informations, voir [Procédure : Ouvrir un jeu de données dans le Concepteur de Dataset](https://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).  
  
2. Double-cliquez sur la barre de titre de la table que vous souhaitez valider. Cette action crée automatiquement le <xref:System.Data.DataTable.RowChanging> Gestionnaire d’événements de la <xref:System.Data.DataTable> dans le fichier de classe partielle du jeu de données.  
  
    > [!TIP]
    > Double-cliquez sur à gauche du nom de table pour créer le Gestionnaire d’événements de modification de ligne. Si vous double-cliquez sur le nom de table, vous pouvez le modifier.  
  
     [!code-vb[VbRaddataValidating#3](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataValidating/VB/NorthwindDataSet.vb#3)]  
  
#### <a name="to-validate-data-when-a-row-changes-c"></a>Pour valider des données lorsqu’une ligne change (c#)  
  
1. Ouvrez votre dataset dans le **Concepteur de DataSet**. Pour plus d'informations, voir [Procédure : Ouvrir un jeu de données dans le Concepteur de Dataset](https://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).  
  
2. Double-cliquez sur la barre de titre de la table que vous souhaitez valider. Cette action crée un fichier de classe partielle pour le <xref:System.Data.DataTable>.  
  
    > [!NOTE]
    > Le **Concepteur de Dataset** ne crée pas automatiquement un gestionnaire d’événements pour le <xref:System.Data.DataTable.RowChanging> événement. Vous devez créer une méthode pour gérer la <xref:System.Data.DataTable.RowChanging> événements et exécuter du code pour raccorder l’événement dans la méthode d’initialisation de la table.  
  
3. Copiez le code suivant dans la classe partielle :  
  
    ```  
    public override void EndInit()  
    {  
        base.EndInit();  
        Order_DetailsRowChanging += TestRowChangeEvent;  
    }  
  
    public void TestRowChangeEvent(object sender, Order_DetailsRowChangeEvent e)  
    {  
        if ((short)e.Row.Quantity <= 0)  
        {  
            e.Row.SetColumnError("Quantity", "Quantity must be greater than 0");  
        }  
        else  
        {  
            e.Row.SetColumnError("Quantity", "");  
        }  
    }  
    ```  
  
## <a name="to-retrieve-changed-rows"></a>Pour récupérer des lignes modifiées  
 Chaque ligne dans une table de données a un <xref:System.Data.DataRow.RowState%2A> propriété qui effectue le suivi de l’état actuel de cette ligne en utilisant les valeurs dans le <xref:System.Data.DataRowState> énumération. Vous pouvez retourner des lignes modifiées d’une table de données ou le jeu de données en appelant le `GetChanges` méthode d’un <xref:System.Data.DataSet> ou <xref:System.Data.DataTable>. Vous pouvez vérifier qu’il existe des modifications avant d’appeler `GetChanges` en appelant le <xref:System.Data.DataSet.HasChanges%2A> méthode d’un jeu de données. Pour plus d’informations sur <xref:System.Data.DataSet.HasChanges%2A>, consultez [Guide pratique pour : Rechercher les lignes modifiées](https://msdn.microsoft.com/library/af160d20-472b-4c13-8f15-75480c39a653).  
  
> [!NOTE]
> Une fois que vous validez des modifications à une table de données ou le jeu de données (en appelant le <xref:System.Data.DataSet.AcceptChanges%2A> méthode), la `GetChanges` méthode ne retourne aucune donnée. Si votre application doit traiter des lignes modifiées, vous devez traiter les modifications avant d’appeler le `AcceptChanges` (méthode).  
  
 Appel de la <xref:System.Data.DataSet.GetChanges%2A> méthode d’une table de données ou le jeu de données retourne une nouvelle table de données ou le jeu de données qui contient uniquement les enregistrements qui ont été modifiés. Si vous souhaitez obtenir des enregistrements spécifiques, par exemple, uniquement de nouveaux enregistrements ou les enregistrements modifiés — vous pouvez passer une valeur à partir de la <xref:System.Data.DataRowState> énumération en tant que paramètre à la `GetChanges` (méthode).  
  
 Utilisez le <xref:System.Data.DataRowVersion> énumération pour accéder aux différentes versions d’une ligne (par exemple, les valeurs d’origine se trouvaient dans une ligne avant de le traiter).  
  
#### <a name="to-get-all-changed-records-from-a-dataset"></a>Pour obtenir tous les enregistrements modifiés à partir d’un jeu de données  
  
- Appelez le <xref:System.Data.DataSet.GetChanges%2A> méthode d’un jeu de données.  
  
     L’exemple suivant crée un nouveau dataset appelé `changedRecords` et la remplit avec tous les enregistrements modifiés d’un autre dataset appelé `dataSet1`.  
  
     [!code-csharp[VbRaddataEditing#14](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#14)]
     [!code-vb[VbRaddataEditing#14](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#14)]  
  
#### <a name="to-get-all-changed-records-from-a-data-table"></a>Pour obtenir tous les enregistrements modifiés à partir d’une table de données  
  
- Appelez le <xref:System.Data.DataTable.GetChanges%2A> méthode d’un DataTable.  
  
     L’exemple suivant crée une nouvelle table de données appelée `changedRecordsTable` et la remplit avec tous les enregistrements modifiés d’une autre table de données appelée `dataTable1`.  
  
     [!code-csharp[VbRaddataEditing#15](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#15)]
     [!code-vb[VbRaddataEditing#15](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#15)]  
  
#### <a name="to-get-all-records-that-have-a-specific-row-state"></a>Pour obtenir tous les enregistrements qui ont un état de ligne spécifique  
  
- Appelez le `GetChanges` (méthode) d’un jeu de données ou la table de données et la passe un <xref:System.Data.DataRowState> valeur d’énumération en tant qu’argument.  
  
     L’exemple suivant montre comment créer un nouveau dataset appelé `addedRecords` et remplir uniquement avec les enregistrements qui ont été ajoutés à la `dataSet1` jeu de données.  
  
     [!code-csharp[VbRaddataEditing#16](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#16)]
     [!code-vb[VbRaddataEditing#16](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#16)]  
  
- L’exemple suivant montre comment retourner tous les enregistrements qui ont été récemment ajoutés à la `Customers` table :  
  
     [!code-csharp[VbRaddataEditing#17](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#17)]
     [!code-vb[VbRaddataEditing#17](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#17)]  
  
## <a name="access-the-original-version-of-a-datarow"></a>Accéder à la version d’origine d’un DataRow  
 Lorsque des modifications sont apportées aux lignes de données, le jeu de données conserve les deux d’origine (<xref:System.Data.DataRowVersion>) et les nouveaux (<xref:System.Data.DataRowVersion>) versions de la ligne. Par exemple, avant d’appeler le `AcceptChanges` (méthode), votre application peut accéder à différentes versions d’un enregistrement (tel que défini dans le <xref:System.Data.DataRowVersion> énumération) et traiter les modifications en conséquence.  
  
> [!NOTE]
> Différentes versions d’une ligne existent uniquement une fois qu’il a été modifié et avant qu’elle le `AcceptChanges` méthode a été appelée. Après le `AcceptChanges` méthode a été appelée, les versions actuelles et d’origine sont identiques.  
  
 En passant le <xref:System.Data.DataRowVersion> valeur, ainsi que l’index de colonne (ou le nom de la colonne sous forme de chaîne) retourne la valeur de la version de ligne particulière de cette colonne. La colonne modifiée est identifiée pendant le <xref:System.Data.DataTable.ColumnChanging> et <xref:System.Data.DataTable.ColumnChanged> événements. Il s’agit d’un bon moment pour examiner les différentes versions de ligne à des fins de validation. Toutefois, si vous avez suspendu temporairement les contraintes, ces événements ne sont pas déclenchés, et vous devrez par programmation identifier les colonnes qui ont été modifiés. Ce faire, vous pouvez itérer au sein du <xref:System.Data.DataTable.Columns%2A> collection et en comparant les différentes <xref:System.Data.DataRowVersion> valeurs.  
  
#### <a name="to-get-the-original-version-of-a-record"></a>Pour obtenir la version d’origine d’un enregistrement  
  
- Accéder à la valeur d’une colonne en passant le <xref:System.Data.DataRowVersion> de la ligne que vous souhaitez retourner.  
  
     L’exemple suivant montre comment utiliser un <xref:System.Data.DataRowVersion> valeur à obtenir la valeur d’origine d’un `CompanyName` champ dans un <xref:System.Data.DataRow>:  
  
     [!code-csharp[VbRaddataEditing#21](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#21)]
     [!code-vb[VbRaddataEditing#21](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#21)]  
  
## <a name="access-the-current-version-of-a-datarow"></a>Accéder à la version actuelle d’un DataRow  
  
#### <a name="to-get-the-current-version-of-a-record"></a>Pour obtenir la version actuelle d’un enregistrement  
  
- Accéder à la valeur d’une colonne, puis ajouter un paramètre à l’index qui indique quelle version d’une ligne que vous souhaitez retourner.  
  
     L’exemple suivant montre comment utiliser un <xref:System.Data.DataRowVersion> valeur à obtenir la valeur actuelle d’un `CompanyName` champ dans un <xref:System.Data.DataRow>:  
  
     [!code-csharp[VbRaddataEditing#22](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#22)]
     [!code-vb[VbRaddataEditing#22](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#22)]  
  
## <a name="see-also"></a>Voir aussi

- [Guide pratique pour Valider les données dans le contrôle de DataGridView Windows Forms](https://msdn.microsoft.com/library/d10aef35-701e-4a3c-a684-2a2ed1aeaca6)   
- [Guide pratique pour Afficher des icônes d’erreur pour la Validation de formulaire à l’aide du composant ErrorProvider Windows Forms](https://msdn.microsoft.com/library/3b681a32-9db4-497b-a34b-34980eabee46)