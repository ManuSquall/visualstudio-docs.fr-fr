---
title: Créer le composant WebPart Silverlight affichant OData pour SharePoint
ms.date: 02/22/2017
ms.topic: conceptual
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
ms.openlocfilehash: f248ce4403e771d9ab8b6d13fe55fd5ca1c960d4
ms.sourcegitcommit: 25570fb5fb197318a96d45160eaf7def60d49b2b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/30/2019
ms.locfileid: "66401130"
---
# <a name="walkthrough-create-a-silverlight-web-part-that-displays-odata-for-sharepoint"></a>Procédure pas à pas : Créer un composant WebPart Silverlight qui affiche OData pour SharePoint
  SharePoint 2010 expose ses données de liste au moyen d’OData. Dans SharePoint, le service OData est implémenté par le service RESTful ListData.svc. Cette procédure pas à pas montre comment créer un composant WebPart SharePoint qui héberge une application Silverlight. L’application Silverlight affiche des informations de liste SharePoint annonce à l’aide de ListData.svc. Pour plus d’informations, consultez [Interface REST de SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=225999) et [Open Data Protocol](http://go.microsoft.com/fwlink/?LinkId=226000).

 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Prérequis
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :

- Éditions prises en charge de Microsoft Windows et SharePoint.

- [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)].

## <a name="create-a-silverlight-application-and-silverlight-web-part"></a>Créer une application Silverlight et le composant WebPart Silverlight
 Tout d’abord, créez une application Silverlight dans Visual Studio. L’application Silverlight récupère des données à partir de la liste d’annonces de SharePoint en utilisant le service ListData.svc.

> [!NOTE]
> Aucune version de Silverlight avant 4.0 prend en charge les interfaces requises pour le référencement des données de liste SharePoint.

#### <a name="to-create-a-silverlight-application-and-silverlight-web-part"></a>Pour créer une application Silverlight et le composant WebPart Silverlight

1. Dans la barre de menus, choisissez **fichier** > **New** > **projet** pour afficher le **nouveau projet** boîte de dialogue.

2. Développez le **SharePoint** nœud sous **Visual C#** ou **Visual Basic**, puis choisissez le **2010** nœud.

3. Dans le volet Modèles, choisissez le **WebPart de SharePoint 2010 Silverlight** modèle.

4. Dans le **nom** , entrez **SLWebPartTest** , puis choisissez le **OK** bouton.

    Le **Assistant Personnalisation de SharePoint** boîte de dialogue s’affiche.

5. Sur le **spécifier le niveau de site et de sécurité pour le débogage** page, entrez l’URL pour le site du serveur SharePoint où vous souhaitez déboguer la définition de site ou utilisez l’emplacement par défaut (http://<em>nom système</em>/) .

6. Dans le **quel est le niveau de confiance de cette solution SharePoint ?** , choisissez le **déployer en tant que solution de batterie** case d’option.

    Bien que cet exemple utilise une solution de batterie de serveurs, les projets de partie web Silverlight peuvent être déployés en tant que batterie de serveurs ou de solutions sandbox. Pour plus d’informations sur les solutions bac à sable et les solutions de batterie de serveurs, consultez [considérations relatives à la solution bac à sable](../sharepoint/sandboxed-solution-considerations.md).

7. Dans le **Comment voulez-vous associer le composant WebPart Silverlight** section de la **spécifier des informations de Configuration Silverlight** page, choisissez le **créer un nouveau projet Silverlight et associer le composant WebPart** case d’option.

8. Modifier le **nom** à **SLApplication**, affectez la valeur **langage** soit **Visual Basic** ou **Visual C#** , puis définissez **Silverlight Version** à **Silverlight 4.0**.

9. Choisissez le **Terminer** bouton. Les projets s’affichent dans **l’Explorateur de solutions**.

     La solution contient deux projets : une application Silverlight et un composant WebPart Silverlight. L’application Silverlight récupère et affiche les données de liste à partir de SharePoint, et le composant WebPart Silverlight héberge l’application Silverlight, ce qui vous permet d’afficher dans SharePoint.

## <a name="customize-the-silverlight-application"></a>Personnaliser l’application Silverlight
 Ajouter des éléments de code et de conception à l’application Silverlight.

#### <a name="to-customize-the-silverlight-application"></a>Pour personnaliser l’application Silverlight

1. Ajoutez une référence d’assembly à System.Windows.Data dans l’application Silverlight. Pour plus d'informations, voir [Procédure : Ajouter ou supprimer des références à l’aide de la boîte de dialogue Ajouter référence](https://msdn.microsoft.com/3bd75d61-f00c-47c0-86a2-dd1f20e231c9).

2. Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour **références**, puis choisissez **ajouter une référence de Service**.

    > [!NOTE]
    > Si vous utilisez Visual Basic, vous devez choisir le **afficher tous les fichiers** icône en haut de **l’Explorateur de solutions** pour afficher le **références** nœud.

3. Dans la zone Adresse de la **ajouter une référence de Service** boîte de dialogue, entrez l’URL de votre site SharePoint, tels que **http://MySPSite** , puis choisissez le **accédez** bouton.

     Lorsque Silverlight localise le service SharePoint OData ListData.svc, il remplace l’adresse par l’URL du service complète. Pour cet exemple, http://myserver devient http://myserver/_vti_bin/ListData.svc.

4. Choisissez le **OK** bouton pour ajouter la référence de service au projet et utilisez le nom de service par défaut, ServiceReference1.

5. Dans la barre de menus, choisissez **Générer**  >  **Générer la solution**.

6. Ajouter une nouvelle source de données au projet basé sur le service SharePoint. Pour ce faire, dans la barre de menus, choisissez **vue** > **Windows autres** > **des Sources de données**.

     Le **des Sources de données** fenêtre affiche toutes les données de liste SharePoint disponibles, telles que des tâches, annonces et le calendrier.

7. Ajouter les données de liste d’annonces à l’application Silverlight. Vous pouvez faire glisser des « Annonces » à partir de la **des Sources de données** fenêtre sur le Concepteur Silverlight.

     Cette opération crée un contrôle de grille lié à la liste d’annonces du site SharePoint.

8. Redimensionner le contrôle de grille pour s’ajuster à la page Silverlight.

9. Dans le fichier de code de MainPage.xaml (*MainPage.xaml.cs* pour Visual c# ou *MainPage.xaml.vb* pour Visual Basic), ajoutez les références d’espace de noms suivantes.

    ```vb
    ' Add the following three Imports statements.
    Imports SLApplication.ServiceReference1
    Imports System.Windows.Data
    Imports System.Data.Services.Client
    ```

    ```csharp
    // Add the following three using statements.
    using SLApplication.ServiceReference1;
    using System.Windows.Data;
    using System.Data.Services.Client;
    ```

10. Ajoutez les déclarations de variable suivantes en haut de la classe.

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

11. Remplacez le `UserControl_Loaded` procédure par le code suivant.

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

     Veillez à remplacer le *nom_serveur* espace réservé par le nom de votre serveur qui exécute SharePoint.

12. Ajoutez la procédure suivante de la gestion des erreurs.

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
 Modifier une propriété dans le projet de composant WebPart Silverlight pour activer le débogage de Silverlight.

#### <a name="to-modify-the-silverlight-web-part"></a>Pour modifier le composant WebPart Silverlight

1. Ouvrez le menu contextuel pour le projet de composant WebPart Silverlight (**SLWebPartTest**), puis choisissez **propriétés**.

2. Dans le **propriétés** fenêtre, choisissez le **SharePoint** onglet.

3. Si ce n’est pas déjà fait, sélectionnez le **Silverlight activer le débogage (au lieu du débogage de Script)** case à cocher.

4. Enregistrez le projet.

## <a name="test-the-silverlight-web-part"></a>Tester le composant WebPart Silverlight
 Testez le nouveau composant WebPart Silverlight dans SharePoint pour vous assurer qu’il affiche correctement les données de liste SharePoint.

#### <a name="to-test-the-silverlight-web-part"></a>Pour tester le composant WebPart Silverlight

1. Choisissez le **F5** clé pour générer et exécuter la solution SharePoint.

2. Dans SharePoint, sur le **Actions du Site** menu, choisissez **nouvelle Page**.

3. Dans le **nouvelle Page** boîte de dialogue, entrez un titre, tel que **SL Web partie Test**, puis choisissez le **créer** bouton.

4. Dans le Concepteur de page, sur le **outils d’édition** , choisir **insérer**.

5. Sur la bande d’onglets, choisissez **WebPart**.

6. Dans le **catégories** , sélectionnez le **personnalisé** dossier.

7. Dans le **WebPart** liste, choisissez le composant WebPart Silverlight, puis le **ajouter** pour ajouter le composant WebPart vers le concepteur.

8. Une fois que vous avez apporté toutes les ajouts à la page web que vous le souhaitez, choisissez le **Page** onglet, puis choisissez le **Enregistrer & fermer** bouton sur la barre d’outils.

     Le composant WebPart Silverlight doit maintenant être affichage des données d’annonce à partir du site SharePoint. Par défaut, la page est stockée dans la liste de Pages de Site dans SharePoint.

    > [!NOTE]
    > Lors de l’accès aux données dans Silverlight sur plusieurs domaines, Silverlight vous protège contre des failles de sécurité qui peuvent être utilisés pour exploiter des applications web. Si vous rencontrez des problèmes lors de l’accès aux données distantes dans Silverlight, consultez [rendre un Service disponible entre les limites du domaine](http://go.microsoft.com/fwlink/?LinkId=223276).

## <a name="see-also"></a>Voir aussi
- [Créer des composants WebPart pour SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)
- [Déployer, publier et mettre à niveau de packages de solution SharePoint](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md)
