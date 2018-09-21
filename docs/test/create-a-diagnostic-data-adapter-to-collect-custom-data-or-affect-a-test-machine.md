---
title: Créer un adaptateur de données de diagnostic à des fins de test dans Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Diagnostic Data Adapter [Visual Studio ALM]
- Diagnostic Data Adapter
ms.assetid: b0b53fae-7007-4ad9-a604-21685937622f
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 0839bbf95b701f1104ab5c9fb1c66318ac4707c9
ms.sourcegitcommit: 28909340cd0a0d7cb5e1fd29cbd37e726d832631
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44321227"
---
# <a name="create-a-diagnostic-data-adapter-to-collect-custom-data-or-affect-a-test-machine"></a>Créer un adaptateur de données de diagnostic pour collecter des données personnalisées ou affecter une machine de test

Vous pouvez créer votre propre adaptateur de données de diagnostic de façon à collecter des données lors de l'exécution d'un test ; vous souhaitez peut-être aussi affecter l'ordinateur de test dans le cadre de votre test. Par exemple, vous pouvez collecter des fichiers journaux qui sont créés par l'application testée et les joindre à vos résultats de tests, ou bien exécuter vos tests lorsque l'espace disque restant sur votre ordinateur est limité. À l’aide des API fournies dans Visual Studio Enterprise, vous pouvez écrire du code pour exécuter des tâches à des points spécifiques de votre série de tests. Par exemple, vous pouvez effectuer des tâches lorsqu’une série de tests démarre, avant et après avoir exécuté chaque test individuel, et lorsque la série de tests se termine.

Vous pouvez fournir l'entrée par défaut de votre adaptateur de données de diagnostic personnalisé à l'aide d'un fichier de paramètres de configuration. Par exemple, vous avez la possibilité de fournir des informations indiquant l'emplacement du fichier que vous voulez collecter et joindre à vos résultats de tests, ou la quantité d'espace disque qui doit rester disponible sur le système. Ces données peuvent être configurées pour chaque paramètre de test que vous créez. Vous pouvez les afficher et les modifier à l’aide de l’éditeur par défaut fourni avec Microsoft Test Manager, ou bien vous pouvez créer votre propre contrôle utilisateur à utiliser en tant qu’éditeur. Toutes les modifications apportées à la configuration de l'adaptateur dans votre éditeur sont stockées avec vos paramètres de test.

Si vous exécutez vos tests à partir de Visual Studio, vous devez définir ces paramètres de test comme étant actifs. Pour plus d’informations sur les paramètres de test, consultez [Collecter des informations de diagnostic à l’aide des paramètres de test](../test/collect-diagnostic-information-using-test-settings.md).

## <a name="tasks"></a>Tâches

 Utilisez les rubriques suivantes pour vous guider dans la création des adaptateurs de données de diagnostic :

|Tâches|Rubriques associées|
|-----------|-----------------------|
|**Création d’un adaptateur de données de diagnostic :** vous pouvez créer un adaptateur de données de diagnostic en définissant une bibliothèque de classes. Vous devez ensuite utiliser les API de l’adaptateur de données de diagnostic pour collecter les informations souhaitées ou impacter un système qui vous permet d’exécuter vos tests.|-   [Guide pratique pour créer un adaptateur de données de diagnostic](../test/how-to-create-a-diagnostic-data-adapter.md)|
|**Installation d’un adaptateur de données de diagnostic personnalisé :** vous pouvez installer votre adaptateur de données de diagnostic, ou un adaptateur fourni par un tiers, en le copiant dans le répertoire approprié.|-   [Guide pratique pour installer un adaptateur de données de diagnostic personnalisé](../test/how-to-install-a-custom-diagnostic-data-adapter.md)|
|**Sélection d’un adaptateur de données de diagnostic personnalisé à utiliser durant l’exécution des tests :** vous pouvez sélectionner l’adaptateur de données de diagnostic à utiliser pour vos paramètres de test afin d’employer cet adaptateur quand vous exécutez vos tests.|-   [Collecter les données de diagnostic pendant les tests (Azure Test Plans)](/azure/devops/test/collect-diagnostic-data?view=vsts)<br />-   [Collecter les données de diagnostic dans des tests manuels (Azure Test Plans)](/azure/devops/test/mtm/collect-more-diagnostic-data-in-manual-tests?view=vsts)|
|**Configuration des opérations exécutées par un adaptateur de données de diagnostic :** vous pouvez configurer les paramètres qui permettent de contrôler les actions de l’adaptateur de données de diagnostic dans ces paramètres de test spécifiques.|-   [Guide pratique pour créer un éditeur personnalisé pour les données de votre adaptateur de données de diagnostic](../test/how-to-create-a-custom-editor-for-data-for-your-diagnostic-data-adapter.md)|

## <a name="see-also"></a>Voir aussi

- [Exemple de projet pour la création d’un adaptateur de données de diagnostic](../test/sample-project-for-creating-a-diagnostic-data-adapter.md)
- [Collecter des informations de diagnostic à l’aide des paramètres de test](../test/collect-diagnostic-information-using-test-settings.md)