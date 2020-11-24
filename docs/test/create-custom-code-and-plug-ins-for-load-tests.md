---
title: Créer un code et des plug-ins personnalisés pour les tests de charge
description: Découvrez comment utiliser l’API de test de charge et l’API de test de performances de site Web pour créer des plug-ins personnalisés pour les tests à développer avec les fonctionnalités intégrées.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
f1_keywords:
- vs.test.dialog.recorderplugin
helpviewer_keywords:
- Web performance tests, plug-ins
- load tests, plug-ins
ms.assetid: 0c0fcc99-673b-4ea0-a268-0475f66e5cb6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: db91f8f5ccf86d67d01bb56a3a42b66757320500
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2020
ms.locfileid: "95442662"
---
# <a name="create-custom-code-and-plug-ins-for-load-tests"></a>Créer un code et des plug-ins personnalisés pour les tests de charge

Un plug-in personnalisé utilise du code écrit et attaché à un test de charge ou à un test de performances web. Vous pouvez utiliser l’API de test de charge et l’API de test de performances web pour créer des plug-ins personnalisés de test qui étendent les fonctionnalités intégrées. Vous pouvez ajouter plusieurs plug-ins à votre test de charge.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="tasks"></a>Tâches

|Tâches|Rubriques associées|
|-|-----------------------|
|**Créer un plug-in personnalisé pour votre test de charge :** vous pouvez utiliser l’API de test de charge pour créer un plug-in personnalisé et ajouter des fonctionnalités de test à votre test de charge.|-   [Comment : utiliser l’API de test de charge](../test/how-to-use-the-load-test-api.md)<br />-   [Comment : créer un plug-in de test de charge](../test/how-to-create-a-load-test-plug-in.md)|
|**Créez un plug-in personnalisé pour votre test de performances de site Web :** Vous pouvez utiliser l’API de test de performances de site Web pour créer un plug-in personnalisé afin d’ajouter d’autres fonctionnalités de test à votre test de performances de site Web, y compris au niveau de la demande. Il est également possible de créer un test de service web.<br /><br /> Par ailleurs, vous pouvez créer un plug-in d’enregistreur web capable de modifier un test de performances web après son enregistrement, mais avant qu’il ne s’affiche dans l’Afficheur de résultats de test de performances web.|-   [Comment : utiliser l’API de test de performances de site Web](../test/how-to-use-the-web-performance-test-api.md)<br />-   [Comment : créer un plug-in de test de performances de site Web](../test/how-to-create-a-web-performance-test-plug-in.md)<br />-   [Comment : créer un plug-in de niveau demande](../test/how-to-create-a-request-level-plug-in.md)<br />-   [Comment : créer un test de service Web](../test/how-to-create-a-web-service-test.md)<br />-   [Comment : créer un plug-in d’enregistreur](../test/how-to-create-a-recorder-plug-in.md)|
|**Ajouter des fonctionnalités d’IU à l’Afficheur des résultats des tests de performances web :** Vous pouvez ajouter d’autres fonctionnalités d’interface utilisateur à l’Afficheur de résultats de test de performances web à l’aide d’un complément Visual Studio.|-   [Comment : créer un complément Visual Studio pour l’afficheur de résultats de test de performances de site Web](../test/how-to-create-an-add-in-for-the-web-performance-test-results-viewer.md)|
|**Créer un éditeur de corps HTTP personnalisé :** vous pouvez créer un éditeur personnalisé pour modifier les réponses XML HTTP binaires ou de chaîne à partir d’un service web.|-   [Comment : créer un éditeur de corps HTTP personnalisé pour l’éditeur de test de performances de site Web](../test/how-to-create-a-custom-http-body-editor-for-the-web-performance-test-editor.md)|

## <a name="reference"></a>Informations de référence

<xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestPlugin>

<xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin>

<xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin>

<xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin>

<xref:Microsoft.VisualStudio.TestTools.LoadTesting>

## <a name="see-also"></a>Voir aussi

- [Analyser les résultats des tests de charge](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Générer et exécuter un test de performances de site Web codé](../test/generate-and-run-a-coded-web-performance-test.md)
