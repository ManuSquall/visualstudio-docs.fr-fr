---
title: "V&#233;rification et d&#233;bogage du code SharePoint"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "test unitaire (développement SharePoint dans Visual Studio)"
  - "IntelliTrace (développement SharePoint dans Visual Studio)"
  - "développement SharePoint dans Visual Studio, IntelliTrace"
  - "développement SharePoint dans Visual Studio, test unitaire"
ms.assetid: b5f3bce2-6a51-41b1-a292-9e384bae420c
caps.latest.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# V&#233;rification et d&#233;bogage du code SharePoint
  À l'aide d'IntelliTrace et du test unitaire, déboguez vos solutions SharePoint plus facilement et vous assurer que chaque méthode dans votre application fonctionne correctement.  Utilisez ces fonctionnalités pour les projets SharePoint dans [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] en suivant les mêmes procédures que pour les autres types de projets.  
  
## IntelliTrace  
 En utilisant IntelliTrace, vous pouvez déterminer non seulement l'état actuel de votre solution SharePoint mais également les événements qui se sont produits dans le passé et le contexte dans lesquels ils se sont produits.  Vous pouvez passer d'un moment donné dans votre solution SharePoint où les événements d'intérêt ont été enregistrés à un autre et examiner les états et valeurs de variables à chaque point.  En utilisant cette navigation dynamique, vous pouvez plus rapidement et facilement déboguer vos solutions SharePoint sans définir de nombreux points d'arrêt.  Vous pouvez également enregistrer la session de débogage à un fichier journal IntelliTrace \(.iTrace\), l'ouvrir ultérieurement dans Visual Studio Ultimate, et exécuter le débogage post\-incident.  Le fichier .iTrace inclut des informations détaillées sur où et quand les erreurs spécifiques SharePoint se sont produites, afin que vous puissiez plus facilement connaître ce qui provoque les erreurs.  Les informations dans le fichier .iTrace sont un sous\-ensemble du journal des erreurs complet que le système d'enregistrement unifié \(ULS\) dans SharePoint crée.  Ces informations incluent les événements qui sont spécifiques à SharePoint, comme lorsqu'un profil utilisateur est ouvert ou fermé et lorsque les propriétés d'un projet SharePoint sont chargées, lues, ou changées.  Vous pouvez configurer quels événements IntelliTrace enregistre.  Pour plus d’informations, consultez [Utilisation des données IntelliTrace enregistrées](../debugger/using-saved-intellitrace-data.md) et [Configurer IntelliTrace pour collecter des informations de débogage](http://msdn.microsoft.com/fr-fr/7657ecab-e07e-4b1b-872d-f05d966be37e).  
  
 Lorsqu'une erreur se produit dans SharePoint, la boîte de dialogue Erreurs affiche un identificateur « ID de corrélation » pour cette erreur particulière.  Vous pouvez également obtenir les ID de corrélation des événements répertoriés dans le fichier .iTrace.  Pour afficher une liste de tous les événements qui se sont produits avec un ID donné de corrélation, écrivez l'ID dans la section **Analyse** de la page Résumé IntelliTrace.  Dans cette section, choisissez d'afficher uniquement les noms des événements qui se sont produits ou les noms des événements avec leurs informations d'appels, telles que le nom de la fonction, la sortie et les points d'entrée, les paramètres, et les valeurs de retour.  
  
 Vous pouvez obtenir des événements de Visual Studio dans IntelliTrace en sélectionnant la touche **F5**.  Pour obtenir des événements spécifiques à SharePoint, toutefois, vous devez collecter des données IntelliTrace dans les solutions SharePoint à l'aide de Microsoft surveillant l'agent.  Cet outil collecte des données IntelliTrace et crée des fichiers .iTrace des applications déployées en dehors de Visual Studio.  Pour plus d’informations, consultez [Fonctionnalités IntelliTrace](../debugger/intellitrace-features.md) et [Utilisation du collecteur autonome IntelliTrace](../debugger/using-the-intellitrace-stand-alone-collector.md).  
  
## Test unitaire  
 Vous pouvez trouver plus facilement les erreurs présentes dans votre code en exécutant le test unitaire, dans lequel vous écrivez et exécutez un code de test dans des méthodes de test.  Ces méthodes contiennent des variables vides et une instruction Assert que vous pouvez utiliser pour vérifier la logique et la fonctionnalité de votre projet en fonction du modèle d'objet de SharePoint.  Pour plus d'informations, consultez [Tests unitaires sur votre code](../test/unit-test-your-code.md).  
  
### Prise en charge de Microsoft Fakes Framework  
 Les projets SharePoint prennent en charge Microsoft Fakes, qui est un Framework d'isolation dans lequel vous pouvez créer des stubs de test basés sur des délégués et des modificateurs de test dans les applications basées sur .NET Framework.  En utilisant le Framework Fakes, il est possible de créer, gérer, et réinjecter des implémentations fictifs dans vos tests unitaires.  Ces stubs et ces modificateurs isolent vos tests unitaires de l'environnement.  Créez des stubs pour tester du code qui utilise des interfaces ou des classes non scellées avec des méthodes substituables.  Créez des modificateurs pour rediriger des appels codés en dur des classes scellées avec des méthodes statiques ou de priorité absolue à une autre implémentation de modificateurs.  Utilisez aussi des délégués avec les types de stub et les types de modificateurs pour personnaliser dynamiquement le comportement de chaque membre stub.  Pour plus d'informations, consultez [Isolation du code sous test avec Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md).  
  
## Rubriques connexes  
  
|Titre|Description|  
|-----------|-----------------|  
|[Utilisation d'IntelliTrace](../debugger/intellitrace.md)|Décrit comment déboguer des solutions Visual Studio plus facilement à l'aide d'IntelliTrace.|  
|[Procédure pas à pas : débogage d'une application SharePoint avec IntelliTrace](../sharepoint/walkthrough-debugging-a-sharepoint-application-by-using-intellitrace.md)|Explique comment utiliser IntelliTrace pour rechercher des erreurs de codage dans un projet SharePoint.|  
|[Tests unitaires sur votre code](../test/unit-test-your-code.md)|Décrit comment rechercher les erreurs de logique dans votre code à l'aide de tests unitaires.|  
  
## Voir aussi  
 [Améliorer la qualité du code](../test/improve-code-quality.md)  
  
  