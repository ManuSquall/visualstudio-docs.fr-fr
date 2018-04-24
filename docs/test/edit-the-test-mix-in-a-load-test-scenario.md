---
title: Combinaison de tests pour un scénario de test de charge dans Visual Studio | Microsoft Docs
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, adding tests
- test mix
- load tests, test mix
- load tests, removing tests
ms.assetid: 303e1d70-5d98-424a-b51e-e0898e16d3f8
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-ide-test
ms.openlocfilehash: 9c7f0cb4c25c99c7ab68400d63e1ec52253a5f61
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="edit-the-test-mix-to-specify-which-web-performance-unit-and-coded-ui-tests-to-include-in-a-load-test-scenario"></a>Modifier la combinaison de tests pour spécifier les tests de performances web, les tests unitaires et les tests codés de l’interface utilisateur à inclure dans un scénario de test de charge

La *combinaison de tests* d’un scénario associe la sélection des tests de performances web et des tests unitaires contenus dans le scénario, et la distribution de ces tests dans le scénario. La distribution est un paramètre que vous pouvez spécifier pour la probabilité qu'un test particulier sera sélectionné par un utilisateur virtuel durant une série de tests de charge.

 Une fois que vous avez ajouté un ensemble de tests à un test de charge, la *combinaison de tests* fonctionne comme les autres options de combinaison. Un utilisateur virtuel sélectionne de manière aléatoire un test, selon la probabilité que vous avez spécifiée dans la combinaison. Par exemple, si vous avez deux tests, chacun représentant 50 % de la combinaison, un nouvel utilisateur virtuel choisit d'exécuter le premier test environ une fois sur deux. Dans une combinaison 50/50, si un test est long et que l'autre est court, une charge plus importante provient du test long.

 Après avoir ajouté des tests à la combinaison, vous pouvez les supprimer si nécessaire. Vous pouvez également modifier la distribution de la combinaison à l'aide du contrôle de combinaison de tests. Le contrôle de combinaison vous permet d'ajuster facilement la distribution des tests dans le scénario.

> [!NOTE]
> La distribution est une mesure de la probabilité selon laquelle un test particulier sera sélectionné par un utilisateur virtuel au cours d'une série de tests de charge. La distribution est exprimée sous la forme d'un pourcentage. Par conséquent, la somme des valeurs de distribution de tous les tests contenus dans un scénario est de 100. Par exemple, si un scénario contient un seul test, la distribution pour ce test est de 100 %.

## <a name="add-new-tests-to-a-test-mix-in-an-existing-scenario"></a>Ajouter de nouveaux tests à une combinaison de tests dans un scénario existant

Lorsque vous créez un scénario à l'aide de l'Assistant Nouveau test de charge, vous pouvez spécifier les tests de performances de site Web et les tests unitaires à ajouter à la combinaison de tests du nouveau scénario.

Vous pouvez ajouter d'autres tests de performances de site Web et tests unitaires à la combinaison de tests du scénario à l'aide de l'éditeur de test de charge.

![Ajout d’un test à un test de charge existant](../test/media/ltest_addingtests.png "LTest_AddingTests")

### <a name="to-add-more-tests-to-an-existing-scenario"></a>Pour ajouter plusieurs tests à un scénario existant

1.  Ouvrez un test de charge.

2.  Dans l’éditeur de test de charge, cliquez avec le bouton droit sur un scénario existant, puis choisissez **Ajouter des tests**.

     La boîte de dialogue **Ajouter des tests** s’affiche. Tous les tests de performances de site Web, tests unitaires et tests codés de l'interface utilisateur de votre solution qui ne figurent pas déjà dans votre scénario peuvent y être ajoutés.

3.  Dans le volet **Tests disponibles**, sélectionnez les tests de performances web, les tests unitaires et les tests codés de l’interface utilisateur à ajouter. Choisissez la flèche droite pour ajouter les tests au volet **Tests sélectionnés**.

4.  Une fois que vous avez fini d’ajouter les tests, choisissez **OK**.

     Les tests sont ajoutés à la combinaison de tests. Une nouvelle distribution leur est automatiquement assignée.

5.  (Facultatif) Ajustez le contrôle de combinaison pour spécifier la distribution de test. Pour plus d’informations, consultez [À propos du contrôle de combinaison](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md).

##  <a name="EditingTestMixRemoveTest"></a> Suppression de tests d’un scénario
 ![Suppression d’un test d’un test de charge existant](../test/media/ltest_removetest.png "LTest_RemoveTest")

### <a name="to-remove-tests-from-a-scenario"></a>Pour supprimer des tests d'un scénario

1.  Ouvrez un test de charge.

2.  Dans l’éditeur de test de charge, dans l’arborescence des tests de charge, cliquez avec le bouton droit sur le scénario dont vous souhaitez supprimer un test, puis sélectionnez **Modifier la combinaison de tests**. La boîte de dialogue **Modifier la combinaison de tests** s’affiche.

3.  Sélectionnez le test de performances web, le test unitaire ou le test codé de l’interface utilisateur dans la grille, puis choisissez **Supprimer**.

    > [!NOTE]
    > Après avoir supprimé le test, ajustez la combinaison de tests à la distribution de votre choix.

4.  Une fois que vous avez fini de supprimer les tests, choisissez **OK**.

##  <a name="EditingTestMixAboutMixControl"></a> À propos du contrôle de combinaison
 Le contrôle de combinaison vous permet d'ajuster le pourcentage de charge distribuée entre les tests, les types de navigateurs ou les types de réseaux dans un scénario de test de charge. Vous ajustez les valeurs en pourcentage en déplaçant des curseurs. L'ajustement de la combinaison de tests spécifie la probabilité qu'un utilisateur virtuel exécute un test spécifique dans un scénario de test de charge.

 Lorsque vous déplacez un curseur, les valeurs en pourcentage de tous les éléments disponibles changent. Si plus de deux éléments sont disponibles, la charge que vous ajoutez ou supprimez est répartie de manière égale entre les autres éléments. Il est possible de modifier ce comportement. Si vous activez la case à cocher dans la colonne de verrouillage d'un élément particulier, vous verrouillez la valeur en pourcentage spécifiée pour cet élément. Ensuite, lorsque vous déplacez un curseur, la charge que vous ajoutez ou supprimez ne s'applique qu'aux éléments non verrouillés restants.

 Le bouton **Distribuer** est utilisé pour allouer les pourcentages de manière égale entre tous les éléments. Par exemple, si trois éléments sont disponibles et si vous choisissez **Distribuer**, les pourcentages sont 34, 33 et 33.

> [!WARNING]
>  Le bouton **Distribuer** permet de remplacer les éléments verrouillés.

 Il est également possible de taper les valeurs en pourcentage directement dans la colonne **%** au lieu d’utiliser les curseurs. Si vous entrez directement une valeur en pourcentage, les autres éléments ne s'ajustent pas automatiquement.

> [!NOTE]
>  Les curseurs sont désactivés quand le total n’atteint pas 100 % ou quand les valeurs en pourcentage entrées dans la colonne **%** sont des nombres décimaux.

 Lorsque vous entrez des valeurs en pourcentage manuellement, vous devez vous assurer que la somme de tous les éléments est 100 %. Lorsque vous enregistrez une combinaison, si la somme n'est pas égale à 100 %, vous serez invité à accepter les valeurs en pourcentage telles qu'elles sont ou à revenir en arrière pour les ajuster. Si vous choisissez de les accepter tels qu'ils sont, ils seront recalculés au prorata de 100 %.  Par exemple, si deux éléments sont disponibles et que vous les définissez manuellement à 80 % et 40 %, le premier élément aura pour valeur 66,67 % (80 divisé par 120) et le deuxième élément sera défini à 33,33 % (40 divisé par 120).

## <a name="see-also"></a>Voir aussi

- [Modification des scénarios de test de charge](../test/edit-load-test-scenarios.md)