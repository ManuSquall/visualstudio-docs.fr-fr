---
title: Ajoutez le code aux jeux de données dans les applications multiniveau | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- n-tier applications, extending datasets
ms.assetid: d43c2ccd-4902-43d8-b1a8-d10ca5d3210c
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 48f27d2e1bb72b7c5c0aaf1a66673beae003dd66
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49202213"
---
# <a name="add-code-to-datasets-in-n-tier-applications"></a>Ajouter du code à des datasets dans des applications multiniveaux
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Vous pouvez étendre les fonctionnalités d’un jeu de données en créant un fichier de classe partielle pour le jeu de données et en ajoutant du code (au lieu d’ajouter du code pour le *DatasetName*. Fichier Dataset.Designer). Classes partielles permettent au code pour une classe spécifique être réparti entre plusieurs fichiers physiques. Pour plus d’informations, consultez [partielle](http://msdn.microsoft.com/library/7adaef80-f435-46e1-970a-269fff63b448) ou [Classes et méthodes partielles](http://msdn.microsoft.com/library/804cecb7-62db-4f97-a99f-60975bd59fa1).  
  
 Le code qui définit un jeu de données est généré chaque fois les modifications sont apportées à la définition du jeu de données (dans le [création et modification de données typés](../data-tools/creating-and-editing-typed-datasets.md)). Ce code est également généré lorsque vous apportez des modifications pendant l’exécution d’un Assistant qui modifie la configuration d’un jeu de données. Pour empêcher que votre code en cours de suppression pendant la régénération d’un jeu de données, ajoutez le code au fichier de classe partielle du jeu de données.  
  
 Par défaut, une fois que vous séparez le dataset et `TableAdapter` code, le résultat est un fichier de classe discret dans chaque projet. Le projet d’origine a une filenamed *DatasetName*. Designer.vb (ou *DatasetName*. Designer.cs) qui contient le `TableAdapter` code. Le projet désigné dans la **Dataset Project** propriété dispose d’un fichier nommé *DatasetName*. DataSet.Designer.vb (ou *DatasetName*. (DataSet.Designer.cs). Ce fichier contient le code de jeu de données.  
  
> [!NOTE]
>  Quand vous séparez les jeux de données et `TableAdapter`s (en définissant le **DataSet Project** propriété), les classes dataset partielles existantes dans le projet ne sont pas déplacées automatiquement. Classes dataset partielles existantes doivent être déplacés manuellement vers le projet dataset.  
  
> [!NOTE]
>  Lorsque le code de validation doit être ajouté, le [création et modification de données typés](../data-tools/creating-and-editing-typed-datasets.md)fournit des fonctionnalités de génération <xref:System.Data.DataTable.ColumnChanging> et <xref:System.Data.DataTable.RowChanging> gestionnaires d’événements. Pour plus d’informations, consultez [ajouter la validation à un jeu de données multicouches](../data-tools/add-validation-to-an-n-tier-dataset.md).  
  
### <a name="to-add-code-to-datasets-in-n-tier-applications"></a>Pour ajouter du code pour les jeux de données dans les applications multicouches  
  
1.  Recherchez le projet qui contient le fichier .xsd (le [création et modification de données typés](../data-tools/creating-and-editing-typed-datasets.md)).  
  
2.  Sélectionnez le **.xsd** fichier à ouvrir le [création et modification de données typés](../data-tools/creating-and-editing-typed-datasets.md).  
  
3.  Avec le bouton droit de la table de données à laquelle vous souhaitez ajouter le code (le nom de table dans la barre de titre) et enfin**afficher le Code**.  
  
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
 [Vue d’ensemble des Applications de données multicouches](../data-tools/n-tier-data-applications-overview.md)   
 [Ajouter du code aux TableAdapters dans des applications multicouches](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md)   
 [TableAdapters](http://msdn.microsoft.com/library/09416de9-134c-4dc7-8262-6c8d81e3f364)   
 [Vue d’ensemble de TableAdapterManager](http://msdn.microsoft.com/library/33076d42-6b41-491a-ac11-6c6339aea650)   
 [Vue d’ensemble de la mise à jour hiérarchique](http://msdn.microsoft.com/library/c4f8e8b9-e4a5-4a02-8462-d03d1e8222d6)   
 [Création d’Applications de données](../data-tools/creating-data-applications.md)   
 [Outils de dataset dans Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)

