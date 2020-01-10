---
title: Créer et exécuter un test de charge
ms.date: 10/01/2016
ms.topic: conceptual
helpviewer_keywords:
- unit tests, in load tests
- unit tests, load test walkthrough
- load tests, walkthrough
ms.assetid: bbf075a5-96d5-48ed-a03c-330f0fc04748
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1c2ade11d4bffc3c9fdf812cb38d21cd742c9845
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75590850"
---
# <a name="walkthrough-create-and-run-a-load-test-that-contains-unit-tests"></a>Procédure pas à pas : Créer et exécuter un test de charge qui contient des tests unitaires

Dans cette procédure pas à pas, vous allez créer un test de charge qui contient des tests unitaires.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Cette procédure pas à pas vous guide dans la création et l'exécution d'un test de charge à l'aide de Visual Studio Enterprise. Un test de charge est un conteneur de tests de performances web et de tests unitaires. Vous créez des tests de charge avec **l’Assistant Nouveau test de charge**.

Un test de charge expose également de nombreuses propriétés à l'exécution qui peuvent être modifiées pour générer la simulation de charge souhaitée. Dans cette procédure pas à pas, vous utilisez **l’Assistant Nouveau test de charge** pour ajouter des tests unitaires à un test de charge.

Dans cette procédure pas à pas, vous effectuerez les tâches suivantes :

- Créez un test de charge qui utilise des tests unitaires.

- Modification de certains des paramètres de test de charge

- Exécution d'un test de charge

- Effectuez les étapes dans [Procédure pas à pas : création et exécution de tests unitaires pour le code managé](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md) afin de créer une bibliothèque de classes C# simple qui contient un projet de test de performances web et de charge avec quelques tests unitaires.

## <a name="create-a-load-test-containing-unit-tests-using-the-new-load-test-wizard"></a>Créer un test de charge contenant des tests unitaires à l’aide de l’Assistant Nouveau test de charge

### <a name="to-start-the-new-load-test-wizard"></a>Pour démarrer l'Assistant Nouveau test de charge

1. Ouvrez la solution Bank que vous avez créée dans [Procédure pas à pas : création et exécution de tests unitaires pour le code managé](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md).

2. Dans **l’Explorateur de solutions**, ouvrez le menu contextuel du nœud de solution Bank, sélectionnez **Ajouter**, puis **Nouveau projet**.

     La boîte de dialogue **Ajouter un nouveau projet** s’affiche.

3. Dans la boîte de dialogue **Ajouter un nouveau projet**, développez **Visual C#** , puis sélectionnez **Test**. Dans la liste de modèles, sélectionnez **Projet de test de performance web et de charge**, puis dans le champ **Nom**, tapez `BankLoadTest`. Cliquez sur **OK**.

     Le projet de test de performance Web et de charge BankLoadTest est ajouté à la solution.

4. Ouvrez le menu contextuel du projet de test de performances web et de charge BankLoadTest, puis choisissez **Ajouter** et **Test de charge**.

5. **L’Assistant Nouveau test de charge** démarre.

6. La page **Bienvenue** de **l’Assistant Nouveau test de charge** est la première page.

7. Sélectionnez **Suivant**.

### <a name="to-edit-settings-for-load-test-scenario"></a>Pour modifier les paramètres du scénario de test de charge

1. Dans la zone de texte **Entrer un nom pour le scénario de test de charge**, tapez **ExempleScénario**.

     Un *scénario* est un mécanisme de regroupement. Il se compose d'un ensemble de tests et des propriétés nécessaires pour exécuter ces tests sous charge.

2. Définissez **Profil de temps de réflexion** avec la valeur `Use normal distribution centered on recorded think times`. Les temps de réflexion représentent la durée pendant laquelle un utilisateur consulte une page Web avant de passer à la page suivante.

1. Choisissez **Suivant** quand vous avez terminé.

### <a name="to-edit-load-pattern-setting-for-test-scenario"></a>Pour modifier le paramètre de modèle de charge du scénario de test

1. Choisissez **Charge dans l’étape**.

    > [!NOTE]
    > Vous pouvez choisir entre deux types de modèles de charge : constante et par étape. Chaque type a une fonction propre dans le test de charge, mais pour les besoins de cette procédure pas à pas, choisissez **Charge dans l’étape**.

2. Définissez **Nombre d’utilisateurs au début** avec la valeur 10 utilisateurs.

3. Définissez **Durée de l’étape** avec la valeur 10 secondes.

4. Définissez **Nombre d’utilisateurs dans l’étape** avec la valeur 10 utilisateurs/étape.

5. Définissez **Nombre maximal d’utilisateurs** avec la valeur 100 utilisateurs.

6. Sélectionnez **Suivant**.

### <a name="to-select-test-mix-model-for-the-scenario"></a>Pour sélectionner le modèle de combinaison de tests du scénario

1. Sous **Comment la combinaison de tests doit être modélisée**, sélectionnez **Sur la base du nombre total de tests**.

2. Sélectionnez **Suivant**.

### <a name="to-add-unit-tests-to-the-scenario"></a>Pour ajouter des tests unitaires au scénario

1. L’étape suivante consiste à **Ajouter des tests à un scénario de test de charge et modifier la combinaison de tests**.

2. Choisissez **Ajouter** pour sélectionner les tests.

3. Choisissez le test unitaire **CreditTest** répertorié dans le volet **Tests disponibles**, qui répertorie tous les tests de performances web et les tests unitaires du projet de test de performances web et de charge.

4. Choisissez la flèche pour ajouter le test unitaire **CreditTest** au volet **Tests sélectionnés**.

5. Répétez les étapes 3 et 4 pour les tests unitaires **DebitTest** et **FreezeAccountTest**.

6. Quand vous avez terminé d’ajouter les trois tests unitaires, choisissez **OK**.

     La combinaison de tests s'affiche à l'écran.

7. Déplacez légèrement vers la droite le curseur situé sous **Distribution** pour le test unitaire **CreditTest** afin d’ajuster la distribution du test. Notez que les autres curseurs se déplacent automatiquement vers la gauche afin que la distribution reste à 100 %.

8. Sélectionnez **Suivant**.

### <a name="to-select-network-mix-for-test-scenario"></a>Pour sélectionner la combinaison de réseaux du scénario de test

1. Sélectionnez le type de connexion de réseau local à ajouter à la combinaison de bande passante réseau.

     Vous pouvez ajouter d'autres types de réseaux. Utilisez les curseurs pour ajuster la distribution et le poids des tests.

2. Sélectionnez **Suivant**.

### <a name="to-specify-computers-to-monitor-with-counter-sets-during-load-test-run"></a>Pour spécifier les ordinateurs à surveiller avec des ensembles de compteurs durant la série de tests de charge

1. Sélectionnez **Suivant**.

     Pour plus d’informations sur les ensembles de compteurs, consultez [Spécifier des ensembles de compteurs et des règles de seuil pour les ordinateurs dans un test de charge](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md).

### <a name="to-edit-run-setting-for-load-test"></a>Pour modifier le paramètre d'exécution du test de charge

1. Sélectionnez **Durée du test de charge**, puis définissez la **Durée d’exécution** avec la valeur 2 minutes afin d’effectuer un *test de détection de fumée*.

     Lorsque vous générez vos tests de charge, il est conseillé de vérifier que tout est configuré correctement et fonctionne comme prévu en exécutant un test de charge court et léger. Ce processus est appelé *test de détection de fumée*.

2. Choisissez **Terminer**. Votre test de charge s’ouvre dans **l’éditeur de test de charge**.

## <a name="run-the-load-test"></a>Exécuter le test de charge
 Après avoir créé le test de charge, exécutez-le pour voir de quelle façon votre application bancaire répond à la simulation de charge. Pendant l’exécution d’un test de charge, la fenêtre **Analyseur de test de charge** s’affiche.

### <a name="to-run-the-load-test"></a>Pour exécuter le test de charge

1. Avec un test de charge ouvert dans **l’éditeur de test de charge**, sélectionnez le bouton vert **Exécuter le test** dans la barre d’outils. L'exécution de votre test de charge démarre.

2. Si votre simulation de test dépasse des seuils, des icônes apparaissent dans les nœuds de contrôle d'arborescence pour indiquer une violation de seuil. Les erreurs sont marquées d'un cercle rouge, les avertissements sont marqués d'un triangle jaune. Vous pouvez rechercher un compteur qui a dépassé le seuil et le tracer en faisant glisser l'icône sur le graphique. Vous pouvez effectuer cette opération pendant l'exécution du test.

## <a name="see-also"></a>Voir aussi

- [Modification de la combinaison de tests pour spécifier les tests à inclure dans un scénario de test de charge](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md)
- [Spécifier des types de réseau virtuel](../test/specify-virtual-network-types-in-a-load-test-scenario.md)
- [Modifier les scénarios de test de charge](../test/edit-load-test-scenarios.md)
- [Modifier les modèles de charge en modèle d’activités des utilisateurs virtuels](../test/edit-load-patterns-to-model-virtual-user-activities.md)
- [Modifier les modèles de combinaison de tests pour spécifier la probabilité d’exécution d’un test par un utilisateur virtuel](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md)
