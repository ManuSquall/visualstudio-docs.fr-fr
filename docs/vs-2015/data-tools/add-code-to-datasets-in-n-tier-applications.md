---
title: Ajouter du code à des jeux de données dans des applications multicouches | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- n-tier applications, extending datasets
ms.assetid: d43c2ccd-4902-43d8-b1a8-d10ca5d3210c
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: aed37ee9cdd8c221fcfb114db426a6286ee8ad6f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72673116"
---
# <a name="add-code-to-datasets-in-n-tier-applications"></a>Ajouter du code à des datasets dans des applications multiniveaux
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez étendre les fonctionnalités d’un jeu de données en créant un fichier de classe partielle pour le jeu de données et en y ajoutant du code (au lieu d’ajouter du code au fichier *NomGroupeDonnées*. Fichier DataSet. Designer). Les classes partielles permettent à du code pour une classe spécifique d’être divisé entre plusieurs fichiers physiques. Pour plus d’informations, consultez [classes et méthodes](https://msdn.microsoft.com/library/804cecb7-62db-4f97-a99f-60975bd59fa1) [partielles](https://msdn.microsoft.com/library/7adaef80-f435-46e1-970a-269fff63b448) ou partielles.

Le code qui définit un DataSet est généré chaque fois que des modifications sont apportées à la définition du jeu de données. Ce code est également généré lorsque vous apportez des modifications au cours de l’exécution d’un assistant qui modifie la configuration d’un jeu de données. Pour empêcher la suppression de votre code pendant la régénération d’un DataSet, ajoutez du code au fichier de classe partielle du DataSet.

Par défaut, après avoir séparé le jeu de données et le `TableAdapter` code, le résultat est un fichier de classe discret dans chaque projet. Le projet d’origine a un nom de fichier *NomGroupeDonnées*. Designer. vb (ou *NomGroupeDonnées*. Designer.cs) qui contient le `TableAdapter` code. Le projet désigné dans la propriété de **projet DataSet** a un fichier nommé *NomGroupeDonnées*. DataSet. Designer. vb (ou *NomGroupeDonnées*. DataSet.Designer.cs). Ce fichier contient le code du DataSet.

> [!NOTE]
> Lorsque vous séparez des DataSets et des `TableAdapter` s (en définissant la propriété **DataSet Project** ), les classes DataSet partielles existantes dans le projet ne sont pas déplacées automatiquement. Les classes partielles de DataSet existantes doivent être déplacées manuellement vers le projet de DataSet.

> [!NOTE]
> Quand le code de validation doit être ajouté, le concepteur de DataSet fournit des fonctionnalités pour générer des <xref:System.Data.DataTable.ColumnChanging> <xref:System.Data.DataTable.RowChanging> gestionnaires d’événements et. Pour plus d’informations, consultez [Ajouter une validation à un DataSet multicouche](../data-tools/add-validation-to-an-n-tier-dataset.md).

## <a name="add-code-to-datasets-in-n-tier-applications"></a>Ajouter du code à des datasets dans des applications multiniveaux

1. Recherchez le projet qui contient le fichier. xsd (le DataSet).

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

- [Vue d’ensemble des applications de données multicouches](../data-tools/n-tier-data-applications-overview.md)
- [Guide pratique pour ajouter du code aux TableAdapters dans des applications multiniveaux](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md)
- [TableAdapters](https://msdn.microsoft.com/library/09416de9-134c-4dc7-8262-6c8d81e3f364)
- [Vue d'ensemble de TableAdapterManager](https://msdn.microsoft.com/library/33076d42-6b41-491a-ac11-6c6339aea650)
- [Vue d’ensemble de la mise à jour hiérarchique](https://msdn.microsoft.com/library/c4f8e8b9-e4a5-4a02-8462-d03d1e8222d6)
- [Outils de dataset dans Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)