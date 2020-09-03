---
title: Créer un Windows Form pour rechercher des données | Microsoft Docs
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
- Windows Forms, searching data
- Windows Forms, displaying data
- parameters, displaying filtered data
- data [Visual Studio], parameterizing queries
- data [Visual Studio], searching
ms.assetid: 65ca79a9-7458-466c-af55-978cd24c549e
caps.latest.revision: 31
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 81980f38cbd8fb595530cc52b2cf32056feb43a7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670063"
---
# <a name="create-a-windows-form-to-search-data"></a>Créer un Windows Form pour rechercher des données
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Un scénario d'application courant consiste à afficher les données sélectionnées dans un formulaire. Par exemple, supposons que vous souhaitiez afficher les commandes d'un client spécifique ou les détails d'une commande spécifique. Dans ce scénario, un utilisateur entre des informations dans un formulaire, puis une requête est exécutée prenant l'entrée de l'utilisateur comme paramètre. C'est-à-dire que les données sont sélectionnées selon une requête paramétrable. La requête retourne uniquement les données répondant aux critères entrés par l'utilisateur. Cette procédure pas à pas indique comment créer une requête retournant les clients d'une ville spécifique et modifier l'interface utilisateur de sorte que les utilisateurs puissent entrer un nom de ville et appuyer sur un bouton pour exécuter la requête.

 L'utilisation des requêtes paramétrables renforce l'efficacité de votre application en utilisant la base de données de la meilleure manière possible : pour filtrer rapidement des enregistrements. À l’inverse, si vous interrogez une table de base de données entière, que vous la transférez sur le réseau et que vous utilisez la logique d’application pour trouver les enregistrements souhaités, votre application peut devenir lente et perdre en efficacité.

 Vous pouvez ajouter des requêtes paramétrables à n’importe quel TableAdapter (et les contrôles pour accepter les valeurs de paramètre et exécuter la requête) à l’aide de la boîte de dialogue **Générateur de critères de recherche** . Ouvrez la boîte de dialogue en sélectionnant la commande **Ajouter une requête** dans le menu **Données** (ou dans n’importe quelle balise active TableAdapter).

 Cette procédure pas à pas décrit notamment les tâches suivantes :

- Création d’un projet d’application de Windows Forms.

- Création et configuration de la source de données dans votre application à l’aide de l’Assistant **configuration de source de données** .

- Définition du type de déplacement des éléments dans la fenêtre **sources de données** .

- Création de contrôles affichant les données en faisant glisser des éléments depuis la fenêtre **Sources de données** vers un formulaire.

- Ajout de contrôles pour afficher les données dans le formulaire.

- Fin de la boîte de dialogue **Générateur de critères de recherche** .

- Entrée de paramètres dans le formulaire et exécution de la requête paramétrable.

## <a name="prerequisites"></a>Prérequis
 Pour exécuter cette procédure pas à pas, vous avez besoin des éléments suivants :

- avoir accès à l'exemple de base de données Northwind.

## <a name="create-the-windows-application"></a>Créer l’application Windows
 La première étape consiste à créer une **application Windows**. L’attribution d’un nom au projet est facultative à cette étape, mais vous lui donnez un nom, car vous l’enregistrerez ultérieurement.

#### <a name="to-create-the-new-windows-application-project"></a>Pour créer le projet d'application Windows

1. Dans le menu **fichier** , créez un nouveau projet.

2. Nommez le projet `WindowsSearchForm`.

3. Sélectionnez **application Windows** , puis cliquez sur **OK**.

     Le projet **WindowsSearchForm** est créé et ajouté à l’**Explorateur de solutions**.

## <a name="create-the-data-source"></a>Créer la source de données
 Cette étape crée une source de données à partir d’une base de données à l’aide de l’Assistant **configuration de source de données** . Vous devez avoir accès à l'exemple de base de données Northwind pour créer la connexion. Pour plus d’informations sur la configuration de l’exemple de base de données Northwind, consultez [installer des exemples de bases de données SQL Server](../data-tools/install-sql-server-sample-databases.md).

#### <a name="to-create-the-data-source"></a>Pour créer la source de données

1. Dans le menu **Données** , cliquez sur **Afficher les sources de données**.

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

## <a name="create-the-form"></a>Créer le formulaire
 Vous pouvez créer les contrôles liés aux données en faisant glisser des éléments depuis la fenêtre **sources de données** vers votre formulaire.

#### <a name="to-create-data-bound-controls-on-the-form"></a>Pour créer des contrôlés liés aux données dans le formulaire

1. Développez le nœud **Customers** dans la fenêtre **Sources de données**.

2. Faites glisser le nœud **Customers** depuis la fenêtre **Sources de données** vers votre formulaire.

     Un <xref:System.Windows.Forms.DataGridView> et une barre d'outils (<xref:System.Windows.Forms.BindingNavigator>) pour parcourir les enregistrements apparaissent sur le formulaire. [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource> et <xref:System.Windows.Forms.BindingNavigator> s’affichent dans la barre d’état des composants.

## <a name="addparameterization-search-functionality-to-the-query"></a>Addparameterization (fonctionnalité de recherche) à la requête
 Vous pouvez ajouter une clause WHERE à la requête d’origine à l’aide de la boîte de dialogue **Générateur de critères de recherche** .

#### <a name="to-create-a-parameterized-query-and-controls-to-enter-the-parameters"></a>Pour créer une requête paramétrable et des contrôles pour entrer les paramètres

1. Sélectionnez le contrôle <xref:System.Windows.Forms.DataGridView>, puis choisissez **Ajouter une requête** dans le menu **Données**.

2. Tapez `FillByCity` dans la zone **nouveau nom** de la requête de la boîte de dialogue **Générateur de critères de recherche** .

3. Ajoutez `WHERE City = @City` à la requête dans la zone **Texte de la requête**.

     La requête doit ressembler à la suivante :

     `SELECT CustomerID, CompanyName, ContactName, ContactTitle, Address, City, Region, PostalCode, Country, Phone, Fax`

     `FROM Customers`

     `WHERE City = @City`

    > [!NOTE]
    > Les sources de données Access et OLE DB utilisent le point d’interrogation («  ? ») pour désigner les paramètres, donc la clause WHERE ressemble à ceci : `WHERE City = ?` .

4. Cliquez sur **OK** pour fermer la boîte de dialogue **Générateur de critères de recherche**.

     Un **FillByCityToolStrip** est ajouté au formulaire.

## <a name="testing-the-application"></a>Test de l’application
 L'exécution de l'application ouvre votre formulaire prêt à utiliser le paramètre comme entrée.

#### <a name="to-test-the-application"></a>Pour tester l'application

1. Appuyez sur F5 pour exécuter l'application.

2. Tapez **London** dans la zone de texte **City**, puis cliquez sur **FillByCity**.

     La grille de données est remplie avec les clients qui répondent aux critères. Dans cet exemple, la grille de données n’affiche que les clients possédant une valeur **London** dans leur colonne **City**.

## <a name="next-steps"></a>Étapes suivantes
 Selon les spécifications de votre application, vous pouvez exécuter différentes étapes après la création d'un formulaire paramétrable. Vous pouvez apporter à cette procédure pas à pas les améliorations suivantes :

- Ajout de contrôles affichant les données associées.

- Modification du dataset pour ajouter ou supprimer des objets de base de données. Pour plus d’informations, consultez [Créer et configurer des datasets](../data-tools/create-and-configure-datasets-in-visual-studio.md).

## <a name="see-also"></a>Voir aussi
 [Lier des contrôles Windows Forms à des données dans Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
