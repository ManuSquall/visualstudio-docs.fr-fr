---
title: 'Procédure pas à pas : Débogage d’une Application SharePoint à l’aide d’IntelliTrace | Documents Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- IntelliTrace [SharePoint development in Visual Studio]
- standalone data collector
- SharePoint development in Visual Studio, IntelliTrace
- data collector
- IntelliTrace
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 173dbc74a24166f69ca97da6d5f68332345b90ea
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-debugging-a-sharepoint-application-by-using-intellitrace"></a>Procédure pas à pas : débogage d'une application SharePoint avec IntelliTrace

Grâce à IntelliTrace, vous pouvez déboguer plus facilement des solutions SharePoint. Les débogueurs classiques vous permettent uniquement d’un instantané d’une solution au moment actuel. Toutefois, vous pouvez utiliser IntelliTrace pour examiner les événements passés qui s’est produite dans votre solution et le contexte dans lequel ils s’est produite et accéder au code.

 Cette procédure pas à pas montre comment déboguer un projet SharePoint 2010 ou SharePoint 2013 dans Visual Studio à l’aide de Microsoft Monitoring Agent pour collecter des données IntelliTrace à partir des applications déployées. Pour analyser ces données, vous devez utiliser Visual Studio Enterprise. Ce projet comprend un récepteur de fonctionnalité qui, lorsque la fonctionnalité est activée, ajoute une tâche à la liste des tâches et une annonce à la liste d’annonces. Lorsque la fonctionnalité est désactivée, la tâche est marquée comme terminée, et une deuxième annonce est ajoutée à la liste d’annonces. Toutefois, la procédure contient une erreur de logique qui empêche le projet de s’exécuter correctement. Grâce à IntelliTrace, vous devez localiser et corriger l’erreur.

 **S’applique à :** les informations contenues dans cette rubrique s’applique aux solutions SharePoint 2010 et SharePoint 2013 qui ont été créées dans Visual Studio.

 Cette procédure pas à pas décrit les tâches suivantes :

- [Créer un récepteur de fonctionnalité](#BKMK_CreateReceiver)

- [Ajoutez le Code au récepteur de fonctionnalité](#BKMK_AddCode)

- [Le projet de test](#BKMK_Test1)

- [Collecter des données IntelliTrace à l’aide de Microsoft Monitoring Agent](#BKMK_CollectDiagnosticData)

- [Déboguer et corriger la Solution SharePoint](#BKMK_DebugSolution)

 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Prérequis

Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :

- Éditions prises en charge de Windows et SharePoint. Consultez [configuration requise pour développer des Solutions SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).

- Visual Studio Enterprise.

## <a name="BKMK_CreateReceiver"></a> Créer un récepteur de fonctionnalité

Tout d’abord, vous créez un projet SharePoint vide qui possède un récepteur de fonctionnalité.

1. Créez un projet de solution SharePoint 2010 ou SharePoint 2013 et nommez-le **IntelliTraceTest**.

     Le **Assistant Personnalisation de SharePoint** s’affiche, dans laquelle vous pouvez spécifier à la fois le site SharePoint pour votre projet et le niveau de confiance de la solution.

2. Choisissez le **déployer une solution de batterie de serveurs** case d’option, puis choisissez le **Terminer** bouton.

     IntelliTrace fonctionne uniquement sur les solutions de batterie de serveurs.

3. Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour le **fonctionnalités** nœud, puis choisissez **ajouter une fonctionnalité**.

     Feature1.Feature s’affiche.

4. Ouvrez le menu contextuel pour Feature1.feature, puis choisissez **ajouter un récepteur d’événements** pour ajouter un module de code à la fonctionnalité.

## <a name="BKMK_AddCode"></a> Ajoutez le Code au récepteur de fonctionnalité

Ensuite, ajoutez le code à deux méthodes dans le récepteur de fonctionnalité : `FeatureActivated` et `FeatureDeactivating`. Ces méthodes déclenchent chaque fois qu’une fonctionnalité est activée ou désactivée dans SharePoint, respectivement.

1. En haut de la `Feature1EventReceiver` de classe, ajoutez le code suivant, qui déclare les variables qui spécifient le site SharePoint et le sous-site :

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

2. Remplacez la méthode `FeatureActivated` par le code suivant :

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

3. Remplacez la méthode `FeatureDeactivating` par le code suivant :

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

## <a name="BKMK_Test1"></a> Le projet de test

Maintenant que le code est ajouté au récepteur de fonctionnalité et le collecteur de données est en cours d’exécution, déployer et exécuter la solution SharePoint pour vérifier si elle fonctionne correctement.

> [!IMPORTANT]
> Pour cet exemple, une erreur est générée dans le Gestionnaire d’événements FeatureDeactivating. Plus loin dans cette procédure pas à pas, vous localisez cette erreur en utilisant le fichier .iTrace créés par le collecteur de données.

1. Déployer la solution sur SharePoint, puis ouvrez le site SharePoint dans un navigateur.

     La fonctionnalité active automatiquement, à l’origine de son récepteur de fonctionnalité Ajouter une annonce et une tâche.

2. Afficher le contenu des listes de tâches et des annonces.

     La liste d’annonces doit avoir une nouvelle annonce nommée **Activated feature : IntelliTraceTest_Feature1**, et la liste des tâches doit avoir une nouvelle tâche qui est nommée **Deactivate feature : IntelliTraceTest_ Feature1**. Si un de ces éléments est manquant, vérifiez si la fonctionnalité est activée. S’il n’est pas activé, activez-le.

3. Désactiver la fonctionnalité en procédant comme suit :

    1. Sur le **Actions du Site** menu dans SharePoint, choisissez **paramètres du Site**.

    2. Sous **Actions du Site**, choisissez le **gérer les fonctionnalités du site** lien.

    3. Regard **IntelliTraceTest Feature1**, choisissez le **Deactivate** bouton.

    4. Dans la page d’avertissement, choisissez la **désactiver cette fonctionnalité** lien.

     Le Gestionnaire d’événements FeatureDeactivating() génère une erreur.

## <a name="BKMK_CollectDiagnosticData"></a> Collecter des données IntelliTrace à l’aide de Microsoft Monitoring Agent

Si vous installez Microsoft Monitoring Agent sur le système qui exécute SharePoint, vous pouvez déboguer des solutions SharePoint à l’aide de données qui sont plus précies que les informations génériques qui retourne par IntelliTrace. L’agent fonctionne en dehors de Visual Studio à l’aide des applets de commande PowerShell pour capturer les informations de débogage lors de l’exécution de votre solution SharePoint.

> [!NOTE]
> Les informations de configuration de cette section sont spécifiques à cet exemple. Pour plus d’informations sur les autres options de configuration, consultez [à l’aide du collecteur autonome IntelliTrace](/visualstudio/debugger/using-the-intellitrace-stand-alone-collector).

1. Sur l’ordinateur qui exécute SharePoint, [configurer Microsoft Monitoring Agent et commencer à surveiller votre solution](/visualstudio/debugger/using-the-intellitrace-stand-alone-collector).

2. Désactiver la fonctionnalité :

    1. Sur le **Actions du Site** menu dans SharePoint, choisissez **paramètres du Site**.

    2. Sous **Actions du Site**, choisissez le **gérer les fonctionnalités du site** lien.

    3. Regard **IntelliTraceTest Feature1**, choisissez le **Deactivate** bouton.

    4. Dans la page d’avertissement, choisissez la **désactiver cette fonctionnalité** lien.

     Une erreur se produit (dans ce cas, en raison de l’erreur levée dans le Gestionnaire d’événements FeatureDeactivating()).

3. Dans la fenêtre PowerShell, exécutez le [Stop-WebApplicationMonitoring](http://go.microsoft.com/fwlink/?LinkID=313687) commande pour créer le fichier .iTrace, arrêter l’analyse et redémarrez votre solution SharePoint.

     **Stop-WebApplicationMonitoring**  *"\<SharePointSite>\\<SharePointAppName\>"*

## <a name="BKMK_DebugSolution"></a> Déboguer et corriger la Solution SharePoint

Maintenant, vous pouvez afficher le fichier journal IntelliTrace dans Visual Studio pour rechercher et corriger l’erreur dans la solution SharePoint.

1. Dans le dossier \IntelliTraceLogs, ouvrez le fichier .iTrace dans Visual Studio.

     Le **résumé IntelliTrace** page s’affiche. Étant donné que l’erreur n’a pas été gérée, un ID de corrélation SharePoint (GUID) apparaît dans la zone de l’exception non gérée de le **analyse** section. Choisissez le **pile des appels** bouton si vous souhaitez afficher la pile des appels où l’erreur s’est produite.

2. Choisissez le **Exception de débogage** bouton.

     Si vous y êtes invité, charger des fichiers de symboles. Dans le **IntelliTrace** fenêtre, l’exception est mise en surbrillance en tant que « levé : une erreur grave s’est produite ! ».

     Dans la fenêtre IntelliTrace, choisir l’exception pour afficher le code qui a échoué.

3. Corrigez l’erreur en ouvrant la solution SharePoint et soit mise en commentaire ou en supprimant la **lever** instruction au début de la procédure FeatureDeactivating().

4. Régénérez la solution dans Visual Studio, puis le redéployer sur SharePoint.

5. Désactiver la fonctionnalité en procédant comme suit :

    1. Sur le **Actions du Site** menu dans SharePoint, choisissez **paramètres du Site**.

    2. Sous **Actions du Site**, choisissez le **gérer les fonctionnalités du site** lien.

    3. Regard **IntelliTraceTest Feature1**, choisissez le **Deactivate** bouton.

    4. Dans la page d’avertissement, choisissez la **désactiver cette fonctionnalité** lien.

6. Ouvrez la liste des tâches et vérifiez que le **état** valeur de la tâche Deactivate est « Completed » et ses **% achevé** valeur est de 100 %.

     Le code s’exécute désormais correctement.

## <a name="see-also"></a>Voir aussi

[Vérification et débogage du code SharePoint](../sharepoint/verifying-and-debugging-sharepoint-code.md)  
[IntelliTrace](/visualstudio/debugger/intellitrace)  
[Procédure pas à pas : Vérifier le Code SharePoint à l’aide de Tests unitaires](https://msdn.microsoft.com/library/gg599006(v=vs.100).aspx)
