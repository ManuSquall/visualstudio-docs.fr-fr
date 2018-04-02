---
title: Ajouter des paramètres de contexte dans un paramètre d’exécution des tests de charge dans Visual Studio | Microsoft Docs
ms.date: 10/19/2016
ms.topic: article
helpviewer_keywords:
- load tests, run settings, context parameters
- load tests, context parameters
ms.assetid: a8a0b97e-8040-4711-85ab-36548b130ed2
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-test
ms.openlocfilehash: 03db08b701574a4e910b96c843d0f2638e71a4f7
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2018
---
# <a name="how-to-add-context-parameters-to-a-load-test-run-setting"></a>Comment : ajouter des paramètres de contexte dans un paramètre d'exécution des tests de charge

Après avoir créé votre test de charge à l’aide de l’**Assistant Nouveau test de charge**, vous pouvez utiliser l’**éditeur de test de charge** pour changer les propriétés des scénarios en fonction de vos besoins et objectifs.

> [!NOTE]
> Pour obtenir une liste complète des propriétés des paramètres d’exécution et leurs descriptions, consultez [Propriétés des paramètres d’exécution pour le test de charge](../test/load-test-run-settings-properties.md).

Vous pouvez créer des paramètres de contexte à utiliser dans un paramètre de série de tests de charge à l'aide de l'éditeur de test de charge. Les paramètres de contexte vous permettent de paramétrer une chaîne.

Supposons que votre test de charge contienne un test de performances de site web qui utilise déjà une URL de serveur web paramétrable à l’aide d’un paramètre de contexte. Vous pouvez ajouter un paramètre de contexte à un paramètre de série de tests de charge qui utilise la même valeur de nom que celui utilisé dans le test de performances de site web. Cela permet de mapper le test de performances de site web à un autre serveur pendant l'exécution du test de charge. Par exemple, si votre test de charge inclut un test de performances de site web qui utilise un paramètre de contexte nommé WebServer1 pour le nom du serveur web dans l’URL. Si vous spécifiez ensuite un paramètre de contexte dans votre paramètre de série de tests de charge également nommé WebServer1, le test de charge utilisera le paramètre de contexte que vous avez assigné dans le paramètre de série de tests de charge. Pour être plus clair, si le test de performances de site web dans le test de charge utilise le même nom de paramètre de contexte qu'un paramètre de contexte dans le test de charge, le paramètre de contexte du test de charge remplacera le paramètre de contexte utilisé dans le test de performances de site web.

> [!WARNING]
> Veillez à ne pas remplacer de manière involontaire le paramètre de contexte d'un test de performances de site web lorsque vous utilisez des paramètres de contexte dans un paramètre d'exécution. Évitez d'utiliser les mêmes noms pour les paramètres de contexte sauf si vous le faites en connaissance de cause.

Si vous assignez la valeur du paramètre de contexte Webserver1 à `http://CorporateStagingWebServer`, vous pouvez ensuite utiliser `WebServer1` tout au long du test de charge et changer ainsi facilement la valeur en choisissant un autre serveur web à tout moment.

En outre, en assignant des valeurs différentes à un paramètre de contexte en reprenant le même nom dans des paramètres d'exécution du test de charge différents, vous pouvez exécuter le test de charge dans différents environnements :

-   Paramètre d’exécution du serveur web intermédiaire d’entreprise : paramètre de contexte nommé WebServer1=http://CorporateStagingWebServer

-   Paramètre d’exécution de serveur web de production d’entreprise : paramètre de contexte nommé WebServer1=http://CorporateProductionWebServer

 **Changement du paramètre d’exécution depuis la ligne de commande**

 Si vous souhaitez utiliser des paramètres d'exécution différents à partir de la ligne de commande pour tirer parti de la stratégie de paramètre de contexte, utilisez les commandes suivantes :

 **Définissez Test.UseRunSetting= CorporateStagingWebServer**

 -et-

 **mstest /testcontainer:loadtest1.loadtest**

## <a name="to-add-a-context-parameter-to-a-run-setting"></a>Pour ajouter un paramètre de contexte à un paramètre d'exécution

1.  Ouvrez un test de charge.

2.  Développez le dossier **Paramètres d’exécution** dans l’arborescence du test de charge de l’éditeur de test de charge.

3.  Cliquez avec le bouton droit sur le paramètre d’exécution spécifique auquel vous souhaitez ajouter un paramètre de contexte, puis choisissez **Ajouter un paramètre de contexte**.

     Un nouveau paramètre de contexte est ajouté au dossier **Paramètres de contexte** dans le dossier **Paramètres d’exécution** de l’arborescence du test de charge.

     - ou -

     Si le paramètre d’exécution contient déjà un dossier **Paramètres de contexte**, vous pouvez cliquer dessus avec le bouton droit, puis choisir **Ajouter un paramètre de contexte**.

4.  Dans la fenêtre Propriétés, changez la valeur de **Nom** si nécessaire (par exemple WebServer1). Dans la fenêtre Propriétés, changez **Valeur** en fonction du paramètre à utiliser (par exemple http://CorporateStagingWebServer).

5.  (Facultatif) Répétez les étapes 3 à 5 et utilisez une chaîne distincte pour la propriété **Valeur** (par exemple http://CorporateProductionWebServer).

6.  Sélectionnez les paramètres d'exécution à activer. Ouvrez le menu contextuel des paramètres d’exécution, puis choisissez **Définir comme actif**.

## <a name="see-also"></a>Voir aussi

- [Configuration des paramètres d’exécution des tests de charge](../test/configure-load-test-run-settings.md)