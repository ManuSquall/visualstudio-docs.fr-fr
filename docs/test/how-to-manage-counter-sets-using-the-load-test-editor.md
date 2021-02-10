---
title: Ensembles de compteurs de test de charge
description: Découvrez comment utiliser la éditeur de test de charge gérer pour gérer les ensembles de compteurs en choisissant les ordinateurs et en assignant des ensembles de compteurs à collecter à partir de chaque ordinateur.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
f1_keywords:
- vs.test.load.dialog.countersetmapping
helpviewer_keywords:
- counters, counter sets
- performance counters
- counter sets
- load tests, counter sets
ms.assetid: 64315c2f-a0b2-4378-be16-0774b99beef5
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: 684715ed8ac29a3c85d0ea46799a2e14fb9722bf
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99961441"
---
# <a name="how-to-manage-counter-sets-using-the-load-test-editor"></a>Guide pratique pour gérer des ensembles de compteurs à l’aide de l’éditeur de test de charge

Quand vous créez un test de charge avec **l’Assistant Nouveau test de charge**, vous ajoutez un ensemble initial de compteurs. Ceux-ci vous offrent un groupe d'ensembles de compteurs prédéfinis pour votre test de charge.

> [!NOTE]
> Si vos tests de charge sont répartis entre des ordinateurs distants, les compteurs de contrôleur et d'agent sont automatiquement mappés au contrôleur et aux ensembles de compteurs de l'agent. Pour plus d’informations sur l’utilisation de machines distantes dans votre test de charge, consultez [Contrôleurs de test et agents de test](configure-test-agents-and-controllers-for-load-tests.md).

La gestion d'ensembles de compteurs implique le choix du jeu d'ordinateurs à partir duquel vous souhaitez collecter des données de performance et l'assignation d'un jeu d'ensembles de compteurs à collecter à partir de chaque ordinateur individuel. Vous gérez vos compteurs dans **l’éditeur de test de charge**.

![Gestion des ensembles de compteurs](../test/media/loadtestmanagecountersets.png)

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-manage-counter-sets"></a>Pour gérer des ensembles de compteurs

1. Ouvrez un test de charge.

2. Choisissez le bouton **Gérer les ensembles de compteurs**.

     – ou –

     Cliquez avec le bouton droit sur le dossier **Ensembles de compteurs** dans l’arborescence du test de charge, puis choisissez **Gérer les ensembles de compteurs**.

     La boîte de dialogue **Gérer les ensembles de compteurs** s’affiche.

3. (Facultatif) Dans la zone de liste **Les ordinateurs et les ensembles de compteurs sélectionnés seront ajoutés aux paramètres d’exécution suivants**, sélectionnez un paramètre d’exécution différent.

    > [!NOTE]
    > Cela ne s'applique que si votre test de charge comporte plusieurs paramètres d'exécution.

4. (Facultatif) Choisissez **Ajout ordinateur** pour ajouter un nouvel ordinateur à monitorer. Vous êtes invité à entrer un nom. Tapez le nom d'un ordinateur et des nœuds s'affichent sous la nouvelle entrée. Par exemple **ASP.NET**, **IIS**, **SQL** et d’autres. Activez les cases à cocher en regard des nœuds que vous souhaitez sélectionner. Les nouveaux compteurs apparaissent dans le volet **Aperçu des sélections**.

5. (Facultatif) Dans la zone de texte **Étiquettes d’ordinateur**, tapez une étiquette à associer à l’ordinateur. Par exemple, « TestMachine12 dans lab3 ».

     Les balises d'ordinateur permettent d'identifier un ordinateur avec un nom facile à reconnaître.

     Les balises s’affichent dans le nœud **Mappages des ensembles de compteurs** de l’arborescence dans l’éditeur de test de charge. Plus important, les balises s'affichent dans les rapports Excel, ce qui permet aux parties prenantes d'identifier le rôle de l'ordinateur dans le test de charge. Par exemple, « Server1 Web dans lab2 » ou « SQL Server2 dans le bureau de Phoenix ». Pour plus d’informations, voir [Créer des rapports sur les résultats des tests de charge à des fins de comparaison ou d’analyse des tendances](../test/compare-load-test-results.md).

6. Choisissez **OK**.

## <a name="see-also"></a>Voir aussi

- [Contrôleurs de test et agents de test](configure-test-agents-and-controllers-for-load-tests.md)
- [Spécifier les ensembles de compteurs et les règles de seuil des ordinateurs dans un test de charge](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [Configurer les paramètres d’exécution des tests de charge](../test/configure-load-test-run-settings.md)
