---
description: La Débogueur de capture instantanée Visual Studio est maintenant connectée à votre service et vous pouvez commencer à collecter des instantanés pour faciliter le débogage.
title: Page de démarrage de la Débogueur de capture instantanée
ms.date: 07/14/2018
robots: noindex, nofollow
ms.topic: reference
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 96e0c6196d99b8a2b7ac9b4187dbd1397111abbd
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102160340"
---
# <a name="getting-started-with-the-snapshot-debugger"></a>Prise en main avec le Débogueur de capture instantanée

La Débogueur de capture instantanée Visual Studio est maintenant connectée à votre service et vous pouvez commencer à collecter des instantanés pour faciliter le débogage.

Pour utiliser le Débogueur de capture instantanée, définissez des points d’ancrage dans votre code, cliquez sur le bouton pour commencer à collecter des instantanés, puis exécutez votre scénario. Lorsque le code s’exécute dans lequel vous avez défini un point d’ancrage, un instantané de votre application est pris. Ouvrez ensuite l’instantané en cliquant dessus dans Visual Studio dans la fenêtre de Outils de diagnostic. Vous pouvez désormais déboguer l’instantané à partir de votre service comme il était local. Pour obtenir des instructions détaillées, poursuivez la lecture.

## <a name="collect-and-view-snapshots"></a>Collecter et afficher des instantanés

Le Débogueur de capture instantanée collecte des captures instantanées à partir de votre application. Les instantanés sont comme des images de vos packages application à un moment donné. Vous indiquez à Visual Studio quand et où collecter un instantané en définissant un point d’ancrage dans le code. Dans le point d’ancrage, vous définissez toutes les conditions dont vous avez besoin pour vous assurer d’obtenir un instantané du problème que vous examinez.

### <a name="set-a-snappoint"></a>Définir un point d’ancrage

1. Dans l’éditeur de code, cliquez sur la marge gauche en regard d’une ligne de code qui vous intéresse pour définir un point d’ancrage. Assurez-vous qu’il s’agit du code que vous savez exécuter.

    ![Définition d’un point d’ancrage dans l’éditeur](../media/snapshot-startpage-set-snappoint.png)

    Un hexagone violet s’affiche à l’endroit où vous cliquez sur la gauche.

2. Cliquez sur **Lancer la collecte** pour activer le snappoint.

### <a name="open-a-snapshot"></a>Ouvrir un instantané

1. Lorsque le point d’ancrage est atteint, un instantané s’affiche dans la fenêtre de Outils de diagnostic à droite. Si la fenêtre ne s’ouvre pas, vous pouvez l’ouvrir en choisissant **Déboguer**  >  **fenêtres**  >  **afficher les outils de diagnostic**.

    ![Capture instantanée dans la fenêtre Outils de diagnostic](../media/snapshot-startpage-diagsession-window.png)

2. Double-cliquez sur l’instantané pour l’ouvrir.

### <a name="inspect-snapshot-data"></a>Inspecter les données d’instantané

Dans cette vue, vous pouvez pointer sur les variables pour afficher les DataTips, utiliser les fenêtres Variables locales, Suivi, et Pile des appels et évaluer des expressions.

Le site web proprement dit est toujours en ligne ; les utilisateurs finaux ne sont pas affectés. Par défaut, un seul instantané est capturé par point d’ancrage. Autrement dit, une fois qu’un instantané est capturé, le point d’ancrage s’éteint. Si vous souhaitez prendre une autre capture instantanée sur le snappoint, vous pouvez le réactiver en cliquant sur **Mettre à jour la collecte**.

### <a name="set-a-logpoint"></a>Définir un point

1. Cliquez avec le bouton droit sur une icône de point d’ancrage (hexagone violet) et choisissez **paramètres**.

2. Dans la fenêtre **paramètres point d’ancrage** , sélectionnez **actions**.

    ![Conditions point d’ancrage](../media/snapshot-startpage-logpoint.png)

3. Dans le champ **message** , entrez un message de journal que vous souhaitez consigner. Vous pouvez également évaluer des variables dans votre message de journal en les plaçant entre accolades.

    Si vous choisissez **Envoyer vers fenêtre Sortie**, le message s’affiche dans la fenêtre outils de diagnostic lorsque le point est atteint.

    Si vous choisissez **Envoyer au journal des applications**, le message s’affiche partout où vous pouvez voir les messages à partir de `System.Diagnostics.Trace` (ou `ILogger` dans .net Core), comme application Insights, lorsque le point est atteint.

## <a name="learn-more"></a>En savoir plus

Vous trouverez plus d’informations sur le Débogueur de capture instantanée sur la [page docs](../debug-live-azure-applications.md). En savoir plus sur la définition des conditions pour faciliter la recherche des bogues.

## <a name="dont-show-me-this-again"></a>Ne plus afficher ce message

Pour ne plus afficher la page de démarrage débogueur de capture instantanée lorsque vous connectez le débogueur de capture instantanée, modifiez la **page afficher la page « prise en main » au démarrage** de la session dans **Outils**  >  **options**  >  **débogueur de capture instantanée**.

![Page d’options de l’outil Débogueur de capture instantanée](../media/snapshot-startpage-tools-options.png)
