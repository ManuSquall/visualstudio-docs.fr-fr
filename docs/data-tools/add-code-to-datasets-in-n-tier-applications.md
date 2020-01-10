---
title: Ajouter un code à des DataSets dans des applications multiniveau
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- n-tier applications, extending DataSets
ms.assetid: d43c2ccd-4902-43d8-b1a8-d10ca5d3210c
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 3d35ff68144e92af12f2ee6284076118493c6be9
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75587119"
---
# <a name="add-code-to-datasets-in-n-tier-applications"></a>Ajouter un code à des DataSets dans des applications multiniveau

Vous pouvez étendre les fonctionnalités d’un jeu de données en créant un fichier de classe partielle pour le jeu de données et en y ajoutant du code (au lieu d’ajouter du code au fichier *NomGroupeDonnées*. Fichier DataSet. Designer). Les classes partielles permettent à du code pour une classe spécifique d’être divisé entre plusieurs fichiers physiques. Pour plus d’informations, consultez [classes et méthodes](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods) [partielles](/dotnet/visual-basic/language-reference/modifiers/partial) ou partielles.

Le code qui définit un DataSet est généré chaque fois que des modifications sont apportées à la définition du jeu de données (dans le DataSet typé). Ce code est également généré lorsque vous apportez des modifications au cours de l’exécution d’un assistant qui modifie la configuration d’un jeu de données. Pour empêcher la suppression de votre code pendant la régénération d’un DataSet, ajoutez du code au fichier de classe partielle du DataSet.

Par défaut, après avoir séparé le jeu de données et le code du TableAdapter, le résultat est un fichier de classe discret dans chaque projet. Le projet d’origine a un fichier nommé *NomGroupeDonnées. Designer. vb* (ou *DataSetName.Designer.cs*) qui contient le code du TableAdapter. Le projet désigné dans la propriété de **projet DataSet** a un fichier nommé *NomGroupeDonnées. DataSet. Designer. vb* (ou *DataSetName.DataSet.Designer.cs*). Ce fichier contient le code du DataSet.

> [!NOTE]
> Lorsque vous séparez des DataSets et des TableAdapters (en définissant la propriété **DataSet Project** ), les classes DataSet partielles existantes dans le projet ne sont pas déplacées automatiquement. Les classes partielles de DataSet existantes doivent être déplacées manuellement vers le projet de DataSet.

> [!NOTE]
> Quand le code de validation doit être ajouté, le DataSet typé fournit des fonctionnalités permettant de générer des gestionnaires d’événements <xref:System.Data.DataTable.ColumnChanging> et <xref:System.Data.DataTable.RowChanging>. Pour plus d’informations, consultez [Ajouter une validation à un DataSet multicouche](../data-tools/add-validation-to-an-n-tier-dataset.md).

## <a name="to-add-code-to-datasets-in-n-tier-applications"></a>Pour ajouter du code à des jeux de données dans des applications multicouches

1. Localisez le projet qui contient le fichier *. xsd* .

2. Sélectionnez le fichier **. xsd** pour ouvrir le jeu de données.

3. Cliquez avec le bouton droit sur la table de données à laquelle vous souhaitez ajouter du code (nom de la table dans la barre de titre), puis sélectionnez **afficher le code**.

     Une classe partielle est créée et s’ouvre dans l’éditeur de code.

4. Ajoutez du code à l’intérieur de la déclaration de classe partielle.

     L’exemple suivant indique où ajouter du code au CustomersDataTable dans NorthwindDataSet :

    ```vb
    Partial Public Class CustomersDataTable
        ' Add code here to add functionality
        ' to the CustomersDataTable.
    End Class
    ```

    ```csharp
    partial class CustomersDataTable
    {
        // Add code here to add functionality
        // to the CustomersDataTable.
    }
    ```

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble des applications de données multiniveaux](../data-tools/n-tier-data-applications-overview.md)
- [Guide pratique pour ajouter du code aux TableAdapters dans des applications multiniveaux](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md)
- [Créer et configurer des TableAdapters](create-and-configure-tableadapters.md)
- [Vue d’ensemble de la mise à jour hiérarchique](hierarchical-update.md)
- [Outils de jeu de données dans Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
