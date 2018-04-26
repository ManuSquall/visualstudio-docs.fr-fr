---
title: Créer un contrôle utilisateur qui prend en charge la liaison de données simple
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
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: a484388223b7dae62f165e13b2fc75368b0e642f
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="create-a-windows-forms-user-control-that-supports-simple-data-binding"></a>Créer un contrôle utilisateur Windows Forms qui prend en charge la liaison de données simple
Lors de l’affichage des données sur les formulaires dans les applications Windows, vous pouvez choisir des contrôles existants à partir de la **boîte à outils**, ou vous pouvez créer des contrôles personnalisés si votre application nécessite des fonctionnalités qui ne sont pas disponible dans les contrôles standard. Cette procédure pas à pas vous indique comment créer un contrôle qui implémente l'objet <xref:System.ComponentModel.DefaultBindingPropertyAttribute>. Les contrôles qui implémentent <xref:System.ComponentModel.DefaultBindingPropertyAttribute> peuvent contenir une propriété pouvant être liée aux données. Ce type de contrôles est similaire à <xref:System.Windows.Forms.TextBox> ou <xref:System.Windows.Forms.CheckBox>.

 Pour plus d’informations sur la création de contrôles, consultez [développement de contrôles Windows Forms au moment du Design](/dotnet/framework/winforms/controls/developing-windows-forms-controls-at-design-time).

 Lorsque vous créez des contrôles utilisables dans les scénarios de liaison de données, vous devez implémenter un des attributs de liaison de données suivants :

|Utilisation d’attributs de liaison de données|
|-----------------------------------|
|Implémentez <xref:System.ComponentModel.DefaultBindingPropertyAttribute> sur des contrôles simples, comme <xref:System.Windows.Forms.TextBox>, qui affichent une seule colonne (ou propriété) de données. (Ce processus est décrit dans cette page de procédure pas à pas.)|
|Implémentez <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> sur des contrôles, comme <xref:System.Windows.Forms.DataGridView>, qui affichent des listes (ou tables) de données. Pour plus d’informations, consultez [créer un contrôle utilisateur Windows Forms qui prend en charge la liaison de données complexe](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md).|
|Implémentez l'objet <xref:System.ComponentModel.LookupBindingPropertiesAttribute> sur des contrôles, comme <xref:System.Windows.Forms.ComboBox>, qui affichent des listes (ou tables) de données, mais doivent également présenter une seule colonne ou propriété. Pour plus d’informations, consultez [créer un contrôle utilisateur Windows Forms qui prend en charge la liaison de données de recherche](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).|

 Cette procédure pas à pas crée un contrôle simple qui affiche les données d'une seule colonne dans une table. Cet exemple utilise la colonne `Phone` de la table `Customers` de l'exemple de base de données Northwind. Le contrôle utilisateur simple affichera les numéros de téléphone de clients dans un format de numéro de téléphone standard, à l’aide un <xref:System.Windows.Forms.MaskedTextBox> et en définissant le masque à un numéro de téléphone.

 Pendant cette procédure pas à pas, vous allez apprendre à :

-   Créer un nouveau **Application Windows Forms**.

-   Ajouter un nouveau **contrôle utilisateur** à votre projet.

-   Concevoir visuellement le contrôle utilisateur.

-   Implémenter l'attribut `DefaultBindingProperty`.

-   Créer un dataset avec le **Configuration de Source de données** Assistant.

-   Définir le **téléphone** colonne dans la **des Sources de données** fenêtre à utiliser le nouveau contrôle.

-   Créer un formulaire pour afficher des données dans le nouveau contrôle.

## <a name="prerequisites"></a>Prérequis
Cette procédure pas à pas utilise SQL Server Express LocalDB et la base de données Northwind.

1.  Si vous n’avez pas SQL Server Express LocalDB, installez-le à partir de la [page de téléchargement de SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), ou via le **le programme d’installation de Visual Studio**. Dans le programme d’installation Visual Studio, SQL Server Express LocalDB peut être installé dans le cadre de la **stockage de données et de traitement** charge de travail, ou sous la forme d’un composant individuel.

2.  Installer la base de données Northwind en procédant comme suit :

    1. Dans Visual Studio, ouvrez le **l’Explorateur d’objets SQL Server** fenêtre. (Explorateur d’objets SQL Server est installé dans le cadre de la **stockage de données et de traitement** charge de travail dans le programme d’installation Visual Studio.) Développez le **SQL Server** nœud. Avec le bouton droit sur votre instance de base de données locale et sélectionnez **nouvelle requête...** .

       Une fenêtre d’éditeur de requête s’ouvre.

    2. Copie le [script Transact-SQL de Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) dans le Presse-papiers. Ce script T-SQL crée la base de données Northwind à partir de zéro et la remplit avec des données.

    3. Collez le script T-SQL dans l’éditeur de requête, puis choisissez le **Execute** bouton.

       Après une courte période, la requête est terminée et la base de données Northwind est créé.

## <a name="create-a-windows-forms-application"></a>Créer une Application Windows Forms
 La première étape consiste à créer un **Application Windows Forms**.

#### <a name="to-create-the-new-windows-project"></a>Pour créer un projet Windows

1. Dans Visual Studio, sur le **fichier** menu, sélectionnez **nouveau**, **projet...** .

2. Développez le **Visual C#** ou **Visual Basic** dans le volet gauche, puis sélectionnez **de bureau Windows classique**.

3. Dans le volet central, sélectionnez le **l’application Windows Forms** type de projet.

4. Nommez le projet **SimpleControlWalkthrough**, puis choisissez **OK**.

     Le **SimpleControlWalkthrough** projet est créé et ajouté à **l’Explorateur de solutions**.

## <a name="add-a-user-control-to-the-project"></a>Ajouter un contrôle utilisateur au projet
 Cette procédure pas à pas crée un contrôle simple pouvant être lié aux données à partir d’un **contrôle utilisateur**, donc ajouter un **contrôle utilisateur** d’élément à la **SimpleControlWalkthrough** projet.

#### <a name="to-add-a-user-control-to-the-project"></a>Pour ajouter un contrôle utilisateur au projet

1.  À partir de la **projet** menu, choisissez **ajouter un contrôle utilisateur**.

2.  Type `PhoneNumberBox` dans la zone Nom, puis cliquez sur **ajouter**.

     Le **PhoneNumberBox** contrôle est ajouté à **l’Explorateur de solutions**et s’ouvre dans le concepteur.

## <a name="design-the-phonenumberbox-control"></a>Concevoir le contrôle PhoneNumberBox
 Cette procédure pas à pas s'appuie sur le <xref:System.Windows.Forms.MaskedTextBox> existant pour créer le contrôle `PhoneNumberBox`.

#### <a name="to-design-the-phonenumberbox-control"></a>Pour concevoir le contrôle PhoneNumberBox

1.  Faites glisser un <xref:System.Windows.Forms.MaskedTextBox> à partir de la **boîte à outils** sur l’aire de conception du contrôle utilisateur.

2.  Sélectionnez la balise active sur le <xref:System.Windows.Forms.MaskedTextBox> simplement faire glisser et choisissez **définir le masque**.

3.  Sélectionnez **numéro de téléphone** dans les **masque de saisie** boîte de dialogue, puis cliquez sur **OK** pour définir le masque.

## <a name="add-the-required-data-binding-attribute"></a>Ajoutez l’attribut DataBinding requis
 Pour des contrôles simples prenant en charge la liaison de données, implémentez l'attribut <xref:System.ComponentModel.DefaultBindingPropertyAttribute>.

#### <a name="to-implement-the-defaultbindingproperty-attribute"></a>Pour implémenter l'attribut DefaultBindingProperty

1.  Basculez le contrôle `PhoneNumberBox` sur le mode Code. (Sur le **vue** menu, choisissez **Code**.)

2.  Remplacez le code de `PhoneNumberBox` par le code suivant :

     [!code-csharp[VbRaddataDisplaying#3](../data-tools/codesnippet/CSharp/create-a-windows-forms-user-control-that-supports-simple-data-binding_1.cs)]
     [!code-vb[VbRaddataDisplaying#3](../data-tools/codesnippet/VisualBasic/create-a-windows-forms-user-control-that-supports-simple-data-binding_1.vb)]

3.  Dans le menu **Générer** , cliquez sur **Générer la solution**.

## <a name="create-a-data-source-from-your-database"></a>Créer une source de données à partir de votre base de données
 Cette étape utilise la **Configuration de Source de données**l’Assistant pour créer une source de données basée sur la `Customers` table dans la base de données Northwind. Vous devez avoir accès à l'exemple de base de données Northwind pour créer la connexion. Pour plus d’informations sur la configuration de la base de données Northwind, consultez [Comment : Install Sample Databases](../data-tools/installing-database-systems-tools-and-samples.md).

#### <a name="to-create-the-data-source"></a>Pour créer la source de données

1.  Dans le menu **Données** , cliquez sur **Afficher les sources de données**.

2.  Dans le **des Sources de données** fenêtre, sélectionnez **ajouter une nouvelle Source de données** pour démarrer le **Configuration de Source de données** Assistant.

3.  Sur le **choisir un Type de Source de données** page, sélectionnez **base de données**, puis cliquez sur **suivant**.

4.  Sur le **choisir votre connexion de données** page, effectuez l’une des opérations suivantes :

    -   Si une connexion de données à l’exemple de base de données Northwind est disponible dans la liste déroulante, sélectionnez-la.

    -   Sélectionnez **nouvelle connexion** pour lancer le **Ajouter/modifier la connexion** boîte de dialogue.

5.  Si votre base de données requiert un mot de passe, sélectionnez l’option pour inclure les données sensibles, puis cliquez sur **suivant**.

6.  Sur le **enregistrer la chaîne de connexion dans le fichier de Configuration de l’Application** , cliquez sur **suivant**.

7.  Sur le **choisir vos objets de base de données** page, développez le **Tables** nœud.

8.  Sélectionnez le `Customers` de table, puis cliquez sur **Terminer**.

     Le **NorthwindDataSet** est ajouté à votre projet et le `Customers` table apparaît dans le **des Sources de données** fenêtre.

## <a name="set-the-phone-column-to-use-the-phonenumberbox-control"></a>Définir la colonne phone pour utiliser le contrôle PhoneNumberBox
 Dans le **des Sources de données** fenêtre, vous pouvez définir le contrôle à créer avant de faire glisser des éléments vers votre formulaire.

#### <a name="to-set-the-phone-column-to-bind-to-the-phonenumberbox-control"></a>Pour définir la colonne Phone pour qu'elle soit liée au contrôle PhoneNumberBox

1.  Ouvrez **Form1** dans le concepteur.

2.  Développez le **clients** nœud dans le **des Sources de données** fenêtre.

3.  Cliquez sur la flèche déroulante la **clients** nœud, puis choisissez **détails** à partir de la liste de contrôle.

4.  Cliquez sur la flèche déroulante du **téléphone** colonne, puis choisissez **personnaliser**.

5.  Sélectionnez le **PhoneNumberBox** dans la liste des **contrôles associés** dans les **Options de personnalisation de l’interface utilisateur de données** boîte de dialogue.

6.  Cliquez sur la flèche déroulante du **téléphone** colonne, puis choisissez **PhoneNumberBox**.

## <a name="add-controls-to-the-form"></a>Ajouter des contrôles au formulaire
 Vous pouvez créer les contrôles liés aux données en faisant glisser des éléments depuis la **des Sources de données** fenêtre sur le formulaire.

#### <a name="to-create-data-bound-controls-on-the-form"></a>Pour créer des contrôlés liés aux données dans le formulaire

-   Faites glisser le **clients** nœud à partir de la **des Sources de données** fenêtre sur le formulaire et vérifiez que le `PhoneNumberBox` contrôle est utilisé pour afficher les données dans les `Phone` colonne.

     Les contrôles liés aux données assortis d'étiquettes descriptives apparaissent dans le formulaire, ainsi qu'une barre d'outils (<xref:System.Windows.Forms.BindingNavigator>) pour parcourir les enregistrements. A [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource>, et <xref:System.Windows.Forms.BindingNavigator> s’affichent dans la barre d’état du composant.

## <a name="run-the-application"></a>Exécuter l'application

#### <a name="to-run-the-application"></a>Pour exécuter l’application

-   Appuyez sur F5 pour exécuter l'application.

## <a name="next-steps"></a>Étapes suivantes
 Selon les exigences de votre application, vous pouvez exécuter différentes étapes après la création d’un contrôle prenant en charge la liaison de données. Les étapes ultérieures sont habituellement celles-ci :

-   Positionnement de vos contrôles personnalisés dans une bibliothèque de contrôles pour pouvoir les réutiliser dans d'autres applications.

-   Création de contrôles prenant en charge des scénarios de liaison de données plus complexes. Pour plus d’informations, consultez [créer un contrôle utilisateur Windows Forms qui prend en charge la liaison de données complexe](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md) et [créer un contrôle utilisateur Windows Forms qui prend en charge la liaison de données de recherche](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).

## <a name="see-also"></a>Voir aussi

- [Lier des contrôles Windows Forms à des données dans Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Définir le contrôle à créer lors d’une opération de glisser-déplacer à partir de la fenêtre Sources de données](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)