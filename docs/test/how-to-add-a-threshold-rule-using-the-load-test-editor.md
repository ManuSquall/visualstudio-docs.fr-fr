---
title: Ajouter une règle de seuil pour un test de charge dans Visual Studio
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
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: ede6e8d3dde3b8a6f76164b02457a98102bcbac7
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31965544"
---
# <a name="how-to-add-a-threshold-rule-using-the-load-test-editor"></a>Guide pratique pour ajouter une règle de seuil à l’aide de l’éditeur de test de charge

Les règles de seuil contenues dans des tests de charge comparent une valeur de compteur de performance à une valeur de constante ou une autre valeur de compteur de performance.

## <a name="to-add-a-threshold-rule"></a>Pour ajouter une règle de seuil

1.  Ouvrez un test de charge.

2.  Dans l’éditeur de test de charge, développez le nœud **Ensembles de compteurs**.

3.  Développez l’une des **Catégories de compteur** dans l’un des Ensembles de compteurs. Par exemple, vous pouvez sélectionner **LoadTest:Scenario**. Développez le nœud.

4.  Cliquez avec le bouton droit sur l’un des compteurs, par exemple **Charge utilisateur**, sous **LoadTest:Scenario**. Sélectionnez **Ajouter une règle de seuil**.

     La boîte de dialogue **Ajouter une règle de seuil** s’affiche.

5.  Vous pouvez choisir parmi deux types de règles : Comparer une constante et Comparer des compteurs. Sélectionnez le type approprié et définissez les valeurs.

    > [!NOTE]
    > Affectez à la propriété **Alerte en cas de dépassement** la valeur **True** pour indiquer que le dépassement d’un seuil constitue un problème, ou la valeur **False** pour indiquer que le fait de ne pas atteindre un seuil constitue un problème.

## <a name="see-also"></a>Voir aussi

- [Analyse des violations des règles de seuil](../test/analyze-threshold-rule-violations-in-load-tests.md)
- [Spécification des ensembles de compteurs et des règles de seuil pour les ordinateurs dans un test de charge](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [Analyser les résultats des tests de charge](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Spécification des ensembles de compteurs et des règles de seuil pour les ordinateurs dans un test de charge](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)