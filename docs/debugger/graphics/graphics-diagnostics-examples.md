---
title: Exemples de Graphics Diagnostics | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 45dd86b2-801e-4b07-a8c4-7bd25641d7f8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4df2fafb523d04a8ec222b10e1ac9ed3aa95454d
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73187927"
---
# <a name="graphics-diagnostics-examples"></a>Exemples Graphics Diagnostics
Ces exemples montrent comment déboguer les problèmes de rendu dans les applications DirectX à l’aide des outils Graphics Diagnostics de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

## <a name="capturing-graphics-information"></a>Capture d'informations graphiques
 Avant d'utiliser Graphics Diagnostics pour diagnostiquer des problèmes de rendu dans votre application, vous devez capturer les informations graphiques de l'application pendant qu'elle s'exécute. Les informations graphiques peuvent être capturées à partir d'une application s'exécutant en local ou sur un ordinateur ou autre appareil distant. Ces procédures pas à pas montrent comment capturer les informations graphiques d'une application manuellement ou par programmation :

- [Procédure pas à pas : capture d’informations graphiques](walkthrough-capturing-graphics-information.md)

- [Procédure pas à pas : capture d’informations graphiques par programmation](walkthrough-capturing-graphics-information-programmatically.md)

## <a name="use-graphics-diagnostics-with-an-arm-based-device"></a>Utiliser Graphics Diagnostics avec un appareil ARM
 Vous pouvez utiliser Graphics Diagnostics pour déboguer votre application Direct3D sur un appareil ARM via le débogage distant. Pour plus d’informations, consultez [Comment : utiliser Graphics Diagnostics avec un appareil ARM](graphics-diagnostics-examples.md).

## <a name="playing-back-graphics-information"></a>Lecture des informations graphiques
 Après avoir capturé les informations graphiques d'une application en cours d'exécution, vous pouvez lire les événements capturés pour diagnostiquer les problèmes de rendu. Pour la lecture, vous pouvez soit utiliser votre ordinateur de développement, soit un ordinateur ou un appareil distant auquel vous êtes connecté. For more information, see [Comment : modifier l'ordinateur de lecture Graphics Diagnostics](how-to-change-the-graphics-diagnostics-playback-machine.md).

## <a name="debugging-missing-objects"></a>Débogage des objets manquants
 L'absence d'un ou plusieurs objets est l'un des problèmes de rendu les plus courants auxquels les développeurs graphiques sont confrontés. Ce type de problème peut être difficile à diagnostiquer, car plusieurs types d'erreurs peuvent être à l'origine de la disparition apparente d'un objet. Un état de périphérique mal configuré, des problèmes de transformation de la géométrie du ou des objets ou un pipeline graphique mal configuré peuvent expliquer l'absence d'objets.

 Ces scénarios montrent comment utiliser Graphics Diagnostics pour déterminer la raison de l’absence d’un objet et identifier le code qui en est responsable.

- [Procédure pas à pas : objets manquants en raison de l’état de l’appareil](walkthrough-missing-objects-due-to-device-state.md)

- [Procédure pas à pas : objets manquants en raison de l’ombrage de vertex](walkthrough-missing-objects-due-to-vertex-shading.md)

- [Procédure pas à pas : objets manquants en raison d’un pipeline mal configuré](walkthrough-missing-objects-due-to-misconfigured-pipeline.md)

## <a name="debugging-rendering-errors"></a>Débogage des erreurs de rendu
 Un objet (ou des objets) n'ayant pas l'apparence correcte est un autre problème courant auquel les développeurs graphiques sont confrontés. Il peut être difficile diagnostiquer ce type de problème, car l’apparence incorrecte et sa cause peuvent aussi bien être évidents (liaison de la mauvaise texture) que très subtils (bogue dans le code du nuanceur ou interaction inattendue entre des nuanceurs). Certains problèmes peuvent être occasionnés par une combinaison d'erreurs.

 Voici un scénario qui montre comment utiliser Graphics Diagnostics pour localiser un problème de rendu, pas si subtil, provoqué par un bogue de nuanceur mineur :

- [Procédure pas à pas : débogage des erreurs de rendu dues à l’ombrage](walkthrough-debugging-rendering-errors-due-to-shading.md)

## <a name="debugging-compute-shaders"></a>Débogage des nuanceurs de calcul
 Vous pouvez utiliser Graphics Diagnostics pour déboguer des noyaux de nuanceur de calcul DirectCompute qui génèrent des résultats incorrects. Avec DirectCompute, vous pouvez utiliser la puissance de calcul du GPU pour effectuer des calculs sur un grand nombre d'éléments de données en parallèle. Pour certains types de problèmes, l'utilisation du GPU peut donner des résultats beaucoup plus rapides qu'un code d'UC même bien optimisé. Cependant, les débogueurs classiques ne peuvent pas détecter le code qui s'exécute sur le GPU. Déboguer ce type de code nécessite des outils spécialisés qui sont souvent propres au fournisseur et peuvent ne pas s'intégrer correctement à Visual Studio. Pour améliorer la cohérence du débogage des nuanceurs de calcul avec divers types de GPU, Graphics Diagnostics capture les événements de distribution DirectCompute (en plus des événements de rendu Direct3D) pour vous permettre d'utiliser des outils qui vous sont familiers pour déboguer les problèmes au niveau de votre code de nuanceur de calcul.

 Pour obtenir un scénario qui montre comment déboguer un problème de simulation provoqué par un bogue dans un nuanceur de calcul, consultez [procédure pas à pas : utilisation de Graphics Diagnostics pour déboguer un nuanceur de calcul](walkthrough-using-graphics-diagnostics-to-debug-a-compute-shader.md).