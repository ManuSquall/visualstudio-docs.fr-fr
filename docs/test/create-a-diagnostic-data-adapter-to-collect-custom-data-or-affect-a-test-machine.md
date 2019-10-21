---
title: Créer un adaptateur de données de diagnostic pour les tests
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Diagnostic Data Adapter [Visual Studio ALM]
- Diagnostic Data Adapter
ms.assetid: b0b53fae-7007-4ad9-a604-21685937622f
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1d518f911f076481e710176924036c6e3f37625e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665125"
---
# <a name="create-a-diagnostic-data-adapter-to-collect-custom-data-or-affect-a-test-machine"></a>Créer un adaptateur de données de diagnostic pour collecter des données personnalisées ou affecter une machine de test

Vous pouvez créer votre propre adaptateur de données de diagnostic de façon à collecter des données lors de l'exécution d'un test ; vous souhaitez peut-être aussi affecter l'ordinateur de test dans le cadre de votre test. Par exemple, vous pouvez collecter des fichiers journaux qui sont créés par l'application testée et les joindre à vos résultats de tests, ou bien exécuter vos tests lorsque l'espace disque restant sur votre ordinateur est limité. À l’aide des API fournies dans Visual Studio Enterprise, vous pouvez écrire du code pour exécuter des tâches à des points spécifiques de votre série de tests. Par exemple, vous pouvez effectuer des tâches lorsqu'une série de tests démarre, avant et après avoir exécuté chaque test individuel, et lorsque la série de tests se termine.

Vous pouvez fournir l'entrée par défaut de votre adaptateur de données de diagnostic personnalisé à l'aide d'un fichier de paramètres de configuration. Par exemple, vous avez la possibilité de fournir des informations indiquant l'emplacement du fichier que vous voulez collecter et joindre à vos résultats de tests, ou la quantité d'espace disque qui doit rester disponible sur le système. Ces données peuvent être configurées pour chaque paramètre de test que vous créez. Vous pouvez les afficher et les modifier à l’aide de l’éditeur par défaut fourni avec Microsoft Test Manager, ou bien vous pouvez créer votre propre contrôle utilisateur à utiliser en tant qu’éditeur. Toutes les modifications apportées à la configuration de l'adaptateur dans votre éditeur sont stockées avec vos paramètres de test.

Si vous exécutez vos tests à partir de Visual Studio, vous devez définir ces paramètres de test comme étant actifs. Pour plus d’informations sur les paramètres de test, consultez [Collecter des informations de diagnostic à l’aide des paramètres de test](../test/collect-diagnostic-information-using-test-settings.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="tasks"></a>Tâches

Utilisez les rubriques suivantes pour vous guider dans la création des adaptateurs de données de diagnostic :

|Tâches|Rubriques associées|
|-|-----------------------|
|**Création d’un adaptateur de données de diagnostic :** vous pouvez créer un adaptateur de données de diagnostic en définissant une bibliothèque de classes. Vous devez ensuite utiliser les API de l’adaptateur de données de diagnostic pour collecter les informations souhaitées ou impacter un système qui vous permet d’exécuter vos tests.|-   [Guide pratique pour créer un adaptateur de données de diagnostic](../test/how-to-create-a-diagnostic-data-adapter.md)|
|**Sélection d’un adaptateur de données de diagnostic personnalisé à utiliser durant l’exécution des tests :** vous pouvez sélectionner l’adaptateur de données de diagnostic à utiliser pour vos paramètres de test afin d’employer cet adaptateur quand vous exécutez vos tests.|-   [Collecter les données de diagnostic pendant les tests (Azure Test Plans)](/azure/devops/test/collect-diagnostic-data?view=vsts)<br />-   [Collecter les données de diagnostic dans des tests manuels (Azure Test Plans)](/azure/devops/test/mtm/collect-more-diagnostic-data-in-manual-tests?view=vsts)|

## <a name="see-also"></a>Voir aussi

- [Collecter des informations de diagnostic à l’aide des paramètres de test](../test/collect-diagnostic-information-using-test-settings.md)