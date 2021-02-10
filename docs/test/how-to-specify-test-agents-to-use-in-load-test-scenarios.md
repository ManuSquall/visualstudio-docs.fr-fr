---
title: spécifier les agents de test à utiliser dans les scénarios de test de charge
description: Découvrez comment spécifier les agents à utiliser dans un scénario en définissant la propriété agents à utiliser dans le Fenêtre Propriétés du éditeur de test de charge.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- test agents, load tests
- load tests, scenarios
- load tests, specifying for load tests
- tests agents, load tests, specifying
- load tests, test agents
ms.assetid: e86806dd-5897-4e4c-bfd4-8d687fb72a6e
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: 0fc1aeb6eed9bf3697d1658a98d00bdfdab42660
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99936208"
---
# <a name="how-to-specify-test-agents-to-use-in-load-test-scenarios"></a>Guide pratique pour spécifier les agents de test à utiliser dans les scénarios de test de charge

Après avoir créé votre test de charge à l’aide de la **nouvelle Assistant test de charge**, vous pouvez utiliser la **éditeur de test de charge** pour modifier les propriétés des scénarios afin de répondre à vos besoins et vos objectifs de test.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!NOTE]
> Pour obtenir une liste complète des propriétés des scénarios de test de charge et leurs descriptions, consultez [Propriétés du scénario de test de charge](../test/load-test-scenario-properties.md).

Les agents sont spécifiés à l’aide de la **éditeur de test de charge** pour modifier la propriété **agents à utiliser** dans la fenêtre **Propriétés** .

Vous pouvez spécifier les agents que votre scénario doit utiliser si vous vous servez de contrôleurs et d'agents pour exécuter le test de charge à distance. Par exemple, vous pouvez définir un ensemble spécifique d'agents afin de maintenir une cohérence lorsque vous analysez des tendances de performance. En outre, les agents peuvent être distribués géographiquement, afin qu'il y ait une affinité entre les scripts qu'ils exécutent et l'emplacement des agents.

> [!TIP]
> Au lieu de placer physiquement un agent sur le site distant, vous disposez d'une autre option qui consiste à utiliser l'émulation de réseau pour émuler le réseau lent. Pour plus d’informations, consultez [Spécifier des types de réseaux virtuels](../test/specify-virtual-network-types-in-a-load-test-scenario.md).

Pour plus d’informations, consultez [Contrôleurs de test et agents de test](configure-test-agents-and-controllers-for-load-tests.md).

Il existe une autre raison selon laquelle une partie des agents peuvent comporter des logiciels installés dont la présence est obligatoire pour un scénario particulier.

Vous pouvez contrôler la sélection des agents pour une série de tests donnée à l'aide de rôles dans les paramètres de test. Pour plus d’informations, consultez  [collecter des informations de diagnostic à l’aide de paramètres de test](../test/collect-diagnostic-information-using-test-settings.md).

Si l'utilisation de l'UC d'un ordinateur agent de test est supérieure à 75 % ou si la mémoire physique disponible de cet ordinateur est inférieure à 10 %, ajoutez des agents à votre test de charge afin de garantir que l'ordinateur agent ne se transforme pas en goulot d'étranglement dans votre test de charge.

## <a name="to-specify-the-agents-to-use-for-a-scenario"></a>Pour spécifier les agents à utiliser pour un scénario

1. Ouvrez un test de charge.

     **L’éditeur de test de charge** s’affiche. L'arborescence du test de charge s'affiche.

2. Dans le dossier **Scénarios** des arborescences du test de charge, choisissez le nœud de scénario pour lequel vous souhaitez spécifier les agents à utiliser.

3. Dans le menu **Affichage**, sélectionnez **Fenêtre Propriétés**.

     Les catégories et les propriétés du scénario s’affichent dans la fenêtre **Propriétés**.

4. Dans la zone de texte de la propriété **Agents à utiliser**, tapez la liste des agents sur lesquels le scénario peut s’exécuter.

     Les agents doivent être séparés par des virgules, par exemple « **Agent1, Agent2, Agent3** ». Si vous laissez la propriété vide, le scénario doit utiliser tous les agents disponibles.

    > [!NOTE]
    > La propriété **Agents à utiliser** est ignorée pour les exécutions locales. Pour les exécutions distantes, s’il n’existe aucun agent spécifié dans **Agents à utiliser**, les tests du scénario ne s’exécutent pas.

5. Une fois que vous avez changé la propriété, choisissez **Enregistrer** dans le menu **Fichier**. Vous pouvez exécuter ensuite votre test de charge à l’aide de la nouvelle valeur associée à **Agents à utiliser**.

## <a name="see-also"></a>Voir aussi

- [Modifier les scénarios de test de charge](../test/edit-load-test-scenarios.md)
- [Procédure pas à pas : Créer et exécuter un test de charge](../test/walkthrough-create-and-run-a-load-test.md)
- [Contrôleurs de test et agents de test](configure-test-agents-and-controllers-for-load-tests.md)
- [Propriétés des scénarios de test de charge](../test/load-test-scenario-properties.md)
