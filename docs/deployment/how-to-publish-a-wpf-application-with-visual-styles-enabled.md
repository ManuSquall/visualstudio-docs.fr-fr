---
title: 'Procédure : Publier une Application WPF avec les Styles visuels activés | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 73b22b02-fc75-42aa-82d3-51fdcaf8e5c8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4ed9a9a349f2496343a9a9828cd436d8d4015aa9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62898345"
---
# <a name="how-to-publish-a-wpf-application-with-visual-styles-enabled"></a>Procédure : Publier une application WPF avec les styles visuels activés

Styles visuels activer l’apparence des contrôles communs à changer en fonction du thème choisi par l’utilisateur. Par défaut, les styles visuels ne sont pas activés pour les applications Windows Presentation Foundation (WPF), vous devez les activer manuellement. Toutefois, l’activation des styles visuels pour une application WPF, puis publiez la solution provoque une erreur. Cette rubrique décrit comment résoudre cette erreur et le processus de publication d’une application WPF avec les styles visuels sont activés. Pour plus d’informations sur les styles visuels, consultez [vue d’ensemble de styles visuels](/windows/desktop/Controls/visual-styles-overview). Pour plus d’informations sur le message d’erreur, consultez [résoudre les erreurs spécifiques dans les déploiements ClickOnce](../deployment/troubleshooting-specific-errors-in-clickonce-deployments.md).

 Pour résoudre l’erreur et publiez la solution, vous devez effectuer les tâches suivantes :

- [Publiez la solution sans styles visuels activés](#publish-the-solution-without-visual-styles-enabled).

- [Créez un fichier manifeste](#create-a-manifest-file).

- [Incorporer le fichier manifest dans le fichier exécutable de la solution publiée](#embed-the-manifest-file-into-the-executable-file-of-the-published-solution).

- [Signer les manifestes d’application et de déploiement](#sign-the-application-and-deployment-manifests).

  Ensuite, vous pouvez déplacer les fichiers publiés à l’emplacement à partir duquel vous souhaitez que les utilisateurs finaux pour installer l’application.

## <a name="publish-the-solution-without-visual-styles-enabled"></a>Publiez la solution sans styles visuels activés

1. Assurez-vous que votre projet n’a pas de styles visuels sont activés. Vérifiez tout d’abord, le fichier manifeste du projet pour le code XML suivant. Ensuite, si le code XML est présent, placez le code XML avec une balise de commentaire.

     Par défaut, les styles visuels ne sont pas activés.

    ```xml
    <dependency>
        <dependentAssembly>
            <assemblyIdentity type="win32" name="Microsoft.Windows.Common-Controls" version="6.0.0.0" processorArchitecture="*" publicKeyToken="6595b64144ccf1df" language="*" />
        </dependentAssembly>
    </dependency>
    ```

     Les procédures suivantes montrent comment ouvrir le fichier manifest associé à votre projet.

    **Pour ouvrir le fichier manifeste dans un projet Visual Basic**

    1. Dans la barre de menus, choisissez **projet**, *nom_projet* **propriétés**, où *nom_projet* est le nom de votre projet WPF.

         Les pages de propriétés pour votre projet WPF s’affichent.

    2. Sur le **Application** , choisir **afficher les paramètres Windows**.

         Le fichier App.manifest s’ouvre dans le **éditeur de Code**.

    **Pour ouvrir le fichier manifeste dans un projet c#**

    1. Dans la barre de menus, choisissez **projet**, *nom_projet* **propriétés**, où *nom_projet* est le nom de votre projet WPF.

         Les pages de propriétés pour votre projet WPF s’affichent.

    2. Sur le **Application** onglet, prenez note du nom qui apparaît dans le champ de manifeste. Il s’agit du nom du manifeste qui est associé à votre projet.

        > [!NOTE]
        > Si **manifeste incorporé avec les paramètres par défaut** ou **créer une application sans manifeste** apparaissent dans le champ de manifeste, les styles visuels ne sont pas activés. Si le nom d’un fichier manifeste apparaît dans le champ de manifeste, passez à l’étape suivante de cette procédure.

    3. Dans l’**Explorateur de solutions**, choisissez **Afficher tous les fichiers**.

         Ce bouton affiche tous les éléments de projet, y compris ceux qui ont été exclus et ceux qui sont normalement masqués. Le fichier manifest apparaît comme un élément de projet.

2. Générez et publiez votre solution. Pour plus d’informations sur la publication de la solution, consultez [Comment : Publier une application ClickOnce à l’aide de l’Assistant Publication](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).

## <a name="create-a-manifest-file"></a>Créez un fichier manifeste

1. Collez le code XML suivant dans un fichier du bloc-notes.

     Ce fichier XML décrit l’assembly qui contient les contrôles qui prennent en charge les styles visuels.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <asmv1:assembly manifestVersion="1.0"
        xmlns="urn:schemas-microsoft-com:asm.v1"
        xmlns:asmv1="urn:schemas-microsoft-com:asm.v1"
        xmlns:asmv2="urn:schemas-microsoft-com:asm.v2"
        xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
        <dependency>
            <dependentAssembly>
                <assemblyIdentity type="win32" name="Microsoft.Windows.Common-Controls" version="6.0.0.0" processorArchitecture="*" publicKeyToken="6595b64144ccf1df" language="*" />
            </dependentAssembly>
        </dependency>
    </asmv1:assembly>
    ```

2. Dans le bloc-notes, cliquez sur **fichier**, puis cliquez sur **Enregistrer sous**.

3. Dans le **enregistrer en tant que** boîte de dialogue le **enregistrer en tant que type** liste déroulante, sélectionnez **tous les fichiers**.

4. Dans le **nom de fichier** boîte, nommez le fichier et ajoutez *.manifest* à la fin du nom de fichier. Par exemple : *themes.manifest*.

5. Choisissez le **parcourir les dossiers** bouton, sélectionnez n’importe quel dossier, puis cliquez sur **enregistrer**.

    > [!NOTE]
    > Les procédures restantes supposent que le nom de ce fichier est *themes.manifest* et que le fichier est enregistré dans le *C:\temp* répertoire sur votre ordinateur.

## <a name="embed-the-manifest-file-into-the-executable-file-of-the-published-solution"></a>Incorporer le fichier manifest dans le fichier exécutable de la solution publiée

1. Ouvrez le **invite de commandes de Visual Studio**.

    Pour plus d’informations sur la façon d’ouvrir le **invite de commandes Visual Studio**, consultez [invites de commandes](/dotnet/framework/tools/developer-command-prompt-for-vs).

   > [!NOTE]
   > Les étapes restantes des hypothèses suivantes relatives à votre solution :
   >
   > - Le nom de la solution est **MyWPFProject**.
   > - La solution se trouve dans le répertoire suivant : `%UserProfile%\Documents\Visual Studio 2010\Projects\`.
   >
   > - La solution est publiée dans le répertoire suivant : `%UserProfile%\Documents\Visual Studio 2010\Projects\publish`.
   > - La version la plus récente des fichiers d’application publiée se trouve dans le répertoire suivant : `%UserProfile%\Documents\Visual Studio 2010\Projects\publish\Application Files\WPFApp_1_0_0_0`
   >
   > Il est inutile d’utiliser le nom ou les emplacements de répertoire décrites ci-dessus. Le nom et les emplacements décrits ci-dessus sont utilisés uniquement pour illustrer les étapes requises pour publier votre solution.

2. À l’invite de commandes, modifiez le chemin d’accès au répertoire qui contient la version la plus récente des fichiers d’application publiée. L’exemple suivant illustre cette étape.

   ```cmd
   cd "%UserProfile%\Documents\Visual Studio 2010\Projects\MyWPFProject\publish\Application Files\WPFApp_1_0_0_0"
   ```

3. À l’invite de commandes, exécutez la commande suivante pour incorporer le fichier manifest dans le fichier exécutable de l’application.

   ```cmd
   mt -manifest c:\temp\themes.manifest -outputresource:MyWPFApp.exe.deploy
   ```

## <a name="sign-the-application-and-deployment-manifests"></a>Signer les manifestes d’application et de déploiement

1. À l’invite de commandes, exécutez la commande suivante pour supprimer le *.deploy* extension à partir du fichier exécutable dans le répertoire actif.

   ```cmd
   ren MyWPFApp.exe.deploy MyWPFApp.exe
   ```

   > [!NOTE]
   > Cet exemple ne suppose qu’un seul fichier possède le *.deploy* extension de fichier. Assurez-vous que vous renommez tous les fichiers dans ce répertoire ayant le *.deploy* extension de fichier.

2. À l’invite de commandes, exécutez la commande suivante pour signer le manifeste d’application.

   ```cmd
   mage -u MyWPFApp.exe.manifest -cf ..\..\..\MyWPFApp_TemporaryKey.pfx
   ```

   > [!NOTE]
   > Cet exemple suppose que vous signez le manifeste à l’aide de la *.pfx* fichier du projet. Si vous signez pas le manifeste, vous pouvez omettre le `-cf` paramètre qui est utilisé dans cet exemple. Si vous signez le manifeste avec un certificat qui requiert un mot de passe, spécifiez le `-password` option (`For example: mage -u MyWPFApp.exe.manifest -cf ..\..\..\MyWPFApp_TemporaryKey.pfx - password Password`).

3. À l’invite de commandes, exécutez la commande suivante pour ajouter le *.deploy* extension pour le nom du fichier que vous avez renommé à l’étape précédente de cette procédure.

   ```
   ren MyWPFApp.exe MyWPFApp.exe.deploy
   ```

   > [!NOTE]
   > Cet exemple ne suppose qu’un seul fichier avait une *.deploy* extension de fichier. Assurez-vous que vous renommez tous les fichiers dans ce répertoire qui avait précédemment le *.deploy* extension de nom de fichier.

4. À l’invite de commandes, exécutez la commande suivante pour signer le manifeste de déploiement.

   ```
   mage -u ..\..\MyWPFApp.application -appm MyWPFApp.exe.manifest -cf ..\..\..\MyWPFApp_TemporaryKey.pfx
   ```

   > [!NOTE]
   > Cet exemple suppose que vous signez le manifeste à l’aide de la *.pfx* fichier du projet. Si vous signez pas le manifeste, vous pouvez omettre le `-cf` paramètre qui est utilisé dans cet exemple. Si vous signez le manifeste avec un certificat qui requiert un mot de passe, spécifiez le `-password` option, comme dans cet exemple :`For example: mage -u MyWPFApp.exe.manifest -cf ..\..\..\MyWPFApp_TemporaryKey.pfx - password Password`.

   Une fois que vous avez effectué ces étapes, vous pouvez déplacer les fichiers publiés à l’emplacement à partir duquel vous souhaitez que les utilisateurs finaux pour installer l’application. Si vous envisagez de mettre à jour la solution souvent, vous pouvez déplacer ces commandes dans un script et exécuter le script chaque fois que vous publiez une nouvelle version.

## <a name="see-also"></a>Voir aussi

-[Dépannage d’erreurs spécifiques dans les déploiements ClickOnce](../deployment/troubleshooting-specific-errors-in-clickonce-deployments.md)
- [Vue d’ensemble de Styles visuels](/windows/desktop/Controls/visual-styles-overview)
- [Activation des styles visuels](/windows/desktop/Controls/cookbook-overview)
- [Invites de commandes](/dotnet/framework/tools/developer-command-prompt-for-vs)
