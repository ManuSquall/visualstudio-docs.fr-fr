---
title: Ajouter des paramètres de contexte à un paramètre d’exécution de test de charge
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, run settings, context parameters
- load tests, context parameters
ms.assetid: a8a0b97e-8040-4711-85ab-36548b130ed2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 05efbba005a9455af3b9d2e8755b580a8af30d0a
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75584476"
---
# <a name="how-to-add-context-parameters-to-a-load-test-run-setting"></a>Guide pratique : Ajouter des paramètres de contexte à un paramètre de série de tests de charge

Après avoir créé votre test de charge en utilisant le **New Load Test Wizard**, vous pouvez utiliser **l’éditeur de test de charge** pour modifier les propriétés des scénarios pour répondre à vos besoins et objectifs de test.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!NOTE]
> Pour obtenir la liste complète des propriétés des paramètres et leur description, voir [Propriétés des paramètres de série de tests de charge](../test/load-test-run-settings-properties.md).

Vous pouvez créer des paramètres de contexte à utiliser dans un paramètre de série de tests de charge à l'aide de l'éditeur de test de charge. Les paramètres de contexte vous permettent de paramétrer une chaîne.

Supposons que votre test de charge contienne un test de performances web qui utilise déjà une URL de serveur web paramétrable à l’aide d’un paramètre de contexte. Vous pouvez ajouter un paramètre de contexte à un paramètre de série de tests de charge qui utilise la même valeur de nom que celle du test de performances web. Cela permet de mapper le test de performances web à un autre serveur pendant l’exécution du test de charge. Supposons par exemple que votre test de charge comporte un test de performances web qui utilise un paramètre de contexte nommé WebServer1 comme nom du serveur web dans l’URL. Si vous spécifiez ensuite un paramètre de contexte dans votre paramètre de série de tests de charge également nommé WebServer1, le test de charge utilisera le paramètre de contexte que vous avez assigné dans le paramètre de série de tests de charge. En d’autres termes, si le test de performances web inclus dans un test de charge utilise le même nom de paramètre de contexte qu’un des paramètres de contexte du test de charge, ce dernier remplacera le paramètre de contexte utilisé dans le test de performances web.

> [!WARNING]
> Faites attention à ne pas écraser de manière involontaire le paramètre de contexte d’un test de performances web lorsque vous utilisez des paramètres de contexte dans un paramètre de série. Évitez d'utiliser les mêmes noms pour les paramètres de contexte sauf si vous le faites en connaissance de cause.

Si vous affectez la valeur du paramètre de contexte Webserver1 à `http://CorporateStagingWebServer`, vous pourrez utiliser `WebServer1` tout au long du test de charge et ainsi remplacer facilement la valeur par un autre serveur web à tout moment.

En outre, en assignant des valeurs différentes à un paramètre de contexte en reprenant le même nom dans des paramètres d'exécution du test de charge différents, vous pouvez exécuter le test de charge dans différents environnements :

- Paramètre d’exécution du serveur web de préproduction d’entreprise : paramètre de contexte nommé `WebServer1=http://CorporateStagingWebServer`

- Paramètre d’exécution du serveur web de production d’entreprise : paramètre de contexte nommé `WebServer1=http://CorporateProductionWebServer`

  **Changement du paramètre d’exécution depuis la ligne de commande**

  Si vous souhaitez utiliser des paramètres d'exécution différents à partir de la ligne de commande pour tirer parti de la stratégie de paramètre de contexte, utilisez les commandes suivantes :

  **Définissez Test.UseRunSetting= CorporateStagingWebServer**

  -et-

  **mstest /testcontainer:loadtest1.loadtest**

## <a name="to-add-a-context-parameter-to-a-run-setting"></a>Pour ajouter un paramètre de contexte à un paramètre d'exécution

1. Ouvrez un test de charge.

2. Développez le dossier **Paramètres d’exécution** dans l’arborescence du test de charge de l’éditeur de test de charge.

3. Cliquez avec le bouton droit sur le paramètre d’exécution spécifique auquel vous souhaitez ajouter un paramètre de contexte, puis choisissez **Ajouter un paramètre de contexte**.

     Un nouveau paramètre de contexte est ajouté au dossier **Paramètres de contexte** dans le dossier **Paramètres d’exécution** de l’arborescence du test de charge.

     -ou-

     Si le paramètre d’exécution contient déjà un dossier **Paramètres de contexte**, vous pouvez cliquer dessus avec le bouton droit, puis choisir **Ajouter un paramètre de contexte**.

4. Dans la fenêtre **Propriétés,** modifiez la valeur du **nom,** le cas échéant (par exemple, WebServer1). Dans la fenêtre **Propriétés,** **changez la valeur** du `http://CorporateStagingWebServer`paramètre que vous souhaitez utiliser (par exemple, ).

5. (Facultatif) Répétez les étapes 3 à 5 et utilisez une `http://CorporateProductionWebServer`chaîne différente pour la propriété **Value** (par exemple, ).

6. Sélectionnez les paramètres d'exécution à activer. Ouvrez le menu contextuel des paramètres d’exécution, puis choisissez **Définir comme actif**.

## <a name="see-also"></a>Voir aussi

- [Configurer les paramètres d’exécution de test de charge](../test/configure-load-test-run-settings.md)
