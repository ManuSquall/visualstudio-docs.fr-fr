---
title: Guide pratique pour spécifier le taux d’échantillonnage d’un paramètre d’exécution des tests de charge dans Visual Studio | Microsoft Docs
ms.date: 10/19/2016
ms.topic: article
helpviewer_keywords:
- load tests, run settings
ms.assetid: 51cbe7d6-5dfd-4842-bca3-f7f8a665dc84
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-test
ms.openlocfilehash: 929946efffe619c81d944e56cf05190b6790f9d9
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2018
---
# <a name="how-to-specify-the-sample-rate-for-a-load-test-run-setting"></a>Comment : spécifier un taux d'échantillonnage d'un paramètre d'exécution des tests de charge

Après avoir créé votre test de charge avec l’**Assistant Nouveau test de charge**, vous pouvez utiliser l’**éditeur de test de charge** pour changer les propriétés en fonction de vos besoins et objectifs.

À l’aide de l’**éditeur de test de charge**, vous pouvez modifier la valeur de la propriété **Taux d’échantillonnage** d’un paramètre d’exécution dans la fenêtre **Propriétés**. Pour obtenir une liste complète des propriétés des paramètres d’exécution et leurs descriptions, consultez [Propriétés des paramètres d’exécution pour le test de charge](../test/load-test-run-settings-properties.md).

Choisissez une valeur appropriée pour la propriété **Taux d’échantillonnage** du paramètre d’exécution d’un test de charge selon la durée de votre test de charge. Un taux d'échantillonnage moins élevé, tel que la valeur par défaut de cinq secondes, nécessite une capacité d'espace supplémentaire dans la base de données des résultats du test de charge. Pour les tests de charge de plus longue durée, l'augmentation du taux d'échantillonnage permet de réduire le volume de données collectées. Pour plus d’informations, consultez [Guide pratique pour spécifier le taux d’échantillonnage d’un paramètre d’exécution des tests de charge](../test/how-to-specify-the-sample-rate-for-a-load-test.md).

Voici quelques instructions sur les taux d'échantillonnage :

|Durée du test de charge|Taux d'échantillonnage recommandé|
|------------------------|-----------------------------|
|\< 1 heure|5 secondes|
|1 à 8 heures|15 secondes|
|8 à 24 heures|30 secondes|
|> 24 heures|60 secondes|

## <a name="to-specify-performance-counter-sampling-rate-in-a-run-setting"></a>Pour spécifier le taux d'échantillonnage du compteur de performance dans un paramètre d'exécution

1.  Ouvrez un test de charge.

     L’**éditeur de test de charge** s’affiche. L’arborescence du test de charge s’affiche.

2.  Dans le dossier **Paramètres d’exécution** de l’arborescence du test de charge, choisissez le paramètre d’exécution pour lequel vous souhaitez spécifier le taux d’échantillonnage.

3.  Dans le menu **Affichage**, sélectionnez **Fenêtre Propriétés**.

     Les catégories et propriétés des paramètres d'exécution du test de charge sont affichées dans la fenêtre Propriétés.

4.  Dans la propriété **Taux d’échantillonnage**, entrez une valeur de temps qui indique la fréquence à laquelle le test de charge doit collecter les données du compteur de performances.

5.  Après avoir changé la propriété, choisissez **Enregistrer** dans le menu **Fichier**. Vous pouvez exécuter ensuite votre test de charge à l’aide de la nouvelle valeur associée à **Taux d’échantillonnage**.

## <a name="see-also"></a>Voir aussi

- [Configuration des paramètres d’exécution des tests de charge](../test/configure-load-test-run-settings.md)
- [Propriétés des scénarios de test de charge](../test/load-test-scenario-properties.md)