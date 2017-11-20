---
title: "Créer une application de données simple avec WPF et Entity Framework 6 | Documents Microsoft"
ms.custom: 
ms.date: 08/22/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: CSharp
ms.assetid: 65929fab-5d78-4e04-af1e-cf4957f230f6
caps.latest.revision: "22"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 24d6401cae58b0bede44519900f6d72bd77ab2a9
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="create-a-simple-data-application-with-wpf-and-entity-framework-6"></a>Créer une application de données simple avec WPF et Entity Framework 6
Cette procédure pas à pas montre comment créer une application de base « formulaires de données » dans Visual Studio avec la base de données SQL Server locale, la base de données Northwind, Entity Framework 6 et Windows Presentation Foundation. Il montre comment effectuer la liaison de données base avec une vue maître / détail, et qu’il comporte également un personnalisé « liaison Navigator » avec des boutons « Déplacer vers le bas », « Move Previous, » « Déplacer au début, » « déplacer à la fin, » « Update » et « Delete ».  
  
 Cet article se concentre sur l’utilisation des outils de données dans Visual Studio et ne tente pas d’expliquer les technologies sous-jacentes dans n’importe quelle profondeur. Il suppose que vous avez une connaissance élémentaire XAML, Entity Framework et SQL. Cet exemple ne présente pas également architecture du modèle-affichage MVVM (Model), qui sont standard pour les applications WPF. Toutefois, vous pouvez copier ce code dans votre propre application MVVM avec très peu de modifications.  
  
## <a name="install-and-connect-to-northwind"></a>Installer et de se connecter à Northwind  
Cet exemple utilise SQL Server Express LocalDB et la base de données Northwind. Il doit fonctionner avec d’autres produits de base de données SQL tout aussi bien, si le fournisseur de données ADO.NET pour ce produit prend en charge Entity Framework.  
  
1.  Si vous n’avez pas SQL Server Express LocalDB, installez-le à partir de la [page de téléchargement des éditions de SQL Server](https://www.microsoft.com/en-us/server-cloud/Products/sql-server-editions/sql-server-express.aspx), ou via le **le programme d’installation de Visual Studio**. Dans le programme d’installation Visual Studio, SQL Server Express LocalDB peut être installé dans le cadre de la **développement de bureau .NET** charge de travail, ou sous la forme d’un composant individuel.  
  
2.  Installer la base de données Northwind en procédant comme suit :  

    1. Dans Visual Studio, ouvrez le **l’Explorateur d’objets SQL Server** fenêtre. (Explorateur d’objets SQL Server est installé dans le cadre de la **stockage de données et de traitement** charge de travail dans le programme d’installation Visual Studio.) Développez le **SQL Server** nœud. Avec le bouton droit sur votre instance de base de données locale et sélectionnez **nouvelle requête...** .  

       Une fenêtre d’éditeur de requête s’ouvre.  

    2. Copie le [script Transact-SQL de Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) dans le Presse-papiers. Ce script T-SQL crée la base de données Northwind à partir de zéro et la remplit avec des données.  

    3. Collez le script T-SQL dans l’éditeur de requête, puis choisissez le **Execute** bouton.  

       Après une courte période, la requête est terminée et la base de données Northwind est créé.  
  
3.  [Ajouter de nouvelles connexions](../data-tools/add-new-connections.md) de Northwind.  
  
## <a name="configure-the-project"></a>Configurer le projet  
  
1.  Dans Visual Studio, choisissez **fichier**, **nouveau**, **projet...**  , puis créez une Application WPF c#.  
  
2.  Ensuite, nous allons ajouter le package NuGet pour Entity Framework 6. Dans l’Explorateur de solutions, sélectionnez le nœud du projet. Dans le menu principal, choisissez **projet**, **gérer les Packages NuGet...**  
  
     ![Gérer les Packages NuGet menu élément](../data-tools/media/raddata_vs2015_manage_nuget_packages.png "raddata_vs2015_manage_nuget_packages")  
  
3.  Dans le Gestionnaire de NuGet Package, cliquez sur le **Parcourir** lien. Entity Framework est probablement le paquet supérieur dans la liste. Cliquez sur **installer** dans le volet droit et suivez les invites. La fenêtre Sortie indique quand l’installation est terminée.  
  
     ![Entity Framework NuGet Package](../data-tools/media/raddata_vs2015_nuget_ef.png "raddata_vs2015_Nuget_EF")  
  
4.  Maintenant, nous pouvons utiliser Visual Studio pour créer un modèle basé sur la base de données Northwind.  
  
## <a name="create-the-model"></a>Créer le modèle  
  
1.  Cliquez avec le bouton droit sur le nœud de projet dans l’Explorateur de solutions et choisissez **ajouter**, **un nouvel élément...** . Dans le volet gauche, sous le nœud C#, choisissez **données** et dans le volet central, sélectionnez **ADO.NET Entity Data Model**.  
  
     ![Entity Framework modèle d’élément de projet](../data-tools/media/raddata-ef-new-project-item.png "raddata EF nouvel élément de projet")  

  2.  Appelez le modèle `Northwind_model` et cliquez sur OK. Ceci fait apparaître la **Assistant Entity Data Model**. Choisissez **EF Designer à partir de la base de données** puis cliquez sur **suivant**.  
  
     ![Modèle EF à partir de la base de données](../data-tools/media/raddata-ef-model-from-database.png "raddata modèle EF à partir de la base de données")  
  
3.  Dans l’écran suivant, choisissez votre LocalDB Northwind connexion et cliquez sur **suivant**.  
  
4.  Dans la page suivante de l’Assistant, nous choisissons les tables, les procédures stockées et autres objets de base de données à inclure dans le modèle Entity Framework. Développez le nœud dbo dans l’arborescence et choisissez Customers, Orders et Order Details. Conservez les valeurs par défaut activées et cliquez sur **Terminer**.  
  
     ![Choisissez des objets de base de données pour le modèle](../data-tools/media/raddata-choose-ef-objects.png "raddata choisir des objets EF")  
  
5.  L’Assistant génère les classes c# qui représentent le modèle Entity Framework. Ceux-ci sont brut ancien classes c# et sont ce que nous allons databind à l’interface utilisateur WPF. Le fichier .edmx décrit les relations et autres métadonnées qui associe les classes d’objets dans la base de données.  Les fichiers .tt sont des modèles T4 qui génèrent le code qui ne fonctionne pas sur le modèle et enregistrer les modifications dans la base de données. Vous pouvez voir ces fichiers dans l’Explorateur de solutions sous le nœud Northwind_model :  

       ![Fichiers de modèle EF de l’Explorateur de solutions](../data-tools/media/raddata-solution-explorer-ef-model-files.png "raddata les fichiers de modèle EF de l’Explorateur de solutions")  
  
     L’aire du concepteur pour le fichier .edmx vous permet de modifier certaines propriétés et les relations dans le modèle. Nous n’allons pas à utiliser le concepteur dans cette procédure pas à pas.  
  
6.  Les fichiers .tt sont à usage général et nous devons modifier un d’eux pour travailler avec la liaison de données WPF, ce qui nécessite ObservableCollections.  Dans l’Explorateur de solutions, développez le nœud de Northwind_model jusqu'à ce que vous trouviez Northwind_model.tt. (Vérifiez que vous êtes **pas** dans le *. Contexte fichier .tt qui est directement sous le fichier .edmx).  
  
    -   Remplacez les deux occurrences de <xref:System.Collections.ICollection> avec <xref:System.Collections.ObjectModel.ObservableCollection%601>.  
  
    -   Remplacer la première occurrence de <xref:System.Collections.Generic.HashSet%601> avec <xref:System.Collections.ObjectModel.ObservableCollection%601> autour de la ligne 51. Ne remplacez pas la deuxième occurrence de HashSet  
  
    -   Remplacer l’occurrence uniquement <xref:System.Collections.Generic> (autour de la ligne 431) avec <xref:System.Collections.ObjectModel>.  
  
7.  Appuyez sur **Ctrl + Maj + B** pour générer le projet. Lorsque la build se termine, les classes de modèle sont visibles par l’Assistant sources de données.  
  
Maintenant, nous sommes prêts à raccorder à ce modèle dans la page XAML afin que nous pouvons afficher, parcourir et modifier les données.  
  
## <a name="databind-the-model-to-the-xaml-page"></a>DataBind le modèle dans la page XAML  
 Il est possible d’écrire votre propre code de liaison de données, mais il est beaucoup plus facile pour permettre à Visual Studio le faire pour vous.  
  
1.  Dans le menu principal, choisissez **projet > Ajouter une nouvelle source de données** pour afficher les **Assistant de Configuration de Source de données**. Choisissez **objet** étant donné que nous créons une liaison avec les classes de modèle, pas à la base de données :  
  
     ![Assistant de Configuration de Source de données avec la Source de l’objet](../data-tools/media/raddata-data-source-configuration-wizard-with-object-source.png "raddata Assistant de Configuration de Source de données avec l’objet Source")  
  
2.  Sélectionnez le client.  (Les sources pour les commandes sont automatiquement générées à partir de la propriété de navigation des commandes client.)  
  
     ![Ajouter des classes d’entité en tant que sources de données](../data-tools/media/raddata-add-entity-classes-as-data-sources.png "raddata ajouter une entité classes en tant que sources de données")  
  
3.  Cliquez sur **terminer**  
  
4.  Accédez à MainWindow.xaml en mode Code. Nous allons conserver le code XAML simple dans le cadre de cet exemple. Modifier le titre de MainWindow un nom plus descriptif et augmenter sa hauteur et sa largeur à 800 x 600 pour le moment. Vous pouvez toujours la modifier ultérieurement. Maintenant, ajoutez ces définitions de trois lignes à la grille principale, une ligne pour les boutons de navigation, l’autre pour les informations du client, un pour la grille qui indique leurs commandes :  

    ```xaml  
    <Grid.RowDefinitions>  
            <RowDefinition Height="auto"/>  
            <RowDefinition Height="auto"/>  
            <RowDefinition Height="*"/>  
        </Grid.RowDefinitions>
    ```

5.  Ouvrez maintenant MainWindow.xaml afin que vous l’affichez dans le concepteur. Cela entraîne la fenêtre Sources de données à afficher en tant qu’option dans la marge de la fenêtre Visual Studio en regard de la boîte à outils. Cliquez sur l’onglet pour ouvrir la fenêtre, ou sinon, appuyez sur **Maj + Alt + D** ou choisissez **View &#124; Autres fenêtres &#124; Sources de données**. Nous allons pour afficher chaque propriété dans la classe de clients dans sa propre zone de texte individuelles. Tout d’abord cliquer sur la flèche dans la zone de liste déroulante de clients et choisissez **détails**. Faites glisser le nœud sur la partie centrale de l’aire de conception pour que le concepteur sait que vous souhaitez qu’il figure dans la ligne du milieu.  Si vous l’égarer, vous pouvez spécifier la ligne manuellement plus tard dans le code XAML. Par défaut, les contrôles sont placés verticalement dans un élément de grille, mais à ce stade vous pouvez les organiser sur le formulaire comme vous le souhaitez.  Par exemple, il peut être utile pour placer la zone de texte Nom en haut, au-dessus de l’adresse. L’exemple d’application pour cet article réorganise les champs et les réorganise dans deux colonnes.  
  
     ![Liaison de source de données de clients à des contrôles individuels](../data-tools/media/raddata-customers-data-source-binding-to-individual-controls.png "liaison de source de données de clients raddata par des contrôles individuels")  
  
     Dans la vue code, vous pouvez maintenant voir un nouveau `Grid` élément dans la ligne 1 (la ligne du milieu) de la grille du parent. Le parent de grille a une `DataContext` attribut qui fait référence à un CollectionViewSource qui a été ajouté à la `Windows.Resources` élément. Étant donné ce contexte de données, lors de la première zone de texte, par exemple, est lié à ce nom de « Address » est mappée à la `Address` propriété en cours `Customer` objet dans CollectionViewSource.  
  
    ```xaml  
    <Grid DataContext="{StaticResource customerViewSource}">  
    ```  

6.  Lorsqu’un client est visible dans la partie supérieure de la fenêtre, que vous souhaitez voir leurs commandes dans la partie inférieure de moitié. Nous allons montrer les commandes dans un contrôle d’affichage de grille. Pour la liaison de données maître / détail à fonctionner comme prévu, il est important que nous lier la propriété de commandes dans la classe de clients, pas pour le nœud de commandes distincte. Faites attention à l’illustration suivante. Faites glisser la propriété de commandes de la classe de clients à la moitié inférieure du formulaire, afin que le concepteur place dans la ligne 2 :  
  
     ![Faites glisser les classes de commandes sous forme de grille](../data-tools/media/raddata-drag-orders-classes-as-grid.png "raddata glisser commandes classes sous forme de grille")  
  
7.  Visual Studio a généré tout le code de liaison qui connecte les contrôles d’interface utilisateur aux événements dans le modèle. Il nous suffit, pour afficher des données, consiste à écrire du code pour remplir le modèle. Première nous allons atteindre MainWindow.xaml.cs et ajouter un membre de données à la classe MainWindow pour le contexte de données. Cet objet, qui a été généré pour nous, agit comme un contrôle qui effectue le suivi des modifications et des événements dans le modèle. Nous allons également ajouter la logique d’initialisation du constructeur. Début de notre classe doit ressembler à ceci :  
  
     [!code-csharp[MainWindow#1](../data-tools/codesnippet/CSharp/CreateWPFDataApp/MainWindow.xaml.cs#1)]  
     
     Ajouter un `using` directive System.Data.Entity à placer la méthode d’extension de charge dans la portée :  
  
     ```csharp
     using System.Data.Entity;  
     ```  

     Maintenant, faites défiler la liste et trouver le Gestionnaire d’événements Window_Loaded. Notez que Visual Studio a ajouté un objet CollectionViewSource pour nous. Représente l’objet NorthwindEntities que nous avons sélectionnés lorsque nous avons créé le modèle. Nous allons ajouter code à Window_Loaded afin que la totalité de la méthode ressemble à ceci :  

     [!code-csharp[Window_Loaded#2](../data-tools/codesnippet/CSharp/CreateWPFDataApp/MainWindow.xaml.cs#2)]  

8.  Appuyez sur **F5**. Vous devez voir les détails pour le premier client qui a été récupéré dans CollectionViewSource. Vous devez également voir leurs commandes dans la grille de données. La mise en forme n’est pas parfaite, nous allons donc que mettre à jour. Nous allons également créer un moyen pour afficher les autres enregistrements et effectuer des opérations CRUD de base.  
  
## <a name="adjust-the-page-design-and-add-grids-for-new-customers-and-orders"></a>Ajuster la mise en page et d’ajouter des grilles pour les commandes et les nouveaux clients  
La disposition par défaut générée par Visual Studio n’est pas idéale pour notre application, nous allons apporter des modifications manuellement dans le code XAML. Nous devrons également certaines « forms » (qui sont en fait des grilles) pour permettre à l’utilisateur Ajouter un nouveau client ou une commande. Pour être en mesure d’ajouter un nouveau client et l’ordre, nous avons besoin d’un ensemble de zones de texte qui ne sont pas liés aux données à le `CollectionViewSource`. Nous allons contrôler quels grille l’utilisateur voit à tout moment en définissant la propriété Visible dans les méthodes du gestionnaire. Enfin, nous allons ajouter un bouton Supprimer pour chaque ligne dans la grille de commandes pour permettre à l’utilisateur supprimer une commande individuelle.  
  
Tout d’abord, ajoutez ces styles à l’élément Windows.Resources dans MainWindow.xaml :  
  
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
  
Ensuite, remplacez l’intégralité de la grille externe par ce balisage :  
  
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
 Dans les applications Windows Forms, vous obtenez un objet BindingNavigator avec des boutons pour parcourir les lignes dans une base de données et effectuer des opérations CRUD de base. WPF ne fournit pas un BindingNavigator, mais il est assez facile de créer un. Nous allons faire avec des boutons à l’intérieur d’un StackPanel horizontal, et nous allons associer les boutons avec les commandes qui sont liés aux méthodes dans le code-behind.  
  
 La logique de commande sur quatre parties : (1) les commandes, (2) les liaisons, (3) les boutons et (4) les gestionnaires de commandes dans le code-behind.  
  
#### <a name="add-commands-bindings-and-buttons-in-xaml"></a>Ajouter des commandes, les liaisons et les boutons en XAML  
  
1.  Tout d’abord, nous allons ajouter les commandes dans notre fichier MainWindow.xaml dans l’élément Windows.Resources :  
  
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
  
2.  CommandBinding est mappé à un événement RoutedUICommand à une méthode dans le code-behind. Ajoutez cet élément CommandBindings après la balise de fermeture de Windows.Resources :  
  
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
  
3.  Maintenant nous allons ajouter StackPanel avec le volet de navigation, ajouter, supprimer et mettre à jour des boutons. Tout d’abord, ajoutez ce style à Windows.Resources :  
  
    ```xaml  
    <Style x:Key="NavButton" TargetType="{x:Type Button}" BasedOn="{x:Null}">  
        <Setter Property="FontSize" Value="24"/>  
        <Setter Property="FontFamily" Value="Segoe UI Symbol"/>  
        <Setter Property="Margin" Value="2,2,2,0"/>  
        <Setter Property="Width" Value="40"/>  
        <Setter Property="Height" Value="auto"/>  
    </Style>  
    ```  
  
     En second lieu, collez ce code juste après les RowDefinitions pour l’élément de grille externe, vers le haut de la page XAML :  
  
    ```xaml  
    <StackPanel Orientation="Horizontal" Margin="2,2,2,0" Height="36" VerticalAlignment="Top" Background="Gainsboro" DataContext="{StaticResource customerViewSource}" d:LayoutOverrides="LeftMargin, RightMargin, TopMargin, BottomMargin">  
        <Button Name="btnFirst" Content="|◄" Command="{StaticResource FirstCommand}" Style="{StaticResource NavButton}"  />  
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
  
#### <a name="add-command-handlers-to-the-mainwindow-class"></a>Ajouter des gestionnaires de commandes à la classe MainWindow  
  
Le code-behind est minime, à l’exception des méthodes d’ajout et de suppression. Navigation est effectuée en appelant des méthodes sur la propriété de la vue de CollectionViewSource. Le DeleteOrderCommandHandler montre comment effectuer une suppression en cascade sur une commande. Nous devons d’abord supprimer le Order_Details qui lui sont associés. Le UpdateCommandHandler ajoute un nouveau client ou une commande à la collection, faute de quoi met simplement à jour d’un client existant ou une commande avec les modifications apporté par l’utilisateur dans les zones de texte.  
  
Ajouter ces méthodes de gestionnaire à la classe MainWindow dans MainWindow.xaml.cs. Si votre CollectionViewSource pour la table Customers a un nom différent, vous devez ajuster le nom de chacune de ces méthodes :  
  
[!code-csharp[CommandHandlers#3](../data-tools/codesnippet/CSharp/CreateWPFDataApp/MainWindow.xaml.cs#3)]  
  
## <a name="run-the-application"></a>Exécuter l'application
Pour démarrer le débogage, appuyez sur **F5**. Vous devez normalement voir remplie dans la grille de données et les boutons de navigation doivent fonctionner comme prévu. Cliquez sur « Commit » pour ajouter un nouveau client ou une commande pour le modèle après avoir entré les données. Cliquez sur « Annuler » pour hors d’un nouveau client ou d’un nouveau formulaire de commande sans enregistrer les données. Vous pouvez apporter des modifications aux clients existants et les commandes directement dans les zones de texte, et ces modifications sont écrites dans le modèle automatiquement.  
  
## <a name="see-also"></a>Voir aussi
[Outils de données Visual Studio pour .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)  
[Documentation d’Entity Framework](https://msdn.microsoft.com/en-us/data/ee712907.aspx)