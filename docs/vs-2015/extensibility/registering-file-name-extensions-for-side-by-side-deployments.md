---
title: Inscription des extensions de nom de fichier pour les déploiements côte à côte | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- file extensions, registering for side-by-side
ms.assetid: 9ab046a2-147d-4167-aa14-7d661b1eaaa5
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 354b91dd1282df9726c1ee9c47f610b0dfdd9c1a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68163700"
---
# <a name="registering-file-name-extensions-for-side-by-side-deployments"></a>Inscription d’extensions de nom de fichier pour les déploiements côte à côte
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pour les VSPackages déployés dans un environnement côte à côte, vous devez inscrire les extensions de nom de fichier pour associer les fichiers à la version correcte de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . À moins que vous n’utilisiez une extension de nom de fichier spécifique à la version, l’inscription permet aux utilisateurs d’ouvrir vos fichiers de projet et d’élément de projet dans la version appropriée de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
## <a name="in-this-section"></a>Dans cette section  
 [À propos des extensions de nom de fichier](../extensibility/about-file-name-extensions.md)  
 Explique comment les extensions de nom de fichier sont inscrites.  
  
 [Spécification des gestionnaires de fichiers pour les extensions de nom de fichier](../extensibility/specifying-file-handlers-for-file-name-extensions.md)  
 Fournit des informations sur l’inscription des applications qui peuvent ouvrir, modifier, etc., une extension de nom de fichier particulière.  
  
 [Inscription des verbes pour les extensions de nom de fichier](../extensibility/registering-verbs-for-file-name-extensions.md)  
 Explique comment inscrire des verbes.  
  
 [Gestion des associations de fichiers côte à côte](../extensibility/managing-side-by-side-file-associations.md)  
 Explique comment gérer des installations côte à côte dans lesquelles une version particulière de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] doit être appelée pour ouvrir un fichier.  
  
## <a name="related-sections"></a>Sections connexes  
 [Prise en charge de plusieurs versions de Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md)  
 Décrit les problèmes liés aux versions multiples de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] et à votre VSPackage lors du développement et du déploiement pour les utilisateurs finaux.
