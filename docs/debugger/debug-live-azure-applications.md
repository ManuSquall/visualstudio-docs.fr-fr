---
title: "Déboguer des applications ASP.NET Azure live - Visual Studio | Documents Microsoft"
ms.date: 11/13/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debugger
ms.assetid: adb22512-4d4d-40e5-9564-1af421b7087e
caps.latest.revision: "1"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 71facc3515bf90d378b19242bb804ce825131b4e
ms.sourcegitcommit: 2c7f48ad6073a81fa927568793633f26cc1f0b15
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="debug-live-aspnet-azure-apps-using-the-snapshot-debugger"></a>Déboguer des applications ASP.NET Azure en direct à l’aide du débogueur de l’instantané

Le débogueur d’instantané prend un instantané de vos applications de production lors de l’exécution de code qui vous intéressez. Pour indiquer au débogueur de prendre un instantané, vous définissez snappoints et logpoints dans votre code. Le débogueur vous permet de voir exactement ce qui s’est produite, sans affecter le trafic de votre application de production. Le débogueur de l’instantané peut vous aider à réduire considérablement le temps que nécessaire pour résoudre les problèmes qui se produisent dans les environnements de production.

Snappoints et logpoints sont semblables aux points d’arrêt. Contrairement aux points d’arrêt, snappoints n’empêchent pas l’application lorsqu’il est atteint. En règle générale, la capture instantanée à un snappoint prend 10 à 20 millisecondes. 

Collection d’instantané est disponible pour les applications web suivantes en cours d’exécution dans Azure App Service :

- Les applications ASP.NET exécutées sur .NET Framework 4.6.1 ou version ultérieure.
- Applications ASP.NET Core en cours d’exécution sur .NET Core 2.0 ou version ultérieure sur Windows.

En outre, le débogueur de l’instantané est uniquement disponible pour Visual Studio 2017 Enterprise version 15,5 ou une version ultérieure. 

## <a name="start-the-snapshot-debugger"></a>Démarrez le débogueur de l’instantané

1. Installer le [Visual Studio Enterprise 15.5 Preview](https://www.visualstudio.com/en-us/news/releasenotes/vs2017-preview-relnotes) ou version ultérieure. Si vous mettez à jour à partir d’une version préliminaire de Visual Studio 2017 précédente, exécutez le programme d’installation Visual Studio et vérifiez le composant de débogueur de l’instantané dans la charge de travail de développement ASP.NET et web.

2. Ouvrez le projet pour le débogage de l’instantané. 

    > [!IMPORTANT] 
    > Dans l’ordre de débogage de l’instantané, vous devez ouvrir le **même version de code source** qui est publié dans votre Service d’applications Azure. 

3. Dans l’Explorateur de Cloud (sélectionnez **vue > Cloud Explorer**), cliquez avec le bouton droit sur votre projet est déployé sur le Service d’applications Azure et sélectionnez **attacher le débogueur instantané** pour démarrer le débogueur de l’instantané.

   ![Lancer le débogueur de l’instantané](../debugger/media/snapshot-launch.png "lancer le débogueur de l’instantané")

    La première fois que vous sélectionnez **attacher le débogueur instantané**, vous êtes invité à installer le débogueur de l’instantané sur votre Service d’applications Azure. Cette installation nécessite un redémarrage de votre Service d’applications Azure. 

   Visual Studio est présent dans l’instantané de mode de débogage.

   ![Débogage en mode de capture instantanée](../debugger/media/snapshot-message.png "mode débogage d’instantané")

   Le **Modules** fenêtre vous indique que tous les modules ont chargés pour le Service d’application Azure (choisissez **déboguer / Windows / Modules** pour ouvrir cette fenêtre).

   ![Vérifiez la fenêtre Modules](../debugger/media/snapshot-modules.png "vérifier la fenêtre Modules")

## <a name="set-a-snappoint"></a>Définir un snappoint

1. Dans l’éditeur de code, cliquez sur la marge gauche en regard d’une ligne de code qui que vous intéressez définir un snappoint. Assurez-vous que c’est le code qui s’exécute.

   ![Définir un snappoint](../debugger/media/snapshot-set-snappoint.png "définir un snappoint")

2. Cliquez sur **démarrer la collecte** pour activer la snappoint.  

   ![Activer la snappoint](../debugger/media/snapshot-start-collection.png "activer le snappoint")

    > [!TIP]
    > Vous ne pouvez pas passer lors de l’affichage d’un instantané, mais vous pouvez placer plusieurs snappoints dans votre code pour suivre l’exécution à différentes lignes de code. Si vous avez plusieurs snappoints dans votre code, le débogueur de l’instantané garantit que les instantanés correspondantes sont de la même session de l’utilisateur final, même s’il existe plusieurs utilisateurs en appuyant sur votre application.

## <a name="take-a-snapshot"></a>Prendre un instantané

Lorsqu’un snappoint est allumé, il capture un instantané chaque fois que la ligne de code où se trouve le snappoint est exécutée. Cette exécution peut être due à une demande réelle sur votre serveur. Pour forcer votre snappoint atteint, vous pouvez également accéder à la vue du navigateur de votre site web et le prenez que toutes les actions requises qui provoquent votre snappoint soit atteint.

## <a name="inspect-snapshot-data"></a>Inspecter les données d’instantané

1. Lorsque le snappoint est atteint, une capture instantanée s’affiche dans la fenêtre Outils de Diagnostic. Choisissez **déboguer / Windows / afficher les outils de Diagnostic** pour ouvrir cette fenêtre.

   ![Ouvrir un snappoint](../debugger/media/snapshot-diagsession-window.png "ouvrir une snappoint")

1. Double-cliquez sur le snappoint pour ouvrir l’instantané dans l’éditeur de code.

   ![Inspecter les données d’instantané](../debugger/media/snapshot-inspect-data.png "inspecter les données d’instantané")

   Dans cette vue, vous pouvez pointer sur les variables pour afficher les DataTips, utilisez le **variables locales**, **observe**, et **pile des appels** windows et également évaluer des expressions.

    Le site Web lui-même est toujours en direct et les utilisateurs finaux ne soient pas affectés. Un seul instantané est capturé par snappoint par défaut : après un instantané capture le snappoint désactive. Si vous souhaitez capturer un autre instantané à le snappoint, vous pouvez activer le snappoint précédent en cliquant sur **mise à jour de Collection**.

Vous pouvez également ajouter plusieurs snappoints à votre application et sous tension avec la **mise à jour de Collection** bouton.

**Besoin d’aide ?** Consultez le [problèmes connus et dépannage](../debugger/debug-live-azure-apps-troubleshooting.md) et [FAQ pour le débogage de l’instantané](../debugger/debug-live-azure-apps-faq.md) pages.

## <a name="set-a-conditional-snappoint"></a>Définir un snappoint conditionnelle

S’il est difficile de recréer un état particulier dans votre application, considérez que l’utilisation d’un snappoint conditionnel peut aider à. Vous pouvez utiliser snappoints conditionnelle pour éviter de créer un instantané jusqu'à ce que l’application passe à l’état souhaité, telles que lorsqu’une variable a une valeur particulière vous intéressent. Vous pouvez définir des conditions à l’aide d’expressions, filtres, ou nombre d’accès.

#### <a name="to-create-a-conditional-snappoint"></a>Pour créer un snappoint conditionnelle

1. Cliquez sur une icône de snappoint (la balle creuse) et choisissez **paramètres**.

   ![Choisissez les paramètres](../debugger/media/snapshot-snappoint-settings.png "choisir des paramètres")

1. Dans la fenêtre de paramètres snappoint, tapez une expression.

   ![Tapez une expression](../debugger/media/snapshot-snappoint-conditions.png "une expression de Type")

   Dans l’illustration précédente, l’instantané est uniquement effectuée pour le snappoint lorsque `visitor.FirstName == "Dan"`.

## <a name="set-a-logpoint"></a>Définir un logpoint

En plus d’une capture instantanée lorsqu’un snappoint est atteint, vous pouvez également configurer un snappoint pour enregistrer un message (autrement dit, créer un logpoint). Vous pouvez définir logpoints sans avoir à redéployer votre application. Logpoints sont exécutées virtuellement et ne provoquer aucun impact ou les effets secondaires à votre application en cours d’exécution.

#### <a name="to-create-a-logpoint"></a>Pour créer un logpoint

1. Cliquez sur une icône de snappoint (l’Hexagone bleu) et choisissez **paramètres**.

1. Dans la fenêtre Paramètres snappoint, sélectionnez **Actions**.

    ![Créer un logpoint](../debugger/media/snapshot-logpoint.png "créer un logpoint")

1. Dans le champ de Message, vous pouvez entrer le nouveau message du journal à enregistrer. Vous pouvez également évaluer des variables dans votre message du journal en les plaçant à l’intérieur des accolades.

    Si vous choisissez **envoyer à la fenêtre sortie**, lorsque le logpoint est atteint, le message s’affiche dans la fenêtre Outils de Diagnostic.

    ![Logpoint des données dans la fenêtre .diagsession](../debugger/media/snapshot-logpoint-output.png "Logpoint des données dans la fenêtre .diagsession")

    Si vous choisissez **envoyer au journal des applications**, lorsque le logpoint est atteint, le message s’affiche partout où que vous pouvez voir des messages à partir de `System.Diagnostics.Trace` (ou `ILogger` dans .NET Core), tel que [application Insights](/azure/application-insights/app-insights-asp-net-trace-logs).

## <a name="next-steps"></a>Étapes suivantes

- Pour savoir comment examiner les variables lors de l’affichage d’un instantané, consultez [visite guidée des fonctionnalités Debbuger](../debugger/debugger-feature-tour.md).
- Afficher le [FAQ pour le débogage de l’instantané](../debugger/debug-live-azure-apps-faq.md).
- Vue [dépannage des conseils et des problèmes connus pour le débogage de l’instantané](../debugger/debug-live-azure-apps-troubleshooting.md).
- Si vous souhaitez afficher des instantanés de l’Application Insights lorsque votre application rencontre une exception, vous pouvez le faire. Pour plus d’informations, consultez [déboguer des instantanés sur les exceptions dans les applications .NET](/azure/application-insights/app-insights-snapshot-debugger). Application Insights prend en charge les applications de Service Fabric en plus du Service d’applications Azure.
