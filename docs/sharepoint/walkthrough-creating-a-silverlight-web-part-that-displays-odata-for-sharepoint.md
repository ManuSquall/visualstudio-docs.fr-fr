---
title: Créer un composant WebPart Silverlight affichant OData pour SharePoint
ms.date: 02/22/2017
ms.topic: how-to
f1_keywords:
- VS.SharePointTools.SPE.SilverlightWebPart
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 75653f0357bcc605e666ee271a527b616985b641
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "86017170"
---
# <a name="walkthrough-create-a-silverlight-web-part-that-displays-odata-for-sharepoint"></a>Procédure pas à pas : créer un composant WebPart Silverlight qui affiche OData pour SharePoint
  SharePoint 2010 expose ses données de liste au moyen d’OData. Dans SharePoint, le service OData est implémenté par le service RESTful ListData. svc. Cette procédure pas à pas montre comment créer un composant WebPart SharePoint qui héberge une application Silverlight. L’application Silverlight affiche les informations de liste d’annonces SharePoint à l’aide de ListData. svc. Pour plus d’informations, consultez [interface REST de SharePoint Foundation](/previous-versions/office/developer/sharepoint-2010/ff521587(v=office.14)) et [Open Data Protocol](https://www.odata.org/).

 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Prérequis
 Vous devez disposer des éléments suivants pour exécuter cette procédure pas à pas :

- Éditions prises en charge de Microsoft Windows et SharePoint.

- [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)].

## <a name="create-a-silverlight-application-and-silverlight-web-part"></a>Créer une application Silverlight et un composant WebPart Silverlight
 Tout d’abord, créez une application Silverlight dans Visual Studio. L’application Silverlight récupère les données de la liste des annonces SharePoint à l’aide du service ListData. svc.

> [!NOTE]
> Les versions de Silverlight antérieures à 4,0 prennent en charge les interfaces requises pour référencer les données de liste SharePoint.

#### <a name="to-create-a-silverlight-application-and-silverlight-web-part"></a>Pour créer une application Silverlight et un composant WebPart Silverlight

1. Dans la barre de menus, choisissez **fichier**  >  **nouveau**  >  **projet** pour afficher la boîte de dialogue **nouveau projet** .

2. Développez le nœud **SharePoint** sous **Visual C#** ou **Visual Basic**, puis choisissez le nœud **2010** .

3. Dans le volet modèles, choisissez le modèle **WebPart Silverlight SharePoint 2010** .

4. Dans la zone **nom** , entrez **SLWebPartTest** , puis choisissez le bouton **OK** .

    La boîte de dialogue **Assistant Personnalisation de SharePoint** s’affiche.

5. Dans la page **spécifier le site et le niveau de sécurité pour le débogage** , entrez l’URL du site du serveur SharePoint où vous souhaitez déboguer la définition de site, ou utilisez l’emplacement par défaut (<em>nom système</em>http:///).

6. Dans la section **quel est le niveau de confiance de cette solution SharePoint ?** , choisissez la case **d’option déployer en tant que solution de batterie** .

    Bien que cet exemple utilise une solution de batterie de serveurs, les projets WebPart Silverlight peuvent être déployés en tant que solutions de batterie de serveurs ou bac à sable (sandbox). Pour plus d’informations sur les solutions sandbox et les solutions de batterie de serveurs, consultez Considérations sur les solutions [bac à sable (sandbox)](../sharepoint/sandboxed-solution-considerations.md).

7. Dans la section **Comment voulez-vous associer le composant WebPart Silverlight** de la page **spécifier les informations de configuration Silverlight** , sélectionnez la case d’option **créer un nouveau projet Silverlight et l’associer au composant WebPart** .

8. Remplacez le **nom** par **SLApplication**, définissez **Language** sur **Visual Basic** ou **Visual C#**, puis définissez version de **Silverlight** sur **Silverlight 4,0**.

9. Cliquez sur le bouton **Terminer**. Les projets s’affichent dans **Explorateur de solutions**.

     La solution contient deux projets : une application Silverlight et un composant WebPart Silverlight. L’application Silverlight récupère et affiche les données de liste à partir de SharePoint, et le composant WebPart Silverlight héberge l’application Silverlight, ce qui vous permet de l’afficher dans SharePoint.

## <a name="customize-the-silverlight-application"></a>Personnaliser l’application Silverlight
 Ajoutez du code et des éléments de conception à l’application Silverlight.

#### <a name="to-customize-the-silverlight-application"></a>Pour personnaliser l’application Silverlight

1. Ajoutez une référence d’assembly à System. Windows. Data dans l’application Silverlight. Pour plus d’informations, consultez [Comment : ajouter ou supprimer des références à l’aide de la boîte de dialogue Ajouter une référence](https://msdn.microsoft.com/3bd75d61-f00c-47c0-86a2-dd1f20e231c9).

2. Dans **Explorateur de solutions**, ouvrez le menu contextuel pour **références**, puis choisissez **Ajouter une référence de service**.

    > [!NOTE]
    > Si vous utilisez Visual Basic, vous devez choisir l’icône **Afficher tous les fichiers** en haut de **Explorateur de solutions** pour afficher le nœud **références** .

3. Dans la zone adresse de la boîte de dialogue **Ajouter une référence de service** , entrez l’URL de votre site SharePoint, par exemple **http://MySPSite** , puis choisissez le bouton **OK** .

     Lorsque Silverlight localise le service OData SharePoint ListData. svc, il remplace l’adresse par l’URL de service complète. Pour cet exemple, http://myserver devient http://myserver/_vti_bin/ListData.svc .

4. Choisissez le bouton **OK** pour ajouter la référence de service au projet et utilisez le nom de service par défaut, ServiceReference1.

5. Dans la barre de menus, choisissez **générer**  >  **générer la solution**.

6. Ajoutez une nouvelle source de données au projet basé sur le service SharePoint. Pour ce faire, dans la barre de menus, choisissez **Afficher**d'  >  **autres**  >  **sources de données**Windows.

     La fenêtre **sources de données** affiche toutes les données de liste SharePoint disponibles, telles que les tâches, les annonces et le calendrier.

7. Ajoutez les données de liste d’annonces à l’application Silverlight. Vous pouvez faire glisser « annonces » depuis la fenêtre **sources de données** vers le Concepteur Silverlight.

     Cela crée un contrôle de grille lié à la liste d’annonces du site SharePoint.

8. Redimensionnez le contrôle de grille en fonction de la page Silverlight.

9. Dans le fichier de code MainPage. XAML (*MainPage.Xaml.cs* pour Visual C# ou *MainPage. Xaml. vb* pour Visual Basic), ajoutez les références d’espace de noms suivantes.

    ```vb
    ' Add the following three Imports statements.
    Imports SLApplication.ServiceReference1
    Imports System.Windows.Data
    Imports System.Data.Services.Client
    ```

    ```csharp
    // Add the following three using directives.
    using SLApplication.ServiceReference1;
    using System.Windows.Data;
    using System.Data.Services.Client;
    ```

10. Ajoutez les déclarations de variables suivantes en haut de la classe.

    ```vb
    Private context As TeamSiteDataContext
    Private myCollectionViewSource As CollectionViewSource
    Private announcements As New DataServiceCollection(Of AnnouncementsItem)()
    ```

    ```csharp
    private TeamSiteDataContext context;
    private CollectionViewSource myCollectionViewSource;
    DataServiceCollection<AnnouncementsItem> announcements = new DataServiceCollection<AnnouncementsItem>();
    ```

11. Remplacez la `UserControl_Loaded` procédure par le code suivant.

    ```vb
    Private Sub UserControl_Loaded_1(sender As Object, e As RoutedEventArgs)
        ' The URL for the OData service.
        ' Replace <server name> in the next line with the name of your SharePoint server.
        context = New TeamSiteDataContext(New Uri("http://<server name>/_vti_bin/ListData.svc"))

        ' Do not load your data at design time.
        If Not System.ComponentModel.DesignerProperties.GetIsInDesignMode(Me) Then
            'Load your data here and assign the results to the CollectionViewSource.
            myCollectionViewSource =   DirectCast(Me.Resources("announcementsViewSource"), System.Windows.Data.CollectionViewSource)
            announcements.LoadCompleted += New EventHandler(Of LoadCompletedEventArgs)(AddressOf announcements_LoadCompleted)
            announcements.LoadAsync(context.Announcements)
        End If
    End Sub
    ```

    ```csharp
    private void UserControl_Loaded_1(object sender, RoutedEventArgs e)
    {
        // The URL for the OData service.
        // Replace <server name> in the next line with the name of your
        // SharePoint server.
        context = new TeamSiteDataContext(new Uri("http://ServerName>/_vti_bin/ListData.svc"));

        // Do not load your data at design time.
        if (!System.ComponentModel.DesignerProperties.GetIsInDesignMode(this))
        {
            //Load your data here and assign the results to the CollectionViewSource.
            myCollectionViewSource = (System.Windows.Data.CollectionViewSource)this.Resources["announcementsViewSource"];
            announcements.LoadCompleted += new EventHandler<LoadCompletedEventArgs>(announcements_LoadCompleted);
            announcements.LoadAsync(context.Announcements);
        }
    }
    ```

     Veillez à remplacer l’espace réservé *ServerName* par le nom de votre serveur qui exécute SharePoint.

12. Ajoutez la procédure de gestion des erreurs suivante.

    ```vb
    Private Sub announcements_LoadCompleted(sender As Object, e As LoadCompletedEventArgs)
        ' Handle any errors.
        If e.[Error] Is Nothing Then
            myCollectionViewSource.Source = announcements
        Else
            MessageBox.Show(String.Format("ERROR: {0}", e.[Error].Message))
        End If
    End Sub

    ```

    ```csharp
    void announcements_LoadCompleted(object sender, LoadCompletedEventArgs e)
    {
        // Handle any errors.
        if (e.Error == null)
        {
            myCollectionViewSource.Source = announcements;
        }
        else
        {
            MessageBox.Show(string.Format("ERROR: {0}", e.Error.Message));
        }
    }
    ```

## <a name="modify-the-silverlight-web-part"></a>Modifier le composant WebPart Silverlight
 Modifiez une propriété dans le projet de composant WebPart Silverlight pour activer le débogage Silverlight.

#### <a name="to-modify-the-silverlight-web-part"></a>Pour modifier le composant WebPart Silverlight

1. Ouvrez le menu contextuel du projet WebPart Silverlight (**SLWebPartTest**), puis choisissez **Propriétés**.

2. Dans la fenêtre **Propriétés** , choisissez l’onglet **SharePoint** .

3. Si cette option n’est pas déjà sélectionnée, activez la case à cocher **activer le débogage Silverlight (au lieu du débogage de script)** .

4. Enregistrez le projet.

## <a name="test-the-silverlight-web-part"></a>Tester le composant WebPart Silverlight
 Testez le nouveau composant WebPart Silverlight dans SharePoint pour vous assurer qu’il affiche correctement les données de la liste SharePoint.

#### <a name="to-test-the-silverlight-web-part"></a>Pour tester le composant WebPart Silverlight

1. Appuyez sur la touche **F5** pour générer et exécuter la solution SharePoint.

2. Dans SharePoint, dans le menu **actions du site** , choisissez **nouvelle page**.

3. Dans la boîte de dialogue **nouvelle page** , entrez un titre, par exemple **SL Web part test**, puis cliquez sur le bouton **créer** .

4. Dans le concepteur de pages, sous l’onglet **Outils d’édition** , choisissez **Insérer**.

5. Dans la bande d’onglets, choisissez **composant WebPart**.

6. Dans la zone **catégories** , choisissez le dossier **personnalisé** .

7. Dans la liste **composants WebPart** , choisissez le composant WebPart Silverlight, puis cliquez sur le bouton **Ajouter** pour ajouter le composant WebPart au concepteur.

8. Une fois que vous avez apporté tous les ajouts à la page Web souhaités, choisissez l’onglet **page** , puis choisissez le bouton **Enregistrer & fermer** dans la barre d’outils.

     Le composant WebPart Silverlight doit maintenant afficher les données d’annonce à partir du site SharePoint. Par défaut, la page est stockée dans la liste pages de site dans SharePoint.

    > [!NOTE]
    > Lors de l’accès aux données dans Silverlight sur plusieurs domaines, Silverlight protège contre les failles de sécurité qui peuvent être utilisées pour exploiter des applications Web. Si vous rencontrez des problèmes lors de l’accès à des données distantes dans Silverlight, consultez Mise à [disposition d’un service au-delà des limites de domaine](/previous-versions/windows/silverlight/dotnet-windows-silverlight/cc197955(v=vs.95)).

## <a name="see-also"></a>Voir aussi
- [Créer des composants WebPart pour SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)
- [Déployer, publier et mettre à niveau des packages de solution SharePoint](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md)
