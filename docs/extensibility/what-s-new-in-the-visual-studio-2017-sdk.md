---
title: Ce que&#39;nouveauté dans le Kit de développement logiciel Visual Studio 2017 | Documents Microsoft
ms.custom: ''
ms.date: 10/31/2017
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 9efcf0a3-dbde-4cab-8ed3-425826a48b2e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: abc1f12a5a6c7368bc47e8f4e924d109dcf87f57
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="what39s-new-in-the-visual-studio-2017-sdk"></a>Ce que&#39;nouveauté dans le Kit de développement logiciel Visual Studio 2017

Le Kit de développement logiciel Visual Studio a les fonctionnalités nouvelles et mises à jour suivantes pour Visual Studio 2017.

## <a name="vsix-v3-format"></a>Format VSIX v3

Pour prendre en charge la nouvelle installation léger de Visual Studio 2017, le format de manifeste VSIX extension a été mis à jour vers la version 3 (v3 VSIX).

Le nouveau format en charge :

* Déclaration explicite des composants requis pour être détecté et installé par le VSIXInstaller.
* Assemblys Ngen'ing sur l’installation de l’extension.
* Lors de l’installation des ressources en dehors de la racine de l’extension habituel.

Pour en savoir plus sur ces modifications, consultez les rubriques suivantes :

* [Les modifications apportées à l’extensibilité pour 2017](breaking-changes-2017.md)
* [Prise en charge de Ngen dans VSIX v3](ngen-support.md)
* [Installation en dehors du dossier d’extensions](set-install-root.md)
* [Forum aux Questions pour l’extensibilité de Visual Studio 2017](faq-2017.md)

## <a name="migrating-extensibility-project-to-visual-studio-2017"></a>Migration de projet d’extensibilité pour Visual Studio 2017

Pour savoir comment mettre à jour vos projets d’extensibilité et leur manifeste VSIX pour Visual Studio 2017, consultez [Comment : migrer les projets d’extensibilité pour Visual Studio 2017](how-to-migrate-extensibility-projects-to-visual-studio-2017.md).

## <a name="custom-project-and-item-templates"></a>Modèles de projet et d’élément personnalisés

À partir de Visual Studio 2017, l’analyse des modèles de projets et modèles d’élément sera n’est plus effectuée. Au lieu de cela, l’extension doit fournir les fichiers de manifeste de modèle qui décrivent l’emplacement d’installation de ces modèles. Vous pouvez utiliser Visual Studio 2017 pour mettre à jour vos extensions VSIX. Si vous déployez votre extension à l’aide d’un fichier MSI, vous devez générer les fichiers manifeste de modèle à la main. Pour plus d’informations, consultez [mise à niveau des projets et des modèles d’élément pour Visual Studio 2017](../extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017.md). Le schéma de modèle de manifeste est documenté dans [Visual Studio Template manifeste Schema Reference](../extensibility/visual-studio-template-manifest-schema-reference.md).

## <a name="updated-extension-performance-guidelines"></a>Recommandations relatives aux performances de mise à jour d’Extension

Il existe un nouveau [Comment : diagnostiquer les performances de l’extension](how-to-diagnose-extension-performance.md) rubrique sous [la gestion des VSPackages](managing-vspackages.md) pour montrer comment détecter et analyser l’impact d’extension de Visual Studio solution et démarrage du temps de chargement.
