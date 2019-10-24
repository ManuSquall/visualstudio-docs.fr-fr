---
title: Configuration du projet pour la sortie | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project configurations, output
ms.assetid: a4517f73-45af-4745-9d7f-9fddf887b636
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8b6337d82e51cf728d69f7aabb46e9d4444ec564
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72725893"
---
# <a name="project-configuration-for-output"></a>Configuration de projet pour la sortie
Chaque configuration peut prendre en charge un ensemble de processus de génération qui génèrent des éléments de sortie tels que des fichiers exécutables ou des fichiers de ressources. Ces éléments de sortie sont privés pour l’utilisateur et peuvent être placés dans des groupes qui lient des types de sortie associés tels que des fichiers exécutables (. exe,. dll,. lib) et des fichiers sources (fichiers. idl,. h).

 Les éléments de sortie peuvent être mis à disposition par le biais des méthodes <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput2> et sont énumérés avec les méthodes <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumOutputs>. Lorsque vous souhaitez regrouper des éléments de sortie, votre projet doit également implémenter l’interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup>.

 La construction développée par l’implémentation de `IVsOutputGroup` permet aux projets de regrouper les sorties en fonction de leur utilisation. Par exemple, une DLL peut être regroupée avec sa base de données de programme (PDB).

> [!NOTE]
> Un fichier PDB contient des informations de débogage et il est créé lorsque l’option « générer des informations de débogage » est spécifiée lors de la génération du fichier. dll ou. exe. Le fichier. pdb est généralement généré uniquement pour la configuration du projet de débogage.

 Le projet doit retourner le même nombre de groupes pour chaque configuration qu’il prend en charge, même si le nombre de sorties contenues dans un groupe peut varier de la configuration à la configuration. Par exemple, la DLL du projet Matt peut inclure le fichier Cached. dll et le fichier Cached. pdb dans la configuration de débogage, mais inclut uniquement Matt. dll dans la configuration de la vente au détail.

 Les groupes ont également les mêmes informations d’identificateur, telles que le nom canonique, le nom complet et les informations de groupe, de la configuration à la configuration au sein d’un projet. Cette cohérence permet au déploiement et à l’empaquetage de continuer à fonctionner même en cas de modification des configurations.

 Les groupes peuvent également avoir une sortie de clé qui permet aux raccourcis de Packaging de pointer vers un nom significatif. Tout groupe peut être vide dans une configuration donnée. par conséquent, aucune hypothèse ne doit être faite sur la taille d’un groupe. La taille (nombre de sorties) de chaque groupe dans une configuration quelconque peut être différente de la taille d’un autre groupe dans la même configuration. Elle peut également être différente de la taille du même groupe dans une autre configuration.

 ![Graphique des groupes de sorties](../../extensibility/internals/media/vsoutputgroups.gif "vsOutputGroups") Groupes de sorties

 La principale utilisation de l’interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg> consiste à fournir un accès pour générer, déployer et déboguer des objets de gestion et autoriser les projets à regrouper les sorties. Pour plus d’informations sur l’utilisation de cette interface, consultez [objet de configuration de projet](../../extensibility/internals/project-configuration-object.md).

 Dans le schéma précédent, le groupe généré a une sortie de clé entre les différentes configurations (bD. exe ou b. exe), de sorte que l’utilisateur peut créer un raccourci pour générer et savoir que le raccourci fonctionnera quelle que soit la configuration déployée. La source de groupe n’a pas de sortie de clé, de sorte que l’utilisateur ne peut pas créer de raccourci vers celle-ci. Si le groupe de débogage généré a une sortie de clé, mais pas le groupe de vente au détail créé, il s’agit d’une implémentation incorrecte. Ensuite, si une configuration a un groupe qui ne contient aucune sortie et, par conséquent, aucun fichier de clé, les autres configurations avec ce groupe qui contiennent des sorties ne peuvent pas avoir de fichiers de clé. Les éditeurs du programme d’installation supposent que les noms canoniques et les noms d’affichage des groupes, plus l’existence d’un fichier de clé, ne changent pas en fonction des configurations.

 Notez que si un projet a un `IVsOutputGroup` qu’il ne souhaite pas empaqueter ou déployer, il suffit de ne pas placer cette sortie dans un groupe. La sortie peut toujours être énumérée normalement en implémentant la méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg.EnumOutputs%2A> qui retourne toutes les sorties d’une configuration, quel que soit le regroupement.

 Pour plus d’informations, consultez l’implémentation de `IVsOutputGroup` dans l’exemple de projet personnalisé sur [MPF pour les projets](https://github.com/tunnelvisionlabs/MPFProj10).

## <a name="see-also"></a>Voir aussi
- [Gestion des options de configuration](../../extensibility/internals/managing-configuration-options.md)
- [Configuration de projet pour la création](../../extensibility/internals/project-configuration-for-building.md)
- [Objet de configuration de projet](../../extensibility/internals/project-configuration-object.md)
- [Configuration de la solution](../../extensibility/internals/solution-configuration.md)