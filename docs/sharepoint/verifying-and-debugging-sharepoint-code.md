---
title: Vérification et débogage du code SharePoint | Microsoft Docs
description: Vérifiez et déboguez le code SharePoint. Utilisez IntelliTrace pour examiner les événements passés et l’état actuel dans votre solution. Utilisez des tests unitaires pour garantir le bon fonctionnement de vos méthodes.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- unit testing [SharePoint development in Visual Studio]
- IntelliTrace [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, IntelliTrace
- SharePoint development in Visual Studio, unit testing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ce891e40552c0f8927bfd4ce006b750b6e5f8a54
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/09/2020
ms.locfileid: "96914502"
---
# <a name="verify-and-debug-sharepoint-code"></a>Vérifier et déboguer le code SharePoint
À l’aide d’IntelliTrace et du test unitaire, déboguez vos solutions SharePoint plus facilement et assurez-vous que chacune de leur méthode fonctionne correctement. Vous pouvez utiliser ces fonctionnalités pour les projets SharePoint dans Visual Studio en suivant les mêmes procédures que pour d’autres types de projets.

## <a name="intellitrace"></a>IntelliTrace
En utilisant IntelliTrace, vous pouvez déterminer non seulement l'état actuel de votre solution SharePoint, mais également les événements qui se sont produits dans le passé et le contexte dans lesquels ils se sont produits. Vous pouvez naviguer dans votre solution SharePoint à travers différents points, où les événements d'intérêt ont été enregistrés et examiner les états et les valeurs des variables à chaque point. En utilisant cette navigation dynamique, vous pouvez plus rapidement et facilement déboguer vos solutions SharePoint sans définir de nombreux points d'arrêt. Vous pouvez également enregistrer la session de débogage dans un fichier Journal IntelliTrace (*. iTrace*), l’ouvrir plus tard dans Visual Studio Enterprise et effectuer un débogage après incident. Le fichier *. iTrace* contient des informations détaillées sur le moment et l’endroit où des erreurs SharePoint spécifiques se sont produites, ce qui vous permet de déterminer plus facilement ce qui est à l’origine des erreurs. Les informations contenues dans le fichier *. iTrace* sont un sous-ensemble du journal des erreurs complet créé par le système de journalisation unifiée (ULS) dans SharePoint. Ces informations incluent les événements qui sont spécifiques à SharePoint, comme lorsqu'un profil utilisateur est ouvert ou fermé et lorsque les propriétés d'un projet SharePoint sont chargées, lues, ou changées. Vous pouvez configurer quels événements IntelliTrace enregistre. Pour plus d’informations, consultez [Utilisation des données IntelliTrace enregistrées](../debugger/using-saved-intellitrace-data.md).

Lorsqu'une erreur se produit dans SharePoint, la boîte de dialogue d'erreurs affiche un identificateur "ID de corrélation" pour cette erreur particulière. Vous pouvez également recevoir des ID de corrélation à partir des événements répertoriés dans le fichier *. iTrace* . Pour afficher la liste de tous les événements qui se sont produits avec un ID de corrélation donné, vous pouvez entrer l’ID dans la section **analyse** de la page Résumé IntelliTrace. Dans cette section, vous pouvez choisir d'afficher uniquement les noms des événements qui se sont produits ou les noms des événements avec leurs informations d'appels, telles que le nom de la fonction, la sortie et les points d'entrée, les paramètres, et les valeurs de retour.

Vous pouvez récupérer des événements Visual Studio dans IntelliTrace en choisissant la touche **F5** . Toutefois, pour obtenir des événements spécifiques à SharePoint, vous devez collecter des données IntelliTrace dans les solutions SharePoint à l'aide de Microsoft Monitoring Agent. Cet outil collecte des données IntelliTrace et crée des fichiers *. iTrace* pour les applications déployées en dehors de Visual Studio. Pour plus d’informations, consultez [fonctionnalités IntelliTrace](../debugger/intellitrace-features.md) et [utilisation du collecteur autonome IntelliTrace](../debugger/using-the-intellitrace-stand-alone-collector.md).

## <a name="unit-test"></a>Test unitaire
Vous pouvez trouver plus facilement les erreurs dans votre code en effectuant des tests unitaires, dans lesquels vous écrivez et exécutez le code de test dans les méthodes de test. Ces méthodes contiennent des variables vides et une instruction Assert que vous pouvez utiliser pour vérifier la logique et les fonctionnalités de votre projet en fonction du modèle d’objet SharePoint. Pour plus d’informations, consultez [Tests unitaires sur votre code](../test/unit-test-your-code.md).

### <a name="support-for-microsoft-fakes-framework"></a>Prise en charge de Microsoft Simulation Framework
Les projets SharePoint prennent en charge Microsoft Fakes, qui est un framework d'isolation dans lequel vous pouvez créer des stubs de test basés sur des délégués et des modificateurs de test dans les applications basées sur .NET Framework. En utilisant le framework Fakes, il est possible de créer, gérer, et réinjecter des implémentations fictives dans vos tests unitaires. Ces stubs et ces modificateurs isolent vos tests unitaires de l'environnement. Créez des stubs pour tester du code qui utilise des interfaces ou des classes non-sealed avec des méthodes remplaçables. Créez des modificateurs pour rediriger des appels codés en dur des classes sealed avec des méthodes statiques ou de priorité absolue à une autre implémentation de modificateurs. Utilisez aussi des délégués avec les types de stub et les types de modificateurs pour personnaliser dynamiquement le comportement de chaque membre stub. Pour plus d’informations, consultez [isolation du code testé avec Microsoft simulations](../test/isolating-code-under-test-with-microsoft-fakes.md).

## <a name="related-articles"></a>Articles connexes

|Titre|Description|
|-----------|-----------------|
|[IntelliTrace](../debugger/intellitrace.md)|Décrit comment déboguer des solutions Visual Studio plus facilement à l'aide d'IntelliTrace.|
|[Procédure pas à pas : déboguer une application SharePoint à l’aide d’IntelliTrace](../sharepoint/walkthrough-debugging-a-sharepoint-application-by-using-intellitrace.md)|Explique comment utiliser IntelliTrace pour rechercher des erreurs de codage dans un projet SharePoint.|
|[Tests unitaires sur votre code](../test/unit-test-your-code.md)|Décrit comment rechercher des erreurs de logique dans votre code à l’aide de tests unitaires.|

## <a name="see-also"></a>Voir aussi

- [Améliorer la qualité du code](../test/improve-code-quality.md)