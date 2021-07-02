---
title: Didacticiel de l’ancrage-étapes suivantes
description: Décrit les options permettant d’étendre les applications de l’arrimeur à l’aide d’une orchestration, en utilisant des projets Cloud Native Computing Foundation.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jmartens
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: e777d80f44c9a11e4d2a893c968d33e348ca442a
ms.sourcegitcommit: 8b75524dc544e34d09ef428c3ebbc9b09f14982d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2021
ms.locfileid: "113222693"
---
# <a name="whats-next"></a>Étapes suivantes

Bien que vous ayez terminé avec votre didacticiel, il reste beaucoup à apprendre sur les conteneurs !
Vous n’allez pas aller plus loin ici, mais voici quelques autres points à prendre en compte.

## <a name="container-orchestration"></a>Orchestration de conteneurs

L’exécution de conteneurs en production est délicate. Vous ne souhaitez pas vous connecter à une machine et exécuter simplement un `docker run` ou un `docker-compose up` . Pourquoi cela ne fonctionne-t-il pas ? Eh bien, que se passe-t-il si les conteneurs meurent ? Comment effectuer une mise à l’échelle sur plusieurs machines ? L’orchestration de conteneur résout ce problème. Les outils tels que Kubernetes, essaim, Nomad et AKS aident à résoudre ce problème, de manière légèrement différente.

L’idée générale est que vous avez des « responsables » qui reçoivent l' **État attendu**. Cet État peut être « je souhaite exécuter deux instances de mon application Web et exposer le port 80 ». Les responsables examinent ensuite tous les ordinateurs du cluster et délèguent le travail aux nœuds « Worker ». Les responsables de la surveillance des modifications (par exemple, un conteneur quittant), puis de faire en sorte que l' **état réel** reflète l’État attendu.

## <a name="cloud-native-computing-foundation-projects"></a>Projets Cloud Native Computing Foundation

Le CNCF est un logement indépendant du fournisseur pour différents projets open source, dont Kubernetes, Prometheus, Envoy, Linkerd, NAT et bien plus encore ! Vous pouvez afficher les [projets gradués et incubes ici](https://www.cncf.io/projects/) , ainsi que l’intégralité du [paysage CNCF ici](https://landscape.cncf.io/). Il existe un grand nombre de projets pour vous aider à résoudre les problèmes liés à la surveillance, à la journalisation, à la sécurité, aux registres d’images, à la messagerie et bien plus encore.

Si vous débutez avec le paysage de conteneur et le développement d’applications natives Cloud, Bienvenue ! Connectez-vous à la Communauté, posez des questions et continuez vos formations ! Nous sommes ravis de vous en faire !

## <a name="working-with-docker-in-vs-code"></a>Utilisation de l’amarrage dans VS Code

en savoir plus sur l’utilisation de l’extension VS Code docker :

- [VS Code Vue d’ensemble de l’extension dockr](https://code.visualstudio.com/docs/containers/overview)
- [Prise en main de Node.js](https://code.visualstudio.com/docs/containers/quickstart-node)
- [Bien démarrer avec Python](https://code.visualstudio.com/docs/containers/quickstart-python)
- [Bien démarrer avec .NET Core](https://code.visualstudio.com/docs/containers/quickstart-aspnet-core)
- [Déboguer des applications en conteneur](https://code.visualstudio.com/docs/containers/debug-common)
