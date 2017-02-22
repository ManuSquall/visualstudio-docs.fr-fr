---
title: "Param&#232;tres des pages de propri&#233;t&#233;s pour les projets Web | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "versions debug, paramètres de projet"
  - "configurations de débogage, projets Web"
  - "déboguer (Visual Studio), applications Web"
  - "déboguer les applications Web, paramètres de projet"
  - "paramètres du projet (Visual Studio), configurations de débogage"
  - "projets (Visual Studio), configurations de débogage"
ms.assetid: 8ec5160a-6408-4f47-8d41-f0e20e79a3b9
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Param&#232;tres des pages de propri&#233;t&#233;s pour les projets Web
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Vous pouvez modifier les paramètres de propriété de configuration Debug d'un site Web dans la boîte de dialogue **Pages de propriétés**, comme indiqué dans [Configurations Debug et Release](../debugger/how-to-set-debug-and-release-configurations.md).  Les tableaux suivants indiquent où se trouvent les paramètres du débogueur dans la boîte de dialogue **Pages de propriétés**.  
  
### Dossier Propriétés de configuration \(catégorie Options de démarrage\)  
  
|**Paramètre**|**Description**|  
|-------------------|---------------------|  
|**Action de démarrage**|Titre qui regroupe les options liées au démarrage d'une application.|  
|**Utiliser la page active**|Spécifie la page active comme point de départ du débogage.|  
|**Page spécifique :**|Spécifie la page Web à partir de laquelle vous voulez débuter le débogage.|  
|**Démarrer le programme externe :**|Spécifie la commande de lancement du programme que vous voulez déboguer.|  
|**Arguments de la ligne de commande :**|Spécifie les arguments de la commande spécifiée ci\-dessus.|  
|**Répertoire de travail :**|Spécifie le répertoire de travail du programme en cours de débogage.  En [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)], le répertoire de travail est celui à partir duquel l'application est lancée : \\bin\\debug par défaut.|  
|**Démarrer l'URL**|Spécifie l'emplacement de l'application Web que vous voulez déboguer.|  
|**Ne pas ouvrir de page.  Attendre une demande émanant d'une application externe**|Indique d'attendre une demande émanant d'une application externe.  Cette option ne lance pas Internet Explorer ou une autre application.  Elle prépare simplement au débogage en cas d'appel par une application.|  
|**Serveur**|Titre qui regroupe des options liées au serveur à utiliser.|  
|**Utiliser le serveur Web par défaut**|Indique d'utiliser le serveur Web par défaut.|  
|**Utiliser le serveur personnalisé**|Vous permet d'entrer l'URL de base à utiliser comme serveur.|  
|**Débogueurs**|Titre qui regroupe des options liées au type de débogage à réaliser.|  
|**Débogage ASP.NET**|Active le débogage des pages ASP écrites pour la plateforme de développement [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].  Vous devez spécifier une URL dans **Démarrer l'URL**.|  
|**Débogage de code natif**|Vous permet de déboguer les appels au code Win32 natif \(non managé\) à partir de votre application managée.|  
|**Débogage SQL Server**|Autorise le débogage d'objets de base de données SQL Server.|  
|**Débogage Silverlight**|Autorise le débogage de composants Silverlight.|  
  
## Voir aussi  
 [Paramètres et préparation du débogage](../debugger/debugger-settings-and-preparation.md)