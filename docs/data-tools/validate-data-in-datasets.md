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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: ed115e851e9c2291dfc9d00f4bb36f670a7f3e00
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586066"
---
# <a name="validate-data-in-datasets"></a>Valider les données dans des datasets
La validation des données est le processus qui consiste à confirmer que les valeurs entrées dans les objets de données sont conformes aux contraintes dans le schéma d’un DataSet. Le processus de validation confirme également que ces valeurs suivent les règles qui ont été établies pour votre application. Il est conseillé de valider les données avant d’envoyer des mises à jour à la base de données sous-jacente. Cela réduit les erreurs ainsi que le nombre potentiel d’allers-retours entre une application et la base de données.

Vous pouvez vérifier que les données écrites dans un jeu de données sont valides en générant des contrôles de validation dans le jeu de données lui-même. Le DataSet peut vérifier les données quelle que soit la façon dont la mise à jour est effectuée, que ce soit directement par des contrôles dans un formulaire, dans un composant ou d’une autre manière. Étant donné que le jeu de données fait partie de votre application (contrairement au serveur principal de la base de données), il s’agit d’un emplacement logique permettant de créer une validation propre à l’application.

Le meilleur emplacement pour ajouter la validation à votre application se trouve dans le fichier de classe partielle du jeu de données. Dans [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] ou [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)], ouvrez le **Concepteur de DataSet** et double-cliquez sur la colonne ou la table pour laquelle vous souhaitez créer la validation. Cette action crée automatiquement un gestionnaire d’événements <xref:System.Data.DataTable.ColumnChanging> ou <xref:System.Data.DataTable.RowChanging>.

## <a name="validate-data"></a>Valider des données
La validation dans un DataSet s’effectue des manières suivantes :

- En créant votre propre validation propre à l’application qui peut vérifier des valeurs dans une colonne de données individuelle pendant les modifications. Pour plus d’informations, consultez [Comment : valider des données pendant les modifications de colonnes](validate-data-in-datasets.md).

- En créant votre propre validation propre à l’application qui peut vérifier les données jusqu’aux valeurs pendant la modification d’une ligne de données entière. Pour plus d’informations, consultez [Comment : valider des données pendant les modifications de ligne](validate-data-in-datasets.md).

- En créant des clés, des contraintes uniques, et ainsi de suite dans le cadre de la définition de schéma réelle du jeu de données.

- En définissant les propriétés de l’objet <xref:System.Data.DataColumn>, comme <xref:System.Data.DataColumn.MaxLength%2A>, <xref:System.Data.DataColumn.AllowDBNull%2A>et <xref:System.Data.DataColumn.Unique%2A>.

Plusieurs événements sont déclenchés par l’objet <xref:System.Data.DataTable> lorsqu’une modification se produit dans un enregistrement :

- Les événements <xref:System.Data.DataTable.ColumnChanging> et <xref:System.Data.DataTable.ColumnChanged> sont déclenchés pendant et après chaque modification apportée à une colonne individuelle. L’événement <xref:System.Data.DataTable.ColumnChanging> est utile lorsque vous souhaitez valider les modifications dans des colonnes spécifiques. Les informations sur la modification proposée sont passées comme argument avec l’événement.
- Les événements <xref:System.Data.DataTable.RowChanging> et <xref:System.Data.DataTable.RowChanged> sont déclenchés pendant et après toute modification apportée à une ligne. L’événement <xref:System.Data.DataTable.RowChanging> est plus général. Elle indique qu’une modification se produit quelque part dans la ligne, mais que vous ne savez pas quelle colonne a changé.

Par défaut, chaque modification apportée à une colonne déclenche donc quatre événements. La première est la <xref:System.Data.DataTable.ColumnChanging> et <xref:System.Data.DataTable.ColumnChanged> événements pour la colonne spécifique qui est modifiée. Ensuite, les événements <xref:System.Data.DataTable.RowChanging> et <xref:System.Data.DataTable.RowChanged>. Si plusieurs modifications sont apportées à la ligne, les événements sont déclenchés pour chaque modification.

> [!NOTE]
> La méthode <xref:System.Data.DataRow.BeginEdit%2A> de la ligne de données désactive les événements <xref:System.Data.DataTable.RowChanging> et <xref:System.Data.DataTable.RowChanged> après chaque modification de chaque colonne. Dans ce cas, l’événement n’est pas déclenché tant que la méthode <xref:System.Data.DataRow.EndEdit%2A> n’a pas été appelée, lorsque les événements <xref:System.Data.DataTable.RowChanging> et <xref:System.Data.DataTable.RowChanged> sont déclenchés une seule fois. Pour plus d’informations, consultez [Désactiver les contraintes lors du remplissage d’un DataSet](../data-tools/turn-off-constraints-while-filling-a-dataset.md).

L’événement que vous choisissez dépend du niveau de granularité souhaité pour la validation. S’il est important d’intercepter immédiatement une erreur en cas de modification d’une colonne, générez la validation à l’aide de l’événement <xref:System.Data.DataTable.ColumnChanging>. Sinon, utilisez l’événement <xref:System.Data.DataTable.RowChanging>, qui peut entraîner l’interception de plusieurs erreurs à la fois. En outre, si vos données sont structurées de manière à ce que la valeur d’une colonne soit validée en fonction du contenu d’une autre colonne, effectuez la validation lors de l’événement <xref:System.Data.DataTable.RowChanging>.

Lorsque les enregistrements sont mis à jour, l’objet <xref:System.Data.DataTable> déclenche des événements auxquels vous pouvez répondre au fur et à mesure que des modifications se produisent et une fois les modifications apportées.

Si votre application utilise un DataSet typé, vous pouvez créer des gestionnaires d’événements fortement typés. Cela ajoute quatre événements typés supplémentaires pour lesquels vous pouvez créer des gestionnaires : `dataTableNameRowChanging`, `dataTableNameRowChanged`, `dataTableNameRowDeleting`et `dataTableNameRowDeleted`. Ces gestionnaires d’événements typés passent un argument qui comprend les noms de colonnes de votre table qui facilitent l’écriture et la lecture de code.

## <a name="data-update-events"></a>Événements de mise à jour des données

|Event|Description|
|-----------|-----------------|
|<xref:System.Data.DataTable.ColumnChanging>|La valeur d’une colonne est en cours de modification. L’événement passe la ligne et la colonne à vous, ainsi que la nouvelle valeur proposée.|
|<xref:System.Data.DataTable.ColumnChanged>|La valeur d’une colonne a été modifiée. L’événement passe la ligne et la colonne à vous, ainsi que la valeur proposée.|
|<xref:System.Data.DataTable.RowChanging>|Les modifications apportées à un objet <xref:System.Data.DataRow> sont sur le présent validées dans le jeu de données. Si vous n’avez pas appelé la méthode <xref:System.Data.DataRow.BeginEdit%2A>, l’événement <xref:System.Data.DataTable.RowChanging> est déclenché pour chaque modification apportée à une colonne immédiatement après le déclenchement de l’événement <xref:System.Data.DataTable.ColumnChanging>. Si vous avez appelé <xref:System.Data.DataRow.BeginEdit%2A> avant d’apporter des modifications, l’événement <xref:System.Data.DataTable.RowChanging> est déclenché uniquement lorsque vous appelez la méthode <xref:System.Data.DataRow.EndEdit%2A>.<br /><br /> L’événement vous transmet la ligne, avec une valeur indiquant le type d’action (modification, insertion, etc.) en cours d’exécution.|
|<xref:System.Data.DataTable.RowChanged>|Une ligne a été modifiée. L’événement vous transmet la ligne, avec une valeur indiquant le type d’action (modification, insertion, etc.) en cours d’exécution.|
|<xref:System.Data.DataTable.RowDeleting>|Une ligne est en cours de suppression. L’événement vous transmet la ligne, avec une valeur indiquant le type d’action (suppression) en cours d’exécution.|
|<xref:System.Data.DataTable.RowDeleted>|Une ligne a été supprimée. L’événement vous transmet la ligne, avec une valeur indiquant le type d’action (suppression) en cours d’exécution.|

Les événements <xref:System.Data.DataTable.ColumnChanging>, <xref:System.Data.DataTable.RowChanging>et <xref:System.Data.DataTable.RowDeleting> sont déclenchés pendant le processus de mise à jour. Vous pouvez utiliser ces événements pour valider des données ou effectuer d’autres types de traitement. Étant donné que la mise à jour est en cours pendant ces événements, vous pouvez l’annuler en levant une exception, ce qui empêche la fin de la mise à jour.

Les événements <xref:System.Data.DataTable.ColumnChanged>, <xref:System.Data.DataTable.RowChanged> et <xref:System.Data.DataTable.RowDeleted> sont des événements de notification déclenchés lorsque la mise à jour est terminée. Ces événements sont utiles lorsque vous souhaitez effectuer des actions supplémentaires en fonction d’une mise à jour réussie.

## <a name="validate-data-during-column-changes"></a>Valider les données lors des modifications de colonne

> [!NOTE]
> L' **Concepteur de DataSet** crée une classe partielle dans laquelle la logique de validation peut être ajoutée à un DataSet. Le jeu de données généré par le concepteur ne supprime pas ou ne modifie pas le code dans la classe partielle.

Vous pouvez valider les données lorsque la valeur dans une colonne de données change en répondant à l’événement <xref:System.Data.DataTable.ColumnChanging>. En cas de déclenchement, cet événement passe un argument d’événement (<xref:System.Data.DataColumnChangeEventArgs.ProposedValue%2A>) qui contient la valeur proposée pour la colonne actuelle. En fonction du contenu de `e.ProposedValue`, vous pouvez :

- Acceptez la valeur proposée en ne faisant rien.

- Rejetez la valeur proposée en définissant l’erreur de colonne (<xref:System.Data.DataRow.SetColumnError%2A>) à partir du gestionnaire d’événements de modification de colonne.

- Si vous le souhaitez, utilisez un contrôle <xref:System.Windows.Forms.ErrorProvider> pour afficher un message d’erreur à l’utilisateur. Pour plus d’informations, consultez [ErrorProvider, composant](/dotnet/framework/winforms/controls/errorprovider-component-windows-forms).

La validation peut également être effectuée au cours de l’événement <xref:System.Data.DataTable.RowChanging>.

## <a name="validate-data-during-row-changes"></a>Valider les données lors des modifications de ligne
Vous pouvez écrire du code pour vérifier que chaque colonne que vous souhaitez valider contient des données qui répondent aux exigences de votre application. Pour ce faire, définissez la colonne pour qu’elle indique qu’elle contient une erreur si une valeur proposée est inacceptable. Les exemples suivants définissent une erreur de colonne lorsque la `Quantity` colonne est inférieure ou égale à 0. Les gestionnaires d’événements de modification de ligne doivent ressembler aux exemples suivants.

### <a name="to-validate-data-when-a-row-changes-visual-basic"></a>Pour valider des données lorsqu’une ligne est modifiée (Visual Basic)

1. Ouvrez votre dataset dans le **Concepteur de DataSet**. Pour plus d’informations, consultez [procédure pas à pas : création d’un DataSet dans le concepteur de DataSet](walkthrough-creating-a-dataset-with-the-dataset-designer.md).

2. Double-cliquez sur la barre de titre de la table que vous souhaitez valider. Cette action crée automatiquement le gestionnaire d’événements <xref:System.Data.DataTable.RowChanging> du <xref:System.Data.DataTable> dans le fichier de classe partielle du DataSet.

    > [!TIP]
    > Double-cliquez à gauche du nom de la table pour créer le gestionnaire d’événements de modification de ligne. Si vous double-cliquez sur le nom de la table, vous pouvez le modifier.

     [!code-vb[VbRaddataValidating#3](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_1.vb)]

### <a name="to-validate-data-when-a-row-changes-c"></a>Pour valider des données en cas de modificationC#d’une ligne ()

1. Ouvrez votre dataset dans le **Concepteur de DataSet**. Pour plus d’informations, consultez [procédure pas à pas : création d’un DataSet dans le concepteur de DataSet](walkthrough-creating-a-dataset-with-the-dataset-designer.md).

2. Double-cliquez sur la barre de titre de la table que vous souhaitez valider. Cette action crée un fichier de classe partielle pour le <xref:System.Data.DataTable>.

    > [!NOTE]
    > Le **Concepteur de DataSet** ne crée pas automatiquement un gestionnaire d’événements pour l’événement <xref:System.Data.DataTable.RowChanging>. Vous devez créer une méthode pour gérer l’événement <xref:System.Data.DataTable.RowChanging> et exécuter du code pour raccorder l’événement dans la méthode d’initialisation de la table.

3. Copiez le code suivant dans la classe partielle :

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
Chaque ligne d’une table de données a une propriété <xref:System.Data.DataRow.RowState%2A> qui effectue le suivi de l’état actuel de cette ligne à l’aide des valeurs de l’énumération <xref:System.Data.DataRowState>. Vous pouvez retourner des lignes modifiées à partir d’un DataSet ou d’une table de données en appelant la méthode `GetChanges` d’un <xref:System.Data.DataSet> ou d’un <xref:System.Data.DataTable>. Vous pouvez vérifier que des modifications existent avant d’appeler `GetChanges` en appelant la méthode <xref:System.Data.DataSet.HasChanges%2A> d’un jeu de données.

> [!NOTE]
> Une fois que vous avez validé les modifications apportées à un DataSet ou une table de données (en appelant la méthode <xref:System.Data.DataSet.AcceptChanges%2A>), la méthode `GetChanges` ne retourne aucune donnée. Si votre application doit traiter les lignes modifiées, vous devez traiter les modifications avant d’appeler la méthode `AcceptChanges`.

L’appel de la méthode <xref:System.Data.DataSet.GetChanges%2A> d’un DataSet ou d’une table de données retourne un nouveau DataSet ou une nouvelle table de données qui contient uniquement les enregistrements qui ont été modifiés. Si vous souhaitez obtenir des enregistrements spécifiques (par exemple, uniquement des nouveaux enregistrements ou des enregistrements modifiés), vous pouvez passer une valeur de l’énumération <xref:System.Data.DataRowState> en tant que paramètre à la méthode `GetChanges`.

Utilisez l’énumération <xref:System.Data.DataRowVersion> pour accéder aux différentes versions d’une ligne (par exemple, les valeurs d’origine qui se trouvaient dans une ligne avant de la traiter).

### <a name="to-get-all-changed-records-from-a-dataset"></a>Pour obtenir tous les enregistrements modifiés d’un DataSet

- Appelez la méthode <xref:System.Data.DataSet.GetChanges%2A> d’un jeu de données.

     L’exemple suivant crée un nouveau jeu de données appelé `changedRecords` et le remplit avec tous les enregistrements modifiés d’un autre jeu de données nommé `dataSet1`.

     [!code-csharp[VbRaddataEditing#14](../data-tools/codesnippet/CSharp/validate-data-in-datasets_2.cs)]
     [!code-vb[VbRaddataEditing#14](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_2.vb)]

### <a name="to-get-all-changed-records-from-a-data-table"></a>Pour obtenir tous les enregistrements modifiés d’une table de données

- Appelez la méthode <xref:System.Data.DataTable.GetChanges%2A> d’un DataTable.

     L’exemple suivant crée une nouvelle table de données appelée `changedRecordsTable` et la remplit avec tous les enregistrements modifiés d’une autre table de données appelée `dataTable1`.

     [!code-csharp[VbRaddataEditing#15](../data-tools/codesnippet/CSharp/validate-data-in-datasets_3.cs)]
     [!code-vb[VbRaddataEditing#15](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_3.vb)]

### <a name="to-get-all-records-that-have-a-specific-row-state"></a>Pour obtenir tous les enregistrements qui ont un état de ligne spécifique

- Appelez la méthode `GetChanges` d’un DataSet ou d’une table de données et transmettez une valeur d’énumération <xref:System.Data.DataRowState> en tant qu’argument.

     L’exemple suivant montre comment créer un jeu de données appelé `addedRecords` et le remplir uniquement avec les enregistrements qui ont été ajoutés au jeu de données `dataSet1`.

     [!code-csharp[VbRaddataEditing#16](../data-tools/codesnippet/CSharp/validate-data-in-datasets_4.cs)]
     [!code-vb[VbRaddataEditing#16](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_4.vb)]

     L’exemple suivant montre comment retourner tous les enregistrements récemment ajoutés à la table `Customers` :

     [!code-csharp[VbRaddataEditing#17](../data-tools/codesnippet/CSharp/validate-data-in-datasets_5.cs)]
     [!code-vb[VbRaddataEditing#17](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_5.vb)]

## <a name="access-the-original-version-of-a-datarow"></a>Accéder à la version d’origine d’un DataRow
Lorsque des modifications sont apportées aux lignes de données, le DataSet conserve à la fois les versions d’origine (<xref:System.Data.DataRowVersion.Original>) et nouvelles (<xref:System.Data.DataRowVersion.Current>) de la ligne. Par exemple, avant d’appeler la méthode `AcceptChanges`, votre application peut accéder aux différentes versions d’un enregistrement (comme défini dans l’énumération <xref:System.Data.DataRowVersion>) et traiter les modifications en conséquence.

> [!NOTE]
> Les différentes versions d’une ligne existent uniquement une fois qu’elle a été modifiée et avant l’appel de la méthode `AcceptChanges`. Une fois la méthode `AcceptChanges` appelée, les versions actuelles et d’origine sont les mêmes.

Le passage de la valeur <xref:System.Data.DataRowVersion> avec l’index de colonne (ou le nom de colonne en tant que chaîne) retourne la valeur de la version de ligne spécifique à cette colonne. La colonne modifiée est identifiée au cours des événements <xref:System.Data.DataTable.ColumnChanging> et <xref:System.Data.DataTable.ColumnChanged>. Il s’agit d’un bon moment pour inspecter les différentes versions de ligne à des fins de validation. Toutefois, si vous avez temporairement suspendu des contraintes, ces événements ne seront pas déclenchés, et vous devrez identifier par programmation les colonnes qui ont changé. Pour ce faire, vous pouvez itérer au sein de la collection <xref:System.Data.DataTable.Columns%2A> et comparer les différentes valeurs de <xref:System.Data.DataRowVersion>.

### <a name="to-get-the-original-version-of-a-record"></a>Pour obtenir la version d’origine d’un enregistrement

- Accédez à la valeur d’une colonne en passant le <xref:System.Data.DataRowVersion> de la ligne que vous souhaitez retourner.

     L’exemple suivant montre comment utiliser une valeur <xref:System.Data.DataRowVersion> pour obtenir la valeur d’origine d’un champ `CompanyName` dans un <xref:System.Data.DataRow>:

     [!code-csharp[VbRaddataEditing#21](../data-tools/codesnippet/CSharp/validate-data-in-datasets_6.cs)]
     [!code-vb[VbRaddataEditing#21](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_6.vb)]

## <a name="access-the-current-version-of-a-datarow"></a>Accéder à la version actuelle d’un DataRow

### <a name="to-get-the-current-version-of-a-record"></a>Pour obtenir la version actuelle d’un enregistrement

- Accédez à la valeur d’une colonne, puis ajoutez un paramètre à l’index qui indique la version d’une ligne que vous souhaitez retourner.

     L’exemple suivant montre comment utiliser une valeur <xref:System.Data.DataRowVersion> pour obtenir la valeur actuelle d’un champ `CompanyName` dans un <xref:System.Data.DataRow>:

     [!code-csharp[VbRaddataEditing#22](../data-tools/codesnippet/CSharp/validate-data-in-datasets_7.cs)]
     [!code-vb[VbRaddataEditing#22](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_7.vb)]

## <a name="see-also"></a>Voir aussi

- [Outils de dataset dans Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
- [Guide pratique pour valider des données dans le contrôle DataGridView Windows Forms](/dotnet/framework/winforms/controls/how-to-validate-data-in-the-windows-forms-datagridview-control)
- [Guide pratique pour afficher des icônes d’erreur pour la validation de formulaire à l’aide du composant ErrorProvider Windows Forms](/dotnet/framework/winforms/controls/display-error-icons-for-form-validation-with-wf-errorprovider)
