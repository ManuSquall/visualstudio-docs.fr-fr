---
title: 'Procédure pas à pas : déploiement manuel d’une application ClickOnce | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Mage.exe, manual ClickOnce deployments
- MageUI.exe, manual ClickOnce deployments
- deploying applications [ClickOnce], manual ClickOnce deployments
- ClickOnce deployment, manually
- ClickOnce deployment, SDK tools
- manual ClickOnce deployments
- manifests [ClickOnce]
ms.assetid: ccee6551-a1b9-4ca2-8845-9c1cf4ac2560
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d02a12c9c412e4dbcc83efc96fd5d8171f0d61b6
ms.sourcegitcommit: 8589d85cc10710ef87e6363a2effa5ee5610d46a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2019
ms.locfileid: "72806816"
---
# <a name="walkthrough-manually-deploy-a-clickonce-application"></a>Procédure pas à pas : déployer manuellement une application ClickOnce
Si vous ne pouvez pas utiliser Visual Studio pour déployer votre application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], ou si vous devez utiliser des fonctionnalités de déploiement avancées, telles que le déploiement d’applications approuvées, vous devez utiliser l’outil en ligne de commande *Mage. exe* pour créer vos manifestes de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]. Cette procédure pas à pas décrit comment créer un déploiement de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] à l’aide de la version de ligne de commande (*Mage. exe*) ou de la version graphique (*MageUI. exe*) du outil Manifest Generation and Editing.

## <a name="prerequisites"></a>Configuration requise
 Cette procédure pas à pas contient des conditions préalables et des options que vous devez choisir avant de créer un déploiement.

- Installez *Mage. exe* et *MageUI. exe*.

   *Mage. exe* et *MageUI. exe* font partie du [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)]. Vous devez avoir le [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] installé ou la version du [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] inclus dans Visual Studio. Pour plus d’informations, consultez [SDK Windows](https://www.microsoft.com/download/details.aspx?id=8279) sur MSDN.

- Fournissez une application à déployer.

   Cette procédure pas à pas suppose que vous disposez d’une application Windows que vous êtes prêt à déployer. Cette application sera appelée AppToDeploy.

- Déterminez la façon dont le déploiement sera distribué.

   Les options de distribution sont les suivantes : Web, partage de fichiers ou CD. Pour plus d'informations, consultez [ClickOnce Security and Deployment](../deployment/clickonce-security-and-deployment.md).

- Déterminez si l’application requiert un niveau élevé de confiance.

   Si votre application nécessite un niveau de confiance totale (par exemple, un accès complet au système de l’utilisateur), vous pouvez utiliser l’option `-TrustLevel` de *Mage. exe* pour la définir. Si vous souhaitez définir un jeu d’autorisations personnalisé pour votre application, vous pouvez copier la section d’autorisation Internet ou intranet d’un autre manifeste, la modifier en fonction de vos besoins, puis l’ajouter au manifeste d’application à l’aide d’un éditeur de texte ou de *MageUI. exe*. Pour plus d’informations, consultez [Vue d’ensemble du déploiement d’applications approuvées](../deployment/trusted-application-deployment-overview.md).

- Obtenez un certificat Authenticode.

   Vous devez signer votre déploiement avec un certificat Authenticode. Vous pouvez générer un certificat de test à l’aide des outils Visual Studio, *MageUI. exe*ou *Makecert. exe* et *Pvk2Pfx. exe* , ou vous pouvez obtenir un certificat auprès d’une autorité de certification. Si vous choisissez d’utiliser le déploiement d’applications approuvées, vous devez également effectuer une installation unique du certificat sur tous les ordinateurs clients. Pour plus d'informations, consultez [Trusted Application Deployment Overview](../deployment/trusted-application-deployment-overview.md).

  > [!NOTE]
  > Vous pouvez également signer votre déploiement avec un certificat CNG que vous pouvez obtenir auprès d’une autorité de certification.

- Assurez-vous que l’application n’a pas de manifeste avec les informations de contrôle de compte d’utilisateur.

   Vous devez déterminer si votre application contient un manifeste avec des informations de contrôle de compte d’utilisateur (UAC, User Account Control), telles qu’un élément `<dependentAssembly>`. Pour examiner un manifeste d’application, vous pouvez utiliser l’utilitaire [sigcheck](/sysinternals/downloads/sigcheck) de Windows Sysinternals.

   Si votre application contient un manifeste avec les détails du contrôle de compte d’utilisateur, vous devez la regénérer sans les informations de contrôle de compte d’utilisateur. Pour un C# projet dans Visual Studio, ouvrez les propriétés du projet, puis sélectionnez l’onglet application. Dans la liste déroulante **manifeste** , sélectionnez **créer une application sans manifeste**. Pour un projet de Visual Basic dans Visual Studio, ouvrez les propriétés du projet, sélectionnez l’onglet application, puis cliquez sur **afficher les paramètres du contrôle de compte d’utilisateur**. Dans le fichier manifeste ouvert, supprimez tous les éléments dans l’élément `<asmv1:assembly>` unique.

- Déterminez si l’application requiert des conditions préalables sur l’ordinateur client.

   [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applications déployées à partir de Visual Studio peuvent inclure un programme d’amorçage d’installation de prérequis (*Setup. exe*) avec votre déploiement. Cette procédure pas à pas crée les deux manifestes requis pour un déploiement de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]. Vous pouvez créer un programme d’amorçage requis à l’aide de la [tâche GenerateBootstrapper,](../msbuild/generatebootstrapper-task.md).

### <a name="to-deploy-an-application-with-the-mageexe-command-line-tool"></a>Pour déployer une application à l’aide de l’outil en ligne de commande Mage. exe

1. Créez un répertoire dans lequel vous allez stocker vos fichiers de déploiement [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].

2. Dans le répertoire de déploiement que vous venez de créer, créez un sous-répertoire de version. S’il s’agit de la première fois que vous déployez l’application, nommez le sous-répertoire version **1.0.0.0**.

   > [!NOTE]
   > La version de votre déploiement peut être différente de la version de votre application.

3. Copiez tous les fichiers de votre application dans le sous-répertoire version, y compris les fichiers exécutables, les assemblys, les ressources et les fichiers de données. Si nécessaire, vous pouvez créer des sous-répertoires supplémentaires qui contiennent des fichiers supplémentaires.

4. Ouvrez la [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] ou l’invite de commandes Visual Studio et accédez au sous-répertoire version.

5. Créez le manifeste d’application avec un appel à *Mage. exe*. L’instruction suivante crée un manifeste d’application pour le code compilé pour s’exécuter sur le processeur Intel x86.

   ```cmd
   mage -New Application -Processor x86 -ToFile AppToDeploy.exe.manifest -name "My App" -Version 1.0.0.0 -FromDirectory .
   ```

   > [!NOTE]
   > Veillez à inclure le point (.) après l’option `-FromDirectory`, qui indique le répertoire actif. Si vous n’incluez pas le point, vous devez spécifier le chemin d’accès à vos fichiers d’application.

6. Signez le manifeste de l’application avec votre certificat Authenticode. Remplacez *myCert. pfx* par le chemin d’accès à votre fichier de certificat. Remplacez *passwd* par le mot de passe de votre fichier de certificat.

   ```cmd
   mage -Sign AppToDeploy.exe.manifest -CertFile mycert.pfx -Password passwd
   ```

   À partir du kit de développement logiciel (SDK) .NET Framework 4.6.2, qui est distribué avec Visual Studio et avec le SDK Windows, *Mage. exe* signe les manifestes avec CNG et les certificats Authenticode. Utilisez les mêmes paramètres de ligne de commande que les certificats Authenticode.

7. Accédez à la racine du répertoire de déploiement.

8. Générez le manifeste de déploiement à l’aide d’un appel à *Mage. exe*. Par défaut, *Mage. exe* marque votre déploiement [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] comme une application installée, afin qu’il puisse être exécuté à la fois en ligne et hors connexion. Pour rendre l’application disponible uniquement lorsque l’utilisateur est en ligne, utilisez l’option `-Install` avec la valeur `false`. Si vous utilisez la valeur par défaut et que les utilisateurs installent votre application à partir d’un site Web ou d’un partage de fichiers, assurez-vous que la valeur de l’option `-ProviderUrl` pointe vers l’emplacement du manifeste d’application sur le serveur Web ou le partage.

   ```cmd
   mage -New Deployment -Processor x86 -Install true -Publisher "My Co." -ProviderUrl "\\myServer\myShare\AppToDeploy.application" -AppManifest 1.0.0.0\AppToDeploy.exe.manifest -ToFile AppToDeploy.application
   ```

9. Signez le manifeste de déploiement avec votre certificat Authenticode ou CNG.

    ```cmd
    mage -Sign AppToDeploy.application -CertFile mycert.pfx -Password passwd
    ```

10. Copiez tous les fichiers du répertoire de déploiement vers la destination ou le support de déploiement. Il peut s’agir d’un dossier sur un site Web ou FTP, d’un partage de fichiers ou d’un CD-ROM.

11. Fournissez à vos utilisateurs l’URL, le chemin UNC ou le support physique requis pour installer votre application. Si vous fournissez une URL ou un UNC, vous devez donner à vos utilisateurs le chemin d’accès complet au manifeste de déploiement. Par exemple, si AppToDeploy est déployée sur http://webserver01/ dans le répertoire AppToDeploy, le chemin d’accès complet à l’URL est http://webserver01/AppToDeploy/AppToDeploy.application.

### <a name="to-deploy-an-application-with-the-mageuiexe-graphical-tool"></a>Pour déployer une application avec l’outil graphique MageUI. exe

1. Créez un répertoire dans lequel vous allez stocker vos fichiers de déploiement [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].

2. Dans le répertoire de déploiement que vous venez de créer, créez un sous-répertoire de version. S’il s’agit de la première fois que vous déployez l’application, nommez le sous-répertoire version **1.0.0.0**.

   > [!NOTE]
   > La version de votre déploiement est probablement différente de la version de votre application.

3. Copiez tous les fichiers de votre application dans le sous-répertoire version, y compris les fichiers exécutables, les assemblys, les ressources et les fichiers de données. Si nécessaire, vous pouvez créer des sous-répertoires supplémentaires qui contiennent des fichiers supplémentaires.

4. Démarrez l’outil graphique *MageUI. exe* .

   ```cmd
   MageUI.exe
   ```

5. Créez un nouveau manifeste d’application en sélectionnant **fichier**, **nouveau**, **manifeste d’application** dans le menu.

6. Sous l’onglet **nom** par défaut, tapez le nom et le numéro de version de ce déploiement. Spécifiez également le **processeur** pour lequel votre application est générée, par exemple x86.

7. Sélectionnez l’onglet **fichiers** , puis cliquez sur le bouton de sélection ( **...** ) en regard de la zone de texte Répertoire de l' **application** . La boîte de dialogue **Rechercher un dossier** s’affiche.

8. Sélectionnez le sous-répertoire version contenant les fichiers de votre application, puis cliquez sur **OK**.

9. Si vous déployez à partir de Internet Information Services (IIS), activez la case à cocher **lors du remplissage de l’extension. deploy dans un fichier qui n’en possède pas** .

10. Cliquez sur le bouton **Populate** pour ajouter tous les fichiers de votre application à la liste des fichiers. Si votre application contient plusieurs fichiers exécutables, marquez le fichier exécutable principal de ce déploiement en tant qu’application de démarrage en sélectionnant **point d’entrée** dans la liste déroulante **type de fichier** . (Si votre application contient un seul fichier exécutable, *MageUI. exe* la marque pour vous.)

11. Sélectionnez l’onglet **autorisations requises** et sélectionnez le niveau de confiance que votre application doit déclarer. La valeur par défaut est **FullTrust**, ce qui convient à la plupart des applications.

12. Sélectionnez **fichier**, **Enregistrer sous** dans le menu. Une boîte de dialogue Options de signature s’affiche pour vous inviter à signer le manifeste de l’application.

13. Si vous avez un certificat stocké en tant que fichier sur votre système de fichiers, utilisez l’option **signer avec le fichier de certificat** , puis sélectionnez le certificat dans le système de fichiers à l’aide du bouton de sélection ( **...** ). Tapez ensuite votre mot de passe de certificat.

     ou

     Si votre certificat est conservé dans un magasin de certificats accessible à partir de votre ordinateur, sélectionnez l’option **signer avec le certificat stocké** , puis sélectionnez le certificat dans la liste fournie.

14. Cliquez sur **OK** pour signer le manifeste de votre application. La boîte de dialogue **Enregistrer sous** s’affiche.

15. Dans la boîte de dialogue **Enregistrer sous** , spécifiez le répertoire de la version, puis cliquez sur **Enregistrer**.

16. Sélectionnez **fichier**, **nouveau**, **manifeste de déploiement** dans le menu pour créer votre manifeste de déploiement.

17. Sous l’onglet **nom** , spécifiez un nom et un numéro de version pour ce déploiement (**1.0.0.0** dans cet exemple). Spécifiez également le **processeur** pour lequel votre application est générée, par exemple x86.

18. Sélectionnez l’onglet **Description** , puis spécifiez des valeurs pour le serveur de **publication** et le **produit**. (**Product** est le nom donné à votre application dans le menu Démarrer de Windows lorsque votre application s’installe sur un ordinateur client pour une utilisation hors connexion).

19. Sélectionnez l’onglet **options de déploiement** , puis dans la zone de texte emplacement de **départ** , spécifiez l’emplacement du manifeste d’application sur le serveur Web ou le partage. Par exemple, *\\\myServer\myShare\AppToDeploy.application*.

20. Si vous avez ajouté l’extension *. deploy* à une étape précédente, sélectionnez également **utiliser l’extension de nom de fichier. deploy** ici.

21. Sélectionnez l’onglet **options de mise à jour** , puis spécifiez la fréquence à laquelle vous souhaitez que cette application soit mise à jour. Si votre application utilise <xref:System.Deployment.Application.UpdateCheckInfo> pour rechercher des mises à jour, désactivez la case à cocher **cette application doit vérifier les mises à jour** .

22. Sélectionnez l’onglet Référence de l' **application** , puis cliquez sur le bouton **Sélectionner le manifeste** . Une boîte de dialogue Ouvrir s’affiche.

23. Sélectionnez le manifeste d’application que vous avez créé précédemment, puis cliquez sur **ouvrir**.

24. Sélectionnez **fichier**, **Enregistrer sous** dans le menu. Une boîte de dialogue **options de signature** s’affiche pour vous inviter à signer le manifeste de déploiement.

25. Si vous avez un certificat stocké en tant que fichier sur votre système de fichiers, utilisez l’option **signer avec le fichier de certificat** , puis sélectionnez le certificat dans le système de fichiers à l’aide du bouton de sélection ( **...** ). Tapez ensuite votre mot de passe de certificat.

     ou

     Si votre certificat est conservé dans un magasin de certificats accessible à partir de votre ordinateur, sélectionnez l’option **signer avec le certificat stocké** , puis sélectionnez le certificat dans la liste fournie.

26. Cliquez sur **OK** pour signer votre manifeste de déploiement. La boîte de dialogue **Enregistrer sous** s’affiche.

27. Dans la boîte de dialogue **Enregistrer sous** , déplacez un répertoire vers la racine de votre déploiement, puis cliquez sur **Enregistrer**.

28. Copiez tous les fichiers du répertoire de déploiement vers la destination ou le support de déploiement. Il peut s’agir d’un dossier sur un site Web ou FTP, d’un partage de fichiers ou d’un CD-ROM.

29. Fournissez à vos utilisateurs l’URL, le chemin UNC ou le support physique requis pour installer votre application. Si vous fournissez une URL ou un UNC, vous devez donner à vos utilisateurs le chemin d’accès complet du manifeste de déploiement. Par exemple, si AppToDeploy est déployée sur http://webserver01/ dans le répertoire AppToDeploy, le chemin d’accès complet à l’URL est http://webserver01/AppToDeploy/AppToDeploy.application.

## <a name="next-steps"></a>Étapes suivantes
 Lorsque vous devez déployer une nouvelle version de l’application, créez un répertoire nommé d’après la nouvelle version (par exemple, 1.0.0.1) et copiez les nouveaux fichiers d’application dans le nouveau répertoire. Ensuite, vous devez suivre les étapes précédentes pour créer et signer un nouveau manifeste d’application, et pour mettre à jour et signer le manifeste de déploiement. Veillez à spécifier la même version supérieure dans le `-New` *Mage. exe* et les appels de `-Update`, car [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] met à jour uniquement les versions plus récentes, avec l’entier le plus à gauche le plus significatif. Si vous avez utilisé *MageUI. exe*, vous pouvez mettre à jour le manifeste de déploiement en l’ouvrant, en sélectionnant l’onglet Référence de l' **application** , en cliquant sur le bouton **Sélectionner un manifeste** , puis en sélectionnant le manifeste d’application mis à jour.

## <a name="see-also"></a>Voir aussi
- [Mage.exe (outil Manifest Generation and Editing)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)
- [MageUI.exe (outil Manifest Generation and Editing, client graphique)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)
- [Publier des applications ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Manifeste de déploiement ClickOnce](../deployment/clickonce-deployment-manifest.md)
- [Manifeste d’application ClickOnce](../deployment/clickonce-application-manifest.md)