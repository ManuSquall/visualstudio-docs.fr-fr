---
title: "Walkthrough: Manually Deploying a ClickOnce Application | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Mage.exe, manual ClickOnce deployments"
  - "MageUI.exe, manual ClickOnce deployments"
  - "deploying applications [ClickOnce], manual ClickOnce deployments"
  - "ClickOnce deployment, manually"
  - "ClickOnce deployment, SDK tools"
  - "manual ClickOnce deployments"
  - "manifests [ClickOnce]"
ms.assetid: ccee6551-a1b9-4ca2-8845-9c1cf4ac2560
caps.latest.revision: 49
caps.handback.revision: 47
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Walkthrough: Manually Deploying a ClickOnce Application
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Si vous ne pouvez pas utiliser Visual Studio pour déployer votre application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], ou si vous devez utiliser des fonctionnalités de déploiement avancées telles que le déploiement d'applications approuvées, il est recommandé d'utiliser l'outil en ligne de commande Mage.exe pour créer vos manifestes [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  Cette procédure pas à pas décrit comment créer un déploiement [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] complet à l'aide de la version en ligne de commande \(Mage.exe\) ou graphique \(MageUI.exe\) de l'outil Manifest Generation and Editing.  
  
## Composants requis  
 Cette procédure pas à pas requiert des composants et des options que vous devez choisir avant de générer un déploiement.  
  
-   Installez Mage.exe et MageUI.exe.  
  
     Mage.exe et MageUI.exe font partie du [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)].  Le [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] doit être installé ou vous devez utiliser la version du [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] incluse avec Visual Studio.  Pour plus d'informations, consultez [Windows SDK](http://go.microsoft.com/fwlink/?LinkId=158044) sur le site MSDN.  
  
-   Fournissez une application à déployer.  
  
     Cette procédure pas à pas suppose que vous avez une application Windows que vous êtes prêt à déployer.  Cette application sera référencée sous le nom AppToDeploy.  
  
-   Déterminez comment le déploiement sera distribué.  
  
     Les options de distribution sont les suivantes : Web, partage de fichiers ou CD.  Pour plus d'informations, consultez [ClickOnce Security and Deployment](../deployment/clickonce-security-and-deployment.md).  
  
-   Déterminez si l'application requiert un niveau élevé d'approbation.  
  
     Si votre application exige une confiance totale, par exemple, un accès complet au système de l'utilisateur, vous pouvez utiliser l'option `-TrustLevel` de Mage.exe pour la définir.  Si vous souhaitez définir un jeu d'autorisations personnalisé pour votre application, vous pouvez copier la section des autorisations intranet ou Internet d'un autre manifeste, la modifier selon vos besoins et l'ajouter au manifeste d'application à l'aide d'un éditeur de texte ou de MageUI.exe.  Pour plus d'informations, consultez [Vue d'ensemble du déploiement d'applications approuvées](../deployment/trusted-application-deployment-overview.md).  
  
-   Obtenez un certificat Authenticode.  
  
     Vous devez signer votre déploiement avec un certificat Authenticode.  Vous pouvez générer un certificat de test à l'aide de Visual Studio, MageUI.exe ou MakeCert.exe et des outils Pvk2Pfx.exe, ou vous pouvez obtenir un certificat d'une autorité de certification.  Si vous choisissez d'utiliser le déploiement d'applications approuvées, vous devez également effectuer une installation unique du certificat sur tous les ordinateurs client.  Pour plus d'informations, consultez [Vue d'ensemble du déploiement d'applications approuvées](../deployment/trusted-application-deployment-overview.md).  
  
-   Assurez\-vous que l'application n'a pas de manifeste avec les informations de contrôle de compte d'utilisateur.  
  
     Vous devez déterminer si votre application contient un manifeste avec des informations de contrôle de compte d'utilisateur \(UAC, User Account Control\), telles qu'un élément `<dependentAssembly>`.  Pour examiner un manifeste d'application, vous pouvez utiliser l'utilitaire Windows Sysinternals [Sigcheck](http://go.microsoft.com/fwlink/?LinkId=158035).  
  
     Si votre application contient un manifeste avec des détails de contrôle de compte d'utilisateur, vous le devez régénérer sans les informations UAC.  Pour un projet C\# dans Visual Studio, ouvrez les propriétés du projet et sélectionnez l'onglet Application.  Dans la liste déroulante **Manifeste**, sélectionnez **Créer une application sans fichier manifeste**.  Pour un projet Visual Basic dans Visual Studio, ouvrez les propriétés du projet, sélectionnez l'onglet Application et cliquez sur **Afficher les paramètres UAC**.  Dans le fichier manifeste ouvert, supprimez tous les éléments dans l'élément `<asmv1:assembly>` unique.  
  
-   Déterminez si l'application requiert certains composants sur l'ordinateur client.  
  
     Les applications [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] déployées à partir de Visual Studio peuvent inclure un programme d'amorçage d'installation de composants requis \(setup.exe\) avec votre déploiement.  Cette procédure pas à pas crée deux manifestes requis pour un déploiement [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  Vous pouvez créer un programme d'amorçage de composants requis à l'aide de la [GenerateBootstrapper Task](../msbuild/generatebootstrapper-task.md).  
  
### Pour déployer une application avec l'outil en ligne de commande Mage.exe  
  
1.  Créez un répertoire dans lequel vous stockerez vos fichiers du déploiement [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  
  
2.  Dans le répertoire de déploiement que vous venez de créer, ajoutez un sous\-répertoire de version.  S'il s'agit du premier déploiement de l'application, nommez ce sous\-répertoire 1.0.0.0.  
  
    > [!NOTE]
    >  La version de votre déploiement peut différer de celle de votre application.  
  
3.  Copiez tous vos fichiers d'application dans le sous\-répertoire de version, y compris les fichiers exécutables, les assemblys, les ressources et les fichiers de données.  Si nécessaire, vous pouvez créer des sous\-répertoires supplémentaires contenant d'autres fichiers.  
  
4.  Ouvrez le [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] ou l'invite de commandes Visual Studio et accédez au sous\-répertoire de version.  
  
5.  Créez le manifeste d'application par un appel à Mage.exe.  L'instruction suivante crée un manifeste d'application pour le code compilé à exécuter sur le processeur Intel x86.  
  
    ```  
    mage -New Application -Processor x86 -ToFile AppToDeploy.exe.manifest -name "My App" -Version 1.0.0.0 -FromDirectory .   
    ```  
  
    > [!NOTE]
    >  Veillez à inclure le point \(.\) après l'option `-FromDirectory`, qui indique le répertoire actif.  Si vous n'incluez pas le point, vous devez spécifier le chemin d'accès de vos fichiers d'application.  
  
6.  Signez le manifeste d'application avec votre certificat Authenticode.  Remplacez *mycert.pfx* par le chemin d'accès de votre fichier de certificat.  Remplacez *passwd* par le mot de passe de votre fichier de certificat.  
  
    ```  
    mage -Sign AppToDeploy.exe.manifest -CertFile mycert.pfx -Password passwd  
    ```  
  
7.  Accédez à la racine du répertoire de déploiement.  
  
8.  Générez le manifeste de déploiement en appelant Mage.exe.  Par défaut, Mage.exe marquera votre déploiement [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] en tant qu'application installée pour pouvoir l'exécuter en ligne et hors connexion.  Pour que l'application soit uniquement accessible lorsque l'utilisateur est en ligne, utilisez l'option `-Install` avec la valeur `false`.  Si vous utilisez la valeur par défaut et si les utilisateurs installent votre application à partir d'un site Web ou d'un partage de fichiers, assurez\-vous que la valeur de l'option `-ProviderUrl` pointe vers l'emplacement du manifeste d'application sur le serveur Web ou le partage.  
  
    ```  
    mage -New Deployment -Processor x86 -Install true -Publisher "My Co." -ProviderUrl "\\myServer\myShare\AppToDeploy.application" -AppManifest 1.0.0.0\AppToDeploy.exe.manifest -ToFile AppToDeploy.application  
    ```  
  
9. Signez le manifeste de déploiement avec votre certificat Authenticode.  
  
    ```  
    mage -Sign AppToDeploy.application -CertFile mycert.pfx -Password passwd  
    ```  
  
10. Copiez tous les fichiers du répertoire de déploiement vers la destination ou le média du déploiement.  Il peut s'agir d'un dossier sur un site Web ou un site FTP, d'un partage de fichiers ou d'un CD\-ROM.  
  
11. Fournissez à vos utilisateurs l'URL, l'UNC ou le média physique requis pour installer votre application.  Si vous fournissez une URL ou un UNC, vous devez communiquer aux utilisateurs le chemin d'accès complet au manifeste de déploiement.  Si, par exemple, AppToDeploy est déployé sur http:\/\/webserver01\/ dans le répertoire AppToDeploy, le chemin d'accès complet de l'URL est http:\/\/webserver01\/AppToDeploy\/AppToDeploy.application.  
  
### Pour déployer une application avec l'outil graphique MageUI.exe  
  
1.  Créez un répertoire dans lequel vous stockerez vos fichiers de déploiement [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  
  
2.  Dans le répertoire de déploiement que vous venez de créer, ajoutez un sous\-répertoire de version.  S'il s'agit du premier déploiement de l'application, nommez ce sous\-répertoire 1.0.0.0.  
  
    > [!NOTE]
    >  La version de votre déploiement diffère sans doute de celle de votre application.  
  
3.  Copiez tous vos fichiers d'application dans le sous\-répertoire de version, y compris les fichiers exécutables, les assemblys, les ressources et les fichiers de données.  Si nécessaire, vous pouvez créer des sous\-répertoires supplémentaires contenant d'autres fichiers.  
  
4.  Lancez l'outil graphique MageUI.exe.  
  
    ```  
    MageUI.exe  
    ```  
  
5.  Créez un nouveau manifeste d'application en sélectionnant **Fichier**, **Nouveau**, puis **Manifeste d'application** dans le menu.  
  
6.  Sous l'onglet **Nom** par défaut, tapez le nom et le numéro de version de ce déploiement.  Spécifiez également le **Processeur** pour lequel votre application est générée, tel que x86.  
  
7.  Sélectionnez l'onglet **Fichiers** puis cliquez sur le bouton de sélection \(**...**\) en regard de la zone de texte **Répertoire d'application**.  La boîte de dialogue Rechercher un dossier s'affiche.  
  
8.  Sélectionnez le sous\-répertoire de version contenant vos fichiers d'application, puis cliquez sur **OK**.  
  
9. Si vous envisagez d'effectuer le déploiement à partir des services IIS \(Internet Information Services\), activez la case à cocher **Lors du peuplement, ajouter l'extension .deploy à tous les fichiers qui n'en sont pas dotés**.  
  
10. Cliquez sur le bouton **Remplir** pour ajouter tous vos fichiers d'application à la liste de fichiers.  Si votre application contient plusieurs fichiers exécutables, marquez le fichier exécutable principal de ce déploiement comme application de démarrage en sélectionnant **Point d'entrée** dans la liste déroulante **Type de fichier**.  \(Si votre application ne contient qu'un seul fichier exécutable, MageUI.exe le marque à votre place.\)  
  
11. Sélectionnez l'onglet **Autorisations requises** et sélectionnez le niveau de confiance que votre application doit déclarer.  La valeur par défaut est **FullTrust**, qui convient à la plupart des applications.  
  
12. Dans le menu, sélectionnez **Fichier**, puis **Enregistrer sous**.  La boîte de dialogue Options de signature s'affiche et vous invite à signer le manifeste de l'application.  
  
13. Si vous possédez un certificat stocké en tant que fichier dans votre système de fichiers, utilisez l'option **Signer avec le fichier de certificat** et sélectionnez le certificat dans le système de fichiers à l'aide du bouton de sélection \(**...**\).  Tapez ensuite votre mot de passe de certificat.  
  
     ou  
  
     Si votre certificat est conservé dans un magasin de certificats accessible à partir de votre ordinateur, sélectionnez l'option **Signer avec le certificat stocké**, puis choisissez le certificat dans la liste fournie.  
  
14. Cliquez sur **OK** pour signer votre manifeste d'application.  La boîte de dialogue Enregistrer sous s'affiche.  
  
15. Dans la boîte de dialogue Enregistrer sous, spécifiez le répertoire de version, puis cliquez sur **Enregistrer**.  
  
16. Dans le menu, sélectionnez **Fichier**, **Nouveau**, **Manifeste de déploiement** pour créer votre manifeste de déploiement.  
  
17. Sous l'onglet **Nom**, spécifiez un nom et un numéro de version pour ce déploiement \(1.0.0.0 dans cet exemple\).  Spécifiez également le **Processeur** pour lequel votre application est générée, tel que x86.  
  
18. Sélectionnez l'onglet **Description** et spécifiez des valeurs pour **Éditeur** et **Produit**.  \(**Produit** est le nom donné à votre application dans le menu Démarrer de Windows lorsque votre application est installée sur un ordinateur client pour une utilisation hors connexion.\)  
  
19. Sélectionnez l'onglet **Options de déploiement**, et dans la zone de texte **Emplacement de démarrage**, spécifiez l'emplacement du manifeste de l'application sur le serveur Web ou le partage.  Par exemple, \\\\myServer\\myShare\\AppToDeploy.application.  
  
20. Si vous avez ajouté l'extension .deploy lors d'une étape précédente, sélectionnez également **Utiliser l'extension de fichier .deploy** ici.  
  
21. Sélectionnez l'onglet **Options de mise à jour** et spécifiez la fréquence de mise à jour souhaitée pour cette application.  Si votre application utilise <xref:System.Deployment.Application.UpdateCheckInfo> pour vérifier elle\-même les mises à jour, désactivez la case à cocher **Cette application doit rechercher des mises à jour**.  
  
22. Sélectionnez l'onglet **Référence d'application**, puis cliquez sur le bouton **Sélectionner un manifeste**.  Une boîte de dialogue s'affiche.  
  
23. Sélectionnez le manifeste d'application créé précédemment, puis cliquez sur **Ouvrir**.  
  
24. Dans le menu, sélectionnez **Fichier**, puis **Enregistrer sous**.  La boîte de dialogue Options de signature s'affiche et vous invite à signer le manifeste de déploiement.  
  
25. Si vous possédez un certificat stocké en tant que fichier dans votre système de fichiers, utilisez l'option **Signer avec le fichier de certificat** et sélectionnez le certificat dans le système de fichiers à l'aide du bouton de sélection \(**...**\).  Tapez ensuite votre mot de passe de certificat.  
  
     ou  
  
     Si votre certificat est conservé dans un magasin de certificats accessible à partir de votre ordinateur, sélectionnez l'option **Signer avec le certificat stocké**, puis choisissez le certificat dans la liste fournie.  
  
26. Cliquez sur **OK** pour signer votre manifeste de déploiement.  La boîte de dialogue Enregistrer sous s'affiche.  
  
27. Dans la boîte de dialogue **Enregistrer sous**, remontez d'un répertoire jusqu'à la racine de votre déploiement, puis cliquez sur **Enregistrer**.  
  
28. Copiez tous les fichiers du répertoire de déploiement vers la destination ou le média du déploiement.  Il peut s'agir d'un dossier sur un site Web ou un site FTP, d'un partage de fichiers ou d'un CD\-ROM.  
  
29. Fournissez à vos utilisateurs l'URL, l'UNC ou le média physique requis pour installer votre application.  Si vous fournissez une URL ou un UNC, vous devez communiquer aux utilisateurs le chemin d'accès complet au manifeste de déploiement.  Si, par exemple, AppToDeploy est déployé sur http:\/\/webserver01\/ dans le répertoire AppToDeploy, le chemin d'accès complet de l'URL est http:\/\/webserver01\/AppToDeploy\/AppToDeploy.application.  
  
## Étapes suivantes  
 Lorsque vous déployez une nouvelle version de l'application, créez un nouveau répertoire dont le nom fait référence à la nouvelle version, par exemple 1.0.0.1, et copiez les nouveaux fichiers d'application dans un nouveau répertoire.  Vous devez ensuite exécuter les étapes précédentes pour créer et signer un nouveau manifeste d'application ainsi que mettre à jour et signer le manifeste de déploiement.  Veillez à spécifier la même version récente dans les appels Mage.exe `-New` et `–Update`, car [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] met uniquement à jour les versions les plus récentes, l'entier situé le plus à gauche étant le plus significatif.  Si vous avez utilisé MageUI.exe, vous pouvez mettre à jour le manifeste de déploiement en l'ouvrant, en sélectionnant l'onglet **Référence d'application,** en cliquant sur le bouton **Sélectionner un manifeste** et en sélectionnant ensuite le manifeste d'application mis à jour.  
  
## Voir aussi  
 [Mage.exe \(outil Manifest Generation and Editing\)](../Topic/Mage.exe%20\(Manifest%20Generation%20and%20Editing%20Tool\).md)   
 [MageUI.exe \(Manifest Generation and Editing Tool, Graphical Client\)](../Topic/MageUI.exe%20\(Manifest%20Generation%20and%20Editing%20Tool,%20Graphical%20Client\).md)   
 [Publishing ClickOnce Applications](../deployment/publishing-clickonce-applications.md)   
 [ClickOnce Deployment Manifest](../deployment/clickonce-deployment-manifest.md)   
 [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md)