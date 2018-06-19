---
title: Forum aux questions pour le débogage de l’instantané | Documents Microsoft
ms.date: 11/07/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- debugger
ms.assetid: 944f1eb0-a74b-4d28-ae2b-a370cd869add
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8547c14cfd8a59d775c909edb06e3542b18710c8
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31473600"
---
# <a name="frequently-asked-questions-for-snapshot-debugging-in-visual-studio"></a>Forum aux Questions pour la capture instantanée de débogage dans Visual Studio

Voici une liste de questions qui se produit lors du débogage des applications Windows Azure en direct à l’aide du débogueur de l’instantané.

#### <a name="what-is-the-performance-cost-of-taking-a-snapshot"></a>Quel est le coût de performances d’une capture instantanée ?

Lorsque le débogueur de l’instantané capture un instantané de votre application, il est bifurcation le processus d’application et la suspension de la copie comprenant des branches. Lorsque vous déboguez un instantané, vous déboguez contre la copie ramifiée du processus. Ce processus prend uniquement 10 à 20 millisecondes, mais ne copie pas le tas complet de l’application ; au lieu de cela, il copie uniquement la table de la page et définit les pages à copier lors de l’écriture. Si certains des objets de votre application sur la modification du segment de mémoire, leurs pages respectives sont ensuite copiés. Par conséquent, chaque instantané a un coût en mémoire très petit (de l’ordre des centaines de kilo-octets pour la plupart des applications). 

#### <a name="what-happens-if-i-have-a-scaled-out-azure-app-service-multiple-instances-of-my-app"></a>Que se passe-t-il si j’ai un Service d’applications Azure à grande échelle (plusieurs instances de mon application) ?

Lorsque vous avez plusieurs instances de votre application, snappoints appliqués à chaque instance unique. Uniquement la première snappoint atteint aux conditions spécifiées crée un instantané. Si vous avez plusieurs snappoints, instantanés suivantes proviennent de l’instance qui a créé le premier instantané. Logpoints envoyé à la fenêtre sortie affichera uniquement les messages à partir d’une seule instance, tandis que logpoints envoyés pour les journaux des applications envoyer des messages à partir de chaque instance. 

#### <a name="how-does-the-snapshot-debugger-load-symbols"></a>Comment le débogueur de l’instantané de charger des symboles ?

Le débogueur de l’instantané nécessite que vous avez les symboles correspondants pour votre application soit localement ou déployé votre service d’application Azure (fichiers PDB incorporées est actuellement pas pris en charge). Le débogueur de l’instantané télécharge automatiquement les symboles à partir de votre Service d’applications Azure. À compter de Visual Studio 2017 version 15,2, déployez également du Service d’applications Azure déploie les symboles de votre application.

#### <a name="does-the-snapshot-debugger-work-against-release-builds-of-my-application"></a>Le débogueur de l’instantané fonctionne par rapport aux versions release de mon application ?

Oui - le débogueur de l’instantané est prévu pour fonctionner par rapport aux versions release. Lorsqu’un snappoint est placé dans une fonction, la fonction est recompilée à une version debug, rendre débogable. Lorsque vous arrêtez le débogueur de l’instantané, les fonctions sont retournées à leur version Release. 

#### <a name="can-logpoints-cause-side-effects-in-my-production-application"></a>Logpoints peuvent provoquer des effets secondaires dans mon application de production ?

Non - tous les messages de journal que vous ajoutez à votre application sont évaluées virtuellement. Ils ne peut avoir d’effets secondaires dans votre application. Toutefois, certaines propriétés natives peut-être pas accessibles avec logpoints. 

#### <a name="does-the-snapshot-debugger-work-if-my-server-is-under-load"></a>Le débogueur de l’instantané fonctionne si mon serveur est sous charge ?

Oui, le débogage de l’instantané peut fonctionne pour les serveurs sous charge. Le débogueur de l’instantané limite et ne capture pas les instantanés dans les situations où il existe une faible quantité de mémoire disponible sur votre serveur.

#### <a name="how-do-i-uninstall-the-snapshot-debugger"></a>Comment désinstaller le débogueur de l’instantané ?

Vous pouvez désinstaller l’extension site instantané sur votre application de Service avec les étapes suivantes :

1. Désactiver le Service de votre application via l’Explorateur de Cloud dans Visual Studio ou le portail Azure.
1. Accédez au site de Kudu de votre Service d’application (autrement dit, yourappservice. **SCM**. azurewebsites.net) et accédez à **extensions de Site**.
1. Cliquez sur le X sur l’extension de site du débogueur de l’instantané pour le supprimer.

## <a name="see-also"></a>Voir aussi

[Débogage dans Visual Studio](../debugger/index.md)  
[Déboguer des applications ASP.NET en direct à l’aide du débogueur de l’instantané](../debugger/debug-live-azure-applications.md)  
[Problèmes connus et dépannage pour le débogage de l’instantané](../debugger/debug-live-azure-apps-troubleshooting.md)
