---
title: Valider les données dans des datasets
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- DataTable.ColumnChanging
- System.Data.DataTable.ColumnChanging
- System.Data.DataTable.RowChanging
- DataTable.RowChanging
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data validation, datasets
- data validation
- validating data, datasets
- updating datasets, validating data
ms.assetid: 79500596-1e4d-478e-a991-a636fd73a622
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 80f258e87bd7bd197460d5ff9ab29b6964347f7c
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68925414"
---
# <a name="validate-data-in-datasets"></a>Valider les données dans des datasets
La validation des données est le processus qui consiste à confirmer que les valeurs entrées dans les objets de données sont conformes aux contraintes dans le schéma d’un DataSet. Le processus de validation confirme également que ces valeurs suivent les règles qui ont été établies pour votre application. Il est conseillé de valider les données avant d’envoyer des mises à jour à la base de données sous-jacente. Cela réduit les erreurs ainsi que le nombre potentiel d’allers-retours entre une application et la base de données.

Vous pouvez vérifier que les données écrites dans un jeu de données sont valides en générant des contrôles de validation dans le jeu de données lui-même. Le DataSet peut vérifier les données quelle que soit la façon dont la mise à jour est effectuée, que ce soit directement par des contrôles dans un formulaire, dans un composant ou d’une autre manière. Étant donné que le jeu de données fait partie de votre application (contrairement au serveur principal de la base de données), il s’agit d’un emplacement logique permettant de créer une validation propre à l’application.

Le meilleur emplacement pour ajouter la validation à votre application se trouve dans le fichier de classe partielle du jeu de données. Dans [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] ou[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)], ouvrez le **Concepteur de DataSet** et double-cliquez sur la colonne ou la table pour laquelle vous souhaitez créer la validation. Cette action crée automatiquement un <xref:System.Data.DataTable.ColumnChanging> gestionnaire <xref:System.Data.DataTable.RowChanging> d’événements ou.

## <a name="validate-data"></a>Valider les données
La validation dans un DataSet s’effectue des manières suivantes:

- En créant votre propre validation propre à l’application qui peut vérifier des valeurs dans une colonne de données individuelle pendant les modifications. Pour plus d'informations, voir [Procédure : Valider les données lors des](validate-data-in-datasets.md)modifications de colonne.

- En créant votre propre validation propre à l’application qui peut vérifier les données jusqu’aux valeurs pendant la modification d’une ligne de données entière. Pour plus d’informations, consultez [Guide pratique pour Validez les données pendant](validate-data-in-datasets.md)les modifications de ligne.

- En créant des clés, des contraintes uniques, et ainsi de suite dans le cadre de la définition de schéma réelle du jeu de données.

- En définissant les propriétés de <xref:System.Data.DataColumn> l’objet, telles que <xref:System.Data.DataColumn.MaxLength%2A>, <xref:System.Data.DataColumn.AllowDBNull%2A>et <xref:System.Data.DataColumn.Unique%2A>.

Plusieurs événements sont déclenchés par <xref:System.Data.DataTable> l’objet lorsqu’une modification se produit dans un enregistrement:

- Les <xref:System.Data.DataTable.ColumnChanging> événements <xref:System.Data.DataTable.ColumnChanged> et sont déclenchés pendant et après chaque modification apportée à une colonne individuelle. L' <xref:System.Data.DataTable.ColumnChanging> événement est utile lorsque vous souhaitez valider les modifications dans des colonnes spécifiques. Les informations sur la modification proposée sont passées comme argument avec l’événement.
- Les <xref:System.Data.DataTable.RowChanging> événements <xref:System.Data.DataTable.RowChanged> et sont déclenchés pendant et après toute modification apportée à une ligne. L' <xref:System.Data.DataTable.RowChanging> événement est plus général. Elle indique qu’une modification se produit quelque part dans la ligne, mais que vous ne savez pas quelle colonne a changé.

Par défaut, chaque modification apportée à une colonne déclenche donc quatre événements. Le premier est le <xref:System.Data.DataTable.ColumnChanging> et <xref:System.Data.DataTable.ColumnChanged> les événements de la colonne spécifique qui est modifiée. Ensuite, les <xref:System.Data.DataTable.RowChanging> événements <xref:System.Data.DataTable.RowChanged> et. Si plusieurs modifications sont apportées à la ligne, les événements sont déclenchés pour chaque modification.

> [!NOTE]
> La méthode de la <xref:System.Data.DataRow.BeginEdit%2A> ligne de données désactive <xref:System.Data.DataTable.RowChanging> les <xref:System.Data.DataTable.RowChanged> événements et après chaque modification de chaque colonne. Dans ce cas, l’événement n’est pas déclenché tant <xref:System.Data.DataRow.EndEdit%2A> que la méthode n’a pas été <xref:System.Data.DataTable.RowChanging> appelée <xref:System.Data.DataTable.RowChanged> , lorsque les événements et ne sont déclenchés qu’une seule fois. Pour plus d’informations, consultez [Désactiver les contraintes lors du remplissage d’un DataSet](../data-tools/turn-off-constraints-while-filling-a-dataset.md).

L’événement que vous choisissez dépend du niveau de granularité souhaité pour la validation. S’il est important d’intercepter immédiatement une erreur en cas de modification d’une colonne, générez <xref:System.Data.DataTable.ColumnChanging> la validation à l’aide de l’événement. Sinon, utilisez l' <xref:System.Data.DataTable.RowChanging> événement, qui peut entraîner l’interception de plusieurs erreurs à la fois. En outre, si vos données sont structurées de manière à ce que la valeur d’une colonne soit validée en fonction du contenu d’une autre colonne <xref:System.Data.DataTable.RowChanging> , effectuez la validation pendant l’événement.

Lorsque des enregistrements sont mis à <xref:System.Data.DataTable> jour, l’objet déclenche des événements auxquels vous pouvez répondre au fur et à mesure que des modifications se produisent et une fois les modifications apportées.

Si votre application utilise un DataSet typé, vous pouvez créer des gestionnaires d’événements fortement typés. Cela ajoute quatre événements typés supplémentaires pour lesquels vous pouvez créer des gestionnaires `dataTableNameRowChanging`: `dataTableNameRowChanged` `dataTableNameRowDeleting`,, et `dataTableNameRowDeleted`. Ces gestionnaires d’événements typés passent un argument qui comprend les noms de colonnes de votre table qui facilitent l’écriture et la lecture de code.

## <a name="data-update-events"></a>Événements de mise à jour des données

|Événement|Description|
|-----------|-----------------|
|<xref:System.Data.DataTable.ColumnChanging>|La valeur d’une colonne est en cours de modification. L’événement passe la ligne et la colonne à vous, ainsi que la nouvelle valeur proposée.|
|<xref:System.Data.DataTable.ColumnChanged>|La valeur d’une colonne a été modifiée. L’événement passe la ligne et la colonne à vous, ainsi que la valeur proposée.|
|<xref:System.Data.DataTable.RowChanging>|Les modifications apportées à un <xref:System.Data.DataRow> objet sont sur le paragraphe d’être validées dans le jeu de données. Si vous n’avez pas appelé <xref:System.Data.DataRow.BeginEdit%2A> la méthode, <xref:System.Data.DataTable.RowChanging> l’événement est déclenché pour chaque modification apportée à une <xref:System.Data.DataTable.ColumnChanging> colonne immédiatement après le déclenchement de l’événement. Si vous avez <xref:System.Data.DataRow.BeginEdit%2A> appelé avant d’apporter des <xref:System.Data.DataTable.RowChanging> modifications, l’événement est déclenché uniquement lorsque <xref:System.Data.DataRow.EndEdit%2A> vous appelez la méthode.<br /><br /> L’événement vous transmet la ligne, avec une valeur indiquant le type d’action (modification, insertion, etc.) en cours d’exécution.|
|<xref:System.Data.DataTable.RowChanged>|Une ligne a été modifiée. L’événement vous transmet la ligne, avec une valeur indiquant le type d’action (modification, insertion, etc.) en cours d’exécution.|
|<xref:System.Data.DataTable.RowDeleting>|Une ligne est en cours de suppression. L’événement vous transmet la ligne, avec une valeur indiquant le type d’action (suppression) en cours d’exécution.|
|<xref:System.Data.DataTable.RowDeleted>|Une ligne a été supprimée. L’événement vous transmet la ligne, avec une valeur indiquant le type d’action (suppression) en cours d’exécution.|

Les <xref:System.Data.DataTable.ColumnChanging>événements <xref:System.Data.DataTable.RowChanging>, et<xref:System.Data.DataTable.RowDeleting> sont déclenchés pendant le processus de mise à jour. Vous pouvez utiliser ces événements pour valider des données ou effectuer d’autres types de traitement. Étant donné que la mise à jour est en cours pendant ces événements, vous pouvez l’annuler en levant une exception, ce qui empêche la fin de la mise à jour.

Les <xref:System.Data.DataTable.ColumnChanged>événements <xref:System.Data.DataTable.RowChanged> , et<xref:System.Data.DataTable.RowDeleted> sont des événements de notification qui sont déclenchés lorsque la mise à jour s’est terminée avec succès. Ces événements sont utiles lorsque vous souhaitez effectuer des actions supplémentaires en fonction d’une mise à jour réussie.

## <a name="validate-data-during-column-changes"></a>Valider les données lors des modifications de colonne

> [!NOTE]
> L' **Concepteur de DataSet** crée une classe partielle dans laquelle la logique de validation peut être ajoutée à un DataSet. Le jeu de données généré par le concepteur ne supprime pas ou ne modifie pas le code dans la classe partielle.

Vous pouvez valider les données lorsque la valeur dans une colonne de données change en répondant <xref:System.Data.DataTable.ColumnChanging> à l’événement. En cas de déclenchement, cet événement passe un argument<xref:System.Data.DataColumnChangeEventArgs.ProposedValue%2A>d’événement () qui contient la valeur proposée pour la colonne actuelle. En fonction du contenu de `e.ProposedValue`, vous pouvez:

- Acceptez la valeur proposée en ne faisant rien.

- Rejetez la valeur proposée en définissant l’erreur<xref:System.Data.DataRow.SetColumnError%2A>de colonne () à partir du gestionnaire d’événements de modification de colonne.

- Si vous le souhaitez <xref:System.Windows.Forms.ErrorProvider> , utilisez un contrôle pour afficher un message d’erreur à l’utilisateur. Pour plus d’informations, consultez [ErrorProvider, composant](/dotnet/framework/winforms/controls/errorprovider-component-windows-forms).

La validation peut également être effectuée pendant <xref:System.Data.DataTable.RowChanging> l’événement.

## <a name="validate-data-during-row-changes"></a>Valider les données lors des modifications de ligne
Vous pouvez écrire du code pour vérifier que chaque colonne que vous souhaitez valider contient des données qui répondent aux exigences de votre application. Pour ce faire, définissez la colonne pour qu’elle indique qu’elle contient une erreur si une valeur proposée est inacceptable. Les exemples suivants définissent une erreur de `Quantity` colonne lorsque la colonne est inférieure ou égale à 0. Les gestionnaires d’événements de modification de ligne doivent ressembler aux exemples suivants.

### <a name="to-validate-data-when-a-row-changes-visual-basic"></a>Pour valider des données lorsqu’une ligne est modifiée (Visual Basic)

1. Ouvrez votre dataset dans le **Concepteur de DataSet**. Pour plus d’informations, consultez [Procédure pas à pas : Création d’un jeu de données](walkthrough-creating-a-dataset-with-the-dataset-designer.md)dans le concepteur de DataSet.

2. Double-cliquez sur la barre de titre de la table que vous souhaitez valider. Cette action crée automatiquement le <xref:System.Data.DataTable.RowChanging> gestionnaire <xref:System.Data.DataTable> d’événements du dans le fichier de classe partielle du DataSet.

    > [!TIP]
    > Double-cliquez à gauche du nom de la table pour créer le gestionnaire d’événements de modification de ligne. Si vous double-cliquez sur le nom de la table, vous pouvez le modifier.

     [!code-vb[VbRaddataValidating#3](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_1.vb)]

### <a name="to-validate-data-when-a-row-changes-c"></a>Pour valider des données en cas de modificationC#d’une ligne ()

1. Ouvrez votre dataset dans le **Concepteur de DataSet**. Pour plus d’informations, consultez [Procédure pas à pas : Création d’un jeu de données](walkthrough-creating-a-dataset-with-the-dataset-designer.md)dans le concepteur de DataSet.

2. Double-cliquez sur la barre de titre de la table que vous souhaitez valider. Cette action crée un fichier de classe partielle pour le <xref:System.Data.DataTable>.

    > [!NOTE]
    > Le **Concepteur de DataSet** ne crée pas automatiquement un gestionnaire d’événements pour <xref:System.Data.DataTable.RowChanging> l’événement. Vous devez créer une méthode pour gérer l' <xref:System.Data.DataTable.RowChanging> événement et exécuter du code pour raccorder l’événement dans la méthode d’initialisation de la table.

3. Copiez le code suivant dans la classe partielle:

    ```csharp
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

## <a name="to-retrieve-changed-rows"></a>Pour récupérer les lignes modifiées
Chaque ligne d’une table de données possède <xref:System.Data.DataRow.RowState%2A> une propriété qui effectue le suivi de l’état actuel de cette ligne à l’aide des <xref:System.Data.DataRowState> valeurs de l’énumération. Vous pouvez retourner des lignes modifiées à partir d’un DataSet ou d’une `GetChanges` table de données <xref:System.Data.DataSet> en <xref:System.Data.DataTable>appelant la méthode d’un ou d’un. Vous pouvez vérifier que des modifications existent avant d' `GetChanges` appeler en appelant <xref:System.Data.DataSet.HasChanges%2A> la méthode d’un jeu de données.

> [!NOTE]
> Une fois que vous avez validé les modifications apportées à un DataSet <xref:System.Data.DataSet.AcceptChanges%2A> ou une table de `GetChanges` données (en appelant la méthode), la méthode ne retourne aucune donnée. Si votre application doit traiter les lignes modifiées, vous devez traiter les modifications avant d’appeler `AcceptChanges` la méthode.

L’appel <xref:System.Data.DataSet.GetChanges%2A> de la méthode d’un DataSet ou d’une table de données retourne un nouveau DataSet ou une nouvelle table de données qui contient uniquement les enregistrements qui ont été modifiés. Si vous souhaitez obtenir des enregistrements spécifiques (par exemple, uniquement des nouveaux enregistrements ou des enregistrements modifiés), vous pouvez passer une valeur <xref:System.Data.DataRowState> de l’énumération en tant `GetChanges` que paramètre à la méthode.

Utilisez l' <xref:System.Data.DataRowVersion> énumération pour accéder aux différentes versions d’une ligne (par exemple, les valeurs d’origine qui se trouvaient dans une ligne avant de la traiter).

### <a name="to-get-all-changed-records-from-a-dataset"></a>Pour obtenir tous les enregistrements modifiés d’un DataSet

- Appelez la <xref:System.Data.DataSet.GetChanges%2A> méthode d’un jeu de données.

     L’exemple suivant crée un nouveau DataSet appelé `changedRecords` et le remplit avec tous les enregistrements modifiés d’un autre DataSet appelé `dataSet1`.

     [!code-csharp[VbRaddataEditing#14](../data-tools/codesnippet/CSharp/validate-data-in-datasets_2.cs)]
     [!code-vb[VbRaddataEditing#14](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_2.vb)]

### <a name="to-get-all-changed-records-from-a-data-table"></a>Pour obtenir tous les enregistrements modifiés d’une table de données

- Appelez la <xref:System.Data.DataTable.GetChanges%2A> méthode d’un DataTable.

     L’exemple suivant crée une nouvelle table de données `changedRecordsTable` appelée et la remplit avec tous les enregistrements modifiés d’une autre table de `dataTable1`données appelée.

     [!code-csharp[VbRaddataEditing#15](../data-tools/codesnippet/CSharp/validate-data-in-datasets_3.cs)]
     [!code-vb[VbRaddataEditing#15](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_3.vb)]

### <a name="to-get-all-records-that-have-a-specific-row-state"></a>Pour obtenir tous les enregistrements qui ont un état de ligne spécifique

- Appelez la `GetChanges` méthode d’un DataSet ou d’une table de données <xref:System.Data.DataRowState> et transmettez une valeur d’énumération en tant qu’argument.

     L’exemple suivant montre comment créer un jeu de données appelé `addedRecords` et le remplir uniquement avec les `dataSet1` enregistrements qui ont été ajoutés au jeu de données.

     [!code-csharp[VbRaddataEditing#16](../data-tools/codesnippet/CSharp/validate-data-in-datasets_4.cs)]
     [!code-vb[VbRaddataEditing#16](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_4.vb)]

     L’exemple suivant montre comment retourner tous les enregistrements qui ont été récemment ajoutés à `Customers` la table:

     [!code-csharp[VbRaddataEditing#17](../data-tools/codesnippet/CSharp/validate-data-in-datasets_5.cs)]
     [!code-vb[VbRaddataEditing#17](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_5.vb)]

## <a name="access-the-original-version-of-a-datarow"></a>Accéder à la version d’origine d’un DataRow
Lorsque des modifications sont apportées aux lignes de données, le DataSet conserve à<xref:System.Data.DataRowVersion.Original>la fois les versions<xref:System.Data.DataRowVersion.Current>d’origine () et New () de la ligne. Par exemple, avant d’appeler `AcceptChanges` la méthode, votre application peut accéder aux différentes versions d’un enregistrement (tel que défini <xref:System.Data.DataRowVersion> dans l’énumération) et traiter les modifications en conséquence.

> [!NOTE]
> Les différentes versions d’une ligne existent uniquement une fois qu’elle a été modifiée et `AcceptChanges` avant que la méthode ait été appelée. Une fois `AcceptChanges` la méthode appelée, les versions actuelles et d’origine sont les mêmes.

Le passage <xref:System.Data.DataRowVersion> de la valeur avec l’index de colonne (ou le nom de colonne en tant que chaîne) retourne la valeur de la version de ligne particulière de cette colonne. La colonne modifiée est identifiée lors <xref:System.Data.DataTable.ColumnChanging> des <xref:System.Data.DataTable.ColumnChanged> événements et. Il s’agit d’un bon moment pour inspecter les différentes versions de ligne à des fins de validation. Toutefois, si vous avez temporairement suspendu des contraintes, ces événements ne seront pas déclenchés, et vous devrez identifier par programmation les colonnes qui ont changé. Pour ce faire, vous pouvez itérer au <xref:System.Data.DataTable.Columns%2A> sein de la collection et <xref:System.Data.DataRowVersion> comparer les différentes valeurs.

### <a name="to-get-the-original-version-of-a-record"></a>Pour obtenir la version d’origine d’un enregistrement

- Accédez à la valeur d’une colonne en passant le <xref:System.Data.DataRowVersion> de la ligne que vous souhaitez retourner.

     L’exemple suivant montre comment utiliser une <xref:System.Data.DataRowVersion> valeur pour obtenir la valeur d’origine d’un `CompanyName` champ dans un: <xref:System.Data.DataRow>

     [!code-csharp[VbRaddataEditing#21](../data-tools/codesnippet/CSharp/validate-data-in-datasets_6.cs)]
     [!code-vb[VbRaddataEditing#21](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_6.vb)]

## <a name="access-the-current-version-of-a-datarow"></a>Accéder à la version actuelle d’un DataRow

### <a name="to-get-the-current-version-of-a-record"></a>Pour obtenir la version actuelle d’un enregistrement

- Accédez à la valeur d’une colonne, puis ajoutez un paramètre à l’index qui indique la version d’une ligne que vous souhaitez retourner.

     L’exemple suivant montre comment utiliser une <xref:System.Data.DataRowVersion> valeur pour obtenir la valeur actuelle d’un `CompanyName` champ dans un <xref:System.Data.DataRow>:

     [!code-csharp[VbRaddataEditing#22](../data-tools/codesnippet/CSharp/validate-data-in-datasets_7.cs)]
     [!code-vb[VbRaddataEditing#22](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_7.vb)]

## <a name="see-also"></a>Voir aussi

- [Outils de dataset dans Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
- [Guide pratique pour Valider les données dans le contrôle DataGridView Windows Forms](/dotnet/framework/winforms/controls/how-to-validate-data-in-the-windows-forms-datagridview-control)
- [Guide pratique : Afficher les icônes d’erreur pour la validation de formulaire avec le composant ErrorProvider Windows Forms](/dotnet/framework/winforms/controls/display-error-icons-for-form-validation-with-wf-errorprovider)