---
title: 'Comment : publier une application WPF avec les styles visuels activés | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
ms.assetid: 73b22b02-fc75-42aa-82d3-51fdcaf8e5c8
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c3691f782f317667b56f6bf3641c0f4c6a703eda
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697572"
---
# <a name="how-to-publish-a-wpf-application-with-visual-styles-enabled"></a>Comment : publier une application WPF avec les styles visuels activés

[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Les styles visuels permettent de modifier l’apparence des contrôles communs en fonction du thème choisi par l’utilisateur. Par défaut, les styles visuels ne sont pas activés pour les applications Windows Presentation Foundation (WPF). vous devez donc les activer manuellement. Toutefois, l’activation de styles visuels pour une application WPF, puis la publication de la solution génère une erreur. Cette rubrique explique comment résoudre cette erreur et le processus de publication d’une application WPF avec les styles visuels activés. Pour plus d’informations sur les styles visuels, consultez [vue d’ensemble des styles visuels](https://msdn.microsoft.com/5b5d7bb6-684f-478d-bf5f-b8d18bbcff2e). Pour plus d’informations sur le message d’erreur, consultez [résolution des erreurs spécifiques dans les déploiements ClickOnce](../deployment/troubleshooting-specific-errors-in-clickonce-deployments.md).

 Pour résoudre l’erreur et publier la solution, vous devez effectuer les tâches suivantes :

- [Publiez la solution sans que les styles visuels soient activés](#BKMK_publishsolwovs).

- [Créez un fichier manifeste](#BKMK_CreateManifest).

- [Incorporez le fichier manifeste dans le fichier exécutable de la solution publiée](#BKMK_embedmanifest).

- [Signez les manifestes d’application et de déploiement](#BKMK_signappdeplyman).

  Ensuite, vous pouvez déplacer les fichiers publiés vers l’emplacement à partir duquel les utilisateurs finaux doivent installer l’application.

## <a name="publish-the-solution-without-visual-styles-enabled"></a><a name="BKMK_publishsolwovs"></a> Publier la solution sans les styles visuels activés

1. Vérifiez que les styles visuels ne sont pas activés pour votre projet. Tout d’abord, examinez le fichier manifeste de votre projet pour obtenir le code XML suivant. Ensuite, si le document XML est présent, placez le code XML avec une balise de commentaire.

     Par défaut, les styles visuels ne sont pas activés.

    ```xml
    <dependency>
        <dependentAssembly>
          <assemblyIdentity
              type="win32"
              name="Microsoft.Windows.Common-Controls"
              version="6.0.0.0"
              processorArchitecture="*"
              publicKeyToken="6595b64144ccf1df"
              language="*" />
        </dependentAssembly>
      </dependency>
    ```

     Les procédures suivantes montrent comment ouvrir le fichier manifeste associé à votre projet.

    **Pour ouvrir le fichier manifeste dans un projet Visual Basic**

    1. Dans la barre de menus, choisissez **projet**,**Propriétés** _ProjectName_, où *NOM_PROJET* est le nom de votre projet WPF.

         Les pages de propriétés de votre projet WPF s’affichent.

    2. Sous l’onglet **application** , choisissez **afficher les paramètres Windows**.

         Le fichier app. manifest s’ouvre dans l' **éditeur de code**.

    **Pour ouvrir le fichier manifeste dans un projet C#**

    1. Dans la barre de menus, choisissez **projet**,**Propriétés** _ProjectName_, où *NOM_PROJET* est le nom de votre projet WPF.

         Les pages de propriétés de votre projet WPF s’affichent.

    2. Sous l’onglet **application** , notez le nom qui s’affiche dans le champ manifeste. Il s’agit du nom du manifeste associé à votre projet.

        > [!NOTE]
        > Si l’option **incorporer le manifeste avec les paramètres par défaut** ou **créer une application sans manifeste** apparaît dans le champ manifeste, les styles visuels ne sont pas activés. Si le nom d’un fichier manifeste apparaît dans le champ manifeste, passez à l’étape suivante de cette procédure.

    3. Dans **Explorateur de solutions**, choisissez **Afficher tous les fichiers** ().

         Ce bouton affiche tous les éléments de projet, y compris ceux qui ont été exclus et ceux qui sont normalement masqués. Le fichier manifeste apparaît en tant qu’élément de projet.

2. Générez et publiez votre solution. Pour plus d’informations sur la publication de la solution, consultez [Comment : publier une application ClickOnce à l’aide de l’Assistant Publication](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).

## <a name="create-a-manifest-file"></a><a name="BKMK_CreateManifest"></a> Créer un fichier manifeste

1. Collez le code XML suivant dans un fichier bloc-notes.

     Ce code XML décrit l’assembly qui contient des contrôles qui prennent en charge les styles visuels.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
     <asmv1:assembly manifestVersion="1.0"
         xmlns="urn:schemas-microsoft-com:asm.v1"
         xmlns:asmv1="urn:schemas-microsoft-com:asm.v1"
         xmlns:asmv2="urn:schemas-microsoft-com:asm.v2"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
      <dependency>
        <dependentAssembly>
          <assemblyIdentity
            type="win32"
            name="Microsoft.Windows.Common-Controls"
            version="6.0.0.0"
            processorArchitecture="*"
            publicKeyToken="6595b64144ccf1df"
            language="*" />
        </dependentAssembly>
      </dependency>
    </asmv1:assembly>
    ```

2. Dans le Bloc-notes, cliquez sur **Fichier**, puis sur **Enregistrer sous.**

3. Dans la boîte de dialogue **Enregistrer sous** , dans la liste déroulante **type** de fichier, sélectionnez **tous les fichiers**.

4. Dans la zone **nom de fichier** , nommez le fichier et ajoutez **. manifest** à la fin du nom de fichier. Par exemple : **Themes. manifest**.

5. Choisissez le bouton **Parcourir les dossiers** , sélectionnez un dossier, puis cliquez sur **Enregistrer**.

    > [!NOTE]
    > Les procédures restantes supposent que le nom de ce fichier est **Themes. manifest** et que le fichier est enregistré dans le répertoire C:\temp sur votre ordinateur.

## <a name="embed-the-manifest-file-into-the-executable-file-of-the-published-solution"></a><a name="BKMK_embedmanifest"></a> Incorporer le fichier manifeste dans le fichier exécutable de la solution publiée

1. Ouvrez l' **invite de commandes de Visual Studio**.

    Pour plus d’informations sur l’ouverture de l' **invite de commandes de Visual Studio**, consultez [invites de commandes](https://msdn.microsoft.com/library/94fcf524-9045-4993-bfb2-e2d8bad44219).

   > [!NOTE]
   > Les étapes restantes font les hypothèses suivantes sur votre solution :
   >
   > - Le nom de la solution est **MyWPFProject**.
   > - La solution se trouve dans le répertoire suivant : `%UserProfile%\Documents\Visual Studio 2010\Projects\` .
   >
   > - La solution est publiée dans le répertoire suivant : `%UserProfile%\Documents\Visual Studio 2010\Projects\publish` .
   > - La version la plus récente des fichiers d’application publiée se trouve dans le répertoire suivant : `%UserProfile%\Documents\Visual Studio 2010\Projects\publish\Application Files\WPFApp_1_0_0_0`
   >
   > Vous n’avez pas besoin d’utiliser le nom ou les emplacements de répertoire décrits ci-dessus. Le nom et les emplacements décrits ci-dessus sont utilisés uniquement pour illustrer les étapes nécessaires à la publication de votre solution.

2. À l’invite de commandes, modifiez le chemin d’accès au répertoire qui contient la version la plus récente des fichiers d’application publiée. L’exemple suivant illustre cette étape.

   ```
   cd "%UserProfile%\Documents\Visual Studio 2010\Projects\MyWPFProject\publish\Application Files\WPFApp_1_0_0_0"
   ```

3. À l’invite de commandes, exécutez la commande suivante pour incorporer le fichier manifeste dans le fichier exécutable de l’application.

   ```
   mt –manifest c:\temp\themes.manifest –outputresource:MyWPFApp.exe.deploy
   ```

## <a name="sign-the-application-and-deployment-manifests"></a><a name="BKMK_signappdeplyman"></a> Signer les manifestes d’application et de déploiement

1. À l’invite de commandes, exécutez la commande suivante pour supprimer l' `.deploy` extension du fichier exécutable dans le répertoire actif.

   ```
   ren MyWPFApp.exe.deploy MyWPFApp.exe
   ```

   > [!NOTE]
   > Cet exemple suppose qu’un seul fichier a l' `.deploy` extension de fichier. Veillez à renommer tous les fichiers de ce répertoire qui ont l' `.deploy` extension de fichier.

2. À l’invite de commandes, exécutez la commande suivante pour signer le manifeste de l’application.

   ```
   mage -u MyWPFApp.exe.manifest -cf ..\..\..\MyWPFApp_TemporaryKey.pfx
   ```

   > [!NOTE]
   > Cet exemple suppose que vous signez le manifeste à l’aide du `.pfx` fichier du projet. Si vous ne signez pas le manifeste, vous pouvez omettre le `–cf` paramètre utilisé dans cet exemple. Si vous signez le manifeste avec un certificat qui requiert un mot de passe, spécifiez l' `–password` option ( `For example: mage –u MyWPFApp.exe.manifest –cf ..\..\..\MyWPFApp_TemporaryKey.pfx – password Password` ).

3. À l’invite de commandes, exécutez la commande suivante pour ajouter l' `.deploy` extension au nom du fichier que vous avez renommé à l’étape précédente de cette procédure.

   ```
   ren MyWPFApp.exe MyWPFApp.exe.deploy
   ```

   > [!NOTE]
   > Cet exemple suppose qu’un seul fichier a une `.deploy` extension de fichier. Veillez à renommer tous les fichiers de ce répertoire ayant précédemment l' `.deploy` extension de nom de fichier.

4. À l’invite de commandes, exécutez la commande suivante pour signer le manifeste de déploiement.

   ```
   mage -u ..\..\MyWPFApp.application -appm MyWPFApp.exe.manifest -cf ..\..\..\MyWPFApp_TemporaryKey.pfx
   ```

   > [!NOTE]
   > Cet exemple suppose que vous signez le manifeste à l’aide du `.pfx` fichier du projet. Si vous ne signez pas le manifeste, vous pouvez omettre le `–cf` paramètre utilisé dans cet exemple. Si vous signez le manifeste avec un certificat qui requiert un mot de passe, spécifiez l' `–password` option, comme dans cet exemple : `For example: mage –u MyWPFApp.exe.manifest –cf ..\..\..\MyWPFApp_TemporaryKey.pfx – password Password` .

   Après avoir effectué ces étapes, vous pouvez déplacer les fichiers publiés vers l’emplacement à partir duquel vous souhaitez que les utilisateurs finaux installent l’application. Si vous envisagez de mettre à jour la solution souvent, vous pouvez déplacer ces commandes dans un script et exécuter le script chaque fois que vous publiez une nouvelle version.

## <a name="see-also"></a>Voir aussi

[Résolution des erreurs spécifiques dans les déploiements ClickOnce](../deployment/troubleshooting-specific-errors-in-clickonce-deployments.md) 
 [Vue d’ensemble](https://msdn.microsoft.com/5b5d7bb6-684f-478d-bf5f-b8d18bbcff2e) 
 des styles visuels [Invites de commandes](https://msdn.microsoft.com/library/94fcf524-9045-4993-bfb2-e2d8bad44219)
