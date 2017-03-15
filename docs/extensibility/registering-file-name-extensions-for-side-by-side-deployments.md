---
title: "L’inscription des Extensions de nom de fichier pour les déploiements côte à côte | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- file extensions, registering for side-by-side
ms.assetid: 9ab046a2-147d-4167-aa14-7d661b1eaaa5
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 216fb4cc449e8a67178f587b0c199864d267ccf4
ms.lasthandoff: 02/22/2017

---
# <a name="registering-file-name-extensions-for-side-by-side-deployments"></a>L’inscription des Extensions de nom de fichier pour les déploiements côte à côte
Pour les VSPackages sont déployés dans un environnement côte à côte, vous devez inscrire des extensions de nom de fichier pour associer les fichiers de la version correcte de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Sauf si vous utilisez une extension de nom de fichier spécifique à la version, l’inscription permet aux utilisateurs d’ouvrir votre projet et élément les fichiers projet dans la version appropriée de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## <a name="in-this-section"></a>Dans cette section  
 [À propos des Extensions de nom de fichier](../extensibility/about-file-name-extensions.md)  
 Explique comment les extensions de nom de fichier sont enregistrées.  
  
 [Spécification des gestionnaires de fichiers pour les Extensions de nom de fichier](../extensibility/specifying-file-handlers-for-file-name-extensions.md)  
 Fournit des informations sur la façon d’inscrire les applications qui peuvent ouvrir, modifier et ainsi de suite, une extension de nom de fichier particulier.  
  
 [Inscription des verbes pour les Extensions de nom de fichier](../extensibility/registering-verbs-for-file-name-extensions.md)  
 Explique comment inscrire des verbes.  
  
 [La gestion des Associations de fichiers de côte à côte](../extensibility/managing-side-by-side-file-associations.md)  
 Explique comment gérer les installations côte à côte dans lequel une version particulière de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] doit être appelé pour ouvrir un fichier.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Prise en charge de plusieurs Versions de Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md)  
 Décrit les problèmes liés à plusieurs versions de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] et votre VSPackage lors du développement et de déploiement pour les utilisateurs finaux.
