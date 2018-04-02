---
title: Enregistrement des journaux de test de charge dans Visual Studio | Microsoft Docs
ms.date: 10/19/2016
ms.topic: article
helpviewer_keywords:
- load tests, scenarios
- load tests, logging
ms.assetid: 9ac88d8a-4777-462c-aa0e-244dadb2cfd1
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-test
ms.openlocfilehash: 0178be52299183a072532d62f323a4612a93f531
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2018
---
# <a name="how-to-specify-how-frequently-test-logs-are-saved-using-the-load-test-editor"></a>Comment : spécifier la fréquence d'enregistrement des journaux des tests à l'aide de l'éditeur de test de charge

Après avoir créé votre test de charge avec l’**Assistant Nouveau test de charge**, vous pouvez utiliser l’**éditeur de test de charge** pour changer les propriétés des tests de charge en fonction de vos besoins et objectifs. Pour plus d’informations, consultez [Procédure pas à pas : Créer et exécuter un test de charge](../test/walkthrough-create-and-run-a-load-test.md).

> [!NOTE]
> Pour obtenir une liste complète des propriétés des paramètres d’exécution et leurs descriptions, consultez [Propriétés des paramètres d’exécution pour le test de charge](../test/load-test-run-settings-properties.md).

Vous pouvez spécifier la fréquence d’enregistrement du journal des tests dans un test de charge en utilisant l’éditeur de test de charge pour changer la propriété **Enregistrer la fréquence d’entrée au journal pour les tests terminés** dans la fenêtre Propriétés.

## <a name="to-specify-the-frequency-for-saving-the-test-log-in-a-load-test"></a>Pour spécifier la fréquence d'enregistrement du journal des tests dans un test de charge

1.  Ouvrez un test de charge.

     L'Éditeur de test de charge s'affiche. Il affiche l’arborescence du test de charge.

2.  Dans le dossier **Paramètres d’exécution** des arborescences du test de charge, choisissez le nœud de paramètres d’exécution pour lequel vous souhaitez spécifier la fréquence d’enregistrement du journal des tests.

3.  Dans le menu **Affichage**, sélectionnez **Fenêtre Propriétés**.

     Les catégories et les propriétés du scénario sont affichées dans la fenêtre Propriétés.

4.  Dans la zone de texte de la propriété **Enregistrer la fréquence d’entrée au journal pour les tests terminés**, tapez un nombre pour indiquer la fréquence d’écriture du journal des tests. Cette valeur indique qu'un test sur le nombre de tests entré doit être enregistré dans le journal des tests. Par exemple, si vous entrez la valeur dix, cela indique que le dixième test, le vingtième test, le trentième test, et ainsi de suite, doivent être écrits dans le journal des tests.

    > [!NOTE]
    > L’utilisation de la valeur 0 pour la propriété **Enregistrer la fréquence d’entrée au journal pour les tests terminés** indique qu’aucun journal des tests n’est enregistré.

5.  Après avoir changé la propriété, choisissez **Enregistrer** dans le menu **Fichier**.

     Les données enregistrées dans le journal peuvent être affichées à l'aide de la vue Tables de l'analyseur de test de charge. Pour plus d’informations, consultez [Analyser les résultats et les erreurs des tests de charge dans la vue Tables](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

## <a name="see-also"></a>Voir aussi

- [Modification des scénarios de test de charge](../test/edit-load-test-scenarios.md)
- [Procédure pas à pas : Créer et exécuter un test de charge](../test/walkthrough-create-and-run-a-load-test.md)
- [Modification des scénarios de test de charge](../test/edit-load-test-scenarios.md)
- [Guide pratique pour spécifier si les échecs de test sont enregistrés dans les journaux des tests](../test/how-to-specify-if-test-failures-are-saved-to-test-logs.md)
- [Guide pratique pour configurer la collecte des détails complets afin d’activer le graphique d’activités des utilisateurs virtuels](../test/how-to-configure-load-tests-to-collect-full-details.md)