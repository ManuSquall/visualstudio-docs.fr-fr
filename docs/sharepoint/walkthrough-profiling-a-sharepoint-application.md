---
title: 'Procédure pas à pas : profilage d’une application SharePoint | Microsoft Docs'
description: Dans cette procédure pas à pas, utilisez les outils de profilage dans Visual Studio pour optimiser les performances d’une application SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, profiling
- performance testing [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, performance testing
- profiling [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 796c41ae50a33f00f72e0286d5e9680f9016cf58
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99952562"
---
# <a name="walkthrough-profile-a-sharepoint-application"></a>Procédure pas à pas : profilage d’une application SharePoint
  Cette procédure pas à pas montre comment utiliser les outils de profilage dans Visual Studio pour optimiser les performances d'une application SharePoint. L'application d'exemple est un récepteur d'événements de fonctionnalité SharePoint qui contient une boucle inactive qui dégrade les performances du récepteur d'événements de fonctionnalité. Le profileur Visual Studio vous permet de localiser et d’éliminer la partie la plus coûteuse (la plus lente) du projet, également appelée *chemin réactif*.

 Cette procédure pas à pas décrit les tâches suivantes :

- [Ajoutez une fonctionnalité et un récepteur d’événements de fonctionnalité](#add-a-feature-and-feature-event-receiver).

- [Configurez et déployez l’application SharePoint](#configure-and-deploy-the-sharepoint-application).

- [Exécutez l’application SharePoint](#run-the-sharepoint-application).

- [Affichez et interprétez les résultats du profil](#view-and-interpret-the-profile-results).

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Prérequis
 Vous devez disposer des éléments suivants pour exécuter cette procédure pas à pas :

- Éditions prises en charge de Microsoft Windows et SharePoint.

- [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)].

## <a name="create-a-sharepoint-project"></a>Créer un projet SharePoint
 Commencez par créer un projet SharePoint.

### <a name="to-create-a-sharepoint-project"></a>Pour créer un projet SharePoint

1. Dans la barre de menus, choisissez **fichier**  >  **nouveau**  >  **projet** pour afficher la boîte de dialogue **nouveau projet** .

2. Développez le nœud **SharePoint** sous **Visual C#** ou **Visual Basic**, puis choisissez le nœud **2010** .

3. Dans le volet modèles, choisissez le modèle de **projet SharePoint 2010** .

4. Dans la zone **nom** **, entrez prolest**, puis choisissez le bouton **OK** .

    L' **Assistant Personnalisation de SharePoint** s’affiche.

5. Dans la page **spécifier le site et le niveau de sécurité pour le débogage** , entrez l’URL du site du serveur SharePoint où vous souhaitez déboguer la définition de site, ou utilisez l’emplacement par défaut (<em>nom système</em>http:///).

6. Dans la section **quel est le niveau de confiance de cette solution SharePoint ?** , choisissez la case **d’option déployer en tant que solution de batterie** .

    Actuellement, vous ne pouvez profiler que des solutions de batterie. Pour plus d’informations sur les solutions sandbox et les solutions de batterie de serveurs, consultez Considérations sur les solutions [bac à sable (sandbox)](../sharepoint/sandboxed-solution-considerations.md).

7. Cliquez sur le bouton **Terminer**. Le projet s’affiche dans **Explorateur de solutions**.

## <a name="add-a-feature-and-feature-event-receiver"></a>Ajouter un récepteur d’événements de fonctionnalité et de fonctionnalité
 Ensuite, ajoutez une fonctionnalité au projet avec un récepteur d’événements pour la fonctionnalité. Ce récepteur d'événements contiendra le code à profiler.

### <a name="to-add-a-feature-and-feature-event-receiver"></a>Pour ajouter une fonctionnalité et un récepteur d’événements de fonctionnalité

1. Dans **Explorateur de solutions**, ouvrez le menu contextuel du nœud **fonctionnalités** , choisissez **Ajouter une fonctionnalité**, puis laissez le nom à la valeur par défaut, **Feature1**.

2. Dans **Explorateur de solutions**, ouvrez le menu contextuel pour **Feature1**, puis choisissez **Ajouter un récepteur d’événements**.

     Cela ajoute un fichier de code à la fonctionnalité avec plusieurs gestionnaires d’événements commentés et ouvre le fichier à modifier.

3. Dans la classe de récepteur d'évènements, ajoutez les déclarations de variables suivantes.

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

4. Remplacez la procédure `FeatureActivated` par le code ci-dessous.

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

5. Ajoutez la procédure suivante en dessous de la `FeatureActivated` procédure.

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

6. Dans **Explorateur de solutions**, ouvrez le menu contextuel du projet (le plus le **plus),** puis choisissez **Propriétés**.

7. Dans la boîte de dialogue **Propriétés** , choisissez l’onglet **SharePoint** .

8. Dans la liste **configuration de déploiement active** , choisissez **aucune activation**.

     Sélectionner cette configuration de déploiement vous permet d’activer manuellement la fonctionnalité ultérieurement dans SharePoint.

9. Enregistrez le projet.

## <a name="configure-and-deploy-the-sharepoint-application"></a>Configurer et déployer l’application SharePoint
 Maintenant que le projet SharePoint est prêt, configurez-le et déployez-le sur le serveur SharePoint.

### <a name="to-configure-and-deploy-the-sharepoint-application"></a>Pour configurer et déployer l'application SharePoint

1. Dans le menu **analyser** , choisissez **lancer l’Assistant Performance**.

2. Sur la page un de l' **Assistant Performance**, laissez la méthode de profilage en tant qu’échantillonnage de l' **UC** et choisissez le bouton **suivant** .

     Les autres méthodes de profilage peuvent être utilisées dans des situations plus avancées de profilage. Pour plus d’informations, consultez [Understanding Performance Collection Methods](../profiling/understanding-performance-collection-methods.md) (Fonctionnement des méthodes de collecte des données de performances).

3. Dans la page 2 de l' **Assistant Performance**, laissez la cible du **profil en tant** que Profile, puis choisissez le bouton **suivant** .

     Si une solution comporte plusieurs projets, ils apparaissent dans cette liste.

4. Dans la page 3 de l' **Assistant Performance**, désactivez la case à cocher **activer le profilage d’interaction de couche** , puis cliquez sur le bouton **suivant** .

     La fonctionnalité de profilage d’interaction de couche (TIP) est utile pour mesurer les performances des applications qui interrogent les bases de données et vous indiquer le nombre de fois qu’une page web est demandée. Étant donné que ces données ne sont pas requises pour cet exemple, nous n'activerons pas cette fonctionnalité.

5. À la page 4 de l' **Assistant Performance**, laissez la case à cocher **lancer le profilage une fois l’Assistant terminé** activée, puis choisissez le bouton **Terminer** .

     L’Assistant Active le profilage d’application sur le serveur, affiche la fenêtre **Explorateur de performances** , puis génère, déploie et exécute l’application SharePoint.

## <a name="run-the-sharepoint-application"></a>Exécuter l’application SharePoint
 Activez la fonctionnalité dans SharePoint, déclenchant le code d'événement `FeatureActivation` à exécuter.

### <a name="to-run-the-sharepoint-application"></a>Pour exécuter l'application SharePoint

1. Dans SharePoint, ouvrez le menu **actions du site** , puis choisissez **paramètres du site**.

2. Dans la liste **actions du site** , choisissez le lien gérer les fonctionnalités du **site** .

3. Dans la liste des **fonctionnalités** , choisissez le bouton **activer** en regard de l’option **Feature1** de la liste de champs.

     Ce faisant, une pause survient en raison de la boucle inactive appelée dans la fonction `FeatureActivated`.

4. Dans la barre **lancement rapide** , choisissez **listes** , puis dans la liste **listes** , choisissez **annonces**.

     Notez qu’une nouvelle annonce a été ajoutée à la liste indiquant que la fonctionnalité a été activée.

5. Fermez le site SharePoint.

     Après avoir fermé SharePoint, le profileur crée et affiche un exemple de rapport de profilage et l’enregistre sous la forme d’un fichier. vsp dans le dossier **du projet** Profile.

## <a name="view-and-interpret-the-profile-results"></a>Afficher et interpréter les résultats du profil
 Maintenant que vous avez exécuté et profilé l'application SharePoint, affichez les résultats des tests.

### <a name="to-view-and-interpret-the-profile-results"></a>Pour afficher et interpréter les résultats du profil

1. Dans la section **fonctions faisant le plus de travail individuel** de l’exemple de rapport de profilage, Notez que `TimeCounter` est proche du haut de la liste.

     Cet emplacement indique que `TimeCounter` est l'une des fonctions présentant le plus grand nombre d'exemples ; autrement dit, il s'agit de l'un des plus importants goulots d'étranglement de performance de l'application. Toutefois, cette situation n'est pas étonnante, parce qu'elle a expressément été conçue à des fins de démonstration.

2. Dans la section **fonctions qui exécutent le plus de travail individuel** , cliquez sur le `ProcessRequest` lien pour afficher la distribution des coûts de la `ProcessRequest` fonction.

     Dans la section **fonctions appelées** pour `ProcessRequest` , Notez que la fonction **FeatureActivated** est listée en tant que fonction appelée la plus coûteuse.

3. Dans la section **fonctions appelées** , choisissez le bouton **FeatureActivated** .

     Dans la section des **fonctions appelées** pour **FeatureActivated**, la `TimeCounter` fonction est indiquée comme la fonction appelée la plus coûteuse. Dans le volet **affichage du code de fonction** , le code en surbrillance ( `TimeCounter` ) est la zone réactive et indique l’endroit où la correction est nécessaire.

4. Fermez le rapport de profilage de l'échantillon.

     Pour afficher à nouveau le rapport à tout moment, ouvrez le fichier. vsp dans la fenêtre **Explorateur de performances** .

## <a name="fix-the-code-and-reprofile-the-application"></a>Corriger le code et reprofiler l’application
 Maintenant que la fonction de la zone réactive de l'application SharePoint a été identifiée, corrigez-la.

### <a name="to-fix-the-code-and-reprofile-the-application"></a>Pour corriger le code et reprofiler l'application

1. Dans le code du récepteur d'événements de fonctionnalité, commentez l'appel de méthode `TimeCounter` dans `FeatureActivated` pour empêcher tout appel.

2. Enregistrez le projet.

3. Dans **Explorateur de performances**, **Ouvrez le dossier** cibles, puis choisissez le nœud prole.

4. Dans la barre d’outils **Explorateur de performances** , sous l’onglet **actions** , choisissez le bouton **Démarrer le profilage** .

     Si vous souhaitez modifier les propriétés de profilage avant de reprofilage l’application, choisissez plutôt le bouton **lancer l’Assistant Performance** .

5. Suivez les instructions de la section **exécution de l’application SharePoint** , précédemment dans cette rubrique.

     Comme l'appel à la boucle inactive a été supprimé, la fonctionnalité doit s'activer beaucoup plus rapidement. Le rapport de profilage d'échantillon doit le refléter.

## <a name="see-also"></a>Voir aussi
- [Présentation de la session de performance](../profiling/performance-session-overview.md)
- [Guide du débutant en profilage des performances](../profiling/beginners-guide-to-performance-profiling.md)
- [Rechercher les goulots d’étranglement d’application avec le profileur Visual Studio](/archive/msdn-magazine/2008/march/find-application-bottlenecks-with-visual-studio-profiler)