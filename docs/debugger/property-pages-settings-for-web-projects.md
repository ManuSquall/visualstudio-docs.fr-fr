---
title: Paramètres de propriété pour les projets Web | Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], Web applications
- project settings [Visual Studio], debug configurations
- debug builds, project settings
- projects [Visual Studio], debug configurations
- debugging Web applications, project settings
- debug configurations, Web projects
ms.assetid: 8ec5160a-6408-4f47-8d41-f0e20e79a3b9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 809e84981bc491a89f8e031f5ac8caf497c1a6e6
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55001967"
---
# <a name="property-pages-settings-for-web-projects"></a>Paramètres des pages de propriétés pour les projets Web
Vous pouvez modifier les paramètres de propriété de configuration Debug d’un site web dans la boîte de dialogue **Pages de propriétés**, comme indiqué dans [Configurations Debug et Release](../debugger/how-to-set-debug-and-release-configurations.md). Les tableaux suivants indiquent où se trouvent les paramètres du débogueur dans la boîte de dialogue **Pages de propriétés**.  
  
### <a name="start-options-category"></a>Catégorie d’Options de démarrage
  
| **Paramètre** | **Description** |
| - | - |
| **Action de démarrage** | Titre qui regroupe les options liées au démarrage d'une application. |
| **Utiliser la page active** | Spécifie la page active comme point de départ du débogage. |
| **Page spécifique :** | Spécifie la page web à partir de laquelle vous voulez débuter le débogage. |
| **Démarrer le programme externe :** | Spécifie la commande de lancement du programme que vous voulez déboguer. |
| **Arguments de ligne de commande :** | Spécifie les arguments de la commande spécifiée ci-dessus. |
| **Répertoire de travail :** | Spécifie le répertoire de travail du programme en cours de débogage. En [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)], le répertoire de travail est celui à partir duquel l'application est lancée : \bin\debug par défaut. |
| **URL de démarrage** | Spécifie l'emplacement de l'application Web que vous voulez déboguer. |
| **Ne pas ouvrir de page. Attendre une demande émanant d’une application externe** | Indique d'attendre une demande émanant d'une application externe. Cette option ne lance pas Internet Explorer ou une autre application. Elle prépare simplement au débogage en cas d'appel par une application. |
| **Serveur** | Titre qui regroupe des options liées au serveur à utiliser. |
| **Utiliser le serveur Web par défaut** | Indique d’utiliser le serveur web par défaut. |
| **Utiliser le serveur personnalisé** | Vous permet d'entrer l'URL de base à utiliser comme serveur. |
| **Débogueurs** | Titre qui regroupe des options liées au type de débogage à réaliser. |
| **Débogage ASP.NET** | Active le débogage des pages ASP écrites pour la plateforme de développement [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]. Vous devez spécifier une URL dans **URL de démarrage**. |
| **Débogage du code natif** | Vous permet de déboguer les appels au code Win32 natif (non managé) à partir de votre application managée. |
| **Débogage SQL Server** | Autorise le débogage d'objets de base de données SQL Server. |
| **Débogage Silverlight** | Autorise le débogage de composants Silverlight. |
  
## <a name="see-also"></a>Voir aussi  
 [Paramètres et préparation du débogueur](../debugger/debugger-settings-and-preparation.md)