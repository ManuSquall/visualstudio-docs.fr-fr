---
title: Mise en route avec les Plug-ins de contrôle de code Source | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- source control plug-ins, getting started
- getting started, source control plug-ins
ms.assetid: 46ac1f9f-4ecc-4a72-88d3-4c7e1647e1cb
caps.latest.revision: 22
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 725adb2325d5da10ff3ecd3c646464c5a4a6eb4f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49236357"
---
# <a name="getting-started-with-source-control-plug-ins"></a>Bien démarrer avec les plug-ins de contrôle de code source
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Pour créer un contrôle de source de plug-in, vous devez créer une DLL qui implémente les fonctions définies dans l’API de plug-in de contrôle de Source, puis inscrire la DLL avec [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] pour le rendre disponible pour une utilisation dans le contrôle de version du code source.  
  
 Trois versions de l’API de plug-in de contrôle de Source (versions 1.1, 1.2 et 1.3) sont disponibles pour les plug-ins de contrôle de code source. L’API de plug-in de contrôle Source décrite ici est la version 1.3. Il a été conçu pour être entièrement compatible avec les plug-ins de contrôle de code source prenant en charge les versions 1.1 et 1.2. Le [What ' s New in Version 1.3 des API de plug-in de contrôle Source](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-3.md) section décrit en détail les nouvelles fonctionnalités prises en charge dans la dernière version de l’API de plug-in de contrôle de Source.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Guide pratique pour installer un plug-in de contrôle de code source](../../extensibility/internals/how-to-install-a-source-control-plug-in.md)  
 Décrit comment rendre les entrées de Registre qui sont requis pour incorporer dans un DLL de contrôle de code source.  
  
 [Nouveautés dans l’API de plug-in de contrôle de code source version 1.3](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-3.md)  
 Fournit une vue d’ensemble des modifications qui ont été apportées à l’API de plug-in de contrôle de Source dans la version 1.3.  
  
 [Nouveautés dans l’API de plug-in de contrôle de code source version 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)  
 Fournit une vue d’ensemble des modifications qui ont été apportées à l’API de plug-in de contrôle de Source dans la version 1.2.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Plug-ins de contrôle de code source](../../extensibility/source-control-plug-ins.md)  
 Fournit une liste complète de tous les éléments dans l’API de plug-in de contrôle de Source.  
  
 [Création d’un plug-in de contrôle de code source](../../extensibility/internals/creating-a-source-control-plug-in.md)  
 Définit le SDK de plug-in de contrôle de Source et décrit les ressources incluses.

