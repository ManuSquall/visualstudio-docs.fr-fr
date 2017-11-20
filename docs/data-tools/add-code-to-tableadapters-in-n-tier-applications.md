---
title: Ajoutez du code aux TableAdapters dans des applications multicouches | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- TableAdapters, n-tier applications
- n-tier applications, extending TableAdapters
ms.assetid: dafac00e-df9d-4d4a-95a6-e34b4d099425
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 396e1132015c2eb37f06095f135dae878bfeb574
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="add-code-to-tableadapters-in-n-tier-applications"></a>Ajoutez du code aux TableAdapters dans des applications multicouches
Vous pouvez étendre les fonctionnalités d’un TableAdapter en ajoutant du code et de création d’un fichier de classe partielle pour le TableAdapter (au lieu d’ajouter du code pour le *DatasetName*. Fichier DataSet.Designer). Classes partielles permettent au code pour une classe spécifique être réparti entre plusieurs fichiers physiques. Pour plus d’informations, consultez [partielle](/dotnet/visual-basic/language-reference/modifiers/partial) ou [partiel, Type](/dotnet/csharp/language-reference/keywords/partial-type).  
  
Le code qui définit un TableAdapter est généré chaque fois les modifications sont apportées au TableAdapter dans le jeu de données. Ce code est également généré lorsque des modifications sont apportées pendant l’exécution d’un Assistant qui modifie la configuration du TableAdapter. Pour empêcher votre code d’être supprimé pendant la régénération d’un TableAdapter, ajoutez le code au fichier de classe partielle du TableAdapter.  
  
Par défaut, une fois que vous séparez le dataset et le code du TableAdapter, le résultat est un fichier de classe discret dans chaque projet. Le projet d’origine a un fichier nommé *DatasetName*. Designer.vb (ou *DatasetName*. Designer.cs) qui contient le code du TableAdapter. Le projet désigné dans la **projet Dataset** propriété dispose d’un fichier nommé *DatasetName*. DataSet.Designer.vb (ou *DatasetName*. (DataSet.Designer.cs) qui contient le code du jeu de données.  
  
> [!NOTE]
>  Quand vous séparez les datasets et les TableAdapters (en définissant le **projet DataSet** propriété), les classes dataset partielles existantes dans le projet ne seront pas être déplacées automatiquement. Les classes dataset partielles existantes doivent être déplacés manuellement vers le projet dataset.  
  
> [!NOTE]
>  Le jeu de données fournit les fonctionnalités de génération <xref:System.Data.DataTable.ColumnChanging> et <xref:System.Data.DataTable.RowChanging> gestionnaires d’événements lorsque la validation est nécessaire. Pour plus d’informations, consultez [ajouter une validation à un dataset MULTICOUCHE](../data-tools/add-validation-to-an-n-tier-dataset.md).  
  
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
[Vue d’ensemble des Applications de données multicouches](../data-tools/n-tier-data-applications-overview.md)   
[Ajouter du code aux groupes de données dans les applications multicouches](../data-tools/add-code-to-datasets-in-n-tier-applications.md)   
[Créer et configurer des TableAdapters](create-and-configure-tableadapters.md)   
[Vue d’ensemble de la mise à jour hiérarchique](hierarchical-update.md)   
