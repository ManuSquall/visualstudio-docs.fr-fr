---
title: L’inscription des Extensions de nom de fichier pour les déploiements côte à côte | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- file extensions, registering for side-by-side
ms.assetid: 9ab046a2-147d-4167-aa14-7d661b1eaaa5
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 996f911f37b8226065feb4da311f736dd910550b
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56709965"
---
# <a name="register-file-name-extensions-for-side-by-side-deployments"></a>Inscrire des extensions de nom de fichier pour les déploiements côte à côte
Pour les VSPackages déployés dans un environnement côte à côte, vous devez inscrire des extensions de nom de fichier pour associer les fichiers à la version correcte du [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Sauf si vous utilisez une extension de nom de fichier spécifique à la version, l’inscription permet aux utilisateurs d’ouvrir votre projet et d’élément les fichiers projet dans la version appropriée de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

## <a name="in-this-section"></a>Dans cette section
- [À propos des extensions de nom de fichier](../extensibility/about-file-name-extensions.md) aborde la manière dont les extensions de nom de fichier sont inscrites.

- [Spécifier des gestionnaires de fichier pour les extensions de nom de fichier](../extensibility/specifying-file-handlers-for-file-name-extensions.md) fournit des informations sur comment inscrire les applications que vous peuvent ouvrir, modifier et ainsi de suite, une extension de nom de fichier particulier.

- [Inscrire des verbes pour les extensions de nom de fichier](../extensibility/registering-verbs-for-file-name-extensions.md) explique comment inscrire des verbes.

- [Gérer les associations de fichiers de côte à côte](../extensibility/managing-side-by-side-file-associations.md) explique comment gérer des installations côte à côte dans lequel une version particulière de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] doit être appelé pour ouvrir un fichier.

## <a name="related-sections"></a>Rubriques connexes
- [Prend en charge plusieurs versions de Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md) décrit les problèmes liés à plusieurs versions de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] et votre VSPackage lors du développement et de déploiement pour les utilisateurs finaux.