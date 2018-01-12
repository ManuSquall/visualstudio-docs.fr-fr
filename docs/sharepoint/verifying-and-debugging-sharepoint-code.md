---
title: "Vérification et débogage du Code SharePoint | Documents Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
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
manager: ghogen
ms.workload: office
ms.openlocfilehash: 8c5eaf68a0d5349df88c2c819bce0f208721d267
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2018
---
# <a name="verifying-and-debugging-sharepoint-code"></a>Vérification et débogage du code SharePoint
  À l’aide d’IntelliTrace et du test unitaire, déboguez vos solutions SharePoint plus facilement et assurez-vous que chacune de leur méthode fonctionne correctement. Vous pouvez utiliser ces fonctionnalités pour les projets SharePoint dans [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] en suivant les mêmes procédures que pour les autres types de projets.  
  
## <a name="intellitrace"></a>IntelliTrace  
 En utilisant IntelliTrace, vous pouvez déterminer non seulement l'état actuel de votre solution SharePoint, mais également les événements qui se sont produits dans le passé et le contexte dans lesquels ils se sont produits. Vous pouvez naviguer dans votre solution SharePoint à travers différents points, où les événements d’intérêt ont été enregistrés et examiner les états et les valeurs des variables à chaque point. En utilisant cette navigation dynamique, vous pouvez plus rapidement et facilement déboguer vos solutions SharePoint sans définir de nombreux points d'arrêt. Vous pouvez également enregistrer la session de débogage dans un fichier journal IntelliTrace (.iTrace), l'ouvrir ultérieurement dans Visual Studio Ultimate, et exécuter le débogage post-incident. Le fichier .iTrace inclut des informations détaillées sur où et quand des erreurs spécifiques SharePoint se sont produites, afin que vous pouvez identifier plus facilement ce qui provoque les erreurs. Les informations dans le fichier .iTrace sont un sous-ensemble du journal des erreurs complet que le système d'enregistrement unifié (ULS) dans SharePoint crée. Ces informations incluent les événements qui sont spécifiques à SharePoint, comme lorsqu'un profil utilisateur est ouvert ou fermé et lorsque les propriétés d'un projet SharePoint sont chargées, lues, ou changées. Vous pouvez configurer quels événements IntelliTrace enregistre. Pour plus d’informations, consultez [à l’aide des données IntelliTrace enregistrée](/visualstudio/debugger/using-saved-intellitrace-data) et [IntelliTrace de configurer](http://msdn.microsoft.com/en-us/7657ecab-e07e-4b1b-872d-f05d966be37e).  
  
 Lorsqu'une erreur se produit dans SharePoint, la boîte de dialogue d'erreurs affiche un identificateur "ID de corrélation" pour cette erreur particulière. Vous pouvez également obtenir les ID de corrélation des événements répertoriés dans le fichier .iTrace. Pour afficher une liste de tous les événements qui se sont produits avec un ID de corrélation donné, vous pouvez entrer l’ID dans le **analyse** section de la page résumée IntelliTrace. Dans cette section, vous pouvez choisir d'afficher uniquement les noms des événements qui se sont produits ou les noms des événements avec leurs informations d'appels, telles que le nom de la fonction, la sortie et les points d'entrée, les paramètres, et les valeurs de retour.  
  
 Vous pouvez obtenir des événements de Visual Studio dans IntelliTrace en choisissant le **F5** clé. Toutefois, pour obtenir des événements spécifiques à SharePoint, vous devez collecter des données IntelliTrace dans les solutions SharePoint à l'aide de Microsoft Monitoring Agent. Cet outil collecte des données IntelliTrace et crée des fichiers .iTrace pour des applications déployées en dehors de Visual Studio. Pour plus d’informations, consultez [des fonctionnalités IntelliTrace](/visualstudio/debugger/intellitrace-features) et [à l’aide du collecteur autonome IntelliTrace](/visualstudio/debugger/using-the-intellitrace-stand-alone-collector).  
  
## <a name="unit-testing"></a>Test unitaire  
 Vous pouvez trouver plus facilement des erreurs dans votre code en effectuant des tests unitaires, d’écrire et exécuter le code de test à l’intérieur des méthodes de test. Ces méthodes contiennent des variables vides et une instruction Assert qui vous permet de vérifier la logique et les fonctionnalités de votre projet basé sur le modèle d’objet SharePoint. Pour plus d’informations, consultez [Tests unitaires sur votre code](/visualstudio/test/unit-test-your-code).  
  
### <a name="support-for-microsoft-fakes-framework"></a>Prise en charge de Microsoft Fakes Framework  
 Les projets SharePoint prennent en charge Microsoft Fakes, qui est un framework d'isolation dans lequel vous pouvez créer des stubs de test basés sur des délégués et des modificateurs de test dans les applications basées sur .NET Framework. En utilisant le framework Fakes, il est possible de créer, gérer, et réinjecter des implémentations fictives dans vos tests unitaires. Ces stubs et ces modificateurs isolent vos tests unitaires de l'environnement. Créez des stubs pour tester du code qui utilise des interfaces ou des classes non-sealed avec des méthodes remplaçables. Créez des modificateurs pour rediriger des appels codés en dur des classes sealed avec des méthodes statiques ou de priorité absolue à une autre implémentation de modificateurs. Utilisez aussi des délégués avec les types de stub et les types de modificateurs pour personnaliser dynamiquement le comportement de chaque membre stub. Pour plus d’informations, consultez [isolation de Code sous Test avec Microsoft Fakes](/visualstudio/test/isolating-code-under-test-with-microsoft-fakes).  
  
## <a name="related-topics"></a>Rubriques connexes  
  
|Titre|Description|  
|-----------|-----------------|  
|[IntelliTrace](/visualstudio/debugger/intellitrace)|Décrit comment déboguer des solutions Visual Studio plus facilement à l'aide d'IntelliTrace.|  
|[Procédure pas à pas : débogage d’une application SharePoint avec IntelliTrace](../sharepoint/walkthrough-debugging-a-sharepoint-application-by-using-intellitrace.md)|Explique comment utiliser IntelliTrace pour rechercher des erreurs de codage dans un projet SharePoint.|  
|[Tests unitaires sur votre code](/visualstudio/test/unit-test-your-code)|Explique comment rechercher des erreurs de logique dans votre code à l’aide de tests unitaires.|  
  
## <a name="see-also"></a>Voir aussi  
 [Améliorer la qualité du code](/visualstudio/test/improve-code-quality)  
  
  