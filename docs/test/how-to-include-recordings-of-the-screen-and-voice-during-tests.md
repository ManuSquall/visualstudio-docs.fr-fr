---
title: Enregistrer le contenu à l’écran et vocal durant les tests
description: Découvrez comment configurer l’adaptateur de données de diagnostic qui enregistre l’écran et la voix de l’utilisateur qui exécute le test dans Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 10/03/2016
ms.topic: how-to
helpviewer_keywords:
- test settings, recording desktop video
ms.assetid: 2cefe8c2-430a-4cb4-bbe0-f3edb2e5bc03
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: 2ca477e25daa76e63e786698e7e2fa1e39c7f77f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99961467"
---
# <a name="how-to-include-recordings-of-the-screen-and-voice-during-tests-using-test-settings"></a>Guide pratique pour inclure des enregistrements d’écran et des enregistrements vocaux pendant des tests à l’aide des paramètres de test

Dans l’éditeur de configuration de Visual Studio, vous pouvez configurer l’adaptateur de données de diagnostic qui enregistre l’écran et la voix de l’utilisateur qui exécute le test. Cet adaptateur de données de diagnostic sauvegarde un enregistrement à l'écran et vocal de la session ouverte pendant le test. L'enregistrement est enregistré avec le résultat du test ou il peut être joint à un bogue. D'autres membres de l'équipe peuvent utiliser l'enregistrement pour isoler les problèmes liés aux applications qui sont difficiles à reproduire.

> [!WARNING]
> Les enregistrements à l'écran et vocaux ne prennent pas en charge les configurations à plusieurs moniteurs.

L'enregistreur à l'écran et vocal peut être utilisé avec des tests manuels ou automatisés. Par exemple, si vous exécutez à distance un test codé de l'interface utilisateur, vous souhaiterez peut-être enregistrer le bureau pour voir le test codé de l'interface utilisateur pendant qu'il s'exécute. Pour plus d’informations sur la capture à distance d’enregistrements d’écran et vocaux, consultez [Guide pratique pour configurer votre agent de test afin d’exécuter des tests qui interagissent avec le Bureau](../test/how-to-set-up-your-test-agent-to-run-tests-that-interact-with-the-desktop.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-configure-screen-and-voice-recording-for-your-test-settings"></a>Pour configurer l'enregistrement à l'écran et vocal pour vos paramètres de test

1. Ouvrez les paramètres de test que vous souhaitez configurer pour enregistrer l'image et le son. Pour plus d’informations, consultez [Collecter les données de diagnostic pendant les tests (Azure Test Plans)](/azure/devops/test/collect-diagnostic-data?view=vsts&preserve-view=true) ou [Collecter des informations de diagnostic avec des paramètres de test](../test/collect-diagnostic-information-using-test-settings.md).

2. Dans les paramètres de test, sélectionnez le **Rôle** à utiliser pour enregistrer l’image et le son.

    > [!NOTE]
    > Pour les tests manuels et automatisés, il s'agit de l'ordinateur qui exécute les tests.

3. Sélectionnez **Enregistreur à l’écran et vocal**, puis choisissez **Configurer**.

     La boîte de dialogue **Configurer l’adaptateur de données de diagnostic – Enregistreur d’écran et vocal** s’affiche.

     ![Configuration vidéo](../test/media/testsettingvideoconfiggdr.png)

4. (Facultatif) Sélectionnez **Activer l’enregistrement vocal** pour capturer le contenu audio dans votre enregistrement.

5. (Facultatif) Cochez la case en regard de l’option **Sauvegarder l’enregistrement si le cas de test réussit** pour spécifier les enregistrements à l’écran et vocaux, à la fois pour les tests réussis et non réussis.

    > [!WARNING]
    > Si vous sélectionnez **Sauvegarder l’enregistrement si le cas de test réussit**, l’enregistrement est stocké avec les résultats des tests, ce qui entraîne l’utilisation de l’espace de stockage sur le serveur. Vous pouvez utiliser **l’outil de nettoyage des pièces jointes de test** pour nettoyer ces pièces jointes.

6. Sous **Qualité de l’enregistrement à l’écran**, configurez les options de liste déroulante suivantes :

    1. **Fréquence d’images :** spécifiez le nombre d’images par seconde à utiliser dans l’enregistrement à l’écran et vocal. La valeur par défaut est 4 images par seconde. Les valeurs comprises entre 2 et 20 peuvent être spécifiées.

    2. **Taux d’échantillonnage :** spécifiez le nombre de kilo-octets par seconde à utiliser dans l’enregistrement à l’écran et vocal. La valeur par défaut est 512. Vous pouvez spécifier une valeur comprise entre 512 et 10 000.

    3. **Qualité (1-100) :** vous pouvez spécifier la qualité de l’enregistrement à l’écran et vocal en sélectionnant une plage de valeurs comprise entre 1 et 100. La valeur par défaut est 50 (moyenne).

7. Choisissez **OK**. Les paramètres du collecteur de traces de diagnostic sont maintenant configurés et enregistrés pour les paramètres de test.

    ::: moniker range="vs-2017"
    > [!TIP]
    > Pour réinitialiser la configuration de cet adaptateur de données de diagnostic, choisissez **Rétablir la configuration par défaut** pour Visual Studio et **Rétablir les valeurs par défaut** pour Microsoft Test Manager.
    ::: moniker-end
    ::: moniker range=">=vs-2019"
    > [!TIP]
    > Pour réinitialiser la configuration de cet adaptateur de données de diagnostic, choisissez **rétablir la configuration par défaut** dans Visual Studio.
    ::: moniker-end

## <a name="see-also"></a>Voir aussi

- [Collecter les données de diagnostic pendant les tests (Azure Test Plans)](/azure/devops/test/collect-diagnostic-data?view=vsts&preserve-view=true)
- [Collecter les données de diagnostic dans des tests manuels (Azure Test Plans)](/azure/devops/test/mtm/collect-more-diagnostic-data-in-manual-tests?view=vsts&preserve-view=true)
- [Collecter des informations de diagnostic avec des paramètres de test](../test/collect-diagnostic-information-using-test-settings.md)
- [Exécuter des tests manuels (Azure Test Plans)](/azure/devops/test/run-manual-tests?view=vsts&preserve-view=true)