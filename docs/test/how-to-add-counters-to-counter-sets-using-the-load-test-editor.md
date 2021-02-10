---
title: Ajouter des compteurs à des ensembles de compteurs pour les tests de charge
description: Lorsque vous créez un test de charge avec l'Assistant Test de charge, vous ajoutez un ensemble initial de compteurs. Découvrez comment ajouter des compteurs à l’aide de éditeur de test de charge.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- counters, counter sets
- counter sets
- load tests, counter sets
ms.assetid: e17d0e71-f982-4fc1-a2df-a1065d37473d
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: ddfdf00a366c18524d2a666a74c7b7a164400402
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99966966"
---
# <a name="how-to-add-counters-to-counter-sets-using-the-load-test-editor"></a>Guide pratique pour ajouter des compteurs à des ensembles de compteurs à l’aide de l’éditeur de test de charge

Quand vous créez un test de charge avec l’**Assistant Test de charge**, vous ajoutez un ensemble initial de compteurs. Ceux-ci vous offrent un groupe d'ensembles de compteurs prédéfinis pour votre test de charge. Pour plus d’informations, consultez [Spécifier les ensembles de compteurs et des règles de seuil pour les ordinateurs dans un test de charge](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!NOTE]
> Si vos tests de charge sont répartis entre des ordinateurs distants, les compteurs de contrôleur et d'agent sont automatiquement mappés au contrôleur et aux ensembles de compteurs de l'agent. Pour plus d’informations sur l’utilisation de machines distantes dans votre test de charge, consultez [Contrôleurs de test et agents de test](configure-test-agents-and-controllers-for-load-tests.md).

Vous gérez vos compteurs dans **l’éditeur de test de charge**. Les ensembles de compteurs qui sont déjà ajoutés au test sont visibles dans le nœud **Ensembles de compteurs** du test de charge. Après avoir créé un test de charge, vous pouvez ajouter de nouveaux compteurs aux ensembles de compteurs existants.

## <a name="to-add-counters-to-a-counter-set"></a>Pour ajouter des compteurs à un ensemble de compteurs

1. Ouvrez un test de charge.

2. Développez le nœud **Ensembles de compteurs**. Tous les ensembles de compteurs qui ont été ajoutés au test de charge sont visibles.

    > [!NOTE]
    > L’arborescence hiérarchique du test de charge contient également le nœud **Paramètres d’exécution**. Ce nœud contient le nœud **Mappages des ensembles de compteurs**, qui affiche tous les ordinateurs, ainsi que les ensembles de compteurs mappés à ces ordinateurs.

3. Cliquez avec le bouton droit sur un ensemble de compteurs existant, puis choisissez **Ajouter des compteurs**.

     La boîte de dialogue **Sélectionner des compteurs de performance** s’affiche.

4. Dans la zone de liste déroulante fixe **Ordinateur**, tapez le nom de l’ordinateur à mapper. Vous pouvez également sélectionner l'un des ordinateurs répertoriés dans la liste déroulante.

    > [!NOTE]
    > Parce que les ensembles de compteurs doivent être mappés à un ordinateur avant que les données de performance soient rassemblées, vous devez spécifier un ordinateur sur lequel rassembler les données de performance.

5. Sélectionnez une **catégorie de performance** pour filtrer les catégories des compteurs de données de performances. Vous verrez deux colonnes de données à partir desquelles sélectionner des compteurs de performance.

    > [!NOTE]
    > Certaines catégories nécessitent également la sélection d'une instance. Par exemple, si vous sélectionnez un compteur SQL, vous devez sélectionner une instance SQL parce que plusieurs instances de SQL peuvent être installées sur l'ordinateur cible.

6. Sélectionnez un compteur et une instance à ajouter à votre ensemble de compteurs personnalisés.

     \- ou -

     Activez la case d’option **Tous les compteurs** pour sélectionner tous les compteurs disponibles.

7. Choisissez **OK**.

    > [!NOTE]
    > Il est également possible d'ajouter des compteurs à un ensemble de compteurs en cliquant sur un compteur ou une catégorie de compteurs, en cliquant sur Copier, puis en le collant sur un autre nœud d'ensemble de compteurs. Il est possible de supprimer les compteurs supplémentaires copiés, mais inutiles.

## <a name="see-also"></a>Voir aussi

- [Spécifier les ensembles de compteurs et les règles de seuil des ordinateurs dans un test de charge](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [Configurer les paramètres d’exécution des tests de charge](../test/configure-load-test-run-settings.md)
