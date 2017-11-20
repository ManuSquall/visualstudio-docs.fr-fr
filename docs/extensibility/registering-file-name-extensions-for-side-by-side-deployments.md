---
title: "L’inscription des Extensions de nom de fichier pour les déploiements côte à côte | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: file extensions, registering for side-by-side
ms.assetid: 9ab046a2-147d-4167-aa14-7d661b1eaaa5
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 42c1c573554ee6d92b3967517bdcdf0f3106ce61
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="registering-file-name-extensions-for-side-by-side-deployments"></a>L’inscription des Extensions de nom de fichier pour les déploiements côte à côte
Pour les VSPackages déployés dans un environnement côte à côte, vous devez inscrire les extensions de nom de fichier pour associer les fichiers de la version correcte de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Sauf si vous utilisez une extension de nom de fichier spécifique à la version, l’inscription permet aux utilisateurs d’ouvrir votre projet et élément les fichiers projet dans la version appropriée de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## <a name="in-this-section"></a>Dans cette section  
 [À propos des extensions de nom de fichier](../extensibility/about-file-name-extensions.md)  
 Explique comment les extensions de nom de fichier sont enregistrées.  
  
 [Spécification des gestionnaires de fichiers pour les extensions de nom de fichier](../extensibility/specifying-file-handlers-for-file-name-extensions.md)  
 Fournit des informations sur la façon d’inscrire les applications que vous peuvent ouvrir, modifier et ainsi de suite, une extension de nom de fichier particulier.  
  
 [Inscription des verbes pour les extensions de nom de fichier](../extensibility/registering-verbs-for-file-name-extensions.md)  
 Explique comment inscrire des verbes.  
  
 [Gestion des associations de fichiers côte à côte](../extensibility/managing-side-by-side-file-associations.md)  
 Explique comment gérer des installations côte à côte dans lesquels une version particulière de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] doit être appelé pour ouvrir un fichier.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Prise en charge de plusieurs versions de Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md)  
 Décrit les problèmes liés à plusieurs versions de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] et votre VSPackage lors du développement et de déploiement pour les utilisateurs finaux.