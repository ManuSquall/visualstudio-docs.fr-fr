---
title: Déployer manuellement l’application ClickOnce & conserver la personnalisation
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9e3f21f9e377b7d3e2d71d499eed25079c7769c7
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90809222"
---
# <a name="walkthrough-manually-deploy-a-clickonce-application-that-does-not-require-re-signing-and-that-preserves-branding-information"></a>Procédure pas à pas : déployer manuellement une application ClickOnce qui ne nécessite pas de nouvelle signature et qui conserve les informations de personnalisation
Lorsque vous créez une [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application et que vous la transmettez à un client pour la publication et le déploiement, le client a traditionnellement dû mettre à jour le manifeste de déploiement et le signer à nouveau. Bien qu’il s’agit toujours de la méthode recommandée dans la plupart des cas, le .NET Framework 3,5 vous permet de créer des [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] déploiements qui peuvent être déployés par les clients sans avoir à régénérer un nouveau manifeste de déploiement. Pour plus d’informations, consultez [déployer des applications ClickOnce pour les serveurs de test et de production sans avoir à vous reconnecter](../deployment/deploying-clickonce-applications-for-testing-and-production-without-resigning.md).

 Lorsque vous créez une [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application et que vous la transmettez à un client pour la publication et le déploiement, l’application peut utiliser la personnalisation du client ou conserver votre personnalisation. Par exemple, si l’application est une application propriétaire unique, vous souhaiterez peut-être conserver votre marque. Si l’application est hautement personnalisée pour chaque client, vous souhaiterez peut-être utiliser la personnalisation du client. La .NET Framework 3,5 vous permet de conserver votre personnalisation, les informations sur l’éditeur et la signature de sécurité lorsque vous fournissez une application à déployer dans une organisation. Pour plus d’informations, consultez [créer des applications ClickOnce à déployer par d’autres](../deployment/creating-clickonce-applications-for-others-to-deploy.md).

> [!NOTE]
> Dans cette procédure pas à pas, vous créez des déploiements manuellement à l’aide de l’outil de ligne de commande *Mage.exe* ou de l’outil graphique *MageUI.exe*. Pour plus d’informations sur les déploiements manuels, consultez [procédure pas à pas : déployer manuellement une application ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).

## <a name="prerequisites"></a>Prérequis
 Pour effectuer les étapes de cette procédure pas à pas, vous avez besoin des éléments suivants :

- Une Windows Forms application que vous êtes prêt à déployer. Cette application sera appelée *WindowsFormsApp1*.

- Visual Studio ou le SDK Windows.

### <a name="to-deploy-a-clickonce-application-with-multiple-deployment-and-branding-support-using-mageexe"></a>Pour déployer une application ClickOnce avec prise en charge de plusieurs déploiements et personnalisations à l’aide de Mage.exe

1. Ouvrez une invite de commandes Visual Studio ou une [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] invite de commandes, puis accédez au répertoire dans lequel vous allez stocker vos [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] fichiers.

2. Créez un répertoire nommé d’après la version actuelle de votre déploiement. S’il s’agit de la première fois que vous déployez l’application, vous choisirez probablement **1.0.0.0**.

   > [!NOTE]
   > La version de votre déploiement peut être différente de la version de vos fichiers d’application.

3. Créez un sous-répertoire nommé **bin** et copiez tous les fichiers de votre application ici, y compris les fichiers exécutables, les assemblys, les ressources et les fichiers de données.

4. Générez le manifeste d’application à l’aide d’un appel à Mage.exe.

   ```cmd
   mage -New Application -ToFile 1.0.0.0\WindowsFormsApp1.exe.manifest -Name "Windows Forms App 1" -Version 1.0.0.0 -FromDirectory 1.0.0.0\bin -UseManifestForTrust true -Publisher "A. Datum Corporation"
   ```

5. Signez le manifeste de l’application avec votre certificat numérique.

   ```cmd
   mage -Sign WindowsFormsApp1.exe.manifest -CertFile mycert.pfx
   ```

6. Générez le manifeste de déploiement à l’aide d’un appel à *Mage.exe*. Par défaut, *Mage.exe* marque votre [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] déploiement comme une application installée, afin qu’il puisse être exécuté à la fois en ligne et hors connexion. Pour rendre l’application disponible uniquement lorsque l’utilisateur est en ligne, utilisez l' `-i` argument avec la valeur `f` . Étant donné que cette application va tirer parti de la fonctionnalité de déploiement multiple, excluez l' `-providerUrl` argument pour *Mage.exe*. (Dans les versions de .NET Framework antérieures à la version 3,5, l’exclusion `-providerUrl` d’une application hors connexion génère une erreur.)

   ```cmd
   mage -New Deployment -ToFile WindowsFormsApp1.application -Name "Windows Forms App 1" -Version 1.0.0.0 -AppManifest 1.0.0.0\WindowsFormsApp1.manifest
   ```

7. Ne signez pas le manifeste de déploiement.

8. Fournissez tous les fichiers au client, qui déploiera l’application sur son réseau.

9. À ce stade, le client doit signer le manifeste de déploiement avec son propre certificat auto-généré. Par exemple, si le client travaille pour une société nommée Adventure Works, il peut générer un certificat auto-signé à l’aide de l’outil *MakeCert.exe* . Ensuite, utilisez l’outil *Pvk2pfx.exe* pour combiner les fichiers créés par *MakeCert.exe* dans un fichier PFX qui peut être passé à *Mage.exe*.

    ```cmd
    makecert -r -pe -n "CN=Adventure Works" -sv MyCert.pvk MyCert.cer
    pvk2pfx.exe -pvk MyCert.pvk -spc MyCert.cer -pfx MyCert.pfx
    ```

10. Le client utilise ensuite ce certificat pour signer le manifeste de déploiement.

    ```cmd
    mage -Sign WindowsFormsApp1.application -CertFile MyCert.pfx
    ```

11. Le client déploie l’application auprès de ses utilisateurs.

### <a name="to-deploy-a-clickonce-application-with-multiple-deployment-and-branding-support-using-mageuiexe"></a>Pour déployer une application ClickOnce avec prise en charge de plusieurs déploiements et personnalisations à l’aide de MageUI.exe

1. Ouvrez une invite de commandes Visual Studio ou une [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] invite de commandes, puis accédez au répertoire dans lequel vous allez stocker vos [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] fichiers.

2. Créez un sous-répertoire nommé **bin** et copiez tous les fichiers de votre application ici, y compris les fichiers exécutables, les assemblys, les ressources et les fichiers de données.

3. Créez un sous-répertoire nommé d’après la version actuelle de votre déploiement. S’il s’agit de la première fois que vous déployez l’application, vous choisirez probablement **1.0.0.0**.

   > [!NOTE]
   > La version de votre déploiement peut être différente de la version de vos fichiers d’application.

4. Déplacez le \\ répertoire **bin** dans le répertoire que vous avez créé à l’étape 2.

5. Démarrez l’outil graphique *MageUI.exe*.

   ```cmd
   MageUI.exe
   ```

6. Créez un nouveau manifeste d’application en sélectionnant **fichier**, **nouveau**, **manifeste d’application** dans le menu.

7. Sous l’onglet **nom** par défaut, entrez le nom et le numéro de version de ce déploiement. Fournissez également une valeur pour **éditeur**, qui sera utilisée comme nom de dossier pour le lien de raccourci de l’application dans le menu Démarrer lors de son déploiement.

8. Sélectionnez l’onglet **options d’application** , puis cliquez sur utiliser le **manifeste d’application pour obtenir des informations d’approbation**. Cette opération active la personnalisation de tiers pour cette [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application.

9. Sélectionnez l’onglet **fichiers** , puis cliquez sur le bouton **Parcourir** en regard de la zone de texte Répertoire de l' **application** .

10. Sélectionnez le répertoire qui contient les fichiers d’application que vous avez créés à l’étape 2, puis cliquez sur **OK** dans la boîte de dialogue Sélection du dossier.

11. Cliquez sur le bouton **Populate** pour ajouter tous les fichiers de votre application à la liste des fichiers. Si votre application contient plusieurs fichiers exécutables, marquez le fichier exécutable principal de ce déploiement en tant qu’application de démarrage en sélectionnant **point d’entrée** dans la liste déroulante **type de fichier** . (Si votre application ne contient qu’un seul fichier exécutable, *MageUI.exe* la marque pour vous.)

12. Sélectionnez l’onglet **autorisations requises** et sélectionnez le niveau de confiance que votre application doit déclarer. La valeur par défaut est **confiance totale**, ce qui convient à la plupart des applications.

13. Sélectionnez **fichier**, **Enregistrer** dans le menu, puis enregistrez le manifeste de l’application. Vous serez invité à signer le manifeste de l’application lors de son enregistrement.

14. Si vous avez un certificat stocké en tant que fichier sur votre système de fichiers, utilisez l’option **signer le fichier de certificat** et sélectionnez le certificat dans le système de fichiers à l’aide du bouton de sélection (**...**).

     - ou -

     Si votre certificat est conservé dans un magasin de certificats accessible à partir de votre ordinateur, sélectionnez l' **option signer avec le certificat stocké**, puis sélectionnez le certificat dans la liste fournie.

15. Sélectionnez **fichier**, **nouveau**, **manifeste de déploiement** dans le menu pour créer votre manifeste de déploiement, puis sous l’onglet **nom** , fournissez un nom et un numéro de version (**1.0.0.0** dans cet exemple).

16. Basculez vers l’onglet **mettre à jour** et spécifiez la fréquence à laquelle vous souhaitez que cette application soit mise à jour. Si votre application utilise l' [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] API de déploiement pour rechercher des mises à jour, désactivez la case à cocher intitulée **cette application doit rechercher les mises à jour**.

17. Basculez vers l’onglet Référence de l' **application** . Vous pouvez préremplir toutes les valeurs de cet onglet en cliquant sur le bouton **Sélectionner un manifeste** et en sélectionnant le manifeste d’application que vous avez créé lors des étapes précédentes.

18. Choisissez **Enregistrer** et enregistrez le manifeste de déploiement sur le disque. Vous serez invité à signer le manifeste de l’application lors de son enregistrement. Cliquez sur **Annuler** pour enregistrer le manifeste sans le signer.

19. Fournissez tous les fichiers d’application au client.

20. À ce stade, le client doit signer le manifeste de déploiement avec son propre certificat auto-généré. Par exemple, si le client travaille pour une société nommée Adventure Works, il peut générer un certificat auto-signé à l’aide de l’outil *MakeCert.exe* . Ensuite, utilisez l’outil *Pvk2pfx.exe* pour combiner les fichiers créés par *MakeCert.exe* dans un fichier PFX qui peut être passé à *MageUI.exe*.

    ```cmd
    makecert -r -pe -n "CN=Adventure Works" -sv MyCert.pvk MyCert.cer
    pvk2pfx.exe -pvk MyCert.pvk -spc MyCert.cer -pfx MyCert.pfx
    ```

21. Une fois le certificat généré, le client signe maintenant le manifeste de déploiement en ouvrant le manifeste de déploiement dans *MageUI.exe*, puis en l’enregistrant. Quand la boîte de dialogue signature s’affiche, le client sélectionne l’option **signer le fichier de certificat** et choisit le fichier PFX qu’il a enregistré sur le disque.

22. Le client déploie l’application auprès de ses utilisateurs.

## <a name="see-also"></a>Voir aussi
- [Mage.exe (Outil Manifest Generation and Editing)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)
- [MageUI.exe (Outil Manifest Generation and Editing, client graphique)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)
- [MakeCert](/windows/desktop/SecCrypto/makecert)
