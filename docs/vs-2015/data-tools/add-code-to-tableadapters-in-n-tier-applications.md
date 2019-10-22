---
title: Ajouter du code aux TableAdapters dans des applications multicouches | Microsoft Docs
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 942850e776cdd493afaad56b782b417db2040625
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72673104"
---
# <a name="add-code-to-tableadapters-in-n-tier-applications"></a>Ajouter du code aux TableAdapters dans des applications multiniveaux
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez étendre les fonctionnalités d’un `TableAdapter` en créant un fichier de classe partielle pour le `TableAdapter` et en y ajoutant du code (au lieu d’ajouter du code au fichier *NomGroupeDonnées*. Fichier DataSet. Designer). Les classes partielles permettent à du code pour une classe spécifique d’être divisé entre plusieurs fichiers physiques. Pour plus d’informations, consultez [Partial](https://msdn.microsoft.com/library/7adaef80-f435-46e1-970a-269fff63b448) ou [Partial (type)](https://msdn.microsoft.com/library/27320743-a22e-4c7b-b0b3-53afe3607334).

 Le code qui définit un `TableAdapter` est généré chaque fois que des modifications sont apportées au `TableAdapter`. Ce code est également généré lorsque des modifications sont apportées pendant l’exécution d’un assistant qui modifie la configuration de l' `TableAdapter`. Pour empêcher la suppression de votre code lors de la régénération d’un `TableAdapter`, ajoutez du code au fichier de classe partielle du `TableAdapter`.

 Par défaut, après avoir séparé le jeu de données et `TableAdapter` code, le résultat est un fichier de classe discret dans chaque projet. Le projet d’origine a un fichier nommé *NomGroupeDonnées*. Designer. vb (ou *NomGroupeDonnées*. Designer.cs) qui contient le code `TableAdapter`. Le projet désigné dans la propriété de **projet DataSet** a un fichier nommé *NomGroupeDonnées*. DataSet. Designer. vb (ou *NomGroupeDonnées*. DataSet.Designer.cs) qui contient le code du DataSet.

> [!NOTE]
> Lorsque vous séparez des DataSets et des `TableAdapter`s (en définissant la propriété **DataSet Project** ), les classes DataSet partielles existantes dans le projet ne sont pas déplacées automatiquement. Les classes partielles de DataSet existantes doivent être déplacées manuellement vers le projet de DataSet.

> [!NOTE]
> Le concepteur de DataSet fournit des fonctionnalités permettant de générer des gestionnaires d’événements <xref:System.Data.DataTable.ColumnChanging> et <xref:System.Data.DataTable.RowChanging> lorsque la validation est nécessaire. Pour plus d’informations, consultez [Ajouter une validation à un DataSet multicouche](../data-tools/add-validation-to-an-n-tier-dataset.md).

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

### <a name="to-add-user-code-to-a-tableadapter-in-an-n-tier-application"></a>Pour ajouter du code utilisateur à un TableAdapter dans une application multiniveau

1. Recherchez le projet qui contient le fichier. xsd (le DataSet).

2. Double-cliquez sur le fichier **. xsd** pour ouvrir le jeu de données.

3. Cliquez avec le bouton droit sur le `TableAdapter` auquel vous souhaitez ajouter du code, puis sélectionnez**afficher le code**.

     Une classe partielle est créée et s’ouvre dans l’éditeur de code.

4. Ajoutez du code à l’intérieur de la déclaration de classe partielle.

5. L’exemple suivant indique où ajouter du code au `CustomersTableAdapter` dans le `NorthwindDataSet` :

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
 [Vue d’ensemble des applications de données multicouches](../data-tools/n-tier-data-applications-overview.md) [Ajouter du code aux jeux de données dans les applications multicouches](../data-tools/add-code-to-datasets-in-n-tier-applications.md) [TableAdapters](https://msdn.microsoft.com/library/09416de9-134c-4dc7-8262-6c8d81e3f364) vue d' [ensemble](https://msdn.microsoft.com/library/33076d42-6b41-491a-ac11-6c6339aea650) [mise à jour hiérarchique](https://msdn.microsoft.com/library/c4f8e8b9-e4a5-4a02-8462-d03d1e8222d6)