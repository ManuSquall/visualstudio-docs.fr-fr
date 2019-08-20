---
title: Créer une application de données simple avec WPF et Entity Framework 6 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 65929fab-5d78-4e04-af1e-cf4957f230f6
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: decb17be7caa4ea0a300ddb4378ac0ad11520109
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68145766"
---
# <a name="create-a-simple-data-application-with-wpf-and-entity-framework-6"></a>Créer une application de données simple avec WPF et Entity Framework 6
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cette procédure pas à pas montre comment créer une application de base « formulaires de données » dans Visual Studio avec SQL Server LocalDB, la base de données Northwind, Entity Framework 6 et Windows Presentation Foundation. Il montre comment effectuer la liaison de données base avec une vue maître-détail, et il a également un personnalisé « liaison Navigator » avec des boutons « Déplacer vers le bas », « Déplacer vers le haut, » « Déplacer vers le début, » « déplacer à la fin, » « Update » et « Supprimer ».  
  
 Cet article se concentre sur l’utilisation des outils de données dans Visual Studio et ne tente pas d’expliquer les technologies sous-jacentes dans n’importe quelle profondeur. Il suppose que vous avez une connaissance de base avec XAML, Entity Framework et SQL. Cet exemple ne montre pas plus d’architecture MVVM, qui est un standard pour les applications WPF. Toutefois, vous pouvez copier ce code dans votre propre application MVVM avec très peu de modifications.  
  
## <a name="install-and-connect-to-northwind"></a>Installer et se connecter à Northwind  
 Cet exemple utilise SQL Server Express LocalDB et la base de données Northwind. Cela devrait fonctionner avec d’autres produits de base de données SQL tout aussi bien si le fournisseur de données ADO.NET pour ce produit prend en charge Entity Framework.  
  
1. Si vous n’êtes déjà fait, installez SQL Server 2014 LocalDB Express 32 bits à partir de la [page de téléchargement des éditions de SQL Server](https://www.microsoft.com/sql-server/sql-server-editions-express).  
  
2. Installer la base de données Northwind en suivant les instructions fournies ici : [Installer les bases de données SQL Server](../data-tools/install-sql-server-sample-databases.md).  
  
3. [Ajouter de nouvelles connexions](../data-tools/add-new-connections.md) pour Northwind.  
  
## <a name="configure-the-project"></a>Configurer le projet  
  
1. Dans Visual Studio, choisissez **fichier &#124; nouveau projet** , puis créez une Application WPF c#.  
  
2. Ensuite, nous allons ajouter le package NuGet pour Entity Framework 6. Dans l’Explorateur de solutions, sélectionnez le nœud du projet. Dans le menu principal, choisissez **projet &#124; gérer les Packages NuGet...**  
  
     ![Gérer l’élément de menu de Packages NuGet](../data-tools/media/raddata-vs2015-manage-nuget-packages.png "raddata_vs2015_manage_nuget_packages")  
  
3. Dans le Gestionnaire de NuGet Package, cliquez sur le **Parcourir** lien. Entity Framework est probablement le paquet supérieur dans la liste. Cliquez sur **installer** dans le volet droit et suivez les invites. La fenêtre Sortie indique quand l’installation est terminée.  
  
     ![Le Package NuGet Entity Framework](../data-tools/media/raddata-vs2015-nuget-ef.png "raddata_vs2015_Nuget_EF")  
  
4. Nous pouvons maintenant utiliser Visual Studio pour créer un modèle basé sur la base de données Northwind.  
  
## <a name="create-the-model"></a>Créer le modèle  
  
1. Cliquez avec le bouton droit sur le nœud de projet dans l’Explorateur de solutions et choisissez **ajouter &#124; un nouvel élément**. Dans le volet gauche, sous le nœud c#, choisissez **données** et dans le volet central, choisissez **ADO.NET Entity Data Model**.  
  
    ![Élément Entity Framework modèle nouveau projet](../data-tools/media/raddata-ef-new-project-item.png "raddata EF nouvel élément de projet")  
  
2. Appeler le modèle `Northwind_model` et choisissez OK. Ceci fait apparaître la **Assistant Entity Data Model**. Choisissez **Entity Framework Designer à partir de la base de données** puis cliquez sur **suivant**.  
  
    ![Modèle EF à partir de la base de données](../data-tools/media/raddata-ef-model-from-database.png "raddata modèle EF à partir de la base de données")  
  
3. Dans l’écran suivant, choisissez votre LocalDB Northwind connexion et cliquez sur **suivant**.  
  
4. Dans la page suivante de l’Assistant, nous choisissons les tables, procédures stockées et autres objets de base de données à inclure dans le modèle Entity Framework. Développez le nœud dbo dans l’arborescence et choisissez Customers, Orders et Order Details. Conservez les valeurs par défaut activées et cliquez sur **Terminer**.  
  
    ![Choisissez les objets de base de données pour le modèle](../data-tools/media/raddata-choose-ef-objects.png "raddata choisir des objets de EF")  
  
5. L’Assistant génère les classes c# qui représentent le modèle Entity Framework. Il s’agit plain old classes c# et ils sont ce que nous allons databind à l’interface utilisateur WPF. Le fichier .edmx décrit les relations et autres métadonnées qui associe les classes d’objets dans la base de données.  Les fichiers .tt sont des modèles T4 qui génèrent le code qui fonctionnent sur le modèle et enregistrer les modifications dans la base de données. Vous pouvez voir ces fichiers dans l’Explorateur de solutions sous le nœud Northwind_model :  
  
    ![Fichiers de modèle de solution Explorer EF](../data-tools/media/raddata-solution-explorer-ef-model-files.png "raddata les fichiers de modèle EF de l’Explorateur de solutions")  
  
    L’aire du concepteur pour le fichier .edmx vous permet de modifier certaines propriétés et les relations dans le modèle. Nous n’allons pas utiliser le concepteur dans cette procédure pas à pas.  
  
6. Les fichiers .tt sont à usage général et nous devons ajuster un d’eux pour travailler avec la liaison de données WPF, ce qui oblige ObservableCollections.  Dans l’Explorateur de solutions, développez le nœud de Northwind_model jusqu'à ce que vous trouviez Northwind_model.tt. (Assurez-vous que vous êtes **pas** dans le *. Contexte fichier .tt qui est directement sous le fichier .edmx).  
  
   - Remplacez les deux occurrences de <xref:System.Collections.ICollection> avec <xref:System.Collections.ObjectModel.ObservableCollection%601>.  
  
   - Remplacez la première occurrence de <xref:System.Collections.Generic.HashSet%601> avec <xref:System.Collections.ObjectModel.ObservableCollection%601> autour de la ligne 51. Ne remplacez pas la deuxième occurrence de HashSet  
  
   - Remplacer l’occurrence uniquement <xref:System.Collections.Generic> (autour de la ligne 334) avec <xref:System.Collections.ObjectModel>.  
  
7. Appuyez sur **Ctrl + Maj + B** pour générer le projet. Une fois la build terminée, les classes de modèle sont visibles par l’Assistant sources de données.  
  
   Nous sommes désormais prêts raccorder à ce modèle à la page XAML afin que nous pouvons afficher, parcourir et modifier les données.  
  
## <a name="databind-the-model-to-the-xaml-page"></a>Lier le modèle à la page XAML  
 Il est possible d’écrire votre propre code de liaison de données, mais il est beaucoup plus facile permettre à Visual Studio de le faire pour vous.  
  
1. Dans le menu principal, choisissez **projet &#124; ajouter une nouvelle source de données** pour faire apparaître le **Assistant de Configuration de Source de données**. Choisissez **objet** , car nous effectuons une liaison aux classes de modèle, pas à la base de données :  
  
     ![Assistant de Configuration de Source de données avec la Source de l’objet](../data-tools/media/raddata-data-source-configuration-wizard-with-object-source.png "raddata Assistant de Configuration de Source de données avec l’objet Source")  
  
2. Sélectionnez le client.  (Sources pour les commandes sont automatiquement générées à partir de la propriété de navigation de commandes dans le client.)  
  
     ![Ajouter des classes d’entité en tant que sources de données](../data-tools/media/raddata-add-entity-classes-as-data-sources.png "raddata Add entity classes en tant que sources de données")  
  
3. Cliquez sur **terminer**  
  
4. Accédez à MainWindow.xaml en mode Code. Nous allons conserver le XAML très simple dans le cadre de cet exemple. Modifier le titre de MainWindow un nom plus descriptif et augmenter sa hauteur et sa largeur à 600 x 800 pour l’instant. Vous pouvez toujours le modifier ultérieurement. Maintenant, ajoutez ces définitions de trois lignes à la grille principale, une ligne pour les boutons de navigation, un pour les informations du client, un pour la grille qui montre leurs commandes :  
  
    ```xaml  
    <Grid.RowDefinitions>  
               <RowDefinition Height="auto"/>  
               <RowDefinition Height="auto"/>  
               <RowDefinition Height="*"/>  
           </Grid.RowDefinitions>  
    ```  
  
5. Ouvrez maintenant MainWindow.xaml afin que vous l’affichez dans le concepteur. Cela entraîne la fenêtre Sources de données apparaissent en tant qu’option dans la marge de la fenêtre Visual Studio en regard de la boîte à outils. Cliquez sur l’onglet pour ouvrir la fenêtre, ou sinon, appuyez sur **Maj + Alt + D** ou choisissez **vue &#124; Windows autres &#124; des Sources de données**. Nous allons afficher chaque propriété de la classe de clients dans sa propre zone de texte individuelles. Tout d’abord cliquer sur la flèche dans la zone de liste déroulante de clients et choisissez **détails**. Puis faire glisser le nœud de la partie centrale de l’aire de conception afin que le concepteur sait que vous souhaitez qu’il figure dans la ligne du milieu.  Si vous égarez il, vous pouvez spécifier la ligne manuellement plus tard dans le XAML. Par défaut, les contrôles sont placés verticalement dans un élément de grille, mais à ce stade vous pouvez les organiser sur le formulaire comme vous le souhaitez.  Par exemple, il peut être judicieux de placer la zone de texte Nom en haut, au-dessus de l’adresse. L’exemple d’application pour cet article réorganise les champs et les réorganise en deux colonnes.  
  
     ![Liaison de source de données de clients par des contrôles individuels](../data-tools/media/raddata-customers-data-source-binding-to-individual-controls.png "liaison de source de données de clients raddata par des contrôles individuels")  
  
     Dans le mode code, vous pouvez maintenant voir un nouveau `Grid` élément dans la ligne 1 (la ligne du milieu) de la grille parent. Le parent de grille a un `DataContext` attribut qui fait référence à un élément CollectionViewSource qui a été ajouté à la `Windows.Resources` élément. Étant donné ce contexte de données, lors de la première zone de texte, par exemple, est lié à ce nom de « Address » est mappée à la `Address` propriété en cours `Customer` objet dans CollectionViewSource.  
  
    ```xaml  
    <Grid DataContext="{StaticResource customerViewSource}">  
    ```  
  
6. Lorsqu’un client est visible dans la partie supérieure de la fenêtre, nous souhaitons afficher ses commandes dans la partie inférieure de moitié. Nous allons montrer les commandes dans un contrôle d’affichage de grille unique. Pour la liaison de données maître / détail de fonctionner comme prévu, il est important que nous lier à la propriété de commandes dans la classe de clients, pas pour le nœud de commandes distinct. Faites attention à l’illustration suivante ! Faites glisser la propriété Orders de la classe de clients à la moitié inférieure du formulaire, afin que le concepteur place dans la ligne 2 :  
  
     ![Faire glisser des classes de commandes sous forme de grille](../data-tools/media/raddata-drag-orders-classes-as-grid.png "raddata glisser Orders classes sous forme de grille")  
  
7. Visual Studio a généré tout le code de liaison qui connecte les contrôles d’interface utilisateur aux événements dans le modèle. Nous devons faire pour voir certaines données, il suffit d’écrire du code pour remplir le modèle. Première nous allons au MainWindow.xaml.cs, puis ajouter un membre de données à la classe MainWindow pour le contexte de données. Cet objet, qui a été généré pour nous, agit comme un contrôle qui effectue le suivi des modifications et les événements dans le modèle. Bien que nous ayons ici, nous allons ajouter deux membres que nous allons utiliser ultérieurement pour ajouter un nouveau client ou un nouvel ordre. Nous allons également ajouter la logique de l’initialisation du constructeur. Début de notre classe doit ressembler à ceci :  
  
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
  
     Ajouter un `using` directive pour System.Data.Entity à placer la méthode d’extension Load dans la portée :  
  
    ```csharp  
    using System.Data.Entity;  
    ```  
  
     Maintenant, faites défiler et trouver le Gestionnaire d’événements Window_Loaded. Notez que Visual Studio a ajouté un objet CollectionViewSource pour nous. Cela représente l’objet NorthwindEntities que nous avons sélectionnés lorsque nous avons créé le modèle. Nous allons ajouter code à Window_loaded afin que l’intégralité de la méthode se présente désormais comme suit :  
  
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
  
8. Appuyez sur **F5**. Vous devez voir les détails pour le premier client qui a été récupéré dans CollectionViewSource et leurs commandes dans la grille de données. La mise en forme n’est pas très bien, nous corrigeons donc que. créer un moyen pour afficher les autres enregistrements et effectuer des opérations CRUD de base.  
  
## <a name="adjust-the-page-design-and-add-grids-for-new-customers-and-orders"></a>Ajuster la conception de page et ajouter des grilles pour les commandes et les nouveaux clients  
 La disposition par défaut générée par Visual Studio n’est pas idéale pour notre application, nous allons apporter des modifications manuellement dans le XAML. Nous devrons également certaines « formes » (qui sont en fait des grilles) pour permettre aux utilisateurs d’ajouter un nouveau client ou un nouvel ordre.    Pour être en mesure d’ajouter un nouveau client et l’ordre, nous avons besoin d’un ensemble distinct de zones de texte qui ne sont pas liés aux données à le `CollectionViewSource`. Nous allons contrôler quelle grille de l’utilisateur voit à tout moment en définissant la propriété Visible dans les méthodes de gestionnaire.  
  
 Enfin, nous allons ajouter un bouton Supprimer pour chaque ligne dans la grille de commandes pour permettre aux utilisateurs de supprimer une commande individuelle.  
  
 Tout d’abord, ajoutez ces styles à Windows.Resources :  
  
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
 Dans les applications Windows Forms, vous obtenez un objet de BindingNavigator avec des boutons pour parcourir les lignes dans une base de données et effectuer des opérations CRUD de base. WPF ne fournit pas un BindingNavigator mais ils sont assez faciles à créer. Nous allons le faire avec des boutons à l’intérieur d’un StackPanel horizontal dans la ligne inférieure de la grille de la page, et nous allons associer les boutons de commandes qui sont liés aux méthodes dans le code-behind.  
  
 Il existe des parties sur quatre à la logique de commande : (1) les commandes (2) les liaisons, (3) les boutons et (4) les gestionnaires de commandes dans le code-behind.  
  
#### <a name="add-commands-bindings-and-buttons-in-xaml"></a>Ajouter des commandes, les liaisons et les boutons dans XAML  
  
1. Tout d’abord, nous allons ajouter les commandes dans notre fichier MainWindow.XAML dans l’élément Windows.Resources :  
  
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
  
2. CommandBinding est mappé à un événement RoutedUICommand à une méthode dans le code-behind. Ajoutez cet élément CommandBindings après la balise de fermeture de Windows.Resources :  
  
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
  
3. Maintenant nous allons ajouter le contrôle StackPanel avec le volet de navigation, ajouter, supprimer et mettre à jour des boutons. Tout d’abord, ajoutez ce style à Windows.Resources :  
  
    ```xaml  
    <Style x:Key="NavButton" TargetType="{x:Type Button}" BasedOn="{x:Null}">  
        <Setter Property="FontSize" Value="24"/>  
        <Setter Property="FontFamily" Value="Segoe UI Symbol"/>  
        <Setter Property="Margin" Value="2,2,2,0"/>  
        <Setter Property="Width" Value="40"/>  
        <Setter Property="Height" Value="auto"/>  
    </Style>  
    ```  
  
     Collez maintenant ce code juste après les paramètres RowDefinitions pour l’élément de grille externe vers le haut de la page XAML :  
  
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
  
1. Le code-behind est minime, à l’exception des méthodes add et delete. Notez que le volet de navigation est effectuée en appelant des méthodes sur la propriété View du CollectionViewSource. Le DeleteOrderCommandHandler montre comment effectuer une suppression en cascade sur une commande. Nous devons tout d’abord supprimer le Order_Details qui y sont associés. Le UpdateCommandHandler ajoute un nouveau client à la collection, faute de quoi met simplement à jour l’objet existant avec tout ce qui modifie l’utilisateur effectuée dans les zones de texte.  
  
2. Ajoutez ces méthodes de gestionnaire à la classe MainWindow dans MainWindow.xaml.cs, si votre CollectionViewSource pour la table Customers a un nom différent, puis vous devrez modifier le nom de chacun de ces méthodes :  
  
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
  
3. Appuyez sur **F5**. Vous devriez voir vos données et les boutons de navigation doivent fonctionner comme prévu. Cliquez sur « Valider » pour ajouter un nouveau client ou une commande pour le modèle après avoir entré les données.  Cliquez sur « Annuler » pour annuler un nouveau formulaire de client ou une nouvelle commande sans l’enregistrer. Vous pouvez apporter des modifications à des clients et des commandes directement dans les zones de texte existants, et ces modifications seront écrites automatiquement dans le modèle.  
  
## <a name="see-also"></a>Voir aussi  
 [Outils de données Visual Studio pour .NET](../data-tools/visual-studio-data-tools-for-dotnet.md) [Documentation d’Entity Framework](https://msdn.microsoft.com/data/ee712907.aspx)
