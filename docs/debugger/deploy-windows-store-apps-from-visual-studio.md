---
title: Déployer des applications UWP | Microsoft Docs
ms.custom: seodec18
ms.date: 01/16/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: 63726f9f38cdede6c8a0525b74244baac9455aad
ms.sourcegitcommit: d4bea2867a4f0c3b044fd334a54407c0fe87f9e8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/01/2019
ms.locfileid: "58790379"
---
# <a name="deploy-uwp-apps-from-visual-studio"></a>Déployer des applications UWP à partir de Visual Studio

La fonctionnalité de déploiement de Visual Studio génère et inscrit les applications UWP qui sont créées avec Visual Studio sur un appareil cible. La façon dont l'application est exactement enregistrée varie selon que le périphérique cible est local ou distant :

- Lorsque la cible est l'ordinateur Visual Studio local, Visual Studio enregistre l'application depuis son dossier de génération.

- Lorsque la cible est un périphérique distant, Visual Studio copie les fichiers requis sur l'ordinateur distant et enregistre l'appareil sur ce périphérique.

Le déploiement est automatique quand vous déboguez votre application à partir de Visual Studio à l’aide de l’option **Démarrer le débogage** (touche F5) ou de l’option **Exécuter sans débogage** (touches CTRL+F5). Vous pouvez aussi déployer votre application manuellement. Le déploiement manuel est utile dans les scénarios suivants :

- Test ad hoc sur un ordinateur local ou distant.

- Déploiement d'une application qui démarre une autre application que vous voulez déboguer.

- Déploiement d'une application qui est déboguée quand elle est démarrée par une autre application ou méthode.

##  <a name="BKMK_How_to_deploy_a_Windows_Store_app"></a> Comment déployer une application UWP
 Le déploiement manuel d'une application obéit à une procédure simple :

1.  Si le déploiement s'effectue sur un périphérique distant, spécifiez le nom ou l'adresse IP du périphérique dans la page des propriétés du projet du projet de démarrage de l'application. (Les étapes associées sont répertoriées plus bas dans cette rubrique.)

2.  Dans la barre d'outils Déboguer de Visual Studio, choisissez la cible de déploiement dans la liste déroulante située à côté du bouton **Démarrer le débogage** .

     ![Exécuter sur l’ordinateur Local](../debugger/media/vsrun_f5_local.png "VSRUN_F5_Local")

3.  Dans le menu **Générer** , choisissez **Déployer**.

##  <a name="BKMK_How_to_specify_a_remote_device"></a> Comment spécifier un périphérique distant

**Composants requis**

Sur un appareil distant Windows 10, vous devez activer [mode développeur](/windows/uwp/get-started/enable-your-device-for-development). Sur les appareils Windows 10 exécutant Update Creators ou une version ultérieure, les outils à distance sont installés automatiquement lorsque vous déployez votre application. Pour plus d’informations, consultez [déboguer un package d’application installé](../debugger/debug-installed-app-package.md).

> [!NOTE]
> Sur les versions de mise à jour du pre-créateur de Windows 10, les outils à distance pour Visual Studio doit être installés sur le périphérique distant, et le débogueur distant doit être en cours d’exécution.

Le déploiement utilise le canal réseau du débogueur distant pour envoyer les fichiers de l'application sur le périphérique distant.

#### <a name="to-specify-a-remote-device"></a>Pour spécifier un périphérique distant

1. Dans la page de propriétés de débogage du projet de démarrage, spécifiez le nom ou l'adresse IP d'une cible de déploiement distante.

2. Pour ouvrir la page de propriétés de débogage, sélectionnez le projet dans l'Explorateur de solutions, puis choisissez **Propriétés** dans le menu contextuel.

3. Sélectionnez ensuite le nœud **Déboguer** dans la fenêtre de la page de propriétés.

4. Pour **appareil cible**, sélectionnez **Machine distante**.

5. Sous **machine distante**, cliquez sur **trouver**.

6. Vous pouvez taper le nom ou l’adresse IP du périphérique distant, ou vous pouvez choisir l’appareil à partir de la **connexion à distance** boîte de dialogue.

    ![Boîte de dialogue de connexion du débogueur distant sélectionnez](../debugger/media/vsrun_selectremotedebuggerdlg.png "VSRUN_SelectRemoteDebuggerDlg")

    Le **connexion à distance** boîte de dialogue affiche les périphériques sur le sous-réseau du réseau local et n’importe quel appareil qui est directement connecté à l’ordinateur Visual Studio via un câble Ethernet.

   **Spécification du périphérique distant dans une page de projet Visual C++**

   ![C&#43; &#43; projeter des propriétés pour le débogage distant](../debugger/media/vsrun_cpp_projprop_remote.png "VSRUN_CPP_ProjProp_Remote")

7. Choisissez **Remote Debugger** dans la liste **Débogueur à lancer** .

8. Entrez le nom du réseau du périphérique distant dans la zone **Nom de l'ordinateur** . Ou cliquez sur la flèche Bas de la zone pour sélectionner le périphérique dans la boîte de dialogue Sélectionner une connexion du débogueur distant.

   **Spécification du périphérique distant dans une page de projet Visual C# ou Visual Basic**

   ![Propriétés du projet pour le débogage distant managé](../debugger/media/vsrun_managed_projprop_remote.png "VSRUN_Managed_ProjProp_Remote")

9. Choisissez **Ordinateur distant** dans la liste **Périphérique cible** .

10. Entrez le nom du réseau du périphérique distant dans la zone **Ordinateur distant** ou cliquez sur **Rechercher** pour sélectionner le périphérique dans la boîte de dialogue **Sélectionner une connexion du débogueur distant** .

##  <a name="BKMK_Deployment_options"></a> Options de déploiement

Vous pouvez définir les options de déploiement suivantes sur la page de propriétés de débogage du projet de démarrage.

**Autoriser le bouclage de réseau**

Pour des raisons de sécurité, une UWP ou [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] application est installée en mode standard n’est pas autorisée à effectuer des appels réseau à l’appareil n’est installé sur. Par défaut, le déploiement Visual Studio crée une exemption à cette règle pour l'application déployée. Cette exemption vous permet de tester les procédures de communication sur un seul ordinateur. Avant d'envoyer votre application au [!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)], vous devez la tester sans l'exemption.

Pour supprimer de l'application l'exemption du bouclage de réseau :

- Sur le C# et Visual Basic page Propriétés de débogage, désactivez le **autoriser le bouclage de réseau** case à cocher.

- Sur la page de propriétés de débogage C++, définissez le **autoriser le bouclage de réseau** valeur **non**.

**Ne pas lancer, mais déboguer mon code au démarrage (C# et Visual Basic) / lancer d’Application (C++)**

Pour configurer le déploiement afin qu'il démarre automatiquement une session de débogage au lancement de l'application :

- Sur le C# et page de propriétés de débogage de Visual Basic, vérifiez le **ne pas lancer, mais déboguer mon code au démarrage** case à cocher.

- Sur la page de propriétés de débogage C++, définissez le **lancer l’Application** valeur **Oui**.

## <a name="see-also"></a>Voir aussi

- [Options avancées de déploiement à distance](/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps#advanced-remote-deployment-options)
- [Déboguer un package d'application installé](../debugger/debug-installed-app-package.md)
- [Exécuter des applications à partir de Visual Studio](/visualstudio/debugger/debugging-windows-store-and-windows-universal-apps)
