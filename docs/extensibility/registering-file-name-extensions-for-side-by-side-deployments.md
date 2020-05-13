---
title: Enregistrement des extensions de noms de fichiers pour les déploiements côte à côte ( Microsoft Docs
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
ms.openlocfilehash: 6717625a44b48a25d293f68d01cd9fa3c7c24853
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701542"
---
# <a name="register-file-name-extensions-for-side-by-side-deployments"></a>Enregistrer les extensions de noms de fichiers pour les déploiements côte à côte
Pour vsPackages déployés dans un environnement côte à côte, vous devez enregistrer des extensions de nom de fichier pour associer les fichiers à la version correcte de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Sauf si vous utilisez une extension de nom de fichier spécifique à la version, l’enregistrement permet aux utilisateurs d’ouvrir vos fichiers de projet et d’élément de projet dans la version appropriée de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

## <a name="in-this-section"></a>Contenu de cette section
- [À propos des extensions de nom de fichier](../extensibility/about-file-name-extensions.md) Discute de la façon dont les extensions de nom de fichier sont enregistrées.

- [Spécifier les gestionnaires de fichiers pour les extensions de nom de fichier](../extensibility/specifying-file-handlers-for-file-name-extensions.md) Fournit des informations sur la façon d’enregistrer les applications qui peuvent ouvrir, modifier, et ainsi de suite, une extension particulière de nom de fichier.

- [Enregistrer les verbes pour les extensions de nom de fichier](../extensibility/registering-verbs-for-file-name-extensions.md) Discute de la façon d’enregistrer les verbes.

- [Gérer les associations de fichiers côte à côte](../extensibility/managing-side-by-side-file-associations.md) Discute de la façon de gérer les installations [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] côte à côte dans lesquelles une version particulière de devrait être invoquée pour ouvrir un fichier.

## <a name="related-sections"></a>Sections connexes
- [Prendre en charge plusieurs versions de Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md) Décrit les problèmes liés à [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] plusieurs versions et à votre VSPackage pendant le développement et le déploiement aux utilisateurs finaux.
