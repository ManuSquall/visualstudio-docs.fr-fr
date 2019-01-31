---
title: Ajouter la validation à un dataset multiniveau
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- n-tier applications, validating
- validation [Visual Basic], n-tier data applications
- validating n-tier data applications
ms.assetid: 34ce4db6-09bb-4b46-b435-b2514aac52d3
author: gewarren
ms.author: gewarren
manager: jillfra
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: 25c80b145db83053edcbdb8f03f4eb703e201974
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54957505"
---
# <a name="add-validation-to-an-n-tier-dataset"></a>Ajouter la validation à un dataset multiniveau
Ajout d’une validation à un dataset qui est divisé en une solution multicouche est fondamentalement identique à l’ajout d’une validation à un jeu de données à fichier unique (un jeu de données dans un seul projet). Pour exécuter la validation sur les données est proposé pendant la <xref:System.Data.DataTable.ColumnChanging> et/ou <xref:System.Data.DataTable.RowChanging> événements d’une table de données.

 Le jeu de données fournit les fonctionnalités pour créer des classes partielles à laquelle vous pouvez ajouter le code utilisateur aux événements de modification de colonne et de ligne des tables de données dans le jeu de données. Pour plus d’informations sur l’ajout de code à un jeu de données dans une solution multicouche, consultez [ajouter du code à des jeux de données dans les applications multicouches](../data-tools/add-code-to-datasets-in-n-tier-applications.md), et [ajouter du code aux TableAdapters dans des applications multicouches](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md). Pour plus d’informations sur les classes partielles, consultez [Comment : Fractionner une classe en classes partielles (Concepteur de classes)](../ide/class-designer/how-to-split-a-class-into-partial-classes.md) ou [classes et méthodes partielles](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods).

> [!NOTE]
>  Quand vous séparez les jeux de données à partir de TableAdapters (en définissant le **DataSet Project** propriété), les classes dataset partielles existantes dans le projet ne sont pas déplacées automatiquement. Les classes dataset partielles existantes doivent être déplacés manuellement dans le projet dataset.

> [!NOTE]
>  Le Concepteur de dataset ne crée pas automatiquement de gestionnaires d’événements dans C# pour le <xref:System.Data.DataTable.ColumnChanging> et <xref:System.Data.DataTable.RowChanging> événements. Vous devez manuellement créer un gestionnaire d’événements et raccorder le Gestionnaire d’événements à l’événement sous-jacent. Les procédures suivantes décrivent comment créer les gestionnaires d’événements requise dans les deux Visual Basic et C#.

## <a name="validate-changes-to-individual-columns"></a>Valider les modifications apportées à des colonnes individuelles
 Valider les valeurs dans des colonnes individuelles en gérant la <xref:System.Data.DataTable.ColumnChanging> événement. Le <xref:System.Data.DataTable.ColumnChanging> événement est déclenché lorsqu’une valeur dans une colonne est modifiée. Créer un gestionnaire d’événements pour le <xref:System.Data.DataTable.ColumnChanging> événement en double-cliquant sur la colonne souhaitée sur le **Concepteur de Dataset**.

 La première fois que vous double-cliquez sur une colonne, le concepteur génère un gestionnaire d’événements pour le <xref:System.Data.DataTable.ColumnChanging> événement. Un `If...Then` est également créée qui teste la colonne spécifique. Par exemple, le code suivant est généré lorsque vous double-cliquez sur le **RequiredDate** colonne sur la table Northwind Orders :

```vb
Private Sub OrdersDataTable_ColumnChanging(ByVal sender As System.Object, ByVal e As System.Data.DataColumnChangeEventArgs) Handles Me.ColumnChanging
    If (e.Column.ColumnName = Me.RequiredDateColumn.ColumnName) Then
        ' Add validation code here.
    End If
End Sub
```

> [!NOTE]
>  Dans C# projets, le Concepteur de Dataset crée uniquement des classes partielles pour le jeu de données et des tables individuelles dans le jeu de données. Le Concepteur de Dataset ne crée pas automatiquement de gestionnaires d’événements pour le <xref:System.Data.DataTable.ColumnChanging> et <xref:System.Data.DataTable.RowChanging> événements dans C# comme il le fait en Visual Basic. Dans C# projets, vous devez construire manuellement une méthode pour gérer l’événement et raccorder la méthode à l’événement sous-jacent. La procédure suivante fournit les étapes pour créer les gestionnaires d’événements requise dans les deux Visual Basic et C#.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

#### <a name="to-add-validation-during-changes-to-individual-column-values"></a>Pour ajouter la validation pendant les modifications apportées aux valeurs de colonne individuels

1.  Ouvrez le jeu de données en double-cliquant sur le *.xsd* fichier **l’Explorateur de solutions**. Pour plus d’informations, consultez [Procédure pas à pas : Création d’un jeu de données dans le Concepteur de Dataset](walkthrough-creating-a-dataset-with-the-dataset-designer.md).

2.  Double-cliquez sur la colonne que vous souhaitez valider. Cette action crée le <xref:System.Data.DataTable.ColumnChanging> Gestionnaire d’événements.

    > [!NOTE]
    >  Le Concepteur de Dataset ne crée pas automatiquement un gestionnaire d’événements pour le C# événement. Le code qui est nécessaire pour gérer l’événement dans C# est inclus dans la section suivante. `SampleColumnChangingEvent` est créé et puis raccordé à le <xref:System.Data.DataTable.ColumnChanging> événement dans le <xref:System.Data.DataTable.EndInit%2A> (méthode).

3.  Ajouter du code pour vérifier que `e.ProposedValue` contient des données qui répondent aux exigences de votre application. Si la valeur proposée est inacceptable, définissez la colonne pour indiquer qu’il contient une erreur.

     L’exemple de code suivant valide le fait que le **quantité** colonne contient une valeur supérieure à 0. Si **quantité** est inférieure ou égale à 0, la colonne est définie sur une erreur. Le `Else` clause efface l’erreur si **quantité** est supérieure à 0. Le code dans le Gestionnaire d’événements de modification de colonne doit ressembler à ce qui suit :

    ```vb
    If (e.Column.ColumnName = Me.QuantityColumn.ColumnName) Then
        If CType(e.ProposedValue, Short) <= 0 Then
            e.Row.SetColumnError(e.Column, "Quantity must be greater than 0")
        Else
            e.Row.SetColumnError(e.Column, "")
        End If
    End If
    ```
    ```csharp
    // Add this code to the DataTable partial class.

    public override void EndInit()
    {
        base.EndInit();
        // Hook up the ColumnChanging event
        // to call the SampleColumnChangingEvent method.
        ColumnChanging += SampleColumnChangingEvent;
    }

    public void SampleColumnChangingEvent(object sender, System.Data.DataColumnChangeEventArgs e)
    {
        if (e.Column.ColumnName == QuantityColumn.ColumnName)
        {
            if ((short)e.ProposedValue <= 0)
            {
                e.Row.SetColumnError("Quantity", "Quantity must be greater than 0");
            }
            else
            {
                e.Row.SetColumnError("Quantity", "");
            }
        }
    }
    ```

## <a name="validate-changes-to-whole-rows"></a>Valider les modifications apportées aux lignes entières
 Valider les valeurs dans les lignes entières en gérant la <xref:System.Data.DataTable.RowChanging> événement. Le <xref:System.Data.DataTable.RowChanging> événement est déclenché lorsque les valeurs de toutes les colonnes sont validées. Il est nécessaire de valider dans le <xref:System.Data.DataTable.RowChanging> événement lorsque la valeur dans une colonne s’appuie sur la valeur dans une autre colonne. Par exemple, considérez OrderDate et RequiredDate dans la table Orders de Northwind.

 Lorsque les commandes sont entrées, la validation permet de s’assurer qu’une commande n’est pas entrée avec une valeur RequiredDate qui est l’ou avant la date de commande. Dans cet exemple, les valeurs des colonnes RequiredDate et OrderDate doivent à comparer, afin de valider une modification de colonne individuelle n’est pas pertinent.

 Créer un gestionnaire d’événements pour le <xref:System.Data.DataTable.RowChanging> événement en double-cliquant sur le nom de table dans la barre de titre de la table sur le **Concepteur de Dataset**.

#### <a name="to-add-validation-during-changes-to-whole-rows"></a>Pour ajouter la validation pendant la modification des lignes entières

1.  Ouvrez le jeu de données en double-cliquant sur le *.xsd* fichier **l’Explorateur de solutions**. Pour plus d’informations, consultez [Procédure pas à pas : Création d’un jeu de données dans le Concepteur de Dataset](walkthrough-creating-a-dataset-with-the-dataset-designer.md).

2.  Double-cliquez sur la barre de titre de la table de données sur le concepteur.

     Une classe partielle est créée avec un `RowChanging` Gestionnaire d’événements et s’ouvre dans l’éditeur de Code.

    > [!NOTE]
    >  Le Concepteur de Dataset ne crée pas automatiquement un gestionnaire d’événements pour le <xref:System.Data.DataTable.RowChanging> événement dans C# projets. Vous devez créer une méthode pour gérer la <xref:System.Data.DataTable.RowChanging> événements et exécuter du code puis de raccorder l’événement dans la méthode d’initialisation de la table.

3.  Ajoutez le code de l’utilisateur à l’intérieur de la déclaration de classe partielle.

4.  Le code suivant indique où ajouter le code utilisateur pour valider lors de la <xref:System.Data.DataTable.RowChanging> événement. Le C# exemple inclut également le code pour la méthode de gestionnaire d’événements de raccordement jusqu'à la `OrdersRowChanging` événement.

    ```vb
    Partial Class OrdersDataTable
        Private Sub OrdersDataTable_OrdersRowChanging(ByVal sender As System.Object, ByVal e As OrdersRowChangeEvent) Handles Me.OrdersRowChanging
            ' Add logic to validate columns here.
            If e.Row.RequiredDate <= e.Row.OrderDate Then
                ' Set the RowError if validation fails.
                e.Row.RowError = "Required Date cannot be on or before the OrderDate"
            Else
                ' Clear the RowError when validation passes.
                e.Row.RowError = ""
            End If
        End Sub
    End Class
    ```
    ```csharp
    partial class OrdersDataTable
    {
        public override void EndInit()
        {
            base.EndInit();
            // Hook up the event to the
            // RowChangingEvent method.
            OrdersRowChanging += RowChangingEvent;
        }

        public void RowChangingEvent(object sender, OrdersRowChangeEvent e)
        {
            // Perform the validation logic.
            if (e.Row.RequiredDate <= e.Row.OrderDate)
            {
                // Set the row to an error when validation fails.
                e.Row.RowError = "Required Date cannot be on or before the OrderDate";
            }
            else
            {
                // Clear the RowError if validation passes.
                e.Row.RowError = "";
            }
        }
    }
    ```

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble des applications de données multiniveaux](../data-tools/n-tier-data-applications-overview.md)
- [Procédure pas à pas : Création d’une application de données multiniveaux](../data-tools/walkthrough-creating-an-n-tier-data-application.md)
- [Valider les données dans des datasets](../data-tools/validate-data-in-datasets.md)