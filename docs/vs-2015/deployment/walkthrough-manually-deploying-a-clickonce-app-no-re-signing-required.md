---
title: 'Procédure pas à pas : Déploiement manuel d’une Application ClickOnce qui ne nécessite pas de nouvelle signature et qui conserve les informations de personnalisation | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
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
- branding
- preserved branding information
- ClickOnce deployment, manually
- multiple ClickOnce deployment and branding
- ClickOnce deployment, SDK tools
- customer deployments
- manual ClickOnce deployments
- manifests [ClickOnce]
- ClickOnce applications, deployed by others
ms.assetid: c21822fb-d4ee-42e4-b72d-41ee9786efe5
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 85453b899501d83191016bde0edd40b4e2a96d94
ms.sourcegitcommit: d705e015cb525bfa87a0b93e93376c3956ec2707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2018
ms.locfileid: "47590497"
---
# <a name="walkthrough-manually-deploying-a-clickonce-application-that-does-not-require-re-signing-and-that-preserves-branding-information"></a>Procédure pas à pas : déploiement manuel d'une application ClickOnce qui ne nécessite pas de nouvelle signature et qui conserve les informations relatives à la personnalisation
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [procédure pas à pas : déploiement manuel d’une Application ClickOnce qui ne nécessite pas de nouvelle signature et qui conserve les informations sur le logo](https://docs.microsoft.com/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-application-that-does-not-require-re-signing-and-that-preserves-branding-information).  
  
Lorsque vous créez un [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] application et puis de lui donner à un client pour publier et le déploiement, le client a généralement mis à jour le manifeste de déploiement et de signer à nouveau. Si qui est toujours la méthode recommandée dans la plupart des cas, le .NET Framework 3.5 vous permet de créer [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] déploiements peuvent être déployés par les clients sans avoir à régénérer un nouveau manifeste de déploiement. Pour plus d’informations, consultez [déploiement ClickOnce Applications pour de test et les serveurs de Production sans Resigning](../deployment/deploying-clickonce-applications-for-testing-and-production-servers-without-resigning.md).  
  
 Lorsque vous créez un [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] application et puis de lui donner à un client pour publier et le déploiement, l’application peut utiliser la personnalisation du client ou conserve la vôtre. Par exemple, si l’application est une application propriétaire unique, vous souhaiterez conserver votre personnalisation. Si l’application est hautement personnalisée pour chaque client, vous souhaiterez probablement utiliser la personnalisation du client. Le .NET Framework 3.5 permet de vous permettent de préserver votre marque, les informations de serveur de publication et signature de sécurité lorsque vous donnez une application à une organisation à déployer. Pour plus d’informations, consultez [création d’Applications ClickOnce pour d’autres personnes à déployer](../deployment/creating-clickonce-applications-for-others-to-deploy.md).  
  
> [!NOTE]
>  Dans cette procédure pas à pas vous créez des déploiements manuellement à l’aide de l’outil de ligne de commande Mage.exe ou l’outil graphique MageUI.exe. Pour plus d’informations sur les déploiements manuels, consultez [procédure pas à pas : déploiement manuel d’une Application ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
## <a name="prerequisites"></a>Prérequis  
 Pour effectuer les étapes dans cette procédure pas à pas, vous devez les éléments suivants :  
  
-   Une application Windows Forms que vous êtes prêt à déployer. Cette application sera appelée WindowsFormsApp1.  
  
-   Visual Studio ou le Kit de développement logiciel Windows.  
  
### <a name="to-deploy-a-clickonce-application-with-multiple-deployment-and-branding-support-using-mageexe"></a>Pour déployer une application ClickOnce avec plusieurs déploiements et la prise en charge de la personnalisation à l’aide de Mage.exe  
  
1.  Ouvrez une invite de commandes Visual Studio ou un [!INCLUDE[winsdkshort](../includes/winsdkshort-md.md)] invite de commandes et accédez au répertoire dans lequel vous souhaitez stocker votre [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] fichiers.  
  
2.  Créez un répertoire nommé d’après la version actuelle de votre déploiement. S’il s’agit de la première fois que vous déployez l’application, vous choisirez probablement **1.0.0.0**.  
  
    > [!NOTE]
    >  La version de votre déploiement peut être différente de la version de vos fichiers d’application.  
  
3.  Créez un sous-répertoire nommé **bin** et copier tous vos fichiers d’application, y compris les fichiers exécutables, les assemblys, les ressources et les fichiers de données.  
  
4.  Générer le manifeste d’application avec un appel à Mage.exe.  
  
    ```  
    mage -New Application -ToFile 1.0.0.0\WindowsFormsApp1.exe.manifest -Name "Windows Forms App 1" -Version 1.0.0.0 -FromDirectory 1.0.0.0\bin -UseManifestForTrust true -Publisher "A. Datum Corporation"  
    ```  
  
5.  Signer le manifeste d’application avec votre certificat numérique.  
  
    ```  
    mage -Sign WindowsFormsApp1.exe.manifest -CertFile mycert.pfx  
    ```  
  
6.  Générer le manifeste de déploiement avec un appel à Mage.exe. Par défaut, Mage.exe marquera votre [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] déploiement sous la forme d’une application installée, afin qu’il peut être exécuté à la fois en ligne et hors connexion. Pour rendre l’application disponible uniquement lorsque l’utilisateur est en ligne, utilisez le `-i` argument avec la valeur `f`. Étant donné que cette application prend en charge plusieurs déploiements, exclure les `-providerUrl` l’argument de Mage.exe. (Dans les versions du .NET Framework antérieures à la version 3.5, à l’exclusion `-providerUrl` pour une application hors connexion entraîne une erreur.)  
  
    ```  
    mage -New Deployment -ToFile WindowsFormsApp1.application -Name "Windows Forms App 1" -Version 1.0.0.0 -AppManifest 1.0.0.0\WindowsFormsApp1.manifest   
    ```  
  
7.  Ne vous connectez pas le manifeste de déploiement.  
  
8.  Fournissez tous les fichiers au client, ce qui vous allez déployer l’application sur son réseau.  
  
9. À ce stade, le client doit signer le manifeste de déploiement avec son propre certificat généré automatiquement. Par exemple, si le client fonctionne pour une société nommée Adventure Works, il peut générer un certificat auto-signé à l’aide de l’outil MakeCert.exe. Ensuite, utilisez l’outil Pvk2pfx.exe pour combiner les fichiers créés par MakeCert.exe dans un fichier PFX qui peut être passé à Mage.exe.  
  
    ```  
    makecert -r -pe -n "CN=Adventure Works" -sv MyCert.pvk MyCert.cer  
    pvk2pfx.exe -pvk MyCert.pvk -spc MyCert.cer -pfx MyCert.pfx  
    ```  
  
10. Le client utilise ensuite ce certificat pour signer le manifeste de déploiement.  
  
    ```  
    mage -Sign WindowsFormsApp1.application -CertFile MyCert.pfx  
    ```  
  
11. Le client déploie l’application à leurs utilisateurs.  
  
### <a name="to-deploy-a-clickonce-application-with-multiple-deployment-and-branding-support-using-mageuiexe"></a>Pour déployer une application ClickOnce avec plusieurs déploiements et la prise en charge de la personnalisation à l’aide de MageUI.exe  
  
1.  Ouvrez une invite de commandes Visual Studio ou un [!INCLUDE[winsdkshort](../includes/winsdkshort-md.md)] invite de commandes et accédez au répertoire dans lequel vous souhaitez stocker votre [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] fichiers.  
  
2.  Créez un sous-répertoire nommé **bin** et copier tous vos fichiers d’application, y compris les fichiers exécutables, les assemblys, les ressources et les fichiers de données.  
  
3.  Créez un sous-répertoire nommé d’après la version actuelle de votre déploiement. S’il s’agit de la première fois que vous déployez l’application, vous choisirez probablement **1.0.0.0**.  
  
    > [!NOTE]
    >  La version de votre déploiement peut être différente de la version de vos fichiers d’application.  
  
4.  Déplacer le \\ **bin** répertoire dans le répertoire que vous avez créé à l’étape 2.  
  
5.  Démarrez l’outil graphique MageUI.exe.  
  
    ```  
    MageUI.exe  
    ```  
  
6.  Créer un nouveau manifeste d’application en sélectionnant **fichier**, **New**, **manifeste d’Application** dans le menu.  
  
7.  Sur la valeur par défaut **nom** , entrez le nom et numéro de version de ce déploiement. Vous devez également fournir une valeur pour **Publisher**, qui sera utilisé comme nom de dossier pour le lien de raccourci de l’application dans le menu Démarrer, lorsqu’elle est déployée.  
  
8.  Sélectionnez le **Options d’Application** onglet et cliquez sur **utiliser le manifeste d’Application pour les informations d’approbation**. Cela permettra de personnalisation pour ce tiers [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] application.  
  
9. Sélectionnez le **fichiers** onglet et cliquez sur le **Parcourir** bouton en regard de la zone de texte du répertoire de l’Application.  
  
10. Sélectionnez le répertoire qui contient vos fichiers d’application que vous avez créé à l’étape 2, puis cliquez sur **OK** dans la boîte de dialogue de sélection de dossier.  
  
11. Cliquez sur le **Populate** pour ajouter tous les fichiers de votre application à la liste des fichiers. Si votre application contient plusieurs fichiers exécutables, marquez le fichier exécutable principal de ce déploiement comme application de démarrage en sélectionnant **Point d’entrée** à partir de la **Type de fichier** liste déroulante. (Si votre application ne contient qu’un seul fichier exécutable, MageUI.exe le marque pour vous.)  
  
12. Sélectionnez le **autorisations requises** onglet et sélectionnez le niveau de confiance que votre application doit déclarer. La valeur par défaut est **confiance totale**, ce qui convient à la plupart des applications.  
  
13. Sélectionnez **fichier**, **enregistrer** dans le menu, puis enregistrez le manifeste d’application. Vous devrez signer le manifeste d’application lorsque vous l’enregistrez.  
  
14. Si vous avez un certificat stocké en tant que fichier sur votre système de fichiers, utilisez le **connexion en tant que fichier de certificat** option et sélectionnez le certificat dans le système de fichiers avec les points de suspension (**...** ) bouton.  
  
     - ou -  
  
     Si votre certificat est conservé dans un magasin de certificats est accessible à partir de votre ordinateur, sélectionnez le **signer avec l’option de certificat stockées**, puis sélectionnez le certificat dans la liste fournie.  
  
15. Sélectionnez **fichier**, **New**, **du manifeste de déploiement** dans le menu pour créer votre manifeste de déploiement, puis, sous la **nom** onglet, fournissez un nom et numéro de version (**1.0.0.0** dans cet exemple).  
  
16. Basculez vers le **mettre à jour** onglet et spécifier la fréquence à laquelle vous souhaitez que cette application pour mettre à jour. Si votre application utilise le [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] API de déploiement pour vérifier les mises à jour elle-même, désactivez la case à cocher intitulée **cette application doit rechercher les mises à jour**.  
  
17. Basculez vers le **Application référence** onglet. Vous pouvez préremplir toutes les valeurs de cet onglet en cliquant sur le **sélectionner un manifeste** bouton et en sélectionnant le manifeste d’application que vous avez créé dans les étapes précédentes.  
  
18. Choisissez **enregistrer** et enregistrer le manifeste de déploiement sur le disque. Vous devrez signer le manifeste d’application lorsque vous l’enregistrez. Cliquez sur **Annuler** pour enregistrer le manifeste sans le signer.  
  
19. Fournissez tous les fichiers d’application au client.  
  
20. À ce stade, le client doit signer le manifeste de déploiement avec son propre certificat généré automatiquement. Par exemple, si le client fonctionne pour une société nommée Adventure Works, il peut générer un certificat auto-signé à l’aide de l’outil MakeCert.exe. Ensuite, utilisez l’outil Pvk2pfx.exe pour combiner les fichiers créés par MakeCert.exe dans un fichier PFX qui peut être passé à MageUI.exe.  
  
    ```  
    makecert -r -pe -n "CN=Adventure Works" -sv MyCert.pvk MyCert.cer  
    pvk2pfx.exe -pvk MyCert.pvk -spc MyCert.cer -pfx MyCert.pfx  
    ```  
  
21. Avec le certificat généré, le client signe maintenant le manifeste de déploiement en ouvrant le manifeste de déploiement dans MageUI.exe et l’enregistrer. Lorsque la signature de la boîte de dialogue s’affiche, le client sélectionne **connexion en tant que fichier de certificat** option et choisit le fichier PFX qu’il a enregistré sur le disque.  
  
22. Le client déploie l’application à leurs utilisateurs.  
  
## <a name="next-steps"></a>Étapes suivantes  
  
## <a name="see-also"></a>Voir aussi  
 [Mage.exe (outil Manifest Generation and Editing)](http://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1)   
 [MageUI.exe (outil Manifest Generation and Editing, client graphique)](http://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14)   
 [Makecert.exe (outil de création du certificat)](http://msdn.microsoft.com/library/b0343f8e-9c41-4852-a85c-f8a0c408cf0d)



