---
title: Modification des modèles de combinaison de tests dans Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, scenarios
- load tests, virtual users
ms.assetid: e3b7d952-9012-400a-8131-3444390a6066
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 591bdaa84d143dc3b639990530a68246dc00385a
ms.sourcegitcommit: a8e01952be5a539104e2c599e9b8945322118055
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32425333"
---
# <a name="edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test"></a>Modifier les modèles de combinaison de tests pour spécifier la probabilité d’exécution d’un test par un utilisateur virtuel

Le *modèle de combinaison de tests* spécifie la probabilité selon laquelle un utilisateur virtuel exécute un test donné dans un scénario de test de charge. Cela vous permet de simuler la charge de façon plus réaliste. Au lieu d'avoir un seul flux de travail dans vos applications, vous pouvez en avoir plusieurs, ce qui représente une meilleure approximation de la façon dont les utilisateurs finaux interagissent avec vos applications.

## <a name="test-mix-model-options"></a>Options du modèle de combinaison de tests

Vous pouvez spécifier l'une des options de modèle de combinaison de tests suivantes pour votre scénario de test de charge :

-   **Sur la base du nombre total de tests :** détermine les tests de performances web ou tests unitaires qui sont exécutés quand un utilisateur virtuel démarre une itération de test. À la fin du test de charge, le nombre de fois où un test particulier exécuté correspond à la distribution de test assignée. Utilisez ce modèle de combinaison de tests lorsque vous basez la combinaison de tests sur les pourcentages de transaction dans un journal IIS ou dans les données de production.

-   **Sur la base du nombre d’utilisateurs virtuels :** détermine le pourcentage des utilisateurs virtuels qui vont exécuter un test de performances web ou un test unitaire particulier. À tout point pendant le test de charge, le nombre d'utilisateurs qui exécutent un test particulier correspond d'aussi près que possible à la distribution assignée de la manière la plus fidèle possible. Utilisez ce modèle de combinaison de tests lorsque vous basez la combinaison de tests sur le pourcentage d'utilisateurs qui exécutent un test particulier.

-   **Sur la base du rythme de l’utilisateur :** au cours du test de charge, chaque test de performances web ou test unitaire est exécuté un nombre spécifique de fois, par utilisateur et par heure. Utilisez ce modèle de combinaison de tests lorsque vous souhaitez que les utilisateurs virtuels exécutent des tests à un certain rythme dans le test de charge.

-   **Sur la base de l’ordre de tests séquentiel :** chaque utilisateur virtuel exécute les tests de performances web ou les tests unitaires dans l’ordre dans lequel les tests sont définis dans le scénario. L'utilisateur virtuel continue à parcourir les tests dans cet ordre jusqu'à ce que le test de charge soit terminé.

## <a name="tasks"></a>Tâches

|Tâches|Rubriques associées|
|-----------|-----------------------|
|**Spécification de la combinaison de tests pour votre test de charge :** quand vous créez un test de charge, vous spécifiez les paramètres du test de charge dans l’Assistant Nouveau test de charge. Dans l'Assistant Nouveau test de charge, vous choisissez les tests Web et unitaires à ajouter au scénario initial. Après avoir ajouté des tests au scénario, vous spécifiez la combinaison de tests pour le scénario.<br /><br /> Vous utilisez les options de modélisation de charge pour prédire l'utilisation réelle attendue d'un site web ou d'une application dont vous testez la charge. Il est important de le faire parce qu'un test de charge qui n'est pas basé sur un modèle de charge précis peut générer des résultats trompeurs.|-   [Émulation de l’utilisation réelle attendue d’une application ou d’un site web](../test/emulate-real-world-usage-of-a-web-site-in-a-load-test-using-test-mix-models.md)|
|**Modifier le modèle de combinaison de tests :** vous pouvez changer un scénario de test de charge pour utiliser l’un des modèles de combinaison de tests à l’aide de l’éditeur de test de charge.||
|**Configurer le rythme d’un modèle de combinaison de tests basé sur le rythme de l’utilisateur :** si votre scénario de test de charge est configuré pour utiliser le modèle de combinaison de tests **Sur la base du rythme de l’utilisateur**, vous pouvez spécifier le mode de configuration du rythme de distribution.|-   [Guide pratique pour appliquer une distribution au rythme durant l’utilisation d’un modèle de combinaison de tests dépendant du rythme de l’utilisateur](../test/how-to-apply-distribution-to-pacing-delay-when-using-a-user-pace-test-mix-model.md)|

## <a name="change-the-test-mix-model-in-a-scenario"></a>Changer le modèle de combinaison de tests dans un scénario

Après avoir créé votre test de charge à l’aide de l’**Assistant Nouveau test de charge**, vous pouvez utiliser l’**éditeur de test de charge** pour changer les propriétés des scénarios en fonction de vos besoins et objectifs.

> [!NOTE]
> Pour obtenir la liste complète des propriétés des paramètres de charge et leurs descriptions, consultez [Propriétés du scénario de test de charge](../test/load-test-scenario-properties.md).

À l’aide de l’éditeur de test de charge, vous pouvez changer le modèle de combinaison de tests d’un scénario de test de charge en modifiant la propriété **Type de combinaison de tests** dans la fenêtre Propriétés.

### <a name="to-change-the-test-mix-model"></a>Pour modifier le modèle de combinaison de tests

1.  Ouvrez un test de charge.

     L'Éditeur de test de charge s'affiche. L’arborescence du test de charge s’affiche.

2.  Dans le dossier **Scénarios** de l’arborescence du test de charge, choisissez le nœud de scénario pour lequel vous souhaitez spécifier le nombre maximal d’itérations de tests.

3.  Dans le menu **Affichage**, sélectionnez **Fenêtre Propriétés**.

     Les catégories et les propriétés du scénario s'affichent.

4.  Dans la propriété **Type de combinaison de tests**, choisissez le bouton de sélection (**...**).

     La boîte de dialogue Modifier la combinaison de tests s'affiche.

5.  Choisissez la liste déroulante sous **Modèle de combinaison de tests**, puis sélectionnez le modèle de combinaison de tests à utiliser pour le scénario.

6.  (Facultatif) Modifiez la combinaison de tests à l’aide des boutons et des curseurs de distribution **Ajouter**, **Supprimer** et **Distribuer**. Pour plus d’informations, consultez [Modification de la combinaison de tests pour spécifier les tests à inclure dans un scénario de test de charge](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md).

7.  Spécifiez un test de performances de site web et un test unitaire pour démarrer ou terminer en utilisant les cases à cocher et en sélectionnant les tests souhaités (facultatif). Pour plus d’informations, consultez [Émulation de l’utilisation réelle attendue d’une application ou d’un site web](../test/emulate-real-world-usage-of-a-web-site-in-a-load-test-using-test-mix-models.md).

8.  Cliquez sur **OK**.

     La fenêtre **Propriétés** affiche le nouveau modèle de combinaison de tests pour la propriété **Type de combinaison de tests**.

9. Après avoir changé la propriété, choisissez **Enregistrer** dans le menu **Fichier**. Vous pouvez exécuter ensuite votre test de charge à l’aide de la nouvelle valeur associée à **Type de combinaison de tests**.

## <a name="see-also"></a>Voir aussi

- [Modifier les scénarios de test de charge](../test/edit-load-test-scenarios.md)
- [Propriétés des scénarios de test de charge](../test/load-test-scenario-properties.md)