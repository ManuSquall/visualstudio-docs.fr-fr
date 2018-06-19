---
title: Taille du fichier journal pour les tests de charge dans Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, logging
ms.assetid: 417059bf-37ae-4e7a-b9b0-29bd71f1414f
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 7faf5402f495eefe64000c67048bcb85c9197388
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31965084"
---
# <a name="how-to-specify-the-maximum-size-for-the-log-file-for-load-tests"></a>Guide pratique pour spécifier la taille maximale du fichier journal pour les tests de charge

Par défaut, la taille maximale du fichier journal utilisé pour les tests de charge a pour valeur 20 mégaoctets. Vous pouvez changer cette valeur en modifiant le fichier de configuration associé au service du contrôleur.

## <a name="specify-the-maximum-log-file-size-for-load-test"></a>Spécifier la taille maximale du fichier journal pour le test de charge

1.  Ouvrez le fichier de configuration XML *QTCcontroller.exe.config* qui se trouve dans %ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\QTCcontroller.exe.config.

2.  Recherchez l'entrée `<add key="LogSizeLimitInMegs" value="20"/>` sous la balise `<appSettings>`.

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

3.  Modifiez `value ="20"` en choisissant la taille maximale autorisée que vous souhaitez spécifier pour le fichier journal.

    > [!NOTE]
    > L'entrée d'une valeur « 0 » indique que la taille du fichier journal est limitée uniquement par l'espace disque disponible.

## <a name="see-also"></a>Voir aussi

- [Modification des paramètres de journalisation du test de charge](../test/modify-load-test-logging-settings.md)
- [Configuration des ports pour les contrôleurs de test et les agents de test](../test/configure-ports-for-test-controllers-and-test-agents.md)