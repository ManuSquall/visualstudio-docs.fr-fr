---
title: L’inscription des Extensions de nom de fichier pour les déploiements côte à côte | Microsoft Docs
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
- file extensions, registering for side-by-side
ms.assetid: 9ab046a2-147d-4167-aa14-7d661b1eaaa5
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9d16c6475675fbf563f8228a6e05dfb81f739485
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49211417"
---
# <a name="registering-file-name-extensions-for-side-by-side-deployments"></a>Inscription d’extensions de nom de fichier pour les déploiements côte à côte
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pour les VSPackages déployés dans un environnement côte à côte, vous devez inscrire des extensions de nom de fichier pour associer les fichiers à la version correcte du [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Sauf si vous utilisez une extension de nom de fichier spécifique à la version, l’inscription permet aux utilisateurs d’ouvrir votre projet et d’élément les fichiers projet dans la version appropriée de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
## <a name="in-this-section"></a>Dans cette section  
 [À propos des extensions de nom de fichier](../extensibility/about-file-name-extensions.md)  
 Explique comment les extensions de nom de fichier sont enregistrées.  
  
 [Spécification des gestionnaires de fichiers pour les extensions de nom de fichier](../extensibility/specifying-file-handlers-for-file-name-extensions.md)  
 Fournit des informations sur la façon d’inscrire les applications que vous peuvent ouvrir, modifier et ainsi de suite, une extension de nom de fichier particulier.  
  
 [Inscription des verbes pour les extensions de nom de fichier](../extensibility/registering-verbs-for-file-name-extensions.md)  
 Explique comment inscrire des verbes.  
  
 [Gestion des associations de fichiers côte à côte](../extensibility/managing-side-by-side-file-associations.md)  
 Explique comment gérer des installations côte à côte dans lequel une version particulière de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] doit être appelé pour ouvrir un fichier.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Prise en charge de plusieurs versions de Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md)  
 Décrit les problèmes liés aux versions multiples de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] et à votre VSPackage lors du développement et du déploiement pour les utilisateurs finaux.

