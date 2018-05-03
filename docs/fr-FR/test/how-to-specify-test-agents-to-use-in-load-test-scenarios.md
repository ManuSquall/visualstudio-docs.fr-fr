---
title: Spécifier les agents de test à utiliser pour les scénarios de test de charge dans Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- test agents, load tests
- load tests, scenarios
- load tests, specifying for load tests
- tests agents, load tests, specifying
- load tests, test agents
ms.assetid: e86806dd-5897-4e4c-bfd4-8d687fb72a6e
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: a4aacbd31516e6a3e55f1b543a3cc8f49ea6ce4d
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-specify-test-agents-to-use-in-load-test-scenarios"></a>Comment : spécifier les agents de test à utiliser dans les scénarios de test de charge

Après avoir créé votre test de charge à l’aide de l’**Assistant Nouveau test de charge**, vous pouvez utiliser l’**éditeur de test de charge** pour changer les propriétés des scénarios en fonction de vos besoins et objectifs.

> [!NOTE]
> Pour obtenir une liste complète des propriétés des scénarios de test de charge et leurs descriptions, consultez [Propriétés du scénario de test de charge](../test/load-test-scenario-properties.md).

Spécifiez les agents à l’aide de l’éditeur de test de charge pour changer la propriété **Agents à utiliser** dans la fenêtre Propriétés.

Vous pouvez spécifier les agents que votre scénario doit utiliser si vous vous servez de contrôleurs et d'agents pour exécuter le test de charge à distance. Par exemple, vous pouvez définir un ensemble spécifique d'agents afin de maintenir une cohérence lorsque vous analysez des tendances de performance. En outre, les agents peuvent être distribués géographiquement, afin qu'il y ait une affinité entre les scripts qu'ils exécutent et l'emplacement des agents.

> [!TIP]
> Au lieu de placer physiquement un agent sur le site distant, vous disposez d'une autre option qui consiste à utiliser l'émulation de réseau pour émuler le réseau lent. Pour plus d’informations, consultez [Spécification des types de réseau virtuel](../test/specify-virtual-network-types-in-a-load-test-scenario.md) et [Spécification des types de réseau virtuel](../test/specify-virtual-network-types-in-a-load-test-scenario.md).

Pour plus d’informations, consultez [Contrôleurs de test et agents de test](configure-test-agents-and-controllers-for-load-tests.md).

Il existe une autre raison selon laquelle une partie des agents peuvent comporter des logiciels installés dont la présence est obligatoire pour un scénario particulier.

Vous pouvez contrôler la sélection des agents pour une série de tests donnée à l'aide de rôles dans les paramètres de test. Pour plus d’informations, consultez [Collecter des informations de diagnostic à l’aide des paramètres de test](../test/collect-diagnostic-information-using-test-settings.md).

Si l’utilisation de l’UC d’un ordinateur agent de test est supérieure à 75 % ou si la mémoire physique disponible de cet ordinateur est inférieure à 10 %, ajoutez des agents à votre test de charge afin de garantir que l’ordinateur agent ne se transforme pas en goulot d’étranglement dans votre test de charge.

## <a name="to-specify-the-agents-to-use-for-a-scenario"></a>Pour spécifier les agents à utiliser pour un scénario

1.  Ouvrez un test de charge.

     L'Éditeur de test de charge s'affiche. L’arborescence du test de charge s’affiche.

2.  Dans le dossier **Scénarios** des arborescences du test de charge, choisissez le nœud de scénario pour lequel vous souhaitez spécifier les agents à utiliser.

3.  Dans le menu **Affichage**, sélectionnez **Fenêtre Propriétés**.

     Les catégories et les propriétés du scénario s'affichent dans la fenêtre Propriétés.

4.  Dans la zone de texte de la propriété **Agents à utiliser**, tapez la liste des agents sur lesquels le scénario peut s’exécuter.

     Les agents doivent être séparés par des virgules, par exemple « **Agent1, Agent2, Agent3** ». Si vous laissez la propriété vide, le scénario doit utiliser tous les agents disponibles.

    > [!NOTE]
    > La propriété **Agents à utiliser** est ignorée pour les exécutions locales. Pour les exécutions distantes, s’il n’existe aucun agent spécifié dans **Agents à utiliser**, les tests du scénario ne s’exécutent pas.

5.  Après avoir changé la propriété, choisissez **Enregistrer** dans le menu **Fichier**. Vous pouvez exécuter ensuite votre test de charge à l’aide de la nouvelle valeur associée à **Agents à utiliser**.

## <a name="see-also"></a>Voir aussi

- [Modification des scénarios de test de charge](../test/edit-load-test-scenarios.md)
- [Procédure pas à pas : Créer et exécuter un test de charge](../test/walkthrough-create-and-run-a-load-test.md)
- [Contrôleurs de test et agents de test](configure-test-agents-and-controllers-for-load-tests.md)
- [Propriétés des scénarios de test de charge](../test/load-test-scenario-properties.md)