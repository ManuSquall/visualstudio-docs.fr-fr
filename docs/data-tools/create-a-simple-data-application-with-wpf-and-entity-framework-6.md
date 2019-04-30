---
title: Créer une application de données simple avec WPF et Entity Framework 6
ms.date: 08/22/2017
ms.topic: conceptual
dev_langs:
- CSharp
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: f5d65ff675329fdc714026ce6fe04ee3bd93086f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62568659"
---
# <a name="create-a-simple-data-application-with-wpf-and-entity-framework-6"></a>Créer une application de données simple avec WPF et Entity Framework 6

Cette procédure pas à pas montre comment créer une application de base « formulaires de données » dans Visual Studio. L’application utilise la base de données SQL Server locale, la base de données Northwind, Entity Framework 6 et Windows Presentation Foundation. Il montre comment effectuer la liaison de données base avec une vue maître-détail, et il a également un navigateur de liaison personnalisée avec des boutons **Move Next**, **Move Previous**, **déplacer au début de**, **Déplacer à la fin**, **mise à jour** et **supprimer**.

Cet article se concentre sur l’utilisation des outils de données dans Visual Studio et ne tente pas d’expliquer les technologies sous-jacentes dans n’importe quelle profondeur. Il suppose que vous avez une connaissance de base avec XAML, Entity Framework et SQL. Cet exemple ne montre pas plus d’architecture Model-View-ViewModel (MVVM), qui est un standard pour les applications WPF. Toutefois, vous pouvez copier ce code dans votre propre application MVVM avec peu de modifications.

## <a name="install-and-connect-to-northwind"></a>Installer et se connecter à Northwind

Cet exemple utilise SQL Server Express LocalDB et la base de données Northwind. Si le fournisseur de données ADO.NET pour ce produit prend en charge Entity Framework, il doit fonctionner tout aussi bien avec d’autres produits de base de données SQL.

1. Si vous n’avez pas SQL Server Express LocalDB, installez-le à partir de la [page de téléchargement de SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), ou via le **le programme d’installation de Visual Studio**. Dans le **le programme d’installation de Visual Studio**, vous pouvez installer SQL Server Express LocalDB dans le cadre de la **développement .NET desktop** charge de travail ou de manière individuelle.

2. Installer la base de données Northwind en suivant ces étapes :

    1. Dans Visual Studio, ouvrez le **Explorateur d’objets SQL Server** fenêtre. (**Explorateur d’objets SQL Server** est installé dans le cadre de la **stockage de données et de traitement** charge de travail dans le **le programme d’installation de Visual Studio**.) Développez le **SQL Server** nœud. Avec le bouton droit sur votre instance de base de données locale et sélectionnez **nouvelle requête**.

       Une fenêtre d’éditeur de requête s’ouvre.

    2. Copie le [script Transact-SQL de Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) dans votre Presse-papiers. Ce script T-SQL crée la base de données Northwind à partir de zéro et la remplit avec des données.

    3. Collez le script T-SQL dans l’éditeur de requête, puis choisissez le **Execute** bouton.

       Après une courte période, la requête est terminée en cours d’exécution et la base de données Northwind est créé.

3. [Ajouter de nouvelles connexions](../data-tools/add-new-connections.md) pour Northwind.

## <a name="configure-the-project"></a>Configurer le projet

1. Dans Visual Studio, créez un nouveau C# **application WPF** projet.

2. Ajoutez le package NuGet pour Entity Framework 6. Dans **l’Explorateur de solutions**, sélectionnez le nœud du projet. Dans le menu principal, choisissez **projet** > **gérer les Packages NuGet**.

     ![Gérer l’élément de menu de Packages NuGet](../data-tools/media/raddata_vs2015_manage_nuget_packages.png)

3. Dans le **Gestionnaire de Package NuGet**, cliquez sur le **Parcourir** lien. Entity Framework est probablement le paquet supérieur dans la liste. Cliquez sur **installer** dans le volet droit et suivez les invites. La fenêtre de sortie vous indique quand l’installation est terminée.

     ![Package NuGet Entity Framework](../data-tools/media/raddata_vs2015_nuget_ef.png)

4. Vous pouvez maintenant utiliser Visual Studio pour créer un modèle basé sur la base de données Northwind.

## <a name="create-the-model"></a>Créer le modèle

1. Avec le bouton droit sur le nœud de projet dans **l’Explorateur de solutions** et choisissez **ajouter** > **un nouvel élément**. Dans le volet gauche, sous le nœud c#, choisissez **données** et dans le volet central, choisissez **ADO.NET Entity Data Model**.

   ![Modèle Entity Framework un nouvel élément](../data-tools/media/raddata-ef-new-project-item.png)

2. Appeler le modèle `Northwind_model` et choisissez **OK**. L’**Assistant Entity Data Model** s’ouvre. Choisissez **Entity Framework Designer à partir de la base de données** puis cliquez sur **suivant**.

   ![Modèle EF à partir de la base de données](../data-tools/media/raddata-ef-model-from-database.png)

3. Dans l’écran suivant, choisissez votre LocalDB Northwind connexion et cliquez sur **suivant**.

4. Dans la page suivante de l’Assistant, choisissez les tables, procédures stockées et autres objets de base de données à inclure dans le modèle Entity Framework. Développez le nœud dbo dans l’arborescence et choisissez **clients**, **commandes**, et **Order Details**. Laissez les valeurs par défaut activées et cliquez sur **Terminer**.

    ![Choisissez les objets de base de données pour le modèle](../data-tools/media/raddata-choose-ef-objects.png)

5. L’Assistant génère les classes c# qui représentent le modèle Entity Framework. Les classes sont plain old classes c# et qui nous sont databind à l’interface utilisateur WPF. Le *.edmx* fichier décrit les relations et autres métadonnées qui associe les classes d’objets dans la base de données. Le *.tt* fichiers sont des modèles T4 qui génèrent le code qui fonctionne sur le modèle et enregistrer les modifications apportées à la base de données. Vous pouvez voir tous ces fichiers dans **l’Explorateur de solutions** sous le nœud Northwind_model :

      ![Fichiers de modèle EF de l’Explorateur de solutions](../data-tools/media/raddata-solution-explorer-ef-model-files.png)

    L’aire du concepteur pour le *.edmx* fichier vous permet de modifier certaines propriétés et les relations dans le modèle. Nous n’allons pas utiliser le concepteur dans cette procédure pas à pas.

6. Le *.tt* fichiers sont à usage général et que vous devez modifier un d’eux pour travailler avec la liaison de données WPF, ce qui oblige ObservableCollections. Dans **l’Explorateur de solutions**, développez le nœud Northwind_model jusqu'à ce que vous trouviez *Northwind_model.tt*. (Assurez-vous que vous n’êtes pas dans le *. Context.tt* fichier, qui est directement sous le *.edmx* fichier.)

   - Remplacez les deux occurrences de <xref:System.Collections.ICollection> avec <xref:System.Collections.ObjectModel.ObservableCollection%601>.

   - Remplacez la première occurrence de <xref:System.Collections.Generic.HashSet%601> avec <xref:System.Collections.ObjectModel.ObservableCollection%601> autour de la ligne 51. Ne remplacez pas la deuxième occurrence de HashSet.

   - Remplacer l’occurrence uniquement <xref:System.Collections.Generic> (autour de la ligne 431) avec <xref:System.Collections.ObjectModel>.

7. Appuyez sur **Ctrl**+**MAJ**+**B** pour générer le projet. Une fois la build terminée, les classes de modèle sont visibles par l’Assistant sources de données.

Vous êtes maintenant prêt à raccorder à ce modèle à la page XAML afin que vous pouvez afficher, parcourir et modifier les données.

## <a name="databind-the-model-to-the-xaml-page"></a>Lier le modèle à la page XAML

Il est possible d’écrire votre propre code de liaison de données, mais il est beaucoup plus facile permettre à Visual Studio de le faire pour vous.

1. Dans le menu principal, choisissez **projet** > **ajouter une nouvelle source de données** pour faire apparaître le **Assistant de Configuration de Source de données**. Choisissez **objet** étant donné que vous liez aux classes de modèle, pas à la base de données :

     ![Assistant de Configuration de Source de données avec l’objet Source](../data-tools/media/raddata-data-source-configuration-wizard-with-object-source.png)

2. Sélectionnez **client**. (Les sources pour les commandes sont automatiquement générés à partir de la propriété de navigation de commandes dans le client.)

     ![Ajouter des classes d’entité en tant que sources de données](../data-tools/media/raddata-add-entity-classes-as-data-sources.png)

3. Cliquez sur **Terminer**.

4. Accédez à *MainWindow.xaml* en mode Code. Nous gardons le XAML simple dans le cadre de cet exemple. Modifier le titre de MainWindow un nom plus descriptif et augmenter sa hauteur et sa largeur à 600 x 800 pour l’instant. Vous pouvez toujours le modifier ultérieurement. Maintenant, ajoutez ces définitions de trois lignes à la grille principale, une ligne pour les boutons de navigation, un pour les informations du client et un pour la grille qui montre leurs commandes :

    ```xaml
    <Grid.RowDefinitions>
            <RowDefinition Height="auto"/>
            <RowDefinition Height="auto"/>
            <RowDefinition Height="*"/>
        </Grid.RowDefinitions>
    ```

5. Ouvrez maintenant *MainWindow.xaml* afin que vous êtes l’affichage dans le concepteur. Cela entraîne le **des Sources de données** fenêtre s’affiche en tant qu’option dans la marge de la fenêtre Visual Studio à côté du **boîte à outils**. Cliquez sur l’onglet pour ouvrir la fenêtre, ou sinon, appuyez sur **MAJ**+**Alt**+**D** ou choisissez **vue**  >  **Autres Windows** > **des Sources de données**. Nous allons afficher chaque propriété de la classe de clients dans sa propre zone de texte individuelles. Tout d’abord, cliquez sur la flèche dans le **clients** liste déroulante et sélectionnez **détails**. Ensuite, faire glisser le nœud de la partie centrale de l’aire de conception afin que le concepteur sait que vous souhaitez qu’il figure dans la ligne du milieu. Si vous égarez il, vous pouvez spécifier la ligne manuellement plus tard dans le XAML. Par défaut, les contrôles sont placés verticalement dans un élément de grille, mais à ce stade, vous pouvez les organiser sur le formulaire comme vous le souhaitez. Par exemple, il peut être judicieux de placer le **nom** zone de texte en haut, au-dessus de l’adresse. L’exemple d’application pour cet article réorganise les champs et les réorganise en deux colonnes.

     ![Liaison de source de données de clients par des contrôles individuels](../data-tools/media/raddata-customers-data-source-binding-to-individual-controls.png)

     Dans le mode code, vous pouvez maintenant voir un nouveau `Grid` élément dans la ligne 1 (la ligne du milieu) de la grille parent. Le parent de grille a un `DataContext` attribut qui fait référence à un élément CollectionViewSource qui a été ajouté à la `Windows.Resources` élément. Étant donné ce contexte de données, lorsque la première zone de texte se lie à **adresse**, ce nom est mappé à la `Address` propriété en cours `Customer` objet dans CollectionViewSource.

    ```xaml
    <Grid DataContext="{StaticResource customerViewSource}">
    ```

6. Lorsqu’un client est visible dans la partie supérieure de la fenêtre, que vous souhaitez afficher ses commandes dans la partie inférieure de moitié. Affichez les commandes dans un contrôle d’affichage de grille unique. Pour la liaison de données maître / détail de fonctionner comme prévu, il est important que vous liez à la propriété Orders dans la classe de clients, pas pour le nœud de commandes distinct. Faites glisser la propriété Orders de la classe de clients à la moitié inférieure du formulaire, afin que le concepteur place dans la ligne 2 :

     ![Faire glisser des classes de commandes sous forme de grille](../data-tools/media/raddata-drag-orders-classes-as-grid.png)

7. Visual Studio a généré tout le code de liaison qui connecte les contrôles d’interface utilisateur aux événements dans le modèle. Il vous suffit, pour voir certaines données, consiste à écrire du code pour remplir le modèle. Tout d’abord, accédez à *MainWindow.xaml.cs* et ajouter un membre de données à la classe MainWindow pour le contexte de données. Cet objet, qui a été généré pour vous, agit comme un contrôle qui effectue le suivi des modifications et les événements dans le modèle. Vous allez également ajouter la logique de l’initialisation du constructeur. En haut de la classe doit ressembler à ceci :

     [!code-csharp[MainWindow#1](../data-tools/codesnippet/CSharp/CreateWPFDataApp/MainWindow.xaml.cs#1)]

     Ajouter un `using` directive pour System.Data.Entity à placer la méthode d’extension Load dans la portée :

     ```csharp
     using System.Data.Entity;
     ```

     Maintenant, faites défiler vers le bas et recherchez le `Window_Loaded` Gestionnaire d’événements. Notez que Visual Studio a ajouté un objet CollectionViewSource. Cela représente l’objet NorthwindEntities que vous avez sélectionné lorsque vous avez créé le modèle. Nous allons ajouter du code à `Window_Loaded` afin que l’intégralité de la méthode se présente désormais comme suit :

     [!code-csharp[Window_Loaded#2](../data-tools/codesnippet/CSharp/CreateWPFDataApp/MainWindow.xaml.cs#2)]

8. Appuyez sur **F5**. Vous devez voir les détails pour le premier client qui a été récupéré dans CollectionViewSource. Vous devez également voir leurs commandes dans la grille de données. La mise en forme n’est pas très bien, nous corrigeons donc que. Vous pouvez également créer un moyen pour afficher les autres enregistrements et effectuer des opérations CRUD de base.

## <a name="adjust-the-page-design-and-add-grids-for-new-customers-and-orders"></a>Ajuster la conception de page et ajouter des grilles pour les commandes et les nouveaux clients

La disposition par défaut générée par Visual Studio n’est pas idéale pour votre application, vous allez apporter certaines modifications manuellement dans le XAML. Vous devez également certaines « formes » (qui sont en fait des grilles) pour permettre aux utilisateurs d’ajouter un nouveau client ou une commande. Pour être en mesure d’ajouter un nouveau client et l’ordre, vous avez besoin d’un ensemble distinct de zones de texte qui ne sont pas liés aux données à le `CollectionViewSource`. Vous allez contrôler quelle grille de l’utilisateur voit à tout moment en définissant la propriété Visible dans les méthodes de gestionnaire. Enfin, vous ajoutez un bouton Supprimer pour chaque ligne dans la grille de commandes pour permettre aux utilisateurs de supprimer une commande individuelle.

Tout d’abord, ajoutez ces styles pour le `Windows.Resources` élément *MainWindow.xaml*:

```xaml
<Style x:Key="Label" TargetType="{x:Type Label}" BasedOn="{x:Null}">
    <Setter Property="HorizontalAlignment" Value="Left"/>
    <Setter Property="VerticalAlignment" Value="Center"/>
    <Setter Property="Margin" Value="3"/>
    <Setter Property="Height" Value="23"/>
</Style>
<Style x:Key="CustTextBox" TargetType="{x:Type TextBox}" BasedOn="{x:Null}">
    <Setter Property="HorizontalAlignment" Value="Right"/>
    <Setter Property="VerticalAlignment" Value="Center"/>
    <Setter Property="Margin" Value="3"/>
    <Setter Property="Height" Value="26"/>
    <Setter Property="Width" Value="120"/>
</Style>
```

Ensuite, remplacez l’intégralité de la grille externe avec ce balisage :

```xaml
<Grid>
     <Grid.RowDefinitions>
         <RowDefinition Height="auto"/>
         <RowDefinition Height="auto"/>
         <RowDefinition Height="*"/>
     </Grid.RowDefinitions>
     <Grid x:Name="existingCustomerGrid" Grid.Row="1" HorizontalAlignment="Left" Margin="5" Visibility="Visible" VerticalAlignment="Top" Background="AntiqueWhite" DataContext="{StaticResource customerViewSource}">
         <Grid.ColumnDefinitions>
             <ColumnDefinition Width="Auto" MinWidth="233"/>
             <ColumnDefinition Width="Auto" MinWidth="397"/>
         </Grid.ColumnDefinitions>
         <Grid.RowDefinitions>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
         </Grid.RowDefinitions>
         <Label Content="Customer ID:" Grid.Row="0" Style="{StaticResource Label}"/>
         <TextBox x:Name="customerIDTextBox" Grid.Row="0" Style="{StaticResource CustTextBox}"
                  Text="{Binding CustomerID, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Company Name:" Grid.Row="1" Style="{StaticResource Label}"/>
         <TextBox x:Name="companyNameTextBox" Grid.Row="1" Style="{StaticResource CustTextBox}"
                  Text="{Binding CompanyName, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Contact Name:" Grid.Row="2" Style="{StaticResource Label}"/>
         <TextBox x:Name="contactNameTextBox" Grid.Row="2" Style="{StaticResource CustTextBox}"
                  Text="{Binding ContactName, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Contact title:" Grid.Row="3" Style="{StaticResource Label}"/>
         <TextBox x:Name="contactTitleTextBox" Grid.Row="3" Style="{StaticResource CustTextBox}"
                  Text="{Binding ContactTitle, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Address:" Grid.Row="4" Style="{StaticResource Label}"/>
         <TextBox x:Name="addressTextBox" Grid.Row="4" Style="{StaticResource CustTextBox}"
                  Text="{Binding Address, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="City:" Grid.Column="1" Grid.Row="0" Style="{StaticResource Label}"/>
         <TextBox x:Name="cityTextBox" Grid.Column="1" Grid.Row="0" Style="{StaticResource CustTextBox}"
                  Text="{Binding City, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Country:" Grid.Column="1" Grid.Row="1" Style="{StaticResource Label}"/>
         <TextBox x:Name="countryTextBox" Grid.Column="1" Grid.Row="1" Style="{StaticResource CustTextBox}"
                  Text="{Binding Country, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Fax:" Grid.Column="1" Grid.Row="2" Style="{StaticResource Label}"/>
         <TextBox x:Name="faxTextBox" Grid.Column="1" Grid.Row="2" Style="{StaticResource CustTextBox}"
                  Text="{Binding Fax, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Phone:" Grid.Column="1" Grid.Row="3" Style="{StaticResource Label}"/>
         <TextBox x:Name="phoneTextBox" Grid.Column="1" Grid.Row="3" Style="{StaticResource CustTextBox}"
                  Text="{Binding Phone, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Postal Code:" Grid.Column="1" Grid.Row="4" VerticalAlignment="Center" Style="{StaticResource Label}"/>
         <TextBox x:Name="postalCodeTextBox" Grid.Column="1" Grid.Row="4" Style="{StaticResource CustTextBox}"
                  Text="{Binding PostalCode, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Region:" Grid.Column="1" Grid.Row="5" Style="{StaticResource Label}"/>
         <TextBox x:Name="regionTextBox" Grid.Column="1" Grid.Row="5" Style="{StaticResource CustTextBox}"
                  Text="{Binding Region, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
     </Grid>
     <Grid x:Name="newCustomerGrid" Grid.Row="1" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="5" DataContext="{Binding RelativeSource={RelativeSource FindAncestor, AncestorType={x:Type Window}}, Path=newCustomer, UpdateSourceTrigger=Explicit}" Visibility="Collapsed" Background="CornflowerBlue">
         <Grid.ColumnDefinitions>
             <ColumnDefinition Width="Auto" MinWidth="233"/>
             <ColumnDefinition Width="Auto" MinWidth="397"/>
         </Grid.ColumnDefinitions>
         <Grid.RowDefinitions>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
         </Grid.RowDefinitions>
         <Label Content="Customer ID:" Grid.Row="0" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_customerIDTextBox" Grid.Row="0" Style="{StaticResource CustTextBox}"
                  Text="{Binding CustomerID, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Company Name:" Grid.Row="1" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_companyNameTextBox" Grid.Row="1" Style="{StaticResource CustTextBox}"
                  Text="{Binding CompanyName, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true }"/>
         <Label Content="Contact Name:" Grid.Row="2" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_contactNameTextBox" Grid.Row="2" Style="{StaticResource CustTextBox}"
                  Text="{Binding ContactName, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Contact title:" Grid.Row="3" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_contactTitleTextBox" Grid.Row="3" Style="{StaticResource CustTextBox}"
                  Text="{Binding ContactTitle, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Address:" Grid.Row="4" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_addressTextBox" Grid.Row="4" Style="{StaticResource CustTextBox}"
                  Text="{Binding Address, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="City:" Grid.Column="1" Grid.Row="0" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_cityTextBox" Grid.Column="1" Grid.Row="0" Style="{StaticResource CustTextBox}"
                  Text="{Binding City, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Country:" Grid.Column="1" Grid.Row="1" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_countryTextBox" Grid.Column="1" Grid.Row="1" Style="{StaticResource CustTextBox}"
                  Text="{Binding Country, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Fax:" Grid.Column="1" Grid.Row="2" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_faxTextBox" Grid.Column="1" Grid.Row="2" Style="{StaticResource CustTextBox}"
                  Text="{Binding Fax, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Phone:" Grid.Column="1" Grid.Row="3" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_phoneTextBox" Grid.Column="1" Grid.Row="3" Style="{StaticResource CustTextBox}"
                  Text="{Binding Phone, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Postal Code:" Grid.Column="1" Grid.Row="4" VerticalAlignment="Center" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_postalCodeTextBox" Grid.Column="1" Grid.Row="4" Style="{StaticResource CustTextBox}"
                  Text="{Binding PostalCode, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Region:" Grid.Column="1" Grid.Row="5" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_regionTextBox" Grid.Column="1" Grid.Row="5" Style="{StaticResource CustTextBox}"
                  Text="{Binding Region, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
     </Grid>
     <Grid x:Name="newOrderGrid" Grid.Row="1" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="5" DataContext="{Binding Path=newOrder, Mode=TwoWay}" Visibility="Collapsed" Background="LightGreen">
         <Grid.ColumnDefinitions>
             <ColumnDefinition Width="Auto" MinWidth="233"/>
             <ColumnDefinition Width="Auto" MinWidth="397"/>
         </Grid.ColumnDefinitions>
         <Grid.RowDefinitions>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
         </Grid.RowDefinitions>
         <Label Content="New Order Form" FontWeight="Bold"/>
         <Label Content="Employee ID:"  Grid.Row="1" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_employeeIDTextBox" Grid.Row="1" Style="{StaticResource CustTextBox}"
                  Text="{Binding EmployeeID, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Order Date:"  Grid.Row="2" Style="{StaticResource Label}"/>
         <DatePicker x:Name="add_orderDatePicker" Grid.Row="2"  HorizontalAlignment="Right" Width="120"
                 SelectedDate="{Binding OrderDate, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true, UpdateSourceTrigger=PropertyChanged}"/>
         <Label Content="Required Date:" Grid.Row="3" Style="{StaticResource Label}"/>
         <DatePicker x:Name="add_requiredDatePicker" Grid.Row="3" HorizontalAlignment="Right" Width="120"
                  SelectedDate="{Binding RequiredDate, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true, UpdateSourceTrigger=PropertyChanged}"/>
         <Label Content="Shipped Date:"  Grid.Row="4"  Style="{StaticResource Label}"/>
         <DatePicker x:Name="add_shippedDatePicker"  Grid.Row="4"  HorizontalAlignment="Right" Width="120"
                 SelectedDate="{Binding ShippedDate, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true, UpdateSourceTrigger=PropertyChanged}"/>
         <Label Content="Ship Via:"  Grid.Row="5" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_ShipViaTextBox"  Grid.Row="5" Style="{StaticResource CustTextBox}"
                  Text="{Binding ShipVia, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Freight"  Grid.Row="6" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_freightTextBox" Grid.Row="6" Style="{StaticResource CustTextBox}"
                  Text="{Binding Freight, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
     </Grid>
     <DataGrid x:Name="ordersDataGrid" SelectionUnit="Cell" SelectionMode="Single" AutoGenerateColumns="False" CanUserAddRows="false" IsEnabled="True" EnableRowVirtualization="True" Width="auto" ItemsSource="{Binding Source={StaticResource customerOrdersViewSource}}" Margin="10,10,10,10" Grid.Row="2" RowDetailsVisibilityMode="VisibleWhenSelected">
         <DataGrid.Columns>
             <DataGridTemplateColumn>
                 <DataGridTemplateColumn.CellTemplate>
                     <DataTemplate>
                         <Button Content="Delete" Command="{StaticResource DeleteOrderCommand}" CommandParameter="{Binding}"/>
                     </DataTemplate>
                 </DataGridTemplateColumn.CellTemplate>
             </DataGridTemplateColumn>
             <DataGridTextColumn x:Name="customerIDColumn" Binding="{Binding CustomerID}" Header="Customer ID" Width="SizeToHeader"/>
             <DataGridTextColumn x:Name="employeeIDColumn" Binding="{Binding EmployeeID}" Header="Employee ID" Width="SizeToHeader"/>
             <DataGridTextColumn x:Name="freightColumn" Binding="{Binding Freight}" Header="Freight" Width="SizeToHeader"/>
             <DataGridTemplateColumn x:Name="orderDateColumn" Header="Order Date" Width="SizeToHeader">
                 <DataGridTemplateColumn.CellTemplate>
                     <DataTemplate>
                         <DatePicker SelectedDate="{Binding OrderDate, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true, UpdateSourceTrigger=PropertyChanged}"/>
                     </DataTemplate>
                 </DataGridTemplateColumn.CellTemplate>
             </DataGridTemplateColumn>
             <DataGridTextColumn x:Name="orderIDColumn" Binding="{Binding OrderID}" Header="Order ID" Width="SizeToHeader"/>
             <DataGridTemplateColumn x:Name="requiredDateColumn" Header="Required Date" Width="SizeToHeader">
                 <DataGridTemplateColumn.CellTemplate>
                     <DataTemplate>
                         <DatePicker SelectedDate="{Binding RequiredDate, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true, UpdateSourceTrigger=PropertyChanged}"/>
                     </DataTemplate>
                 </DataGridTemplateColumn.CellTemplate>
             </DataGridTemplateColumn>
             <DataGridTextColumn x:Name="shipAddressColumn" Binding="{Binding ShipAddress}" Header="Ship Address" Width="SizeToHeader"/>
             <DataGridTextColumn x:Name="shipCityColumn" Binding="{Binding ShipCity}" Header="Ship City" Width="SizeToHeader"/>
             <DataGridTextColumn x:Name="shipCountryColumn" Binding="{Binding ShipCountry}" Header="Ship Country" Width="SizeToHeader"/>
             <DataGridTextColumn x:Name="shipNameColumn" Binding="{Binding ShipName}" Header="Ship Name" Width="SizeToHeader"/>
             <DataGridTemplateColumn x:Name="shippedDateColumn" Header="Shipped Date" Width="SizeToHeader">
                 <DataGridTemplateColumn.CellTemplate>
                     <DataTemplate>
                         <DatePicker SelectedDate="{Binding ShippedDate, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true, UpdateSourceTrigger=PropertyChanged}"/>
                     </DataTemplate>
                 </DataGridTemplateColumn.CellTemplate>
             </DataGridTemplateColumn>
             <DataGridTextColumn x:Name="shipPostalCodeColumn" Binding="{Binding ShipPostalCode}" Header="Ship Postal Code" Width="SizeToHeader"/>
             <DataGridTextColumn x:Name="shipRegionColumn" Binding="{Binding ShipRegion}" Header="Ship Region" Width="SizeToHeader"/>
             <DataGridTextColumn x:Name="shipViaColumn" Binding="{Binding ShipVia}" Header="Ship Via" Width="SizeToHeader"/>
         </DataGrid.Columns>
     </DataGrid>
 </Grid>
```

## <a name="add-buttons-to-navigate-add-update-and-delete"></a>Ajouter des boutons pour naviguer, ajouter, mettre à jour et supprimer

Dans les applications Windows Forms, vous obtenez un objet de BindingNavigator avec des boutons pour parcourir les lignes dans une base de données et effectuer des opérations CRUD de base. WPF ne fournit pas un BindingNavigator, mais il est assez facile de créer un. Vous le faire avec les boutons à l’intérieur d’un StackPanel horizontal et associez les boutons avec les commandes qui sont liés aux méthodes dans le code-behind.

Il existe des parties sur quatre à la logique de commande : (1) les commandes (2) les liaisons, (3) les boutons et (4) les gestionnaires de commandes dans le code-behind.

### <a name="add-commands-bindings-and-buttons-in-xaml"></a>Ajouter des boutons, les liaisons et les commandes dans XAML

1. Tout d’abord, ajoutez les commandes dans le *MainWindow.xaml* de fichiers à l’intérieur du `Windows.Resources` élément :

    ```xaml
    <RoutedUICommand x:Key="FirstCommand" Text="First"/>
    <RoutedUICommand x:Key="LastCommand" Text="Last"/>
    <RoutedUICommand x:Key="NextCommand" Text="Next"/>
    <RoutedUICommand x:Key="PreviousCommand" Text="Previous"/>
    <RoutedUICommand x:Key="DeleteCustomerCommand" Text="Delete Customer"/>
    <RoutedUICommand x:Key="DeleteOrderCommand" Text="Delete Order"/>
    <RoutedUICommand x:Key="UpdateCommand" Text="Update"/>
    <RoutedUICommand x:Key="AddCommand" Text="Add"/>
    <RoutedUICommand x:Key="CancelCommand" Text="Cancel"/>
    ```

2. Mappe un CommandBinding un `RoutedUICommand` événement à une méthode dans le code-behind. Ajoutez ce `CommandBindings` élément après le `Windows.Resources` balise de fermeture :

    ```xaml
    <Window.CommandBindings>
        <CommandBinding Command="{StaticResource FirstCommand}" Executed="FirstCommandHandler"/>
        <CommandBinding Command="{StaticResource LastCommand}" Executed="LastCommandHandler"/>
        <CommandBinding Command="{StaticResource NextCommand}" Executed="NextCommandHandler"/>
        <CommandBinding Command="{StaticResource PreviousCommand}" Executed="PreviousCommandHandler"/>
        <CommandBinding Command="{StaticResource DeleteCustomerCommand}" Executed="DeleteCustomerCommandHandler"/>
        <CommandBinding Command="{StaticResource DeleteOrderCommand}" Executed="DeleteOrderCommandHandler"/>
        <CommandBinding Command="{StaticResource UpdateCommand}" Executed="UpdateCommandHandler"/>
        <CommandBinding Command="{StaticResource AddCommand}" Executed="AddCommandHandler"/>
        <CommandBinding Command="{StaticResource CancelCommand}" Executed="CancelCommandHandler"/>
    </Window.CommandBindings>
    ```

3. Maintenant, ajoutez le `StackPanel` avec le volet de navigation, ajouter, supprimer et mettre à jour des boutons. Tout d’abord, ajoutez ce style à `Windows.Resources`:

    ```xaml
    <Style x:Key="NavButton" TargetType="{x:Type Button}" BasedOn="{x:Null}">
        <Setter Property="FontSize" Value="24"/>
        <Setter Property="FontFamily" Value="Segoe UI Symbol"/>
        <Setter Property="Margin" Value="2,2,2,0"/>
        <Setter Property="Width" Value="40"/>
        <Setter Property="Height" Value="auto"/>
    </Style>
    ```

     Ensuite, collez ce code juste après le `RowDefinitions` externe `Grid` élément, vers le haut de la page XAML :

    ```xaml
    <StackPanel Orientation="Horizontal" Margin="2,2,2,0" Height="36" VerticalAlignment="Top" Background="Gainsboro" DataContext="{StaticResource customerViewSource}" d:LayoutOverrides="LeftMargin, RightMargin, TopMargin, BottomMargin">
        <Button Name="btnFirst" Content="|◄" Command="{StaticResource FirstCommand}" Style="{StaticResource NavButton}"/>
        <Button Name="btnPrev" Content="◄" Command="{StaticResource PreviousCommand}" Style="{StaticResource NavButton}"/>
        <Button Name="btnNext" Content="►" Command="{StaticResource NextCommand}" Style="{StaticResource NavButton}"/>
        <Button Name="btnLast" Content="►|" Command="{StaticResource LastCommand}" Style="{StaticResource NavButton}"/>
        <Button Name="btnDelete" Content="Delete Customer" Command="{StaticResource DeleteCustomerCommand}" FontSize="11" Width="120" Style="{StaticResource NavButton}"/>
        <Button Name="btnAdd" Content="New Customer" Command="{StaticResource AddCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>
        <Button Content="New Order" Name="btnNewOrder" FontSize="11" Width="80" Style="{StaticResource NavButton}" Click="NewOrder_click"/>
        <Button Name="btnUpdate" Content="Commit" Command="{StaticResource UpdateCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>
        <Button Content="Cancel" Name="btnCancel" Command="{StaticResource CancelCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>
    </StackPanel>
    ```

### <a name="add-command-handlers-to-the-mainwindow-class"></a>Ajouter des gestionnaires de commandes à la classe MainWindow

Le code-behind est minime, à l’exception des méthodes add et delete. Navigation est effectuée en appelant des méthodes sur la propriété View du CollectionViewSource. Le `DeleteOrderCommandHandler` montre comment effectuer une suppression en cascade sur une commande. Nous devons tout d’abord supprimer le Order_Details qui y sont associés. Le `UpdateCommandHandler` ajoute un nouveau client ou une commande à la collection, sinon met simplement à jour d’un client existant ou une commande avec les modifications apportée par l’utilisateur dans les zones de texte.

Ajoutez ces méthodes de gestionnaire à la classe MainWindow dans *MainWindow.xaml.cs*. Si votre CollectionViewSource pour la table Customers a un nom différent, vous devez ajuster le nom dans chacune de ces méthodes :

[!code-csharp[CommandHandlers#3](../data-tools/codesnippet/CSharp/CreateWPFDataApp/MainWindow.xaml.cs#3)]

## <a name="run-the-application"></a>Exécuter l'application

Pour démarrer le débogage, appuyez sur **F5**. Vous devez voir les données renseignées dans la grille, et les boutons de navigation doivent fonctionner comme prévu. Cliquez sur **valider** pour ajouter un nouveau client ou une commande pour le modèle après avoir entré les données. Cliquez sur **Annuler** pour la sauvegarde hors d’un nouveau client ou d’un nouveau bon de commande sans enregistrer les données. Vous pouvez apporter des modifications pour les clients existants et des commandes directement dans les zones de texte, et ces modifications sont écrites dans le modèle automatiquement.

## <a name="see-also"></a>Voir aussi

- [Outils de données Visual Studio pour .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
- [Documentation d’Entity Framework](/ef/)