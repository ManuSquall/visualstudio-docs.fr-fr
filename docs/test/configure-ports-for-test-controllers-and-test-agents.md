---
title: Configurer les ports des contrôleurs de test et des agents de test
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- firewalls, configuring for test agents
- firewalls, configuring for test controllers
- test agents, firewalls
- test controllers, firewalls
- agents, firewalls
- controllers, firewalls
ms.assetid: 211edbd7-9fe4-4251-ba85-8bec4363261b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2228f5ac4dce4743fa6dafbb321f0106b5d6cc11
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595941"
---
# <a name="configure-ports-for-test-controllers-and-test-agents"></a>Configurer les ports des contrôleurs de test et des agents de test

Vous pouvez modifier les ports entrants par défaut utilisés par le contrôleur de test, l'agent de test et le client. Cela peut s'avérer nécessaire si vous essayez d'utiliser le contrôleur de test, l'agent de test ou le client avec un autre logiciel qui entre en conflit avec les paramètres de port. Une autre raison motivant le changement de ports est la restriction de pare-feu entre le contrôleur de test et le client. Dans ce cas, vous pouvez configurer manuellement le port pour l'activer pour un pare-feu afin que le contrôleur de test puisse envoyer des résultats au client.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

L’illustration suivante montre les points de connexion entre le contrôleur de test, l’agent de test et le client. Elle décrit les ports utilisés pour les connexions entrantes et sortantes ainsi que les restrictions de sécurité sur ces ports.

![Ports et sécurité du contrôleur de test et de l’agent de test](../test/media/test-controller-agent-firewall.png)

## <a name="incoming-connections"></a>Connexions entrantes

Le port par défaut utilisé par le contrôleur de test est 6901 et le port par défaut de l’agent de test est 6910. Le client utilise un port aléatoire par défaut qui est utilisé pour recevoir les résultats de test du contrôleur de test. Pour toutes les connexions entrantes, le contrôleur de test authentifie l'abonné appelant et vérifie s'il appartient à un groupe de sécurité spécifique.

- **Test Controller** Les connexions entrantes s’effectuent sur le port TCP 6901. Si cela s'avère nécessaire, vous pouvez configurer le port entrant. Pour plus d’informations, voir [Configurer les ports entrants](#configure-the-incoming-ports).

    Le contrôleur de test doit être en mesure d'établir la connexion sortante vers les agents de test et le client.

    > [!NOTE]
    > Le contrôleur de test a besoin d’une connexion **Partage de fichiers et d’imprimantes** entrante ouverte.

- **Test Agent** Les connexions entrantes s’effectuent sur le port TCP 6910. Si cela s'avère nécessaire, vous pouvez configurer le port entrant. Pour plus d’informations, voir [Configurer les ports entrants](#configure-the-incoming-ports).

   L'agent de test doit être en mesure d'établir une connexion sortante vers le contrôleur de test.

- **Client** Par défaut, un port TCP aléatoire est utilisé pour les connexions entrantes. Si cela s'avère nécessaire, vous pouvez configurer le port entrant. Pour plus d’informations, voir [Configurer les ports entrants](#configure-the-incoming-ports).

   Vous pouvez obtenir des notifications de pare-feu lorsque le contrôleur de test essaie de se connecter au client pour la première fois.

   Sur Windows Server 2008, les notifications pare-feu sont désactivées par défaut et vous devez ajouter manuellement des exceptions pare-feu pour les programmes clients (*devenv.exe*, *mstest.exe*, *mlm.exe*) afin qu’il puisse accepter les connexions entrantes.

## <a name="outgoing-connections"></a>Connexions sortantes

Des ports TCP aléatoires sont utilisés pour toutes les connexions sortantes.

- **Test Controller** Le contrôleur de test doit pouvoir établir la connexion sortante vers les agents et le client.

- **Test Agent** L’agent de test doit pouvoir établir une connexion sortante vers le contrôleur.

- **Client** Le client doit pouvoir établir la connexion sortante vers le contrôleur.

## <a name="configure-the-incoming-ports"></a>Configurer les ports entrants

Suivez les instructions ci-après pour configurer les ports d'un contrôleur de test et des agents de test.

- **Service de contrôleur** Modifier la valeur du port en éditant le *fichier %ProgramFiles(x86)%-Microsoft Visual Studio-2017-Enterprise-Common7-IDE-QTCcontroller.exe.config* :

    ```xml
    <appSettings>
      <add key="ControllerServicePort" value="6901"/>
    </appSettings>
    ```

- **Service d’agent** Modifier le port en éditant le *fichier %ProgramFiles(x86)%-Microsoft Visual Studio-2017-Enterprise-Common7-IDE-QTAgentService.exe.config* :

    ```xml
    <appSettings>
      <add key="AgentServicePort" value="6910"/>
    </appSettings>
    ```

- **Client** Utilisez l’éditeur du registre pour ajouter les valeurs suivantes du registre **(DWORD).** Le client utilisera l'un des ports de la plage spécifiée pour la réception des données envoyées par le contrôleur de test :

     **HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\VisualStudio\12.0\EnterpriseTools\QualityTools\ListenPortRange\PortRangeStart**

     **HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\VisualStudio\12.0\EnterpriseTools\QualityTools\ListenPortRange\PortRangeEnd**

## <a name="see-also"></a>Voir aussi

- [Installer et configurer des agents de test](../test/lab-management/install-configure-test-agents.md)
