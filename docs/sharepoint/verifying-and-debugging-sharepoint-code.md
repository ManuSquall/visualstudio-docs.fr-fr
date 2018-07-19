---
title: Vérification et débogage du Code SharePoint | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- unit testing [SharePoint development in Visual Studio]
- IntelliTrace [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, IntelliTrace
- SharePoint development in Visual Studio, unit testing
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 327e7be43fc60142fc50634ec61f6fd9499461e2
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37119191"
---
# <a name="verify-and-debug-sharepoint-code"></a>Vérifier et de déboguer du code SharePoint
À l’aide d’IntelliTrace et du test unitaire, déboguez vos solutions SharePoint plus facilement et assurez-vous que chacune de leur méthode fonctionne correctement. Vous pouvez utiliser ces fonctionnalités pour les projets SharePoint dans Visual Studio en suivant les mêmes procédures que pour d’autres types de projets.

## <a name="intellitrace"></a>IntelliTrace
En utilisant IntelliTrace, vous pouvez déterminer non seulement l'état actuel de votre solution SharePoint, mais également les événements qui se sont produits dans le passé et le contexte dans lesquels ils se sont produits. Vous pouvez naviguer dans votre solution SharePoint à travers différents points, où les événements d’intérêt ont été enregistrés et examiner les états et les valeurs des variables à chaque point. En utilisant cette navigation dynamique, vous pouvez plus rapidement et facilement déboguer vos solutions SharePoint sans définir de nombreux points d'arrêt. Vous pouvez également enregistrer la session de débogage dans un fichier journal IntelliTrace (*.iTrace*) de fichiers, plus tard dans Visual Studio Enterprise et exécuter le débogage post-incident. Le *.iTrace* fichier comprend des informations détaillées sur quand et où des erreurs spécifiques SharePoint est arrivé, afin que vous pouvez déterminer plus facilement ce qui provoque les erreurs. Les informations contenues dans le *.iTrace* fichier est un sous-ensemble du journal des erreurs complet qui crée le système ULS (Unified Logging) dans SharePoint. Ces informations incluent les événements qui sont spécifiques à SharePoint, comme lorsqu'un profil utilisateur est ouvert ou fermé et lorsque les propriétés d'un projet SharePoint sont chargées, lues, ou changées. Vous pouvez configurer quels événements IntelliTrace enregistre. Pour plus d’informations, consultez [à l’aide des données IntelliTrace enregistrée](/visualstudio/debugger/using-saved-intellitrace-data).

Lorsqu'une erreur se produit dans SharePoint, la boîte de dialogue d'erreurs affiche un identificateur "ID de corrélation" pour cette erreur particulière. Vous pouvez également obtenir l’ID de corrélation à partir d’événements qui sont répertoriées dans le *.iTrace* fichier. Pour afficher une liste de tous les événements qui se sont produits avec un ID de corrélation donné, vous pouvez entrer l’ID dans le **Analysis** section de la page résumée IntelliTrace. Dans cette section, vous pouvez choisir d'afficher uniquement les noms des événements qui se sont produits ou les noms des événements avec leurs informations d'appels, telles que le nom de la fonction, la sortie et les points d'entrée, les paramètres, et les valeurs de retour.

Vous pouvez obtenir des événements de Visual Studio dans IntelliTrace en choisissant le **F5** clé. Toutefois, pour obtenir des événements spécifiques à SharePoint, vous devez collecter des données IntelliTrace dans les solutions SharePoint à l'aide de Microsoft Monitoring Agent. Cet outil collecte des données IntelliTrace et crée *.iTrace* fichiers pour les applications qui sont déployées en dehors de Visual Studio. Pour plus d’informations, consultez [fonctionnalités IntelliTrace](/visualstudio/debugger/intellitrace-features) et [à l’aide du collecteur autonome IntelliTrace](/visualstudio/debugger/using-the-intellitrace-stand-alone-collector).

## <a name="unit-test"></a>Test unitaire
Vous pouvez trouver plus facilement les erreurs dans votre code en effectuant des tests unitaires, dans lequel vous écrivez et exécutez le code de test à l’intérieur des méthodes de test. Ces méthodes contiennent des variables vides et une instruction Assert qui vous permettent de vérifier la logique et les fonctionnalités de votre projet en fonction du modèle objet SharePoint. Pour plus d’informations, consultez [Tests unitaires sur votre code](/visualstudio/test/unit-test-your-code).

### <a name="support-for-microsoft-fakes-framework"></a>Prise en charge Microsoft Fakes framework
Les projets SharePoint prennent en charge Microsoft Fakes, qui est un framework d'isolation dans lequel vous pouvez créer des stubs de test basés sur des délégués et des modificateurs de test dans les applications basées sur .NET Framework. En utilisant le framework Fakes, il est possible de créer, gérer, et réinjecter des implémentations fictives dans vos tests unitaires. Ces stubs et ces modificateurs isolent vos tests unitaires de l'environnement. Créez des stubs pour tester du code qui utilise des interfaces ou des classes non-sealed avec des méthodes remplaçables. Créez des modificateurs pour rediriger des appels codés en dur des classes sealed avec des méthodes statiques ou de priorité absolue à une autre implémentation de modificateurs. Utilisez aussi des délégués avec les types de stub et les types de modificateurs pour personnaliser dynamiquement le comportement de chaque membre stub. Pour plus d’informations, consultez [isolation du Code sous Test avec Microsoft Fakes](/visualstudio/test/isolating-code-under-test-with-microsoft-fakes).

## <a name="related-articles"></a>Articles connexes

|Titre|Description|
|-----------|-----------------|
|[IntelliTrace](/visualstudio/debugger/intellitrace)|Décrit comment déboguer des solutions Visual Studio plus facilement à l'aide d'IntelliTrace.|
|[Procédure pas à pas : Déboguer une application SharePoint à l’aide d’IntelliTrace](../sharepoint/walkthrough-debugging-a-sharepoint-application-by-using-intellitrace.md)|Explique comment utiliser IntelliTrace pour rechercher des erreurs de codage dans un projet SharePoint.|
|[Tests unitaires sur votre code](/visualstudio/test/unit-test-your-code)|Décrit comment rechercher des erreurs de logique dans votre code à l’aide de tests unitaires.|

## <a name="see-also"></a>Voir aussi
[Améliorer la qualité du code](/visualstudio/test/improve-code-quality)
