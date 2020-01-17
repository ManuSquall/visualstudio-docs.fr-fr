---
title: Spécification de types de réseaux virtuels dans un scénario de test de charge
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, scenarios
- load tests, adding networks
- load tests, removing networks
- load tests, virtual networks
- network mix
ms.assetid: 3c4f7874-081a-4ec4-9510-4d6d7d863a11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 60fa2bd38f3d7e594e9af7ba8ec544518bdbb920
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2020
ms.locfileid: "76115300"
---
# <a name="specify-virtual-network-types-in-a-load-test-scenario"></a>Spécifier des types de réseaux virtuels dans un scénario de test de charge

La *combinaison de réseaux* vous permet de simuler une charge avec plus de réalisme dans un scénario de test de charge. La charge est générée à l'aide d'une combinaison hétérogène de types de réseaux au lieu d'un seul type de réseau. Vous créez une meilleure approximation de la façon dont les utilisateurs finaux interagissent avec vos applications.

Une combinaison de réseaux spécifie la probabilité qu’un utilisateur virtuel exécute un *profil réseau* donné. Un profil réseau est une simulation de bande passante réseau au niveau de la couche Application. Il ne simule pas la latence.

Lorsque vous créez un test de charge, vous pouvez souhaiter simuler que cette charge soit générée par plusieurs types de connexions réseau. La combinaison de réseaux offre plusieurs types de réseau. Les différents réseaux sont simulés. Quand vous choisissez une option comme `Cable-DSL 1.5Mbps`, des durées d’attente sont injectées dans le test afin de simuler la bande passante sélectionnée.

La combinaison de réseaux fonctionne comme d'autres options de combinaison. Un type de réseau est sélectionné et associé aléatoirement à un utilisateur virtuel, selon la combinaison de réseaux. Les tests de cet utilisateur sont exécutés avec un type de réseau particulier, selon la probabilité que vous avez spécifiée dans la combinaison.

Après avoir spécifié une combinaison de réseaux, vous pouvez ajouter et supprimer des types de réseaux. Vous pouvez également modifier la distribution de la combinaison de réseaux à l'aide du contrôle de combinaison.

Le contrôle de combinaison vous permet d'ajuster facilement la distribution des réseaux dans un scénario.

Pour plus d’informations, consultez [À propos du contrôle de combinaison](../test/specify-virtual-network-types-in-a-load-test-scenario.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="true-network-emulation"></a>Émulation réseau véritable

Visual Studio utilise une émulation de réseau véritable basée sur un logiciel pour tous les types de tests, notamment les tests de charge. L'émulation de réseau véritable simule les conditions d'un réseau par manipulation directe des paquets réseau. L'émulateur de réseau véritable peut émuler le comportement des réseaux avec et sans fil en utilisant un lien physique fiable, par exemple Ethernet. Les attributs de réseau suivants sont incorporés dans une émulation de réseau véritable :

- Délai aller-retour sur le réseau (latence)

- Bande passante disponible

- Comportement de mise en file d'attente

- Perte de paquets

- Réorganisation des paquets

- Propagations des erreurs

L'émulation de réseau véritable fournit également la flexibilité nécessaire au filtrage des paquets réseau selon les adresses IP ou en fonction des protocoles tels que TCP, UDP et ICMP.

L'émulation de réseau véritable peut être utilisée par les développeurs et les testeurs d'applications réseau pour émuler un environnement de test souhaité, évaluer les performances, prévoir l'impact des modifications ou prendre des décisions en matière d'optimisation de technologie. En comparaison des bancs d'essais matériels, l'émulation de réseau véritable est une solution bien plus économique et plus flexible.

## <a name="to-add-new-networks-to-a-scenario"></a>Pour ajouter de nouveaux réseaux à un scénario

1. Durant le processus de spécification de la combinaison de réseaux pour un scénario, choisissez **Ajouter**.

     Une nouvelle entrée de réseau est ajoutée à la grille.

    > [!NOTE]
    > Pour afficher la boîte de dialogue **Modifier la combinaison de réseaux**, cliquez avec le bouton droit sur un scénario existant, puis choisissez **Modifier la combinaison de réseaux**.

2. Dans la colonne **Type de réseau**, cliquez sur la flèche correspondant à la nouvelle entrée. Choisissez le type de réseau désiré.

3. (Facultatif) Ajustez le contrôle de combinaison pour spécifier la distribution de test. Pour plus d’informations, consultez [À propos du contrôle de combinaison](../test/specify-virtual-network-types-in-a-load-test-scenario.md).

4. Une fois que vous avez terminé d’ajouter des réseaux, choisissez **OK**.

## <a name="to-remove-networks-from-a-scenario"></a>Pour supprimer des réseaux d'un scénario

1. Ouvrez un test de charge.

2. Cliquez avec le bouton droit sur le scénario dont vous souhaitez supprimer un réseau, puis choisissez **Modifier la combinaison de réseaux**. La boîte de dialogue **Modifier la combinaison de réseaux** s’affiche.

3. Sélectionnez le réseau dans la grille, puis choisissez **Supprimer**.

4. (Facultatif) Ajustez le contrôle de combinaison pour spécifier la distribution de test. Pour plus d’informations, consultez [À propos du contrôle de combinaison](../test/specify-virtual-network-types-in-a-load-test-scenario.md).

5. Une fois que vous avez fini de supprimer des réseaux, choisissez **OK**.

## <a name="about-the-mix-control"></a>À propos du contrôle de combinaison

Le contrôle de combinaison vous permet d'ajuster le pourcentage de charge distribuée entre les tests, les types de navigateurs ou les types de réseaux dans un scénario de test de charge. Pour ajuster les valeurs en pourcentage, déplacez les curseurs. L'ajustement de la combinaison de types de réseau spécifie la probabilité qu'un utilisateur virtuel exécute un profil réseau spécifique dans un scénario de test de charge.

Lorsque vous déplacez un curseur, les valeurs en pourcentage de tous les éléments disponibles changent. Si plus de deux éléments sont disponibles, la charge que vous ajoutez ou supprimez est répartie de manière égale entre les autres éléments. Il est possible de modifier ce comportement. Si vous activez la case à cocher dans la colonne de verrouillage d'un élément particulier, vous verrouillez la valeur en pourcentage spécifiée pour cet élément. Ensuite, lorsque vous déplacez un curseur, la charge que vous ajoutez ou supprimez ne s'applique qu'aux éléments non verrouillés restants.

Le bouton **Distribuer** permet d’allouer les valeurs en pourcentage de manière égale entre tous les éléments. Par exemple, si trois éléments sont disponibles et si vous choisissez **Distribuer**, les pourcentages sont 34, 33 et 33.

> [!WARNING]
> Le bouton **Distribuer** permet de remplacer les éléments verrouillés.

Il est également possible de taper les valeurs en pourcentage directement dans la colonne **%** au lieu d’utiliser les curseurs. Si vous entrez directement une valeur en pourcentage, les autres éléments ne s'ajustent pas automatiquement.

> [!NOTE]
> Les curseurs sont désactivés quand le total n’atteint pas 100 % ou quand les valeurs en pourcentage entrées dans la colonne **%** sont des nombres décimaux.

Lorsque vous entrez des valeurs en pourcentage manuellement, vous devez vous assurer que la somme de tous les éléments est 100 %. Lorsque vous enregistrez une combinaison, si la somme n'est pas égale à 100 %, vous serez invité à accepter les valeurs en pourcentage telles qu'elles sont ou à revenir en arrière pour les ajuster. Si vous choisissez de les accepter tels qu'ils sont, ils seront recalculés au prorata de 100 %.  Par exemple, si deux éléments sont disponibles et que vous les définissez manuellement à 80 % et 40 %, le premier élément aura pour valeur 66,67 % (80 divisé par 120) et le deuxième élément sera défini à 33,33 % (40 divisé par 120).
