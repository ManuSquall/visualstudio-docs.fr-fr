---
title: Paramètres de journalisation du test de charge dans Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, logging, modifying
ms.assetid: 9649226a-857d-41ef-8ec7-047b6e498033
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: d24bb1b3af468f35ae333407fc96c42f4f9e669b
ms.sourcegitcommit: ae46be4a2b2b63da7e7049e9ed67cd80897c8102
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2018
ms.locfileid: "52894883"
---
# <a name="modify-load-test-logging-settings"></a>Modifier les paramètres de journalisation du test de charge

Le résultat du test de charge pour le test de charge terminé contient des exemples de compteur de performance et des informations sur les erreurs qui ont été collectées à intervalles réguliers dans un journal sur les ordinateurs en cours de test. Un grand nombre d'exemples de compteurs de performance peuvent être collectés au cours d'une série de tests de charge. La quantité de données de performance collectées dépend de la durée de la série de tests, de l'intervalle d'échantillonnage, du nombre d'ordinateurs sous test et du nombre de compteurs collectés. Pour un test de charge volumineux, le volume de données des performances collectées peut atteindre facilement plusieurs gigaoctets. Par conséquent, vous pouvez envisager de modifier la fréquence d'enregistrement des données dans le journal. Consultez [Contrôleurs de test et agents de test](configure-test-agents-and-controllers-for-load-tests.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Le *contrôleur de test* met en attente toutes les données d’échantillons de test de charge collectées dans un journal de base de données pendant l’exécution du test. Des données supplémentaires, telles que les informations relatives à la minuterie et aux erreurs, sont chargées dans la base de données à l'issue de l'exécution du test.

|Tâche|Rubriques associées|
|-|-----------------------|
|**Enregistrer des journaux si un test de charge échoue :** Vous pouvez également spécifier si vous souhaitez enregistrer le journal des tests chaque fois qu’un test de charge échoue.|-   [Guide pratique pour spécifier si les échecs de test doivent être enregistrés dans les journaux de tests](../test/how-to-specify-if-test-failures-are-saved-to-test-logs.md)|
|**Définir la taille de fichier maximum du fichier journal :** Vous pouvez modifier le fichier de configuration XML associé au service de contrôleur de test pour spécifier la taille de fichier maximum à utiliser pour le fichier journal.|[Guide pratique pour spécifier la taille maximale du fichier journal](../test/how-to-specify-the-maximum-size-for-the-log-file.md)|

## <a name="see-also"></a>Voir aussi

- [Configurer les paramètres d’exécution des tests de charge](../test/configure-load-test-run-settings.md)