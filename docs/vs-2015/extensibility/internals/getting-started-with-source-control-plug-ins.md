---
title: Prise en main avec des plug-ins de contrôle de code source | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, getting started
- getting started, source control plug-ins
ms.assetid: 46ac1f9f-4ecc-4a72-88d3-4c7e1647e1cb
caps.latest.revision: 22
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 85aa5727f252ad75c45064d7b885e3d282da36a4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62538159"
---
# <a name="getting-started-with-source-control-plug-ins"></a>Bien démarrer avec les plug-ins de contrôle de code source
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Pour créer un plug-in de contrôle de code source, vous devez créer une DLL qui implémente les fonctions définies dans l’API de plug-in de contrôle de code source, puis inscrire la DLL auprès [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] de afin de la rendre disponible pour une utilisation dans le contrôle de version de code source.  
  
 Trois versions de l’API de plug-in de contrôle de code source (versions 1,1, 1,2 et 1,3) sont disponibles pour les plug-ins de contrôle de code source. L’API de plug-in de contrôle de code source décrite ici est la version 1,3. Il a été conçu pour être entièrement compatible avec les plug-ins de contrôle de code source prenant en charge les versions 1,1 et 1,2. La section [Nouveautés de la version 1,3 de l’API de plug-in de contrôle de code source](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-3.md) détaille les nouvelles fonctionnalités prises en charge dans la dernière version de l’API de plug-in de contrôle de code source.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Guide pratique pour installer un plug-in de contrôle de code source](../../extensibility/internals/how-to-install-a-source-control-plug-in.md)  
 Décrit comment rendre les entrées de Registre requises pour le plug-in d’une DLL de contrôle de code source.  
  
 [Nouveautés de l’API de plug-in de contrôle de code source version 1.3](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-3.md)  
 Fournit une brève vue d’ensemble des modifications apportées à l’API de plug-in de contrôle de code source dans la version 1,3.  
  
 [Nouveautés de l’API de plug-in de contrôle de code source version 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)  
 Fournit une brève vue d’ensemble des modifications apportées à l’API de plug-in de contrôle de code source dans la version 1,2.  
  
## <a name="related-sections"></a>Sections connexes  
 [Plug-ins de contrôle de code source](../../extensibility/source-control-plug-ins.md)  
 Fournit une liste complète de tous les éléments de l’API de plug-in de contrôle de code source.  
  
 [Création d’un plug-in de contrôle de code source](../../extensibility/internals/creating-a-source-control-plug-in.md)  
 Définit le kit de développement logiciel (SDK) du plug-in de contrôle de code source et décrit les ressources incluses.
