---
title: "Walkthrough: Manually Deploying a ClickOnce Application that Does Not Require Re-Signing and that Preserves Branding Information | Microsoft Docs"
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
  - "branding"
  - "preserved branding information"
  - "ClickOnce deployment, manually"
  - "multiple ClickOnce deployment and branding"
  - "ClickOnce deployment, SDK tools"
  - "customer deployments"
  - "manual ClickOnce deployments"
  - "manifests [ClickOnce]"
  - "ClickOnce applications, deployed by others"
ms.assetid: c21822fb-d4ee-42e4-b72d-41ee9786efe5
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Walkthrough: Manually Deploying a ClickOnce Application that Does Not Require Re-Signing and that Preserves Branding Information
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Le client à qui vous confiez la publication et le déploiement d'une application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] que vous avez créée a généralement mis à jour le manifeste de déploiement et l'a de nouveau signé. Bien que cette méthode soit encore la plus répandue, .NET Framework 3.5 vous permet de créer des déploiements [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] qui peuvent être déployés par les clients sans avoir à régénérer un nouveau manifeste de déploiement.  Pour plus d'informations, consultez [Deploying ClickOnce Applications For Testing and Production Servers without Resigning](../deployment/deploying-clickonce-applications-for-testing-and-production-servers-without-resigning.md).  
  
 L'application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] que vous créez et confiez à un client à des fins de publication et de déploiement peut utiliser la personnalisation du client ou conserver la vôtre.  Par exemple, si vous disposez d'une seule application propriétaire, vous souhaiterez peut\-être conserver votre personnalisation.  Si l'application est hautement personnalisée pour chaque client, il est peut\-être préférable d'utiliser la personnalisation du client.  .NET Framework 3.5 vous permet de conserver votre personnalisation, les informations sur l'éditeur et la signature de sécurité lorsque vous confiez le déploiement d'une application à une société.  Pour plus d'informations, consultez [Creating ClickOnce Applications for Others to Deploy](../deployment/creating-clickonce-applications-for-others-to-deploy.md).  
  
> [!NOTE]
>  Dans cette procédure pas à pas, vous créez manuellement des déploiements à l'aide de l'outil de ligne de commande Mage.exe ou de l'outil graphique MageUI.exe.  Pour plus d'informations sur les déploiements manuels, consultez [Walkthrough: Manually Deploying a ClickOnce Application](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
## Composants requis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des éléments suivants :  
  
-   une application Windows Forms que vous êtes prêt à déployer,  nommée WindowsFormsApp1 ;  
  
-   Visual Studio ou le Kit de développement logiciel Windows.  
  
### Pour déployer une application ClickOnce prenant en charge plusieurs déploiements et la personnalisation à l'aide de Mage.exe  
  
1.  Ouvrez une invite de commandes Visual Studio ou une invite de commandes du [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] et basculez vers le répertoire dans lequel vous souhaitez stocker vos fichiers [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  
  
2.  Créez un répertoire dont le nom indique la version actuelle de votre déploiement.  S'il s'agit du premier déploiement de l'application, choisissez par exemple 1.0.0.0.  
  
    > [!NOTE]
    >  La version de votre déploiement peut différer de la version de vos fichiers d'application.  
  
3.  Créez un sous\-répertoire nommé bin et copiez tous vos fichiers d'application, y compris les fichiers exécutables, les assemblys, les ressources et les fichiers de données.  
  
4.  Générez le manifeste d'application en appelant Mage.exe.  
  
    ```  
    mage -New Application -ToFile 1.0.0.0\WindowsFormsApp1.exe.manifest -Name "Windows Forms App 1" -Version 1.0.0.0 -FromDirectory 1.0.0.0\bin -UseManifestForTrust true -Publisher "A. Datum Corporation"  
    ```  
  
5.  Signez le manifeste d'application avec votre certificat numérique.  
  
    ```  
    mage -Sign WindowsFormsApp1.exe.manifest -CertFile mycert.pfx  
    ```  
  
6.  Générez le manifeste de déploiement en appelant Mage.exe.  Par défaut, Mage.exe marquera votre déploiement [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] en tant qu'application installée pour pouvoir l'exécuter en ligne et hors connexion.  Pour que l'application ne soit accessible que lorsque l'utilisateur est en ligne, utilisez l'argument `-i` avec la valeur `f`.  Comme cette application prend en charge plusieurs déploiements, vous devez exclure l'argument `-providerUrl` dans Mage.exe.  \(Dans les versions du .NET Framework antérieures à la version 3.5, l'exclusion de `-providerUrl` pour une application hors connexion génère une erreur.\)  
  
    ```  
    mage -New Deployment -ToFile WindowsFormsApp1.application -Name "Windows Forms App 1" -Version 1.0.0.0 -AppManifest 1.0.0.0\WindowsFormsApp1.manifest   
    ```  
  
7.  Ne signez pas le manifeste de déploiement.  
  
8.  Fournissez tous les fichiers au client qui déploiera l'application sur son réseau.  
  
9. À ce stade, le client doit signer le manifeste de déploiement avec son certificat généré automatiquement.  Par exemple, si le client travaille pour la société Adventure Works, il peut générer un certificat auto\-signé à l'aide de l'outil MakeCert.exe.  Il doit ensuite utiliser l'outil Pvk2pfx.exe pour combiner les fichiers créés par MakeCert.exe dans un fichier PFX pouvant être passé à Mage.exe.  
  
    ```  
    makecert -r -pe -n "CN=Adventure Works" -sv MyCert.pvk MyCert.cer  
    pvk2pfx.exe -pvk MyCert.pvk -spc MyCert.cer -pfx MyCert.pfx  
    ```  
  
10. Le client utilise ensuite ce certificat pour signer le manifeste de déploiement.  
  
    ```  
    mage -Sign WindowsFormsApp1.application -CertFile MyCert.pfx  
    ```  
  
11. Le client déploie l'application auprès de ses utilisateurs.  
  
### Pour déployer une application ClickOnce prenant en charge plusieurs déploiements et la personnalisation à l'aide de MageUI.exe  
  
1.  Ouvrez une invite de commandes Visual Studio ou une invite de commandes du [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] et naviguez vers le répertoire dans lequel vous souhaitez stocker vos fichiers [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  
  
2.  Créez un sous\-répertoire nommé bin et copiez tous vos fichiers d'application, y compris les fichiers exécutables, les assemblys, les ressources et les fichiers de données.  
  
3.  Créez un sous\-répertoire dont le nom indique la version actuelle de votre déploiement.  S'il s'agit du premier déploiement de l'application, choisissez par exemple 1.0.0.0.  
  
    > [!NOTE]
    >  La version de votre déploiement peut différer de la version de vos fichiers d'application.  
  
4.  Déplacez le répertoire \\bin dans le répertoire créé à l'étape 2.  
  
5.  Lancez l'outil graphique MageUI.exe.  
  
    ```  
    MageUI.exe  
    ```  
  
6.  Créez un nouveau manifeste d'application en sélectionnant **Fichier**, **Nouveau**, puis **Manifeste d'application** dans le menu.  
  
7.  Sous l'onglet **Nom** par défaut, entrez le nom et le numéro de version de ce déploiement.  Vous devez également fournir une valeur **Éditeur** qui sera utilisée comme nom de dossier pour le lien de raccourci de l'application dans le menu Démarrer lors de son déploiement.  
  
8.  Sélectionnez l'onglet **Options d'application** et cliquez sur **Utiliser le manifeste d'application pour les informations d'approbation**.  La personnalisation par un tiers sera alors activée pour cette application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  
  
9. Sélectionnez l'onglet **Fichiers** et cliquez sur le bouton **Parcourir** en regard de la zone de texte Répertoire d'application.  
  
10. Sélectionnez le répertoire qui contient vos fichiers d'application créés à l'étape 2, puis cliquez sur **OK** dans la boîte de dialogue de sélection de dossier.  
  
11. Cliquez sur le bouton **Remplir** pour ajouter tous vos fichiers d'application à la liste de fichiers.  Si votre application contient plusieurs fichiers exécutables, marquez le fichier exécutable principal de ce déploiement comme application de démarrage en sélectionnant **Point d'entrée** dans la liste déroulante **Type de fichier**.  \(Si votre application ne contient qu'un seul fichier exécutable, MageUI.exe le marque pour vous.\)  
  
12. Sélectionnez l'onglet **Autorisations requises** et sélectionnez le niveau de confiance que votre application doit déclarer.  La valeur par défaut est **Confiance totale**, laquelle convient à la plupart des applications.  
  
13. Sélectionnez **Fichier**, puis **Enregistrer** dans le menu, et enregistrez le manifeste d'application.  Vous êtes invité à signer le manifeste d'application lorsque vous l'enregistrez.  
  
14. Si vous possédez un certificat stocké en tant que fichier dans votre système de fichiers, utilisez l'option **Signer avec le fichier de certificat** et sélectionnez le certificat dans le système de fichiers à l'aide du bouton de sélection \(**...**\).  
  
     ou  
  
     Si votre certificat est conservé dans un magasin de certificats accessible à partir de votre ordinateur, sélectionnez l'option **Signer avec le certificat stocké**, puis choisissez le certificat dans la liste fournie.  
  
15. Sélectionnez **Fichier**, **Nouveau**, **Manifeste de déploiement** dans le menu pour créer votre manifeste de déploiement, puis dans l'onglet **Nom**, indiquez un nom et un numéro de version \(1.0.0.0 dans cet exemple\).  
  
16. Basculez vers l'onglet **Mettre à jour** et spécifiez la fréquence de mise à jour souhaitée de cette application.  Si votre application utilise l'API de déploiement de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] pour vérifier elle\-même les mises à jour, désactivez la case à cocher intitulée **Cette application doit rechercher des mises à jour**.  
  
17. Basculez vers l'onglet **Référence d'application**.  Vous pouvez remplir préalablement toutes les valeurs sous cet onglet en cliquant sur le bouton **Sélectionner un manifeste** et en sélectionnant le manifeste d'application créé au cours des étapes précédentes.  
  
18. Choisissez **Enregistrer** et enregistrez le manifeste de déploiement sur le disque.  Vous êtes invité à signer le manifeste d'application lorsque vous l'enregistrez.  Cliquez sur **Annuler** pour enregistrer le manifeste sans le signer.  
  
19. Fournissez tous les fichiers d'application au client.  
  
20. À ce stade, le client doit signer le manifeste de déploiement avec son certificat généré automatiquement.  Par exemple, si le client travaille pour la société Adventure Works, il peut générer un certificat auto\-signé à l'aide de l'outil MakeCert.exe.  Ensuite, il peut utiliser l'outil Pvk2pfx.exe pour combiner les fichiers créés par MakeCert.exe dans un fichier PFX pouvant être passé à MageUI.exe.  
  
    ```  
    makecert -r -pe -n "CN=Adventure Works" -sv MyCert.pvk MyCert.cer  
    pvk2pfx.exe -pvk MyCert.pvk -spc MyCert.cer -pfx MyCert.pfx  
    ```  
  
21. Maintenant que le certificat est généré, le client doit signer le manifeste de déploiement en l'ouvrant dans MageUI.exe puis en l'enregistrant.  Lorsque la boîte de dialogue de signature apparaît, il sélectionne l'option **Signer avec le fichier de certificat** et choisit le fichier PFX qu'il a enregistré sur le disque.  
  
22. Le client déploie l'application auprès de ses utilisateurs.  
  
## Étapes suivantes  
  
## Voir aussi  
 [Mage.exe \(outil Manifest Generation and Editing\)](../Topic/Mage.exe%20\(Manifest%20Generation%20and%20Editing%20Tool\).md)   
 [MageUI.exe \(Manifest Generation and Editing Tool, Graphical Client\)](../Topic/MageUI.exe%20\(Manifest%20Generation%20and%20Editing%20Tool,%20Graphical%20Client\).md)   
 [Makecert.exe \(Certificate Creation Tool\)](../Topic/Makecert.exe%20\(Certificate%20Creation%20Tool\).md)