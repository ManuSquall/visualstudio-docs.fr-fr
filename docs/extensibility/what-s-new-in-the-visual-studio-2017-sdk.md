---
title: Nouveautés &apos; du kit de développement logiciel (SDK) Visual Studio 2017 | Microsoft Docs
ms.date: 10/31/2017
ms.topic: conceptual
ms.assetid: 9efcf0a3-dbde-4cab-8ed3-425826a48b2e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6fb5b81341f8184d713755b3b934fbae4c8031b1
ms.sourcegitcommit: de98ed7edc81383e47b87ae6e61143fbbbe7bc56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2020
ms.locfileid: "88711597"
---
# <a name="what39s-new-in-the-visual-studio-2017-sdk"></a>&#39;nouveautés du kit de développement logiciel (SDK) Visual Studio 2017

Le kit de développement logiciel (SDK) Visual Studio propose les fonctionnalités nouvelles et mises à jour suivantes pour Visual Studio 2017.

## <a name="vsix-v3-format"></a>Format VSIX v3

Pour prendre en charge la nouvelle installation légère de Visual Studio 2017, le format de manifeste de l’extension VSIX a été mis à jour vers la version 3 (VSIX v3).

Le nouveau format prend en charge :

* Déclaration explicite des conditions préalables à détecter et à installer par le VSIXInstaller.
* Assemblys Ngen sur l’installation de l’extension.
* Installation des ressources en dehors de la racine d’extension habituelle.

Pour en savoir plus sur ces modifications, consultez les rubriques suivantes :

* [Modifications apportées à l’extensibilité pour Visual Studio 2017](breaking-changes-2017.md)
* [Prise en charge de Ngen dans VSIX v3](ngen-support.md)
* [Installer en dehors du dossier d’extensions](set-install-root.md)
* [Forum aux questions sur l’extensibilité de Visual Studio 2017](faq-2017.md)

## <a name="migrate-extensibility-project-to-visual-studio-2017"></a>Migrer le projet d’extensibilité vers Visual Studio 2017

Pour savoir comment mettre à jour vos projets d’extensibilité et leurs manifestes VSIX vers Visual Studio 2017, consultez Guide pratique [pour migrer des projets d’extensibilité vers Visual studio 2017](how-to-migrate-extensibility-projects-to-visual-studio-2017.md).

## <a name="custom-project-and-item-templates"></a>Modèles de projet et d’élément personnalisés

À compter de Visual Studio 2017, l’analyse des modèles de projet et d’élément personnalisés ne sera plus effectuée. Au lieu de cela, l’extension doit fournir des fichiers manifestes de modèle qui décrivent l’emplacement d’installation de ces modèles. Vous pouvez utiliser Visual Studio 2017 pour mettre à jour vos extensions VSIX. Si vous déployez votre extension à l’aide d’un MSI, vous devez générer manuellement les fichiers manifeste de modèle. Pour plus d’informations, consultez [mettre à niveau les modèles de projet et d’élément personnalisés pour Visual Studio 2017](../extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017.md). Le schéma de manifeste de modèle est documenté dans [référence de schéma du manifeste de modèle Visual Studio](../extensibility/visual-studio-template-manifest-schema-reference.md).

## <a name="updated-extension-performance-guidelines"></a>Règles de performance des extensions mises à jour

Il existe une nouvelle [procédure : diagnostiquer les performances des extensions](how-to-diagnose-extension-performance.md) sous [gérer les VSPackages](managing-vspackages.md) pour montrer comment détecter et analyser l’impact des extensions sur le démarrage de Visual Studio et les temps de chargement de la solution.
