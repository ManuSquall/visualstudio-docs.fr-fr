---
title: Enregistrer le journal des tests de charge pour les échecs de test dans Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, scenarios
- load tests, logging
ms.assetid: 08a7fe98-a7f7-4b8d-94a3-ec82b65a2aaf
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: d6196a940ff1aba0c072c2b81a96371a5ad700d1
ms.sourcegitcommit: 495bba1d8029646653f99ad20df2f80faad8d58b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/31/2018
ms.locfileid: "39381451"
---
# <a name="how-to-specify-if-test-failures-are-saved-to-test-logs-using-the-load-test-editor"></a>Guide pratique pour spécifier si les échecs de test sont enregistrés dans les journaux des tests à l’aide de l’éditeur de test de charge

Après avoir créé votre test de charge avec l’**Assistant Nouveau test de charge**, vous pouvez utiliser l’**éditeur de test de charge** pour changer les propriétés du test de charge en fonction de vos besoins et objectifs. Consultez [Procédure pas à pas : Créer et exécuter un test de charge](../test/walkthrough-create-and-run-a-load-test.md). Vous pouvez spécifier l’enregistrement du journal des tests en cas d’échec d’un test de charge. Pour ce faire, changez la propriété **Enregistrer le journal lors de l’échec d’un test**.

> [!NOTE]
> Pour obtenir la liste complète des propriétés des paramètres d’exécution et leurs descriptions, consultez [Propriétés des paramètres d’exécution pour le test de charge](../test/load-test-run-settings-properties.md).


## <a name="to-specify-if-the-test-log-is-saved-when-a-test-fails-in-a-scenario"></a>Pour spécifier si le journal des tests doit être enregistré en cas d'échec d'un test dans un scénario

1.  Ouvrez un test de charge.

     L’**éditeur de test de charge** s’affiche. L’arborescence du test de charge s’affiche.

2.  Dans le dossier **Paramètres d’exécution** des arborescences du test de charge, choisissez le nœud de paramètres d’exécution pour lequel vous souhaitez spécifier le nombre maximal d’itérations de tests.

3.  Dans le menu **Affichage**, sélectionnez **Fenêtre Propriétés**.

     Les catégories et propriétés des paramètres d’exécution sont affichées dans la fenêtre **Propriétés**.

4.  Dans la propriété **Enregistrer le journal lors de l’échec d’un test**, sélectionnez **True** ou **False** pour indiquer si vous souhaitez enregistrer le journal des tests en cas d’échec d’un test dans le scénario.

     Après avoir changé la propriété, choisissez **Enregistrer** dans le menu **Fichier**.

     Les données enregistrées dans le journal peuvent être affichées à l'aide de la vue Tables de l'analyseur de test de charge. Pour plus d’informations, consultez [Analyser les résultats et les erreurs des tests de charge dans la vue Tables](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

## <a name="see-also"></a>Voir aussi

- [Modifier les scénarios de test de charge](../test/edit-load-test-scenarios.md)
- [Procédure pas à pas : Créer et exécuter un test de charge](../test/walkthrough-create-and-run-a-load-test.md)
- [Guide pratique pour configurer la collecte des détails complets afin d’activer le graphique d’activités des utilisateurs virtuels](../test/how-to-configure-load-tests-to-collect-full-details.md)
- [Guide pratique pour spécifier la fréquence d’enregistrement des journaux des tests](../test/how-to-specify-how-frequently-test-logs-are-saved.md)