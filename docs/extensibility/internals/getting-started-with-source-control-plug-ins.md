---
title: "Prise en main de Plug-ins de contrôle de code Source | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control plug-ins, getting started
- getting started, source control plug-ins
ms.assetid: 46ac1f9f-4ecc-4a72-88d3-4c7e1647e1cb
caps.latest.revision: "21"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 197cc0f0997e80d6cae277c4b19c5bbc82dce805
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="getting-started-with-source-control-plug-ins"></a>Prise en main de Plug-ins de contrôle de code Source
Pour créer un contrôle de source de plug-in, vous devez créer une DLL qui implémente les fonctions définies dans l’API de plug-in de contrôle de Source, puis inscrire la DLL avec [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pour le rendre disponible pour une utilisation dans le contrôle de version du code source.  
  
 Trois versions de l’API de plug-in de contrôle de Source (versions 1.1, 1.2 et 1.3) sont disponibles pour les plug-ins de contrôle de code source. L’API de plug-in de contrôle de Source documenté ici est la version 1.3. Il a été conçu pour être entièrement compatible avec les plug-ins de contrôle de code source prise en charge les versions 1.1 et 1.2. Le [Nouveautés de la Version 1.3 des API de plug-in de contrôle Source](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-3.md) section détaille les nouvelles fonctionnalités prises en charge dans la dernière version de l’API de plug-in de contrôle de Source.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Guide pratique pour installer un plug-in de contrôle de code source](../../extensibility/internals/how-to-install-a-source-control-plug-in.md)  
 Décrit comment créer les entrées de Registre nécessaires pour incorporer dans un DLL de contrôle de code source.  
  
 [Nouveautés dans l’API de plug-in de contrôle de code source version 1.3](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-3.md)  
 Fournit une vue d’ensemble des modifications qui ont été apportées à l’API de plug-in de contrôle de Source dans la version 1.3.  
  
 [Nouveautés dans l’API de plug-in de contrôle de code source version 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)  
 Fournit une vue d’ensemble des modifications qui ont été apportées à l’API de plug-in de contrôle de Source dans la version 1.2.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Plug-ins de contrôle de code source](../../extensibility/source-control-plug-ins.md)  
 Fournit une liste complète de tous les éléments dans l’API de plug-in de contrôle de Source.  
  
 [Création d’un plug-in de contrôle de code source](../../extensibility/internals/creating-a-source-control-plug-in.md)  
 Définit le SDK de plug-in de contrôle de Source et décrit les ressources incluses.