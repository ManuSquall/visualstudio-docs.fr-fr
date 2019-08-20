---
title: Exemples Graphics Diagnostics | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 45dd86b2-801e-4b07-a8c4-7bd25641d7f8
caps.latest.revision: 36
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 14b4ac689109e29baa4ee06c668b208d0d5227b0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68159718"
---
# <a name="graphics-diagnostics-examples"></a>Exemples Graphics Diagnostics
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ces exemples montrent comment déboguer les problèmes de rendu dans les applications DirectX à l’aide des outils Graphics Diagnostics de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
## <a name="capturing-graphics-information"></a>Capture d'informations graphiques  
 Avant d'utiliser Graphics Diagnostics pour diagnostiquer des problèmes de rendu dans votre application, vous devez capturer les informations graphiques de l'application pendant qu'elle s'exécute. Les informations graphiques peuvent être capturées à partir d'une application s'exécutant en local ou sur un ordinateur ou autre appareil distant. Ces procédures pas à pas montrent comment capturer les informations graphiques d'une application manuellement ou par programmation :  
  
- [Procédure pas à pas : capture d’informations graphiques](../debugger/walkthrough-capturing-graphics-information.md)  
  
- [Procédure pas à pas : capture d’informations graphiques par programmation](../debugger/walkthrough-capturing-graphics-information-programmatically.md)  
  
## <a name="use-graphics-diagnostics-with-an-arm-based-device"></a>Utiliser Graphics Diagnostics avec un appareil ARM  
 Vous pouvez utiliser Graphics Diagnostics pour déboguer votre application Direct3D sur un appareil ARM via le débogage distant. Pour plus d'informations, consultez [Guide pratique pour utiliser Graphics Diagnostics avec un appareil ARM](../debugger/how-to-use-graphics-diagnostics-with-an-arm-device.md).  
  
## <a name="playing-back-graphics-information"></a>Lecture des informations graphiques  
 Après avoir capturé les informations graphiques d'une application en cours d'exécution, vous pouvez lire les événements capturés pour diagnostiquer les problèmes de rendu. Pour la lecture, vous pouvez soit utiliser votre ordinateur de développement, soit un ordinateur ou un appareil distant auquel vous êtes connecté. Pour plus d’informations, consultez [Guide pratique pour modifier l’ordinateur de lecture Graphics Diagnostics](../debugger/how-to-change-the-graphics-diagnostics-playback-machine.md).  
  
## <a name="debugging-missing-objects"></a>Débogage des objets manquants  
 L'absence d'un ou plusieurs objets est l'un des problèmes de rendu les plus courants auxquels les développeurs graphiques sont confrontés. Ce type de problème peut être difficile à diagnostiquer, car plusieurs types d'erreurs peuvent être à l'origine de la disparition apparente d'un objet. Un état de périphérique mal configuré, des problèmes de transformation de la géométrie du ou des objets ou un pipeline graphique mal configuré peuvent expliquer l'absence d'objets.  
  
 Ces scénarios montrent comment utiliser Graphics Diagnostics pour déterminer la raison de l'absence d'un objet et identifier le code qui en est responsable.  
  
- [Procédure pas à pas : objets manquants en raison de l’état du périphérique](../debugger/walkthrough-missing-objects-due-to-device-state.md)  
  
- [Procédure pas à pas : objets manquants en raison de Vertex Shader](../debugger/walkthrough-missing-objects-due-to-vertex-shading.md)  
  
- [Procédure pas à pas : objets manquants en raison d’un pipeline mal configuré](../debugger/walkthrough-missing-objects-due-to-misconfigured-pipeline.md)  
  
## <a name="debugging-rendering-errors"></a>Débogage des erreurs de rendu  
 Un objet (ou des objets) n'ayant pas l'apparence correcte est un autre problème courant auquel les développeurs graphiques sont confrontés. Il peut être difficile diagnostiquer ce type de problème, car l’apparence incorrecte et sa cause peuvent aussi bien être évidents (liaison de la mauvaise texture) que très subtils (bogue dans le code du nuanceur ou interaction inattendue entre des nuanceurs). Certains problèmes peuvent être occasionnés par une combinaison d'erreurs.  
  
 Voici un scénario qui montre comment utiliser Graphics Diagnostics pour localiser un problème de rendu, pas si subtil, provoqué par un bogue de nuanceur mineur :  
  
- [Procédure pas à pas : débogage des erreurs de rendu dues à l’ombrage](../debugger/walkthrough-debugging-rendering-errors-due-to-shading.md)  
  
## <a name="debugging-compute-shaders"></a>Débogage des nuanceurs de calcul  
 Vous pouvez utiliser Graphics Diagnostics pour déboguer des noyaux de nuanceur de calcul DirectCompute qui génèrent des résultats incorrects. Avec DirectCompute, vous pouvez utiliser la puissance de calcul du GPU pour effectuer des calculs sur un grand nombre d'éléments de données en parallèle. Pour certains types de problèmes, l'utilisation du GPU peut donner des résultats beaucoup plus rapides qu'un code d'UC même bien optimisé. Cependant, les débogueurs classiques ne peuvent pas détecter le code qui s'exécute sur le GPU. Déboguer ce type de code nécessite des outils spécialisés qui sont souvent propres au fournisseur et peuvent ne pas s'intégrer correctement à Visual Studio. Pour améliorer la cohérence du débogage des nuanceurs de calcul avec divers types de GPU, Graphics Diagnostics capture les événements de distribution DirectCompute (en plus des événements de rendu Direct3D) pour vous permettre d'utiliser des outils qui vous sont familiers pour déboguer les problèmes au niveau de votre code de nuanceur de calcul.  
  
 Pour un scénario qui montre comment déboguer un problème de simulation qui est provoqué par un bogue dans un nuanceur de calcul, consultez [procédure pas à pas : À l’aide de Graphics Diagnostics pour déboguer un nuanceur de calcul](../debugger/walkthrough-using-graphics-diagnostics-to-debug-a-compute-shader.md).
