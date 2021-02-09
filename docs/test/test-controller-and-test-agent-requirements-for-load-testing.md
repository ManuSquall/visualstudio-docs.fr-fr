---
title: Configuration requise pour le contrôleur de test/agent de test (test de charge)
description: En savoir plus sur les spécifications du contrôleur de test et de l’agent de test pour le test de charge. Visual Studio prend en charge plusieurs types de test.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- agents, requirements
- controllers, requirements
ms.assetid: 372d97ce-12e4-46a9-9863-da508adba68f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: a123a147d038a41f799c2fdf9d4fb26eaa4f3490
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99894489"
---
# <a name="test-controller-and-test-agent-requirements-for-load-testing"></a>Configuration requise du contrôleur de test et de l’agent de test pour le test de charge

Visual Studio intègre plusieurs types de tests, notamment les tests de performances web, les tests de charge et les tests manuels. Visual Studio permet aux utilisateurs de Visual Studio Application Lifecycle Management d’exécuter des tests sur des ordinateurs distants à l’aide d’un contrôleur de test et d’un ou plusieurs agents. Consultez [Installer et configurer des agents de test](../test/lab-management/install-configure-test-agents.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="hardware-and-software-requirements"></a>Spécifications matérielles et logicielles

À la fois les ordinateurs du contrôleur de test et de l'agent de test ont des configurations matérielle et logicielle requises spécifiques. De plus, pour déployer les ordinateurs des agents de test et du contrôleur de test en plusieurs langues, vous devez planifier la prise en charge de ces langues.

### <a name="hardware-requirements"></a>Configuration matérielle requise

Le tableau suivant affiche la configuration matérielle requise recommandée pour le déploiement d'un contrôleur de test et d'agents de test.

|**Configuration**|**Composant**|**UC**|**Disque dur**|**Mémoire**|
|-|-------------------|-|------------|-|
|< 500 utilisateurs virtuels|Agent de test|2,6 GHz|10 Go|2 Go|
|< 1 000 utilisateurs virtuels|Agent de test|Biprocesseur, 2,6 GHz|10 Go|2 Go|
|N x 1 000 utilisateurs virtuels|Agent de test|Évolutivité à N agents avec, chacun, un biprocesseur 2,6 GHz|10 Go|2 Go|
|\< 30 ordinateurs dans l’environnement de test. Avec agents et serveurs en cours de test.|Test Controller|2,6 GHz|||
|N x 30 ordinateurs dans l'environnement de test. Avec agents et serveurs en cours de test.|Test Controller|N processeurs 2,6 GHz|||

> [!NOTE]
> Le nombre d'utilisateurs virtuels varie considérablement d'un test à l'autre. Cette variation est due en grande partie au *temps de réflexion* ou délai d’utilisateur. Pour plus d’informations, consultez [Modifier les temps de réflexion pour simuler les délais d’interaction humaine avec un site web](../test/edit-think-times-in-load-test-scenarios.md). Dans un test de charge, les tests web sont généralement plus efficaces et génèrent une plus grande charge que les tests unitaires. Les chiffres du tableau précédent s'appliquent aux tests web avec un temps de réflexion de 3 à 5 secondes dans une applications web typique.

Les indications présentées ici fournissent une aide générale en matière de planification matérielle. Les performances des tests seront très différentes selon la quantité de données des tests et le nombre d'agents de test. Pour les agents de test, la vitesse du processeur et la mémoire disponible limiteront la charge du test. Les contrôleurs de test ont besoin de ressources plus nombreuses en fonction du nombre d'agents de test et du volume de données impliqués dans les tests.

Le serveur qui exécute Visual Studio doit disposer d’une connexion réseau fiable avec une bande passante d’au moins 1 Mbit/s et une latence maximale de 350 ms. Il ne doit y avoir aucun pare-feu entre les agents de test et le contrôleur de test. Si vos performances de tests ne répondent pas à vos attentes, songez à mettre votre configuration matérielle à niveau.

### <a name="additional-hardware-considerations"></a>Considérations sur le matériel supplémentaire

Les agents de test génèrent un large volume de données sur les contrôleurs de test, selon la durée et la taille du test. En général, vous devez prévoir 10 Go supplémentaires de stockage sur le disque dur pour 24 heures de données de test.

Outre le matériel recommandé ici, vous devez envisager d'acquérir du matériel supplémentaire pour les serveurs critiques, tels qu'une alimentation et des ventilateurs supplémentaires.

### <a name="language-requirements"></a>Exigences relatives à la langue

Pour éviter toute confusion et simplifier l’opération, un contrôleur de test et des agents de test doivent être configurés pour utiliser la même langue que le système d’exploitation de l’ordinateur et que celle de Team Foundation Server. Si l'agent de test et le contrôleur de test sont installés sur des ordinateurs différents, ils doivent être configurés afin d'utiliser la même langue. Toutefois, vous pouvez installer une autre version linguistique de Visual Studio sous un système d’exploitation en langue anglaise, si tant est que cette langue correspond à celle du déploiement de Team Foundation Server.

## <a name="monitor-agent-resources"></a>Surveiller les ressources des agents

Vous pouvez monitorer les ordinateurs agents pour déterminer leurs besoins en matière de ressources, en observant les processus *QTAgent\*.exe* qui sont exécutés et mis à l’échelle pendant les tests. Le goulot d’étranglement le plus courant pendant les processus *QTAgent\*.exe* correspond à l’utilisation du processeur. Si l'utilisation du processeur est constamment supérieure à 95 %, cela indique que l'agent subit une charge importante. L'autre goulot d'étranglement courant est l'utilisation de la mémoire. Pour les tests exigeants, la surveillance de ces ressources peut aider à déterminer si une augmentation des ressources de l'ordinateur est nécessaire ou si les tests doivent être répartis différemment.

## <a name="see-also"></a>Voir aussi

- [Installer et configurer des agents de test](../test/lab-management/install-configure-test-agents.md)
