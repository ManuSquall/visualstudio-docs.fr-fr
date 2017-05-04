---
title: "Proc&#233;dure pas &#224; pas&#160;: cr&#233;ation d&#39;un composant WebPart Silverlight qui affiche OData pour SharePoint | Microsoft Docs"
ms.custom: ""
ms.date: "02/22/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.SharePointTools.SPE.SilverlightWebPart"
dev_langs: 
  - "VB"
  - "CSharp"
ms.assetid: 92d55e68-8f3f-4bf7-a21b-801c298b04c4
caps.latest.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 20
---
# Proc&#233;dure pas &#224; pas&#160;: cr&#233;ation d&#39;un composant WebPart Silverlight qui affiche OData pour SharePoint
  SharePoint 2010 présente les données de liste avec OData.  Dans SharePoint, le service OData est implémenté par le service RESTful ListData.svc.  Cette procédure pas\-à\-pas montre comment créer un composant WebPart SharePoint qui héberge une application Silverlight.  L'application Silverlight affiche l'information de la liste SharePoint Announcement à l'aide de ListData.svc.  Pour plus d'informations, consultez [Interface SharePoint Foundation REST](http://go.microsoft.com/fwlink/?LinkId=225999) et [Ouvrir un protocole de données](http://go.microsoft.com/fwlink/?LinkId=226000).  
  
 Cette procédure pas à pas présente les tâches suivantes :  
  
-   [Créer une application Silverlight et un composant WebPart de Silverlight](#BKMK_creatingSLApp).  
  
-   [Personnalisation de l'application Silverlight](#BKMK_customizeSLApp).  
  
-   [Personnalisation de l'application Silverlight](#BKMK_customizeSLApp).  
  
-   [Personnalisation de l'application Silverlight](#BKMK_customizeSLApp).  
  
-   [Test des composants WebPart Silverlight](#BKMK_testSLApp).  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Composants requis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   Éditions de Microsoft Windows et SharePoint prises en charge.  [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)] [Configuration requise pour développer des solutions SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)].  
  
##  <a name="BKMK_creatingSLApp"></a> Créer une application Silverlight et un composant WebPart de Silverlight  
 En premier lieu, créez une application Silverlight dans Visual Studio.  L'application Silverlight récupère les données de la liste Annonces SharePoint à l'aide du service de ListData.svc.  
  
> [!NOTE]  
>  Aucune version de Silverlight avant 4.0 ne prend en charge les interfaces requises pour référencer des données de liste SharePoint.  
  
#### Pour créer une application Silverlight et un composant WebPart de Silverlight  
  
1.  Dans la barre de menus, choisissez **Fichier**, **Nouveau**, **Projet** pour afficher la boîte de dialogue **Nouveau projet**.  
  
2.  Développez le nœud **SharePoint** sous **Visual C\#** ou **Visual Basic**, puis cliquez sur le noeud **2010**.  
  
3.  Dans le volet modèles, sélectionnez le modèle **WebPart SharePoint 2010 Silverlight**.  
  
4.  Dans la zone de texte **Nom**, entrez SLWebPartTest, puis choisissez le bouton **OK**.  
  
     La boîte de dialogue **Assistant Personnalisation de SharePoint** s'affiche.  
  
5.  Dans la page **Spécifier le site et le niveau de sécurité pour le débogage**, entrez l'URL du site du serveur SharePoint où vous souhaitez déboguer la définition de site, ou utilisez l'emplacement par défaut \(http:\/\/*system name*\/\).  
  
6.  Dans la section **Quel est le niveau de confiance de cette solution SharePoint ?**, choisissez la case d'option **Déployer en tant que solution de batterie**.  
  
     Bien que cet exemple utilise une solution de batterie de serveurs, les projets de Silverlight WebPart peuvent être déployés sous la forme d'une batterie de serveurs ou solutions sandboxed.  Pour plus d'informations sur les différences entre les solutions bac à sable \(sandbox\) et les solutions de batterie, consultez [Considérations sur les solutions bac à sable &#40;sandbox&#41;](../sharepoint/sandboxed-solution-considerations.md).  
  
7.  Dans la section **Comment souhaitez\-vous associer le composant WebPart de Silverlight** de la page **Spécifier les informations de configuration de Silverlight**, sélectionnez la case **Créer un projet Silverlight et l'associer au composant WebPart**.  
  
8.  Modifiez **Nom** à la valeur SLApplication, définissez **Langage** à **Visual Basic** ou à **Visual C\#**, puis définissez **Version de Silverlight** à **Silverlight 4.0**.  
  
9. Choisissez le bouton **Terminer**.  Les projets s'affichent dans l'**Explorateur de solutions**.  
  
     La solution contient plusieurs projets : une application Silverlight et un composant WebPart Silverlight.  L'application Silverlight récupère et affiche les données de liste SharePoint, et Silverlight WebPart héberge l'application Silverlight, vous permettant de l'afficher dans SharePoint.  
  
##  <a name="BKMK_customizeSLApp"></a> Personnalisation de l'application Silverlight  
 Ajouter des éléments de code et de création dans l'application Silverlight.  
  
#### Pour personnaliser l'application Silverlight  
  
1.  Ajouter une référence d'assembly à System.Windows.Data dans l'application Silverlight.  Pour plus d'informations, consultez [Comment : ajouter ou supprimer des références à l'aide de la boîte de dialogue Ajouter une référence](http://msdn.microsoft.com/fr-fr/3bd75d61-f00c-47c0-86a2-dd1f20e231c9).  
  
2.  Dans l'**Explorateur de solutions**, ouvrez le menu contextuel du nœud **References**, puis choisissez **Ajouter une référence de service**.  
  
    > [!NOTE]  
    >  Si vous utilisez Visual Basic, vous devez choisir l'icône **Afficher tous les fichiers** en haut de l'**Explorateur de solutions** pour afficher le nœud **Références**.  
  
3.  Dans la zone d'adresse de la boîte de dialogue **Ajouter une référence de service**, entrez l'URL de votre site SharePoint, tel qu' **http:\/\/MySPSite**, puis cliquez sur le bouton **OK**.  
  
     Lorsque Silverlight localise le service SharePoint OData ListData.svc, il remplace l'adresse par l'URL de service complet.  Pour cet exemple, http:\/\/myserver et http:\/\/myserver\/\_vti\_bin\/ListData.svc.  
  
4.  Cliquez sur le bouton **OK** pour ajouter la référence de service au projet, puis utilisez le nom du service par défaut, ServiceReference1.  
  
5.  Dans la barre de menus, choisissez **Générer**, puis **Générer la solution**.  
  
6.  Ajoutez une nouvelle source de données dans le projet basé sur le service SharePoint.  Pour effectuer cela, dans la barre de menus, sélectionnez **Afficher**, **Autres fenêtres**, **Sources de données**.  
  
     La fenêtre **Sources de données** affiche toutes les données disponibles de liste SharePoint, telles que des tâches, des annonces, et le calendrier.  
  
7.  Ajouter des données de liste Annonces à l'application Silverlight.  Vous pouvez faire glisser des "annonces" dans la fenêtre **Sources de données** dans le concepteur Silverlight.  
  
     Cela crée une grille lié à la liste Annonces du site SharePoint.  
  
8.  Redimensionnez la grille à la page de Silverlight.  
  
9. Dans le fichier de code de MainPage.xaml \(MainPage.xaml.cs pour Visual C\# ou MainPage.xaml.vb pour Visual Basic\), ajoutez des références d'espace de noms suivants.  
  
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
  
<!-- TODO: review snippet reference      [!CODE [SP_SLWebPart#1](SP_SLWebPart#1)]  -->  
  
10. Ajoutez les déclarations de variable suivantes en haut de la classe .  
  
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
  
<!-- TODO: review snippet reference      [!CODE [SP_SLWebPart#2](SP_SLWebPart#2)]  -->  
  
11. Remplacez la procédure `UserControl_Loaded` par la méthode suivante :  
  
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
  
<!-- TODO: review snippet reference      [!CODE [SP_SLWebPart#3](SP_SLWebPart#3)]  -->  
  
     Veillez à remplacer l'espace réservé *ServerName* par le nom de votre serveur exécutant SharePoint.  
  
12. Ajoutez la procédure de gestion d'erreur suivante.  
  
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
  
<!-- TODO: review snippet reference      [!CODE [SP_SLWebPart#4](SP_SLWebPart#4)]  -->  
  
## Modifier le composant WebPart de Silverlight  
 Modifiez une propriété dans le projet de Silverlight WebPart pour activer le débogage de Silverlight.  
  
#### Pour modifier le composant WebPart Silverlight.  
  
1.  Ouvrez le menu contextuel du projet Silverlight WebPart \(**SLWebPartTest**\) puis choisissez **Propriétés**.  
  
2.  Dans la fenêtre **Propriétés**, choisissez le tableau **SharePoint**.  
  
3.  Si elle ne l'est pas déjà, activez la case à cocher **Activer le débogage Silverlight \(au lieu du débogage de script\)**.  
  
4.  Enregistrez le projet.  
  
##  <a name="BKMK_testSLApp"></a> Test des composants WebPart Silverlight  
 Testez nouveau Silverlight WebPart de SharePoint pour s'assurer qu'il affiche des données de liste SharePoint correctement.  
  
#### Pour tester le composant Silverlight WebPart  
  
1.  Appuyez sur la touche F5 pour générer et exécuter la solution SharePoint.  
  
2.  Dans SharePoint, dans le menu **Les actions de site**, choisissez **Nouvelle page**.  
  
3.  Dans la boîte de dialogue **Nouvelle page**, tapez un titre, par exemple le test de composant WebPart de SL, puis cliquez sur le bouton **Créer**.  
  
4.  Dans le concepteur de page, dans l'onglet de **Outils de modification**, choisissez **Insert**.  
  
5.  Sur le contrôle onglet, sélectionnez **Composant WebPart**.  
  
6.  Dans la zone **Catégories**, choisissez le dossier **Personnalisé**.  
  
7.  Dans la liste **Composants WebPart**, choisissez Silverlight WebPart, puis cliquez sur le bouton **Ajouter** pour ajouter le concepteur WebPart.  
  
8.  Après avoir effectué les ajouts à la page Web souhaitée, choisissez l'onglet de **Page**, puis cliquez sur le bouton **Enregistrer & fermer**  dans la barre d'outils.  
  
     Silverlight WebPart doit désormais afficher les données d'annonce de site SharePoint.  Par défaut, la page est stockée dans la liste des Pages de Site dans SharePoint.  
  
    > [!NOTE]  
    >  Lorsque l'accès aux données dans Silverlight traverse différents domaines, Silverlight se protège contre des failles de sécurité qui peuvent être utilisées pour exploiter les applications Web.  Si vous rencontrez des problèmes lors de l'accès aux données distantes de Silverlight, consultez [En effectuant un service disponible sur les limites de domaine](http://go.microsoft.com/fwlink/?LinkId=223276).  
  
## Voir aussi  
 [Création de composants WebPart pour SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)   
 [Déploiement, publication et mise à niveau de packages de solutions SharePoint](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md)  
  
  