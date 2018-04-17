---
title: Déboguer des applications ASP.NET Azure live - Visual Studio | Documents Microsoft
ms.description: Learn how to set snappoints and view snapshots with the Snapshot Debugger
ms.custom: mvc
ms.date: 03/16/2018
ms.technology:
- vs-ide-debug
ms.topic: tutorial
helpviewer_keywords:
- debugger
ms.assetid: adb22512-4d4d-40e5-9564-1af421b7087e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
- azure
ms.openlocfilehash: 3d6173c62b359508819db26ff9dcdceb90644202
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="debug-live-aspnet-azure-apps-using-the-snapshot-debugger"></a>Déboguer des applications ASP.NET Azure en direct à l’aide du débogueur de l’instantané

Le débogueur d’instantané prend un instantané de vos applications de production lors de l’exécution de code qui vous intéresse. Pour indiquer au débogueur de prendre une capture instantanée, vous définissez des points d’ancrage et des points de journalisation dans votre code. Dans le débogueur, vous pouvez voir précisément à quel endroit le code ne s’est pas exécuté correctement, sans que cela impacte le trafic de votre application en production. Snapshot Debugger peut vous aider à résoudre beaucoup plus vite les problèmes rencontrés dans les environnements de production.

Snappoints et logpoints sont similaires aux points d’arrêt, mais contrairement aux points d’arrêt, snappoints ne pas arrêter l’application lorsqu’il est atteint. En règle générale, la capture instantanée à un snappoint prend 10 à 20 millisecondes. 

La fonctionnalité de capture instantanée est disponible pour les applications web suivantes qui s’exécutent dans Azure App Service :

- Applications ASP.NET exécutées sur .NET Framework version 4.6.1 ou ultérieure.
- Applications ASP.NET Core exécutées sur .NET Core version 2.0 ou ultérieure sur Windows.

En outre, le débogueur de l’instantané est uniquement disponible pour Visual Studio 2017 Enterprise version 15,5 ou une version ultérieure et les plans de Service d’applications de base ou une version ultérieure. 

Dans ce didacticiel, vous allez effectuer les actions suivantes :

> [!div class="checklist"]
> * Démarrez le débogueur de l’instantané
> * Définir un snappoint et afficher un instantané
> * Définir un logpoint

## <a name="start-the-snapshot-debugger"></a>Démarrez le débogueur de l’instantané

1. Installer [Visual Studio 2017 Enterprise version 15.5](https://www.visualstudio.com/downloads/) ou version ultérieure. Si vous mettez à jour à partir d’une précédente installation de Visual Studio 2017, exécutez le programme d’installation Visual Studio et vérifiez le composant de débogueur de l’instantané dans la charge de travail de développement ASP.NET et web.

2. Ouvrez le projet pour le débogage de l’instantané. 

    > [!IMPORTANT] 
    > Débogage de l’instantané, vous devez ouvrir le **même version de code source** qui est publié dans votre Service d’applications Azure. 

3. Dans l’Explorateur de Cloud (**vue > Cloud Explorer**), avec le bouton droit de votre projet est déployé sur le Service d’applications Azure et sélectionnez **attacher le débogueur instantané**.

   ![Lancer le débogueur de l’instantané](../debugger/media/snapshot-launch.png)

    La première fois que vous sélectionnez **attacher le débogueur instantané**, vous êtes invité à installer l’extension de site du débogueur de l’instantané sur votre Service d’applications Azure. Cette installation nécessite un redémarrage de votre Service d’applications Azure. 

   Visual Studio est présent dans l’instantané de mode de débogage.

    > [!NOTE]
    > L’extension de site Application Insights prend également en charge le débogage de l’instantané. Si vous rencontrez un message d’erreur « extension obsolète de site », consultez [dépannage des conseils et des problèmes connus pour le débogage de l’instantané](../debugger/debug-live-azure-apps-troubleshooting.md) détails de la mise à niveau.

   ![Mode de débogage d’instantané](../debugger/media/snapshot-message.png)

   Le **Modules** fenêtre vous indique que tous les modules ont chargés pour le Service d’application Azure (choisissez **déboguer / Windows / Modules** pour ouvrir cette fenêtre).

   ![Vérification de la fenêtre Modules](../debugger/media/snapshot-modules.png)

## <a name="set-a-snappoint"></a>Définir un snappoint

1. Dans l’éditeur de code, cliquez sur la marge gauche en regard d’une ligne de code qui que vous intéressez définir un snappoint. Assurez-vous que c’est le code qui s’exécute.

   ![Définir un snappoint](../debugger/media/snapshot-set-snappoint.png)

2. Cliquez sur **démarrer la collecte** pour activer la snappoint.  

   ![Activer la snappoint](../debugger/media/snapshot-start-collection.png)

    > [!TIP]
    > Vous ne pouvez pas passer lors de l’affichage d’un instantané, mais vous pouvez placer plusieurs snappoints dans votre code pour suivre l’exécution à différentes lignes de code. Si vous avez plusieurs snappoints dans votre code, le débogueur de l’instantané permet de s’assurer que les instantanés correspondantes sont de la même session de l’utilisateur final. Le débogueur de l’instantané pour cela, même s’il existe de nombreux utilisateurs atteignez votre application.

## <a name="take-a-snapshot"></a>Prendre un instantané

Lorsqu’un snappoint est allumé, il capture un instantané chaque fois que la ligne de code où se trouve le snappoint s’exécute. Cette exécution peut être due à une demande réelle sur votre serveur. Pour forcer votre snappoint pour atteindre, accédez à la vue du navigateur de votre site web et prendre les mesures nécessaires qui provoquent votre snappoint soit atteint.

## <a name="inspect-snapshot-data"></a>Inspecter les données d’instantané

1. Lorsque le snappoint est atteint, une capture instantanée s’affiche dans la fenêtre Outils de Diagnostic. Pour ouvrir cette fenêtre, choisissez **déboguer / Windows / afficher les outils de Diagnostic**.

   ![Ouvrir un snappoint](../debugger/media/snapshot-diagsession-window.png)

1. Double-cliquez sur le snappoint pour ouvrir l’instantané dans l’éditeur de code.

   ![Inspecter les données d’instantané](../debugger/media/snapshot-inspect-data.png)

   Dans cette vue, vous pouvez pointer sur les variables pour afficher les DataTips, utilisez le **variables locales**, **observe**, et **pile des appels** windows et également évaluer des expressions.

    Le site Web lui-même est toujours actif et les utilisateurs finaux ne sont pas affectés. Un seul instantané est capturé par snappoint par défaut : après un instantané capture le snappoint désactive. Si vous souhaitez capturer un autre instantané à le snappoint, vous pouvez activer le snappoint précédent en cliquant sur **mise à jour de Collection**.

Vous pouvez également ajouter plusieurs snappoints à votre application et sous tension avec la **mise à jour de Collection** bouton.

**Besoin d’aide ?** Consultez le [problèmes connus et dépannage](../debugger/debug-live-azure-apps-troubleshooting.md) et [FAQ pour le débogage de l’instantané](../debugger/debug-live-azure-apps-faq.md) pages.

## <a name="set-a-conditional-snappoint"></a>Définir un snappoint conditionnelle

S’il est difficile de recréer un état particulier dans votre application, considérez que l’utilisation d’un snappoint conditionnel peut aider à. Snappoints conditionnel vous évitent une capture instantanée jusqu'à ce que l’application passe à l’état souhaité, par exemple, lorsqu’une variable a une valeur particulière que vous voulez inspecter. Vous pouvez définir des conditions à l’aide d’expressions, filtres, ou nombre d’accès.

#### <a name="to-create-a-conditional-snappoint"></a>Pour créer un snappoint conditionnelle

1. Cliquez sur une icône de snappoint (la balle creuse) et choisissez **paramètres**.

   ![Choisir les paramètres](../debugger/media/snapshot-snappoint-settings.png)

1. Dans la fenêtre de paramètres snappoint, tapez une expression.

   ![Tapez une expression](../debugger/media/snapshot-snappoint-conditions.png)

   Dans l’illustration précédente, l’instantané est uniquement effectuée pour le snappoint lorsque `visitor.FirstName == "Dan"`.

## <a name="set-a-logpoint"></a>Définir un logpoint

En plus d’une capture instantanée lorsqu’un snappoint est atteint, vous pouvez également configurer un snappoint pour enregistrer un message (autrement dit, créer un logpoint). Vous pouvez définir logpoints sans avoir à redéployer votre application. Logpoints sont exécutées virtuellement et ne provoquer aucun impact ou les effets secondaires à votre application en cours d’exécution.

#### <a name="to-create-a-logpoint"></a>Pour créer un logpoint

1. Cliquez sur une icône de snappoint (l’Hexagone bleu) et choisissez **paramètres**.

1. Dans la fenêtre Paramètres snappoint, sélectionnez **Actions**.

    ![Créer un logpoint](../debugger/media/snapshot-logpoint.png)

1. Dans le champ de Message, vous pouvez entrer le nouveau message du journal à enregistrer. Vous pouvez également évaluer des variables dans votre message du journal en les plaçant à l’intérieur des accolades.

    Si vous choisissez **envoyer à la fenêtre sortie**, lorsque le logpoint est atteint, le message s’affiche dans la fenêtre Outils de Diagnostic.

    ![Logpoint des données dans la fenêtre diagsession](../debugger/media/snapshot-logpoint-output.png)

    Si vous choisissez **envoyer au journal des applications**, lorsque le logpoint est atteint, le message s’affiche partout où que vous pouvez voir des messages à partir de `System.Diagnostics.Trace` (ou `ILogger` dans .NET Core), tel que [application Insights](/azure/application-insights/app-insights-asp-net-trace-logs).

## <a name="next-steps"></a>Étapes suivantes

Dans ce didacticiel, vous avez appris à utiliser le débogueur de l’instantané. Voulez-vous lire plus de détails sur cette fonctionnalité.

> [!div class="nextstepaction"]
> [FAQ pour le débogage d’instantané](../debugger/debug-live-azure-apps-faq.md)
