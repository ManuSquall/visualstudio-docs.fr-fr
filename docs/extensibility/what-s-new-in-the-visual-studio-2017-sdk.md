---
title: Qu’est-ce&#39;nouveau dans le Studio Visuel 2017 SDK (fr) Microsoft Docs
ms.date: 10/31/2017
ms.topic: conceptual
ms.assetid: 9efcf0a3-dbde-4cab-8ed3-425826a48b2e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 88330aa68f2a3752431fd2fbe6c5c1c649acbb8b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697207"
---
# <a name="what39s-new-in-the-visual-studio-2017-sdk"></a>Qu’est-ce&#39;nouveau dans le Studio Visuel 2017 SDK

Le Visual Studio SDK a les fonctionnalités nouvelles et mises à jour suivantes pour Visual Studio 2017.

## <a name="vsix-v3-format"></a>Format VSIX v3

Pour soutenir la nouvelle installation légère de Visual Studio 2017, le format manifeste d’extension VSIX a été mis à jour à la version 3 (VSIX v3).

Le nouveau format a un support pour :

* Déclarer explicitement les conditions préalables à détecter et à installer par le VSIXInstaller.
* Assemblages Ngen sur l’installation d’extension.
* Installation d’actifs en dehors de la racine d’extension habituelle.

Pour en savoir plus sur ces changements, consultez les sujets suivants :

* [Changements à l’extensibility pour Visual Studio 2017](breaking-changes-2017.md)
* [Prise en charge de Ngen dans VSIX v3](ngen-support.md)
* [Installer en dehors du dossier d’extensions](set-install-root.md)
* [Questions fréquemment posées pour Visual Studio 2017 extensibility](faq-2017.md)

## <a name="migrate-extensibility-project-to-visual-studio-2017"></a>Projet d’extensibility De Migration à Visual Studio 2017

Pour apprendre à mettre à jour vos projets d’extensibility et leurs manifestes VSIX à Visual Studio 2017, voir [Comment : Migrer les projets d’extensibility à Visual Studio 2017](how-to-migrate-extensibility-projects-to-visual-studio-2017.md).

## <a name="custom-project-and-item-templates"></a>Modèles de projet et d’objets personnalisés

À partir de Visual Studio 2017, la numérisation des modèles de projets et d’objets personnalisés ne sera plus effectuée. Au lieu de cela, l’extension doit fournir des fichiers manifestes modèle qui décrivent l’emplacement d’installation de ces modèles. Vous pouvez utiliser Visual Studio 2017 pour mettre à jour vos extensions VSIX. Si vous déployez votre extension à l’aide d’un MSI, vous devez générer les fichiers manifestes de modèle à la main. Pour plus d’informations, consultez [les modèles de projets et d’objets personnalisés Upgrade pour Visual Studio 2017](../extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017.md). Le schéma manifeste de modèle est documenté dans [visual Studio modèle de référence manifeste schéma](../extensibility/visual-studio-template-manifest-schema-reference.md).

## <a name="updated-extension-performance-guidelines"></a>Mise à jour des lignes directrices sur le rendement des extensions

Il ya un nouveau [Comment: Diagnostiquer l’article de performance d’extension](how-to-diagnose-extension-performance.md) sous [Gérer VSPackages](managing-vspackages.md) pour montrer comment détecter et analyser l’impact d’extension sur le démarrage Visual Studio et les temps de chargement de solution.
