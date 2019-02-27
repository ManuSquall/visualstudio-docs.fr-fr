---
title: Forum aux questions sur le débogage d’instantané | Microsoft Docs
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
ms.openlocfilehash: f5b6315ba3cc99b60c97e70621f42cf13f6397c9
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56630715"
---
# <a name="frequently-asked-questions-for-snapshot-debugging-in-visual-studio"></a>Forum aux Questions sur le débogage d’instantané dans Visual Studio

Voici une liste de questions qui s’affiche lors du débogage d’applications Azure en production à l’aide du débogueur de capture instantanée.

#### <a name="what-is-the-performance-cost-of-taking-a-snapshot"></a>Qu’est le coût de performances d’un instantané ?

Lorsque le débogueur d’instantané capture un instantané de votre application, il est bifurcation du processus de l’application et la suspension de la copie dupliquée. Lorsque vous déboguez un instantané, vous déboguez contre la copie dupliquée du processus. Ce processus prend uniquement 10-20 millisecondes, mais ne copie pas le tas complet de l’application. Au lieu de cela, il copie uniquement la table des pages et définit les pages à copier lors de l’écriture. Si certains des objets de votre application sur la modification du segment de mémoire, les pages correspondantes sont ensuite copiés. Par conséquent, chaque capture instantanée a un moindre coût en mémoire (selon l’ordre des centaines de kilo-octets pour la plupart des applications).

#### <a name="what-happens-if-i-have-a-scaled-out-azure-app-service-multiple-instances-of-my-app"></a>Que se passe-t-il si j’ai un Service d’applications Azure à grande échelle (plusieurs instances de mon application) ?

Lorsque vous avez plusieurs instances de votre application, les points d’ancrage sont appliquées à chaque instance unique. Uniquement le premier point d’ancrage à atteindre les conditions spécifiées crée un instantané. Si vous avez plusieurs points d’ancrage, les instantanés suivants proviennent de l’instance qui a créé le premier instantané. Points de journalisation envoyé à la fenêtre Sortie affiche uniquement les messages d’une instance, tandis que les points envoyées dans les journaux d’application de journalisation envoyer des messages à partir de chaque instance de.

#### <a name="how-does-the-snapshot-debugger-load-symbols"></a>Comment le débogueur de capture instantanée charger des symboles ?

Le débogueur de capture instantanée nécessite d’avoir les symboles correspondants pour votre application en locale ou déployée sur votre Azure App Service. (Fichiers PDB incorporés sont actuellement pas pris en charge.) Le débogueur de capture instantanée télécharge automatiquement les symboles à partir de votre Azure App Service. À compter de Visual Studio 2017 version 15.2, déployez également Azure App Service déploie les symboles de votre application.

#### <a name="does-the-snapshot-debugger-work-against-release-builds-of-my-application"></a>Le débogueur de capture instantanée fonctionne avec les versions release de mon application ?

Oui - le débogueur de capture instantanée est prévu pour fonctionner sur les versions release. Lorsqu’un point d’ancrage est placé dans une fonction, la fonction est recompilée à une version debug, rendre débogable. Lorsque vous arrêtez le débogueur de capture instantanée, les fonctions sont retournées à leur version Release.

#### <a name="can-logpoints-cause-side-effects-in-my-production-application"></a>Points de journalisation peuvent provoquer des effets secondaires dans mon application de production ?

Les messages de journal que vous ajoutez à votre application sont non - évaluées pratiquement. Ils ne peut avoir des effets secondaires dans votre application. Toutefois, certaines propriétés natives peut-être pas accessibles avec les points de journalisation.

#### <a name="does-the-snapshot-debugger-work-if-my-server-is-under-load"></a>Le débogueur de capture instantanée fonctionne si mon serveur est sous charge ?

Oui, le débogage d’instantané peut fonctionner pour les serveurs sous charge. Le débogueur d’instantané limite et ne capture pas de captures instantanées dans les situations où il existe une faible quantité de mémoire disponible sur votre serveur.

#### <a name="how-do-i-uninstall-the-snapshot-debugger"></a>Comment désinstaller le débogueur de capture instantanée ?

Vous pouvez désinstaller l’extension de site du débogueur de capture instantanée sur votre Service d’application en procédant comme suit :

1. Désactivez l’option de votre application de Service via Cloud Explorer dans Visual Studio ou le portail Azure.
1. Accédez au site de Kudu du Service de votre application (autrement dit, yourappservice. **SCM**. azurewebsites.net) et accédez à **extensions de Site**.
1. Cliquez sur le X sur l’extension de site du débogueur de capture instantanée pour le supprimer.

## <a name="see-also"></a>Voir aussi

- [Débogage dans Visual Studio](../debugger/index.md)
- [Déboguer des applications ASP.NET en production à l’aide du débogueur de capture instantanée](../debugger/debug-live-azure-applications.md)
- [Débogage en direct ASP.NET Azure virtuel Machines\Virtual Machines identiques à l’aide du débogueur de capture instantanée](../debugger/debug-live-azure-virtual-machines.md)
- [Déboguer ASP.NET Azure Kubernetes en direct à l’aide du débogueur de capture instantanée](../debugger/debug-live-azure-kubernetes.md)
- [Problèmes connus et dépannage pour le débogage d’instantané](../debugger/debug-live-azure-apps-troubleshooting.md)