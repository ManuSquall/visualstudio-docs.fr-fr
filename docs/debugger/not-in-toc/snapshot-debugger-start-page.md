---
title: Page de démarrage pour le débogueur de capture instantanée
ms.date: 07/14/2018
robots: noindex, nofollow
ms.technology: vs-ide-debug
ms.topic: reference
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c7b5b48aeeb0cfcaeed72a06bfb6709892c58de7
ms.sourcegitcommit: e6ef03cc415ca67f75fd1f26e0e7b8846857166d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2018
ms.locfileid: "39310111"
---
# Mise en route avec le débogueur de capture instantanée

Le débogueur de capture instantanée Visual Studio est maintenant connecté à votre service et vous pouvez commencer à collecter des instantanés pour faciliter le débogage.

Pour utiliser le débogueur de capture instantanée, définissez des points d’ancrage dans votre code, cliquez sur le bouton pour commencer la collecte de captures instantanées, puis exécutez votre scénario. Quand le code s’exécute dans laquelle vous avez défini un point d’ancrage, un instantané de votre application. Ensuite, ouvrir la capture instantanée en cliquant dessus dans la fenêtre Outils de Diagnostic Visual Studio. Vous pouvez maintenant déboguer l’instantané à partir de votre service, comme c’était local. Pour obtenir des instructions détaillées, poursuivez votre lecture.

## Collecter et afficher les captures instantanées

Le débogueur d’instantané collecte des captures instantanées à partir de votre application. Les instantanés sont comme les images de votre application à un point dans le temps. Vous indiquez à Visual Studio quand et où collecter un instantané en définissant un point d’ancrage dans le code. Le point d’ancrage, vous allez définir des conditions que vous devez vous assurer de qu'obtenir un instantané du problème que vous recherchez.

### Définir un point d’ancrage

1. Dans l’éditeur de code, cliquez sur la marge gauche en regard d’une ligne de code qui vous intéresse définir un point d’ancrage. Assurez-vous que c’est le code que vous connaissez s’exécutera. 

    ![Définition d’un point d’ancrage dans l’éditeur](../media/snapshot-startpage-set-snappoint.png)

    Un hexagone violet s’affiche lorsque vous cliquez sur la gauche.

2. Cliquez sur **démarrer la collecte** pour activer le point d’ancrage.

### Ouvrez un instantané

1. Lorsque le point d’ancrage est atteint, une capture instantanée apparaît dans la fenêtre d’outils de Diagnostic sur la droite. Si la fenêtre ne s’ouvre, vous pouvez l’ouvrir en choisissant **déboguer** > **Windows** > **afficher les outils de Diagnostic**. 

    ![Instantané dans la fenêtre Outils de Diagnostic](../media/snapshot-startpage-diagsession-window.png)

2. Double-cliquez sur la capture instantanée pour l’ouvrir.

### Inspecter les données d’instantané

Dans cette vue, vous pouvez pointer sur les variables à afficher des DataTips, utilisez les variables locales, espions et appeler windows de la pile et également évaluer des expressions.

Le site Web lui-même est toujours en direct et les utilisateurs finaux ne sont pas affectées. Par défaut, une seule capture instantanée est capturée par le point d’ancrage. Autrement dit, une fois une capture instantanée est capturée, le point d’ancrage désactive. Si vous souhaitez capturer un autre instantané sur le point d’ancrage, vous pouvez activer le point d’ancrage précédent en cliquant sur **mise à jour Collection**.

### Définir un point de journalisation

1. Cliquez sur une icône de point d’ancrage (l’Hexagone violet) et choisissez **paramètres**.

2. Dans le **les paramètres de point d’ancrage** fenêtre, sélectionnez **Actions**.

    ![Conditions de point d’ancrage](../media/snapshot-startpage-logpoint.png)

3. Dans le **Message** , entrez un message de journal que vous souhaitez ouvrir une session. Vous pouvez également évaluer des variables dans votre message de journal en les plaçant entre accolades.

    Si vous choisissez **envoyer dans la fenêtre sortie**, le message s’affiche dans la fenêtre Outils de Diagnostic lorsque le point de journalisation est atteint. 

    Si vous choisissez **envoyer au journal des applications**, le message s’affiche de n’importe où que vous pouvez voir des messages à partir de `System.Diagnostics.Trace` (ou `ILogger` dans .NET Core), tels qu’application Insights, lorsque le point de journalisation est atteint.

## En savoir plus

Vous trouverez plus d’informations sur le débogueur de capture instantanée sur le [page docs](../debug-live-azure-applications.md). En savoir plus sur la définition des conditions pour le rendre plus facile à trouver des bogues.

## Ne ' plus afficher ce message

Pour ne jamais afficher la Page de démarrage de débogueur de capture instantanée à nouveau lorsque vous vous connectez le débogueur de capture instantanée, vous devez modifier le **afficher la page « Prise en main » sur le démarrage d’une session** option **outils**  >   **Options** > **débogueur de captures instantanées**. 

![Instantané la Page d’options de l’outil débogueur](../media/snapshot-startpage-tools-options.png)
