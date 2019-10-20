---
title: Lier un contrôleur de test ou un agent de test à une carte réseau
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- controllers, netwrok adapter
- agents, configuring
- agents, network adapter
- controllers, configuring
ms.assetid: 7eb9290a-f9f6-4e41-9caa-796fcfaf0610
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b0dc70169deb8d09fed45bcb921c783765e87c0e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72643781"
---
# <a name="how-to-bind-a-test-controller-or-test-agent-to-a-network-adapter"></a>Guide pratique pour lier un contrôleur de test ou un agent de test à une carte réseau

Si un ordinateur, sur lequel le contrôleur de test ou l’agent de test est installé, a plusieurs cartes réseau, vous devez spécifier l’adresse IP à la place du nom de l’ordinateur pour identifier le contrôleur de test ou l’agent de test.

> [!WARNING]
> Lors de la configuration d'un agent de test, vous pouvez recevoir l'erreur suivante :
>
> **Erreur 8110. Impossible de se connecter à l’ordinateur contrôleur spécifié ou d’accéder à l’objet contrôleur**
>
> Cette erreur peut être provoquée par l'installation du contrôleur de test sur un ordinateur doté de plusieurs cartes réseau. Il est également possible d'installer avec succès des agents et de ne pas rencontrer ce problème avant d'exécuter un test.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="bind-a-test-controller-to-a-specific-network-adapter"></a>Liaison entre un contrôleur de test et une carte réseau spécifique

### <a name="to-obtain-the-ip-addresses-of-the-network-adapters"></a>Pour obtenir l'adresse IP des cartes réseau

1. Dans Microsoft Windows, choisissez **Démarrer**, dans la zone **Rechercher**, tapez **cmd**, puis choisissez **Entrée**.

2. Tapez **ipconfig /all**.

     Les adresses IP de vos cartes réseau s'affichent. Enregistrez l'adresse IP de la carte réseau à laquelle vous souhaitez lier votre contrôleur.

### <a name="to-bind-a-network-adapter-to-a-test-controller"></a>Pour lier une carte réseau à un contrôleur de test

1. Dans Microsoft Windows, choisissez **Démarrer**, dans la zone **Rechercher**, tapez **services.msc**, puis choisissez **Entrée**.

     La boîte de dialogue **Services** s’affiche.

2. Dans le volet de résultats, sous la colonne **Nom**, cliquez avec le bouton droit sur le service **Visual Studio Test Controller**, puis choisissez **Arrêter**.

     ou

     Ouvrez une invite de commandes élevée et exécutez la commande suivante à une commande :

     `net stop vsttcontroller`

3. Ouvrez le fichier de configuration XML *QTCcontroller.exe.config* qui se trouve dans *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\\\<édition>\Common7\IDE*.

4. recherchez la balise `<appSettings>`.

    ```xml
    <appSettings>
      <add key="LogSizeLimitInMegs" value="20"/>
      <add key="AgentConnectionTimeoutInSeconds" value="120"/>
      <add key="AgentSyncTimeoutInSeconds" value="300"/>
      <add key="ControllerServicePort" value="6901"/>
      <add key="ControllerUsersGroup" value="TeamTestControllerUsers"/>
      <add key="ControllerAdminsGroup" value="TeamTestControllerAdmins"/>
      <add key="CreateTraceListener" value="no"/>
    </appSettings>
    ```

5. Ajoutez la clé `BindTo` pour spécifier la carte réseau à utiliser dans la section `<appSettings>`.

    ```xml
            <add key="BindTo" value="<YOUR IP ADDRESS>"/>
    </appSettings>
    ```

6. Démarrez le service du contrôleur de test. Pour cela, exécutez la commande suivante à l'invite de commande :

    `net start vsttcontroller`

    > [!WARNING]
    > Vous devez encore exécuter l'installation de l'agent de test pour connecter l'agent de test au contrôleur. Cette fois, spécifiez l'adresse IP du contrôleur à la place de son nom.

     Cela s'applique au contrôleur, au service Agent et au processus Agent. La propriété `BindTo` doit être définie pour chaque processus qui s'exécute sur un ordinateur doté de plusieurs cartes réseau. La procédure permettant de définir la propriété `BindTo` est la même pour les trois processus et correspond à celle spécifiée précédemment dans cette rubrique pour le contrôleur de test.

### <a name="to-bind-a-network-interface-card-to-a-test-agent"></a>Pour lier une carte d’interface réseau à un agent de test

1. Dans Microsoft Windows, choisissez **Démarrer**, dans la zone **Rechercher**, tapez **services.msc**, puis choisissez **Entrée**.

    La boîte de dialogue **Services** s’affiche.

2. Dans le volet de résultats, sous la colonne **Nom**, cliquez avec le bouton droit sur le service **Visual Studio Test Agent**, puis choisissez **Arrêter**.

     ou

     Ouvrez une invite de commandes élevée et exécutez la commande suivante à une commande :

     **net stop vsttagent**

3. Ouvrez le fichier de configuration XML *QTAgentService.exe.config* qui se trouve dans *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\\\<édition>\Common7\IDE*.

4. recherchez la balise `<appSettings>`.

    ```xml
    <appSettings>
      <appSettings>
      <add key="LogSizeLimitInMegs" value="20"/>
      <add key="AgentServicePort" value="6910"/>
      <add key="ControllerConnectionPeriodInSeconds" value="30"/>
      <add key="StopTestRunCallTimeoutInSeconds" value="120"/>
      <add key="CreateTraceListener" value="no"/>
      <add key="GetCollectorDataTimeout" value="300"/>
    </appSettings>  </appSettings>
    ```

5. Ajoutez la clé `BindTo` pour spécifier la carte réseau à utiliser dans la section `<appSettings>`.

    ```xml
            <add key="BindTo" value="<YOUR IP ADDRESS>"/>
    </appSettings>
    ```

6. Démarrez le service de l’agent de test. Pour cela, exécutez la commande suivante à l'invite de commande :

    `net start vsttagent`

## <a name="see-also"></a>Voir aussi

- [Installer et configurer des agents de test](../test/lab-management/install-configure-test-agents.md)
- [Modifier les paramètres de journalisation du test de charge](../test/modify-load-test-logging-settings.md)
- [Configurer les ports des contrôleurs de test et des agents de test](../test/configure-ports-for-test-controllers-and-test-agents.md)
- [Guide pratique pour spécifier durées du délai d’expiration des contrôleurs de test et des agents de test](../test/how-to-specify-timeout-periods-for-test-controllers-and-test-agents.md)