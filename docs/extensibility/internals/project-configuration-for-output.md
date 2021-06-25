---
title: Configuration du projet pour la sortie | Microsoft Docs
description: Découvrez les processus de génération que chaque configuration peut prendre en charge, ainsi que les interfaces et les méthodes par lesquelles les éléments de sortie peuvent être mis à disposition.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- project configurations, output
ms.assetid: a4517f73-45af-4745-9d7f-9fddf887b636
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8b718e70bac0d9e09936daf743420acc04a1c4ad
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899873"
---
# <a name="project-configuration-for-output"></a>Configuration de projet pour la sortie
Chaque configuration peut prendre en charge un ensemble de processus de génération qui génèrent des éléments de sortie tels que des fichiers exécutables ou des fichiers de ressources. Ces éléments de sortie sont privés pour l’utilisateur et peuvent être placés dans des groupes qui lient des types de sortie associés tels que des fichiers exécutables (.exe, .dll,. lib) et des fichiers sources (fichiers. idl,. h).

 Les éléments de sortie peuvent être mis à disposition via les <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput2> méthodes et sont énumérés avec les <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumOutputs> méthodes. Lorsque vous souhaitez regrouper des éléments de sortie, votre projet doit également implémenter l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup> interface.

 La construction développée par l’implémentation de `IVsOutputGroup` permet aux projets de regrouper les sorties en fonction de leur utilisation. Par exemple, une DLL peut être regroupée avec sa base de données de programme (PDB).

> [!NOTE]
> Un fichier PDB contient des informations de débogage et il est créé lorsque l’option « générer des informations de débogage » est spécifiée lors de la génération du .dll ou .exe. Le fichier. pdb est généralement généré uniquement pour la configuration du projet de débogage.

 Le projet doit retourner le même nombre de groupes pour chaque configuration qu’il prend en charge, même si le nombre de sorties contenues dans un groupe peut varier de la configuration à la configuration. Par exemple, la DLL de Project Matt peut inclure des mattd.dll et matted. pdb dans la configuration Debug, mais incluez uniquement matt.dll dans la configuration de la vente au détail.

 Les groupes ont également les mêmes informations d’identificateur, telles que le nom canonique, le nom complet et les informations de groupe, de la configuration à la configuration au sein d’un projet. Cette cohérence permet au déploiement et à l’empaquetage de continuer à fonctionner même en cas de modification des configurations.

 Les groupes peuvent également avoir une sortie de clé qui permet aux raccourcis de Packaging de pointer vers un nom significatif. Tout groupe peut être vide dans une configuration donnée. par conséquent, aucune hypothèse ne doit être faite sur la taille d’un groupe. La taille (nombre de sorties) de chaque groupe dans une configuration quelconque peut être différente de la taille d’un autre groupe dans la même configuration. Elle peut également être différente de la taille du même groupe dans une autre configuration.

 ![Graphique des groupes de sorties](../../extensibility/internals/media/vsoutputgroups.gif "vsOutputGroups") Groupes de sorties

 La principale utilisation de l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg> interface consiste à fournir un accès pour générer, déployer et déboguer des objets de gestion et autoriser les projets à regrouper les sorties. Pour plus d’informations sur l’utilisation de cette interface, consultez [objet de configuration de projet](../../extensibility/internals/project-configuration-object.md).

 Dans le schéma précédent, le groupe généré a une sortie de clé entre les configurations (bD.exe ou b.exe), de sorte que l’utilisateur peut créer un raccourci pour générer et savoir que le raccourci fonctionne indépendamment de la configuration déployée. La source de groupe n’a pas de sortie de clé, de sorte que l’utilisateur ne peut pas créer de raccourci vers celle-ci. Si le groupe de débogage généré a une sortie de clé, mais pas le groupe de vente au détail créé, il s’agit d’une implémentation incorrecte. Ensuite, si une configuration a un groupe qui ne contient aucune sortie et, par conséquent, aucun fichier de clé, les autres configurations avec ce groupe qui contiennent des sorties ne peuvent pas avoir de fichiers de clé. Les éditeurs du programme d’installation supposent que les noms canoniques et les noms d’affichage des groupes, plus l’existence d’un fichier de clé, ne changent pas en fonction des configurations.

 Notez que si un projet possède un `IVsOutputGroup` qu’il ne souhaite pas empaqueter ou déployer, il suffit de ne pas placer cette sortie dans un groupe. La sortie peut toujours être énumérée normalement en implémentant la <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg.EnumOutputs%2A> méthode qui retourne toutes les sorties d’une configuration, quel que soit le regroupement.

 Pour plus d’informations, consultez l’implémentation de `IVsOutputGroup` dans l’exemple de projet personnalisé sur [MPF pour les projets](https://github.com/tunnelvisionlabs/MPFProj10).

## <a name="see-also"></a>Voir aussi
- [Gestion des options de configuration](../../extensibility/internals/managing-configuration-options.md)
- [Configuration de projet pour la création](../../extensibility/internals/project-configuration-for-building.md)
- [Objet de configuration de projet](../../extensibility/internals/project-configuration-object.md)
- [Configuration de la solution](../../extensibility/internals/solution-configuration.md)
