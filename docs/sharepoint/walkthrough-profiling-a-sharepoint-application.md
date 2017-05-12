---
title: "Walkthrough: Profiling a SharePoint Application"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "SharePoint development in Visual Studio, profiling"
  - "performance testing [SharePoint development in Visual Studio]"
  - "SharePoint development in Visual Studio, performance testing"
  - "profiling [SharePoint development in Visual Studio]"
ms.assetid: 0b19d4b7-5fcc-42a2-b411-96eccd00137f
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 15
---
# Walkthrough: Profiling a SharePoint Application
  Cette procédure pas à pas montre comment utiliser les outils de profilage dans Visual Studio pour optimiser les performances d'une application SharePoint.  L'application d'exemple est un récepteur d'événements de fonctionnalité SharePoint qui contient une boucle inactive qui dégrade les performances du récepteur d'événements de fonctionnalité.  Le profileur Visual Studio vous permet de définir et supprimer la partie la plus coûteuse \(exécution la plus lente\) du projet, également appelée *chemin réactif*.  
  
 Cette procédure pas à pas décrit les tâches suivantes :  
  
-   [Ajout d'une fonctionnalité et d'un récepteur d'événements de fonctionnalité](#BKMK_AddFtrandFtrEvntReceiver).  
  
-   [Configuration et déploiement de l'application SharePoint](#BKMK_ConfigSharePointApp).  
  
-   [Exécution de l'application SharePoint](#BKMK_RunSPApp).  
  
-   [Affichage et interprétation des résultats de profilage](#BKMK_ViewResults).  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Composants requis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   Éditions prises en charge de Microsoft Windows et SharePoint.  [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)] [Configuration requise pour développer des solutions SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)].  
  
## Création d'un projet SharePoint  
 Commencez par créer un projet SharePoint.  
  
#### Pour créer un projet SharePoint  
  
1.  Dans la barre de menus, sélectionnez **Fichier**, **Nouveau**, **Projet** pour afficher la boîte de dialogue **Nouveau projet**.  
  
2.  Développez le nœud **SharePoint** sous **Visual C\#** ou **Visual Basic**, puis sélectionnez le nœud **2010**.  
  
3.  Dans le volet Modèles, sélectionnez le modèle **Projet SharePoint 2010**.  
  
4.  Dans la zone **Nom**, entrez ProfileTest, puis choisissez le bouton **OK**.  
  
     L'**Assistant Personnalisation de SharePoint** apparaît.  
  
5.  Dans la page **Spécifier le site et le niveau de sécurité pour le débogage**, entrez l'URL du site du serveur SharePoint où vous souhaitez déboguer la définition de site, ou utilisez l'emplacement par défaut \(http:\/\/*nom système*\/\).  
  
6.  Dans la section **Quel est le niveau de confiance de cette solution SharePoint ?**, choisissez la case d'option **Déployer en tant que solution de batterie**.  
  
     Actuellement, vous ne pouvez profiler que des solutions de batterie.  Pour plus d'informations sur les solutions bac à sable \(sandbox\) par rapport aux solutions de batterie, consultez [Considérations sur les solutions bac à sable &#40;sandbox&#41;](../sharepoint/sandboxed-solution-considerations.md).  
  
7.  Choisissez le bouton **Terminer**.  Le projet apparaît dans l'**Explorateur de solutions**.  
  
##  <a name="BKMK_AddFtrandFtrEvntReceiver"></a> Ajout d'une fonctionnalité et d'un récepteur d'événements de fonctionnalité  
 Ensuite, ajoutez une fonctionnalité au projet avec un récepteur d'événements pour la fonctionnalité.  Ce récepteur d'événements contiendra le code à profiler.  
  
#### Pour ajouter une fonctionnalité et un récepteur d'événements de fonctionnalité  
  
1.  Dans l'**Explorateur de solutions**, ouvrez le menu contextuel du nœud **Fonctionnalités**, choisissez **Ajouter une fonctionnalité**, et conservez le nom par défaut, **Feature1**.  
  
2.  Dans l'**Explorateur de solutions**, ouvrez le menu contextuel pour **Feature1**, puis choisissez **Ajouter un récepteur d'événements**.  
  
     Cela ajoute un fichier de code à la fonctionnalité avec plusieurs gestionnaires d'événements commentés et ouvre le fichier à modifier.  
  
3.  Dans la classe de récepteur d'évènements, ajoutez les déclarations de variables suivantes.  
  
    ```vb  
    ' SharePoint site/subsite.  
    Private siteUrl As String = "http://localhost"  
    Private webUrl As String = "/"  
    ```  
  
    ```csharp  
    // SharePoint site/subsite.  
    private string siteUrl = "http://localhost";  
    private string webUrl = "/";  
    ```  
  
4.  Remplacez la procédure `FeatureActivated` par le code ci\-dessous.  
  
    ```vb  
    Public Overrides Sub FeatureActivated(properties As SPFeatureReceiverProperties)  
        Try  
            Using site As New SPSite(siteUrl)  
                Using web As SPWeb = site.OpenWeb(webUrl)  
                    ' Reference the lists.  
                    Dim announcementsList As SPList = web.Lists("Announcements")  
  
                    ' Add a new announcement to the Announcements list.  
                    Dim listItem As SPListItem = announcementsList.Items.Add()  
                    listItem("Title") = "Activated Feature: " & Convert.ToString(properties.Definition.DisplayName)  
                    listItem("Body") = Convert.ToString(properties.Definition.DisplayName) & " was activated on: " & DateTime.Now.ToString()  
                    ' Waste some time.  
                    TimeCounter()  
                    ' Update the list.  
                    listItem.Update()  
                End Using  
            End Using  
  
        Catch e As Exception  
            Console.WriteLine("Error: " & e.ToString())  
        End Try  
    End Sub  
    ```  
  
    ```csharp  
    public override void FeatureActivated(SPFeatureReceiverProperties properties)  
    {  
        try  
        {  
            using (SPSite site = new SPSite(siteUrl))  
            {  
                using (SPWeb web = site.OpenWeb(webUrl))  
                {  
                    // Reference the lists.  
                    SPList announcementsList = web.Lists["Announcements"];  
  
                    // Add a new announcement to the Announcements list.  
                    SPListItem listItem = announcementsList.Items.Add();  
                    listItem["Title"] = "Activated Feature: " + properties.Definition.DisplayName;  
                    listItem["Body"] = properties.Definition.DisplayName + " was activated on: " +   
    DateTime.Now.ToString();  
                    // Waste some time.  
                    TimeCounter();  
                    // Update the list.  
                    listItem.Update();                          
                }  
            }  
        }  
  
        catch (Exception e)  
        {  
            Console.WriteLine("Error: " + e.ToString());  
        }  
    }  
    ```  
  
5.  Ajoutez la procédure suivante sous la procédure `FeatureActivated`.  
  
    ```vb  
  
    Public Sub TimeCounter()  
        Dim result As Integer  
        For i As Integer = 0 To 99999  
            For j As Integer = 0 To 9999  
                result = i * j  
            Next j  
        Next i  
    End Sub  
    ```  
  
    ```csharp  
    public void TimeCounter()  
    {  
        for (int i = 0; i < 100000; i++)  
        {  
            for (int j = 0; j < 10000; j++)  
            {  
                int result = i * j;  
            }  
        }  
    }  
    ```  
  
6.  Dans l'**Explorateur de solutions**, ouvrez le menu contextuel du projet \(**ProfileTest**\), puis choisissez **Propriétés**.  
  
7.  Dans la boîte de dialogue **Propriétés**, choisissez l'onglet **SharePoint**.  
  
8.  Dans la liste **Configuration de déploiement active**, choisissez **Aucune activation**.  
  
     Sélectionner cette configuration de déploiement vous permet d'activer manuellement la fonctionnalité ultérieurement dans SharePoint.  
  
9. Enregistrez le projet.  
  
##  <a name="BKMK_ConfigSharePointApp"></a> Configuration et déploiement de l'application SharePoint  
 Maintenant que le projet SharePoint est prêt, configurez\-le et déployez\-le sur le serveur SharePoint.  
  
#### Pour configurer et déployer l'application SharePoint  
  
1.  Dans le menu **Analyser**, choisissez **Lancer l'Assistant Performance**.  
  
2.  Dans la première page de l'**Assistant Performance**, laissez la méthode de profilage sur **Échantillonnage de l'UC** et cliquez sur le bouton **Suivant**.  
  
     Les autres méthodes de profilage peuvent être utilisées dans des situations plus avancées de profilage.  Pour plus d'informations, consultez [Fonctionnement des méthodes de profilage](../profiling/understanding-performance-collection-methods.md).  
  
3.  Dans la deuxième page de l'**Assistant Performance**, laissez la cible de profil sur **ProfileTest** et cliquez sur le bouton **Suivant**.  
  
     Si une solution comporte plusieurs projets, ils apparaissent dans cette liste.  
  
4.  Dans la troisième page de l'**Assistant Performance**, désactivez la case à cocher **Activer le profilage d'interaction de couche**, puis cliquez sur le bouton **Suivant**.  
  
     La fonctionnalité de profilage d'interaction de couche \(TIP\) est utile pour mesurer les performances des applications qui interrogent les bases de données et vous indiquer le nombre de fois qu'une page Web est demandée.  Étant donné que ces données ne sont pas requises pour cet exemple, nous n'activerons pas cette fonctionnalité.  
  
5.  Dans la quatrième page de l'**Assistant Performance**, veillez à ce que la case **Lancer le profilage une fois l'Assistant terminé** reste cochée, puis cliquez sur le bouton **Terminer**.  
  
     L'Assistant active le profilage de l'application sur le serveur, affiche la fenêtre **Explorateur de performances**, puis génère, déploie et exécute l'application SharePoint.  
  
##  <a name="BKMK_RunSPApp"></a> Exécution de l'application SharePoint  
 Activez la fonctionnalité dans SharePoint, déclenchant le code d'événement `FeatureActivation` à exécuter.  
  
#### Pour exécuter l'application SharePoint  
  
1.  Dans SharePoint, ouvrez le menu **Actions du site**, puis sélectionnez **Paramètres du site**.  
  
2.  Dans la liste **Actions du site**, sélectionnez le lien **Gérer les fonctionnalités du site**.  
  
3.  Dans la liste **Fonctionnalités**, cliquez sur le bouton **Activer** à côté de **ProfileTest Feature1**.  
  
     Ce faisant, une pause survient en raison de la boucle inactive appelée dans la fonction `FeatureActivated`.  
  
4.  Dans la barre **Lancement rapide**, choisissez **Listes**, puis dans la liste **Listes**, choisissez **Annonces**.  
  
     Notez qu'une nouvelle annonce a été ajoutée à la liste indiquant que la fonctionnalité a été activée.  
  
5.  Fermez le site SharePoint.  
  
     Après avoir fermé SharePoint, le profileur crée et affiche un rapport de profilage d'échantillon et l'enregistre en tant que fichier .vsp dans le dossier du projet **ProfileTest**.  
  
##  <a name="BKMK_ViewResults"></a> Affichage et interprétation des résultats de profilage  
 Maintenant que vous avez exécuté et profilé l'application SharePoint, affichez les résultats des tests.  
  
#### Pour afficher et interpréter les résultats de profilage  
  
1.  Dans la section **Fonctions faisant le plus de travail individuel** du rapport de profilage d'échantillon, notez que `TimeCounter` figure en haut de la liste.  
  
     Cet emplacement indique que `TimeCounter` est l'une des fonctions présentant le plus grand nombre d'exemples ; autrement dit, il s'agit de l'un des plus importants goulots d'étranglement de performance de l'application.  Toutefois, cette situation n'est pas étonnante, parce qu'elle a expressément été conçue à des fins de démonstration.  
  
2.  Dans la section **Fonctions faisant le plus de travail individuel**, sélectionnez le lien `ProcessRequest` pour afficher la distribution des coûts de la fonction `ProcessRequest`.  
  
     Dans la section **Fonctions appelées** pour `ProcessRequest`, notez que la fonction **FeatureActiviated** est répertoriée comme la fonction appelée la plus coûteuse.  
  
3.  Dans la section **Fonctions appelées**, cliquez sur le bouton **FeatureActivated**.  
  
     Dans la section **Fonctions appelées** pour **FeatureActivated**, la fonction `TimeCounter` est répertoriée comme la fonction appelée la plus coûteuse.  Dans la section **Affichage du code de fonction**, le code en surbrillance \(`TimeCounter`\) est la zone réactive et indique où la correction est nécessaire.  
  
4.  Fermez le rapport de profilage de l'échantillon.  
  
     Pour afficher à nouveau le rapport à tout moment, ouvrez le fichier .vsp dans la fenêtre **Explorateur de performances**.  
  
## Correction du code et reprofilage de l'application  
 Maintenant que la fonction de la zone réactive de l'application SharePoint a été identifiée, corrigez\-la.  
  
#### Pour corriger le code et reprofiler l'application  
  
1.  Dans le code du récepteur d'événements de fonctionnalité, commentez l'appel de méthode `TimeCounter` dans `FeatureActivated` pour empêcher tout appel.  
  
2.  Enregistrez le projet.  
  
3.  Dans l'**Explorateur de performances**, ouvrez le dossier Cibles, puis sélectionnez le nœud **ProfileTest**.  
  
4.  Dans la barre d'outils **Explorateur de performances**, dans l'onglet **Actions**, cliquez sur le bouton **Démarrer le profilage**.  
  
     Si vous souhaitez modifier les propriétés de profilage avant de reprofiler l'application, cliquez plutôt sur le bouton **Lancer l'Assistant Performance**.  
  
5.  Suivez les instructions dans la section **Exécution de l'application SharePoint**, plus haut dans cette rubrique.  
  
     Comme l'appel à la boucle inactive a été supprimé, la fonctionnalité doit s'activer beaucoup plus rapidement.  Le rapport de profilage d'échantillon doit le refléter.  
  
## Voir aussi  
 [Utilisation des outils de profilage](../profiling/performance-explorer.md)   
 [Vue d’ensemble de la session de performance des outils de profilage](../profiling/performance-session-overview.md)   
 [Guide du débutant en profilage des performances](../profiling/beginners-guide-to-performance-profiling.md)   
 [Repérez les goulots d'étranglement d'application avec le profileur Visual Studio](http://go.microsoft.com/fwlink/?LinkID=137266)  
  
  