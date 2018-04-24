---
title: Ajoutez du code aux TableAdapters dans des applications multicouches
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- TableAdapters, n-tier applications
- n-tier applications, extending TableAdapters
ms.assetid: dafac00e-df9d-4d4a-95a6-e34b4d099425
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 165d0e76eb030d8a173761733245c993115ed315
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2018
---
# <a name="add-code-to-tableadapters-in-n-tier-applications"></a>Ajoutez du code aux TableAdapters dans des applications multicouches
Vous pouvez étendre les fonctionnalités d’un TableAdapter en ajoutant du code et de création d’un fichier de classe partielle pour le TableAdapter (au lieu d’ajouter du code pour le *DatasetName*. Fichier DataSet.Designer). Classes partielles permettent au code pour une classe spécifique être réparti entre plusieurs fichiers physiques. Pour plus d’informations, consultez [partielle](/dotnet/visual-basic/language-reference/modifiers/partial) ou [partiel, Type](/dotnet/csharp/language-reference/keywords/partial-type).

Le code qui définit un TableAdapter est généré chaque fois les modifications sont apportées au TableAdapter dans le jeu de données. Ce code est également généré lorsque des modifications sont apportées pendant l’exécution d’un Assistant qui modifie la configuration du TableAdapter. Pour empêcher votre code d’être supprimé pendant la régénération d’un TableAdapter, ajoutez le code au fichier de classe partielle du TableAdapter.

Par défaut, une fois que vous séparez le dataset et le code du TableAdapter, le résultat est un fichier de classe discret dans chaque projet. Le projet d’origine a un fichier nommé *DatasetName*. Designer.vb (ou *DatasetName*. Designer.cs) qui contient le code du TableAdapter. Le projet désigné dans la **projet Dataset** propriété dispose d’un fichier nommé *DatasetName*. DataSet.Designer.vb (ou *DatasetName*. (DataSet.Designer.cs) qui contient le code du jeu de données.

> [!NOTE]
>  Quand vous séparez les datasets et les TableAdapters (en définissant le **projet DataSet** propriété), les classes dataset partielles existantes dans le projet ne seront pas être déplacées automatiquement. Les classes dataset partielles existantes doivent être déplacés manuellement vers le projet dataset.

> [!NOTE]
> Le jeu de données fournit les fonctionnalités de génération <xref:System.Data.DataTable.ColumnChanging> et <xref:System.Data.DataTable.RowChanging> gestionnaires d’événements lorsque la validation est nécessaire. Pour plus d’informations, consultez [ajouter une validation à un dataset MULTICOUCHE](../data-tools/add-validation-to-an-n-tier-dataset.md).

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="to-add-user-code-to-a-tableadapter-in-an-n-tier-application"></a>Pour ajouter du code de l’utilisateur à un TableAdapter dans une application multicouche

1.  Recherchez le projet qui contient le fichier .xsd.

2.  Double-cliquez sur le **.xsd** fichier à ouvrir le **Concepteur de Dataset**.

3.  Cliquez sur le TableAdapter que vous souhaitez ajouter le code et sélectionnez **afficher le Code**.

     Une classe partielle est créée et s’ouvre dans l’éditeur de Code.

4.  Ajoutez du code à l’intérieur de la déclaration de classe partielle.

5.  L’exemple suivant montre où ajouter le code pour le `CustomersTableAdapter` dans le `NorthwindDataSet`:

    ```vb
    Partial Public Class CustomersTableAdapter
        ' Add code here to add functionality
        ' to the CustomersTableAdapter.
    End Class
    ```

    ```csharp
    public partial class CustomersTableAdapter
    {
        // Add code here to add functionality
        // to the CustomersTableAdapter.
    }
    ```

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble des applications de données multiniveaux](../data-tools/n-tier-data-applications-overview.md)
- [Guide pratique pour ajouter du code à des datasets dans des applications multiniveaux](../data-tools/add-code-to-datasets-in-n-tier-applications.md)
- [Créer et configurer des TableAdapters](create-and-configure-tableadapters.md)
- [Vue d’ensemble de la mise à jour hiérarchique](hierarchical-update.md)
