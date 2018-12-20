---
title: Appliquer une distribution au rythme pour les tests de charges
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, test mix model
ms.assetid: ae8b35f9-d465-4d72-8d7d-7b56ae6ffd22
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 19634186e13574c322c2e9bcc636dda3a823b158
ms.sourcegitcommit: ae46be4a2b2b63da7e7049e9ed67cd80897c8102
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2018
ms.locfileid: "52896188"
---
# <a name="how-to-apply-distribution-to-pacing-delay-for-a-user-pace-test-mix-model"></a>Guide pratique afin d’appliquer une distribution au rythme pour un modèle de combinaison de tests dépendant du rythme de l’utilisateur

Après avoir créé votre test de charge avec l’**Assistant Nouveau test de charge**, vous pouvez utiliser l’éditeur de test de charge pour changer les propriétés des scénarios afin de répondre à vos besoins et vos objectifs de test.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

La propriété **Appliquer une distribution au rythme** est définie dans la fenêtre **Propriétés**. Les propriétés du scénario de test de charge sont modifiées à l'aide de l'Éditeur de test de charge.

> [!NOTE]
> La propriété **Appliquer une distribution au rythme** s’applique uniquement si la *combinaison de tests de charge* est configurée en fonction du rythme de l’utilisateur. Pour plus d’informations, consultez [Modifier des modèles de combinaison de texte pour spécifier la probabilité d’exécution d’un test par un utilisateur virtuel](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md).

La valeur de la propriété **Appliquer une distribution au rythme** peut avoir la valeur True ou False :

- **True** : le scénario applique des délais de distribution statistiques normaux spécifiés par la valeur de la colonne **Tests par utilisateur et par heure** dans la boîte de dialogue **Modifier la combinaison de tests**. Pour plus d’informations, consultez [Modifier des modèles de combinaison de texte pour spécifier la probabilité d’exécution d’un test par un utilisateur virtuel](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md).

     Supposons que vous ayez comme valeur **Tests par utilisateur et par heure** dans la boîte de dialogue **Modifier la combinaison de tests** du jeu de tests deux utilisateurs par heure. Si la propriété **Appliquer une distribution au rythme** a la valeur **True**, une distribution statistique normale s’applique au délai d’attente entre les tests. Les tests exécuteront toujours deux tests par heure, mais l'intervalle entre eux ne sera pas nécessairement de 30 minutes. Le premier test peut être exécuté après quatre minutes et le deuxième test après 45 minutes.

- **False** : Les tests s’exécutent à un rythme que vous avez spécifié avec la valeur de la colonne **Tests par utilisateur et par heure** dans la boîte de dialogue **Modifier la combinaison de tests**. Pour plus d’informations, consultez [Modifier des modèles de combinaison de texte pour spécifier la probabilité d’exécution d’un test par un utilisateur virtuel](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md).

     Supposons que vous ayez comme valeur **Tests par utilisateur et par heure** dans la boîte de dialogue **Modifier la combinaison de tests** du jeu de tests deux utilisateurs par heure. Si la propriété **Appliquer une distribution au rythme** a la valeur **False**, vous n’avez aucune marge de manœuvre pour exécuter vos tests exécutés. Le test s'exécutera toutes les 30 minutes. Cela permet de s'assurer que vous exécutez deux tests par heure.

## <a name="to-specify-the-apply-distribution-to-pacing-delay-property-setting-for-a-scenario"></a>Pour spécifier le paramètre de la propriété Appliquer une distribution au rythme pour un scénario

1. Ouvrez un test de charge.

   L’**éditeur de test de charge** s’affiche. L’arborescence du test de charge s’affiche.

2. Dans le dossier **Scénarios** de l’arborescence du test de charge, sélectionnez le nœud de scénario auquel vous souhaitez appliquer une distribution au rythme.

3. Dans le menu **Affichage**, sélectionnez **Fenêtre Propriétés**.

   Les catégories et les propriétés du scénario s’affichent dans la fenêtre **Propriétés**.

4. Dans la valeur de la propriété **Appliquer une distribution au rythme**, sélectionnez **True** ou **False**.

5. Sélectionnez **Fichier** > **Enregistrer**. Vous pouvez maintenant exécuter votre test de charge avec la nouvelle valeur de la propriété **Appliquer une distribution au rythme**.

## <a name="see-also"></a>Voir aussi

- [Modifier les scénarios de test de charge](../test/edit-load-test-scenarios.md)
- [Procédure pas à pas : Créer et exécuter un test de charge](../test/walkthrough-create-and-run-a-load-test.md)
- [Contrôleurs de test et agents de test](configure-test-agents-and-controllers-for-load-tests.md)
- [Propriétés des scénarios de test de charge](../test/load-test-scenario-properties.md)