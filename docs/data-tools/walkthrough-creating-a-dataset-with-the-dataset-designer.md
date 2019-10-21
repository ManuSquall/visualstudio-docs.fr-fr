---
title: "Procédure pas à pas : création d'un groupe de données avec le Concepteur de DataSet"
ms.date: 09/11/2017
ms.topic: conceptual
helpviewer_keywords:
- datasets [Visual Basic], walkthroughs
- XML schemas, creating datasets
- data [Visual Studio], Dataset Designer
- Dataset Designer, walkthroughs
- datasets [Visual Basic], creating
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 9b6c91e6074e34a8207325e25f4a48b94dd037ef
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72639440"
---
# <a name="walkthrough-create-a-dataset-with-the-dataset-designer"></a>Procédure pas à pas : création d’un DataSet avec le Concepteur de DataSet

Dans cette procédure pas à pas, vous créez un DataSet à l’aide de l' **Concepteur de DataSet**. L’article vous guide tout au long du processus de création d’un nouveau projet et d’ajout d’un nouvel élément de **jeu de données** . Vous allez apprendre à créer des tables basées sur des tables dans une base de données sans utiliser d’Assistant.

## <a name="prerequisites"></a>Configuration requise

Cette procédure pas à pas utilise SQL Server Express base de données locale et l’exemple de base de données Northwind.

1. Si vous n’avez pas SQL Server Express base de données locale, installez-la à partir de la [page de téléchargement SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express)ou via le **Visual Studio installer**. Dans le Visual Studio Installer, SQL Server Express base de données locale peut être installée dans le cadre de la charge de travail de **stockage et de traitement des données** , ou en tant que composant individuel.

2. Installez l’exemple de base de données Northwind en procédant comme suit :

    1. Dans Visual Studio, ouvrez la fenêtre de **Explorateur d’objets SQL Server** . (Explorateur d’objets SQL Server est installé dans le cadre de la charge de travail **stockage et traitement des données** dans le Visual Studio installer.) Développez le nœud **SQL Server** . Cliquez avec le bouton droit sur votre instance de base de données locale, puis sélectionnez **nouvelle requête**.

       Une fenêtre de l’éditeur de requête s’ouvre.

    2. Copiez le [script Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) dans le presse-papiers. Ce script T-SQL crée la base de données Northwind à partir de zéro et la remplit avec des données.

    3. Collez le script T-SQL dans l’éditeur de requête, puis choisissez le bouton **exécuter** .

       Après un bref laps de temps, l’exécution de la requête se termine et la base de données Northwind est créée.

## <a name="create-a-new-windows-forms-application-project"></a>Créer un projet Application Windows Forms

1. Dans Visual Studio, dans le menu **fichier** , sélectionnez **nouveau**  > **projet**.

2. Développez **Visual C#**  ou **Visual Basic** dans le volet gauche, puis sélectionnez **Bureau Windows**.

3. Dans le volet central, sélectionnez le type de projet d' **application Windows Forms** .

4. Nommez le projet **DatasetDesignerWalkthrough**, puis choisissez **OK**.

     Visual Studio ajoute le projet à **Explorateur de solutions** et affiche un nouveau formulaire dans le concepteur.

## <a name="add-a-new-dataset-to-the-application"></a>Ajouter un nouveau jeu de données à l’application

1. Dans le menu **Projet**, sélectionnez **Ajouter un nouvel élément**.

     La boîte de dialogue **Ajouter un nouvel élément** s’affiche.

2. Dans le volet gauche, sélectionnez **données**, puis sélectionnez **DataSet** dans le volet central.

3. Nommez le jeu de données **NorthwindDataSet**, puis choisissez **Ajouter**.

     Visual Studio ajoute le fichier **NorthwindDataSet. xsd** au projet et l’ouvre dans le **Concepteur de DataSet**.

## <a name="create-a-data-connection-in-server-explorer"></a>Créer une connexion de données dans Explorateur de serveurs

1. Dans le menu **Affichage**, cliquez sur **Explorateur de serveurs**.

2. Dans **Explorateur de serveurs**, cliquez sur le bouton **se connecter à la base de données** .

3. Créez une connexion à l’exemple de base de données Northwind.

## <a name="create-the-tables-in-the-dataset"></a>Créer les tables dans le jeu de données

Cette section explique comment ajouter des tables au jeu de données.

### <a name="to-create-the-customers-table"></a>Pour créer la table Customers

1. Développez la connexion de données que vous avez créée dans **Explorateur de serveurs**, puis développez le nœud **tables** .

2. Faites glisser la table **Customers** de **Explorateur de serveurs** sur le **Concepteur de DataSet**.

     Une table de données **Customers** et un **CustomersTableAdapter** sont ajoutés au DataSet.

### <a name="to-create-the-orders-table"></a>Pour créer la table Orders

- Faites glisser la table **Orders** à partir de **Explorateur de serveurs** sur le **Concepteur de DataSet**.

     Une table de données de **commandes** , un **OrdersTableAdapter**et une relation de données entre les tables **Customers** et **Orders** sont ajoutés au DataSet.

### <a name="to-create-the-orderdetails-table"></a>Pour créer la table OrderDetails

- Faites glisser la table **Order Details** de **Explorateur de serveurs** vers le **Concepteur de DataSet**.

     Une table de données **Order Details** , **OrderDetailsTableAdapter**et une relation de données entre les tables **Orders** et **OrderDetails** sont ajoutées au DataSet.

## <a name="next-steps"></a>Étapes suivantes

- Enregistrez le jeu de données.

- Sélectionnez des éléments dans la fenêtre **sources de données** et faites-les glisser sur un formulaire. Pour plus d’informations, consultez [lier des contrôles Windows Forms à des données dans Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md).

- Ajoutez des requêtes supplémentaires aux TableAdapters.

- Ajoutez une logique de validation aux événements <xref:System.Data.DataTable.ColumnChanging> ou <xref:System.Data.DataTable.RowChanging> des tables de données dans le DataSet. Pour plus d’informations, consultez [valider des données dans des datasets](../data-tools/validate-data-in-datasets.md).

## <a name="see-also"></a>Voir aussi

- [Créer et configurer des datasets dans Visual Studio](../data-tools/create-and-configure-datasets-in-visual-studio.md)
- [Lier des contrôles Windows Forms à des données dans Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Lier des contrôles à des données dans Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
- [Valider les données](../data-tools/validate-data-in-datasets.md)