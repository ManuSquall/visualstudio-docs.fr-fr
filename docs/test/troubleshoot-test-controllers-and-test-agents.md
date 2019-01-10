---
title: Résolution des problèmes des contrôleurs de test et des agents de test
ms.date: 10/20/2016
ms.topic: troubleshooting
helpviewer_keywords:
- load tests, test controllers
- load tests, troubleshooting
- load tests, test agents
- troubleshooting, test controllers and agents in load tests
ms.assetid: 77329348-3a5d-43de-b6cb-90f93296a081
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.openlocfilehash: abd5b690e828bad4e457514091a79b5ddcf1e7e6
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53935123"
---
# <a name="strategies-for-troubleshooting-test-controllers-and-test-agents-in-load-tests"></a>Stratégies de résolution des problèmes des contrôleurs de test et des agents de test lors de tests de charge

Cet article décrit certains problèmes courants que vous pouvez rencontrer quand vous utilisez des contrôleurs de test et agents de test dans Visual Studio.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

##  <a name="unable-to-collect-performance-counters-on-test-agent-computer"></a>Impossible de collecter les compteurs de performances sur un ordinateur d’agent de test

Lors de l’exécution d’un test de charge, vous pouvez recevoir des erreurs si vous tentez de vous connecter à un ordinateur d’agent de test et de collecter les compteurs de performance. Le service Registre distant est le service chargé de fournir les données de compteur de performance à un ordinateur distant. Sur certains systèmes d’exploitation, le service Registre à distance ne démarre pas automatiquement. Pour résoudre ce problème, démarrez manuellement le service Registre distant.

> [!NOTE]
> Vous pouvez accéder au service Registre à distance dans le **Panneau de configuration**. Choisissez **Outils d’administration**, puis **Services**.

Ce problème peut être également dû au fait que vous ne disposez pas d'autorisations suffisantes pour lire les compteurs de performance. Pour les séries de tests locales, le compte de l'utilisateur qui exécute le test doit être membre du groupe Utilisateurs avec pouvoir (ou d'un groupe disposant d'autorisations supérieures) ou du groupe Utilisateurs de l'Analyseur de performances. Pour les séries de tests distantes, le contrôleur est configuré pour s'exécuter sous un compte qui doit être membre du groupe Utilisateurs avec pouvoir (ou d'un groupe disposant d'autorisations supérieures) ou du groupe Utilisateurs de l'Analyseur de performances.

## <a name="set-the-logging-level-on-a-test-controller-computer"></a>Définir le niveau de journalisation sur un ordinateur contrôleur de test

Vous pouvez contrôler le niveau de journalisation sur un ordinateur contrôleur de test. Cette opération s'avère utile si vous tentez de diagnostiquer un problème lors de l'exécution d'un test de charge sur un environnement.

### <a name="to-set-the-logging-level-on-a-test-controller-computer"></a>Pour définir le niveau de journalisation sur un ordinateur contrôleur de test

1.  Arrêtez le service du contrôleur de test. À l’invite de commandes, tapez `net stop vsttcontroller`.

2.  Ouvrez le fichier *QTController.exe.config*. Ce fichier se trouve dans le répertoire d'installation du contrôleur.

3.  Modifiez l'entrée pour le commutateur `EqtTraceLevel` dans la section des diagnostics du système du fichier. Votre code doit être semblable au suivant :

    ```xml
    <system.diagnostics>
        <trace autoflush="true" indentsize="4">
            <listeners>
                <add name="myListener" type="System.Diagnostics.TextWriterTraceListener" initializeData="d:\VSTestHost.log" />
            </listeners>
        </trace>
        <switches>
            <!-- You must use integral values for "value":
                    0 = off,
                    1 = error,
                    2 = warn,
                    3 = info,
                    4 = verbose. -->
            <add name="EqtTraceLevel" value="4" />
        </switches>
    </system.diagnostics>
    ```

4.  Enregistrez le fichier.

5.  Démarrez le service du contrôleur. À l’invite de commandes, tapez `net start vsttcontroller`.

Cette procédure s’applique aux processus du contrôleur de test, du service d’agent de test et de l’agent de test. Lors du diagnostic de problèmes, il est utile d'activer la journalisation pour les trois processus. La procédure permettant de définir le niveau de journalisation est la même pour les trois processus et correspond à celle spécifiée précédemment pour le contrôleur de test. Pour définir les niveaux de journalisation pour les processus du service d’agent de test et de l’agent, utilisez les fichiers de configuration suivants :

-   *QTController.exe.config* (service de contrôleur)

-   *QTAgentService.exe.config* (service Agent)

-   *QTDCAgent(32).exe.config* (processus d’adaptateur de données Agent pour architecture 32 bits)

-   *QTDCAgent(64).exe.config* (processus d’adaptateur de données Agent pour architecture 64 bits)

-   *QTAgent(32).exe.config* (processus de test Agent pour architecture 32 bits)

-   *QTAgent(64).exe.config* (processus de test Agent pour architecture 64 bits)

## <a name="bind-a-test-controller-to-a-network-adapter"></a>Lier un contrôleur de test à une carte réseau

Lors de la configuration d’un agent de test, vous pouvez recevoir l’erreur suivante :

**Erreur 8110. Impossible de se connecter à l’ordinateur contrôleur spécifié ou d’accéder à l’objet contrôleur.**

Cette erreur peut être provoquée par l'installation du contrôleur de test sur un ordinateur doté de plusieurs cartes réseau.

> [!NOTE]
> Il est également possible que vous réussissiez à installer les agents de test et que nous ne rencontriez pas ce problème tant que vous n’essayez pas d’exécuter un test.

Pour corriger cette erreur, vous devez lier le contrôleur de test à l'une des cartes réseau. Vous devez définir la propriété `BindTo` sur le contrôleur de test, puis modifier l'agent de test de sorte qu'il fasse référence au contrôleur de test par son adresse IP, plutôt que par son nom. Les étapes sont indiquées dans les procédures suivantes.

### <a name="to-obtain-the-ip-address-of-the-network-adapter"></a>Pour obtenir l'adresse IP de la carte réseau

1.  Choisissez **Démarrer**, puis **Exécuter**.

     La boîte de dialogue **Exécuter** s’affiche.

2.  Tapez `cmd`, puis choisissez **OK**.

     Une invite de commandes s'ouvre.

3.  Tapez `ipconfig /all`.

     Les adresses IP de vos cartes réseau s'affichent. Enregistrez l'adresse IP de la carte réseau à laquelle vous souhaitez lier votre contrôleur.

### <a name="to-bind-a-test-controller-to-a-network-adapter"></a>Pour lier un contrôleur de test à une carte réseau

1.  Arrêtez le service du contrôleur de test. À l’invite de commandes, tapez `net stop vsttcontroller`.

2.  Ouvrez le fichier *QTController.exe.config*. Ce fichier se trouve sous *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE*.

3.  Ajoutez une entrée pour la propriété `BindTo` aux paramètres d'application. Spécifiez l'adresse IP de la carte réseau à laquelle vous souhaitez lier le contrôleur. Votre code doit être semblable au suivant :

    ```xml
    <appSettings>
        <add key="LogSizeLimitInMegs" value="20" />
        <add key="AgentSyncTimeoutInSeconds" value="120" />
        <add key="ControllerServicePort" value="6901" />
        <add key="ControllerUsersGroup" value="TeamTestControllerUsers" />
        <add key="ControllerAdminsGroup" value="TeamTestControllerAdmins" />
        <add key="CreateTraceListener" value="no" />
        <add key="BindTo" value="<YOUR IP ADDRESS>" />
    </appSettings>
    ```

4.  Enregistrez le fichier.

5.  Démarrez le service du contrôleur de test. À l’invite de commandes, tapez `net start vsttcontroller`.

### <a name="to-connect-a-test-agent-to-a-bound-controller"></a>Pour connecter un agent de test à un contrôleur lié

-   Réexécutez l'installation de l'agent de test. Cette fois, spécifiez l'adresse IP du contrôleur de test à la place de son nom.

Cette procédure s’applique aux processus du contrôleur de test, du service d’agent de test et de l’agent de test. La propriété `BindTo` doit être définie pour chaque processus qui s'exécute sur un ordinateur doté de plusieurs cartes réseau. La procédure permettant de définir la propriété `BindTo` est la même pour les trois processus et correspond à celle spécifiée précédemment pour le contrôleur de test. Si vous souhaitez définir les niveaux de journalisation pour les processus du service d’agent de test et de l’agent, utilisez les fichiers de configuration répertoriés dans [Définir le niveau de journalisation sur un ordinateur contrôleur de test](#set-the-logging-level-on-a-test-controller-computer).

## <a name="see-also"></a>Voir aussi

- [Contrôleurs de test et agents de test](../test/configure-test-agents-and-controllers-for-load-tests.md)
