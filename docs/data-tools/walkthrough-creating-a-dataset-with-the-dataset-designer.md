---
title: 'Procédure pas à pas : Création d’un Dataset avec le Concepteur de Dataset'
ms.date: 09/11/2017
ms.topic: conceptual
helpviewer_keywords:
- datasets [Visual Basic], walkthroughs
- XML schemas, creating datasets
- data [Visual Studio], Dataset Designer
- Dataset Designer, walkthroughs
- datasets [Visual Basic], creating
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: f91c24885cc6817889671dd7a1a6e7e1686ce93f
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60070523"
---
# <a name="walkthrough-create-a-dataset-with-the-dataset-designer"></a>Procédure pas à pas : Créer un jeu de données avec le Concepteur de Dataset

Dans cette procédure pas à pas, vous allez créer un jeu de données à l’aide de la **Concepteur de Dataset**. L’article passe en revue le processus de création d’un projet et l’ajout d’une nouvelle **DataSet** élément à ce dernier. Vous allez apprendre à créer des tables basées sur les tables dans une base de données sans utiliser l’Assistant.

## <a name="prerequisites"></a>Prérequis

Cette procédure pas à pas utilise SQL Server Express LocalDB et la base de données Northwind.

1. Si vous n’avez pas SQL Server Express LocalDB, installez-le à partir de la [page de téléchargement de SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), ou via le **le programme d’installation de Visual Studio**. Dans le programme d’installation Visual Studio, SQL Server Express LocalDB peuvent être installé dans le cadre de la **stockage de données et de traitement** charge de travail, ou comme un composant individuel.

2. Installer la base de données Northwind en suivant ces étapes :

    1. Dans Visual Studio, ouvrez le **Explorateur d’objets SQL Server** fenêtre. (Explorateur d’objets SQL Server est installé dans le cadre de la **stockage de données et de traitement** charge de travail dans Visual Studio Installer.) Développez le **SQL Server** nœud. Avec le bouton droit sur votre instance de base de données locale et sélectionnez **nouvelle requête**.

       Une fenêtre d’éditeur de requête s’ouvre.

    2. Copie le [script Transact-SQL de Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) dans votre Presse-papiers. Ce script T-SQL crée la base de données Northwind à partir de zéro et la remplit avec des données.

    3. Collez le script T-SQL dans l’éditeur de requête, puis choisissez le **Execute** bouton.

       Après une courte période, la requête est terminée et la base de données Northwind est créé.

## <a name="create-a-new-windows-forms-application-project"></a>Créer un projet Application Windows Forms

1. Dans Visual Studio, sur le **fichier** menu, sélectionnez **New** > **projet**.

2. Développez le **Visual C#** ou **Visual Basic** dans le volet gauche, puis sélectionnez **Windows Desktop**.

3. Dans le volet central, sélectionnez le **Windows Forms application** type de projet.

4. Nommez le projet **DatasetDesignerWalkthrough**, puis choisissez **OK**.

     Visual Studio ajoute le projet à **l’Explorateur de solutions** et afficher un nouveau formulaire dans le concepteur.

## <a name="add-a-new-dataset-to-the-application"></a>Ajouter un nouveau jeu de données à l’Application

1. Dans le menu **Projet**, sélectionnez **Ajouter un nouvel élément**.

     La boîte de dialogue **Ajouter un nouvel élément** s’affiche.

2. Dans le volet gauche, sélectionnez **données**, puis sélectionnez **DataSet** dans le volet central.

3. Nommez le jeu de données **NorthwindDataset**, puis choisissez **ajouter**.

     Visual Studio ajoute un fichier appelé **NorthwindDataset.xsd** au projet et l’ouvre dans le **Concepteur de Dataset**.

## <a name="create-a-data-connection-in-server-explorer"></a>Créer une connexion de données dans l’Explorateur de serveurs

1. Dans le menu **Affichage**, cliquez sur **Explorateur de serveurs**.

2. Dans **Explorateur de serveurs**, cliquez sur le **se connecter à la base de données** bouton.

3. Créer une connexion à la base de données Northwind.

## <a name="create-the-tables-in-the-dataset"></a>Créer les Tables dans le jeu de données

Cette section explique comment ajouter des tables au jeu de données.

### <a name="to-create-the-customers-table"></a>Pour créer la table Customers

1. Développez la connexion de données que vous avez créé dans **Explorateur de serveurs**, puis développez le **Tables** nœud.

2. Faites glisser le **clients** à partir de la table **Explorateur de serveurs** sur le **Concepteur de Dataset**.

     Un **clients** table de données et **CustomersTableAdapter** sont ajoutées au jeu de données.

### <a name="to-create-the-orders-table"></a>Pour créer la table Orders

- Faites glisser le **commandes** à partir de la table **Explorateur de serveurs** sur le **Concepteur de Dataset**.

     Un **commandes** table de données, **OrdersTableAdapter**et la relation de données entre le **clients** et **commandes** tables sont ajoutées à la jeu de données.

### <a name="to-create-the-orderdetails-table"></a>Pour créer la table OrderDetails

- Faites glisser le **Order Details** à partir de la table **Explorateur de serveurs** sur le **Concepteur de Dataset**.

     Un **Order Details** table de données, **OrderDetailsTableAdapter**et une relation de données entre le **commandes** et **OrderDetails** tables sont ajoutés au jeu de données.

## <a name="next-steps"></a>Étapes suivantes

- Enregistrer le jeu de données.

- Sélectionnez des éléments dans le **des Sources de données** fenêtre et faites-les glisser jusqu'à un formulaire. Pour plus d’informations, consultez [lier les formulaires Windows contrôle aux données dans Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md).

- Ajoutez davantage de requêtes pour les TableAdapters.

- Ajouter une logique de validation pour le <xref:System.Data.DataTable.ColumnChanging> ou <xref:System.Data.DataTable.RowChanging> événements les tables de données dans le jeu de données. Pour plus d’informations, consultez [valider des données dans les jeux de données](../data-tools/validate-data-in-datasets.md).

## <a name="see-also"></a>Voir aussi

- [Créer et configurer des datasets dans Visual Studio](../data-tools/create-and-configure-datasets-in-visual-studio.md)
- [Lier des contrôles Windows Forms à des données dans Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Lier des contrôles à des données dans Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
- [Valider des données](../data-tools/validate-data-in-datasets.md)