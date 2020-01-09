---
title: Durée de démarrage de l’étape d’un modèle de charge par étape pour les tests de charge
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, load patterns
ms.assetid: 4a69e857-f93b-4907-9a01-fd1b66291205
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a40f7ce4aacfdc03b5e05becbfc83439945f7e8a
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75588913"
---
# <a name="how-to-specify-the-step-ramp-time-property-for-a-step-load-pattern"></a>Guide pratique pour spécifier la propriété de la durée de démarrage de l’étape dans le modèle de charge

Après avoir créé votre test de charge avec l’**Assistant Nouveau test de charge**, vous pouvez utiliser l’**éditeur de test de charge** pour changer les propriétés des scénarios en fonction de vos besoins et objectifs. Pour plus d’informations, consultez [Procédure pas à pas : création et exécution d’un test de charge](../test/walkthrough-create-and-run-a-load-test.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!NOTE]
> Pour obtenir une liste complète des propriétés des scénarios de test de charge et leurs descriptions, consultez [Propriétés du scénario de test de charge](../test/load-test-scenario-properties.md).

La propriété **Durée de démarrage de l’étape** est définie dans la fenêtre **Propriétés**. Vous modifiez des propriétés du scénario de test de charge dans **l’Éditeur de test de charge**.

La propriété **Durée de démarrage de l’étape** est utilisée uniquement avec un modèle de charge dans l’étape. Pour plus d’informations, consultez [Modifier les modèles de charge en modèle d’activités des utilisateurs virtuels](../test/edit-load-patterns-to-model-virtual-user-activities.md).

Un modèle de charge dans l'étape est utilisé pour augmenter la charge sur le ou les serveurs au cours de l'exécution du test de charge pour voir comment les performances varient au fur et à mesure que la charge utilisateur augmente. Par exemple, pour voir les performances de votre serveur ou de vos serveurs lorsque la charge utilisateur passe à 2 000 utilisateurs, vous pouvez exécuter un test de charge de 10 heures à l'aide d'un modèle de charge dans l'étape dont les propriétés sont les suivantes :

- Nombre initial d'utilisateurs : 100

- Nombre maximal d'utilisateurs : 2 000

- Durée de l'étape (secondes) : 1 800

- Durée de démarrage de l'étape (secondes) : 20

- Nombre d'utilisateurs dans l'étape : 100

Ces paramètres exécutent le test de charge pendant 30 minutes (1 800 secondes) avec des charges utilisateur de 100, 200, 300 et jusqu'à 2 000 utilisateurs.

> [!NOTE]
> La propriété **Durée de démarrage de l’étape** est la seule propriété qui ne peut pas être sélectionnée dans **l’Assistant Nouveau test de charge**.

La propriété **Durée de démarrage de l’étape** autorise l’accroissement par étape (par exemple de 100 à 200 utilisateurs) graduel plutôt qu’immédiat. Dans l'exemple, la charge utilisateur passerait de 100 à 200 utilisateurs sur une période de 20 secondes (soit une augmentation de 5 utilisateurs par seconde).

## <a name="to-edit-the-step-ramp-time-property-for-a-step-load-pattern"></a>Pour modifier la propriété Durée de démarrage de l’étape d’un modèle de charge dans l’étape

1. Ouvrez un test de charge.

     **L’éditeur de test de charge** s’affiche. L'arborescence du test de charge s'affiche.

2. Dans le dossier **Scénarios** des arborescences du test de charge, ouvrez le nœud de scénario pour lequel vous voulez spécifier la durée de démarrage de l’étape.

3. Sélectionnez le nœud **Modèle de charge dans l’étape**.

    > [!NOTE]
    > Le modèle de charge du scénario doit être un modèle de charge dans l'étape. Si ce n'est pas le cas, le modèle de charge affichera le type du modèle de charge associé actuellement au scénario. Pour plus d’informations, consultez [Modifier les modèles de charge en modèle d’activités des utilisateurs virtuels](../test/edit-load-patterns-to-model-virtual-user-activities.md).

4. Dans le menu **Affichage**, sélectionnez **Fenêtre Propriétés**.

     Les catégories et les propriétés du scénario sont affichées dans la fenêtre **Propriétés**.

5. Définissez la valeur de la propriété **Durée de démarrage de l’étape** en entrant un nombre pour les secondes prises dans chaque étape afin d’ajouter progressivement les utilisateurs spécifiés par la propriété **Nombre d’utilisateurs dans l’étape**.

6. Après avoir changé la propriété, choisissez **Enregistrer** dans le menu **Fichier**. Vous pouvez ensuite exécuter votre test de charge à l’aide de la nouvelle valeur **Durée de démarrage de l’étape**.

## <a name="see-also"></a>Voir aussi

- [Modifier les scénarios de test de charge](../test/edit-load-test-scenarios.md)
- [Contrôleurs de test et agents de test](configure-test-agents-and-controllers-for-load-tests.md)
- [Propriétés des scénarios de test de charge](../test/load-test-scenario-properties.md)
- [Modifier les modèles de charge en modèle d’activités des utilisateurs virtuels](../test/edit-load-patterns-to-model-virtual-user-activities.md)
