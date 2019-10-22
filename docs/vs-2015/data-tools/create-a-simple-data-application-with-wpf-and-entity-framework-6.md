---
title: Créer une application de données simple avec WPF et Entity Framework 6 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 65929fab-5d78-4e04-af1e-cf4957f230f6
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 403415eaf8a882efdd63fdb9a73b5489b91f2529
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651083"
---
# <a name="create-a-simple-data-application-with-wpf-and-entity-framework-6"></a>Créer une application de données simple avec WPF et Entity Framework 6
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ce Walkthough montre comment créer une application de base « formulaires de données » dans Visual Studio avec SQL Server base de données locale, la base de données Northwind, Entity Framework 6 et Windows Presentation Foundation. Il montre comment effectuer une liaison de données de base avec un affichage maître-détail et un « navigateur de liaisons » personnalisé avec des boutons pour « déplacer suivant », « déplacer vers le haut », « déplacer vers le début », « déplacer vers la fin », « mettre à jour » et « supprimer ».

 Cet article se concentre sur l’utilisation des outils de données dans Visual Studio et ne tente pas d’expliquer les technologies sous-jacentes en toute profondeur. Il part du principe que vous avez une connaissance de base de XAML, Entity Framework et SQL. Cet exemple ne montre pas non plus l’architecture MVVM, qui est standard pour les applications WPF. Toutefois, vous pouvez copier ce code dans votre propre application MVVM avec très peu de modifications.

## <a name="install-and-connect-to-northwind"></a>Installer et se connecter à Northwind
 Cet exemple utilise SQL Server Express base de données locale et l’exemple de base de données Northwind. Il doit fonctionner avec d’autres produits de base de données SQL également si le fournisseur de données ADO.NET pour ce produit prend en charge Entity Framework.

1. Si vous ne l’avez pas déjà fait, installez SQL Server 2014 de la base de données locale Express 32 à partir de la [page de téléchargement de SQL Server éditions](https://www.microsoft.com/sql-server/sql-server-editions-express).

2. Installez l’exemple de base de données Northwind en suivant les instructions fournies ici : [installer SQL Server exemples de bases de données](../data-tools/install-sql-server-sample-databases.md).

3. [Ajoutez de nouvelles connexions](../data-tools/add-new-connections.md) pour Northwind.

## <a name="configure-the-project"></a>Configurer le projet

1. Dans Visual Studio, choisissez **fichier &#124; nouveau projet** , puis créer une application C# WPF.

2. Ensuite, nous allons ajouter le package NuGet pour Entity Framework 6. Dans Explorateur de solutions, sélectionnez le nœud du projet. Dans le menu principal, choisissez **projet &#124; gérer les packages NuGet...**

     ![Élément de menu gérer les packages NuGet](../data-tools/media/raddata-vs2015-manage-nuget-packages.png "raddata_vs2015_manage_nuget_packages")

3. Dans le gestionnaire de package NuGet, cliquez sur le lien **Parcourir** . Entity Framework est probablement le package le plus haut dans la liste. Cliquez sur **installer** dans le volet droit et suivez les invites. La fenêtre sortie vous indiquera quand l’installation sera terminée.

     ![Entity Framework package NuGet](../data-tools/media/raddata-vs2015-nuget-ef.png "raddata_vs2015_Nuget_EF")

4. Nous pouvons maintenant utiliser Visual Studio pour créer un modèle basé sur la base de données Northwind.

## <a name="create-the-model"></a>Créer le modèle

1. Cliquez avec le bouton droit sur le nœud du projet dans Explorateur de solutions et choisissez **ajouter &#124; un nouvel élément**. Dans le volet gauche, sous le C# nœud, choisissez **données** , puis dans le volet central, choisissez **ADO.NET Entity Data Model**.

    ![Modèle de Entity Framework nouvel élément de projet](../data-tools/media/raddata-ef-new-project-item.png "raddata EF nouvel élément de projet")

2. Appelez le `Northwind_model` de modèle, puis choisissez OK. L' **assistant Entity Data Model**s’affiche. Choisissez le **Concepteur EF dans la base de données** , puis cliquez sur **suivant**.

    ![Modèle EF à partir de la base de données](../data-tools/media/raddata-ef-model-from-database.png "raddata EF modèle de la base de données")

3. Dans l’écran suivant, choisissez votre connexion de base de données locale Northwind, puis cliquez sur **suivant**.

4. Dans la page suivante de l’Assistant, nous choisissons les tables, les procédures stockées et autres objets de base de données à inclure dans le modèle de Entity Framework. Développez le nœud dbo dans l’arborescence, puis choisissez Customers, Orders et Order Details. Laissez les valeurs par défaut cochées, puis cliquez sur **Terminer**.

    ![Choisir les objets de base de données pour le modèle](../data-tools/media/raddata-choose-ef-objects.png "raddata choisir des objets EF")

5. L’Assistant génère les C# classes qui représentent le modèle de Entity Framework. Il s’agit de C# classes classiques et c’est ce que nous allons lier à l’interface utilisateur WPF. Le fichier. edmx décrit les relations et les autres métadonnées qui associent les classes aux objets de la base de données.  Les fichiers. TT sont des modèles T4 qui génèrent le code qui fonctionne sur le modèle et enregistrent les modifications apportées à la base de données. Vous pouvez voir tous ces fichiers dans Explorateur de solutions sous le nœud Northwind_model :

    ![Explorateur de solutions les fichiers de modèle EF](../data-tools/media/raddata-solution-explorer-ef-model-files.png "fichiers de modèle raddata Explorateur de solutions EF")

    L’aire du concepteur pour le fichier. edmx vous permet de modifier certaines propriétés et relations dans le modèle. Nous n’allons pas utiliser le concepteur dans cette procédure pas à pas.

6. Les fichiers. TT sont à usage général et nous devons en modifier l’un pour travailler avec la liaison de liaison WPF, ce qui nécessite ObservableCollections.  Dans Explorateur de solutions, développez le nœud Northwind_model jusqu’à ce que vous trouviez Northwind_model. TT. (Assurez-vous que vous n’êtes **pas** dans le *. Fichier context. TT qui se trouve directement sous le fichier. edmx).

   - Remplacez les deux occurrences de <xref:System.Collections.ICollection> par <xref:System.Collections.ObjectModel.ObservableCollection%601>.

   - Remplacez la première occurrence de <xref:System.Collections.Generic.HashSet%601> par <xref:System.Collections.ObjectModel.ObservableCollection%601> autour de la ligne 51. Ne pas remplacer la deuxième occurrence de HashSet

   - Remplacez la seule occurrence de <xref:System.Collections.Generic> (autour de la ligne 334) par <xref:System.Collections.ObjectModel>.

7. Appuyez sur **Ctrl + Maj + B** pour générer le projet. Une fois la génération terminée, les classes de modèle sont visibles par l’Assistant sources de données.

   Nous sommes maintenant prêts à raccorder ce modèle à la page XAML pour pouvoir afficher, parcourir et modifier les données.

## <a name="databind-the-model-to-the-xaml-page"></a>Lier le modèle à la page XAML
 Il est possible d’écrire votre propre code DataBinding, mais il est beaucoup plus facile de laisser Visual Studio le faire pour vous.

1. Dans le menu principal, choisissez **projet &#124; ajouter une nouvelle source de données** pour afficher l **'Assistant Configuration de source de données**. Choisissez **objet** , car nous créons une liaison avec les classes de modèle, pas avec la base de données :

     ![Assistant Configuration de source de données avec source de l’objet](../data-tools/media/raddata-data-source-configuration-wizard-with-object-source.png "Assistant Configuration de source de données raddata avec source de l’objet")

2. Sélectionnez Customer.  (Les sources des commandes sont générées automatiquement à partir de la propriété de navigation Orders dans Customer.)

     ![Ajouter des classes d’entité en tant que sources de données](../data-tools/media/raddata-add-entity-classes-as-data-sources.png "raddata ajouter des classes d’entité en tant que sources de données")

3. Cliquez sur **Terminer**

4. Accédez à MainWindow. XAML en mode Code. Nous allons garder le XAML très simple dans le cadre de cet exemple. Remplacez le titre de MainWindow par un nom plus descriptif et augmentez sa hauteur et sa largeur à 600 x 800 pour l’instant. Vous pouvez toujours le modifier ultérieurement. Ajoutez maintenant ces trois définitions de ligne à la grille principale, une ligne pour les boutons de navigation, une pour les détails du client, une pour la grille qui affiche les commandes suivantes :

    ```xaml
    <Grid.RowDefinitions>
               <RowDefinition Height="auto"/>
               <RowDefinition Height="auto"/>
               <RowDefinition Height="*"/>
           </Grid.RowDefinitions>
    ```

5. Maintenant, Ouvrez MainWindow. Xaml afin de l’afficher dans le concepteur. Cela entraîne l’affichage de la fenêtre sources de données en tant qu’option dans la marge de la fenêtre Visual Studio en regard de boîte à outils. Cliquez sur l’onglet pour ouvrir la fenêtre, ou appuyez sur **MAJ + ALT + D** ou choisissez **afficher &#124; d’autres &#124; sources de données Windows**. Nous allons afficher chaque propriété de la classe Customers dans sa propre zone de texte individuelle. Tout d’abord, cliquez sur la flèche dans la zone de liste déroulante Customers et choisissez **Details**. Faites ensuite glisser le nœud sur la partie centrale de l’aire de conception afin que le concepteur sache que vous souhaitez qu’il figure dans la ligne du milieu.  Si vous l’avez égaré, vous pouvez spécifier la ligne manuellement plus tard dans le code XAML. Par défaut, les contrôles sont placés verticalement dans un élément Grid, mais à ce stade, vous pouvez les réorganiser comme vous le souhaitez dans le formulaire.  Par exemple, il peut être judicieux de placer la zone de texte nom en haut, au-dessus de l’adresse. L’exemple d’application de cet article réorganise les champs et les réorganise en deux colonnes.

     ![Liaison de la source de données des clients à des contrôles individuels](../data-tools/media/raddata-customers-data-source-binding-to-individual-controls.png "liaison de la source de données des clients raddata à des contrôles individuels")

     Dans le mode Code, vous pouvez maintenant voir un nouvel élément `Grid` dans la ligne 1 (la ligne du milieu) de la grille parente. La grille parente a un attribut `DataContext` qui fait référence à un CollectionViewSource qui a été ajouté à l’élément `Windows.Resources`. À partir de ce contexte de données, lorsque la première zone de texte, par exemple, se lie à « Address », ce nom est mappé à la propriété `Address` dans l’objet `Customer` actuel dans le CollectionViewSource.

    ```xaml
    <Grid DataContext="{StaticResource customerViewSource}">
    ```

6. Quand un client est visible dans la moitié supérieure de la fenêtre, nous souhaitons voir ses commandes dans la moitié inférieure. Nous allons afficher les commandes dans un seul contrôle d’affichage de grille. Pour que la liaison de données maître/détail fonctionne comme prévu, il est important que nous créons une liaison avec la propriété Orders dans la classe Customers, et non dans le nœud distinct Orders. Soyez attentif à l’illustration suivante. Faites glisser la propriété Orders de la classe Customers vers la partie inférieure du formulaire, afin que le concepteur l’insère dans la ligne 2 :

     ![Faire glisser les classes Orders en tant que Grid](../data-tools/media/raddata-drag-orders-classes-as-grid.png "raddata faire glisser les classes Orders en tant que Grid")

7. Visual Studio a généré tout le code de liaison qui connecte les contrôles d’interface utilisateur aux événements du modèle. Tout ce que nous devons faire, afin de voir certaines données, est d’écrire du code pour remplir le modèle. Tout d’abord, accédez à MainWindow.xaml.cs et ajoutez un membre de données à la classe MainWindow pour le contexte de données. Cet objet, qui a été généré pour nous, agit comme un contrôle qui effectue le suivi des modifications et des événements dans le modèle. Alors que nous sommes ici, nous allons ajouter deux membres que nous utiliserons ultérieurement pour ajouter un nouveau client ou une nouvelle commande. Nous allons également ajouter la logique d’initialisation du constructeur. La partie supérieure de notre classe doit ressembler à ceci :

    ```csharp
    public partial class MainWindow : Window
       {
           public Customer newCustomer { get; set; }
           public Order newOrder { get; set; }

           NorthwindEntities context = new NorthwindEntities();
           CollectionViewSource custViewSource;
           CollectionViewSource ordViewSource;

           public MainWindow()
           {
               InitializeComponent();
               newCustomer = new Customer();
               newOrder = new Order();
               custViewSource = ((CollectionViewSource)
                   (FindResource("customerViewSource")));
               ordViewSource = ((CollectionViewSource)
                   (FindResource("customerOrdersViewSource")));
               DataContext = this;
           }
    ```

     Ajoutez une directive `using` pour System. Data. Entity pour placer la méthode d’extension Load dans la portée :

    ```csharp
    using System.Data.Entity;
    ```

     Faites défiler vers le dessous et recherchez le gestionnaire d’événements Window_Loaded. Notez que Visual Studio a ajouté un objet CollectionViewSource pour nous. Cela représente l’objet NorthwindEntities que nous avons sélectionné lors de la création du modèle. Nous allons ajouter du code à Window_loaded pour que l’ensemble de la méthode ressemble à ceci :

    ```csharp
    private void Window_Loaded(object sender, RoutedEventArgs e)
        {
            // Load is an extension method on IQueryable,
            // defined in the System.Data.Entity namespace.
            // This method enumerates the results of the query,
            // similar to ToList but without creating a list.
            // When used with Linq to Entities this method
            // creates entity objects and adds them to the context.
            context.Customers.Load();

            // After the data is loaded call the DbSet<T>.Local property
            // to use the DbSet<T> as a binding source.
            custViewSource.Source = context.Customers.Local;
        }
    ```

8. Appuyez sur **F5**. Vous devez voir les détails pour le premier client qui a été récupéré dans le CollectionViewSource et leurs commandes dans la grille de données. La mise en forme n’est pas très intéressante. nous allons donc résoudre le problème. vous pouvez ainsi afficher les autres enregistrements et effectuer des opérations CRUD de base.

## <a name="adjust-the-page-design-and-add-grids-for-new-customers-and-orders"></a>Ajuster la conception de la page et ajouter des grilles pour les nouveaux clients et les nouvelles commandes
 La disposition par défaut générée par Visual Studio n’est pas idéale pour notre application. nous allons donc apporter des modifications manuellement dans le code XAML. Nous aurons également besoin de « formulaires » (qui sont en fait des grilles) pour permettre à l’utilisateur d’ajouter un nouveau client ou une nouvelle commande.    Pour pouvoir ajouter un nouveau client et une nouvelle commande, nous avons besoin d’un ensemble distinct de zones de texte qui ne sont pas liées aux données du `CollectionViewSource`. Nous allons contrôler la grille que l’utilisateur voit à un moment donné en définissant la propriété visible dans les méthodes de gestionnaire.

 Enfin, nous allons ajouter un bouton supprimer à chaque ligne de la grille Orders pour permettre à un utilisateur de supprimer une commande individuelle.

 Tout d’abord, ajoutez ces styles à Windows. Resources :

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

 Ensuite, remplacez l’intégralité de la grille externe par cette balise :

```xaml
<Grid >
     <Grid.RowDefinitions>
         <RowDefinition Height="auto"/>
         <RowDefinition Height="auto"/>
         <RowDefinition Height="*"/>
     </Grid.RowDefinitions>
     <StackPanel  Orientation="Horizontal" Margin="2,2,2,0" Height="36" VerticalAlignment="Top" Background="Gainsboro" DataContext="{StaticResource customerViewSource}" d:LayoutOverrides="LeftMargin, RightMargin, TopMargin, BottomMargin">
         <Button Name="btnFirst" Content="|◄" Command="{StaticResource FirstCommand}" Style="{StaticResource NavButton}"  />
         <Button Name="btnPrev"  Content="◄" Command="{StaticResource PreviousCommand}" Style="{StaticResource NavButton}"/>
         <Button Name="btnNext"  Content="►" Command="{StaticResource NextCommand}"     Style="{StaticResource NavButton}"/>
         <Button Name="btnLast"  Content="►|" Command="{StaticResource LastCommand}" Style="{StaticResource NavButton}"/>
         <Button Name="btnDelete" Content="Delete Customer" Command="{StaticResource DeleteCustomerCommand}" FontSize="11" Width="120" Style="{StaticResource NavButton}"/>
         <Button  Name="btnAdd"   Content="New Customer"  Command="{StaticResource AddCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>
         <Button Content="New Order" Name="btnNewOrder" FontSize="11" Width="80" Style="{StaticResource NavButton}" Click="NewOrder_click"/>
         <Button Name="btnUpdate" Content="Commit" Command="{StaticResource UpdateCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>
         <Button Content="Cancel" Name="btnCancel"  Command="{StaticResource CancelCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>
     </StackPanel>
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
         <TextBox x:Name="customerIDTextBox"  Grid.Row="0" Style="{StaticResource CustTextBox}"
                  Text="{Binding CustomerID, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Company Name:"  Grid.Row="1" Style="{StaticResource Label}"/>
         <TextBox x:Name="companyNameTextBox"  Grid.Row="1" Style="{StaticResource CustTextBox}"
                  Text="{Binding CompanyName, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Contact Name:"  Grid.Row="2" Style="{StaticResource Label}"/>
         <TextBox x:Name="contactNameTextBox" Grid.Row="2" Style="{StaticResource CustTextBox}"
                  Text="{Binding ContactName, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Contact Title:"  Grid.Row="3" Style="{StaticResource Label}"/>
         <TextBox x:Name="contactTitleTextBox" Grid.Row="3" Style="{StaticResource CustTextBox}"
                  Text="{Binding ContactTitle, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Address:" Grid.Row="4" Style="{StaticResource Label}"/>
         <TextBox x:Name="addressTextBox" Grid.Row="4" Style="{StaticResource CustTextBox}"
                  Text="{Binding Address, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="City:" Grid.Column="1" Grid.Row="0"  Style="{StaticResource Label}"/>
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
         <TextBox x:Name="add_customerIDTextBox"  Grid.Row="0"  Style="{StaticResource CustTextBox}"
                  Text="{Binding CustomerID, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Company Name:"  Grid.Row="1" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_companyNameTextBox"  Grid.Row="1" Style="{StaticResource CustTextBox}"
                  Text="{Binding CompanyName, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true }"/>
         <Label Content="Contact Name:"  Grid.Row="2" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_contactNameTextBox" Grid.Row="2" Style="{StaticResource CustTextBox}"
                  Text="{Binding ContactName, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Contact Title:"  Grid.Row="3" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_contactTitleTextBox" Grid.Row="3" Style="{StaticResource CustTextBox}"
                  Text="{Binding ContactTitle, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Address:" Grid.Row="4" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_addressTextBox" Grid.Row="4" Style="{StaticResource CustTextBox}"
                  Text="{Binding Address, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="City:" Grid.Column="1" Grid.Row="0"  Style="{StaticResource Label}"/>
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
                         <Button Content="Delete"  Command="{StaticResource DeleteOrderCommand}" CommandParameter="{Binding}"/>
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
 Dans Windows Forms applications, vous pouvez obtenir un objet BindingNavigator avec des boutons permettant de naviguer dans les lignes d’une base de données et d’effectuer des opérations CRUD de base. WPF ne fournit pas de BindingNavigator, mais il est assez facile de le faire. Nous allons le faire avec des boutons à l’intérieur d’un contrôle StackPanel horizontal dans la ligne inférieure de la grille de la page, et nous allons associer les boutons aux commandes qui sont liées aux méthodes dans le code-behind.

 La logique de commande comprend quatre parties : (1) les commandes, (2) les liaisons, (3) les boutons et (4) les gestionnaires de commandes dans le code-behind.

#### <a name="add-commands-bindings-and-buttons-in-xaml"></a>Ajouter des commandes, des liaisons et des boutons en XAML

1. Tout d’abord, nous allons ajouter les commandes dans notre fichier MainWindow. XAML à l’intérieur de l’élément Windows. Resources :

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

2. Un CommandBinding mappe un événement RoutedUICommand à une méthode dans le code-behind. Ajoutez cet élément CommandBindings après la balise de fermeture Windows. Resources :

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

3. À présent, nous allons ajouter le StackPanel avec les boutons de navigation, d’ajout, de suppression et de mise à jour. Tout d’abord, ajoutez ce style à Windows. Resources :

    ```xaml
    <Style x:Key="NavButton" TargetType="{x:Type Button}" BasedOn="{x:Null}">
        <Setter Property="FontSize" Value="24"/>
        <Setter Property="FontFamily" Value="Segoe UI Symbol"/>
        <Setter Property="Margin" Value="2,2,2,0"/>
        <Setter Property="Width" Value="40"/>
        <Setter Property="Height" Value="auto"/>
    </Style>
    ```

     Collez maintenant ce code juste après le RowDefinitions pour l’élément de grille externe vers le haut de la page XAML :

    ```xaml
    <StackPanel  Orientation="Horizontal" Margin="2,2,2,0" Height="36" VerticalAlignment="Top" Background="Gainsboro" DataContext="{StaticResource customerViewSource}" d:LayoutOverrides="LeftMargin, RightMargin, TopMargin, BottomMargin">
        <Button Name="btnFirst" Content="|◄" Command="{StaticResource FirstCommand}" Style="{StaticResource NavButton}"  />
        <Button Name="btnPrev"  Content="◄" Command="{StaticResource PreviousCommand}" Style="{StaticResource NavButton}"/>
        <Button Name="btnNext"  Content="►" Command="{StaticResource NextCommand}"     Style="{StaticResource NavButton}"/>
        <Button Name="btnLast"  Content="►|" Command="{StaticResource LastCommand}" Style="{StaticResource NavButton}"/>
        <Button Name="btnDelete" Content="Delete Customer" Command="{StaticResource DeleteCustomerCommand}" FontSize="11" Width="120" Style="{StaticResource NavButton}"/>
        <Button  Name="btnAdd"   Content="New Customer"  Command="{StaticResource AddCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>
        <Button Content="New Order" Name="btnNewOrder" FontSize="11" Width="80" Style="{StaticResource NavButton}" Click="NewOrder_click"/>
        <Button Name="btnUpdate" Content="Commit" Command="{StaticResource UpdateCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>
        <Button Content="Cancel" Name="btnCancel"  Command="{StaticResource CancelCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>
    </StackPanel>
    ```

#### <a name="add-command-handlers-to-the-mainwindow-class"></a>Ajouter des gestionnaires de commandes à la classe MainWindow

1. Le code-behind est minimal, à l’exception des méthodes d’ajout et de suppression. Notez que la navigation est effectuée en appelant des méthodes sur la propriété View de CollectionViewSource. Le DeleteOrderCommandHandler montre comment effectuer une suppression en cascade sur une commande. Nous devons tout d’abord supprimer le Order_Details qui lui est associé. UpdateCommandHandler ajoute un nouveau client à la collection, ou simplement met à jour l’objet existant avec les modifications apportées par l’utilisateur dans les zones de texte.

2. Ajoutez ces méthodes de gestionnaire à la classe MainWindow dans MainWindow.xaml.cs, si votre CollectionViewSource pour la table Customers a un nom différent, vous devrez ajuster le nom dans chacune de ces méthodes :

    ```csharp
       private void LastCommandHandler(object sender, ExecutedRoutedEventArgs e)
    {
        custViewSource.View.MoveCurrentToLast();
    }

    private void PreviousCommandHandler(object sender, ExecutedRoutedEventArgs e)
    {
        custViewSource.View.MoveCurrentToPrevious();
    }

    private void NextCommandHandler(object sender, ExecutedRoutedEventArgs e)
    {
        custViewSource.View.MoveCurrentToNext();
    }

    private void FirstCommandHandler(object sender, ExecutedRoutedEventArgs e)
    {
        custViewSource.View.MoveCurrentToFirst();
    }

    private void DeleteCustomerCommandHandler(object sender, ExecutedRoutedEventArgs e)
    {
        // If existing window is visible, then delete the customer and all their orders.
        // In a real application, you should add warnings and allow a user to cancel the operation.
        var cur = custViewSource.View.CurrentItem as Customer;

        var cust = (from c in context.Customers
                    where c.CustomerID == cur.CustomerID
                    select c).FirstOrDefault();

        if (cust != null)
        {
            foreach (var ord in cust.Orders.ToList())
            {
                Delete_Order(ord);
            }
            context.Customers.Remove(cust);
        }
        context.SaveChanges();
        custViewSource.View.Refresh();
    }

    // Commit changes from the new customer form, the new order form,
    // or edits made to the existing customer form.
    private void UpdateCommandHandler(object sender, ExecutedRoutedEventArgs e)
    {
        if (newCustomerGrid.IsVisible)
        {
            // Create a new object because the old one
            // is being tracked by EF now.
            newCustomer = new Customer();
            newCustomer.Address = add_addressTextBox.Text;
            newCustomer.City = add_cityTextBox.Text;
            newCustomer.CompanyName = add_companyNameTextBox.Text;
            newCustomer.ContactName = add_contactNameTextBox.Text;
            newCustomer.ContactTitle = add_contactTitleTextBox.Text;
            newCustomer.Country = add_countryTextBox.Text;
            newCustomer.CustomerID = add_customerIDTextBox.Text;
            newCustomer.Fax = add_faxTextBox.Text;
            newCustomer.Phone = add_phoneTextBox.Text;
            newCustomer.PostalCode = add_postalCodeTextBox.Text;
            newCustomer.Region = add_regionTextBox.Text;

            // Perform very basic validation
            if (newCustomer.CustomerID.Length == 5)
            {
                // Insert the new customer at correct position:
                int len = context.Customers.Local.Count();
                int pos = len;
                for (int i = 0; i < len; ++i)
                {
                    if (String.CompareOrdinal(newCustomer.CustomerID, context.Customers.Local[i].CustomerID) < 0)
                    {
                        pos = i;
                        break;
                    }
                }
                context.Customers.Local.Insert(pos, newCustomer);
                custViewSource.View.Refresh();
                custViewSource.View.MoveCurrentTo(newCustomer);
            }
            else
            {
                MessageBox.Show("CustomerID must have 5 characters.");
            }

            newCustomerGrid.Visibility = Visibility.Collapsed;
            existingCustomerGrid.Visibility = Visibility.Visible;
        }
        else if (newOrderGrid.IsVisible)
        {
            // Order ID is auto-generated so we don't set it here.
            // For CustomerID, address, etc we use the values from current customer.
            // User can modify these in the datagrid after the order is entered.

            newOrder.OrderDate = add_orderDatePicker.SelectedDate;
            newOrder.RequiredDate = add_requiredDatePicker.SelectedDate;
            newOrder.ShippedDate = add_shippedDatePicker.SelectedDate;
            try
            {
                // Exercise for the reader if you are using Northwind:
                // Add the Northwind Shippers table to the model.
                // Acceptable ShipperID values are 1, 2, or 3.
                if (add_ShipViaTextBox.Text == "1" || add_ShipViaTextBox.Text == "2"
                    || add_ShipViaTextBox.Text == "3")
                {
                    newOrder.ShipVia = Convert.ToInt32(add_ShipViaTextBox.Text);
                }
                else
                {
                    MessageBox.Show("Shipper ID must be 1, 2, or 3 in Northwind.");
                    return;
                }
            }
            catch
            {
                MessageBox.Show("Ship Via must be convertible to int");
                return;
            }
            try
            {
                newOrder.Freight = Convert.ToDecimal(add_freightTextBox.Text);
            }
            catch
            {
                MessageBox.Show("Freight must be convertible to decimal.");
                return;
            }

            // Add the order into the EF model
            context.Orders.Add(newOrder);
            ordViewSource.View.Refresh();
        }

        // Save the changes, either for a new customer, a new order
        // or an edit in an existing customer or order
        context.SaveChanges();
    }

    // Sets up the form so that user can enter data. Data is later
    // saved when user clicks Commit.
    private void AddCommandHandler(object sender, ExecutedRoutedEventArgs e)
    {
        existingCustomerGrid.Visibility = Visibility.Collapsed;
        newOrderGrid.Visibility = Visibility.Collapsed;
        newCustomerGrid.Visibility = Visibility.Visible;

        // Clear all the text boxes before adding a new customer.
        foreach (var child in newCustomerGrid.Children)
        {
            var tb = child as TextBox;
            if (tb != null)
            {
                tb.Text = "";
            }
        }
    }

    private void NewOrder_click(object sender, RoutedEventArgs e)
    {
        var cust = custViewSource.View.CurrentItem as Customer;
        if (cust == null)
        {
            MessageBox.Show("No customer selected.");
            return;
        }

        newOrder.CustomerID = cust.CustomerID;

        // Get address and other mostly constant fields from
        // an existing order, if one exists
        var coll = custViewSource.Source as IEnumerable<Customer>;
        var lastOrder = (from c in coll
                         from ord in c.Orders
                         select ord).LastOrDefault();
        if (lastOrder != null)
        {
            newOrder.ShipAddress = lastOrder.ShipAddress;
            newOrder.ShipCity = lastOrder.ShipCity;
            newOrder.ShipCountry = lastOrder.ShipCountry;
            newOrder.ShipName = lastOrder.ShipName;
            newOrder.ShipPostalCode = lastOrder.ShipPostalCode;
            newOrder.ShipRegion = lastOrder.ShipRegion;
        }

        existingCustomerGrid.Visibility = Visibility.Collapsed;
        newCustomerGrid.Visibility = Visibility.Collapsed;
        newOrderGrid.UpdateLayout();
        newOrderGrid.Visibility = Visibility.Visible;
    }

    // Cancels any input into the new customer form
    private void CancelCommandHandler(object sender, ExecutedRoutedEventArgs e)
    {
        add_addressTextBox.Text = "";
        add_cityTextBox.Text = "";
        add_companyNameTextBox.Text = "";
        add_contactNameTextBox.Text = "";
        add_contactTitleTextBox.Text = "";
        add_countryTextBox.Text = "";
        add_customerIDTextBox.Text = "";
        add_faxTextBox.Text = "";
        add_phoneTextBox.Text = "";
        add_postalCodeTextBox.Text = "";
        add_regionTextBox.Text = "";

        existingCustomerGrid.Visibility = Visibility.Visible;
        newCustomerGrid.Visibility = Visibility.Collapsed;
        newOrderGrid.Visibility = Visibility.Collapsed;
    }

    private void Delete_Order(Order order)
    {
        // Find the order in the EF model.
        var ord = (from o in context.Orders.Local
                   where o.OrderID == order.OrderID
                   select o).FirstOrDefault();

        // Delete all the order_details that have
        // this Order as a foreign key
        foreach (var detail in ord.Order_Details.ToList())
        {
            context.Order_Details.Remove(detail);
        }

        // Now it's safe to delete the order.
        context.Orders.Remove(ord);
        context.SaveChanges();

        // Update the data grid.
        ordViewSource.View.Refresh();
    }

    private void DeleteOrderCommandHandler(object sender, ExecutedRoutedEventArgs e)
    {
        // Get the Order in the row in which the Delete button was clicked.
        Order obj = e.Parameter as Order;
        Delete_Order(obj);
    }
    ```

3. Appuyez sur **F5**. Vos données doivent s’afficher et les boutons de navigation doivent fonctionner comme prévu. Cliquez sur « valider » pour ajouter un nouveau client ou une commande au modèle une fois que vous avez entré les données.  Cliquez sur « Annuler » pour revenir en arrière d’un nouveau formulaire de client ou de commande sans l’enregistrer. Vous pouvez apporter des modifications aux clients et aux commandes existants directement dans les zones de texte, et ces modifications sont écrites automatiquement dans le modèle.

## <a name="see-also"></a>Voir aussi
 Documentation [Visual Studio Data Tools pour .net](../data-tools/visual-studio-data-tools-for-dotnet.md) [Entity Framework](https://msdn.microsoft.com/data/ee712907.aspx)
