---
title: Créer un contrôle utilisateur prenant en charge la liaison de données simples
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom controls [Visual Studio], Data Sources Window
- Data Sources Window, controls
ms.assetid: b1488366-6dfb-454e-9751-f42fd3f3ddfb
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 716366366bd9bb7514d042748b07dcb30a3567eb
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55923822"
---
# <a name="create-a-windows-forms-user-control-that-supports-simple-data-binding"></a>Créer un contrôle utilisateur Windows Forms prenant en charge la liaison de données simples

Pour présenter des données dans des formulaires d’applications Windows, vous pouvez choisir des contrôles existants dans la **Boîte à outils** ou créer des contrôles personnalisés si votre application nécessite des fonctionnalités qui ne sont pas disponibles dans les contrôles standard. Cette procédure pas à pas vous indique comment créer un contrôle qui implémente l'objet <xref:System.ComponentModel.DefaultBindingPropertyAttribute>. Les contrôles qui implémentent <xref:System.ComponentModel.DefaultBindingPropertyAttribute> peuvent contenir une propriété pouvant être liée aux données. Ce type de contrôles est similaire à <xref:System.Windows.Forms.TextBox> ou <xref:System.Windows.Forms.CheckBox>.

Pour plus d’informations sur la création de contrôles, consultez [développement de contrôles Windows Forms au moment du Design](/dotnet/framework/winforms/controls/developing-windows-forms-controls-at-design-time).

Lorsque vous créez des contrôles utilisables dans les scénarios de liaison de données, vous devez implémenter un des attributs de liaison de données suivants :

|Utilisation d’attributs de liaison de données|
| - |
|Implémentez <xref:System.ComponentModel.DefaultBindingPropertyAttribute> sur des contrôles simples, comme <xref:System.Windows.Forms.TextBox>, qui affichent une seule colonne (ou propriété) de données. (Ce processus est décrit dans cette page de procédure pas à pas.)|
|Implémentez <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> sur des contrôles, comme <xref:System.Windows.Forms.DataGridView>, qui affichent des listes (ou tables) de données. Pour plus d’informations, consultez [créer un contrôle utilisateur Windows Forms qui prend en charge la liaison de données complexe](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md).|
|Implémentez l'objet <xref:System.ComponentModel.LookupBindingPropertiesAttribute> sur des contrôles, comme <xref:System.Windows.Forms.ComboBox>, qui affichent des listes (ou tables) de données, mais doivent également présenter une seule colonne ou propriété. Pour plus d’informations, consultez [créer un contrôle utilisateur Windows Forms qui prend en charge la liaison de données de recherche](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).|

Cette procédure pas à pas crée un contrôle simple qui affiche les données d'une seule colonne dans une table. Cet exemple utilise la colonne `Phone` de la table `Customers` de l'exemple de base de données Northwind. Le contrôle utilisateur simple affiche les numéros de téléphone des clients dans un format de numéro de téléphone standard, en utilisant un <xref:System.Windows.Forms.MaskedTextBox> et en définissant le masque sur un numéro de téléphone.

Pendant cette procédure pas à pas, vous allez apprendre à :

-   Créer une **application Windows Forms**.

-   Ajouter un nouveau **Contrôle utilisateur** à votre projet.

-   Concevoir visuellement le contrôle utilisateur.

-   Implémenter l'attribut `DefaultBindingProperty`.

-   Créer un jeu de données avec le **Configuration de Source de données** Assistant.

-   Définir la colonne **Phone** dans la fenêtre **Sources de données** pour qu’elle utilise le nouveau contrôle.

-   Créer un formulaire pour afficher des données dans le nouveau contrôle.

## <a name="prerequisites"></a>Prérequis

Cette procédure pas à pas utilise SQL Server Express LocalDB et la base de données Northwind.

1.  Si vous n’avez pas SQL Server Express LocalDB, installez-le à partir de la [page de téléchargement de SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), ou via le **le programme d’installation de Visual Studio**. Dans le **le programme d’installation de Visual Studio**, vous pouvez installer SQL Server Express LocalDB dans le cadre de la **stockage de données et de traitement** charge de travail, ou comme un composant individuel.

2.  Installer la base de données Northwind en suivant ces étapes :

    1. Dans Visual Studio, ouvrez le **Explorateur d’objets SQL Server** fenêtre. (Explorateur d’objets SQL Server est installé dans le cadre de la **stockage de données et de traitement** charge de travail dans le **le programme d’installation de Visual Studio**.) Développez le **SQL Server** nœud. Avec le bouton droit sur votre instance de base de données locale et sélectionnez **nouvelle requête**.

       Une fenêtre d’éditeur de requête s’ouvre.

    2. Copie le [script Transact-SQL de Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) dans votre Presse-papiers. Ce script T-SQL crée la base de données Northwind à partir de zéro et la remplit avec des données.

    3. Collez le script T-SQL dans l’éditeur de requête, puis choisissez le **Execute** bouton.

       Après une courte période, la requête est terminée en cours d’exécution et la base de données Northwind est créé.

## <a name="create-a-windows-forms-application"></a>Créer une application Windows Forms

La première étape consiste à créer un **Windows Forms Application**:

1. Dans Visual Studio, sur le **fichier** menu, sélectionnez **New** > **projet**.

2. Développez le **Visual C#**  ou **Visual Basic** dans le volet gauche, puis sélectionnez **Windows Desktop**.

3. Dans le volet central, sélectionnez le **Windows Forms application** type de projet.

4. Nommez le projet **SimpleControlWalkthrough**, puis choisissez **OK**.

     Le projet **SimpleControlWalkthrough** est créé et ajouté à l’**Explorateur de solutions**.

## <a name="add-a-user-control-to-the-project"></a>Ajouter un contrôle utilisateur au projet

Cette procédure pas à pas crée un contrôle simple pouvant être lié à des données à partir d’un **contrôle utilisateur**. Ajouter un **contrôle utilisateur** d’élément à la **SimpleControlWalkthrough** projet :

1.  Dans le menu **Projet**, choisissez **Ajouter un contrôle utilisateur**.

2.  Tapez **PhoneNumberBox** dans la zone Nom, puis cliquez sur **Ajouter**.

     Le contrôle **PhoneNumberBox** est ajouté à l’**Explorateur de solutions** et s’ouvre dans le concepteur.

## <a name="design-the-phonenumberbox-control"></a>Concevoir le contrôle PhoneNumberBox

Cette procédure pas à pas développe existant <xref:System.Windows.Forms.MaskedTextBox> pour créer le **PhoneNumberBox** contrôle :

1.  Faites glisser un <xref:System.Windows.Forms.MaskedTextBox> depuis la **Boîte à outils** vers l’aire de conception du contrôle utilisateur.

2.  Sélectionnez la balise active du <xref:System.Windows.Forms.MaskedTextBox> que vous venez de faire glisser et choisissez **Définir le masque**.

3.  Sélectionnez **Numéro de téléphone** dans la boîte de dialogue **Masque de saisie** et cliquez sur **OK** pour définir le masque.

## <a name="add-the-required-data-binding-attribute"></a>Ajoutez l’attribut de liaison de données requis

Pour des contrôles simples prenant en charge la liaison de données, implémentez <xref:System.ComponentModel.DefaultBindingPropertyAttribute> :

1.  Commutateur le **PhoneNumberBox** contrôle en mode code. (Dans le menu **Affichage**, choisissez **Code**.)

2.  Remplacez le code dans le **PhoneNumberBox** par le code suivant :

     [!code-csharp[VbRaddataDisplaying#3](../data-tools/codesnippet/CSharp/create-a-windows-forms-user-control-that-supports-simple-data-binding_1.cs)]
     [!code-vb[VbRaddataDisplaying#3](../data-tools/codesnippet/VisualBasic/create-a-windows-forms-user-control-that-supports-simple-data-binding_1.vb)]

3.  Dans le menu **Générer** , cliquez sur **Générer la solution**.

## <a name="create-a-data-source-from-your-database"></a>Créer une source de données à partir de votre base de données

Cette étape utilise l’Assistant **Configuration de source de données** pour créer une source de données basée sur la table `Customers` de l’exemple de base de données Northwind. Vous devez avoir accès à l'exemple de base de données Northwind pour créer la connexion. Pour plus d’informations sur la configuration de la base de données Northwind, consultez [Comment : installer les bases de données exemple](../data-tools/installing-database-systems-tools-and-samples.md).

1.  Pour ouvrir le **des Sources de données** fenêtre, dans le **données** menu, cliquez sur **afficher les Sources de données**.

2.  Dans la fenêtre **Sources de données**, sélectionnez **Ajouter une nouvelle source de données** pour démarrer l’Assistant **Configuration de source de données**.

3.  Dans la page **Choisir un type de source de données**, sélectionnez **Base de données**, puis cliquez sur **Suivant**.

4.  Dans la page **Choisir votre connexion de données**, effectuez l’une des opérations suivantes :

    -   Si une connexion de données à l’exemple de base de données Northwind est disponible dans la liste déroulante, sélectionnez-la.

    -   Sélectionnez **Nouvelle connexion** pour afficher la boîte de dialogue **Ajouter/Modifier la connexion**.

5.  Si votre base de données nécessite un mot de passe, sélectionnez l’option pour inclure les données sensibles, puis cliquez sur **Suivant**.

6.  Sur le **enregistrer la chaîne de connexion dans le fichier de Configuration de l’Application** , cliquez sur **suivant**.

7.  Dans la page **Choisir vos objets de base de données**, développez le nœud **Tables**.

8.  Sélectionnez la table `Customers`, puis cliquez sur **Terminer**.

     **NorthwindDataSet** est ajouté à votre projet et la table `Customers` apparaît dans la fenêtre **Sources de données**.

## <a name="set-the-phone-column-to-use-the-phonenumberbox-control"></a>Définir la colonne phone pour utiliser le contrôle PhoneNumberBox

Dans la fenêtre **Sources de données**, vous pouvez définir le contrôle à créer avant de faire glisser des éléments vers votre formulaire :

1.  Ouvrez **Form1** dans le concepteur.

2.  Développez le nœud **Customers** dans la fenêtre **Sources de données**.

3.  Cliquez sur la flèche déroulante du nœud **Customers** et choisissez **Détails** dans la liste de contrôles.

4.  Cliquez sur la flèche déroulante de la colonne **Phone** et choisissez **Personnaliser**.

5.  Sélectionnez **PhoneNumberBox** dans la liste des **Contrôles associés** de la boîte de dialogue **Options de personnalisation de l’interface utilisateur de données**.

6.  Cliquez sur la flèche déroulante de la colonne **Phone** et choisissez **PhoneNumberBox**.

## <a name="add-controls-to-the-form"></a>Ajouter des contrôles au formulaire

Pour créer des contrôles liés aux données, vous pouvez faire glisser des éléments depuis la fenêtre **Sources de données** vers le formulaire.

Pour créer des contrôles liés aux données sur le formulaire, faites glisser le **clients** nœud à partir de la **des Sources de données** fenêtre vers le formulaire et vérifiez que le **PhoneNumberBox** contrôle est utilisé pour afficher les données dans le **téléphone** colonne.

     Data-bound controls with descriptive labels appear on the form, along with a tool strip (<xref:System.Windows.Forms.BindingNavigator>) for navigating records. A [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource>, and <xref:System.Windows.Forms.BindingNavigator> appear in the component tray.

## <a name="run-the-application"></a>Exécuter l'application

Appuyez sur **F5** pour exécuter l’application.

## <a name="next-steps"></a>Étapes suivantes

Selon les exigences de votre application, vous pouvez exécuter différentes étapes après la création d’un contrôle prenant en charge la liaison de données. Les étapes ultérieures sont habituellement celles-ci :

-   Positionnement de vos contrôles personnalisés dans une bibliothèque de contrôles pour pouvoir les réutiliser dans d'autres applications.

-   Création de contrôles prenant en charge des scénarios de liaison de données plus complexes. Pour plus d’informations, consultez [créer un contrôle utilisateur Windows Forms qui prend en charge la liaison de données complexe](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md) et [créer un contrôle utilisateur Windows Forms qui prend en charge la liaison de données de recherche](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).

## <a name="see-also"></a>Voir aussi

- [Lier des contrôles Windows Forms à des données dans Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Définir le contrôle à créer lors d’une opération de glisser-déplacer à partir de la fenêtre Sources de données](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)