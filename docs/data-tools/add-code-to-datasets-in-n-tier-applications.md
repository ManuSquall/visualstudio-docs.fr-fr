---
title: Ajouter du code à des datasets dans des applications multiniveaux
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- n-tier applications, extending datasets
ms.assetid: d43c2ccd-4902-43d8-b1a8-d10ca5d3210c
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: c2d1784e498cb856cc388b8e7f26dd57f978e79f
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53927387"
---
# <a name="add-code-to-datasets-in-n-tier-applications"></a>Ajouter du code à des datasets dans des applications multiniveaux
Vous pouvez étendre les fonctionnalités d’un jeu de données en créant un fichier de classe partielle pour le jeu de données et en ajoutant du code (au lieu d’ajouter du code pour le *DatasetName*. Fichier Dataset.Designer). Classes partielles permettent au code pour une classe spécifique être réparti entre plusieurs fichiers physiques. Pour plus d’informations, consultez [partielle](/dotnet/visual-basic/language-reference/modifiers/partial) ou [classes et méthodes partielles](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods).

Le code qui définit un jeu de données est généré chaque fois les modifications sont apportées à la définition de jeu de données (dans le dataset typé). Ce code est également généré lorsque vous apportez des modifications pendant l’exécution d’un Assistant qui modifie la configuration d’un jeu de données. Pour empêcher que votre code en cours de suppression pendant la régénération d’un jeu de données, ajoutez le code au fichier de classe partielle du jeu de données.

Par défaut, une fois que vous séparez le jeu de données et le code du TableAdapter, le résultat est un fichier de classe discret dans chaque projet. Le projet d’origine a un fichier nommé *NomGroupeDonnées.Designer.vb* (ou *NomGroupeDonnées.Designer.cs*) qui contient le code du TableAdapter. Le projet désigné dans la **Dataset Project** propriété dispose d’un fichier nommé *NomGroupeDonnées.DataSet.Designer.vb* (ou *NomGroupeDonnées.DataSet.Designer.cs*) . Ce fichier contient le code de jeu de données.

> [!NOTE]
>  Quand vous séparez les datasets et les TableAdapters (en définissant le **DataSet Project** propriété), les classes dataset partielles existantes dans le projet ne sont pas déplacées automatiquement. Classes dataset partielles existantes doivent être déplacés manuellement vers le projet dataset.

> [!NOTE]
>  Lorsque le code de validation doit être ajouté, le dataset typé fournit des fonctionnalités de génération <xref:System.Data.DataTable.ColumnChanging> et <xref:System.Data.DataTable.RowChanging> gestionnaires d’événements. Pour plus d’informations, consultez [ajouter la validation à un jeu de données multicouches](../data-tools/add-validation-to-an-n-tier-dataset.md).

## <a name="to-add-code-to-datasets-in-n-tier-applications"></a>Pour ajouter du code pour les jeux de données dans les applications multicouches

1.  Recherchez le projet qui contient le *.xsd* fichier.

2.  Sélectionnez le **.xsd** fichier à ouvrir le jeu de données.

3.  Avec le bouton droit de la table de données à laquelle vous souhaitez ajouter du code (le nom de table dans la barre de titre), puis sélectionnez **afficher le Code**.

     Une classe partielle est créée et s’ouvre dans l’éditeur de Code.

4.  Ajoutez le code à l’intérieur de la déclaration de classe partielle.

     L’exemple suivant indique où ajouter le code au CustomersDataTable dans NorthwindDataSet :

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
- [Outils de dataset dans Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)