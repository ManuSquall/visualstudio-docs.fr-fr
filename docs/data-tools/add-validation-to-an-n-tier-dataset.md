---
title: Ajouter la validation à un dataset multiniveau
description: Ajoutez la validation à un jeu de données multicouches dans Visual Studio. Valider les modifications apportées à des colonnes individuelles ou à des lignes entières.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- n-tier applications, validating
- validation [Visual Basic], n-tier data applications
- validating n-tier data applications
ms.assetid: 34ce4db6-09bb-4b46-b435-b2514aac52d3
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 4911cc5ced991389d2c7b03a405c4fe9e28c5cc0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99859357"
---
# <a name="add-validation-to-an-n-tier-dataset"></a>Ajouter la validation à un dataset multiniveau
L’ajout de la validation à un DataSet qui est séparé dans une solution multiniveau est fondamentalement le même que l’ajout d’une validation à un DataSet à fichier unique (un DataSet dans un projet unique). L’emplacement suggéré pour effectuer la validation sur les données est au cours des <xref:System.Data.DataTable.ColumnChanging> événements et/ou <xref:System.Data.DataTable.RowChanging> d’une table de données.

Le DataSet fournit les fonctionnalités permettant de créer des classes partielles auxquelles vous pouvez ajouter du code utilisateur aux événements de modification de colonne et de ligne des tables de données dans le DataSet. Pour plus d’informations sur l’ajout de code à un DataSet dans une solution multicouche, consultez [Ajouter du code aux jeux de données dans des applications multicouches](../data-tools/add-code-to-datasets-in-n-tier-applications.md)et [Ajouter du code aux TableAdapters dans des applications multicouches](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md). Pour plus d’informations sur les classes partielles, consultez [Comment : fractionner une classe en classes partielles (Concepteur de classes)](../ide/class-designer/how-to-split-a-class-into-partial-classes.md) ou [classes et méthodes partielles](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods).

> [!NOTE]
> Lorsque vous séparez des datasets de TableAdapters (en définissant la propriété **DataSet Project** ), les classes DataSet partielles existantes dans le projet ne sont pas déplacées automatiquement. Les classes de DataSet partielles existantes doivent être déplacées manuellement vers le projet de DataSet.

> [!NOTE]
> Le concepteur de DataSet ne crée pas automatiquement de gestionnaires d’événements en C# pour les <xref:System.Data.DataTable.ColumnChanging> <xref:System.Data.DataTable.RowChanging> événements et. Vous devez créer manuellement un gestionnaire d’événements et raccorder le gestionnaire d’événements à l’événement sous-jacent. Les procédures suivantes décrivent comment créer les gestionnaires d’événements requis dans Visual Basic et C#.

## <a name="validate-changes-to-individual-columns"></a>Valider les modifications apportées aux colonnes individuelles
Validez les valeurs dans des colonnes individuelles en gérant l' <xref:System.Data.DataTable.ColumnChanging> événement. L' <xref:System.Data.DataTable.ColumnChanging> événement est déclenché lorsqu’une valeur d’une colonne est modifiée. Créez un gestionnaire d’événements pour l' <xref:System.Data.DataTable.ColumnChanging> événement en double-cliquant sur la colonne souhaitée sur la **Concepteur de DataSet**.

La première fois que vous double-cliquez sur une colonne, le concepteur génère un gestionnaire d’événements pour l' <xref:System.Data.DataTable.ColumnChanging> événement. Une `If...Then` instruction est également créée pour tester la colonne spécifique. Par exemple, le code suivant est généré lorsque vous double-cliquez sur la colonne **DateRequise** de la table Northwind Orders :

```vb
Private Sub OrdersDataTable_ColumnChanging(ByVal sender As System.Object, ByVal e As System.Data.DataColumnChangeEventArgs) Handles Me.ColumnChanging
    If (e.Column.ColumnName = Me.RequiredDateColumn.ColumnName) Then
        ' Add validation code here.
    End If
End Sub
```

> [!NOTE]
> Dans les projets C#, le Concepteur de DataSet crée uniquement des classes partielles pour le DataSet et les tables individuelles dans le DataSet. Le Concepteur de DataSet ne crée pas automatiquement de gestionnaires d’événements pour <xref:System.Data.DataTable.ColumnChanging> les <xref:System.Data.DataTable.RowChanging> événements et en C# comme il le fait dans Visual Basic. Dans les projets C#, vous devez construire manuellement une méthode pour gérer l’événement et raccorder la méthode à l’événement sous-jacent. La procédure suivante fournit les étapes permettant de créer les gestionnaires d’événements requis dans Visual Basic et C#.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

#### <a name="to-add-validation-during-changes-to-individual-column-values"></a>Pour ajouter la validation lors des modifications apportées aux valeurs de colonnes individuelles

1. Ouvrez le jeu de données en double-cliquant sur le fichier *. xsd* dans **Explorateur de solutions**. Pour plus d’informations, consultez [procédure pas à pas : création d’un DataSet dans le concepteur de DataSet](walkthrough-creating-a-dataset-with-the-dataset-designer.md).

2. Double-cliquez sur la colonne que vous souhaitez valider. Cette action crée le <xref:System.Data.DataTable.ColumnChanging> Gestionnaire d’événements.

    > [!NOTE]
    > Le Concepteur de DataSet ne crée pas automatiquement un gestionnaire d’événements pour l’événement C#. Le code nécessaire pour gérer l’événement en C# est inclus dans la section suivante. `SampleColumnChangingEvent` est créé, puis raccordé à l' <xref:System.Data.DataTable.ColumnChanging> événement dans la <xref:System.Data.DataTable.EndInit%2A> méthode.

3. Ajoutez du code pour vérifier que `e.ProposedValue` contient des données qui répondent aux exigences de votre application. Si la valeur proposée est inacceptable, définissez la colonne pour indiquer qu’elle contient une erreur.

     L’exemple de code suivant valide que la colonne **Quantity** contient une valeur supérieure à 0. Si la **quantité** est inférieure ou égale à 0, la colonne est définie sur une erreur. La `Else` clause efface l’erreur si la **quantité** est supérieure à 0. Le code dans le gestionnaire d’événements de modification de colonne doit ressembler à ce qui suit :

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

## <a name="validate-changes-to-whole-rows"></a>Valider les modifications apportées à des lignes entières
Validez les valeurs dans les lignes entières en gérant l' <xref:System.Data.DataTable.RowChanging> événement. L' <xref:System.Data.DataTable.RowChanging> événement est déclenché lorsque les valeurs de toutes les colonnes sont validées. Il est nécessaire de valider dans l' <xref:System.Data.DataTable.RowChanging> événement lorsque la valeur d’une colonne repose sur la valeur d’une autre colonne. Par exemple, considérez OrderDate et DateRequise dans la table Orders de Northwind.

Lorsque des commandes sont entrées, la validation garantit qu’une commande n’est pas entrée avec une commande DateRequise qui est le ou avant la date de commande. Dans cet exemple, les valeurs des colonnes DateRequise et OrderDate doivent être comparées, de sorte que la validation d’une modification de colonne individuelle n’a aucun sens.

Créez un gestionnaire d’événements pour l' <xref:System.Data.DataTable.RowChanging> événement en double-cliquant sur le nom de la table dans la barre de titre de la table sur le **Concepteur de DataSet**.

#### <a name="to-add-validation-during-changes-to-whole-rows"></a>Pour ajouter la validation lors des modifications apportées à des lignes entières

1. Ouvrez le jeu de données en double-cliquant sur le fichier *. xsd* dans **Explorateur de solutions**. Pour plus d’informations, consultez [procédure pas à pas : création d’un DataSet dans le concepteur de DataSet](walkthrough-creating-a-dataset-with-the-dataset-designer.md).

2. Double-cliquez sur la barre de titre de la table de données sur le concepteur.

     Une classe partielle est créée à l’aide d’un `RowChanging` Gestionnaire d’événements et s’ouvre dans l’éditeur de code.

    > [!NOTE]
    > Le Concepteur de DataSet ne crée pas automatiquement un gestionnaire d’événements pour l' <xref:System.Data.DataTable.RowChanging> événement dans les projets C#. Vous devez créer une méthode pour gérer l' <xref:System.Data.DataTable.RowChanging> événement et exécuter le code, puis raccorder l’événement dans la méthode d’initialisation de la table.

3. Ajoutez du code utilisateur à l’intérieur de la déclaration de classe partielle.

4. Le code suivant indique où ajouter le code utilisateur à valider pendant l' <xref:System.Data.DataTable.RowChanging> événement. L’exemple C# comprend également du code pour raccorder la méthode de gestionnaire d’événements à l' `OrdersRowChanging` événement.

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

- [Vue d’ensemble des applications de données multicouches](../data-tools/n-tier-data-applications-overview.md)
- [Procédure pas à pas : création d’une application de données multicouches](../data-tools/walkthrough-creating-an-n-tier-data-application.md)
- [Valider les données dans des datasets](../data-tools/validate-data-in-datasets.md)
