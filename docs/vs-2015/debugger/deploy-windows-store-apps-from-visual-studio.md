---
title: Déployer des applications du Windows Store
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: ef3a0f36-bfc9-4ca0-aa61-18261f619bff
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 73b4350a2e7f277a11f4d6650d8089df0f87fe4d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68177476"
---
# <a name="deploy-windows-store-apps-from-visual-studio"></a>Déployer des applications du Windows Store à partir de Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

S’applique uniquement à Windows] (.. /Image/windows_only_content.png « windows_only_content »)

 La fonctionnalité de déploiement de Visual Studio génère et enregistre les applications du Windows Store créées avec Visual Studio sur un périphérique cible. La façon dont l'application est exactement enregistrée varie selon que le périphérique cible est local ou distant :

- Lorsque la cible est l'ordinateur Visual Studio local, Visual Studio enregistre l'application depuis son dossier de génération.

- Lorsque la cible est un périphérique distant, Visual Studio copie les fichiers requis sur l'ordinateur distant et enregistre l'appareil sur ce périphérique.

  Le déploiement est automatique lorsque vous déboguez votre application à partir de Visual Studio à l’aide de la **démarrer le débogage** option (clavier : F5) ou le **démarrer sans débogage** option (clavier : CTRL + F5). Vous pouvez aussi déployer votre application manuellement. Le déploiement manuel est utile dans les scénarios suivants :

- Test ad hoc sur un ordinateur local ou distant.

- Déploiement d'une application qui démarre une autre application que vous voulez déboguer.

- Déploiement d'une application qui est déboguée quand elle est démarrée par une autre application ou méthode.

## <a name="BKMK_In_this_topic"></a> Dans cette rubrique
 Dans cette rubrique, vous pouvez apprendre :

 [Comment déployer une application du Windows Store](#BKMK_How_to_deploy_a_Windows_Store_app)

 [Comment spécifier un périphérique distant](#BKMK_How_to_specify_a_remote_device)

 [Options de déploiement](#BKMK_Deployment_options)

## <a name="BKMK_How_to_deploy_a_Windows_Store_app"></a> Comment déployer une application du Windows Store
 Le déploiement manuel d'une application obéit à une procédure simple :

1. Si le déploiement s'effectue sur un périphérique distant, spécifiez le nom ou l'adresse IP du périphérique dans la page des propriétés du projet du projet de démarrage de l'application. (Les étapes associées sont répertoriées plus bas dans cette rubrique.)

2. Dans la barre d'outils Déboguer de Visual Studio, choisissez la cible de déploiement dans la liste déroulante située à côté du bouton **Démarrer le débogage** .

     ![Exécuter sur l’ordinateur Local](../debugger/media/vsrun-f5-local.png "VSRUN_F5_Local")

3. Dans le menu **Générer** , choisissez **Déployer**.

## <a name="BKMK_How_to_specify_a_remote_device"></a> Comment spécifier un périphérique distant
 **Conditions préalables**

 Pour déployer une application sur un périphérique distant :

- Une licence de développeur doit être installée sur le périphérique distant.

- Les outils de contrôle à distance Visual Studio doivent être installés sur le périphérique distant et le Remote Debugging Monitor doit être en cours d'exécution.

     Le déploiement utilise le canal réseau du débogueur distant pour envoyer les fichiers de l'application sur le périphérique distant.

#### <a name="to-specify-a-remote-device"></a>Pour spécifier un périphérique distant

1. Dans la page de propriétés de débogage du projet de démarrage, spécifiez le nom ou l'adresse IP d'une cible de déploiement distante.

2. Pour ouvrir la page de propriétés de débogage, sélectionnez le projet dans l'Explorateur de solutions, puis choisissez **Propriétés** dans le menu contextuel.

3. Sélectionnez ensuite le nœud **Déboguer** dans la fenêtre de la page de propriétés.

4. Vous pouvez entrer le nom ou l'adresse IP du périphérique distant, ou choisir le périphérique dans la boîte de dialogue **Sélectionner une connexion du débogueur distant** .

    ![Boîte de dialogue de connexion du débogueur distant sélectionnez](../debugger/media/vsrun-selectremotedebuggerdlg.png "VSRUN_SelectRemoteDebuggerDlg")

    La boîte de dialogue **Sélectionner une connexion du débogueur distant** affiche les périphériques situés sur le sous-réseau du réseau local et tout périphérique qui est directement connecté à l'ordinateur Visual Studio via un câble Ethernet.

   **Spécification du périphérique distant dans une page de projet JavaScript ou Visual C++**

   ![C&#43; &#43; projeter des propriétés pour le débogage distant](../debugger/media/vsrun-cpp-projprop-remote.png "VSRUN_CPP_ProjProp_Remote")

5. Choisissez **Remote Debugger** dans la liste **Débogueur à lancer** .

6. Entrez le nom du réseau du périphérique distant dans la zone **Nom de l'ordinateur** . Ou cliquez sur la flèche Bas de la zone pour sélectionner le périphérique dans la boîte de dialogue Sélectionner une connexion du débogueur distant.

   **Spécification du périphérique distant dans une page de projet Visual C# ou Visual Basic**

   ![Propriétés du projet pour le débogage distant managé](../debugger/media/vsrun-managed-projprop-remote.png "VSRUN_Managed_ProjProp_Remote")

7. Choisissez **Ordinateur distant** dans la liste **Périphérique cible** .

8. Entrez le nom du réseau du périphérique distant dans la zone **Ordinateur distant** ou cliquez sur **Rechercher** pour sélectionner le périphérique dans la boîte de dialogue **Sélectionner une connexion du débogueur distant** .

## <a name="BKMK_Deployment_options"></a> Options de déploiement
 Vous pouvez définir les options de déploiement suivantes sur la page de propriétés de débogage du projet de démarrage.

 **Autoriser le bouclage de réseau** pour des raisons de sécurité, un [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] application est installée en mode standard n’est pas autorisée à effectuer des appels réseau à l’appareil n’est installé sur. Par défaut, le déploiement Visual Studio crée une exemption à cette règle pour l'application déployée. Cette exemption vous permet de tester les procédures de communication sur un seul ordinateur. Avant d'envoyer votre application au [!INCLUDE[win8_appstore_long](../includes/win8-appstore-long-md.md)], vous devez la tester sans l'exemption.

 Pour supprimer de l'application l'exemption du bouclage de réseau :

- Dans la page de propriétés de débogage C# ou VB, décochez la case **Autoriser le bouclage de réseau** .

- Dans la page de propriétés de débogage JavaScript ou C++, attribuez à **Autoriser le bouclage de réseau** la valeur **Non**.

  **Ne pas lancer, mais déboguer mon code au démarrage (C# et VB) / lancer l’Application (JavaScript et C++)** pour configurer le déploiement pour démarrer automatiquement une session de débogage lorsque l’application est lancée :

- Dans la page de propriétés de débogage C# ou VB, cochez la case **Ne pas lancer, mais déboguer mon code au démarrage** .

- Dans la page de propriétés de débogage JavaScript ou C++, attribuez à **Lancer l'application** la valeur **Oui**.

## <a name="see-also"></a>Voir aussi
 [Exécuter des applications à partir de Visual Studio](../debugger/run-store-apps-from-visual-studio.md)
