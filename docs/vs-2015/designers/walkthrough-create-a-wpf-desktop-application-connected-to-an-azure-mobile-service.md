---
title: 'Procédure pas à pas : Créer une Application de bureau WPF connectée à un Service Mobile Azure | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 8d42620f-553b-4b04-a38b-f6b306d73a50
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 126aa1ad57aa5f8961803b8443365c208f5623ff
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63421251"
---
# <a name="walkthrough-create-a-wpf-desktop-application-connected-to-an-azure-mobile-service"></a>Procédure pas à pas : Créer une Application de bureau WPF connectée à un Service Mobile Azure
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez utiliser Windows Presentation Foundation (WPF) pour créer rapidement une application de bureau moderne qui utilise un service mobile Azure pour stocker et fournir des données.  
  
## <a name="Requirements"></a> Composants requis  
 Les éléments suivants sont nécessaires pour effectuer cette procédure pas à pas :  
  
- Visual Studio 2015 – toute version prenant en charge le développement WPF.  
  
- Un compte Microsoft Azure actif.  
  
    - Vous pouvez créer un compte d’évaluation gratuit [ici](http://azure.microsoft.com/pricing/free-trial/).  
  
    - Vous pouvez activer les [avantages pour les abonné MSDN](https://azure.microsoft.com/pricing/member-offers/msdn-benefits-details/?WT.mc_id=A261C142F). Votre abonnement MSDN vous donne des crédits chaque mois utilisables pour les services Azure payants.  
  
## <a name="create-a-project-and-add-references"></a>Créer un projet et ajouter des références  
 La première étape consiste à créer un projet WPF et ajouter un package NuGet permettant de se connecter à Azure Mobile Services.  
  
#### <a name="to-create-the-project"></a>Pour créer le projet  
  
1. Dans la barre de menus, sélectionnez **Fichier**, **Nouveau**, **Projet**.  
  
2. Dans la boîte de dialogue **Nouveau projet** , développez le nœud **Visual C#** ou **Visual Basic** et choisissez le nœud **Windows** , puis développez le nœud **Windows** et choisissez le nœud **Bureau classique** .  
  
3. Dans la liste de modèles, choisissez le modèle **Application WPF** .  
  
4. Dans la boîte de dialogue **Nom** , entrez `WPFQuickStart`, puis choisissez le bouton **OK** .  
  
     Le projet est créé et les fichiers projet sont ajoutés à l’ **Explorateur de solutions**. Le concepteur pour la fenêtre d’application par défaut nommée **MainWindow.xaml** s’affiche.  
  
#### <a name="to-add-a-reference-to-the-windows-azure-mobile-services-sdk"></a>Pour ajouter une référence au kit de développement logiciel (SDK) Microsoft Azure Mobile Services  
  
1. Dans l’ **Explorateur de solutions**, ouvrez le menu contextuel du nœud **Références** et choisissez **Gérer les packages NuGet**.  
  
2. Dans la boîte de dialogue **Gestionnaire de package NuGet**, choisissez le champ **Rechercher** et entrez `mobileservices`.  
  
3. Dans le volet gauche, choisissez **WindowsAzure.MobileServices**, puis, dans le volet droit, choisissez le bouton **Installer** .  
  
    > [!NOTE]
    > Si une boîte de dialogue **Aperçu** s’affiche, passez en revue les modifications proposées, puis choisissez le bouton **OK** .  
  
4. Dans la boîte de dialogue **Acceptation de la licence** , passez en revue les termes du contrat de licence, puis acceptez-les en choisissant le bouton **J’accepte** .  
  
     Les références nécessaires sont ajoutées à l’ **Explorateur de solutions**.  
  
    > [!NOTE]
    > Si vous n’acceptez pas les termes du contrat de licence, cliquez sur le bouton **Je refuse** . Dans ce cas, vous ne pouvez pas terminer le reste de la procédure pas à pas.  
  
## <a name="create-the-user-interface"></a>Créer l’interface utilisateur  
 L’étape suivante consiste à créer l’interface utilisateur de l’application. Tout d’abord, vous créez un contrôle utilisateur réutilisable qui affiche une disposition standard de deux volets côte à côte. Vous ajoutez le contrôle utilisateur dans la fenêtre d’application principale ainsi que des contrôles permettant d’entrer et d’afficher les données. Ensuite, vous écrivez du code pour définir l’interaction avec le serveur principal du service mobile.  
  
#### <a name="to-add-a-user-control"></a>Pour ajouter un contrôle utilisateur  
  
1. Dans l’ **Explorateur de solutions**, ouvrez le menu contextuel du nœud **WPFQuickStart** et choisissez **Ajouter**, **Nouveau projet**.  
  
2. Nommez le dossier `Common`.  
  
3. Ouvrez le menu contextuel du dossier **Common** et choisissez **Ajouter**, **Contrôle utilisateur**.  
  
4. Dans la boîte de dialogue **Ajouter un nouvel élément** , choisissez le champ Nom et entrez `QuickStartTask`, puis choisissez le bouton **Ajouter** .  
  
     Le contrôle utilisateur est ajouté au projet et le fichier **QuickStartTask.xaml** s’ouvre dans le concepteur.  
  
5. Dans le volet inférieur du concepteur, sélectionnez les balises `<Grid>` et `</Grid>` et remplacez-les par le code XAML suivant :  
  
    ```xaml  
    <Grid VerticalAlignment="Top">  
            <StackPanel Orientation="Horizontal">  
                <Border BorderThickness="0,0,1,0" BorderBrush="DarkGray" Margin="0,10" MinWidth="70">  
                    <TextBlock Text="{Binding Number}" FontSize="45" Foreground="DarkGray" Margin="20,0"/>  
                </Border>  
                <StackPanel>  
                    <TextBlock Text="{Binding Title}" Margin="10,10,0,0" FontSize="16" FontWeight="Bold" />  
                    <TextBlock Text="{Binding Description}" Margin="10,0,0,0" TextWrapping="Wrap" MaxWidth="500" />  
                </StackPanel>  
            </StackPanel>  
        </Grid>  
    ```  
  
     Ce code XAML crée une disposition réutilisable avec des espaces réservés pour les champs number, title et description. Au moment de l’exécution, les espaces réservés peuvent être remplacés par du texte, comme indiqué dans l’illustration suivante.  
  
     ![Contrôle utilisateur QuickStartTask](../designers/media/wpfquickstart1.PNG "WPFQuickStart1")  
  
6. Dans l’ **Explorateur de solutions**, développez le nœud **QuickStartTask.xaml** et ouvrez le fichier **QuickStartTask.xaml.cs** ou **QuickStartTask.xaml.vb** .  
  
7. Dans l’éditeur de code, remplacez l’espace de noms `namespace WPFQuickStart.Common` (C#) ou la méthode `Public Class QuickStartTask` (VB) par le code suivant :  
  
    ```csharp  
    namespace WPFQuickStart.Common  
    {  
        /// <summary>  
        /// Interaction logic for QuickStartTask.xaml  
        /// </summary>  
        public partial class QuickStartTask : UserControl  
        {  
            public QuickStartTask()  
            {  
                this.InitializeComponent();  
                this.DataContext = this;  
            }  
  
            public int Number  
            {  
                get { return (int)GetValue(NumberProperty); }  
                set { SetValue(NumberProperty, value); }  
            }  
  
            // Using a DependencyProperty as the backing store for Number.  This enables animation, styling, binding, etc...  
            public static readonly DependencyProperty NumberProperty =  
                DependencyProperty.Register("Number", typeof(int), typeof(QuickStartTask), new PropertyMetadata(0));  
  
            public string Title  
            {  
                get { return (string)GetValue(TitleProperty); }  
                set { SetValue(TitleProperty, value); }  
            }  
  
            // Using a DependencyProperty as the backing store for Title.  This enables animation, styling, binding, etc...  
            public static readonly DependencyProperty TitleProperty =  
                DependencyProperty.Register("Title", typeof(string), typeof(QuickStartTask), new PropertyMetadata(default(string)));  
  
            public string Description  
            {  
                get { return (string)GetValue(DescriptionProperty); }  
                set { SetValue(DescriptionProperty, value); }  
            }  
  
            // Using a DependencyProperty as the backing store for Description.  This enables animation, styling, binding, etc...  
            public static readonly DependencyProperty DescriptionProperty =  
                DependencyProperty.Register("Description", typeof(string), typeof(QuickStartTask), new PropertyMetadata(default(string)));  
        }  
    }  
    ```  
  
    ```vb  
    Partial Public Class QuickStartTask  
            Inherits UserControl  
  
            Public Sub New()  
                Me.InitializeComponent()  
                Me.DataContext = Me  
            End Sub  
  
            Public Property Number() As Integer  
                Get  
                    Return CInt(Fix(GetValue(NumberProperty)))  
                End Get  
                Set(ByVal value As Integer)  
                    SetValue(NumberProperty, value)  
                End Set  
            End Property  
  
            ' Using a DependencyProperty as the backing store for Number.  This enables animation, styling, binding, etc...  
            Public Shared ReadOnly NumberProperty As DependencyProperty = DependencyProperty.Register("Number", GetType(Integer), GetType(QuickStartTask), New PropertyMetadata(0))  
  
            Public Property Title() As String  
                Get  
                    Return CStr(GetValue(TitleProperty))  
                End Get  
                Set(ByVal value As String)  
                    SetValue(TitleProperty, value)  
                End Set  
            End Property  
  
            ' Using a DependencyProperty as the backing store for Title.  This enables animation, styling, binding, etc...  
            Public Shared ReadOnly TitleProperty As DependencyProperty = DependencyProperty.Register("Title", GetType(String), GetType(QuickStartTask), New PropertyMetadata(Nothing))  
  
            Public Property Description() As String  
                Get  
                    Return CStr(GetValue(DescriptionProperty))  
                End Get  
                Set(ByVal value As String)  
                    SetValue(DescriptionProperty, value)  
                End Set  
            End Property  
  
            ' Using a DependencyProperty as the backing store for Description.  This enables animation, styling, binding, etc...  
            Public Shared ReadOnly DescriptionProperty As DependencyProperty = DependencyProperty.Register("Description", GetType(String), GetType(QuickStartTask), New PropertyMetadata(Nothing))  
        End Class  
    ```  
  
     Ce code utilise les propriétés de dépendance pour définir les valeurs des champs number, title et description au moment de l’exécution.  
  
8. Dans la barre de menus, choisissez **Générer**, **Générer WPFQuickStart** pour générer le contrôle utilisateur.  
  
#### <a name="to-create-and-modify-the-main-window"></a>Pour créer et modifier la fenêtre principale  
  
1. Dans l’ **Explorateur de solutions**, ouvrez le fichier **MainWindow.xaml** .  
  
2. **Important**. Cette étape concerne uniquement C#. Si vous utilisez Visual Basic, passez à l’étape suivante. Dans le volet inférieur du concepteur, recherchez la ligne `xmlns:local=”clr-namespace:WPFQuickStart”` et remplacez-la par le code XAML suivant :  
  
    ```xaml  
    xmlns:local=”clr-namespace:WPFQuickStart.Common”  
    ```  
  
3. Dans la boîte de dialogue **Propriétés** , développez le nœud de catégorie **Common** et choisissez la propriété **Title** , puis entrez `WPF Todo List` et appuyez sur la touche **Entrée** .  
  
     Notez que l’élément **Title** de la fenêtre XAML est remplacé par la nouvelle valeur. Vous pouvez modifier des propriétés XAML dans la fenêtre XAML ou la fenêtre **Propriétés** , les modifications sont synchronisées.  
  
4. Dans la fenêtre XAML, définissez la valeur de l’élément **Height** sur `768`et la valeur de la propriété **Width** sur `1280`.  
  
     Ces éléments correspondent aux propriétés **Height** et **Width** de la catégorie **Disposition** de la fenêtre **Propriétés** .  
  
5. Sélectionnez les balises `<Grid>` et `</Grid>` , et remplacez-les par le code XAML suivant :  
  
    ```xaml  
    <Grid>  
  
            <Grid Margin="50,50,10,10">  
                <Grid.ColumnDefinitions>  
                    <ColumnDefinition Width="*" />  
                    <ColumnDefinition Width="*" />  
                </Grid.ColumnDefinitions>  
                <Grid.RowDefinitions>  
                    <RowDefinition Height="Auto" />  
                    <RowDefinition Height="*" />  
                </Grid.RowDefinitions>  
  
                <Grid Grid.Row="0" Grid.ColumnSpan="2" Margin="0,0,0,20">  
                    <StackPanel>  
                        <TextBlock Foreground="#0094ff" FontFamily="Segoe UI Light" Margin="0,0,0,6">MICROSOFT AZURE MOBILE SERVICES</TextBlock>  
                        <TextBlock Foreground="Gray" FontFamily="Segoe UI Light" FontSize="45" ><Run Text="My Todo List"/></TextBlock>  
                    </StackPanel>  
                </Grid>  
  
                <Grid Grid.Row="1">  
                    <StackPanel>  
  
                        <local:QuickStartTask Number="1" Title="Insert a TodoItem" Description="Enter some text below and click Save to insert a new todo item into the list." />  
  
                        <StackPanel Orientation="Horizontal" Margin="72,0,0,0">  
                            <TextBox x:Name="TodoInput" Margin="5" MinWidth="300"/>  
                            <Button x:Name="ButtonSave" Click="ButtonSave_Click" Content="Save"/>  
                        </StackPanel>  
  
                    </StackPanel>  
                </Grid>  
  
                <Grid Grid.Row="1" Grid.Column="1">  
                    <Grid.RowDefinitions>  
                        <RowDefinition Height="Auto" />  
                        <RowDefinition />  
                    </Grid.RowDefinitions>  
                    <StackPanel>  
                        <local:QuickStartTask Number="2" Title="Query and Update Data" Description="Click the Refresh button to load the unfinished TodoItems from the Azure Mobile Service. Select the checkbox to mark a ToDo item as complete and update the list." />  
                        <Button Margin="72,0,0,0" Name="ButtonRefresh" Click="ButtonRefresh_Click">Refresh</Button>  
                    </StackPanel>  
  
                    <ListView Name="ListItems" Margin="62,10,0,0" Grid.Row="1">  
                        <ListView.ItemTemplate>  
                            <DataTemplate>  
                                <StackPanel Orientation="Horizontal">  
                                    <CheckBox Name="CheckBoxComplete" IsChecked="{Binding Complete, Mode=TwoWay}" Checked="CheckBoxComplete_Checked" Content="{Binding Text}" Margin="10,5" VerticalAlignment="Center"/>  
                                </StackPanel>  
                            </DataTemplate>  
                        </ListView.ItemTemplate>  
                    </ListView>  
  
                </Grid>  
  
            </Grid>  
        </Grid>  
    ```  
  
     Notez que les modifications sont répercutées dans la fenêtre de conception. Une fois encore, vous pouvez également définir l’interface utilisateur en ajoutant des contrôles à partir de la fenêtre **Boîte à outils** et en définissant des propriétés dans la fenêtre **Propriétés** . Tout ce qui peut être effectué dans le concepteur peut l’être aussi en code XAML, et réciproquement.  
  
     À ce stade, la conception doit ressembler à l’illustration suivante :  
  
     ![MainWindow dans le concepteur](../designers/media/wpfquickstart2.PNG "WPFQuickStart2")  
  
    > [!NOTE]
    > Pendant l’application des procédures suivantes, vous pouvez observer des erreurs dans la **Liste d’erreurs** , si elle est ouverte. Ne vous inquiétez pas, ces erreurs disparaissent à la fin des procédures restantes.  
  
6. Dans l’ **Explorateur de solutions**, développez le nœud **MainWindow.xaml** et ouvrez le fichier **MainWindow.xaml.cs** ou **MainWindow.xaml.vb** .  
  
7. Dans l’éditeur de code, ajoutez les directives `using` ou `Imports` suivantes en haut du fichier :  
  
    ```csharp  
    using Microsoft.WindowsAzure.MobileServices;  
    using Newtonsoft.Json;   
    ```  
  
    ```vb  
    Imports Microsoft.WindowsAzure.MobileServices  
    Imports Newtonsoft.Json  
    ```  
  
8. Remplacez tout le code de l’espace de noms **WPFQuickStart** (C#) ou de la classe **MainWindow** (VB) par le code suivant :  
  
    ```csharp  
    namespace WPFQuickStart  
    {  
        /// <summary>  
        /// Interaction logic for MainWindow.xaml  
        /// </summary>  
        public class TodoItem  
        {  
            public string Id { get; set; }  
  
            [JsonProperty(PropertyName = "text")]  
            public string Text { get; set; }  
  
            [JsonProperty(PropertyName = "complete")]  
            public bool Complete { get; set; }  
        }  
  
        public partial class MainWindow : Window  
        {  
            private MobileServiceCollection<TodoItem, TodoItem> items;  
            private IMobileServiceTable<TodoItem> todoTable = App.MobileService.GetTable<TodoItem>();  
  
            public MainWindow()  
            {  
                InitializeComponent();  
            }  
  
            private async void InsertTodoItem(TodoItem todoItem)  
            {  
                // This code inserts a new TodoItem into the database. When the operation completes  
                // and Mobile Services has assigned an Id, the item is added to the CollectionView  
                await todoTable.InsertAsync(todoItem);  
                items.Add(todoItem);  
            }  
  
            private async void RefreshTodoItems()  
            {  
                try  
                {  
                    // This code refreshes the entries in the list view by querying the TodoItem table.  
                    // The query excludes completed TodoItems  
                    items = await todoTable  
                        .Where(todoItem => todoItem.Complete == false)  
                        .ToCollectionAsync();  
                    ListItems.ItemsSource = items;  
                }  
                catch (MobileServiceInvalidOperationException e)  
                {  
                    MessageBox.Show(e.Message, "Error loading items");  
                }  
            }  
  
            private async void UpdateCheckedTodoItem(TodoItem item)  
            {  
                // This code takes a freshly completed TodoItem and updates the database. When the MobileService   
                // responds, the item is removed from the list   
                await todoTable.UpdateAsync(item);  
                items.Remove(item);  
            }  
  
            private void ButtonRefresh_Click(object sender, RoutedEventArgs e)  
            {  
                RefreshTodoItems();  
            }  
  
            private void ButtonSave_Click(object sender, RoutedEventArgs e)  
            {  
                var todoItem = new TodoItem { Text = TodoInput.Text };  
                InsertTodoItem(todoItem);  
                TodoInput.Text = "";  
            }  
  
            private void CheckBoxComplete_Checked(object sender, RoutedEventArgs e)  
            {  
                CheckBox cb = (CheckBox)sender;  
                TodoItem item = cb.DataContext as TodoItem;  
                UpdateCheckedTodoItem(item);  
            }  
  
            protected override void OnActivated(EventArgs e)  
            {  
                RefreshTodoItems();  
            }  
        }  
  
    }  
    ```  
  
    ```vb  
    Public Class TodoItem  
        Public Property Id() As String  
  
        <JsonProperty(PropertyName:="text")>  
        Public Property Text() As String  
  
        <JsonProperty(PropertyName:="complete")>  
        Public Property Complete() As Boolean  
    End Class  
  
    Partial Public Class MainWindow  
        Inherits Window  
  
        Private items As MobileServiceCollection(Of TodoItem, TodoItem)  
        Private todoTable As IMobileServiceTable(Of TodoItem) = Application.MobileService.GetTable(Of TodoItem)()  
  
        Public Sub New()  
            InitializeComponent()  
        End Sub  
  
        Private Async Sub InsertTodoItem(ByVal todoItem As TodoItem)  
            ' This code inserts a new TodoItem into the database. When the operation completes  
            ' and Mobile Services has assigned an Id, the item is added to the CollectionView  
            Await todoTable.InsertAsync(todoItem)  
            items.Add(todoItem)  
        End Sub  
  
        Private Async Sub RefreshTodoItems()  
            Dim exception As MobileServiceInvalidOperationException = Nothing  
            Try  
                ' This code refreshes the entries in the list view by querying the TodoItem table.  
                ' The query excludes completed TodoItems  
                items = Await todoTable.Where(Function(todoItem) todoItem.Complete = False).ToCollectionAsync()  
            Catch e As MobileServiceInvalidOperationException  
                exception = e  
            End Try  
  
            If exception IsNot Nothing Then  
                MessageBox.Show(exception.Message, "Error loading items")  
            Else  
                ListItems.ItemsSource = items  
            End If  
        End Sub  
  
        Private Async Sub UpdateCheckedTodoItem(ByVal item As TodoItem)  
            ' This code takes a freshly completed TodoItem and updates the database. When the MobileService   
            ' responds, the item is removed from the list   
            Await todoTable.UpdateAsync(item)  
            items.Remove(item)  
        End Sub  
  
        Private Sub ButtonRefresh_Click(ByVal sender As Object, ByVal e As RoutedEventArgs)  
            RefreshTodoItems()  
        End Sub  
  
        Private Sub ButtonSave_Click(ByVal sender As Object, ByVal e As RoutedEventArgs)  
            Dim todoItem = New TodoItem With {.Text = TodoInput.Text}  
            InsertTodoItem(todoItem)  
            TodoInput.Text = ""  
        End Sub  
  
        Private Sub CheckBoxComplete_Checked(ByVal sender As Object, ByVal e As RoutedEventArgs)  
            Dim cb As CheckBox = DirectCast(sender, CheckBox)  
            Dim item As TodoItem = TryCast(cb.DataContext, TodoItem)  
            UpdateCheckedTodoItem(item)  
        End Sub  
  
        Protected Overrides Sub OnActivated(ByVal e As EventArgs)  
            RefreshTodoItems()  
        End Sub  
    End Class  
    ```  
  
     Ce code définit l’interaction entre l’interface utilisateur et la base de données dans le service mobile à l’aide de méthodes asynchrones.  
  
## <a name="create-the-azure-mobile-service"></a>Créer le service mobile Azure  
 L’étape finale consiste à créer un service mobile dans Microsoft Azure, ajouter une table pour stocker vos données et faire référence à l’instance de service dans votre application.  
  
#### <a name="to-create-a-mobile-service"></a>Pour créer un service mobile  
  
1. Ouvrez un navigateur web et connectez-vous à votre portail Microsoft Azure, puis choisissez l’onglet **Mobile Services** .  
  
2. Choisissez le bouton **Nouveau**, puis, dans la boîte de dialogue contextuelle, choisissez **Calculer**, **Service mobile, Créer**.  
  
3. Dans la boîte de dialogue **Nouveau service mobile** , choisissez la zone de texte **URL** et entrez `wpfquickstart01`.  
  
    > [!NOTE]
    > Vous devez peut-être modifier la partie numérique de l’URL. Microsoft Azure nécessite une URL unique pour chaque service mobile.  
  
     Cela définit l’URL du service `https://wpfquickstart01.azure-mobile.net/`.  
  
4. Dans la liste **Base de données** , choisissez une option de base de données. Comme il s’agit d’une application qui ne sera probablement pas beaucoup utilisée, choisissez l’option **Créer une base de données SQL gratuite de 20 Mo** , ou choisissez la base de données gratuite déjà associée à votre abonnement.  
  
5. Dans la liste **Région** , choisissez le centre de données dans lequel déployer le service mobile, puis choisissez le bouton **Suivant** (flèche droite).  
  
    > [!NOTE]
    > Pour ce service, vous utilisez le paramètre par défaut **Principal** , **JavaScript**.  
  
6. Si vous créez une base de données, dans la page **Spécifier les paramètres de base de données** , dans la liste **Serveur** , choisissez **Nouveau serveur de base de données SQL**, entrez votre **Nom de connexion SQL** et votre **Mot de passe**, puis choisissez le bouton **Terminé** (coche).  
  
7. Si vous avez choisi une base de données existante, dans la page **Paramètres de base de données** , entrez votre **Mot de passe de connexion** , puis choisissez le bouton **Terminé** (coche).  
  
     Le processus de création du service mobile démarre. Une fois le processus terminé, l’état passe à **Prêt** , et vous pouvez passer à l’étape suivante.  
  
8. Dans le portail, sélectionnez le service mobile nouvellement créé, puis choisissez le bouton **Gérer les clés** .  
  
9. Dans la boîte de dialogue **Gérer les clés d’accès** , copiez la **Clé d’application**.  
  
     Vous allez l’utiliser dans la procédure suivante.  
  
#### <a name="to-create-a-table"></a>Pour créer une table  
  
1. Dans le portail Microsoft Azure, choisissez la flèche vers la droite à côté du nom de votre service mobile, et dans la barre de menus, choisissez **Données**, puis le lien **Ajouter une table** .  
  
2. Dans la boîte de dialogue **Créer une table** , dans la zone de texte **Nom de la table** , entrez `TodoItem`, puis choisissez le bouton **Terminé** (coche).  
  
     Attendez que la table soit créée et passez à la dernière procédure.  
  
#### <a name="to-add-a-declaration-for-the-mobile-service"></a>Pour ajouter une déclaration pour le service mobile  
  
1. Retournez dans Visual Studio. Dans l’ **Explorateur de solutions**, développez le nœud **App.xaml** (C#) ou **Application.xaml** (Visual Basic) et ouvrez le fichier **App.xaml.cs** ou **App.xaml.vb** .  
  
2. Dans l’éditeur de code, ajoutez les directives `using` ou **Imports** suivantes en haut du fichier :  
  
    ```csharp  
    using Microsoft.WindowsAzure.MobileServices;  
    ```  
  
    ```vb  
    Imports Microsoft.WindowsAzure.MobileServices  
    ```  
  
3. Ajoutez la déclaration suivante à la classe, en remplaçant *YOUR-SERVICE_HERE* par le nom de l’URL de votre service et *YOUR-KEY_HERE* par la clé d’application que vous avez copiée dans la procédure précédente :  
  
    ```csharp  
    public static MobileServiceClient MobileService = new MobileServiceClient(  
                 "https://YOUR-SERVICE-HERE.azure-mobile.net/",  
                 "YOUR-KEY-HERE"  
             );  
    ```  
  
    ```vb  
    Public Shared MobileService As New MobileServiceClient("https://YOUR-SERVICE-HERE.azure-mobile.net/", "YOUR-KEY-HERE")  
    ```  
  
     Ce code permet à l’application d’accéder au service mobile en cours d’exécution sur Microsoft Azure.  
  
## <a name="test-the-application"></a>Tester l’application  
 Voilà, vous avez créé une application de bureau WPF qui accède à un service mobile Azure. Maintenant, vous devez exécuter l’application pour la voir en fonctionnement.  
  
#### <a name="to-run-the-application"></a>Pour exécuter l’application  
  
1. Dans la barre de menus, choisissez **Déboguer**, **Démarrer le débogage** (ou appuyez sur F5).  
  
2. Dans la boîte de dialogue **Insert a TodoItem** , entrez `Do something`, puis choisissez le bouton **Enregistrer** .  
  
3. Entrée `Do something else`, puis choisissez le bouton **Enregistrer** .  
  
     Notez que les deux entrées sont ajoutées à la liste **Query and Update Data** , comme indiqué dans l’illustration suivante.  
  
     ![Les éléments TODO sont ajoutés à la liste.](../designers/media/wpfquickstart3.PNG "WPFQuickStart3")  
  
4. Cochez la case de l’entrée **Do something else** dans la liste.  
  
     Cette action appelle la méthode **UpdateCheckedTodoItem** et supprime l’élément de la liste et de la base de données.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Vous avez terminé un exemple assez simple d’une application de bureau WPF avec un serveur principal Azure. Bien entendu, une application réelle est susceptible d’être beaucoup plus complexe, mais les mêmes concepts de base s’appliquent. Consultez [WPF dans le .NET Framework](https://msdn.microsoft.com/library/ms754130\(v=vs.100\).aspx).  
  
 Vous pouvez rendre l’interface utilisateur plus attrayante en ajoutant des couleurs, des formes, des graphiques et même des animations. Consultez l’article [Conception XAML dans Visual Studio et Blend pour Visual Studio](../designers/designing-xaml-in-visual-studio.md).  
  
 Vous pouvez vous connecter aux bases de données SQL ou à d’autres sources de données à l’aide d’Azure Mobile Services. Consultez la [Documentation sur Mobile Services](http://azure.microsoft.com/services/app-service/mobile/).  
  
## <a name="see-also"></a>Voir aussi  
 [Procédure pas à pas : Ma première Application de bureau WPF](../designers/walkthrough-my-first-wpf-desktop-application2.md)   
 [Créer des applications de bureau modernes à l’aide de Windows Presentation Foundation](../designers/create-modern-desktop-applications-with-windows-presentation-foundation.md)
