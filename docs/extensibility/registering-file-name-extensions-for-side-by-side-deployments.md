---
title: Inscrire des extensions de nom de fichier pour les IDE côte à côte
description: En savoir plus sur l’inscription des extensions de nom de fichier pour les déploiements côte à côte, ce qui permet aux utilisateurs d’ouvrir des fichiers dans la version appropriée de Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- file extensions, registering for side-by-side
ms.assetid: 9ab046a2-147d-4167-aa14-7d661b1eaaa5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ad6b5715b767729715403d064cd46b4556fa17e3
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105056556"
---
# <a name="register-file-name-extensions-for-side-by-side-deployments"></a>Inscrire des extensions de nom de fichier pour les déploiements côte à côte
Pour les VSPackages déployés dans un environnement côte à côte, vous devez inscrire les extensions de nom de fichier pour associer les fichiers à la version correcte de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . À moins que vous n’utilisiez une extension de nom de fichier spécifique à la version, l’inscription permet aux utilisateurs d’ouvrir vos fichiers de projet et d’élément de projet dans la version appropriée de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

## <a name="in-this-section"></a>Dans cette section
- [À propos des extensions de nom de fichier](../extensibility/about-file-name-extensions.md) Explique comment les extensions de nom de fichier sont inscrites.

- [Spécifier des gestionnaires de fichiers pour les extensions de nom de fichier](../extensibility/specifying-file-handlers-for-file-name-extensions.md) Fournit des informations sur l’inscription des applications qui peuvent ouvrir, modifier, etc., une extension de nom de fichier particulière.

- [Verbes Register pour les extensions de nom de fichier](../extensibility/registering-verbs-for-file-name-extensions.md) Explique comment inscrire des verbes.

- [Gérer les associations de fichiers côte à côte](../extensibility/managing-side-by-side-file-associations.md) Explique comment gérer des installations côte à côte dans lesquelles une version particulière de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] doit être appelée pour ouvrir un fichier.

## <a name="related-sections"></a>Sections connexes
- [Prendre en charge plusieurs versions de Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md) Décrit les problèmes liés à plusieurs versions de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] et à votre VSPackage lors du développement et du déploiement pour les utilisateurs finaux.
