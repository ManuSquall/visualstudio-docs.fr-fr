---
title: Ajouter la validation à un jeu de données multiniveau | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- n-tier applications, validating
- validation [Visual Basic], n-tier data applications
- validating n-tier data applications
ms.assetid: 34ce4db6-09bb-4b46-b435-b2514aac52d3
caps.latest.revision: 27
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b03f1e85140d62d84ae7c706a9bfee6a7c515abb
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72673056"
---
# <a name="add-validation-to-an-n-tier-dataset"></a>Ajouter la validation à un dataset multiniveau
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L’ajout de la validation à un DataSet qui est séparé dans une solution multiniveau est fondamentalement le même que l’ajout d’une validation à un DataSet à fichier unique (un DataSet dans un projet unique). L’emplacement suggéré pour effectuer la validation sur les données est au cours des événements de <xref:System.Data.DataTable.ColumnChanging> et/ou de <xref:System.Data.DataTable.RowChanging> d’une table de données.

Le concepteur de DataSet fournit les fonctionnalités permettant de créer des classes partielles auxquelles vous pouvez ajouter du code utilisateur aux événements de modification de colonne et de ligne des tables de données du DataSet. Pour plus d’informations sur l’ajout de code à un DataSet dans une solution multicouche, consultez [Ajouter du code aux jeux de données dans des applications multicouches](../data-tools/add-code-to-datasets-in-n-tier-applications.md)et [Ajouter du code aux TableAdapters dans des applications multicouches](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md). Pour plus d’informations sur les classes partielles, consultez [Comment : fractionner une classe en classes partielles (Concepteur de classes)](../ide/how-to-split-a-class-into-partial-classes-class-designer.md) ou [classes et méthodes partielles](https://msdn.microsoft.com/library/804cecb7-62db-4f97-a99f-60975bd59fa1).

> [!NOTE]
> Lorsque vous séparez des datasets de TableAdapters (en définissant la propriété **DataSet Project** ), les classes DataSet partielles existantes dans le projet ne sont pas déplacées automatiquement. Les classes partielles de DataSet existantes doivent être déplacées manuellement vers le projet de DataSet.

> [!NOTE]
> Le Concepteur de DataSet ne crée pas automatiquement de gestionnaires d’événements C# dans pour les événements <xref:System.Data.DataTable.ColumnChanging> et <xref:System.Data.DataTable.RowChanging>. Vous devez créer manuellement un gestionnaire d’événements et raccorder le gestionnaire d’événements à l’événement sous-jacent. Les procédures suivantes décrivent comment créer les gestionnaires d’événements requis dans Visual Basic et C#.

## <a name="validatechanges-to-individual-columns"></a>ValidateChanges à des colonnes individuelles
 Validez les valeurs dans des colonnes individuelles en gérant l’événement <xref:System.Data.DataTable.ColumnChanging>. L’événement <xref:System.Data.DataTable.ColumnChanging> est déclenché lors de la modification d’une valeur dans une colonne. Créez un gestionnaire d’événements pour l’événement <xref:System.Data.DataTable.ColumnChanging> en double-cliquant sur la colonne souhaitée sur le jeu de données.

 La première fois que vous double-cliquez sur une colonne, le concepteur génère un gestionnaire d’événements pour l’événement <xref:System.Data.DataTable.ColumnChanging>. Une instruction `If…Then` est également créée pour tester la colonne spécifique. Par exemple, le code suivant est généré lorsque vous double-cliquez sur la colonne DateRequise de la table Northwind Orders :

```vb
Private Sub OrdersDataTable_ColumnChanging(ByVal sender As System.Object, ByVal e As System.Data.DataColumnChangeEventArgs) Handles Me.ColumnChanging
    If (e.Column.ColumnName = Me.RequiredDateColumn.ColumnName) Then
        ' Add validation code here.
    End If
End Sub
```

> [!NOTE]
> Dans C# les projets, le concepteur de DataSet crée uniquement des classes partielles pour le jeu de données et les tables individuelles dans le DataSet. Le Concepteur de DataSet ne crée pas automatiquement de gestionnaires d’événements pour les événements <xref:System.Data.DataTable.ColumnChanging> et <xref:System.Data.DataTable.RowChanging> C# dans comme dans Visual Basic. Dans C# les projets, vous devez construire manuellement une méthode pour gérer l’événement et raccorder la méthode à l’événement sous-jacent. La procédure suivante décrit les étapes de création des gestionnaires d’événements requis dans Visual Basic et C#.

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

#### <a name="to-add-validation-during-changes-to-individual-column-values"></a>Pour ajouter la validation lors des modifications apportées aux valeurs de colonnes individuelles

1. Ouvrez le jeu de données dans le concepteur en double-cliquant sur le fichier **. xsd** dans **Explorateur de solutions**. Pour plus d’informations, consultez [Comment : ouvrir un DataSet dans le concepteur de DataSet](https://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).

2. Double-cliquez sur la colonne que vous souhaitez valider. Cette action crée le gestionnaire d’événements <xref:System.Data.DataTable.ColumnChanging>.

    > [!NOTE]
    > Le Concepteur de DataSet ne crée pas automatiquement un gestionnaire d’événements pour C# l’événement. Le code nécessaire pour gérer l’événement dans C# est inclus dans la section suivante. `SampleColumnChangingEvent` est créé, puis raccordé à l’événement <xref:System.Data.DataTable.ColumnChanging> dans la méthode <xref:System.Data.DataTable.EndInit%2A>.

3. Ajoutez du code pour vérifier que `e.ProposedValue` contient des données qui répondent aux exigences de votre application. Si la valeur proposée est inacceptable, définissez la colonne pour indiquer qu’elle contient une erreur.

     L’exemple de code suivant valide que la colonne **Quantity** contient plus de 0. Si la **quantité** est inférieure ou égale à 0, la colonne est définie sur une erreur. La clause `Else` efface l’erreur si la **quantité** est supérieure à 0. Le code dans le gestionnaire d’événements de modification de colonne doit ressembler à ce qui suit :

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
    // C#
    // Add this code to the DataTable
    // partial class.

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

## <a name="validatechanges-to-whole-rows"></a>ValidateChanges à lignes entières
 Validez les valeurs dans les lignes entières en gérant l’événement <xref:System.Data.DataTable.RowChanging>. L’événement <xref:System.Data.DataTable.RowChanging> est déclenché lorsque les valeurs de toutes les colonnes sont validées. Il est nécessaire de valider dans l’événement <xref:System.Data.DataTable.RowChanging> lorsque la valeur d’une colonne s’appuie sur la valeur d’une autre colonne. Par exemple, considérez OrderDate et DateRequise dans la table Orders de Northwind.

 Lorsque des commandes sont entrées, la validation garantit qu’une commande n’est pas entrée avec une commande DateRequise qui est le ou avant la date de commande. Dans cet exemple, les valeurs des colonnes DateRequise et OrderDate doivent être comparées, de sorte que la validation d’une modification de colonne individuelle n’a aucun sens.

 Créez un gestionnaire d’événements pour l’événement <xref:System.Data.DataTable.RowChanging> en double-cliquant sur le nom de la table dans la barre de titre de la table.

#### <a name="to-add-validation-during-changes-to-whole-rows"></a>Pour ajouter la validation lors des modifications apportées à des lignes entières

1. Ouvrez le jeu de données dans le concepteur en double-cliquant sur le fichier **. xsd** dans **Explorateur de solutions**. Pour plus d’informations, consultez [Comment : ouvrir un DataSet dans le concepteur de DataSet](https://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).

2. Double-cliquez sur la barre de titre de la table de données sur le concepteur.

     Une classe partielle est créée avec un gestionnaire d’événements `RowChanging` et s’ouvre dans l’éditeur de code.

    > [!NOTE]
    > Le Concepteur de DataSet ne crée pas automatiquement un gestionnaire d’événements pour l’événement <xref:System.Data.DataTable.RowChanging> C# dans les projets. Vous devez créer une méthode pour gérer l’événement <xref:System.Data.DataTable.RowChanging> et exécuter du code pour raccorder l’événement dans la méthode d’initialisation de la table.

3. Ajoutez du code utilisateur à l’intérieur de la déclaration de classe partielle.

4. Le code suivant indique où ajouter le code utilisateur à valider au cours de l’événement <xref:System.Data.DataTable.RowChanging> pour Visual Basic :

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

5. Le code suivant montre comment créer le gestionnaire d’événements `RowChanging` et où ajouter le code utilisateur à valider pendant l’événement <xref:System.Data.DataTable.RowChanging> pour C#:

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
 [Présentation des applications de données multicouches](../data-tools/n-tier-data-applications-overview.md) [procédure pas à pas : création d’une application de données multicouche](../data-tools/walkthrough-creating-an-n-tier-data-application.md) [valider les données dans les datasets](../data-tools/validate-data-in-datasets.md)
