---
title: 'Procédure pas à pas : déploiement manuel d’une application ClickOnce | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
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
caps.latest.revision: 51
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cba55c9f4a8f7436b97099b6b548b916ea6e5ecb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75844941"
---
# <a name="walkthrough-manually-deploying-a-clickonce-application"></a>Procédure pas à pas : déploiement manuel d'une application ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Si vous ne pouvez pas utiliser Visual Studio pour déployer votre [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] application, ou si vous devez utiliser des fonctionnalités de déploiement avancées, telles que le déploiement d’applications approuvées, vous devez utiliser l’outil de ligne de commande Mage.exe pour créer vos [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifestes. Cette procédure pas à pas décrit comment créer un déploiement à l' [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aide de la version de ligne de commande (Mage.exe) ou de la version graphique (MageUI.exe) du outil Manifest Generation and Editing.  
  
## <a name="prerequisites"></a>Prérequis  
 Cette procédure pas à pas contient des conditions préalables et des options que vous devez choisir avant de créer un déploiement.  
  
- Installez Mage.exe et MageUI.exe.  
  
     Mage.exe et MageUI.exe font partie du [!INCLUDE[winsdklong](../includes/winsdklong-md.md)] . Vous devez avoir [!INCLUDE[winsdkshort](../includes/winsdkshort-md.md)] installé ou la version de [!INCLUDE[winsdkshort](../includes/winsdkshort-md.md)] inclus dans Visual Studio. Pour plus d’informations, consultez [SDK Windows](https://msdn.microsoft.com/windowsserver/bb980924.aspx) sur MSDN.  
  
- Fournissez une application à déployer.  
  
     Cette procédure pas à pas suppose que vous disposez d’une application Windows que vous êtes prêt à déployer. Cette application sera appelée AppToDeploy.  
  
- Déterminez la façon dont le déploiement sera distribué.  
  
     Les options de distribution sont les suivantes : Web, partage de fichiers ou CD. Pour plus d'informations, consultez [ClickOnce Security and Deployment](../deployment/clickonce-security-and-deployment.md).  
  
- Déterminez si l’application requiert un niveau élevé de confiance.  
  
     Si votre application nécessite un niveau de confiance totale (par exemple, un accès complet au système de l’utilisateur), vous pouvez utiliser l' `-TrustLevel` option de Mage.exe pour la définir. Si vous souhaitez définir un jeu d’autorisations personnalisé pour votre application, vous pouvez copier la section d’autorisation Internet ou intranet à partir d’un autre manifeste, la modifier en fonction de vos besoins, puis l’ajouter au manifeste d’application à l’aide d’un éditeur de texte ou d’un MageUI.exe. Pour plus d'informations, consultez [Trusted Application Deployment Overview](../deployment/trusted-application-deployment-overview.md).  
  
- Obtenez un certificat Authenticode.  
  
     Vous devez signer votre déploiement avec un certificat Authenticode. Vous pouvez générer un certificat de test à l’aide de Visual Studio, MageUI.exe ou MakeCert.exe et Pvk2Pfx.exe outils, ou vous pouvez obtenir un certificat auprès d’une autorité de certification. Si vous choisissez d’utiliser le déploiement d’applications approuvées, vous devez également effectuer une installation unique du certificat sur tous les ordinateurs clients. Pour plus d'informations, consultez [Trusted Application Deployment Overview](../deployment/trusted-application-deployment-overview.md).  
  
    > [!NOTE]
    > Vous pouvez également signer votre déploiement avec un certificat CNG que vous pouvez obtenir auprès d’une autorité de certification.  
  
- Assurez-vous que l’application n’a pas de manifeste avec les informations de contrôle de compte d’utilisateur.  
  
     Vous devez déterminer si votre application contient un manifeste avec des informations de contrôle de compte d’utilisateur (UAC), telles qu’un `<dependentAssembly>` élément. Pour examiner un manifeste d’application, vous pouvez utiliser l’utilitaire [sigcheck](https://technet.microsoft.com/sysinternals/bb897441.aspx) de Windows Sysinternals.  
  
     Si votre application contient un manifeste avec les détails du contrôle de compte d’utilisateur, vous devez la regénérer sans les informations de contrôle de compte d’utilisateur. Pour un projet C# dans Visual Studio, ouvrez les propriétés du projet, puis sélectionnez l’onglet application. Dans la liste déroulante **manifeste** , sélectionnez **créer une application sans manifeste**. Pour un projet de Visual Basic dans Visual Studio, ouvrez les propriétés du projet, sélectionnez l’onglet application, puis cliquez sur **afficher les paramètres du contrôle de compte d’utilisateur**. Dans le fichier manifeste ouvert, supprimez tous les éléments dans l' `<asmv1:assembly>` élément unique.  
  
- Déterminez si l’application requiert des conditions préalables sur l’ordinateur client.  
  
     [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] les applications déployées à partir de Visual Studio peuvent inclure un programme d’amorçage d’installation de prérequis (setup.exe) avec votre déploiement. Cette procédure pas à pas crée les deux manifestes requis pour un [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] déploiement. Vous pouvez créer un programme d’amorçage requis à l’aide de la [tâche GenerateBootstrapper,](../msbuild/generatebootstrapper-task.md).  
  
### <a name="to-deploy-an-application-with-the-mageexe-command-line-tool"></a>Pour déployer une application avec l’outil en ligne de commande Mage.exe  
  
1. Créez un répertoire dans lequel vous allez stocker vos [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] fichiers de déploiement.  
  
2. Dans le répertoire de déploiement que vous venez de créer, créez un sous-répertoire de version. S’il s’agit de la première fois que vous déployez l’application, nommez le sous-répertoire version **1.0.0.0**.  
  
    > [!NOTE]
    > La version de votre déploiement peut être différente de la version de votre application.  
  
3. Copiez tous les fichiers de votre application dans le sous-répertoire version, y compris les fichiers exécutables, les assemblys, les ressources et les fichiers de données. Si nécessaire, vous pouvez créer des sous-répertoires supplémentaires qui contiennent des fichiers supplémentaires.  
  
4. Ouvrez l' [!INCLUDE[winsdkshort](../includes/winsdkshort-md.md)] invite de commandes ou Visual Studio et accédez au sous-répertoire version.  
  
5. Créez le manifeste d’application à l’aide d’un appel à Mage.exe. L’instruction suivante crée un manifeste d’application pour le code compilé pour s’exécuter sur le processeur Intel x86.  
  
    ```  
    mage -New Application -Processor x86 -ToFile AppToDeploy.exe.manifest -name "My App" -Version 1.0.0.0 -FromDirectory .   
    ```  
  
    > [!NOTE]
    > Veillez à inclure le point (.) après l' `-FromDirectory` option, qui indique le répertoire actif. Si vous n’incluez pas le point, vous devez spécifier le chemin d’accès à vos fichiers d’application.  
  
6. Signez le manifeste de l’application avec votre certificat Authenticode. Remplacez *myCert. pfx* par le chemin d’accès à votre fichier de certificat. Remplacez *passwd* par le mot de passe de votre fichier de certificat.  
  
    ```  
    mage -Sign AppToDeploy.exe.manifest -CertFile mycert.pfx -Password passwd  
    ```  
  
     Pour signer le manifeste d’application avec un certificat CNG, utilisez la commande suivante. Remplacez *cngCert. pfx* par le chemin d’accès à votre fichier de certificat.  
  
    ```  
    mage -Sign AppToDeploy.exe.manifest -CertFile cngCert.pfx  
    ```  
  
7. Accédez à la racine du répertoire de déploiement.  
  
8. Générez le manifeste de déploiement à l’aide d’un appel à Mage.exe. Par défaut, Mage.exe marque votre [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] déploiement comme une application installée, afin qu’il puisse être exécuté à la fois en ligne et hors connexion. Pour rendre l’application disponible uniquement lorsque l’utilisateur est en ligne, utilisez l' `-Install` option avec la valeur `false` . Si vous utilisez la valeur par défaut et que les utilisateurs installent votre application à partir d’un site Web ou d’un partage de fichiers, assurez-vous que la valeur de l' `-ProviderUrl` option pointe vers l’emplacement du manifeste d’application sur le serveur Web ou le partage.  
  
    ```  
    mage -New Deployment -Processor x86 -Install true -Publisher "My Co." -ProviderUrl "\\myServer\myShare\AppToDeploy.application" -AppManifest 1.0.0.0\AppToDeploy.exe.manifest -ToFile AppToDeploy.application  
    ```  
  
9. Signez le manifeste de déploiement avec votre certificat Authenticode ou CNG.  
  
    ```  
    mage -Sign AppToDeploy.application -CertFile mycert.pfx -Password passwd  
    ```  
  
     or  
  
    ```  
    mage -Sign AppToDeploy.exe.manifest -CertFile cngCert.pfx  
    ```  
  
10. Copiez tous les fichiers du répertoire de déploiement vers la destination ou le support de déploiement. Il peut s’agir d’un dossier sur un site Web ou FTP, d’un partage de fichiers ou d’un CD-ROM.  
  
11. Fournissez à vos utilisateurs l’URL, le chemin UNC ou le support physique requis pour installer votre application. Si vous fournissez une URL ou un UNC, vous devez donner à vos utilisateurs le chemin d’accès complet au manifeste de déploiement. Par exemple, si AppToDeploy est déployé http://webserver01/ dans le répertoire AppToDeploy, le chemin d’accès complet à l’URL est http://webserver01/AppToDeploy/AppToDeploy.application .  
  
### <a name="to-deploy-an-application-with-the-mageuiexe-graphical-tool"></a>Pour déployer une application avec l’outil graphique MageUI.exe  
  
1. Créez un répertoire dans lequel vous allez stocker vos [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] fichiers de déploiement.  
  
2. Dans le répertoire de déploiement que vous venez de créer, créez un sous-répertoire de version. S’il s’agit de la première fois que vous déployez l’application, nommez le sous-répertoire version **1.0.0.0**.  
  
    > [!NOTE]
    > La version de votre déploiement est probablement différente de la version de votre application.  
  
3. Copiez tous les fichiers de votre application dans le sous-répertoire version, y compris les fichiers exécutables, les assemblys, les ressources et les fichiers de données. Si nécessaire, vous pouvez créer des sous-répertoires supplémentaires qui contiennent des fichiers supplémentaires.  
  
4. Démarrez l’outil graphique MageUI.exe.  
  
    ```  
    MageUI.exe  
    ```  
  
5. Créez un nouveau manifeste d’application en sélectionnant **fichier**, **nouveau**, **manifeste d’application** dans le menu.  
  
6. Sous l’onglet **nom** par défaut, tapez le nom et le numéro de version de ce déploiement. Spécifiez également le **processeur** pour lequel votre application est générée, par exemple x86.  
  
7. Sélectionnez l’onglet **fichiers** , puis cliquez sur le bouton de sélection (**...**) en regard de la zone de texte Répertoire de l' **application** . La boîte de dialogue Rechercher un dossier s’affiche.  
  
8. Sélectionnez le sous-répertoire version contenant les fichiers de votre application, puis cliquez sur **OK**.  
  
9. Si vous déployez à partir de Internet Information Services (IIS), activez la case à cocher **lors du remplissage de l’extension. deploy dans un fichier qui n’en possède pas** .  
  
10. Cliquez sur le bouton **Populate** pour ajouter tous les fichiers de votre application à la liste des fichiers. Si votre application contient plusieurs fichiers exécutables, marquez le fichier exécutable principal de ce déploiement en tant qu’application de démarrage en sélectionnant **point d’entrée** dans la liste déroulante **type de fichier** . (Si votre application contient un seul fichier exécutable, MageUI.exe le marque pour vous.)  
  
11. Sélectionnez l’onglet **autorisations requises** et sélectionnez le niveau de confiance que votre application doit déclarer. La valeur par défaut est **FullTrust**, ce qui convient à la plupart des applications.  
  
12. Sélectionnez **fichier**, **Enregistrer sous** dans le menu. Une boîte de dialogue Options de signature s’affiche pour vous inviter à signer le manifeste de l’application.  
  
13. Si vous avez un certificat stocké en tant que fichier sur votre système de fichiers, utilisez l’option **signer avec le fichier de certificat** , puis sélectionnez le certificat dans le système de fichiers à l’aide du bouton de sélection (**...**). Tapez ensuite votre mot de passe de certificat.  
  
     -ou-  
  
     Si votre certificat est conservé dans un magasin de certificats accessible à partir de votre ordinateur, sélectionnez l’option **signer avec le certificat stocké** , puis sélectionnez le certificat dans la liste fournie.  
  
14. Cliquez sur **OK** pour signer le manifeste de votre application. La boîte de dialogue Enregistrer sous s'affiche.  
  
15. Dans la boîte de dialogue Enregistrer sous, spécifiez le répertoire de la version, puis cliquez sur **Enregistrer**.  
  
16. Sélectionnez **fichier**, **nouveau**, **manifeste de déploiement** dans le menu pour créer votre manifeste de déploiement.  
  
17. Sous l’onglet **nom** , spécifiez un nom et un numéro de version pour ce déploiement (**1.0.0.0** dans cet exemple). Spécifiez également le **processeur** pour lequel votre application est générée, par exemple x86.  
  
18. Sélectionnez l’onglet **Description** , puis spécifiez des valeurs pour le serveur de **publication** et le **produit**. (**Product** est le nom donné à votre application dans le menu Démarrer de Windows lorsque votre application s’installe sur un ordinateur client pour une utilisation hors connexion).  
  
19. Sélectionnez l’onglet **options de déploiement** , puis dans la zone de texte emplacement de **départ** , spécifiez l’emplacement du manifeste d’application sur le serveur Web ou le partage. Par exemple, \\ \myServer\myShare\AppToDeploy.application.  
  
20. Si vous avez ajouté l’extension. deploy à une étape précédente, sélectionnez également **utiliser l’extension de nom de fichier. deploy** ici.  
  
21. Sélectionnez l’onglet **options de mise à jour** , puis spécifiez la fréquence à laquelle vous souhaitez que cette application soit mise à jour. Si votre application utilise <xref:System.Deployment.Application.UpdateCheckInfo> pour rechercher des mises à jour proprement dites, désactivez la case à cocher **cette application doit vérifier les mises à jour** .  
  
22. Sélectionnez l’onglet Référence de l' **application** , puis cliquez sur le bouton **Sélectionner le manifeste** . Une boîte de dialogue Ouvrir s’affiche.  
  
23. Sélectionnez le manifeste d’application que vous avez créé précédemment, puis cliquez sur **ouvrir**.  
  
24. Sélectionnez **fichier**, **Enregistrer sous** dans le menu. Une boîte de dialogue Options de signature s’affiche pour vous inviter à signer le manifeste de déploiement.  
  
25. Si vous avez un certificat stocké en tant que fichier sur votre système de fichiers, utilisez l’option **signer avec le fichier de certificat** , puis sélectionnez le certificat dans le système de fichiers à l’aide du bouton de sélection (**...**). Tapez ensuite votre mot de passe de certificat.  
  
     -ou-  
  
     Si votre certificat est conservé dans un magasin de certificats accessible à partir de votre ordinateur, sélectionnez l’option **signer avec le certificat stocké** , puis sélectionnez le certificat dans la liste fournie.  
  
26. Cliquez sur **OK** pour signer votre manifeste de déploiement. La boîte de dialogue Enregistrer sous s'affiche.  
  
27. Dans la boîte de dialogue **Enregistrer sous** , déplacez un répertoire vers la racine de votre déploiement, puis cliquez sur **Enregistrer**.  
  
28. Copiez tous les fichiers du répertoire de déploiement vers la destination ou le support de déploiement. Il peut s’agir d’un dossier sur un site Web ou FTP, d’un partage de fichiers ou d’un CD-ROM.  
  
29. Fournissez à vos utilisateurs l’URL, le chemin UNC ou le support physique requis pour installer votre application. Si vous fournissez une URL ou un UNC, vous devez donner à vos utilisateurs le chemin d’accès complet du manifeste de déploiement. Par exemple, si AppToDeploy est déployé http://webserver01/ dans le répertoire AppToDeploy, le chemin d’accès complet à l’URL est http://webserver01/AppToDeploy/AppToDeploy.application .  
  
## <a name="next-steps"></a>Étapes suivantes  
 Lorsque vous devez déployer une nouvelle version de l’application, créez un répertoire nommé d’après la nouvelle version (par exemple, 1.0.0.1) et copiez les nouveaux fichiers d’application dans le nouveau répertoire. Ensuite, vous devez suivre les étapes précédentes pour créer et signer un nouveau manifeste d’application, et pour mettre à jour et signer le manifeste de déploiement. Veillez à spécifier la même version supérieure dans le Mage.exe `-New` et les `–Update` appels, car [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] seules les versions plus récentes sont mises à jour, avec l’entier le plus à gauche le plus significatif. Si vous avez utilisé MageUI.exe, vous pouvez mettre à jour le manifeste de déploiement en l’ouvrant, en sélectionnant l’onglet Référence de l' **application** , en cliquant sur le bouton **Sélectionner un manifeste** , puis en sélectionnant le manifeste d’application mis à jour.  
  
## <a name="see-also"></a>Voir aussi  
 [Mage.exe (Outil Manifest Generation and Editing)](https://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1)   
 [MageUI.exe (Outil Manifest Generation and Editing, client graphique)](https://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14)   
 [Publication d’applications ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Manifeste de déploiement ClickOnce](../deployment/clickonce-deployment-manifest.md)   
 [Manifeste d’application ClickOnce](../deployment/clickonce-application-manifest.md)
