---
title: 'Comment : publier un projet qui a des paramètres régionaux spécifique | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- publishing, localized projects
- locales, publishing for
- deploying applications [ClickOnce], localized projects
- locales, deploying for
- publishing localized projects
- macros, deploying with
- macros, publishing with
ms.assetid: 7c4cd83a-f985-4c85-9022-fadb5dbd2b39
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: a08c7cc22129a783e692c437724114b3f44888a3
ms.sourcegitcommit: 6a955a2d179cd0e137942389f940d9fcbbe125de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2018
ms.locfileid: "51607781"
---
# <a name="how-to-publish-a-project-that-has-a-specific-locale"></a>Comment : publier un projet qui a des paramètres régionaux spécifiques
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Une application peut contenir des composants ayant des paramètres régionaux différents. Dans ce scénario, vous devez créer une solution avec plusieurs projets, puis publier des projets distincts pour chacun des paramètres régionaux. Cette procédure montre comment utiliser une macro pour publier le premier projet dans une solution avec les paramètres régionaux « en ». Si vous souhaitez essayer cette procédure avec d'autres paramètres régionaux, veillez à définir `localeString` dans la macro pour que sa valeur corresponde aux paramètres régionaux que vous utilisez (par exemple, « fr » ou « fr-FR »).  
  
> [!NOTE]
>  Quand vous utilisez cette macro, l'emplacement de publication doit être une URL ou un partage UNC (Universal Naming Convention) valide. De plus, les services IIS (Internet Information Services) doivent être installés sur votre ordinateur. Pour installer IIS, sur le **Démarrer** menu, cliquez sur **le panneau de configuration**. Double-cliquez sur **ajouter ou supprimer des programmes**. Dans **Ajout / Suppression de programmes**, cliquez sur **ajouter/supprimer des composants Windows**. Dans le **Assistant Composants de Windows**, sélectionnez le **Internet Information Services (IIS)** case à cocher dans la **composants** liste. Puis cliquez sur **Terminer** pour fermer l’Assistant.  
  
### <a name="to-create-the-publishing-macro"></a>Pour créer la macro de publication  
  
1.  Pour ouvrir l’Explorateur de macros, sur le **outils** menu, pointez sur **Macros**, puis cliquez sur **Explorateur de macros**.  
  
2.  Créez un module de macro. Dans l’Explorateur de macros, sélectionnez **MyMacros**. Sur le **outils** menu, pointez sur **Macros**, puis cliquez sur **nouveau Module de Macro**. Nommez le module **PublishSpecificCulture**.  
  
3.  Dans l’Explorateur de macros, développez le **MyMacros** nœud, puis ouvrez le **PublishAllProjects** module en double-cliquant dessus (ou, à partir de la **outils** menu, pointez sur **Macros**, puis cliquez sur **de macros**).  
  
4.  Dans l'Éditeur de macros, ajoutez le code suivant au module, après les instructions `Import` :  
  
    ```vb  
    Module PublishSpecificCulture  
        Sub PublishProjectFirstProjectWithEnLocale()  
            ' Note: You should publish projects by using the IDE at least once  
            ' before you use this macro. Items such as the certificate and the   
            ' security zone must be set.  
            Dim localeString As String = "en"  
  
            ' Get first project.  
            Dim proj As Project = DTE.Solution.Projects.Item(1)  
            Dim publishProperties As Object = proj.Properties.Item("Publish").Value  
  
            ' GenerateManifests and SignManifests must always be set to  
            ' True for publishing to work.   
            proj.Properties.Item("GenerateManifests").Value = True  
            proj.Properties.Item("SignManifests").Value = True  
  
            'Set the publish language.  
            'This will set the deployment language and pick up all   
            ' en resource dlls:  
            Dim originalTargetCulture As String = _  
                publishProperties.Item("TargetCulture").Value  
            publishProperties.Item("TargetCulture").Value = localeString  
  
            'Append 'en' to end of publish, install, and update URLs if needed:  
            Dim originalPublishUrl As String = _  
                publishProperties.Item("PublishUrl").Value  
            Dim originalInstallUrl As String = _  
                publishProperties.Item("InstallUrl").Value  
            Dim originalUpdateUrl As String = _  
                publishProperties.Item("UpdateUrl").Value  
            publishProperties.Item("PublishUrl").Value = _  
                AppendStringToUrl(localeString, New Uri(originalPublishUrl))  
            If originalInstallUrl <> String.Empty Then  
                publishProperties.Item("InstallUrl").Value = _  
                    AppendStringToUrl(localeString, New Uri(originalInstallUrl))  
            End If  
            If originalUpdateUrl <> String.Empty Then  
                publishProperties.Item("UpdateUrl").Value = _  
                    AppendStringToUrl(localeString, New Uri(originalUpdateUrl))  
            End If  
            proj.Save()  
  
            Dim slnbld2 As SolutionBuild2 = _  
                CType(DTE.Solution.SolutionBuild, SolutionBuild2)  
            slnbld2.Clean(True)  
  
            slnbld2.BuildProject( _  
            proj.ConfigurationManager.ActiveConfiguration.ConfigurationName, _  
            proj.UniqueName, True)  
  
            ' Only publish if build is successful.  
            If slnbld2.LastBuildInfo <> 0 Then  
                MsgBox("Build failed for " & proj.UniqueName)  
            Else  
                slnbld2.PublishProject( _  
                proj.ConfigurationManager.ActiveConfiguration.ConfigurationName, _  
                proj.UniqueName, True)  
                If slnbld2.LastPublishInfo = 0 Then  
                    MsgBox("Publish succeeded for " & proj.UniqueName _  
                    & vbCrLf & "." _  
                    & " Publish Language was '" & localeString & "'.")  
                Else  
                    MsgBox("Publish failed for " & proj.UniqueName)  
                End If  
            End If  
  
            ' Return URLs and target culture to their previous state.  
            publishProperties.Item("PublishUrl").Value = originalPublishUrl  
            publishProperties.Item("InstallUrl").Value = originalInstallUrl  
            publishProperties.Item("UpdateUrl").Value = originalUpdateUrl  
            publishProperties.Item("TargetCulture").Value = originalTargetCulture  
            proj.Save()  
        End Sub  
  
        Private Function AppendStringToUrl(ByVal str As String, _  
        ByVal baseUri As Uri) As String  
            Dim returnValue As String = baseUri.OriginalString  
            If baseUri.IsFile OrElse baseUri.IsUnc Then  
                returnValue = IO.Path.Combine(baseUri.OriginalString, str)  
            Else  
                If Not baseUri.ToString.EndsWith("/") Then  
                    returnValue = baseUri.OriginalString & "/" & str  
                Else  
                    returnValue = baseUri.OriginalString & str  
                End If  
            End If  
            Return returnValue  
        End Function  
    End Module  
    ```  
  
5.  Fermez l'éditeur de macros. Le focus retourne dans Visual Studio.  
  
### <a name="to-publish-a-project-for-a-specific-locale"></a>Pour publier un projet avec des paramètres régionaux spécifiques  
  
1.  Pour créer un projet d’Application Windows de Visual Basic, sur le **fichier** menu, pointez sur **New**, puis cliquez sur **projet**.  
  
2.  Dans le **nouveau projet** boîte de dialogue, sélectionnez **Windows Application** à partir de la **Visual Basic** nœud. Nommez le projet **PublishLocales**.  
  
3.  Cliquez sur Form1. Dans le **propriétés** fenêtre, sous **conception**, modifier le **langage** propriété à partir de **(par défaut)** à **anglais**. Modifier le **texte** propriété du formulaire à **MyForm**.  
  
     Notez que les DLL de ressource localisées ne sont pas créées tant qu'elles ne sont pas requises. Par exemple, elles sont créées quand vous modifiez le texte du formulaire ou l'un de ses contrôles, une fois les nouveaux paramètres régionaux spécifiés.  
  
4.  Publiez PublishLocales à l'aide de l'IDE de Visual Studio.  
  
     Dans **l’Explorateur de solutions**, sélectionnez PublishLocales. Sur le **projet** menu, sélectionnez **propriétés**. Dans le Concepteur de projets, sur le **publier** , spécifiez un emplacement de publication de **http://localhost/PublishLocales**, puis cliquez sur **publier maintenant**.  
  
     Quand la page web de publication apparaît, fermez-la. (Pour cette étape, vous devez uniquement publier le projet, sans l'installer.)  
  
5.  Publiez à nouveau PublishLocales en appelant la macro dans la fenêtre d'invite de commandes Visual Studio. Pour afficher la fenêtre d’invite de commandes, sur le **vue** menu, pointez sur **Windows autres** puis cliquez sur **fenêtre de commande**, ou appuyez sur CTRL + ALT + A. Dans la fenêtre d’invite de commandes, tapez `macros`; saisie semi-automatique fournit une liste des macros disponibles. Sélectionnez la macro suivante et appuyez sur ENTRÉE :  
  
     `Macros.MyMacros.PublishSpecificCulture.PublishProjectFirstProjectWithEnLocale`  
  
6.  Une fois le processus de publication terminé, un message confirme que la publication de PublishLocales\PublishLocales.vbproj a été correctement effectuée. La langue de publication était « en ». Cliquez sur **OK** dans la boîte de message. Lorsque la page Web de publication s’affiche, cliquez sur **installer**.  
  
7.  Consultez C:\Inetpub\wwwroot\PublishLocales\en. Les fichiers installés tels que les manifestes, setup.exe et le fichier de page web de publication doivent s'afficher, en plus de la DLL de ressource localisée. (Par défaut, ClickOnce ajoute une extension .deploy aux fichiers EXE et DLL. Vous pouvez supprimer cette extension après le déploiement.)  
  
## <a name="see-also"></a>Voir aussi  
 [Publication d’applications ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Environnement de développement des macros](http://msdn.microsoft.com/en-us/d23105d8-34fe-4ad9-8278-fae2c660aeac)   
 [Fenêtre Explorateur de macros](http://msdn.microsoft.com/en-us/762169e6-f83f-44b4-bffa-d0f107cae9a3)   
 [Comment : modifier et créer des Macros par programmation](http://msdn.microsoft.com/en-us/6716f820-1feb-48ad-a718-27eb6b473c5a)



