---
title: Ajouter du code aux TableAdapters dans les applications multiniveau | Microsoft Docs
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
- TableAdapters, n-tier applications
- n-tier applications, extending TableAdapters
ms.assetid: dafac00e-df9d-4d4a-95a6-e34b4d099425
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: ed2a999fc3480bda8aa534d3dd32a00f5ff5c039
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/17/2019
ms.locfileid: "59651917"
---
# <a name="add-code-to-tableadapters-in-n-tier-applications"></a>Ajouter du code aux TableAdapters dans des applications multiniveaux
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez étendre les fonctionnalités d’un `TableAdapter` en créant un fichier de classe partielle pour le `TableAdapter` et ajoutant du code (au lieu d’ajouter du code pour le *DatasetName*. Fichier DataSet.Designer). Classes partielles permettent au code pour une classe spécifique être réparti entre plusieurs fichiers physiques. Pour plus d’informations, consultez [partielle](http://msdn.microsoft.com/library/7adaef80-f435-46e1-970a-269fff63b448) ou [partial (Type)](http://msdn.microsoft.com/library/27320743-a22e-4c7b-b0b3-53afe3607334).  
  
 Le code qui définit un `TableAdapter` est généré chaque fois les modifications sont apportées à la `TableAdapter`. Ce code est également généré lorsque des modifications sont apportées pendant l’exécution d’un Assistant qui modifie la configuration de la `TableAdapter`. Pour empêcher votre code d’être supprimé pendant la régénération d’un `TableAdapter`, ajoutez le code au fichier de classe partielle de la `TableAdapter`.  
  
 Par défaut, une fois que vous séparez le dataset et `TableAdapter` code, le résultat est un fichier de classe discret dans chaque projet. Le projet d’origine a un fichier nommé *DatasetName*. Designer.vb (ou *DatasetName*. Designer.cs) qui contient le `TableAdapter` code. Le projet désigné dans la **Dataset Project** propriété dispose d’un fichier nommé *DatasetName*. DataSet.Designer.vb (ou *DatasetName*. (DataSet.Designer.cs) qui contient le code de jeu de données.  
  
> [!NOTE]
> Quand vous séparez les jeux de données et `TableAdapter`s (en définissant le **DataSet Project** propriété), les classes dataset partielles existantes dans le projet ne seront pas être déplacées automatiquement. Classes dataset partielles existantes doivent être déplacés manuellement vers le projet dataset.  
  
> [!NOTE]
> Le Concepteur de DataSet fournit des fonctionnalités de génération <xref:System.Data.DataTable.ColumnChanging> et <xref:System.Data.DataTable.RowChanging> gestionnaires d’événements lorsque la validation est nécessaire. Pour plus d’informations, consultez [ajouter la validation à un jeu de données multicouches](../data-tools/add-validation-to-an-n-tier-dataset.md).  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
### <a name="to-add-user-code-to-a-tableadapter-in-an-n-tier-application"></a>Pour ajouter du code de l’utilisateur à un TableAdapter dans une architecture multiniveau  
  
1.  Recherchez le projet qui contient le fichier .xsd (le jeu de données).  
  
2.  Double-cliquez sur le **.xsd** fichier à ouvrir le jeu de données.  
  
3.  Cliquez sur le `TableAdapter` que vous souhaitez ajouter le code et sélectionnez**afficher le Code**.  
  
     Une classe partielle est créée et s’ouvre dans l’éditeur de Code.  
  
4.  Ajoutez le code à l’intérieur de la déclaration de classe partielle.  
  
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
 [Vue d’ensemble des Applications de données multicouches](../data-tools/n-tier-data-applications-overview.md)   
 [Ajoutez le code pour les jeux de données dans les applications multicouches](../data-tools/add-code-to-datasets-in-n-tier-applications.md)   
 [TableAdapters](http://msdn.microsoft.com/library/09416de9-134c-4dc7-8262-6c8d81e3f364)   
 [Vue d’ensemble de TableAdapterManager](http://msdn.microsoft.com/library/33076d42-6b41-491a-ac11-6c6339aea650)   
 [Vue d’ensemble de la mise à jour hiérarchique](http://msdn.microsoft.com/library/c4f8e8b9-e4a5-4a02-8462-d03d1e8222d6)