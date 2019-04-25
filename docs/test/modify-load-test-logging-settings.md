---
title: Paramètres de journalisation du test de charge
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, logging, modifying
ms.assetid: 9649226a-857d-41ef-8ec7-047b6e498033
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 9751ce3b08a0ac963cccdf091ccb99001c6f2c9f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62785771"
---
# <a name="modify-load-test-logging-settings"></a>Modifier les paramètres de journalisation du test de charge

Le résultat du test de charge pour le test de charge terminé contient des exemples de compteur de performance et des informations sur les erreurs qui ont été collectées à intervalles réguliers dans un journal sur les ordinateurs en cours de test. Un grand nombre d'exemples de compteurs de performance peuvent être collectés au cours d'une série de tests de charge. La quantité de données de performance collectées dépend de la durée de la série de tests, de l'intervalle d'échantillonnage, du nombre d'ordinateurs sous test et du nombre de compteurs collectés. Pour un test de charge volumineux, le volume de données des performances collectées peut atteindre facilement plusieurs gigaoctets. Par conséquent, vous pouvez envisager de modifier la fréquence d'enregistrement des données dans le journal. Consultez [Contrôleurs de test et agents de test](configure-test-agents-and-controllers-for-load-tests.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Le *contrôleur de test* met en attente toutes les données d’échantillons de test de charge collectées dans un journal de base de données pendant l’exécution du test. Des données supplémentaires, telles que les informations relatives à la minuterie et aux erreurs, sont chargées dans la base de données à l'issue de l'exécution du test.

|Tâche|Rubriques associées|
|-|-----------------------|
|**Enregistrer des journaux en cas d’échec d’un test de charge :** vous pouvez spécifier si vous souhaitez enregistrer le journal des tests chaque fois qu’un test de charge échoue.|-   [Guide pratique pour spécifier si les échecs de test doivent être enregistrés dans les journaux des tests](../test/how-to-specify-if-test-failures-are-saved-to-test-logs.md)|
|**Définir la taille maximale du fichier journal :** vous pouvez modifier le fichier config XML associé au service de contrôleur de test pour spécifier la taille de fichier maximale à utiliser pour le fichier journal.|Modifiez `<add key="LogSizeLimitInMegs" value="20"/>` dans le fichier de configuration XML *QTCcontroller.exe.config*.|

## <a name="see-also"></a>Voir aussi

- [Configurer les paramètres d’exécution des tests de charge](../test/configure-load-test-run-settings.md)