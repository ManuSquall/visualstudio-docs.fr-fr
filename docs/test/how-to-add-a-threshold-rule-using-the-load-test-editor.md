---
title: Ajouter une règle de seuil pour un test de charge
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, monitoring
- load tests, thresholds
- load tests, analyzing
- thresholds in load tests
ms.assetid: 3d8fac8f-426f-4155-9ced-f7cd4c79792c
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 2a5865eba5ec6971a35104af3ccd090ee6b06410
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63002295"
---
# <a name="how-to-add-a-threshold-rule-using-the-load-test-editor"></a>Procédure : ajouter une règle de seuil à l’aide de l’éditeur de test de charge

Les règles de seuil contenues dans des tests de charge comparent une valeur de compteur de performance à une valeur de constante ou une autre valeur de compteur de performance.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-add-a-threshold-rule"></a>Pour ajouter une règle de seuil

1. Ouvrez un test de charge.

2. Dans l’éditeur de test de charge, développez le nœud **Ensembles de compteurs**.

3. Développez l’une des **Catégories de compteur** dans l’un des Ensembles de compteurs. Par exemple, vous pouvez sélectionner **LoadTest:Scenario**. Développez le nœud.

4. Cliquez avec le bouton droit sur l’un des compteurs, par exemple **Charge utilisateur**, sous **LoadTest:Scenario**. Sélectionnez **Ajouter une règle de seuil**.

     La boîte de dialogue **Ajouter une règle de seuil** s’affiche.

5. Vous avez le choix entre deux types de règle : **Comparer une constante** et **Comparer des compteurs**. Sélectionnez le type approprié et définissez les valeurs.

    > [!NOTE]
    > Affectez à la propriété **Alerte en cas de dépassement** la valeur **True** pour indiquer que le dépassement d’un seuil constitue un problème, ou la valeur **False** pour indiquer que le fait de ne pas atteindre un seuil constitue un problème.

## <a name="see-also"></a>Voir aussi

- [Analyser les violations des règles de seuil](../test/analyze-threshold-rule-violations-in-load-tests.md)
- [Spécifier les ensembles de compteurs et les règles de seuil des ordinateurs dans un test de charge](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [Analyser les résultats des tests de charge](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
