---
title: 'Comment : publier un projet qui a des paramètres régionaux spécifique | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 70300e7d6090e7c8155281e771522bec08308f5b
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56629662"
---
# <a name="how-to-publish-a-project-that-has-a-specific-locale"></a>Guide pratique pour publier un projet qui a des paramètres régionaux spécifiques
Une application peut contenir des composants ayant des paramètres régionaux différents. Dans ce scénario, vous devez créer une solution avec plusieurs projets, puis publier des projets distincts pour chacun des paramètres régionaux. Cette procédure montre comment utiliser une macro pour publier le premier projet dans une solution avec les paramètres régionaux « en ». Si vous souhaitez essayer cette procédure avec d'autres paramètres régionaux, veillez à définir `localeString` dans la macro pour que sa valeur corresponde aux paramètres régionaux que vous utilisez (par exemple, « fr » ou « fr-FR »).

> [!NOTE]
>  Quand vous utilisez cette macro, l'emplacement de publication doit être une URL ou un partage UNC (Universal Naming Convention) valide. De plus, les services IIS (Internet Information Services) doivent être installés sur votre ordinateur. Pour installer IIS, dans le menu **Démarrer**, cliquez sur **Panneau de configuration**. Double-cliquez sur **Ajouter ou supprimer des programmes**. Dans **Ajouter ou supprimer des programmes**, cliquez sur **Ajouter ou supprimer des composants Windows**. Dans l’**Assistant Composants Windows**, cochez la case **Gestionnaire des services Internet (IIS)** dans la liste **Composants**. Cliquez ensuite sur **Terminer** pour fermer l’Assistant.

### <a name="to-create-the-publishing-macro"></a>Pour créer la macro de publication

1.  Pour ouvrir l’Explorateur de macros, dans le menu **Outils**, pointez sur **Macros**, puis cliquez sur **Explorateur de macros**.

2.  Créez un module de macro. Dans l’Explorateur de macros, sélectionnez **MyMacros**. Sur le **outils** menu, pointez sur **Macros**, puis cliquez sur **nouveau Module de Macro**. Nommez le module **PublishSpecificCulture**.

3.  Dans l’Explorateur de macros, développez le nœud **MyMacros**, puis ouvrez le module **PublishAllProjects** en double-cliquant dessus (ou, dans le menu **Outils**, pointez sur **Macros**, puis cliquez sur **Éditeur de macros**).

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

1.  Pour créer un projet d’application Windows Visual Basic, dans le menu **Fichier**, pointez sur **Nouveau**, puis cliquez sur **Projet**.

2.  Dans la boîte de dialogue **Nouveau projet**, sélectionnez **Application Windows** dans le nœud **Visual Basic**. Nommez le projet *PublishLocales*.

3.  Cliquez sur Form1. Dans la fenêtre **Propriétés**, sous **Design**, changez la propriété **Langue** de **(Par défaut)** en **Anglais**. Changez la propriété **Texte** du formulaire en **MyForm**.

     Notez que les DLL de ressource localisées ne sont pas créées tant qu'elles ne sont pas requises. Par exemple, elles sont créées quand vous modifiez le texte du formulaire ou l'un de ses contrôles, une fois les nouveaux paramètres régionaux spécifiés.

4.  Publiez *PublishLocales* à l’aide de l’IDE de Visual Studio.

     Dans l’**Explorateur de solutions**, sélectionnez *PublishLocales*. Dans le menu **Projet**, sélectionnez **Propriétés**. Dans le Concepteur de projets, sur le **publier** , spécifiez un emplacement de publication de **http://localhost/PublishLocales**, puis cliquez sur **publier maintenant**.

     Quand la page web de publication apparaît, fermez-la. (Pour cette étape, vous devez uniquement publier le projet, sans l'installer.)

5.  Republiez *PublishLocales* en appelant la macro dans la fenêtre d’invite de commandes Visual Studio. Pour afficher la fenêtre d’invite de commandes, sur le **vue** menu, pointez sur **Windows autres** puis cliquez sur **fenêtre de commande**, ou appuyez sur **Ctrl** + **Alt**+**A**. Dans la fenêtre d’invite de commandes, tapez `macros`; saisie semi-automatique fournit une liste des macros disponibles. Sélectionnez la macro suivante et appuyez sur ENTRÉE :

     `Macros.MyMacros.PublishSpecificCulture.PublishProjectFirstProjectWithEnLocale`

6.  Une fois le processus de publication terminé, un message confirme que la publication de *PublishLocales\PublishLocales.vbproj* a été correctement effectuée. La langue de publication était « en ». Cliquez sur **OK** dans la boîte de message. Quand la page web de publication apparaît, cliquez sur **Installer**.

7.  Consultez *C:\Inetpub\wwwroot\PublishLocales\en*. Vous devez voir les fichiers installés, comme les manifestes, *setup.exe* et le fichier de page web de publication, en plus de la DLL de ressource localisée. (Par défaut, ClickOnce ajoute une extension *.deploy* aux fichiers EXE et DLL. Vous pouvez supprimer cette extension après le déploiement.)

## <a name="see-also"></a>Voir aussi
- [Publier des applications ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Environnement de développement des macros](/previous-versions/visualstudio/visual-studio-2010/fb30sxt3(v=vs.100))
- [Fenêtre Explorateur de macros](/previous-versions/visualstudio/visual-studio-2010/wwkx67sw(v=vs.100))
- [Comment : modifier et créer des macros par programmation](/previous-versions/visualstudio/visual-studio-2010/k91y6132(v=vs.100))