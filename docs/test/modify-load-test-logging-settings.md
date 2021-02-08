---
title: Paramètres de journalisation du test de charge
description: Découvrez comment modifier les paramètres de journalisation des tests de charge pour contrôler la quantité de données de performances collectées, ce qui peut entraîner des fichiers de résultats très volumineux.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, logging, modifying
ms.assetid: 9649226a-857d-41ef-8ec7-047b6e498033
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: db84e5be44d70934331d9e7d9c47e78bc669bedb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99838293"
---
# <a name="modify-load-test-logging-settings"></a>Modifier les paramètres de journalisation du test de charge

Le résultat du test de charge pour le test de charge terminé contient des exemples de compteur de performance et des informations sur les erreurs qui ont été collectées à intervalles réguliers dans un journal sur les ordinateurs en cours de test. Un grand nombre d'exemples de compteurs de performance peuvent être collectés au cours d'une série de tests de charge. La quantité de données de performance collectées dépend de la durée de la série de tests, de l'intervalle d'échantillonnage, du nombre d'ordinateurs sous test et du nombre de compteurs collectés. Pour un test de charge volumineux, le volume de données des performances collectées peut atteindre facilement plusieurs gigaoctets. Par conséquent, vous pouvez envisager de modifier la fréquence d'enregistrement des données dans le journal. Consultez [Contrôleurs de test et agents de test](configure-test-agents-and-controllers-for-load-tests.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Le *contrôleur de test* met en attente toutes les données d’échantillons de test de charge collectées dans un journal de base de données pendant l’exécution du test. Des données supplémentaires, telles que les informations relatives à la minuterie et aux erreurs, sont chargées dans la base de données à l'issue de l'exécution du test.

|Tâche|Rubriques associées|
|-|-----------------------|
|**Enregistrer des journaux si un test de charge échoue :** Vous pouvez également spécifier si vous souhaitez enregistrer le journal des tests chaque fois qu’un test de charge échoue.|-   [Guide pratique pour spécifier si les échecs de test doivent être enregistrés dans les journaux de tests](../test/how-to-specify-if-test-failures-are-saved-to-test-logs.md)|
|**Définir la taille de fichier maximum du fichier journal :** Vous pouvez modifier le fichier de configuration XML associé au service de contrôleur de test pour spécifier la taille de fichier maximum à utiliser pour le fichier journal.|Modifiez `<add key="LogSizeLimitInMegs" value="20"/>` dans le fichier de configuration XML *QTCcontroller.exe.config*.|

## <a name="see-also"></a>Voir aussi

- [Configurer les paramètres d’exécution des tests de charge](../test/configure-load-test-run-settings.md)
