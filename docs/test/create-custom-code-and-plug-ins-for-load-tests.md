---
title: Créer un code et des plug-ins personnalisés pour les tests de charge
ms.date: 10/19/2016
ms.topic: conceptual
f1_keywords:
- vs.test.dialog.recorderplugin
helpviewer_keywords:
- Web performance tests, plug-ins
- load tests, plug-ins
ms.assetid: 0c0fcc99-673b-4ea0-a268-0475f66e5cb6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 8382d5014b88d9f1711a082e46530e1e3dfb96e4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62965457"
---
# <a name="create-custom-code-and-plug-ins-for-load-tests"></a>Créer un code et des plug-ins personnalisés pour les tests de charge

Un plug-in personnalisé utilise du code écrit et attaché à un test de charge ou à un test de performances web. Vous pouvez utiliser l’API de test de charge et l’API de test de performances web pour créer des plug-ins personnalisés de test qui étendent les fonctionnalités intégrées. Vous pouvez ajouter plusieurs plug-ins à votre test de charge.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="tasks"></a>Tâches

|Tâches|Rubriques associées|
|-|-----------------------|
|**Créer un plug-in personnalisé pour votre test de charge** : vous pouvez utiliser l’API de test de charge pour créer un plug-in personnalisé et ajouter des fonctionnalités de test à votre test de charge.|-   [Guide pratique pour utiliser l’API de test de charge](../test/how-to-use-the-load-test-api.md)<br />-   [Guide pratique pour créer un plug-in de test de charge](../test/how-to-create-a-load-test-plug-in.md)|
|**Créer un plug-in personnalisé pour votre test de performances web** : vous pouvez utiliser l’API de test de performances web pour créer un plug-in personnalisé visant à ajouter des fonctionnalités de test au test de performances web, notamment au niveau de la requête. Il est également possible de créer un test de service web.<br /><br /> Par ailleurs, vous pouvez créer un plug-in d’enregistreur web capable de modifier un test de performances web après son enregistrement, mais avant qu’il ne s’affiche dans l’Afficheur de résultats de test de performances web.|-   [Guide pratique pour utiliser l’API de test de performances web](../test/how-to-use-the-web-performance-test-api.md)<br />-   [Guide pratique pour créer un plug-in de test de performances web](../test/how-to-create-a-web-performance-test-plug-in.md)<br />-   [Guide pratique pour créer un plug-in au niveau de la requête](../test/how-to-create-a-request-level-plug-in.md)<br />-   [Guide pratique pour créer un test de service web](../test/how-to-create-a-web-service-test.md)<br />-   [Guide pratique pour créer un plug-in d’enregistreur](../test/how-to-create-a-recorder-plug-in.md)|
|**Ajouter des fonctionnalités d’IU à l’Afficheur de résultats de test de performances Web :** vous pouvez ajouter d’autres fonctionnalités d’IU à l’Afficheur de résultats de test de performances Web à l’aide d’un complément Visual Studio.|-   [Guide pratique pour créer un complément Visual Studio pour l’Afficheur de résultats de test de performances Web](../test/how-to-create-an-add-in-for-the-web-performance-test-results-viewer.md)|
|**Créer un éditeur de corps HTTP personnalisé :** vous pouvez créer un éditeur personnalisé pour modifier les réponses XML http binaires ou de chaîne à partir d’un service web.|-   [Guide pratique pour créer un éditeur de corps HTTP personnalisé pour l’éditeur de test de performances web](../test/how-to-create-a-custom-http-body-editor-for-the-web-performance-test-editor.md)|

## <a name="reference"></a>Référence

<xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestPlugin>

<xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin>

<xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin>

<xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin>

<xref:Microsoft.VisualStudio.TestTools.LoadTesting>

## <a name="see-also"></a>Voir aussi

- [Analyser les résultats des tests de charge](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Générer et exécuter un test de performances web codé](../test/generate-and-run-a-coded-web-performance-test.md)