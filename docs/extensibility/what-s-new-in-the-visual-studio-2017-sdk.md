---
title: Ce que&#39;s dans le Kit de développement logiciel Visual Studio 2017 | Microsoft Docs
ms.date: 10/31/2017
ms.topic: conceptual
ms.assetid: 9efcf0a3-dbde-4cab-8ed3-425826a48b2e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e3d149a7cec711e59909ff21944ed52e3c074113
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56710173"
---
# <a name="what39s-new-in-the-visual-studio-2017-sdk"></a>Ce que&#39;s dans le Kit de développement logiciel Visual Studio 2017

Le SDK Visual Studio a les fonctionnalités nouvelles et mises à jour suivantes pour Visual Studio 2017.

## <a name="vsix-v3-format"></a>Format VSIX v3

Pour prendre en charge la nouvelle installation de légères de Visual Studio 2017, le format de manifeste d’extension VSIX a été mis à jour vers la version 3 (v3 VSIX).

Le nouveau format prend en charge :

* Déclarer explicitement les conditions requises pour être détectée et installée par le VSIXInstaller.
* Assemblys Ngen sur l’installation de l’extension.
* Installation des ressources en dehors de la racine d’extension habituel.

Pour en savoir plus sur ces modifications, consultez les rubriques suivantes :

* [Modifications apportées à l’extensibilité pour 2017](breaking-changes-2017.md)
* [Prise en charge de Ngen dans VSIX v3](ngen-support.md)
* [Installer en dehors du dossier d’extensions](set-install-root.md)
* [Forum aux questions pour l’extensibilité de Visual Studio 2017](faq-2017.md)

## <a name="migrate-extensibility-project-to-visual-studio-2017"></a>Migrer un projet d’extensibilité vers Visual Studio 2017

Pour savoir comment mettre à jour vos projets d’extensibilité et leur manifeste VSIX pour Visual Studio 2017, consultez [Comment : Migrer des projets d’extensibilité vers Visual Studio 2017](how-to-migrate-extensibility-projects-to-visual-studio-2017.md).

## <a name="custom-project-and-item-templates"></a>Modèles de projet et d’élément personnalisés

À partir de Visual Studio 2017, l’analyse pour les modèles de projets et modèles d’élément est n’est plus effectuée. Au lieu de cela, l’extension doit fournir les fichiers de manifeste de modèle qui décrivent l’emplacement d’installation de ces modèles. Vous pouvez utiliser Visual Studio 2017 pour mettre à jour vos extensions VSIX. Si vous déployez votre extension à l’aide d’un fichier MSI, vous devez générer manuellement les fichiers manifeste de modèle. Pour plus d’informations, consultez [mise à niveau des modèles de projet et d’élément personnalisés pour Visual Studio 2017](../extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017.md). Le schéma de manifeste de modèle est documenté dans [référence de schéma de manifeste de modèle Visual Studio](../extensibility/visual-studio-template-manifest-schema-reference.md).

## <a name="updated-extension-performance-guidelines"></a>Instructions relatives aux performances de mise à jour d’extension

Il existe un nouveau [Comment : Diagnostiquer les performances de l’extension](how-to-diagnose-extension-performance.md) article sous [gérer les VSPackages](managing-vspackages.md) de montrer comment détecter et analyser l’impact de l’extension de Visual Studio solution et démarrage les temps de chargement.
