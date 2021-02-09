---
title: Application de données simple avec WPF et Entity Framework 6
description: Dans cette procédure pas à pas, consultez Comment créer une application Forms-on-Data simple dans Visual Studio avec Windows Presentation Foundation (WPF) et Entity Framework 6.
ms.custom: SEO-VS-2020
ms.date: 08/22/2017
ms.topic: conceptual
dev_langs:
- CSharp
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 52c9d8ca4af6467c6db21be64083b5bf64af0b6a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99859188"
---
# <a name="create-a-simple-data-application-with-wpf-and-entity-framework-6"></a>Créer une application de données simple avec WPF et Entity Framework 6

Cette procédure pas à pas montre comment créer une application de base « formulaires sur des données » dans Visual Studio. L’application utilise SQL Server base de données locale, la base de données Northwind, Entity Framework 6 (pas Entity Framework Core) et Windows Presentation Foundation pour .NET Framework (pas .NET Core). Il montre comment effectuer une liaison de données de base avec un affichage maître-détail et un navigateur de liaisons personnalisé avec des boutons pour **déplacer** vers le bas, déplacer vers le **haut**, déplacer **vers le début**, **déplacer vers la fin**, **mettre à jour** et **supprimer**.

Cet article se concentre sur l’utilisation des outils de données dans Visual Studio et ne tente pas d’expliquer les technologies sous-jacentes en toute profondeur. Il part du principe que vous avez une connaissance de base de XAML, Entity Framework et SQL. Cet exemple ne montre pas non plus l’architecture MVVM (Model-View-ViewModel), qui est standard pour les applications WPF. Toutefois, vous pouvez copier ce code dans votre propre application MVVM avec quelques modifications.

## <a name="install-and-connect-to-northwind"></a>Installer et se connecter à Northwind

Cet exemple utilise SQL Server Express base de données locale et l’exemple de base de données Northwind. Si le fournisseur de données ADO.NET pour ce produit prend en charge Entity Framework, il doit également fonctionner avec d’autres produits de base de données SQL.

1. Si vous n’avez pas SQL Server Express base de données locale, installez-la à partir de la [page de téléchargement SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express)ou via le **Visual Studio installer**. Dans **Visual Studio Installer**, vous pouvez installer SQL Server Express LocalDB dans le cadre de la charge de travail **Développement .NET Desktop**, ou l’installer comme un composant seul.

2. Installez l’exemple de base de données Northwind en procédant comme suit :

    1. Dans Visual Studio, ouvrez la fenêtre de **Explorateur d’objets SQL Server** . (**Explorateur d’objets SQL Server** est installé dans le cadre de la charge de travail **stockage et traitement des données** dans le **Visual Studio installer**.) Développez le nœud **SQL Server** . Cliquez avec le bouton droit sur votre instance de base de données locale, puis sélectionnez **nouvelle requête**.

       Une fenêtre de l’éditeur de requête s’ouvre.

    2. Copiez le [script Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) dans le presse-papiers. Ce script T-SQL crée la base de données Northwind à partir de zéro et la remplit avec des données.

    3. Collez le script T-SQL dans l’éditeur de requête, puis choisissez le bouton **exécuter** .

       Après un bref laps de temps, l’exécution de la requête se termine et la base de données Northwind est créée.

3. [Ajoutez de nouvelles connexions](../data-tools/add-new-connections.md) pour Northwind.

## <a name="configure-the-project"></a>Configurer le projet

1. Dans Visual Studio, créez un projet d' **application WPF** C#.

2. Ajoutez le package NuGet pour Entity Framework 6. Dans **Explorateur de solutions**, sélectionnez le nœud du projet. Dans le menu principal, choisissez **projet**  >  **gérer les packages NuGet**.

     ![Élément de menu gérer les packages NuGet](../data-tools/media/raddata_vs2015_manage_nuget_packages.png)

3. Dans le **Gestionnaire de package NuGet**, cliquez sur le lien **Parcourir** . Entity Framework est probablement le package le plus haut dans la liste. Cliquez sur **installer** dans le volet droit et suivez les invites. La fenêtre sortie vous indique quand l’installation est terminée.

     ![Entity Framework package NuGet](../data-tools/media/raddata_vs2015_nuget_ef.png)

4. Vous pouvez maintenant utiliser Visual Studio pour créer un modèle basé sur la base de données Northwind.

## <a name="create-the-model"></a>Créer le modèle

1. Cliquez avec le bouton droit sur le nœud du projet dans **Explorateur de solutions** et choisissez **Ajouter**  >  **un nouvel élément**. Dans le volet gauche, sous le nœud C#, choisissez **données** , puis dans le volet central, choisissez **ADO.NET Entity Data Model**.

   ![Entity Framework un nouvel élément de modèle](../data-tools/media/raddata-ef-new-project-item.png)

2. Appelez le modèle `Northwind_model` et choisissez **OK**. L' **assistant Entity Data Model** s’ouvre. Choisissez le **Concepteur EF dans la base de données** , puis cliquez sur **suivant**.

   ![Modèle EF à partir de la base de données](../data-tools/media/raddata-ef-model-from-database.png)

3. Dans l’écran suivant, entrez ou choisissez votre connexion à la base de données locale Northwind (par exemple, (\MSSQLLocalDB), spécifiez la base de données Northwind, puis cliquez sur **suivant**.

4. Dans la page suivante de l’Assistant, choisissez les tables, les procédures stockées et les autres objets de base de données à inclure dans le modèle de Entity Framework. Développez le nœud dbo dans l’arborescence, puis choisissez **Customers**, **Orders** et **Order Details**. Laissez les valeurs par défaut activées et cliquez sur **Terminer**.

    ![Choisir les objets de base de données pour le modèle](../data-tools/media/raddata-choose-ef-objects.png)

5. L’Assistant génère les classes C# qui représentent le modèle de Entity Framework. Les classes sont des classes C# classiques et c’est ce que nous créons dans l’interface utilisateur WPF. Le fichier *. edmx* décrit les relations et les autres métadonnées qui associent les classes aux objets de la base de données. Les fichiers *. TT* sont des modèles T4 qui génèrent le code qui fonctionne sur le modèle et enregistre les modifications apportées à la base de données. Vous pouvez voir tous ces fichiers dans **Explorateur de solutions** sous le nœud Northwind_model :

      ![Explorateur de solutions les fichiers de modèle EF](../data-tools/media/raddata-solution-explorer-ef-model-files.png)

    L’aire du concepteur pour le fichier *. edmx* vous permet de modifier certaines propriétés et relations dans le modèle. Nous n’allons pas utiliser le concepteur dans cette procédure pas à pas.

6. Les fichiers *. TT* sont à usage général et vous devez en modifier l’un pour travailler avec la liaison de liaison WPF, ce qui requiert ObservableCollections. Dans **Explorateur de solutions**, développez le nœud Northwind_model jusqu’à ce que vous trouviez *Northwind_model. TT*. (Assurez-vous que vous n’êtes pas dans le *. Fichier Context.tt* , qui se trouve directement sous le fichier *. edmx* .)

   - Remplacez les deux occurrences de <xref:System.Collections.ICollection> par <xref:System.Collections.ObjectModel.ObservableCollection%601> .

   - Remplacez la première occurrence de <xref:System.Collections.Generic.HashSet%601> par <xref:System.Collections.ObjectModel.ObservableCollection%601> autour de la ligne 51. Ne remplacez pas la deuxième occurrence de HashSet.

   - Remplacez la seule occurrence de <xref:System.Collections.Generic> (autour de la ligne 431) par <xref:System.Collections.ObjectModel> .

7. Appuyez sur **CTRL** + **MAJ** + **B** pour générer le projet. Une fois la génération terminée, les classes de modèle sont visibles par l’Assistant sources de données.

Vous êtes maintenant prêt à raccorder ce modèle à la page XAML afin que vous puissiez afficher, parcourir et modifier les données.

## <a name="databind-the-model-to-the-xaml-page"></a>Lier le modèle à la page XAML

Il est possible d’écrire votre propre code DataBinding, mais il est beaucoup plus facile de laisser Visual Studio le faire pour vous.

1. Dans le menu principal, choisissez **projet**  >  **Ajouter une nouvelle source de données** pour afficher l **'Assistant Configuration de source de données**. Choisissez **objet** , car vous effectuez une liaison aux classes de modèle, et non à la base de données :

     ![Assistant Configuration de source de données avec source de l’objet](../data-tools/media/raddata-data-source-configuration-wizard-with-object-source.png)

2. Développez le nœud de votre projet, puis sélectionnez **Customer**. (Les sources des commandes sont générées automatiquement à partir de la propriété de navigation Orders dans Customer.)

     ![Ajouter des classes d’entité en tant que sources de données](../data-tools/media/raddata-add-entity-classes-as-data-sources.png)

3. Cliquez sur **Terminer**.

4. Accédez à *MainWindow. Xaml* en mode Code. Nous conservons le XAML simple dans le cadre de cet exemple. Remplacez le titre de MainWindow par un nom plus descriptif et augmentez sa hauteur et sa largeur à 600 x 800 pour l’instant. Vous pouvez toujours le modifier ultérieurement. Ajoutez maintenant ces trois définitions de ligne à la grille principale, une ligne pour les boutons de navigation, une pour les détails du client et une pour la grille qui affiche les commandes suivantes :

    ```xaml
        <Grid.RowDefinitions>
            <RowDefinition Height="auto"/>
            <RowDefinition Height="auto"/>
            <RowDefinition Height="*"/>
        </Grid.RowDefinitions>
    ```

5. Maintenant, ouvrez *MainWindow. Xaml* afin de l’afficher dans le concepteur. La fenêtre **sources de données** s’affiche alors en tant qu’option dans la marge de la fenêtre Visual Studio en regard de la **boîte à outils**. Cliquez sur l’onglet pour ouvrir la fenêtre, ou appuyez sur **MAJ** + **ALT** + **D** ou choisissez **Afficher** d'  >  **autres**  >  **sources de données** Windows. Nous allons afficher chaque propriété de la classe Customers dans sa propre zone de texte individuelle. Tout d’abord, cliquez sur la flèche dans la zone de liste déroulante **Customers** et choisissez **Details**. Ensuite, faites glisser le nœud sur la partie centrale de l’aire de conception afin que le concepteur sache que vous souhaitez qu’il figure dans la ligne du milieu. Si vous l’avez égaré, vous pouvez spécifier la ligne manuellement plus tard dans le code XAML. Par défaut, les contrôles sont placés verticalement dans un élément Grid, mais à ce stade, vous pouvez les réorganiser comme vous le souhaitez dans le formulaire. Par exemple, il peut être judicieux de placer la zone de texte **nom** en haut, au-dessus de l’adresse. L’exemple d’application de cet article réorganise les champs et les réorganise en deux colonnes.

     ![Liaison de la source de données des clients à des contrôles individuels](../data-tools/media/raddata-customers-data-source-binding-to-individual-controls.png)

     Dans le mode Code, vous pouvez maintenant voir un nouvel `Grid` élément dans la ligne 1 (la ligne du milieu) de la grille parente. La grille parente a un `DataContext` attribut qui fait référence à un CollectionViewSource qui a été ajouté à l' `Windows.Resources` élément. À partir de ce contexte de données, lorsque la première zone de texte se lie à **Address**, ce nom est mappé à la `Address` propriété dans l' `Customer` objet actuel dans le CollectionViewSource.

    ```xaml
    <Grid DataContext="{StaticResource customerViewSource}">
    ```

6. Quand un client est visible dans la moitié supérieure de la fenêtre, vous souhaitez afficher ses commandes dans la moitié inférieure. Vous affichez les commandes dans un seul contrôle d’affichage de grille. Pour que la liaison de données maître/détail fonctionne comme prévu, il est important que vous vous connectiez à la propriété Orders de la classe Customers, et non au nœud distinct Orders. Faites glisser la propriété Orders de la classe Customers vers la partie inférieure du formulaire, afin que le concepteur l’insère dans la ligne 2 :

     ![Faire glisser les classes Orders en tant que Grid](../data-tools/media/raddata-drag-orders-classes-as-grid.png)

7. Visual Studio a généré tout le code de liaison qui connecte les contrôles d’interface utilisateur aux événements du modèle. Pour voir certaines données, il vous suffit d’écrire du code pour remplir le modèle. Tout d’abord, accédez à *MainWindow.Xaml.cs* et ajoutez un membre de données à la classe MainWindow pour le contexte de données. Cet objet, qui a été généré pour vous, agit comme un contrôle qui effectue le suivi des modifications et des événements dans le modèle. Vous ajouterez également des membres de données CollectionViewSource pour les clients et les commandes, ainsi que la logique d’initialisation du constructeur associé. La partie supérieure de la classe doit ressembler à ceci :

     [!code-csharp[MainWindow#1](../data-tools/codesnippet/CSharp/CreateWPFDataApp/MainWindow.xaml.cs#1)]

     Ajoutez une `using` directive pour System. Data. Entity pour placer la méthode d’extension de charge dans la portée :

     ```csharp
     using System.Data.Entity;
     ```

     À présent, faites défiler le gestionnaire d’événements et recherchez-le `Window_Loaded` . Notez que Visual Studio a ajouté un objet CollectionViewSource. Cela représente l’objet NorthwindEntities que vous avez sélectionné lors de la création du modèle. Vous l’avez déjà ajoutée, donc vous n’en avez pas besoin ici. Remplaçons le code dans `Window_Loaded` afin que la méthode ressemble maintenant à ceci :

     [!code-csharp[Window_Loaded#2](../data-tools/codesnippet/CSharp/CreateWPFDataApp/MainWindow.xaml.cs#2)]

8. Appuyez sur **F5**. Vous devez voir les détails pour le premier client qui a été récupéré dans le CollectionViewSource. Vous devez également voir leurs commandes dans la grille de données. La mise en forme n’est pas très intéressante. nous allons donc résoudre le problème. Vous pouvez également créer un moyen d’afficher les autres enregistrements et d’effectuer des opérations CRUD de base.

## <a name="adjust-the-page-design-and-add-grids-for-new-customers-and-orders"></a>Ajuster la conception de la page et ajouter des grilles pour les nouveaux clients et les nouvelles commandes

La disposition par défaut générée par Visual Studio n’est pas idéale pour votre application. nous fournirons donc le XAML final ici pour copier dans votre code. Vous avez également besoin de « formulaires » (qui sont en fait des grilles) pour permettre à l’utilisateur d’ajouter un nouveau client ou une nouvelle commande. Pour pouvoir ajouter un nouveau client et une nouvelle commande, vous avez besoin d’un ensemble distinct de zones de texte qui ne sont pas liées aux données de `CollectionViewSource` . Vous allez contrôler la grille que l’utilisateur voit à un moment donné en définissant la propriété visible dans les méthodes de gestionnaire. Enfin, vous ajoutez un bouton supprimer à chaque ligne de la grille Orders pour permettre à l’utilisateur de supprimer une commande individuelle.

Tout d’abord, ajoutez ces styles à l' `Windows.Resources` élément dans *MainWindow. Xaml*:

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

Dans Windows Forms applications, vous pouvez obtenir un objet BindingNavigator avec des boutons permettant de naviguer dans les lignes d’une base de données et d’effectuer des opérations CRUD de base. WPF ne fournit pas de BindingNavigator, mais il est assez facile d’en créer un. Pour ce faire, vous pouvez utiliser des boutons à l’intérieur d’un StackPanel horizontal et associer les boutons à des commandes qui sont liées à des méthodes dans le code-behind.

La logique de commande comprend quatre parties : (1) les commandes, (2) les liaisons, (3) les boutons et (4) les gestionnaires de commandes dans le code-behind.

### <a name="add-commands-bindings-and-buttons-in-xaml"></a>Ajouter des commandes, des liaisons et des boutons en XAML

1. Tout d’abord, ajoutez les commandes dans le fichier *MainWindow. Xaml* à l’intérieur de l' `Windows.Resources` élément :

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

2. Une CommandBinding mappe un `RoutedUICommand` événement à une méthode dans le code-behind. Ajoutez cet `CommandBindings` élément après la `Windows.Resources` balise de fermeture :

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

3. À présent, ajoutez le `StackPanel` avec les boutons de navigation, d’ajout, de suppression et de mise à jour. Tout d’abord, ajoutez ce style à `Windows.Resources` :

    ```xaml
    <Style x:Key="NavButton" TargetType="{x:Type Button}" BasedOn="{x:Null}">
        <Setter Property="FontSize" Value="24"/>
        <Setter Property="FontFamily" Value="Segoe UI Symbol"/>
        <Setter Property="Margin" Value="2,2,2,0"/>
        <Setter Property="Width" Value="40"/>
        <Setter Property="Height" Value="auto"/>
    </Style>
    ```

     Ensuite, collez ce code juste après le `RowDefinitions` pour l' `Grid` élément externe, vers le haut de la page XAML :

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

Le code-behind est minimal, à l’exception des méthodes d’ajout et de suppression. La navigation est effectuée en appelant des méthodes sur la propriété View du CollectionViewSource. `DeleteOrderCommandHandler`Indique comment effectuer une suppression en cascade sur une commande. Nous devons tout d’abord supprimer les Order_Details qui y sont associés. Le `UpdateCommandHandler` ajoute un nouveau client ou une commande au regroupement, ou simplement met à jour un client existant ou une commande avec les modifications apportées par l’utilisateur dans les zones de texte.

Ajoutez ces méthodes de gestionnaire à la classe MainWindow dans *MainWindow.Xaml.cs*. Si votre CollectionViewSource pour la table Customers a un nom différent, vous devez ajuster le nom dans chacune de ces méthodes :

[!code-csharp[CommandHandlers#3](../data-tools/codesnippet/CSharp/CreateWPFDataApp/MainWindow.xaml.cs#3)]

## <a name="run-the-application"></a>Exécution de l'application

Pour démarrer le débogage, appuyez sur **F5**. Vous devez voir les données de client et de commande renseignées dans la grille, et les boutons de navigation devraient fonctionner comme prévu. Cliquez sur **valider** pour ajouter un nouveau client ou une commande au modèle une fois que vous avez entré les données. Cliquez sur **Annuler** pour revenir en arrière d’un nouveau formulaire de client ou de commande sans enregistrer les données. Vous pouvez apporter des modifications aux clients et aux commandes existants directement dans les zones de texte, et ces modifications sont écrites automatiquement dans le modèle.

## <a name="see-also"></a>Voir aussi

- [Outils de données Visual Studio pour .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
- [Documentation Entity Framework](/ef/)
