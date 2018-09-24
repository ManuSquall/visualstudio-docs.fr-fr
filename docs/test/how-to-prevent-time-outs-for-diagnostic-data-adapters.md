---
title: Délais d’attente des adaptateurs de données de diagnostic dans Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Diagnostic Data Adapter, increasing time-outs
ms.assetid: 39fff4fc-9233-4f67-96ac-e81bbaf7ca82
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 8359aa76dc2f62afb63f6a36984492210d9aeeff
ms.sourcegitcommit: 495bba1d8029646653f99ad20df2f80faad8d58b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/31/2018
ms.locfileid: "39380012"
---
# <a name="how-to-prevent-time-outs-for-diagnostic-data-adapters"></a>Guide pratique pour éviter les dépassements des délais d’expiration des adaptateurs de données de diagnostic

Si vous utilisez des adaptateurs de données de diagnostic dans les paramètres de tests, un délai d'expiration peut se produire lorsque vous démarrez votre série de tests pour l'une des raisons suivantes :

-   Le service de contrôleur de test n'est pas exécuté sur l'ordinateur de contrôleur de test. Vous devez peut-être redémarrer le service. Pour plus d’informations sur la façon de déterminer votre contrôleur de test et de gérer les contrôleurs de test, consultez [Gérer les contrôleurs de test et les agents de test avec Visual Studio](../test/manage-test-controllers-and-test-agents.md).

-   Si vous collectez des données sur un ordinateur distant, le pare-feu peut bloquer Microsoft Test Manager. L’ordinateur qui exécute Microsoft Test Manager doit accepter les connexions entrantes du contrôleur de test. Un délai d’expiration se produit quand Microsoft Test Manager ne reçoit pas de message du contrôleur parce qu’il est bloqué par le pare-feu. Vous devez vérifier les paramètres de votre pare-feu sur l’ordinateur qui exécute Microsoft Test Manager.

-   Le contrôleur de test ne peut pas convertir le nom de l’ordinateur qui exécute Microsoft Test Manager. Cela peut se produire si le DNS fournit l'adresse incorrecte de cet ordinateur. Vous devrez peut-être contacter l'administrateur réseau pour résoudre ce problème.

Lorsque vous exécutez un long test qui doit collecter un volume de données important, vous remarquerez que la collection de ces données expire. Vous pouvez utiliser la procédure suivante pour résoudre ce problème.

Vous pouvez augmenter le délai d’attente en mettant à jour le fichier de configuration de Microsoft Test Manager ou le fichier de configuration de l’agent de test dont le délai d’attente arrive à expiration.

Le fichier de configuration de Microsoft Test Manager s’appelle *mtm.exe.config*. Il se trouve dans le répertoire *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE*.

Pour mettre à jour un agent de test, vous devez mettre à jour les fichiers de configuration suivants sur l’ordinateur de l’agent de test. Tous ces fichiers se trouvent sur l’ordinateur de l’agent de test dans le même répertoire : *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE*.

-   *QTAgent.exe.config*

-   *QTAgent32.exe.config*

-   *QTDCAgent.exe.config*

-   *QTDCAgent32.exe.config*

Si vous exécutez des tests manuels et que vous collectez des données d'un environnement, lorsqu'un bogue est créé ou que le cas de test est terminé, toutes les données collectées par les adaptateurs de données de diagnostic sont transférées sur l'ordinateur qui exécute les tests manuels. Si vous avez collecté un volume de données important ou que vous avez une connexion réseau lente, le processus peut durer au-delà de la valeur par défaut de 60 secondes. Par exemple, si vous avez configuré l’adaptateur IntelliTrace pour collecter des événements IntelliTrace et informations d’appels sur de nombreux processus, le transfert de ces données peut dépasser le délai d’expiration par défaut. Pour augmenter cette valeur, vous pouvez utiliser la procédure suivante et mettre à jour *mtm.exe.config*.

Un message d’erreur s’affiche en cas d’expiration du délai d’attente d’un agent de test ou de l’activité de Test Runner. Le message d’erreur relatif à l’agent de test donne des informations sur l’ordinateur de l’agent de test dont le délai d’attente est arrivé à expiration. Suivez la procédure suivante pour mettre à jour les fichiers de configuration, en fonction du message d'erreur que vous avez reçu.

## <a name="to-increase-the-time-outs-for-your-diagnostic-data-adapters"></a>Pour augmenter les délais d'attente pour vos adaptateurs de données de diagnostic

1.  Ouvrez une fenêtre Explorateur Windows (ou Explorateur de fichiers).

     Pour ce faire, cliquez avec le bouton droit sur **Démarrer**, puis pointez sur **Explorer**.

    > [!NOTE]
    > Il est possible que vous deviez disposer de privilèges d'administrateur pour mettre à jour le fichier.

2.  Localisez sur votre ordinateur le répertoire *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE* qui contient le fichier que vous devez mettre à jour.

3.  Cliquez avec le bouton droit sur le fichier, puis pointez sur **Ouvrir avec**. Sélectionnez un éditeur.

     Le fichier s'affiche dans cet éditeur. De nombreux paramètres sont stockés dans ce fichier. Vous pouvez changer la plupart de ces paramètres à l’aide de Microsoft Test Manager. Les paramètres de délai d'attente doivent toutefois être modifiés manuellement, comme indiqué dans les étapes suivantes.

4.  Vous devez modifier la section relative aux paramètres d'exécution des tests pour augmenter les valeurs de délai d'attente. Cette section se présente sous la forme suivante :

    ```text
    <!-- Begin: Test execution settings -->

        <!-- How long test runner will wait for an event raised to all local data collectors to complete.  Default is 300. -->
        <add key="DataCollectorEventTimeoutInSeconds" value="300"/>

        <!-- How long test runner will wait for test run operations, such as starting or stopping a test run, to complete.  Default is 60. -->
        <add key="RunOperationTimeoutInSeconds" value="60"/>

        <!-- End: Test execution settings -->
    ```

5.  Pour augmenter le délai pendant lequel les adaptateurs de données de diagnostic doivent attendre la fin des d’événements, augmentez la valeur de la clé **DataCollectorEventTimeoutInSeconds**.

6.  Si le message d’erreur relatif à l’expiration du délai d’attente concerne l’activité de Test Runner, vous devez augmenter la valeur de la clé **RunOperationTimeoutInSeconds**.

7.  Pour augmenter le délai d’expiration du transfert des données collectées pour un bogue ou quand un test se termine sur l’ordinateur qui exécute les tests, vous devez ajouter le délai d’expiration suivant à *mtm.exe.config* dans la section appSettings du fichier :

    ```text
    <!-- How long test runner waits for data collected by diagnostic data adapters to be transferred to the computer. Default is 60 seconds. -->
    <add key="GetCollectorDataTimeout" value="300"/>
    ```

    > [!NOTE]
    > La valeur du délai d'attente est exprimée en secondes.

8.  Enregistrez les modifications que vous avez apportées au fichier et réexécutez les tests dont le délai d'attente était arrivé à expiration.

## <a name="see-also"></a>Voir aussi

- [Collecter des informations de diagnostic à l’aide des paramètres de test](../test/collect-diagnostic-information-using-test-settings.md)