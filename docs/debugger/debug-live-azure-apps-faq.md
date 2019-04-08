---
title: Questions fréquentes (FAQ) sur le débogage d’instantané | Microsoft Docs
ms.date: 11/07/2017
ms.topic: reference
helpviewer_keywords:
- debugger
ms.assetid: 944f1eb0-a74b-4d28-ae2b-a370cd869add
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7ea593ad5f88ba29f6b1c0d7c64a129b8f71c7f5
ms.sourcegitcommit: 509fc3a324b7748f96a072d0023572f8a645bffc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58857072"
---
# <a name="frequently-asked-questions-for-snapshot-debugging-in-visual-studio"></a>Questions fréquentes sur le débogage d’instantané dans Visual Studio

Voici une liste de questions qui peuvent survenir lors du débogage d’applications Azure en production à l’aide du Débogueur de capture instantanée.

#### <a name="what-is-the-performance-cost-of-taking-a-snapshot"></a>Quel est le coût en matière de performances de la prise d’un instantané ?

Lorsque le Débogueur de capture instantanée capture un instantané de votre application, il duplique (fork) le processu de l’application et interrompt la copie dupliquée. Lorsque vous déboguez un instantané, vous déboguez sur la copie dupliquée du processus. Ce processus ne prend que 10 à 20 millisecondes, mais ne copie pas le tas complet de l’application. À la place, il copie uniquement la table des pages et définit les pages sur « copie pour écriture ». Si certains des objets de votre application sur la pile changent, leurs pages correspondantes sont alors copiées. C’est pourquoi chaque capture instantanée a un petit coût en mémoire (de l’ordre de centaines de kilo-octets pour la plupart des applications).

#### <a name="what-happens-if-i-have-a-scaled-out-azure-app-service-multiple-instances-of-my-app"></a>Que se passe-t-il si j’ai un Azure App Service scaled-out (plusieurs instances de mon application) ?

Lorsque vous avez plusieurs instances de votre application, les snappoints sont appliqués à chaque instance unique. Seul le premier snappoint à atteindre les conditions spécifiées crée un instantané. Si vous avez plusieurs snappoints, les instantanés ultérieurs proviennent de l’instance qui a créé le premier instantané. Les logpoints envoyés à la fenêtre de sortie affichent uniquement les messages d’une instance, tandis que les logpoints envoyés aux journaux d’application envoient des messages à partir de chaque instance.

#### <a name="how-does-the-snapshot-debugger-load-symbols"></a>Comment le Débogueur de capture instantanée charge-t-il des symboles ?

Le Débogueur de capture instantanée nécessite que vous ayez les symboles correspondants pour votre application de manière locale ou déployée sur votre Azure App Service. (Les PDB incorporés ne sont actuellement pas pris en charge.) Le Débogueur de capture instantanée télécharge automatiquement les symboles à partir de votre Azure App Service. À partir de Visual Studio 2017 version 15.2, le déploiement sur Azure App Service déploie également les symboles de votre application.

#### <a name="does-the-snapshot-debugger-work-against-release-builds-of-my-application"></a>Le Débogueur de capture instantanée fonctionne-t-il avec les builds de publication de mon application ?

Oui. Le Débogueur de capture instantanée est prévu pour fonctionner sur les builds de publication. Lorsqu’un snappoint est placé dans une fonction, la fonction est recompilée dans une version de débogage, pour la rendre compatible avec le débogage. L’arrêt du Débogueur de capture instantanée restaure les fonctions sur la build de publication.

#### <a name="can-logpoints-cause-side-effects-in-my-production-application"></a>Les logpoints peuvent-ils provoquer des effets secondaires dans mon application de production ?

Non. Les messages de journal que vous ajoutez à votre application sont évalués de manière virtuelle. Ils ne peuvent pas causer d’effets secondaires dans votre application. Toutefois, certaines propriétés natives peuvent ne pas être accessibles avec les logpoints.

#### <a name="does-the-snapshot-debugger-work-if-my-server-is-under-load"></a>Le Débogueur de capture instantanée fonctionne-t-il si mon serveur est en charge ?

Oui, le débogage d’instantané peut fonctionner pour les serveurs en charge. Le Débogueur de capture instantanée limite et ne capture pas les instantanés en cas de faible quantité de mémoire disponible sur votre serveur.

#### <a name="how-do-i-uninstall-the-snapshot-debugger"></a>Comment désinstaller le Débogueur de capture instantanée ?

Vous pouvez désinstaller l’extension de site du Débogueur de capture instantanée sur votre App Service en procédant comme suit :

1. Désactivez votre App Service via Cloud Explorer dans Visual Studio ou le portail Azure.
1. Accédez au site Kudu de votre App Service (autrement dit, yourappservice.**scm**.azurewebsites.net) et accédez à **Extensions de site**.
1. Cliquez sur le X de l’extension de site du Débogueur de capture instantanée pour le supprimer.

#### <a name="why-are-ports-opened-during-a-snapshot-debugger-session"></a>Pourquoi les ports sont-ils ouverts pendant une session du Débogueur de capture instantanée ?

Le Débogueur de capture instantanée doit ouvrir un ensemble de ports pour déboguer les instantanés pris dans Azure, ce sont les mêmes ports requis pour le débogage distant. [Vous trouverez la liste des ports ici](../debugger/remote-debugger-port-assignments.md).

## <a name="see-also"></a>Voir aussi

- [Débogage dans Visual Studio](../debugger/index.md)
- [Déboguer des applications ASP.NET en production avec le Débogueur de capture instantanée](../debugger/debug-live-azure-applications.md)
- [Déboguer des machines virtuelles\groupes de machines virtuelles identiques Azure ASP.NET en production à l’aide du Débogueur de capture instantanée](../debugger/debug-live-azure-virtual-machines.md)
- [Déboguer Azure Kubernetes ASP.NET en production avec le Débogueur de capture instantanée](../debugger/debug-live-azure-kubernetes.md)
- [Résolution des problèmes et problèmes connus du débogage d’instantané](../debugger/debug-live-azure-apps-troubleshooting.md)