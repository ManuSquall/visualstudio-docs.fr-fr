---
title: Créer un Windows Form pour rechercher des données
description: Lisez un exemple de création d’un Windows Form pour rechercher des données. Créez l’application Windows Form, la source de données et le formulaire. Ajoutez le paramétrage. Tester l'application.
ms.custom: SEO-VS-2020
ms.date: 06/07/2021
ms.topic: conceptual
helpviewer_keywords:
- Windows Forms, searching data
- Windows Forms, displaying data
- parameters, displaying filtered data
- data [Visual Studio], parameterizing queries
- data [Visual Studio], searching
ms.assetid: 65ca79a9-7458-466c-af55-978cd24c549e
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 2ce9d3eeebf42855ad69f02b2d72330190a2b390
ms.sourcegitcommit: 01a411cd7ae3488b7b979a947bca92fd296a98e9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2021
ms.locfileid: "111761093"
---
# <a name="create-a-windows-form-to-search-data"></a>Créer un Windows Form pour rechercher des données

Un scénario d'application courant consiste à afficher les données sélectionnées dans un formulaire. Par exemple, supposons que vous souhaitiez afficher les commandes d'un client spécifique ou les détails d'une commande spécifique. Dans ce scénario, un utilisateur entre des informations dans un formulaire, puis une requête est exécutée prenant l'entrée de l'utilisateur comme paramètre. C'est-à-dire que les données sont sélectionnées selon une requête paramétrable. La requête retourne uniquement les données répondant aux critères entrés par l'utilisateur. Cette procédure pas à pas indique comment créer une requête retournant les clients d'une ville spécifique et modifier l'interface utilisateur de sorte que les utilisateurs puissent entrer un nom de ville et appuyer sur un bouton pour exécuter la requête.

L'utilisation des requêtes paramétrables renforce l'efficacité de votre application en utilisant la base de données de la meilleure manière possible : pour filtrer rapidement des enregistrements. À l’inverse, si vous interrogez une table de base de données entière, que vous la transférez sur le réseau et que vous utilisez la logique d’application pour trouver les enregistrements souhaités, votre application peut devenir lente et perdre en efficacité.

Vous pouvez ajouter des requêtes paramétrables à n’importe quel TableAdapter (et les contrôles pour accepter les valeurs de paramètre et exécuter la requête) à l’aide de la boîte de dialogue **Générateur de critères de recherche** . Ouvrez la boîte de dialogue en sélectionnant la commande **Ajouter une requête** dans le menu **Données** (ou dans n’importe quelle balise active TableAdapter).

Cette procédure pas à pas décrit notamment les tâches suivantes :

- Création et configuration de la source de données dans votre application à l’aide de l’Assistant **configuration de source de données** .

- Définition du type de déplacement des éléments dans la fenêtre **sources de données** .

- Création de contrôles affichant les données en faisant glisser des éléments depuis la fenêtre **Sources de données** vers un formulaire.

- Ajout de contrôles pour afficher les données dans le formulaire.

- Fin de la boîte de dialogue **Générateur de critères de recherche** .

- Entrée de paramètres dans le formulaire et exécution de la requête paramétrable.

> [!NOTE]
> Les procédures de cet article s’appliquent uniquement aux projets .NET Framework Windows Forms, et non aux projets Windows Forms .NET Core.

## <a name="prerequisites"></a>Prérequis

La charge de travail **stockage et traitement des données** doit être installée. Consultez [modifier Visual Studio](../install/modify-visual-studio.md).

Cette procédure pas à pas utilise SQL Server Express base de données locale et l’exemple de base de données Northwind.

1. Si vous n’avez pas SQL Server Express base de données locale, installez-la à partir de la [page de téléchargement SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express)ou via le **Visual Studio installer**. Dans le **Visual Studio installer**, vous pouvez installer SQL Server Express base de données locale dans le cadre de la charge de travail de **stockage et de traitement des données** , ou en tant que composant individuel.

2. Installez l’exemple de base de données Northwind en procédant comme suit :

    1. Dans Visual Studio, ouvrez la fenêtre de **Explorateur d’objets SQL Server** . (Explorateur d’objets SQL Server est installé dans le cadre de la charge de travail **stockage et traitement des données** dans le **Visual Studio installer**.) Développez le nœud **SQL Server** . Cliquez avec le bouton droit sur votre instance de base de données locale, puis sélectionnez **nouvelle requête**.

       Une fenêtre de l’éditeur de requête s’ouvre.

    2. Copiez le [script Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) dans le presse-papiers. Ce script T-SQL crée la base de données Northwind à partir de zéro et la remplit avec des données.

    3. Collez le script T-SQL dans l’éditeur de requête, puis choisissez le bouton **exécuter** .

       Après un bref laps de temps, l’exécution de la requête se termine et la base de données Northwind est créée.

## <a name="create-the-windows-forms-application"></a>Créer l’application Windows Forms

:::moniker range="vs-2017"

Créez un projet d' **application Windows Forms (.NET Framework)** pour C# ou Visual Basic. Attribuez le nom **WindowsSearchForm** au projet.

## <a name="create-the-data-source"></a>Créer la source de données

Cette étape crée une source de données à partir d’une base de données à l’aide de l’**Assistant Configuration de source de données** :

1. Pour ouvrir la fenêtre **sources de données** , dans le menu **données** , cliquez sur Afficher les **sources de données**.

2. Dans la fenêtre **sources de données** , sélectionnez Ajouter une **nouvelle source de données** pour démarrer l’Assistant Configuration de source de **données** .

3. Sélectionnez **Base de données** dans la page **Choisir un type de source de données** , puis cliquez sur **Suivant**.

4. Dans la page **Choisir votre connexion de données**, effectuez l’une des opérations suivantes :

    - Si une connexion de données à l’exemple de base de données Northwind est disponible dans la liste déroulante, sélectionnez-la.

    - Sélectionnez **Nouvelle connexion** pour afficher la boîte de dialogue **Ajouter/Modifier la connexion**.

5. Si votre base de données nécessite un mot de passe, sélectionnez l’option pour inclure les données sensibles, puis cliquez sur **Suivant**.

6. Dans la page **enregistrer la chaîne de connexion dans le fichier de configuration de l’application** , cliquez sur **suivant**.

7. Dans la page **Choisir vos objets de base de données**, développez le nœud **Tables**.

8. Sélectionnez la table **Customers**, puis cliquez sur **Terminer**.

     **NorthwindDataSet** est ajouté à votre projet et la table **Customers** apparaît dans la fenêtre **Sources de données**.

:::moniker-end

:::moniker range=">=vs-2019"

Créez un projet d' **application Windows Forms (.NET Framework)** pour C# ou Visual Basic. Attribuez le nom **WindowsSearchForm** au projet.

## <a name="create-the-data-source"></a>Créer la source de données

Cette étape crée une source de données à partir d’une base de données à l’aide de l’**Assistant Configuration de source de données** :

1. Pour ouvrir la fenêtre **sources de données** , utilisez la recherche rapide (**CTRL** + **Q**) et recherchez les sources de **données**.

1. Dans la fenêtre **sources de données** , sélectionnez Ajouter une **nouvelle source de données** pour démarrer l’Assistant Configuration de source de **données** .

1. Sélectionnez **Base de données** dans la page **Choisir un type de source de données** , puis cliquez sur **Suivant**.

1. Dans l’écran **choisir un modèle de base de données** , choisissez **DataSet**, puis cliquez sur **suivant**.

1. Dans la page **Choisir votre connexion de données**, effectuez l’une des opérations suivantes :

    - Si une connexion de données à l’exemple de base de données Northwind est disponible dans la liste déroulante, sélectionnez-la.

    - Sélectionnez **Nouvelle connexion** pour afficher la boîte de dialogue **Ajouter/Modifier la connexion**.

1. Dans la page **enregistrer la chaîne de connexion dans le fichier de configuration de l’application** , cliquez sur **suivant**.

1. Dans la page **Choisir vos objets de base de données**, développez le nœud **Tables**.

1. Sélectionnez la table **Customers**, puis cliquez sur **Terminer**.

     **NorthwindDataSet** est ajouté à votre projet et la table **Customers** apparaît dans la fenêtre **Sources de données**.

:::moniker-end

## <a name="create-the-form"></a>Créer le formulaire

Pour créer des contrôles liés aux données, vous pouvez faire glisser des éléments depuis la fenêtre **Sources de données** vers votre formulaire :

1. Assurez-vous que le concepteur de Windows Forms a le focus actif et que la fenêtre **sources de données** est ouverte et épinglée.

1. Développez le nœud **Customers** dans la fenêtre **Sources de données**.

1. Faites glisser le nœud **Customers** depuis la fenêtre **Sources de données** vers votre formulaire.

     Un <xref:System.Windows.Forms.DataGridView> et une barre d'outils (<xref:System.Windows.Forms.BindingNavigator>) pour parcourir les enregistrements apparaissent sur le formulaire. [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource> et <xref:System.Windows.Forms.BindingNavigator> s’affichent dans la barre d’état des composants.

## <a name="add-parameterization-search-functionality-to-the-query"></a>Ajouter le paramétrage (fonctionnalité de recherche) à la requête

Vous pouvez ajouter une clause WHERE à la requête d’origine à l’aide de la boîte de dialogue **Générateur de critères de recherche** :

1. Juste en dessous de l’aire de conception de votre formulaire, sélectionnez le bouton **customersTableAdapter** , puis, dans la fenêtre **Propriétés** , choisissez **Ajouter une requête...**.

2. Tapez **FillByCity** dans la zone **nouveau nom** de la requête de la boîte de dialogue **Générateur de critères de recherche** .

3. Ajoutez `WHERE City = @City` à la requête dans la zone **Texte de la requête**.

     La requête doit ressembler à la suivante :

     ```sql
     SELECT CustomerID, CompanyName, ContactName, ContactTitle,
          Address, City, Region, PostalCode, Country, Phone, Fax
     FROM Customers
     WHERE City = @City
     ```

    > [!NOTE]
    > Les sources de données Access et OLE DB utilisent le point d’interrogation («  ? ») pour désigner les paramètres, donc la clause WHERE ressemble à ceci : `WHERE City = ?` .

4. Cliquez sur **OK** pour fermer la boîte de dialogue **Générateur de critères de recherche**.

     Un **FillByCityToolStrip** est ajouté au formulaire.

## <a name="test-the-application"></a>Test de l’application

L’exécution de l’application ouvre votre formulaire et le rend prêt à prendre le paramètre comme entrée :

1. Appuyez sur **F5** pour exécuter l'application.

2. Tapez **London** dans la zone de texte **City**, puis cliquez sur **FillByCity**.

     La grille de données est remplie avec les clients qui répondent aux critères. Dans cet exemple, la grille de données n’affiche que les clients possédant une valeur **London** dans leur colonne **City**.

## <a name="next-steps"></a>Étapes suivantes

Selon les spécifications de votre application, vous pouvez exécuter différentes étapes après la création d'un formulaire paramétrable. Vous pouvez apporter à cette procédure pas à pas les améliorations suivantes :

- Ajout de contrôles affichant les données associées. Pour plus d’informations, consultez [relations dans les jeux de données](relationships-in-datasets.md).

- Modification du dataset pour ajouter ou supprimer des objets de base de données. Pour plus d’informations, consultez [Créer et configurer des datasets](../data-tools/create-and-configure-datasets-in-visual-studio.md).

## <a name="see-also"></a>Voir aussi

- [Lier des contrôles Windows Forms à des données dans Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
