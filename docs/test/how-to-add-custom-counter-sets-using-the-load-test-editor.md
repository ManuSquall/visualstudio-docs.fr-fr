---
title: Ajouter des ensembles de compteurs personnalisés pour un test de charge
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- counters, counter sets
- counter sets
- load tests, counter sets
ms.assetid: 499aca80-1069-408d-ac68-326da6a50645
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f7438f657af2ba40fbda5afefbd8a12cc56a2a4c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "76114873"
---
# <a name="how-to-add-custom-counter-sets-using-the-load-test-editor"></a>Guide pratique pour ajouter des ensembles de compteurs personnalisés à l’aide de l’éditeur de test de charge

Quand vous créez un test de charge avec **l’Assistant Nouveau test de charge**, vous ajoutez un ensemble initial de compteurs. Ceux-ci vous offrent un groupe d'ensembles de compteurs prédéfinis pour votre test de charge.

> [!NOTE]
> Si vos tests de charge sont répartis entre des ordinateurs distants, les compteurs de contrôleur et d'agent sont automatiquement mappés au contrôleur et aux ensembles de compteurs de l'agent. Pour plus d’informations sur l’utilisation de machines distantes dans votre test de charge, consultez [Contrôleurs de test et agents de test](configure-test-agents-and-controllers-for-load-tests.md).

Vous gérez vos compteurs dans **l’éditeur de test de charge**. Les ensembles de compteurs qui sont déjà ajoutés au test sont visibles dans le nœud **Ensembles de compteurs** du test de charge. Après avoir créé un test de charge, vous pouvez lui ajouter de nouveaux ensembles de compteurs personnalisés.

![Ensemble de compteurs personnalisé](../test/media/loadtestcustomcounter.png)

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-add-a-custom-counter-set-to-a-load-test"></a>Pour ajouter un ensemble de compteurs personnalisé à un test de charge

1. Ouvrez un test de charge.

2. Développez le nœud **Ensembles de compteurs**. Tous les ensembles de compteurs qui ont été ajoutés au test de charge sont visibles.

3. Cliquez avec le bouton droit sur le nœud **Ensembles de compteurs**, puis sélectionnez **Ajouter un ensemble de compteurs personnalisés**.

    > [!NOTE]
    > L’ensemble de compteurs se voit attribuer un nom par défaut, par exemple **Personnalisé1**. Vous pouvez changer le nom dans la fenêtre **Propriétés**. Appuyez sur **F4** pour afficher la fenêtre **Propriétés**.

4. Pour ajouter des compteurs à votre ensemble de compteurs personnalisés, cliquez avec le bouton droit sur le nouvel ensemble de compteurs, puis choisissez **Ajouter des compteurs**. Pour plus d’informations sur la façon d’ajouter des compteurs, voir [Comment : Ajouter des compteurs pour contrer les ensembles.](../test/how-to-add-counters-to-counter-sets-using-the-load-test-editor.md)

    > [!NOTE]
    > Il est également possible d'ajouter un ensemble de compteurs personnalisé en cliquant avec le bouton droit sur un ensemble de compteurs existant, en choisissant Copier et en le collant ensuite dans le nœud des ensembles de compteurs. Il est possible de supprimer les compteurs supplémentaires copiés, mais inutiles. Vous pouvez changer le nom du nouvel ensemble de compteurs en utilisant la fenêtre **Propriétés**.

## <a name="see-also"></a>Voir aussi

- [Spécifier les ensembles de compteurs et les règles de seuil des ordinateurs dans un test de charge](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [Configurer les paramètres d’exécution de test de charge](../test/configure-load-test-run-settings.md)
