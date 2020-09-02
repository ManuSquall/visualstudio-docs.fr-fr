---
title: Ajouter du code aux TableAdapters dans des applications multiniveaux
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- TableAdapters, n-tier applications
- n-tier applications, extending TableAdapters
ms.assetid: dafac00e-df9d-4d4a-95a6-e34b4d099425
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 3ea451ac60de971677ee2f7910b28b334c67dff3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85283097"
---
# <a name="add-code-to-tableadapters-in-n-tier-applications"></a>Ajouter du code aux TableAdapters dans des applications multiniveaux
Vous pouvez étendre les fonctionnalités d’un TableAdapter en créant un fichier de classe partielle pour le TableAdapter et en y ajoutant du code (au lieu d’ajouter du code au fichier *NomGroupeDonnées. DataSet. designer* ). Les classes partielles permettent à du code pour une classe spécifique d’être divisé entre plusieurs fichiers physiques. Pour plus d’informations, consultez [Partial](/dotnet/visual-basic/language-reference/modifiers/partial) ou [Partial (type)](/dotnet/csharp/language-reference/keywords/partial-type).

Le code qui définit un TableAdapter est généré chaque fois que des modifications sont apportées au TableAdapter dans le DataSet. Ce code est également généré lorsque des modifications sont apportées pendant l’exécution d’un assistant qui modifie la configuration du TableAdapter. Pour empêcher la suppression de votre code pendant la régénération d’un TableAdapter, ajoutez du code au fichier de classe partielle du TableAdapter.

Par défaut, après avoir séparé le jeu de données et le code du TableAdapter, le résultat est un fichier de classe discret dans chaque projet. Le projet d’origine a un fichier nommé *NomGroupeDonnées. Designer. vb* (ou *DataSetName.Designer.cs*) qui contient le code du TableAdapter. Le projet désigné dans la propriété de **projet DataSet** a un fichier nommé *NomGroupeDonnées. DataSet. Designer. vb* (ou *DataSetName.DataSet.Designer.cs*) qui contient le code du DataSet.

> [!NOTE]
> Quand vous séparez les datasets et les TableAdapters (en définissant la propriété **Projet DataSet**), les classes DataSet partielles existantes dans le projet ne sont pas déplacées automatiquement. Les classes de DataSet partielles existantes doivent être déplacées manuellement vers le projet de DataSet.

> [!NOTE]
> Le DataSet fournit des fonctionnalités pour générer des <xref:System.Data.DataTable.ColumnChanging> <xref:System.Data.DataTable.RowChanging> gestionnaires d’événements et lorsque la validation est nécessaire. Pour plus d’informations, consultez [Ajouter une validation à un DataSet multicouche](../data-tools/add-validation-to-an-n-tier-dataset.md).

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="to-add-user-code-to-a-tableadapter-in-an-n-tier-application"></a>Pour ajouter du code utilisateur à un TableAdapter dans une application multiniveau

1. Localisez le projet qui contient le fichier *. xsd* .

2. Double-cliquez sur le fichier *. xsd* pour ouvrir le **Concepteur de DataSet**.

3. Cliquez avec le bouton droit sur le TableAdapter auquel vous souhaitez ajouter du code, puis sélectionnez **afficher le code**.

     Une classe partielle est créée et s’ouvre dans l’éditeur de code.

4. Ajoutez du code à l’intérieur de la déclaration de classe partielle.

5. L’exemple suivant indique où ajouter du code à `CustomersTableAdapter` dans le `NorthwindDataSet` :

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

- [Vue d’ensemble des applications de données multicouches](../data-tools/n-tier-data-applications-overview.md)
- [Ajouter du code à des jeux de données dans des applications multicouches](../data-tools/add-code-to-datasets-in-n-tier-applications.md)
- [Créer et configurer des TableAdapters](create-and-configure-tableadapters.md)
- [Vue d’ensemble de la mise à jour hiérarchique](hierarchical-update.md)
