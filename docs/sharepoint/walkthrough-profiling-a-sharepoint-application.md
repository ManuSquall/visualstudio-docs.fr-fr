---
title: 'Procédure pas à pas : Profilage d’une Application SharePoint | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, profiling
- performance testing [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, performance testing
- profiling [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: d235508bb0b58ac17846d0b02db25f044c504deb
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42634704"
---
# <a name="walkthrough-profile-a-sharepoint-application"></a>Procédure pas à pas : Profiler une application SharePoint
  Cette procédure pas à pas montre comment utiliser les outils de profilage dans Visual Studio pour optimiser les performances d'une application SharePoint. L’application d’exemple est un récepteur d’événements de fonctionnalité SharePoint qui contient une boucle inactive qui dégrade les performances du récepteur d’événements de fonctionnalité. Le profileur Visual Studio vous permet de définir et supprimer la partie la plus coûteuse (exécution la plus lente) du projet, également connu sous le *chemin réactif*.  
  
 Cette procédure pas à pas décrit les tâches suivantes :  
  
-   [Ajout d’une fonctionnalité et un récepteur d’événements de fonctionnalité](#BKMK_AddFtrandFtrEvntReceiver).  
  
-   [Configuration et déploiement de l’Application SharePoint](#BKMK_ConfigSharePointApp).  
  
-   [Exécution de l’Application SharePoint](#BKMK_RunSPApp).  
  
-   [Affichage et interprétation des résultats de profilage](#BKMK_ViewResults).  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Prérequis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   Éditions prises en charge de Microsoft Windows et SharePoint.
  
-   [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)].  
  
## <a name="create-a-sharepoint-project"></a>Créer un projet SharePoint
 Commencez par créer un projet SharePoint.  
  
#### <a name="to-create-a-sharepoint-project"></a>Pour créer un projet SharePoint  
  
1.  Dans la barre de menus, choisissez **fichier** > **New** > **projet** pour afficher le **nouveau projet** boîte de dialogue.  
  
2.  Développez le **SharePoint** nœud sous **Visual C#** ou **Visual Basic**, puis choisissez le **2010** nœud.  
  
3.  Dans le volet Modèles, choisissez le **projet SharePoint 2010** modèle.  
  
4.  Dans le **nom** , entrez **ProfileTest**, puis choisissez le **OK** bouton.  
  
     Le **Assistant Personnalisation de SharePoint** s’affiche.  
  
5.  Sur le **spécifier le niveau de site et de sécurité pour le débogage** page, entrez l’URL pour le site du serveur SharePoint où vous souhaitez déboguer la définition de site ou utilisez l’emplacement par défaut (http://*nom système*/) .  
  
6.  Dans le **quel est le niveau de confiance de cette solution SharePoint ?** , choisissez le **déployer en tant que solution de batterie** case d’option.  
  
     Actuellement, vous ne pouvez profiler que des solutions de batterie. Pour plus d’informations sur les solutions bac à sable par rapport aux solutions de batterie de serveurs, consultez [considérations relatives à la solution bac à sable](../sharepoint/sandboxed-solution-considerations.md).  
  
7.  Choisissez le **Terminer** bouton. Le projet s’affiche dans **l’Explorateur de solutions**.  
  
## <a name="add-a-feature-and-feature-event-receiver"></a>Ajouter une fonctionnalité et un récepteur d’événements de fonctionnalité
 Ensuite, ajoutez une fonctionnalité au projet avec un récepteur d’événements pour la fonctionnalité. Ce récepteur d'événements contiendra le code à profiler.  
  
#### <a name="to-add-a-feature-and-feature-event-receiver"></a>Pour ajouter une fonctionnalité et un récepteur d’événements de fonctionnalité  
  
1.  Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour le **fonctionnalités** nœud, choisissez **ajouter une fonctionnalité**et conservez la valeur par défaut, le nom **Feature1**.  
  
2.  Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour **Feature1**, puis choisissez **ajouter un récepteur d’événements**.  
  
     Cela ajoute un fichier de code à la fonctionnalité avec plusieurs gestionnaires d’événements commentés et ouvre le fichier à modifier.  
  
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
  
4.  Remplacez la procédure `FeatureActivated` par le code ci-dessous.  
  
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
  
5.  Ajoutez la procédure suivante ci-dessous le `FeatureActivated`procédure.  
  
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
  
6.  Dans **l’Explorateur de solutions**, ouvrez le menu contextuel du projet (**ProfileTest**), puis choisissez **propriétés**.  
  
7.  Dans le **propriétés** boîte de dialogue, sélectionnez le **SharePoint** onglet.  
  
8.  Dans le **Configuration de déploiement Active** , choisissez **aucune Activation**.  
  
     Sélectionner cette configuration de déploiement vous permet d’activer manuellement la fonctionnalité ultérieurement dans SharePoint.  
  
9. Enregistrez le projet.  
  
## <a name="configure-and-deploy-the-sharepoint-application"></a>Configurer et déployer l’application SharePoint
 Maintenant que le projet SharePoint est prêt, configurez-le et déployez-le sur le serveur SharePoint.  
  
#### <a name="to-configure-and-deploy-the-sharepoint-application"></a>Pour configurer et déployer l'application SharePoint  
  
1.  Sur le **analyser** menu, choisissez **lancer l’Assistant Performance**.  
  
2.  Dans la première page de la **Assistant Performance**, laissez la méthode de profilage en tant que **échantillonnage de l’UC** et choisissez le **suivant** bouton.  
  
     Les autres méthodes de profilage peuvent être utilisées dans des situations plus avancées de profilage. Pour plus d’informations, consultez [Understanding Performance Collection Methods](/visualstudio/profiling/understanding-performance-collection-methods) (Fonctionnement des méthodes de collecte des données de performances).  
  
3.  Dans la page deux de la **Assistant Performance**, laisser la cible de profil en tant que **ProfileTest** et choisissez le **suivant** bouton.  
  
     Si une solution comporte plusieurs projets, ils apparaissent dans cette liste.  
  
4.  Dans la troisième page de le **Assistant Performance**, désactivez le **activer le profilage d’Interaction de couche** case à cocher, puis choisissez le **suivant** bouton.  
  
     La fonctionnalité de profilage d’interaction de couche (TIP) est utile pour mesurer les performances des applications qui interrogent les bases de données et vous indiquer le nombre de fois qu’une page web est demandée. Étant donné que ces données ne sont pas requises pour cet exemple, nous n’activerons pas cette fonctionnalité.  
  
5.  Dans la quatrième page de la **Assistant Performance**, laissez le **lancer le profilage une fois l’Assistant terminé** case à cocher, puis choisissez le **Terminer** bouton.  
  
     L’Assistant permet le profilage de l’application sur le serveur, affiche le **Explorateur de performances** fenêtre, puis génère, déploie et exécute l’application SharePoint.  
  
## <a name="run-the-sharepoint-application"></a>Exécutez l’application SharePoint
 Activez la fonctionnalité dans SharePoint, déclenchant le code d'événement `FeatureActivation` à exécuter.  
  
#### <a name="to-run-the-sharepoint-application"></a>Pour exécuter l'application SharePoint  
  
1.  Dans SharePoint, ouvrez le **Actions du Site** menu, puis choisissez **paramètres du Site**.  
  
2.  Dans le **Actions du Site** , choisissez le **gérer les fonctionnalités du site** lien.  
  
3.  Dans le **fonctionnalités** , choisissez le **activer** situé en regard **ProfileTest Feature1**.  
  
     Ce faisant, une pause survient en raison de la boucle inactive appelée dans la fonction `FeatureActivated`.  
  
4.  Sur le **lancement rapide** barre, choisissez **répertorie** puis, dans le **répertorie** , choisissez **annonces**.  
  
     Notez qu’une nouvelle annonce a été ajoutée à la liste indiquant que la fonctionnalité a été activée.  
  
5.  Fermez le site SharePoint.  
  
     Après avoir fermé SharePoint, le profileur crée et affiche un exemple de rapport de profilage et l’enregistre dans un fichier .vsp dans le **ProfileTest** dossier du projet.  
  
## <a name="view-and-interpret-the-profile-results"></a>Afficher et interpréter les résultats du profil
 Maintenant que vous avez exécuté et profilé l'application SharePoint, affichez les résultats des tests.  
  
#### <a name="to-view-and-interpret-the-profile-results"></a>Pour afficher et interpréter les résultats du profil
  
1.  Dans le **fonctions faisant le plus de travail individuel** section de l’exemple de profilage de rapport, notez que `TimeCounter` est près du haut de la liste.  
  
     Cet emplacement indique que `TimeCounter` est l'une des fonctions présentant le plus grand nombre d'exemples ; autrement dit, il s'agit de l'un des plus importants goulots d'étranglement de performance de l'application. Toutefois, cette situation n'est pas étonnante, parce qu'elle a expressément été conçue à des fins de démonstration.  
  
2.  Dans le **fonctions faisant le plus de travail individuel** , choisissez le `ProcessRequest` lien pour afficher la distribution des coûts pour le `ProcessRequest` (fonction).  
  
     Dans le **appelées fonctions** section pour `ProcessRequest`, notez que le **FeatureActivated** fonction est répertoriée comme étant les plus coûteux fonction appelée.  
  
3.  Dans le **appelées fonctions** , choisissez le **FeatureActivated** bouton.  
  
     Dans le **appelées fonctions** section pour **FeatureActivated**, le `TimeCounter` fonction est répertoriée comme étant les plus coûteux fonction appelée. Dans le **affichage du Code de fonction** volet, le code en surbrillance (`TimeCounter`) est la zone réactive et indique où la correction est nécessaire.  
  
4.  Fermez le rapport de profilage de l'échantillon.  
  
     Pour afficher le rapport à tout moment, ouvrez le fichier .vsp dans le **Explorateur de performances** fenêtre.  
  
## <a name="fix-the-code-and-reprofile-the-application"></a>Corriger le code et reprofiler l’application
 Maintenant que la fonction de la zone réactive de l'application SharePoint a été identifiée, corrigez-la.  
  
#### <a name="to-fix-the-code-and-reprofile-the-application"></a>Pour corriger le code et reprofiler l'application  
  
1.  Dans le code du récepteur d'événements de fonctionnalité, commentez l'appel de méthode `TimeCounter` dans `FeatureActivated` pour empêcher tout appel.  
  
2.  Enregistrez le projet.  
  
3.  Dans **Explorateur de performances**, ouvrez le dossier cibles, puis choisissez le **ProfileTest** nœud.  
  
4.  Sur le **Explorateur de performances** barre d’outils, dans le **Actions** , choisir le **démarrer le profilage** bouton.  
  
     Si vous souhaitez modifier les propriétés de profilage avant de reprofiler l’application, choisissez le **lancer l’Assistant Performance** bouton à la place.  
  
5.  Suivez les instructions de la **l’Application SharePoint en cours d’exécution** section précédemment dans cette rubrique.  
  
     Comme l’appel à la boucle inactive a été supprimé, la fonctionnalité doit s’activer beaucoup plus rapidement. Le rapport de profilage d'échantillon doit le refléter.  
  
## <a name="see-also"></a>Voir aussi
 [Explorateur de performances](/visualstudio/profiling/performance-explorer)   
 [Vue d’ensemble des sessions de performance](/visualstudio/profiling/performance-session-overview)   
 [Guide du débutant en profilage des performances](/visualstudio/profiling/beginners-guide-to-performance-profiling)   
 [Trouver les goulots d’étranglement de l’Application avec Visual Studio Profiler](http://go.microsoft.com/fwlink/?LinkID=137266)  
  
