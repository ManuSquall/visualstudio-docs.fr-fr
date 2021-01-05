---
title: Inscrire des extensions de nom de fichier pour les IDE côte à côte
description: En savoir plus sur l’inscription des extensions de nom de fichier pour les déploiements côte à côte, ce qui permet aux utilisateurs d’ouvrir des fichiers dans la version appropriée de Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- file extensions, registering for side-by-side
ms.assetid: 9ab046a2-147d-4167-aa14-7d661b1eaaa5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c66413890f0aaa08e09a291f5bf31a44e7c24706
ms.sourcegitcommit: dd96a95d87a039525aac86abe689c30e2073ae87
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/04/2021
ms.locfileid: "97863026"
---
# <a name="register-file-name-extensions-for-side-by-side-deployments"></a>Inscrire des extensions de nom de fichier pour les déploiements côte à côte
Pour les VSPackages déployés dans un environnement côte à côte, vous devez inscrire les extensions de nom de fichier pour associer les fichiers à la version correcte de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . À moins que vous n’utilisiez une extension de nom de fichier spécifique à la version, l’inscription permet aux utilisateurs d’ouvrir vos fichiers de projet et d’élément de projet dans la version appropriée de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

## <a name="in-this-section"></a>Contenu de cette section
- [À propos des extensions de nom de fichier](../extensibility/about-file-name-extensions.md) Explique comment les extensions de nom de fichier sont inscrites.

- [Spécifier des gestionnaires de fichiers pour les extensions de nom de fichier](../extensibility/specifying-file-handlers-for-file-name-extensions.md) Fournit des informations sur l’inscription des applications qui peuvent ouvrir, modifier, etc., une extension de nom de fichier particulière.

- [Verbes Register pour les extensions de nom de fichier](../extensibility/registering-verbs-for-file-name-extensions.md) Explique comment inscrire des verbes.

- [Gérer les associations de fichiers côte à côte](../extensibility/managing-side-by-side-file-associations.md) Explique comment gérer des installations côte à côte dans lesquelles une version particulière de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] doit être appelée pour ouvrir un fichier.

## <a name="related-sections"></a>Sections connexes
- [Prendre en charge plusieurs versions de Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md) Décrit les problèmes liés à plusieurs versions de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] et à votre VSPackage lors du développement et du déploiement pour les utilisateurs finaux.
