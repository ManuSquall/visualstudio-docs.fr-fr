---
title: "Quelles sont les nouveautés dans le Kit de développement logiciel Visual Studio 2017 | Documents Microsoft"
ms.custom: 
ms.date: 11/09/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9efcf0a3-dbde-4cab-8ed3-425826a48b2e
caps.latest.revision: 1
author: gregvanl
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
ms.sourcegitcommit: 221f4911981deec0330f76a82c0cc8a1b968e56e
ms.openlocfilehash: 60898d7cace1c10006436a8d98cbd7f7628cf972
ms.lasthandoff: 02/22/2017

---
# <a name="what39s-new-in-the-visual-studio-2017-sdk"></a>Quelles sont les nouveautés dans le Kit de développement logiciel Visual Studio 2017

>**Remarque :** cette documentation est préliminaire et en fonction de la version de Visual Studio 2017 RC.

Le Kit de développement logiciel Visual Studio propose les fonctionnalités suivantes de nouvelle et mis à jour pour Visual Studio 2017.

## <a name="vsix-v3-format"></a>Format de v3 VSIX

Pour prendre en charge les nouvelles installations de Visual Studio 2017 léger, le format de manifeste VSIX extension a été mis à jour vers la version 3 (v3 VSIX).

Le nouveau format prend en charge :

* Déclarer explicitement les conditions requises pour être détecté et installé par le VSIXInstaller.
* Assemblys Ngen'ing sur l’installation de l’extension.
* Installation des ressources en dehors de la racine d’extension habituel.

Pour en savoir plus sur ces modifications, consultez les rubriques suivantes :

* [Les modifications apportées à l’extensibilité pour 2017](breaking-changes-2017.md)
* [Prise en charge de NGen dans VSIX v3](ngen-support.md)
* [L’installation en dehors du dossier extensions](set-install-root.md)
* [Forum aux Questions pour l’extensibilité de Visual Studio 2017](faq-2017.md)

## <a name="migrating-extensibility-project-to-visual-studio-2017"></a>Migration de projet d’extensibilité pour Visual Studio 2017

Pour savoir comment mettre à jour vos projets d’extensibilité et leur manifeste VSIX à Visual Studio 2017, consultez [Comment : migrer les projets d’extensibilité pour Visual Studio 2017](how-to-migrate-extensibility-projects-to-visual-studio-2017.md).

## <a name="lightweight-solution-load-lsl"></a>Charge une Solution légère (LSL)

Charge de Solution légère est une nouvelle fonctionnalité de 2017 VS qui réduit considérablement le temps de charge Solution, ce qui vous permet d’être plus productifs plus rapidement. Lorsque LSL est activée, Visual Studio entièrement ne chargera pas les projets jusqu'à ce que vous commencerez à les utiliser.

LSL peut avoir un impact extensions Visual Studio. Extensions dont les fonctions dépendent d’un projet en cours de chargement complet ne peuvent pas fonctionne ou mal fonctionner. Consultez la page [Lightweight Solution charge](lightweight-solution-load-extension-impact.md) pour savoir si votre extension peuvent être réduites et obtenez des conseils sur la mise à jour de votre extension.

## <a name="custom-project-and-item-templates"></a>Modèles de projet et d’élément personnalisés

À partir de Visual Studio 2017, l’analyse des modèles d’élément et de projet personnalisé sera n’est plus effectuée. Au lieu de cela, l’extension doit fournir les fichiers de manifeste de modèle qui décrivent l’emplacement d’installation de ces modèles. Vous pouvez utiliser Visual Studio 2017 pour mettre à jour vos extensions VSIX. Si vous déployez votre extension à l’aide d’un fichier MSI, vous devez générer manuellement les fichiers manifeste de modèle. Pour plus d’informations, consultez [la mise à niveau un projet personnalisé et des modèles d’élément pour Visual Studio 2017](../extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017.md). Le schéma de manifeste de modèle est documenté dans [Visual Studio Template manifeste Schema Reference](../extensibility/visual-studio-template-manifest-schema-reference.md).

## <a name="updated-extension-performance-guidelines"></a>Recommandations relatives aux performances de mise à jour d’Extension

Un nouveau [Comment : diagnostiquer les performances de l’extension](how-to-diagnose-extension-performance.md) rubrique sous [la gestion de packages VS](managing-vspackages.md) pour montrer comment détecter et analyser l’impact d’extension de Visual Studio solution et démarrage du temps de chargement.

