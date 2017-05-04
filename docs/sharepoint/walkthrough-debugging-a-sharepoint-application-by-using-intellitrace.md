---
title: "Proc&#233;dure pas &#224; pas&#160;: d&#233;bogage d&#39;une application SharePoint avec IntelliTrace | Microsoft Docs"
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
  - "IntelliTrace (développement SharePoint dans Visual Studio)"
  - "collecteur de données autonome"
  - "développement SharePoint dans Visual Studio, IntelliTrace"
  - "collecteur de données"
  - "IntelliTrace"
ms.assetid: 4bd80d2f-f680-4bf4-81c3-f14e8185f6a4
caps.latest.revision: 27
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 26
---
# Proc&#233;dure pas &#224; pas&#160;: d&#233;bogage d&#39;une application SharePoint avec IntelliTrace
  En utilisant IntelliTrace, déboguez plus facilement des solutions SharePoint.  Les débogueurs traditionnels vous fournissent uniquement une image instantanée de solution à un moment précis.  Toutefois, vous pouvez utiliser IntelliTrace pour examiner des événements passés qui se sont produits dans votre application et le contexte dans lesquels ils se sont produits. Vous pouvez également naviguer dans le code.  
  
 Cette procédure pas\-à\-pas explique comment déboguer un projet SharePoint 2010 ou SharePoint 2013 dans Visual Studio Ultimate à l'aide de l'agent de surveillance Microsoft pour collecter les données IntelliTrace des applications déployées.  Pour analyser ces données, vous devez utiliser Visual Studio Ultimate.  Ce projet comprend un récepteur de fonctionnalité qui, lorsque la fonctionnalité est activée, ajoute une tâche à la liste Tâches et une annonce à la liste Annonces.  Lorsque la fonctionnalité est désactivée, la tâche est marquée comme terminée, et une deuxième annonce est ajoutée à la liste Annonces.  Toutefois, la procédure contient une erreur logique qui empêche le projet de s'exécuter correctement.  À l'aide d'IntelliTrace, vous trouverez et corrigerez l'erreur.  
  
 **S'applique à :** Les informations contenues dans cette rubrique s'appliquent aux solutions SharePoint 2010 et SharePoint 2013 qui ont été créées dans Visual Studio.  
  
 Cette procédure pas à pas décrit les tâches suivantes :  
  
-   [Créer un récepteur de fonctionnalité](#BKMK_CreateReceiver)  
  
-   [Ajouter le code au récepteur de fonctionnalité](#BKMK_AddCode)  
  
-   [Tester le projet](#BKMK_Test1)  
  
-   [Collecte des données IntelliTrace à l'aide de l'agent de surveillance Microsoft.](#BKMK_CollectDiagnosticData)  
  
-   [Déboguer et corriger la solution SharePoint](#BKMK_DebugSolution)  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Composants requis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   Éditions prises en charge de Windows et SharePoint.  Consultez [Configuration requise pour développer des solutions SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Visual Studio Ultimate.  
  
##  <a name="BKMK_CreateReceiver"></a> Créer un récepteur de fonctionnalité  
 Tout d'abord, créez un projet SharePoint vide qui possède un récepteur de fonctionnalité.  
  
#### Pour créer un récepteur de fonctionnalité  
  
1.  Créez un projet solution SharePoint 2010 ou Sharepoint 2013, et nommez la IntelliTraceTest.  
  
     L' **Assistant Personnalisation de SharePoint** s'affiche, dans lequel vous pouvez spécifier à la fois le site SharePoint pour votre projet et le niveau de confiance de la solution.  
  
2.  Sélectionnez la case d'option **Déployer en tant que solution de batterie**, puis choisissez le bouton **Terminer**.  
  
     IntelliTrace fonctionne uniquement sur les solutions de batterie.  
  
3.  Dans l' **Explorateur de solutions**, ouvrez le menu contextuel du nœud **Fonctionnalités**, puis choisissez **Ajouter une Fonctionnalité**.  
  
     Feature1.feature s'affiche.  
  
4.  Ouvrez le menu contextuel pour Feature1.feature, puis choisissez **Ajouter un récepteur d'événements** pour ajouter un module de code à la fonctionnalité.  
  
##  <a name="BKMK_AddCode"></a> Ajouter le code au récepteur de fonctionnalité  
 Ensuite, ajoutez le code à deux méthodes dans le récepteur de fonctionnalité : `FeatureActivated` et `FeatureDeactivating`.  Ces méthodes se déclenchent à chaque fois qu'une fonctionnalité est activée ou désactivée dans SharePoint, respectivement.  
  
#### Pour ajouter un code au récepteur de fonctionnalité  
  
1.  En haut de la classe `Feature1EventReceiver`, ajoutez le code suivant qui déclare des variables qui spécifient le site et le sous\-site SharePoint :  
  
    ```vb  
    ' SharePoint site and subsite.  
    Private siteUrl As String = "http://localhost"  
    Private webUrl As String = "/"  
    ```  
  
    ```csharp  
    // SharePoint site and subsite.  
    private string siteUrl = "http://localhost";  
    private string webUrl = "/";  
    ```  
  
2.  Remplacez la méthode `FeatureActivated` par le code suivant :  
  
    ```vb  
    Public Overrides Sub FeatureActivated(ByVal properties As SPFeatureReceiverProperties)  
        Try  
            Using site As New SPSite(siteUrl)  
                Using web As SPWeb = site.OpenWeb(webUrl)  
                    ' Reference the lists.  
                    Dim announcementsList As SPList = web.Lists("Announcements")  
                    Dim taskList As SPList = web.Lists("Tasks")  
  
                    ' Add an announcement to the Announcements list.  
                    Dim listItem As SPListItem = announcementsList.Items.Add()  
                    listItem("Title") = "Activated Feature: " & Convert.ToString(properties.Definition.DisplayName)  
                    listItem("Body") = Convert.ToString(properties.Definition.DisplayName) & " was activated on: " & DateTime.Now.ToString()  
                    listItem.Update()  
  
                    ' Add a task to the Task list.  
                    Dim newTask As SPListItem = taskList.Items.Add()  
                    newTask("Title") = "Deactivate feature: " & Convert.ToString(properties.Definition.DisplayName)  
                    newTask.Update()  
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
                    SPList taskList = web.Lists["Tasks"];  
  
                    // Add an announcement to the Announcements list.  
                    SPListItem listItem = announcementsList.Items.Add();  
                    listItem["Title"] = "Activated Feature: " + properties.Definition.DisplayName;  
                    listItem["Body"] = properties.Definition.DisplayName + " was activated on: " + DateTime.Now.ToString();  
                    listItem.Update();  
  
                    // Add a task to the Task list.  
                    SPListItem newTask = taskList.Items.Add();  
                    newTask["Title"] = "Deactivate feature: " + properties.Definition.DisplayName;  
                    newTask.Update();  
                }  
            }  
        }  
  
        catch (Exception e)  
        {  
            Console.WriteLine("Error: " + e.ToString());  
        }  
  
    }  
    ```  
  
3.  Remplacez la méthode `FeatureDeactivating` par le code suivant :  
  
    ```vb  
    Public Overrides Sub FeatureDeactivating(ByVal properties As SPFeatureReceiverProperties)  
        ' The following line induces an error to demonstrate debugging.  
        ' Remove this line later for proper operation.  
        Throw New System.InvalidOperationException("Serious error occurred!")  
        Try  
            Using site As New SPSite(siteUrl)  
                Using web As SPWeb = site.OpenWeb(webUrl)  
                    ' Reference the lists.  
                    Dim taskList As SPList = web.Lists("Tasks")  
                    Dim announcementsList As SPList = web.Lists("Announcements")  
  
                    ' Add an announcement that the feature was deactivated.  
                    Dim listItem As SPListItem = announcementsList.Items.Add()  
                    listItem("Title") = "Deactivated Feature: " & Convert.ToString(properties.Definition.DisplayName)  
                    listItem("Body") = Convert.ToString(properties.Definition.DisplayName) & " was deactivated on: " & DateTime.Now.ToString()  
                    listItem.Update()  
  
                    ' Find the task that the feature receiver added to the Task list when the  
                    ' feature was activated.  
                    Dim qry As New SPQuery()  
                    qry.Query = "<Where><Contains><FieldRef Name='Title' /><Value Type='Text'>Deactivate</Value></Contains></Where>"  
                    Dim taskItems As SPListItemCollection = taskList.GetItems(qry)  
  
                    For Each taskItem As SPListItem In taskItems  
                        ' Mark the task as complete.  
                        taskItem("PercentComplete") = 1  
                        taskItem("Status") = "Completed"  
                        taskItem.Update()  
                    Next  
                End Using  
  
            End Using  
  
        Catch e As Exception  
            Console.WriteLine("Error: " & e.ToString())  
        End Try  
  
    End Sub  
    ```  
  
    ```csharp  
    public override void FeatureDeactivating(SPFeatureReceiverProperties properties)  
    {  
        // The following line induces an error to demonstrate debugging.  
        // Remove this line later for proper operation.  
        throw new System.InvalidOperationException("A serious error occurred!");   
        try  
        {  
            using (SPSite site = new SPSite(siteUrl))  
            {  
                using (SPWeb web = site.OpenWeb(webUrl))  
                {  
                    // Reference the lists.  
                    SPList taskList = web.Lists["Tasks"];  
                    SPList announcementsList = web.Lists["Announcements"];  
  
                    // Add an announcement that the feature was deactivated.  
                    SPListItem listItem = announcementsList.Items.Add();  
                    listItem["Title"] = "Deactivated Feature: " + properties.Definition.DisplayName;  
                    listItem["Body"] = properties.Definition.DisplayName + " was deactivated on: " + DateTime.Now.ToString();  
                    listItem.Update();  
  
                    // Find the task that the feature receiver added to the Task list when the  
                    // feature was activated.  
                    SPQuery qry = new SPQuery();  
                    qry.Query = "<Where><Contains><FieldRef Name='Title' /><Value Type='Text'>Deactivate</Value></Contains></Where>";  
                    SPListItemCollection taskItems = taskList.GetItems(qry);  
  
                    foreach (SPListItem taskItem in taskItems)  
                    {  
                        // Mark the task as complete.  
                        taskItem["PercentComplete"] = 1;  
                        taskItem["Status"] = "Completed";  
                        taskItem.Update();  
                    }  
                }  
            }  
  
        }  
  
        catch (Exception e)  
        {  
            Console.WriteLine("Error: " + e.ToString());  
        }  
    }  
    ```  
  
##  <a name="BKMK_Test1"></a> Tester le projet  
 Maintenant que le code est ajouté au récepteur de fonctionnalité et que le collecteur de données s'exécute, déployez et exécutez la solution SharePoint pour vérifier qu'elle fonctionne correctement.  
  
> [!IMPORTANT]  
>  Pour cet exemple, une erreur est levée dans le gestionnaire d'événements FeatureDeactivating.  À une étape ultérieure de cette procédure, vous localisez cette erreur en utilisant le fichier .iTrace que le collecteur de données a créé.  
  
#### Pour tester le projet  
  
1.  Déployez la solution dans SharePoint, puis ouvrez le site SharePoint dans un navigateur.  
  
     La fonctionnalité s'active automatiquement, ce qui entraîne l'ajout d'une annonce et d'une tâche par son récepteur de fonctionnalité.  
  
2.  Affichez le contenu des listes d'annonce et de tâches.  
  
     La liste d'Annonces devrait avoir une nouvelle annonce nommée **Fonctionnalité activée : IntelliTraceTest\_Feature1**, et la liste des tâches devrait avoir une nouvelle tâche nommée **Deactivate feature: IntelliTraceTest\_Feature1**.  Si l'un de ces éléments est manquant, vérifiez si la fonctionnalité est activée.  Si elle n'est pas activée, activez là.  
  
3.  Désactivez la fonctionnalité en procédant comme suit :  
  
    1.  Dans SharePoint, dans le menu **Actions du site**, cliquez sur **Paramètres du site**.  
  
    2.  Dans **Actions du site**, choisissez le lien **Gérer les fonctionnalités du site**.  
  
    3.  A côté de **IntelliTraceTest Feature1**, cliquez sur le bouton **Désactiver**.  
  
    4.  Sur la page d'Avertissement, choisissez le lien **Désactiver la fonctionnalité**.  
  
     Le gestionnaire d'événements FeatureDeactivating\(\) génère une erreur.  
  
##  <a name="BKMK_CollectDiagnosticData"></a> Collecte des données IntelliTrace à l'aide de l'agent de surveillance Microsoft.  
 Si vous installez l'agent de surveillance Microsoft sur le système qui exécute SharePoint, vous pouvez déboguer des solutions SharePoint à l'aide des données qui sont plus spécifiques que les informations génériques retournées par IntelliTrace.  L'agent travaille en dehors de Visual Studio à l'aide des cmdlets de PowerShell pour capturer des informations de débogage pendant que votre solution SharePoint s'exécute.  
  
> [!NOTE]  
>  Les données de configuration de cette section sont spécifiques à cet exemple.  Pour plus d'informations sur d'autres options de configuration, consultez [Utilisation du collecteur autonome IntelliTrace](../debugger/using-the-intellitrace-stand-alone-collector.md).  
  
1.  Sur l'ordinateur qui exécute SharePoint, [installez l'agent de surveillance Microsoft et démarrez la surveillance de votre solution](../debugger/using-the-intellitrace-stand-alone-collector.md).  
  
2.  Désactivez la fonctionnalité :  
  
    1.  Dans SharePoint, dans le menu **Actions du site**, cliquez sur **Paramètres du site**.  
  
    2.  Dans **Actions du site**, choisissez le lien **Gérer les fonctionnalités du site**.  
  
    3.  A côté de **IntelliTraceTest Feature1**, cliquez sur le bouton **Désactiver**.  
  
    4.  Sur la page d'Avertissement, choisissez le lien **Désactiver la fonctionnalité**.  
  
     Une erreur se produit \(dans ce cas, à cause de l'erreur levée dans le gestionnaire d'événements FeatureDeactivating\(\) \).  
  
3.  Dans la fenêtre de PowerShell, exécutez la commande [Stop\-WebApplicationMonitoring](http://go.microsoft.com/fwlink/?LinkID=313687) afin de créer le fichier .iTrace, arrêtez la surveillance, et redémarrez votre solution SharePoint.  
  
     **Stop\-WebApplicationMonitoring**  *"\<SharePointSite\>\\\<SharePointAppName\>"*  
  
##  <a name="BKMK_DebugSolution"></a> Déboguer et corriger la solution SharePoint  
 Maintenant, affichez le fichier journal d'IntelliTrace dans Visual Studio pour rechercher et corriger l'erreur dans la solution SharePoint.  
  
#### Pour déboguer et corriger la solution SharePoint  
  
1.  Depuis le dossier \\d'IntelliTraceLogs, ouvrez le fichier .iTrace dans Visual Studio.  
  
     La page **Résumé IntelliTrace** s'affiche.  Étant donné que l'erreur n'a pas été gérée, un ID de corrélation SharePoint \(un GUID\) apparaît dans la zone d'exception non gérée de la section **Analyse**.  Cliquez sur le bouton **Pile des appels** si vous souhaitez afficher la pile des appels où l'erreur s'est produite.  
  
2.  Cliquez sur le bouton **Exception de débogage**.  
  
     Si vous y êtes invité, chargez les fichiers de symboles.  Dans la fenêtre **IntelliTrace**, l'exception est mise en surbrillance comme « levée : Erreur sérieuse produite \! ».  
  
     Dans la fenêtre IntelliTrace, choisissez l'exception pour afficher le code qui a échoué.  
  
3.  Corrigez l'erreur en ouvrant la solution SharePoint puis en commentant ou en supprimant le relevé **throw** en haut de la procédure FeatureDeactivating\(\).  
  
4.  Régénérez la solution dans Visual Studio, puis redéployez la vers SharePoint.  
  
5.  Désactivez la fonctionnalité en procédant comme suit :  
  
    1.  Dans SharePoint, dans le menu **Actions du site**, cliquez sur **Paramètres du site**.  
  
    2.  Dans **Actions du site**, choisissez le lien **Gérer les fonctionnalités du site**.  
  
    3.  A côté de **IntelliTraceTest Feature1**, cliquez sur le bouton **Désactiver**.  
  
    4.  Sur la page d'Avertissement, choisissez le lien **Désactiver la fonctionnalité**.  
  
6.  Ouvrez la liste Tâche et vérifiez que la valeur **État** de la tâche Deactivate est maintenant définie correctement sur « Terminé » et que sa valeur **% achevé** est 100 %.  
  
     Le code fonctionne maintenant correctement.  
  
## Voir aussi  
 [Vérification et débogage du code SharePoint](../sharepoint/verifying-and-debugging-sharepoint-code.md)   
 [Utilisation d'IntelliTrace](../debugger/intellitrace.md)   
 [Procédure pas à pas : Vérifier le code SharePoint à l'aide de tests unitaires](http://msdn.microsoft.com/fr-fr/3d2c4aaf-3cb5-4825-b21b-f10222abe818)  
  
  