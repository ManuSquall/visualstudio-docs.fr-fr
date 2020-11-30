---
title: Délais d’expiration des contrôleurs de test et des agents de test
description: Découvrez comment modifier les valeurs de délai d’attente pour le contrôleur de test et l’agent de test en modifiant les fichiers de configuration XML associés.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- agents, configuring
- agetns, timeouts
- controllers, configuring
- controllers, timeouts
ms.assetid: 777d0db5-0073-458a-a2a3-58b1c1f24c60
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9dc661999eb12bb679aa3622f0f14adc3ffc661a
ms.sourcegitcommit: 9ce13a961719afbb389fa033fbb1a93bea814aae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/30/2020
ms.locfileid: "96330002"
---
# <a name="how-to-specify-timeout-periods-for-test-controllers-and-test-agents"></a>Guide pratique pour spécifier les délais d’expiration des contrôleurs de test et des agents de test

Le contrôleur de test et l'agent de test comportent plusieurs paramètres de délai d'attente qui spécifient le délai d'attente des réponses entre eux, ou à partir d'une source de données avant de se solder par un échec avec une erreur. Dans certaines circonstances, il peut être nécessaire de modifier les valeurs du délai d'attente en fonction des besoins de votre topologie ou d'autres problèmes d'environnement. Pour modifier les valeurs du délai d’attente, modifiez le fichier de configuration XML associé au contrôleur de test ou à l’agent de test, comme indiqué dans les procédures suivantes.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Pour modifier les divers paramètres de délai d'attente d'un contrôleur de test ou d'un agent de test, modifiez les fichiers de configuration suivants à l'aide des noms de clé et des valeurs des tables :

- Contrôleur de test : *QTController.exe.config*

    |Nom de clé|Description|Valeur|
    |-|-----------------|-|
    |AgentConnectionTimeoutInSeconds|Nombre de secondes du délai d'attente de la demande de la commande ping de l'agent avant que la connexion ne soit perdue.|"n" secondes.|
    |AgentSyncTimeoutInSeconds|Lorsque vous démarrez une série de tests de synchronisation, nombre de secondes d'attente de la synchronisation de tous les agents avant d'abandonner l'exécution.|"n" secondes.|
    |AgentInitializeTimeout|Nombre de secondes d'attente de l'initialisation de tous les agents et de leurs collecteurs de données initialise au début de l'exécution d'un test, avant d'abandonner la série de tests. Cette valeur doit être raisonnablement élevée si vous utilisez des collecteurs de données.|"n" secondes. Valeur par défaut : "120" (deux minutes).|
    |AgentCleanupTimeout|Nombre de secondes d'attente du nettoyage de tous les agents et de leurs collecteurs de données, avant de compléter la série de tests. Cette valeur doit être raisonnablement élevée si vous utilisez des collecteurs de données.|"n" secondes. Valeur par défaut : "120" (deux minutes).|

- Agent de test : *QTAgentService.exe.config*

    |Nom de clé|Description|Valeur|
    |-|-----------------|-|
    |ControllerConnectionPeriodInSeconds|Nombre de secondes séparant deux tentatives de connexion au contrôleur.|"n" secondes. Valeur par défaut : "30" (trente secondes).|
    |RemotingTimeoutSeconds|Durée maximum d'un appel à distance en secondes.|"n" secondes. Valeur par défaut : "600" (dix minutes).|
    |StopTestRunCallTimeoutInSeconds|Nombre de secondes d'attente l'appel de l'arrêt de la série de tests.|"n" secondes. Valeur par défaut : "120" (deux minutes).|
    |GetCollectorDataTimeout|Nombre de secondes d'attente du collecteur de données.|"n" secondes. Valeur par défaut : "300" (cinq minutes).|

## <a name="to-specify-agent-timeout-options-for-a-test-controller"></a>Pour spécifier les options d’expiration de l’agent d’un contrôleur de test

1. Ouvrez le fichier de configuration XML *QTCcontroller.exe.config* situé dans *% ProgramFiles (x86)% \ Microsoft Visual Studio\2017\Enterprise\Common7\IDE*.

2. Recherchez l’étiquette `<appSettings>`.

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

3. Modifiez une valeur existante pour l'une des clés de délai d'attente du contrôleur de test. Par exemple, vous pouvez remplacer la valeur par défaut de la clé `AgentConnectionTimeoutInSeconds` de 2 minutes par 3 minutes :

    ```xml
    <add key="AgentConnectionTimeoutInSeconds" value="180"/>
    ```

    -ou-

    Ajoutez une clé supplémentaire et spécifiez une valeur de délai d'attente. Par exemple, vous pouvez ajouter la clé `AgentInitializeTimeout` dans la section `<appSettings>` et spécifier une valeur de cinq minutes :

    ```xml
    <appSettings>
            <add key="AgentInitializeTimeout" value="300"/>
    </appSettings>
    ```

## <a name="to-specify-agent-timeout-options-for-a-test-agent"></a>Pour spécifier les options d’expiration de l’agent d’un agent de test

1. Ouvrez le fichier de configuration XML *QTAgentService.exe.config* situé dans *% ProgramFiles (x86)% \ Microsoft Visual Studio\2017\Enterprise\Common7\IDE*.

2. Recherchez l’étiquette `<appSettings>`.

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

3. Modifiez une valeur existante pour l'une des clés de délai d'attente de l'agent de test. Par exemple, vous pouvez remplacer la valeur par défaut de la clé `ControllerConnectionPeriodInSeconds` de trente secondes par une minute :

    ```xml
    <add key="ControllerConnectionPeriodInSeconds" value="60"/>
    ```

    -ou-

    Ajoutez une clé supplémentaire et spécifiez une valeur de délai d'attente. Par exemple, vous pouvez ajouter la clé `RemotingTimeoutSeconds` dans la section `<appSettings>` et spécifier une valeur de quinze minutes :

    ```xml
    <appSettings>
            <add key=" RemotingTimeoutSeconds " value="900"/>
    </appSettings>
    ```

## <a name="see-also"></a>Voir aussi

- [Installer et configurer des agents de test](../test/lab-management/install-configure-test-agents.md)
- [Modifier les paramètres de journalisation du test de charge](../test/modify-load-test-logging-settings.md)
- [Configurer des ports pour les contrôleurs de test et les agents de test](../test/configure-ports-for-test-controllers-and-test-agents.md)
- [Guide pratique pour lier un contrôleur de test ou un agent de test à une carte réseau](../test/how-to-bind-a-test-controller-or-test-agent-to-a-network-adapter.md)
