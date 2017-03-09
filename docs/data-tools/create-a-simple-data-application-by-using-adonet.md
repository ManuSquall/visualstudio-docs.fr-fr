---
title: "Proc&#233;dure pas &#224; pas&#160;: cr&#233;ation d&#39;une application de donn&#233;es simple &#224; l&#39;aide d&#39;ADO.NET | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
ms.assetid: 2222841f-e443-4a3d-8c70-4506aa905193
caps.latest.revision: 42
caps.handback.revision: 30
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Proc&#233;dure pas &#224; pas&#160;: cr&#233;ation d&#39;une application de donn&#233;es simple &#224; l&#39;aide d&#39;ADO.NET
Quand vous créez une application qui manipule les données d'une base de données, vous effectuez des tâches élémentaires, comme définir les chaînes de connexion, insérer les données et exécuter les procédures stockées.  En suivant cette rubrique, vous pouvez découvrir comment interagir avec une base de données dans une application Windows Forms simple à l'aide de Visual C\# ou Visual Basic et ADO.NET.  
  
> [!IMPORTANT]
>  Pour que le code reste simple, il n'inclut pas la gestion des exceptions prête à la production.  
  
 **Dans cette rubrique**  
  
-   [Installer l'exemple de base de données](../data-tools/create-a-simple-data-application-by-using-adonet.md#BKMK_setupthesampledatabase)  
  
-   [Créer les formulaires et ajouter les contrôles](../data-tools/create-a-simple-data-application-by-using-adonet.md#BKMK_createtheformsandaddcontrols)  
  
-   [Stocker la chaîne de connexion](../data-tools/create-a-simple-data-application-by-using-adonet.md#BKMK_storetheconnectionstring)  
  
-   [Récupérer la chaîne de connexion](../data-tools/create-a-simple-data-application-by-using-adonet.md#BKMK_retrievetheconnectionstring)  
  
-   [Écrire le code des formulaires](../data-tools/create-a-simple-data-application-by-using-adonet.md#BKMK_writethecodefortheforms)  
  
-   [Tester votre application](../data-tools/create-a-simple-data-application-by-using-adonet.md#BKMK_testyourapplication)  
  
## Composants requis  
 Pour créer l'application, vous aurez besoin des éléments suivants :  
  
-   Visual Studio 2012 avec Update 1 ou [!INCLUDE[vs_dev12](../data-tools/includes/vs_dev12_md.md)]  
  
-   SQL Server 2012 Express LocalDB  
  
-   Petit exemple de base de données que vous créez en suivant les étapes décrites dans [Procédure pas à pas : création d'un petit exemple de base de données](../data-tools/create-a-sql-database-by-using-a-script.md).  
  
-   Chaîne de connexion de la base de données, une fois que vous l'avez configurée.  Pour rechercher cette valeur, ouvrez **Explorateur d'objets SQL Server**, puis le menu contextuel de la base de données, sélectionnez **Propriétés**, puis faites défiler jusqu'à la propriété **Chaîne de connexion**.  
  
 Cette rubrique suppose que vous êtes familiarisé avec les fonctionnalités de base de l'IDE de Visual Studio et que vous pouvez créer une application Windows Forms, ajouter des formulaires à ce projet, placer des boutons et autres contrôles sur les formulaires, définir les propriétés de ces contrôles et coder des événements simples.  Si vous n'êtes pas à l'aise avec ces tâches, nous vous suggérons d'effectuer les [Mises en route de Visual Basic et Visual C\#](../ide/getting-started-with-visual-csharp-and-visual-basic.md) avant de démarrer cette rubrique.  
  
##  <a name="BKMK_setupthesampledatabase"></a> Installer l'exemple de base de données  
 L'exemple de base de données pour cette procédure pas à pas inclut les tables Customer et Orders.  Initialement, les tables ne contiennent pas de données, mais vous les ajouterez quand vous exécuterez l'application que vous allez créer.  La base de données dispose également de cinq procédures stockées simples.  La [Procédure pas à pas : création d'un petit exemple de base de données](../data-tools/create-a-sql-database-by-using-a-script.md) contient un script Transact\-SQL qui crée les tables, les clés primaires et les clés étrangères, les contraintes et les procédures stockées.  
  
##  <a name="BKMK_createtheformsandaddcontrols"></a> Créer les formulaires et ajouter les contrôles  
  
1.  Créez un projet pour une application Windows Forms, puis nommez\-le `SimpleDataApp`.  
  
     Visual Studio crée le projet et plusieurs fichiers, y compris un formulaire Windows vide nommé Form1.  
  
2.  Ajoutez deux formulaires Windows à votre projet afin qu'il comporte trois formulaires, puis attribuez\-leur les noms suivants.  
  
    -   Navigation  
  
    -   NewCustomer  
  
    -   FillOrCancel  
  
3.  Pour chaque formulaire, ajoutez les zones de texte, les boutons et les autres contrôles indiqués dans les illustrations suivantes.  Pour chaque contrôle, définissez les propriétés que les tables décrivent.  
  
    > [!NOTE]
    >  La zone de groupe et les contrôles d'étiquette ajoutent de la clarté mais ne sont pas utilisés dans le code.  
  
 **Formulaire Navigation**  
  
 ![Boîte de dialogue Navigation](../data-tools/media/simpleappnav.png "SimpleAppNav")  
  
|Contrôles du formulaire Navigation|Propriétés|  
|----------------------------------------|----------------|  
|Bouton|Name \= btnGoToAdd|  
|Bouton|Name \= btnGoToFillOrCancel|  
|Bouton|Name \= btnExit|  
  
 **Formulaire NewCustomer**  
  
 ![Ajouter un nouveau client et passer une commande](../data-tools/media/simpleappnewcust.png "SimpleAppNewCust")  
  
|Contrôles du formulaire NewCustomer|Propriétés|  
|-----------------------------------------|----------------|  
|TextBox|Name \= txtCustomerName|  
|TextBox|Name \= txtCustomerID<br /><br /> Readonly \= True|  
|Bouton|Name \= btnCreateAccount|  
|NumericUpdown|DecimalPlaces \= 0<br /><br /> Maximum \= 5000<br /><br /> Name \= numOrderAmount|  
|DateTimePicker|Format \= Short<br /><br /> Name \= dtpOrderDate|  
|Bouton|Name \= btnPlaceOrder|  
|Bouton|Name \= btnAddAnotherAccount|  
|Bouton|Name \= btnAddFinish|  
  
 **Formulaire FillOrCancel**  
  
 ![remplir ou annuler les commandes](../data-tools/media/simpleappcancelfill.png "SimpleAppCancelFill")  
  
|Contrôles du formulaire FillOrCancel|Propriétés|  
|------------------------------------------|----------------|  
|TextBox|Name \= txtOrderID|  
|Bouton|Name \= btnFindByOrderID|  
|DateTimePicker|Format \= Short<br /><br /> Name \= dtpFillDate|  
|DataGridView|Name \= dgvCustomerOrders<br /><br /> Readonly \= True<br /><br /> RowHeadersVisible \= False|  
|Bouton|Name \= btnCancelOrder|  
|Bouton|Name \= btnFillOrder|  
|Bouton|Name \= btnFinishUpdates|  
  
##  <a name="BKMK_storetheconnectionstring"></a> Stocker la chaîne de connexion  
 Quand votre application tente d'ouvrir une connexion à la base de données, elle doit avoir accès à la chaîne de connexion.  Pour éviter d'entrer la chaîne manuellement sur chaque formulaire, stockez la chaîne dans le fichier de configuration d'application de votre projet, puis créez une méthode qui retourne la chaîne quand elle est appelée depuis un formulaire de votre application.  
  
1.  Ouvrez le menu contextuel du projet, puis choisissez **Propriétés**.  
  
2.  Dans le panneau gauche de la fenêtre **Propriétés**, choisissez l'onglet **Paramètres**.  
  
3.  Dans la colonne **Nom**, entrez `connString`.  
  
4.  Dans la liste **Type**, choisissez **\(Chaîne de connexion\)**.  
  
5.  Dans la liste **Portée**, choisissez **Application**.  
  
6.  Dans la colonne **Valeur**, entrez votre chaîne de connexion, puis enregistrez vos modifications.  
  
##  <a name="BKMK_retrievetheconnectionstring"></a> Récupérer la chaîne de connexion  
  
1.  Dans la barre de menus, choisissez **Projet**, **Ajouter une référence**, puis ajoutez une référence à System.Configuration.dll.  
  
2.  Dans la barre de menus, choisissez **Projet**, **Ajouter une classe** pour ajouter un fichier de classe à votre projet, puis nommez le fichier `Utility`.  
  
     Visual Studio crée le fichier et l'affiche dans l'**Explorateur de solutions**.  
  
3.  Dans le fichier Utility, remplacez le code d'espace réservé par le code suivant.  Notez les commentaires numérotés \(précédés de Util\-\) qui identifient les sections du code.  Le tableau qui suit le code souligne des points clés.  
  
    ```c#  
    using System;  
    using System.Collections.Generic;  
    using System.Linq;  
    using System.Text;  
    using System.Threading.Tasks;  
    //Util-1 More namespaces.  
    using System.Configuration;   
  
    namespace SimpleDataApp  
    {  
        internal class Utility  
        {  
  
            //Get the connection string from App config file.  
            internal static string GetConnectionString()  
            {  
                //Util-2 Assume failure.  
                string returnValue = null;  
  
                //Util-3 Look for the name in the connectionStrings section.  
                ConnectionStringSettings settings =  
                ConfigurationManager.ConnectionStrings["SimpleDataApp.Properties.Settings.connString"];  
  
                //If found, return the connection string.  
                if (settings != null)  
                    returnValue = settings.ConnectionString;  
  
                return returnValue;  
            }  
        }  
    }  
    ```  
  
    ```vb  
    Imports System  
    Imports System.Collections.Generic  
    Imports System.Linq  
    Imports System.Text  
    Imports System.Threading.Tasks  
    ' Util-1 More namespaces.  
    Imports System.Configuration  
  
    Namespace SimpleDataApp  
        Friend Class Utility  
  
            ' Get connection string from App config file.  
            Friend Shared Function GetConnectionString() As String  
  
                ' Util-2 Assume failure.  
                Dim returnValue As String = Nothing  
  
                ' Util-3 Look for the name in the connectionStrings section.  
                Dim settings As ConnectionStringSettings = ConfigurationManager.ConnectionStrings("SimpleDataApp.My.MySettings.connString")  
  
                ' If found, return the connection string.  
                If settings IsNot Nothing Then  
                    returnValue = settings.ConnectionString  
                End If  
  
                Return returnValue  
            End Function  
        End Class  
    End Namespace  
    ```  
  
    |Commentaire|Description|  
    |-----------------|-----------------|  
    |Util\-1|Ajoutez l'espace de noms System.Configuration.|  
    |Util\-2|Définissez une variable `returnValue` et initialisez\-la sur `null` \(C\#\) ou `Nothing` \(Visual Basic\).|  
    |Util\-3|Même si vous avez entré `connString` comme nom de chaîne de connexion dans la fenêtre **Propriétés**, vous devez spécifier `"SimpleDataApp.Properties.Settings.connString"` \(C\#\) ou `"SimpleDataApp.My.MySettings.connString"` \(Visual Basic\) dans le code.|  
  
##  <a name="BKMK_writethecodefortheforms"></a> Écrire le code des formulaires  
 Cette section contient des vues d'ensemble de ce que fait chaque formulaire et indique le code qui crée les formulaires.  Les commentaires numérotés identifient des sections du code.  
  
### Formulaire Navigation  
 Le formulaire Navigation s'ouvre quand vous exécutez l'application.  Le bouton **Add an account** ouvre le formulaire NewCustomer.  Le bouton **Fill or cancel orders** ouvre le formulaire FillOrCancel.  Le bouton **Exit** ferme l'application.  
  
#### Faire du formulaire Navigation le formulaire de démarrage  
 Si vous utilisez C\#, dans l'**Explorateur de solutions**, ouvrez Program.cs, puis modifiez la ligne `Application.Run` comme suit : `Application.Run(new Navigation());`  
  
 Si vous utilisez Visual Basic, dans l'**Explorateur de solutions**, ouvrez la fenêtre **Propriétés**, choisissez l'onglet **Application**, puis SimpleDataApp.Navigation dans la liste **Formulaire de démarrage**.  
  
#### Créer des gestionnaires d'événements  
 Créez des gestionnaires d'événements Click vides pour les trois boutons du formulaire.  Consultez [Comment : créer des gestionnaires d'événements par défaut dans le Concepteur Windows Forms](http://msdn.microsoft.com/fr-fr/757bcc16-1dc2-4d68-b115-ac0f53f05c8d).  
  
#### Créer du code pour le formulaire Navigation  
 Dans le formulaire Navigation, remplacez le code existant par le code suivant.  
  
```c#  
using System;  
using System.Collections.Generic;  
using System.ComponentModel;  
using System.Data;  
using System.Drawing;  
using System.Linq;  
using System.Text;  
using System.Threading.Tasks;  
using System.Windows.Forms;  
  
namespace SimpleDataApp  
{  
    public partial class Navigation : Form  
    {  
        public Navigation()  
        {  
            InitializeComponent();  
        }  
  
        //Open the NewCustomer form as a dialog box, which will return focus to the calling form when it closes.  
        private void btnGoToAdd_Click(object sender, EventArgs e)  
        {  
            Form frm = new NewCustomer();  
            frm.Show();  
        }  
  
        //Open the FillorCancel form as a dialog box.  
        private void btnGoToFillOrCancel_Click(object sender, EventArgs e)  
        {  
            Form frm = new FillOrCancel();  
            frm.ShowDialog();  
        }  
  
        //Close the application, not just the Navigation form.  
        private void btnExit_Click(object sender, EventArgs e)  
        {  
            this.Close();  
        }  
    }  
}  
```  
  
```vb  
Imports System  
Imports System.Collections.Generic  
Imports System.ComponentModel  
Imports System.Data  
Imports System.Drawing  
Imports System.Linq  
Imports System.Text  
Imports System.Threading.Tasks  
Imports System.Windows.Forms  
  
Namespace SimpleDataApp  
    Partial Public Class Navigation  
        Inherits Form  
        Public Sub New()  
            InitializeComponent()  
        End Sub  
  
        ' Open the NewCustomer form as a dialog box, which will return focus to the calling form when it closes.  
        Private Sub btnGoToAdd_Click() Handles btnGoToAdd.Click  
            Dim frm As Form = New NewCustomer()  
            frm.Show()  
        End Sub  
  
        ' Open the FillorCancel form as a dialog box.  
        Private Sub btnGoToFillOrCancel_Click() Handles btnGoToFillOrCancel.Click  
            Dim frm As Form = New FillOrCancel()  
            frm.ShowDialog()  
        End Sub  
  
        ' Close the application, not just the Navigation form.  
        Private Sub btnExit_Click() Handles btnExit.Click  
            Me.Close()  
        End Sub  
    End Class  
End Namespace  
  
```  
  
### Formulaire NewCustomer  
 Quand vous écrivez un nom de client, puis que vous choisissez le bouton **Create Account**, le formulaire NewCustomer crée un compte client, et SQL Server retourne une valeur IDENTITY comme nouveau numéro de compte.  Vous passez ensuite une commande pour le nouveau compte en spécifiant une quantité et une date de commande, et en choisissant le bouton **Place Order**.  
  
#### Créer des gestionnaires d'événements  
 Créez un gestionnaire d'événements Click vide pour chaque bouton du formulaire.  
  
#### Créer du code pour le formulaire NewCustomer  
 Ajoutez le code suivant au formulaire NewCustomer.  Parcourez chaque bloc de code en utilisant les commentaires numérotés et le tableau situé après le code.  
  
```c#  
using System;  
using System.Collections.Generic;  
using System.ComponentModel;  
using System.Data;  
using System.Drawing;  
using System.Linq;  
using System.Text;  
using System.Threading.Tasks;  
using System.Windows.Forms;  
//NC-1 More namespaces.  
using System.Data.SqlClient;  
using System.Configuration;  
  
namespace SimpleDataApp  
{  
    public partial class NewCustomer : Form  
    {  
        //NC-2 Storage for IDENTITY values returned from database.  
        private int parsedCustomerID;  
        private int orderID;  
  
        //NC-3 Specify a connection string.  
        string connstr = SimpleDataApp.Utility.GetConnectionString();  
  
        public NewCustomer()  
        {  
            InitializeComponent();  
        }  
  
        //NC-4 Create account.  
        private void btnCreateAccount_Click(object sender, EventArgs e)  
        {  
            //NC-5 Set up and run stored procedure only if Customer Name is present.  
            if (isCustomerName())  
            {  
  
                //NC-6 Create the connection.  
                SqlConnection conn = new SqlConnection(connstr);  
  
                //NC-7 Create a SqlCommand, and identify it as a stored procedure.  
                SqlCommand cmdNewCustomer = new SqlCommand("Sales.uspNewCustomer", conn);  
                cmdNewCustomer.CommandType = CommandType.StoredProcedure;  
  
                //NC-8 Add input parameter from the stored procedure and specify what to use as its value.  
                cmdNewCustomer.Parameters.Add(new SqlParameter("@CustomerName", SqlDbType.NVarChar, 40));  
                cmdNewCustomer.Parameters["@CustomerName"].Value = txtCustomerName.Text;  
  
                //NC-9 Add output parameter.  
                cmdNewCustomer.Parameters.Add(new SqlParameter("@CustomerID", SqlDbType.Int));  
                cmdNewCustomer.Parameters["@CustomerID"].Direction = ParameterDirection.Output;  
  
                //NC-10 try-catch-finally  
                try  
                {  
                    //NC-11 Open the connection.  
                    conn.Open();  
  
                    //NC-12 Run the stored procedure.  
                    cmdNewCustomer.ExecuteNonQuery();  
  
                    //NC-13 Customer ID is an IDENTITY value from the database.   
                    this.parsedCustomerID = (int)cmdNewCustomer.Parameters["@CustomerID"].Value;  
                    this.txtCustomerID.Text = Convert.ToString(parsedCustomerID);  
  
                }  
                catch  
                {  
                    //NC-14 A simple catch.  
  
                    MessageBox.Show("Customer ID was not returned. Account could not be created.");  
                }  
                finally  
                {  
                    //NC-15 Close the connection.  
                    conn.Close();  
                }  
            }  
        }  
  
        //NC-16 Verify that Customer Name is present.  
        private bool isCustomerName()  
        {  
            if (txtCustomerName.Text == "")  
            {  
                MessageBox.Show("Please enter a name.");  
                return false;  
            }  
            else  
            {  
                return true;  
            }  
        }  
  
        //NC-17 Place order.  
        private void btnPlaceOrder_Click(object sender, EventArgs e)  
        {  
            //NC-18 Set up and run stored procedure only if required input is present.  
            if (isPlaceOrderReady())  
            {  
                // Create the connection.  
                SqlConnection conn = new SqlConnection(connstr);  
  
                //NC-19 Create SqlCommand and identify it as a stored procedure.  
                SqlCommand cmdNewOrder = new SqlCommand("Sales.uspPlaceNewOrder", conn);  
                cmdNewOrder.CommandType = CommandType.StoredProcedure;  
  
                //NC-20 @CustomerID, which was an output parameter from uspNewCustomer.  
                cmdNewOrder.Parameters.Add(new SqlParameter("@CustomerID", SqlDbType.Int));  
                cmdNewOrder.Parameters["@CustomerID"].Value = this.parsedCustomerID;  
  
                //NC-21 @OrderDate.  
                cmdNewOrder.Parameters.Add(new SqlParameter("@OrderDate", SqlDbType.DateTime, 8));  
                cmdNewOrder.Parameters["@OrderDate"].Value = dtpOrderDate.Value;  
  
                //NC-22 @Amount.  
                cmdNewOrder.Parameters.Add(new SqlParameter("@Amount", SqlDbType.Int));  
                cmdNewOrder.Parameters["@Amount"].Value = numOrderAmount.Value;  
  
                //NC-23 @Status. For a new order, the status is always O (open)  
                cmdNewOrder.Parameters.Add(new SqlParameter("@Status", SqlDbType.Char, 1));  
                cmdNewOrder.Parameters["@Status"].Value = "O";  
  
                //NC-24 Add return value for stored procedure, which is the orderID.  
                cmdNewOrder.Parameters.Add(new SqlParameter("@RC", SqlDbType.Int));  
                cmdNewOrder.Parameters["@RC"].Direction = ParameterDirection.ReturnValue;  
  
                //try – catch - finally  
                try  
                {  
                    //Open connection.  
                    conn.Open();  
  
                    //Run the stored procedure.  
                    cmdNewOrder.ExecuteNonQuery();  
  
                    //NC-25 Display the order number.  
                    this.orderID = (int)cmdNewOrder.Parameters["@RC"].Value;  
                    MessageBox.Show("Order number " + this.orderID + " has been submitted.");  
                }  
                catch  
                {  
                    //A simple catch.  
                    MessageBox.Show("Order could not be placed.");  
                }  
                finally  
                {  
                    //Close connection.  
                    conn.Close();  
                }  
            }  
        }  
  
        //NC-26 Verify that order data is ready.  
        private bool isPlaceOrderReady()  
        {  
            // Verify that CustomerID is present.  
            if (txtCustomerID.Text == "")  
            {  
                MessageBox.Show("Please create customer account before placing order.");  
                return false;  
            }  
  
            // Verify that Amount isn't 0.   
            else if ((numOrderAmount.Value < 1))  
            {  
                MessageBox.Show("Please specify an order amount.");  
                return false;  
            }  
            else  
            {  
                // Order can be submitted.  
                return true;  
            }  
        }  
  
        //NC-27 Reset the form for another new account  
        private void btnAddAnotherAccount_Click(object sender, EventArgs e)  
        {  
            this.ClearForm();  
        }  
  
        //NC-28 Clear values from controls  
        private void ClearForm()  
        {  
            txtCustomerName.Clear();  
            txtCustomerID.Clear();  
            dtpOrderDate.Value = DateTime.Now;  
            numOrderAmount.Value = 0;  
            this.parsedCustomerID = 0;  
        }  
  
        //NC-29 Close the form.  
        private void btnAddFinish_Click(object sender, EventArgs e)  
        {  
            this.Close();  
        }  
  
    }  
}  
  
```  
  
```vb  
Imports System  
Imports System.Collections.Generic  
Imports System.ComponentModel  
Imports System.Data  
Imports System.Drawing  
Imports System.Linq  
Imports System.Text  
Imports System.Threading.Tasks  
Imports System.Windows.Forms  
' NC-1 More namespaces.  
Imports System.Data.SqlClient  
Imports System.Configuration  
  
Namespace SimpleDataApp  
    Partial Public Class NewCustomer  
        Inherits Form  
  
        ' NC-2 Storage for IDENTITY values returned from database.  
        Private parsedCustomerID As Integer  
        Private orderID As Integer  
  
        ' NC-3 Specify a connection string.  
        Private connstr As String = SimpleDataApp.Utility.GetConnectionString()  
  
        Public Sub New()  
            InitializeComponent()  
        End Sub  
  
        ' NC-4 Create account.  
        Private Sub btnCreateAccount_Click() Handles btnCreateAccount.Click  
  
            ' NC-5 Set up and run stored procedure only if Customer Name is present.  
            If isCustomerName() Then  
  
                ' NC-6 Create the connection.  
                Dim conn As New SqlConnection(connstr)  
  
                ' NC-7 Create a SqlCommand, and identify it as a stored procedure.  
                Dim cmdNewCustomer As New SqlCommand("Sales.uspNewCustomer", conn)  
                cmdNewCustomer.CommandType = CommandType.StoredProcedure  
  
                ' NC-8 Add input parameter from the stored procedure and specify what to use as its value.  
                cmdNewCustomer.Parameters.Add(New SqlParameter("@CustomerName", SqlDbType.NVarChar, 40))  
                cmdNewCustomer.Parameters("@CustomerName").Value = txtCustomerName.Text  
  
                ' NC-9 Add output parameter.  
                cmdNewCustomer.Parameters.Add(New SqlParameter("@CustomerID", SqlDbType.Int))  
                cmdNewCustomer.Parameters("@CustomerID").Direction = ParameterDirection.Output  
  
                ' NC-10 try-catch-finally  
                Try  
                    ' NC-11 Open the connection.  
                    conn.Open()  
  
                    ' NC-12 Run the stored procedure.  
                    cmdNewCustomer.ExecuteNonQuery()  
  
                    ' NC-13 Customer ID is an IDENTITY value from the database.   
                    Me.parsedCustomerID = CInt(cmdNewCustomer.Parameters("@CustomerID").Value)  
                    Me.txtCustomerID.Text = Convert.ToString(parsedCustomerID)  
  
                Catch  
                    ' NC-14 A simple catch.  
                    MessageBox.Show("Customer ID was not returned. Account could not be created.")  
                Finally  
                    ' NC-15 Close the connection.  
                    conn.Close()  
                End Try  
            End If  
        End Sub  
  
        ' NC-16 Verify that Customer Name is present.  
        Private Function isCustomerName() As Boolean  
            If txtCustomerName.Text = "" Then  
                MessageBox.Show("Please enter a name.")  
                Return False  
            Else  
                Return True  
            End If  
        End Function  
  
        ' NC-17 Place order.  
        Private Sub btnPlaceOrder_Click() Handles btnPlaceOrder.Click  
  
            ' NC-18 Set up and run stored procedure only if necessary input is present.  
            If isPlaceOrderReady() Then  
  
                ' Create the connection.  
                Dim conn As New SqlConnection(connstr)  
  
                ' NC-19 Create SqlCommand and identify it as a stored procedure.  
                Dim cmdNewOrder As New SqlCommand("Sales.uspPlaceNewOrder", conn)  
                cmdNewOrder.CommandType = CommandType.StoredProcedure  
  
                ' NC-20 @CustomerID, which was an output parameter from uspNewCustomer.  
                cmdNewOrder.Parameters.Add(New SqlParameter("@CustomerID", SqlDbType.Int))  
                cmdNewOrder.Parameters("@CustomerID").Value = Me.parsedCustomerID  
  
                ' NC-21 @OrderDate.  
                cmdNewOrder.Parameters.Add(New SqlParameter("@OrderDate", SqlDbType.DateTime, 8))  
                cmdNewOrder.Parameters("@OrderDate").Value = dtpOrderDate.Value  
  
                ' NC-22 @Amount.  
                cmdNewOrder.Parameters.Add(New SqlParameter("@Amount", SqlDbType.Int))  
                cmdNewOrder.Parameters("@Amount").Value = numOrderAmount.Value  
  
                ' NC-23 @Status. For a new order, the status is always O (open).  
                cmdNewOrder.Parameters.Add(New SqlParameter("@Status", SqlDbType.[Char], 1))  
                cmdNewOrder.Parameters("@Status").Value = "O"  
  
                ' NC-24 add return value for stored procedure, which is the orderID  
                cmdNewOrder.Parameters.Add(New SqlParameter("@RC", SqlDbType.Int))  
                cmdNewOrder.Parameters("@RC").Direction = ParameterDirection.ReturnValue  
  
                ' try – catch - finally  
                Try  
                    ' Open connection.  
                    conn.Open()  
  
                    ' Run the stored procedure.  
                    cmdNewOrder.ExecuteNonQuery()  
  
                    ' NC-25 Display the order number.  
                    Me.orderID = CInt(cmdNewOrder.Parameters("@RC").Value)  
                    MessageBox.Show("Order number " & (Me.orderID).ToString & " has been submitted.")  
  
                Catch  
                    ' A simple catch.  
                    MessageBox.Show("Order could not not be placed.")  
  
                Finally  
                    ' Close connection.  
                    conn.Close()  
                End Try  
            End If  
        End Sub  
  
        ' NC-26 Verify that order data is ready.  
        Private Function isPlaceOrderReady() As Boolean  
  
            ' Verify that CustomerID is present.  
            If txtCustomerID.Text = "" Then  
                MessageBox.Show("Please create customer account before placing order.")  
                Return False  
  
                ' Verify that Amount isn't 0   
            ElseIf (numOrderAmount.Value < 1) Then  
  
                MessageBox.Show("Please specify an order amount.")  
                Return False  
            Else  
                ' Order can be submitted.  
                Return True  
            End If  
        End Function  
  
        ' NC-27 Reset the form for another new account.  
        Private Sub btnAddAnotherAccount_Click() Handles btnAddAnotherAccount.Click  
            Me.ClearForm()  
        End Sub  
  
        ' NC-28 Clear values from controls.  
        Private Sub ClearForm()  
            txtCustomerName.Clear()  
            txtCustomerID.Clear()  
            dtpOrderDate.Value = DateTime.Now  
            numOrderAmount.Value = 0  
            Me.parsedCustomerID = 0  
        End Sub  
  
        ' NC-29 Close the form.  
        Private Sub btnAddFinish_Click() Handles btnAddFinish.Click  
            Me.Close()  
        End Sub  
  
    End Class  
End Namespace  
```  
  
|Commentaire|Description|  
|-----------------|-----------------|  
|NC\-1|Ajoutez System.Data.SqlClient et System.Configuration à la liste des espaces de noms.|  
|NC\-2|Déclarez les variables `parsedCustomerID` et `orderID`, que vous utiliserez ultérieurement.|  
|NC\-3|Appelez la méthode `GetConnectionString` pour obtenir la chaîne de connexion du fichier de configuration d'application, et stockez la valeur dans la variable chaîne `connstr`.|  
|NC\-4|Ajoutez le code au gestionnaire d'événements Click pour le bouton `btnCreateAccount`.|  
|NC\-5|Enveloppez l'appel à `isCustomerName` autour du code de l'événement Click pour qu'`uspNewCustomer` s'exécute uniquement si un nom de client est présent.|  
|NC\-6|Créez un objet `SqlConnection` \(`conn`\) et passez la chaîne de connexion dans `connstr`.|  
|NC\-7|Créez un objet `SqlCommand`, `cmdNewCustomer`.<br /><br /> -   Spécifiez `Sales.uspNewCustomer` en tant que procédure stockée à exécuter.<br />-   Utilisez la propriété `CommandType` pour indiquer que la commande est une procédure stockée.|  
|NC\-8|Ajoutez le paramètre d'entrée `@CustomerName` de la procédure stockée.<br /><br /> -   Ajoutez le paramètre à la collection `Parameters`.<br />-   Utilisez l'énumération SqlDbType pour spécifier le type de paramètre comme nvarchar\(40\).<br />-   Spécifiez `txtCustomerName.Text` comme source.|  
|NC\-9|Ajoutez le paramètre de sortie de la procédure stockée.<br /><br /> -   Ajoutez le paramètre à la collection `Parameters`.<br />-   Utilisez `ParameterDirection.Output` pour identifier le paramètre en tant que sortie.|  
|NC\-10|Ajoutez un bloc Try – Catch – Finally pour ouvrir la connexion, exécuter la procédure stockée, gérer les exceptions, puis fermer la connexion.|  
|NC\-11|Ouvrez la connexion \(`conn`\) que vous avez créée au niveau NC\-6.|  
|NC\-12|Utilisez la méthode `ExecuteNonQuery` de `cmdNewCustomer` pour exécuter la procédure stockée `Sales.uspNewCustomer`, qui exécute une instruction `INSERT`, pas une requête.|  
|NC\-13|La valeur `@CustomerID` est retournée en tant que valeur IDENTITY à partir de la base de données.  Étant donné qu'il s'agit d'un entier, vous devez le convertir en une chaîne pour l'afficher dans la zone de texte Customer ID.<br /><br /> -   Vous avez déclaré `parsedCustomerID` au niveau NC\-2.<br />-   Stockez la valeur de `@CustomerID` dans `parsedCustomerID` pour une utilisation ultérieure.<br />-   Convertissez l'ID de client retourné en une chaîne et insérez celle\-ci dans `txtCustomerID.Text`.|  
|NC\-14|Pour cet exemple, ajoutez une clause catch simple, non liée à la qualité de la production.|  
|NC\-15|Fermez toujours une connexion après avoir terminé de l'utiliser pour qu'elle soit libérée dans le pool de connexions.  Consultez [Regroupement de connexions SQL Server \(ADO.NET\)](http://msdn.microsoft.com/library/8xx3tyca\(l=en-us,v=VS.110\).aspx).|  
|NC\-16|Définissez une méthode pour vérifier qu'il existe un nom de client.<br /><br /> -   Si la zone de texte est vide, affiche un message et retourne `false`, car un nom est nécessaire pour créer le compte.<br />-   Si la zone de texte n'est pas vide, retourne `true`.|  
|NC\-17|Ajoutez le code au gestionnaire d'événements Click pour le bouton `btnPlaceOrder`.|  
|NC\-18|Enveloppez l'appel à `isPlaceOrderReady` autour du code de l'événement `btnPlaceOrder_Click` pour qu'`uspPlaceNewOrder` ne s'exécute pas si l'entrée requise n'est pas présente.|  
|NC\-19 à NC\-25|Ces sections de code sont similaires au code que vous avez ajouté pour le gestionnaire d'événements `btnCreateAccount_Click`.<br /><br /> -   NC\-19.  Créez l'objet `SqlCommand`, `cmdNewOrder`, et spécifiez `Sales.uspPlaceOrder` en tant que procédure stockée.<br />-   NC\-20 à NC\-23 correspondent aux paramètres d'entrée pour la procédure stockée.<br />-   NC\-24.  `@RC` contient une valeur de retour qui correspond à la référence de commande générée depuis la base de données.  La direction de ce paramètre est spécifiée comme `ReturnValue`.<br />-   NC\-25.  Stockez la valeur de la référence de commande dans la variable `orderID` que vous avez déclarée au niveau NC\-2, puis affichez la valeur dans une boîte de message.|  
|NC\-26|Définissez une méthode pour vérifier qu'un ID de client existe et qu'une quantité a été spécifiée dans `numOrderAmount`.|  
|NC\-27|Appelez la méthode `ClearForm` dans le gestionnaire d'événements Click `btnAddAnotherAccount`.|  
|NC\-28|Créez la méthode `ClearForm` pour effacer les valeurs du formulaire si vous souhaitez ajouter un client.|  
|NC\-29|Fermez le formulaire NewCustomer et retournez le focus au formulaire Navigation.|  
  
### Formulaire FillOrCancel  
 Le formulaire FillorCancel exécute une requête pour retourner une commande quand vous entrez une référence de commande et que vous choisissez le bouton **Find Order**.  La ligne retournée apparaît dans une grille de données en lecture seule.  Vous pouvez marquer la commande comme annulée \(X\) en choisissant le bouton **Cancel Order**, ou comme remplie \(F\) en choisissant le bouton **Fill Order**.  Si vous choisissez à nouveau le bouton **Find Order**, la ligne mise à jour apparaît.  
  
#### Créer des gestionnaires d'événements  
 Créez des gestionnaires d'événements Click vides pour les quatre boutons du formulaire.  
  
#### Créer du code pour le formulaire FillOrCancel  
 Ajoutez le code suivant au formulaire FillOrCancel.  Parcourez les blocs de code en utilisant les commentaires numérotés et le tableau situé après le code.  
  
```c#  
using System;  
using System.Collections.Generic;  
using System.ComponentModel;  
using System.Data;  
using System.Drawing;  
using System.Linq;  
using System.Text;  
using System.Threading.Tasks;  
using System.Windows.Forms;  
//FC-1 More namespaces.  
using System.Text.RegularExpressions;  
using System.Data.SqlClient;  
using System.Configuration;  
  
namespace SimpleDataApp  
{  
    public partial class FillOrCancel : Form  
    {  
        //FC-2 Storage for OrderID.  
        private int parsedOrderID;  
  
        //FC-3 Specify a connection string.  
        string connstr = SimpleDataApp.Utility.GetConnectionString();  
  
        public FillOrCancel()  
        {  
            InitializeComponent();  
        }  
  
        //FC-4 Find an order.  
        private void btnFindByOrderID_Click(object sender, EventArgs e)  
        {  
            //FC-5 Prepare the connection and the command  
            if (isOrderID())  
            {  
                //Create the connection.  
                SqlConnection conn = new SqlConnection(connstr);  
  
                //Define a query string that has a parameter for orderID.  
                string sql = "select * from Sales.Orders where orderID = @orderID";  
  
                //Create a SqlCommand object.  
                SqlCommand cmdOrderID = new SqlCommand(sql, conn);  
  
                //Define the @orderID parameter and its value.  
                cmdOrderID.Parameters.Add(new SqlParameter("@orderID", SqlDbType.Int));  
                cmdOrderID.Parameters["@orderID"].Value = parsedOrderID;  
  
                //try – catch - finally  
                try  
                {  
                    //FC-6 Run the command and display the results.  
                    //Open the connection.  
                    conn.Open();  
  
                    //Run the command by using SqlDataReader.  
                    SqlDataReader rdr = cmdOrderID.ExecuteReader();  
  
                    //Create a data table to hold the retrieved data.  
                    DataTable dataTable = new DataTable();  
  
                    //Load the data from SqlDataReader into the data table.  
                    dataTable.Load(rdr);  
  
                    //Display the data from the datatable in the datagridview.  
                    this.dgvCustomerOrders.DataSource = dataTable;  
  
                    //Close the SqlDataReader.  
                    rdr.Close();  
                }  
                catch  
                {  
                    //A simple catch.  
                    MessageBox.Show("The requested order could not be loaded into the form.");  
                }  
                finally  
                {  
                    //Close the connection.  
                    conn.Close();  
                }  
            }  
        }  
  
        //FC-7 Cancel an order.  
        private void btnCancelOrder_Click(object sender, EventArgs e)  
        {  
            //Set up and run stored procedure only if OrderID is ready.  
            if (isOrderID())  
            {  
                //Create the connection.  
                SqlConnection conn = new SqlConnection(connstr);  
  
                // Create command and identify it as a stored procedure.  
                SqlCommand cmdCancelOrder = new SqlCommand("Sales.uspCancelOrder", conn);  
                cmdCancelOrder.CommandType = CommandType.StoredProcedure;  
  
                cmdCancelOrder.Parameters.Add(new SqlParameter("@orderID", SqlDbType.Int));  
                cmdCancelOrder.Parameters["@orderID"].Value = parsedOrderID;  
  
                // try-catch-finally  
                try  
                {  
                    // Open the connection.  
                    conn.Open();  
  
                    // Run the cmdCancelOrder command.  
                    cmdCancelOrder.ExecuteNonQuery();  
                }  
                // A simple catch.  
                catch  
                {  
                    MessageBox.Show("The cancel operation was not completed.");  
                }  
                finally  
                {  
                    //Close connection.  
                    conn.Close();  
                }  
            }  
        }  
  
        //FC-8 Fill an order.  
        private void btnFillOrder_Click(object sender, EventArgs e)  
        {  
            //Set up and run stored procedure only if OrderID is ready.  
            if (isOrderID())  
            {  
                //Create the connection.  
                SqlConnection conn = new SqlConnection(connstr);  
  
                //Create command and identify it as a stored procedure.  
                SqlCommand cmdFillOrder = new SqlCommand("Sales.uspFillOrder", conn);  
                cmdFillOrder.CommandType = CommandType.StoredProcedure;  
  
                // Add input parameter from the stored procedure.  
                cmdFillOrder.Parameters.Add(new SqlParameter("@orderID", SqlDbType.Int));  
                cmdFillOrder.Parameters["@orderID"].Value = parsedOrderID;  
  
                //Add the second input parameter.  
                cmdFillOrder.Parameters.Add(new SqlParameter("@FilledDate", SqlDbType.DateTime, 8));  
                cmdFillOrder.Parameters["@FilledDate"].Value = dtpFillDate.Value;  
  
                //try – catch - finally  
                try  
                {  
                    //Open the connection.  
                    conn.Open();  
  
                    //Run the cmdFillOrder command.  
                    cmdFillOrder.ExecuteNonQuery();  
                }  
                catch  
                {  
                    //A simple catch.  
                    MessageBox.Show("The fill operation was not completed.");  
                }  
                finally  
                {  
                    //Close the connection.  
                    conn.Close();  
                }  
            }  
        }  
  
        //FC-9 Verify that OrderID is ready.  
        private bool isOrderID()  
        {  
  
            //Check for input in the Order ID text box.  
            if (txtOrderID.Text == "")  
            {  
                MessageBox.Show("Please specify the Order ID.");  
                return false;  
            }  
  
            // Check for characters other than integers.  
            else if (Regex.IsMatch(txtOrderID.Text, @"^\D*$"))  
            {  
               //Show message and clear input.  
                MessageBox.Show("Please specify integers only.");  
                txtOrderID.Clear();  
                return false;  
            }  
            else  
            {  
                //Convert the text in the text box to an integer to send to the database.  
                parsedOrderID = Int32.Parse(txtOrderID.Text);  
                return true;  
            }  
        }  
  
        //Close the form.  
        private void btnFinishUpdates_Click(object sender, EventArgs e)  
        {  
            this.Close();  
        }  
    }  
}  
```  
  
```vb  
Imports System  
Imports System.Collections.Generic  
Imports System.ComponentModel  
Imports System.Data  
Imports System.Drawing  
Imports System.Linq  
Imports System.Text  
Imports System.Threading.Tasks  
Imports System.Windows.Forms  
' FC-1 More namespaces.  
Imports System.Text.RegularExpressions  
Imports System.Data.SqlClient  
Imports System.Configuration  
  
Namespace SimpleDataApp  
    Partial Public Class FillOrCancel  
        Inherits Form  
        ' FC-2 Storage for OrderID  
        Private parsedOrderID As Integer  
  
        ' FC-3 Specify a connection string  
        Private connstr As String = SimpleDataApp.Utility.GetConnectionString()  
  
        Public Sub New()  
            InitializeComponent()  
        End Sub  
  
        ' FC-4 Find an order.  
        Private Sub btnFindByOrderID_Click() Handles btnFindByOrderID.Click  
  
            ' FC-5 Prepare the connection and the command.  
  
            If isOrderID() Then  
                ' Create the connection.  
                Dim conn As New SqlConnection(connstr)  
  
                ' Define the query string that has a parameter for orderID.  
                Dim sql As String = "select * from Sales.Orders where orderID = @orderID"  
  
                ' Create a SqlCommand object.  
                Dim cmdOrderID As New SqlCommand(sql, conn)  
  
                ' Define the @orderID parameter and its value.  
                cmdOrderID.Parameters.Add(New SqlParameter("@orderID", SqlDbType.Int))  
                cmdOrderID.Parameters("@orderID").Value = parsedOrderID  
  
                ' try-catch-finally  
                Try  
                    ' FC-6 Run the command and display the results.  
                    ' Open connection.  
                    conn.Open()  
  
                    ' Run the command by using SqlDataReader.  
                    Dim rdr As SqlDataReader = cmdOrderID.ExecuteReader()  
  
                    ' Create a data table to hold the retrieved data.  
                    Dim dataTable As New DataTable()  
  
                    ' Load the data from the SqlDataReader into the data table.  
                    dataTable.Load(rdr)  
  
                    ' Display the data from the data table in the datagridview.  
                    Me.dgvCustomerOrders.DataSource = dataTable  
  
                    ' Close the SqlDataReader.  
                    rdr.Close()  
                Catch  
                    ' A simple catch.  
                    MessageBox.Show("The requested order could not be loaded into the form.")  
                Finally  
                    ' Close the connection.  
                    conn.Close()  
                End Try  
            End If  
        End Sub  
  
        ' FC-7 Cancel an order.  
        Private Sub btnCancelOrder_Click() Handles btnCancelOrder.Click  
  
            ' Set up and run stored procedure only if OrderID is ready.  
            If isOrderID() Then  
  
                ' Create the connection.  
                Dim conn As New SqlConnection(connstr)  
  
                ' Create the command and identify it as a stored procedure.  
                Dim cmdCancelOrder As New SqlCommand("Sales.uspCancelOrder", conn)  
                cmdCancelOrder.CommandType = CommandType.StoredProcedure  
  
                ' Add input parameter from the stored procedure.  
                cmdCancelOrder.Parameters.Add(New SqlParameter("@orderID", SqlDbType.Int))  
                cmdCancelOrder.Parameters("@orderID").Value = parsedOrderID  
  
                ' try-catch-finally  
                Try  
                    ' Open the connection.  
                    conn.Open()  
  
                    ' Run the cmdCancelOrder command.  
                    cmdCancelOrder.ExecuteNonQuery()  
                Catch  
                    ' A simple catch.  
                    MessageBox.Show("The cancel operation was not completed.")  
                Finally  
                    ' Close connection.  
                    conn.Close()  
                End Try  
            End If  
        End Sub  
  
        ' FC-8 Fill an order.  
        Private Sub btnFillOrder_Click() Handles btnFillOrder.Click  
  
            ' Set up and run stored procedure only if OrderID is ready.  
            If isOrderID() Then  
  
                ' Create the connection.  
                Dim conn As New SqlConnection(connstr)  
  
                ' Create command and identify it as a stored procedure.  
                Dim cmdFillOrder As New SqlCommand("Sales.uspFillOrder", conn)  
                cmdFillOrder.CommandType = CommandType.StoredProcedure  
  
                ' Add input parameter from the stored procedure.  
                cmdFillOrder.Parameters.Add(New SqlParameter("@orderID", SqlDbType.Int))  
                cmdFillOrder.Parameters("@orderID").Value = parsedOrderID  
  
                ' Add second input parameter.  
                cmdFillOrder.Parameters.Add(New SqlParameter("@FilledDate", SqlDbType.DateTime, 8))  
                cmdFillOrder.Parameters("@FilledDate").Value = dtpFillDate.Value  
  
                ' try-catch-finally  
                Try  
                    ' Open the connection.  
                    conn.Open()  
  
                    ' Run the cmdFillOrder command.   
                    cmdFillOrder.ExecuteNonQuery()  
                Catch  
                    ' A simple catch.  
                    MessageBox.Show("The fill operation was not completed.")  
                Finally  
                    ' Close the connection.  
                    conn.Close()  
                End Try  
            End If  
        End Sub  
  
        ' FC-9 Verify that OrderID is ready.  
        Private Function isOrderID() As Boolean  
  
            ' Check for input in the Order ID text box.  
            If txtOrderID.Text = "" Then  
                MessageBox.Show("Please specify the Order ID.")  
                Return False  
  
                ' Check for characters other than integers.  
            ElseIf Regex.IsMatch(txtOrderID.Text, "^\D*$") Then  
  
                ' Show message and clear input.  
                MessageBox.Show("Please specify integers only.")  
                txtOrderID.Clear()  
                Return False  
  
            Else  
                ' Convert the text in the text box to an integer to send to the database.  
                parsedOrderID = Int32.Parse(txtOrderID.Text)  
                Return True  
  
            End If  
        End Function  
  
        ' Close the form.  
        Private Sub btnFinishUpdates_Click() Handles btnFinishUpdates.Click  
            Me.Close()  
        End Sub  
    End Class  
End Namespace  
```  
  
|Commentaire|Description|  
|-----------------|-----------------|  
|FC\-1|Ajoutez System.Data.SqlClient, System.Configuration et System.Text.RegularExpressions à la liste des espaces de noms.|  
|FC\-2|Déclarez la variable `parsedOrderID`.|  
|FC\-3|Appelez la méthode `GetConnectionString` pour obtenir la chaîne de connexion du fichier de configuration d'application, et stockez la valeur dans la variable chaîne `connstr`.|  
|FC\-4|Ajoutez le code au gestionnaire d'événements Click pour `btnFindOrderByID`.|  
|FC\-5|Cela vous rappelle quelque chose ?  Ces tâches sont obligatoires avant que vous n'exécutiez une instruction SQL ou une procédure stockée.<br /><br /> -   Créez un objet SqlConnection.<br />-   Définissez l'instruction SQL ou indiquez le nom de la procédure stockée.  \(Dans ce cas, vous exécuterez une instruction `SELECT`.\)<br />-   Créez un objet `SqlCommand`.<br />-   Définissez les paramètres de l'instruction SQL ou de la procédure stockée.|  
|FC\-6|Ce code utilise `SqlDataReader` et `DataTable` pour récupérer et afficher le résultat de la requête.<br /><br /> -   Ouvrez la connexion.<br />-   Créez un SqlDataReader, `rdr`, en exécutant la méthode `ExecuteReader` de `cmdOrderID`.<br />-   Créez un objet `DataTable`, destiné à contenir les données récupérées.<br />-   Chargez les données de `SqlDataReader` dans l'objet `DataTable`.<br />-   Affichez les données dans le datagridview en spécifiant le `DataTable` comme `DataSource` pour datagridview.<br />-   Fermez le SqlDataReader.|  
|FC\-7|Ajoutez le code au gestionnaire d'événements Click pour `btnCancelOrder`.  Ce code exécute la procédure stockée `Sales.uspCancelOrder`.|  
|FC\-8|Ajoutez le code au gestionnaire d'événements Click pour `btnFillOrder`.  Ce code exécute la procédure stockée `Sales.uspFillOrder`.|  
|FC\-9|Créez une méthode pour vérifier que l'`OrderID` est prêt à être envoyé comme paramètre à l'objet `SqlCommand`.<br /><br /> -   Assurez\-vous qu'un ID a été entré dans `txtOrderID`.<br />-   Utilisez `Regex.IsMatch` pour définir un contrôle simple des caractères autres que les entiers.<br />-   Vous avez déclaré la variable `parsedOrderID` au niveau FC\-2.<br />-   Si l'entrée est valide, convertissez le texte en entier et stockez la valeur dans la variable `parsedOrderID`.<br />-   Enveloppez la méthode `isOrderID` autour des gestionnaires d'événements Click `btnFindByOrderID`, `btnCancelOrder` et `btnFillOrder`.|  
  
##  <a name="BKMK_testyourapplication"></a> Tester votre application  
 Choisissez la touche F5 pour générer et tester votre application après avoir codé chaque gestionnaire d'événements Click et avoir terminé le codage.