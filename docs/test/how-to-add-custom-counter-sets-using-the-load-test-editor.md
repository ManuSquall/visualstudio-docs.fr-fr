---
title: Ajouter des ensembles de compteurs personnalisés pour un test de charge dans Visual Studio | Microsoft Docs
ms.date: 10/19/2016
ms.topic: article
helpviewer_keywords:
- counters, counter sets
- counter sets
- load tests, counter sets
ms.assetid: 499aca80-1069-408d-ac68-326da6a50645
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-test
ms.openlocfilehash: 8f691c0eac38dae9e9f419335eb1d3ae87c693df
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2018
---
# <a name="how-to-add-custom-counter-sets-using-the-load-test-editor"></a>Comment : ajouter des ensembles de compteurs personnalisés à l'aide de l'éditeur de test de charge

Quand vous créez un test de charge avec l’**Assistant Nouveau test de charge**, vous ajoutez un ensemble initial de compteurs. Ceux-ci vous offrent un groupe d'ensembles de compteurs prédéfinis pour votre test de charge.

> [!NOTE]
> Si vos tests de charge sont répartis entre des ordinateurs distants, les compteurs de contrôleur et d'agent sont automatiquement mappés au contrôleur et aux ensembles de compteurs de l'agent. Pour plus d’informations sur l’utilisation de machines distantes dans votre test de charge, consultez [Contrôleurs de test et agents de test](configure-test-agents-and-controllers-for-load-tests.md).

Vous gérez vos compteurs dans l’**éditeur de test de charge**. Les ensembles de compteurs qui sont déjà ajoutés au test sont visibles dans le nœud **Ensembles de compteurs** du test de charge. Après avoir créé un test de charge, vous pouvez lui ajouter de nouveaux ensembles de compteurs personnalisés.

![Ensemble de compteurs personnalisés](../test/media/loadtestcustomcounter.png "LoadTestCustomCounter")

## <a name="to-add-a-custom-counter-set-to-a-load-test"></a>Pour ajouter un ensemble de compteurs personnalisé à un test de charge

1.  Ouvrez un test de charge.

2.  Développez le nœud **Ensembles de compteurs**. Tous les ensembles de compteurs qui ont été ajoutés au test de charge sont visibles.

3.  Cliquez avec le bouton droit sur le nœud **Ensembles de compteurs**, puis sélectionnez **Ajouter un ensemble de compteurs personnalisés**.

    > [!NOTE]
    > L’ensemble de compteurs se voit attribuer un nom par défaut, par exemple **Personnalisé1**. Vous pouvez changer le nom dans la fenêtre **Propriétés**. Appuyez sur F4 pour afficher la fenêtre **Propriétés**.

4.  Pour ajouter des compteurs à votre ensemble de compteurs personnalisés, cliquez avec le bouton droit sur le nouvel ensemble de compteurs, puis choisissez **Ajouter des compteurs**. Pour plus d’informations sur l’ajout de compteurs, consultez [Guide pratique pour ajouter des compteurs à des ensembles de compteurs](../test/how-to-add-counters-to-counter-sets-using-the-load-test-editor.md).

    > [!NOTE]
    > Il est également possible d'ajouter un ensemble de compteurs personnalisé en cliquant avec le bouton droit sur un ensemble de compteurs existant, en choisissant Copier et en le collant ensuite dans le nœud des ensembles de compteurs. Il est possible de supprimer les compteurs supplémentaires copiés, mais inutiles. Vous pouvez changer le nom du nouvel ensemble de compteurs en utilisant la fenêtre **Propriétés**.

## <a name="see-also"></a>Voir aussi

- [Spécification des ensembles de compteurs et des règles de seuil pour les ordinateurs dans un test de charge](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [Configuration des paramètres d’exécution des tests de charge](../test/configure-load-test-run-settings.md)