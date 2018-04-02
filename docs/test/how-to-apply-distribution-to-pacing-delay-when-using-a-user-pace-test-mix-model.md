---
title: Appliquer une distribution au rythme pour les tests de charges dans Visual Studio | Microsoft Docs
ms.date: 10/19/2016
ms.topic: article
helpviewer_keywords:
- load tests, test mix model
ms.assetid: ae8b35f9-d465-4d72-8d7d-7b56ae6ffd22
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-test
ms.openlocfilehash: 047a8fd8dea60ca86c39922f8cd0aed6e65ec6d3
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2018
---
# <a name="how-to-apply-distribution-to-pacing-delay-when-using-a-user-pace-test-mix-model"></a>Comment : appliquer la distribution au retard rythmé lorsque vous utilisez un modèle de combinaison de tests basée sur le rythme de l'utilisateur

Après avoir créé votre test de charge avec l’Assistant Nouveau test de charge, vous pouvez utiliser l’éditeur de test de charge pour changer les propriétés des scénarios afin de répondre à vos besoins et vos objectifs de test.

La propriété **Appliquer une distribution au rythme** est définie dans la fenêtre Propriétés. Les propriétés du scénario de test de charge sont modifiées à l'aide de l'Éditeur de test de charge.

> [!NOTE]
> La propriété **Appliquer une distribution au rythme** s’applique uniquement si la *combinaison de tests de charge* est configurée en fonction du rythme de l’utilisateur. Pour plus d’informations, consultez [Modification des modèles de combinaison de texte pour spécifier la probabilité d’exécution d’un test par un utilisateur virtuel](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md).

La valeur de la propriété **Appliquer une distribution au rythme** peut avoir la valeur True ou False :

-   **True** : Le scénario applique des délais de distribution statistiques normaux spécifiés par la valeur de la colonne **Tests par utilisateur et par heure** dans la boîte de dialogue Modifier la combinaison de tests. Pour plus d’informations, consultez [Modification des modèles de combinaison de texte pour spécifier la probabilité d’exécution d’un test par un utilisateur virtuel](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md).

     Supposons que vous ayez comme valeur **Tests par utilisateur et par heure** dans la boîte de dialogue Modifier la combinaison de tests du jeu de tests deux utilisateurs par heure. Si la propriété **Appliquer une distribution au rythme** a la valeur **True**, une distribution statistique normale s’applique au délai d’attente entre les tests. Les tests exécuteront toujours deux tests par heure, mais l'intervalle entre eux ne sera pas nécessairement de 30 minutes. Le premier test peut être exécuté après quatre minutes et le deuxième test après 45 minutes.

-   **False** : Les tests seront exécutés à un rythme que vous avez spécifié avec la valeur de la colonne **Tests par utilisateur et par heure** dans la boîte de dialogue Modifier la combinaison de tests. Pour plus d’informations, consultez [Modification des modèles de combinaison de texte pour spécifier la probabilité d’exécution d’un test par un utilisateur virtuel](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md).

     Supposons que vous ayez comme valeur **Tests par utilisateur et par heure** dans la boîte de dialogue Modifier la combinaison de tests du jeu de tests deux utilisateurs par heure. Si la propriété **Appliquer une distribution au rythme** a la valeur **False**, vous n’avez aucune marge de manœuvre pour exécuter vos tests exécutés. Le test s'exécutera toutes les 30 minutes. Cela permet de s'assurer que vous exécutez deux tests par heure.

## <a name="to-specify-the-apply-distribution-to-pacing-delay-property-setting-for-a-scenario"></a>Pour spécifier le paramètre de la propriété Appliquer une distribution au rythme pour un scénario

1.  Ouvrez un test de charge.

     **L’éditeur de test de charge** s’affiche. L’arborescence du test de charge s’affiche.

2.  Dans le dossier **Scénarios** de l’arborescence du test de charge, sélectionnez le nœud du scénario pour lequel vous voulez spécifier les agents à utiliser.

3.  Dans le menu **Affichage**, sélectionnez la fenêtre **Propriétés**.

     Les catégories et les propriétés du scénario s’affichent dans la fenêtre **Propriétés**.

4.  Dans la valeur de la propriété **Appliquer une distribution au rythme**, sélectionnez **True** ou **False**.

5.  Une fois que vous avez changé la propriété, choisissez **Enregistrer** dans le menu **Fichier**. Vous pouvez exécuter ensuite votre test de charge à l’aide de la nouvelle valeur de la propriété **Appliquer une distribution au rythme**.

## <a name="see-also"></a>Voir aussi

- [Modification des scénarios de test de charge](../test/edit-load-test-scenarios.md)
- [Procédure pas à pas : Créer et exécuter un test de charge](../test/walkthrough-create-and-run-a-load-test.md)
- [Contrôleurs de test et agents de test](configure-test-agents-and-controllers-for-load-tests.md)
- [Propriétés des scénarios de test de charge](../test/load-test-scenario-properties.md)