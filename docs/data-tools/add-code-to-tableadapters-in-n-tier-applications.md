---
title: Ajouter du code aux TableAdapters dans des applications multiniveaux
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
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 6454eb53bf6d171e469a4cf2758e0e10a76eab6e
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60066115"
---
# <a name="add-code-to-tableadapters-in-n-tier-applications"></a>Ajouter du code aux TableAdapters dans des applications multiniveaux
Vous pouvez étendre les fonctionnalités d’un TableAdapter en créant un fichier de classe partielle du TableAdapter et en ajoutant du code (au lieu d’ajouter du code pour le *DatasetName.DataSet.Designer* fichier). Classes partielles permettent au code pour une classe spécifique être réparti entre plusieurs fichiers physiques. Pour plus d’informations, consultez [partielle](/dotnet/visual-basic/language-reference/modifiers/partial) ou [partial (Type)](/dotnet/csharp/language-reference/keywords/partial-type).

Le code qui définit un TableAdapter est généré chaque fois les modifications sont apportées au TableAdapter dans le jeu de données. Ce code est également généré lorsque des modifications sont apportées pendant l’exécution d’un Assistant qui modifie la configuration du TableAdapter. Pour empêcher que votre code en cours de suppression pendant la régénération d’un TableAdapter, ajoutez le code au fichier de classe partielle du TableAdapter.

Par défaut, une fois que vous séparez le jeu de données et le code du TableAdapter, le résultat est un fichier de classe discret dans chaque projet. Le projet d’origine a un fichier nommé *NomGroupeDonnées.Designer.vb* (ou *NomGroupeDonnées.Designer.cs*) qui contient le code du TableAdapter. Le projet désigné dans la **Dataset Project** propriété dispose d’un fichier nommé *NomGroupeDonnées.DataSet.Designer.vb* (ou *NomGroupeDonnées.DataSet.Designer.cs*) qui contient le code de jeu de données.

> [!NOTE]
>  Quand vous séparez les datasets et les TableAdapters (en définissant la propriété **Projet DataSet**), les classes DataSet partielles existantes dans le projet ne sont pas déplacées automatiquement. Les classes dataset partielles existantes doivent être déplacés manuellement dans le projet dataset.

> [!NOTE]
> Le jeu de données fournit des fonctionnalités de génération <xref:System.Data.DataTable.ColumnChanging> et <xref:System.Data.DataTable.RowChanging> gestionnaires d’événements lorsque la validation est nécessaire. Pour plus d’informations, consultez [ajouter la validation à un jeu de données multicouches](../data-tools/add-validation-to-an-n-tier-dataset.md).

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="to-add-user-code-to-a-tableadapter-in-an-n-tier-application"></a>Pour ajouter du code de l’utilisateur à un TableAdapter dans une architecture multiniveau

1. Recherchez le projet qui contient le *.xsd* fichier.

2. Double-cliquez sur le *.xsd* fichier à ouvrir le **Concepteur de Dataset**.

3. Cliquez sur le TableAdapter que vous souhaitez ajouter le code et sélectionnez **afficher le Code**.

     Une classe partielle est créée et s’ouvre dans l’éditeur de Code.

4. Ajoutez le code à l’intérieur de la déclaration de classe partielle.

5. L’exemple suivant montre où ajouter le code pour le `CustomersTableAdapter` dans le `NorthwindDataSet`:

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
