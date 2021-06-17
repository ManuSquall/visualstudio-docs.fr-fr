---
title: Déboguer une application SharePoint à l’aide d’IntelliTrace
description: Utilisez IntelliTrace pour déboguer et résoudre plus facilement les applications SharePoint. Créez et ajoutez du code à un récepteur de fonctionnalité. Testez le projet. Collecter les données IntelliTrace.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- IntelliTrace [SharePoint development in Visual Studio]
- standalone data collector
- SharePoint development in Visual Studio, IntelliTrace
- data collector
- IntelliTrace
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: cf7fa6c7255e05c465d6c209db5e9581a49aee64
ms.sourcegitcommit: 1f27f33852112702ee35fbc0c02fba37899e4cf5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2021
ms.locfileid: "112112842"
---
# <a name="walkthrough-debug-a-sharepoint-application-by-using-intellitrace"></a>Procédure pas à pas : déboguer une application SharePoint à l’aide d’IntelliTrace

Avec IntelliTrace, vous pouvez déboguer plus facilement des solutions SharePoint. Les débogueurs traditionnels vous offrent uniquement une capture instantanée d’une solution à l’heure actuelle. Toutefois, vous pouvez utiliser IntelliTrace pour examiner les événements passés qui se sont produits dans votre solution et le contexte dans lequel ils se sont produits et accéder au code.

 Cette procédure pas à pas montre comment déboguer un projet SharePoint dans Visual Studio à l’aide de Microsoft Monitoring Agent pour collecter des données IntelliTrace à partir d’applications déployées. Pour analyser ces données, vous devez utiliser Visual Studio Enterprise. Ce projet incorpore un récepteur de fonctionnalité qui, lorsque la fonctionnalité est activée, ajoute une tâche à la liste des tâches et une annonce à la liste annonces. Lorsque la fonctionnalité est désactivée, la tâche est marquée comme terminée et une deuxième annonce est ajoutée à la liste des annonces. Toutefois, la procédure contient une erreur logique qui empêche le projet de s’exécuter correctement. À l’aide d’IntelliTrace, vous allez Rechercher et corriger l’erreur.

 **S’applique à :** Les informations contenues dans cette rubrique s’appliquent aux solutions SharePoint qui ont été créées dans Visual Studio.

 Cette procédure pas à pas décrit les tâches suivantes :

- [Créer un récepteur de fonctionnalité](#create-a-feature-receiver)

- [Ajouter le code au récepteur de fonctionnalité](#add-code-to-the-feature-receiver)

- [Tester le projet](#test-the-project)

- [Collecter des données IntelliTrace à l’aide de Microsoft Monitoring Agent](#collect-intellitrace-data-by-using-microsoft-monitoring-agent)

- [Déboguer et corriger la solution SharePoint](#debug-and-fix-the-sharepoint-solution)

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Prérequis

Vous devez disposer des éléments suivants pour exécuter cette procédure pas à pas :

- Éditions prises en charge de Windows et SharePoint.

- Visual Studio Enterprise.

## <a name="create-a-feature-receiver"></a>Créer un récepteur de fonctionnalité

Tout d’abord, vous créez un projet SharePoint vide qui possède un récepteur de fonctionnalité.

1. Créez un projet de solution SharePoint ciblant la version de SharePoint que vous avez installée et nommez-le **IntelliTraceTest**.

     L' **Assistant Personnalisation de SharePoint** s’affiche, dans lequel vous pouvez spécifier à la fois le site SharePoint pour votre projet et le niveau de confiance de la solution.

2. Sélectionnez la case **d’option déployer en tant que solution de batterie** , puis choisissez le bouton **Terminer** .

     IntelliTrace fonctionne uniquement sur les solutions de batterie de serveurs.

3. Dans **Explorateur de solutions**, ouvrez le menu contextuel du nœud **fonctionnalités** , puis choisissez **Ajouter une fonctionnalité**.

     *Feature1. Feature* s’affiche.

4. Ouvrez le menu contextuel pour Feature1. Feature, puis choisissez **Ajouter un récepteur d’événements** pour ajouter un module de code à la fonctionnalité.

## <a name="add-code-to-the-feature-receiver"></a>Ajouter du code au récepteur de fonctionnalité

Ensuite, ajoutez du code à deux méthodes dans le récepteur de fonctionnalité : `FeatureActivated` et `FeatureDeactivating` . Ces méthodes se déclenchent lorsqu’une fonctionnalité est activée ou désactivée dans SharePoint, respectivement.

1. En haut de la `Feature1EventReceiver` classe, ajoutez le code suivant, qui déclare les variables qui spécifient le site et le sous-site SharePoint :

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

## <a name="test-the-project"></a>Tester le projet

Maintenant que le code est ajouté au récepteur de fonctionnalité et que le collecteur de données est en cours d’exécution, déployez et exécutez la solution SharePoint pour vérifier si elle fonctionne correctement.

> [!IMPORTANT]
> Pour cet exemple, une erreur est générée dans le gestionnaire d’événements FeatureDeactivating. Plus loin dans cette procédure pas à pas, vous localisez cette erreur en utilisant le fichier. iTrace créé par le collecteur de données.

1. Déployez la solution sur SharePoint, puis ouvrez le site SharePoint dans un navigateur.

     La fonctionnalité est automatiquement activée, ce qui amène son récepteur de fonctionnalité à ajouter une annonce et une tâche.

2. Affichez le contenu des listes annonces et tâches.

     La liste d’annonces doit avoir une nouvelle annonce nommée **fonctionnalité activée : IntelliTraceTest_Feature1**, et la liste des tâches doit avoir une nouvelle tâche nommée désactiver la **fonctionnalité : IntelliTraceTest_Feature1**. Si l’un de ces éléments est manquant, vérifiez si la fonctionnalité est activée. S’il n’est pas activé, activez-le.

3. Désactivez la fonctionnalité en procédant comme suit :

   1. Dans le menu **actions du site** dans SharePoint, choisissez Paramètres du **site**.

   2. Sous **actions du site**, choisissez le lien **gérer les fonctionnalités du site** .

   3. En regard de **IntelliTraceTest Feature1**, choisissez le bouton **Désactiver** .

   4. Sur la page avertissement, choisissez le lien **désactiver cette fonctionnalité** .

      Le gestionnaire d’événements FeatureDeactivating () génère une erreur.

## <a name="collect-intellitrace-data-by-using-microsoft-monitoring-agent"></a>Collecter des données IntelliTrace à l’aide de Microsoft Monitoring Agent

Si vous installez Microsoft Monitoring Agent sur le système qui exécute SharePoint, vous pouvez déboguer des solutions SharePoint en utilisant des données plus spécifiques que les informations génériques retournées par IntelliTrace. L’agent fonctionne en dehors de Visual Studio à l’aide des applets de commande PowerShell pour capturer les informations de débogage pendant l’exécution de votre solution SharePoint.

> [!NOTE]
> Les informations de configuration de cette section sont spécifiques à cet exemple. Pour plus d’informations sur les autres options de configuration, consultez [utilisation du collecteur autonome IntelliTrace](../debugger/using-the-intellitrace-stand-alone-collector.md).

1. Sur l’ordinateur qui exécute SharePoint, [configurez Microsoft Monitoring agent et commencez à surveiller votre solution](../debugger/using-the-intellitrace-stand-alone-collector.md).

2. Désactivez la fonctionnalité :

   1. Dans le menu **actions du site** dans SharePoint, choisissez Paramètres du **site**.

   2. Sous **actions du site**, choisissez le lien **gérer les fonctionnalités du site** .

   3. En regard de **IntelliTraceTest Feature1**, choisissez le bouton **Désactiver** .

   4. Sur la page avertissement, choisissez le lien **désactiver cette fonctionnalité** .

      Une erreur se produit (dans ce cas, en raison de l’erreur levée dans le gestionnaire d’événements FeatureDeactivating ()).

3. Dans la fenêtre PowerShell, exécutez la commande [Stop-WebApplicationMonitoring](/previous-versions/system-center/powershell/system-center-2012-r2/dn472753(v=sc.20)) pour créer le fichier. iTrace, arrêtez la surveillance, puis redémarrez votre solution SharePoint.

     **Stop-WebApplicationMonitoring***« \<SharePointSite> \\<SharePointAppName \> »*  

## <a name="debug-and-fix-the-sharepoint-solution"></a>Déboguer et corriger la solution SharePoint

Vous pouvez maintenant consulter le fichier Journal IntelliTrace dans Visual Studio pour rechercher et corriger l’erreur dans la solution SharePoint.

1. Dans le dossier \IntelliTraceLogs, ouvrez le fichier. iTrace dans Visual Studio.

     La page **Résumé IntelliTrace** s’affiche. Étant donné que l’erreur n’a pas été gérée, un ID de corrélation SharePoint (un GUID) apparaît dans la zone d’exception non gérée de la section **analyse** . Choisissez le bouton **pile des appels** si vous souhaitez afficher la pile des appels dans laquelle l’erreur s’est produite.

2. Choisissez le bouton d' **exception de débogage** .

     Si vous y êtes invité, chargez les fichiers de symboles. Dans la fenêtre **IntelliTrace** , l’exception est mise en surbrillance comme « levée : une erreur grave s’est produite ! ».

     Dans la fenêtre IntelliTrace, choisissez l’exception pour afficher le code qui a échoué.

3. Corrigez l’erreur en ouvrant la solution SharePoint, puis en commentant ou en supprimant l’instruction **throw** en haut de la procédure FeatureDeactivating ().

4. Régénérez la solution dans Visual Studio, puis redéployez-la sur SharePoint.

5. Désactivez la fonctionnalité en procédant comme suit :

    1. Dans le menu **actions du site** dans SharePoint, choisissez Paramètres du **site**.

    2. Sous **actions du site**, choisissez le lien **gérer les fonctionnalités du site** .

    3. En regard de **IntelliTraceTest Feature1**, choisissez le bouton **Désactiver** .

    4. Sur la page avertissement, choisissez le lien **désactiver cette fonctionnalité** .

6. Ouvrez la liste des tâches, puis vérifiez que la valeur d' **État** de la tâche de désactivation est « terminé » et que sa valeur **% achevée** est de 100%.

     Le code s’exécute désormais correctement.

## <a name="see-also"></a>Voir aussi

- [Vérifier et déboguer le code SharePoint](../sharepoint/verifying-and-debugging-sharepoint-code.md)
- [IntelliTrace](../debugger/intellitrace.md)
- [Procédure pas à pas : vérifier le code SharePoint à l’aide de tests unitaires](/previous-versions/visualstudio/visual-studio-2010/gg599006\(v\=vs.100\))
