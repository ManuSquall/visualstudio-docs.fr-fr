---
title: "Déployer des applications de plateforme Windows universelle à partir de Visual Studio | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: ef3a0f36-bfc9-4ca0-aa61-18261f619bff
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d411a65e3882ed85bb3c100e8f7705623a7ce91f
ms.sourcegitcommit: 26419ab0cccdc30d279c32d6a841758cfa903806
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/11/2017
---
# <a name="deploy-uwp-apps-from-visual-studio"></a>Déployer des applications de plateforme Windows universelle à partir de Visual Studio
![S’applique uniquement à Windows](../debugger/media/windows_only_content.png "windows_only_content")  
  
 La fonctionnalité de déploiement de Visual Studio génère et enregistre les applications UWP qui sont créées avec Visual Studio sur un appareil cible. La façon dont l'application est exactement enregistrée varie selon que le périphérique cible est local ou distant :  
  
-   Lorsque la cible est l'ordinateur Visual Studio local, Visual Studio enregistre l'application depuis son dossier de génération.  
  
-   Lorsque la cible est un périphérique distant, Visual Studio copie les fichiers requis sur l'ordinateur distant et enregistre l'appareil sur ce périphérique.  
  
 Le déploiement est automatique lorsque vous déboguez votre application à partir de Visual Studio à l’aide de la **démarrer le débogage** option (clavier : F5) ou le **démarrer sans débogage** option (clavier : CTRL + F5). Vous pouvez aussi déployer votre application manuellement. Le déploiement manuel est utile dans les scénarios suivants :  
  
-   Test ad hoc sur un ordinateur local ou distant.  
  
-   Déploiement d'une application qui démarre une autre application que vous voulez déboguer.  
  
-   Déploiement d'une application qui est déboguée quand elle est démarrée par une autre application ou méthode.
  
##  <a name="BKMK_How_to_deploy_a_Windows_Store_app"></a>Comment déployer une application UWP  
 Le déploiement manuel d'une application obéit à une procédure simple :  
  
1.  Si le déploiement s'effectue sur un périphérique distant, spécifiez le nom ou l'adresse IP du périphérique dans la page des propriétés du projet du projet de démarrage de l'application. (Les étapes associées sont répertoriées plus bas dans cette rubrique.)  
  
2.  Dans la barre d'outils Déboguer de Visual Studio, choisissez la cible de déploiement dans la liste déroulante située à côté du bouton **Démarrer le débogage** .  
  
     ![Exécuter sur l’ordinateur Local](../debugger/media/vsrun_f5_local.png "VSRUN_F5_Local")  
  
3.  Dans le menu **Générer** , choisissez **Déployer**.  
  
##  <a name="BKMK_How_to_specify_a_remote_device"></a> Comment spécifier un périphérique distant  

**Composants requis**  
  
Sur un appareil distant Windows 10, vous devez activer [mode développeur](/windows/uwp/get-started/enable-your-device-for-development). Sur les appareils Windows 10 mise à jour du créateur ou une version ultérieure, les outils à distance sont installés automatiquement lorsque vous déployez votre application. Pour plus d’informations, consultez [déboguer un package d’application installés](../debugger/debug-installed-app-package.md).

> [!NOTE]
> Sur Windows 8.1 et versions de mise à jour du pre-créateur de Windows 10, les outils distants Visual Studio doit être installés sur le périphérique distant, et le débogueur distant doit être en cours d’exécution. Sur Windows 8.1, vous devez également installer une licence de développeur.
  
Le déploiement utilise le canal réseau du débogueur distant pour envoyer les fichiers de l'application sur le périphérique distant.  
  
#### <a name="to-specify-a-remote-device"></a>Pour spécifier un périphérique distant  
  
1.  Dans la page de propriétés de débogage du projet de démarrage, spécifiez le nom ou l'adresse IP d'une cible de déploiement distante.  
  
2.  Pour ouvrir la page de propriétés de débogage, sélectionnez le projet dans l'Explorateur de solutions, puis choisissez **Propriétés** dans le menu contextuel.  
  
3.  Sélectionnez ensuite le nœud **Déboguer** dans la fenêtre de la page de propriétés.

4. Pour **appareil cible**, sélectionnez **ordinateur distant**.

5. Sous **ordinateur distant**, cliquez sur **trouver**.
  
4.  Vous pouvez taper le nom ou l’adresse IP du périphérique distant, ou vous pouvez choisir le périphérique à partir de la **connexion à distance** boîte de dialogue.  
  
     ![Boîte de dialogue de connexion du débogueur distant sélectionnez](../debugger/media/vsrun_selectremotedebuggerdlg.png "VSRUN_SelectRemoteDebuggerDlg")  
  
     Le **connexion à distance** boîte de dialogue affiche les périphériques sur le sous-réseau local et tout périphérique qui est directement connecté à l’ordinateur Visual Studio via un câble Ethernet.  
  
 **Spécification du périphérique distant dans une page de projet JavaScript ou Visual C++**  
  
 ![C &#43; &#43; propriétés pour le débogage distant de projet](../debugger/media/vsrun_cpp_projprop_remote.png "VSRUN_CPP_ProjProp_Remote")  
  
1.  Choisissez **Remote Debugger** dans la liste **Débogueur à lancer** .  
  
2.  Entrez le nom du réseau du périphérique distant dans la zone **Nom de l'ordinateur** . Ou cliquez sur la flèche Bas de la zone pour sélectionner le périphérique dans la boîte de dialogue Sélectionner une connexion du débogueur distant.  
  
 **Spécification du périphérique distant dans une page de projet Visual C# ou Visual Basic**  
  
 ![Propriétés du projet pour le débogage distant managé](../debugger/media/vsrun_managed_projprop_remote.png "VSRUN_Managed_ProjProp_Remote")  
  
1.  Choisissez **Ordinateur distant** dans la liste **Périphérique cible** .  
  
2.  Entrez le nom du réseau du périphérique distant dans la zone **Ordinateur distant** ou cliquez sur **Rechercher** pour sélectionner le périphérique dans la boîte de dialogue **Sélectionner une connexion du débogueur distant** .  
  
##  <a name="BKMK_Deployment_options"></a> Options de déploiement  
 Vous pouvez définir les options de déploiement suivantes sur la page de propriétés de débogage du projet de démarrage.  
  
 **Autoriser le bouclage de réseau**  
 Pour des raisons de sécurité, une application [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] installée en mode standard n'est pas autorisée à effectuer des appels réseau vers le périphérique sur lequel elle est installée. Par défaut, le déploiement Visual Studio crée une exemption à cette règle pour l'application déployée. Cette exemption vous permet de tester les procédures de communication sur un seul ordinateur. Avant d'envoyer votre application au [!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)], vous devez la tester sans l'exemption.  
  
 Pour supprimer de l'application l'exemption du bouclage de réseau :  
  
-   Dans la page de propriétés de débogage C# ou VB, décochez la case **Autoriser le bouclage de réseau** .  
  
-   Dans la page de propriétés de débogage JavaScript ou C++, attribuez à **Autoriser le bouclage de réseau** la valeur **Non**.  
  
 **Ne pas lancer, mais déboguer mon code au démarrage (C# et VB) / Lancer l'application (JavaScript and C++)**  
 Pour configurer le déploiement afin qu'il démarre automatiquement une session de débogage au lancement de l'application :  
  
-   Dans la page de propriétés de débogage C# ou VB, cochez la case **Ne pas lancer, mais déboguer mon code au démarrage** .  
  
-   Dans la page de propriétés de débogage JavaScript ou C++, attribuez à **Lancer l'application** la valeur **Oui**.  
  
## <a name="see-also"></a>Voir aussi  
 [Déboguer un package d’application installés](../debugger/debug-installed-app-package.md).   
 [Exécuter des applications à partir de Visual Studio](../debugger/run-store-apps-from-visual-studio.md)