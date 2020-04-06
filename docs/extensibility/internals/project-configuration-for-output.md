---
title: Configuration du projet pour la sortie (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project configurations, output
ms.assetid: a4517f73-45af-4745-9d7f-9fddf887b636
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 78b95457af4c5d806fdfcc20f49ac4e82df36488
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706669"
---
# <a name="project-configuration-for-output"></a>Configuration de projet pour la sortie
Chaque configuration peut prendre en charge un ensemble de processus de construction qui produisent des éléments de sortie tels que des fichiers exécutables ou des fichiers de ressources. Ces éléments de sortie sont privés de l’utilisateur et peuvent être placés dans des groupes qui lient les types de sortie connexes tels que les fichiers exécutables (.exe, .dll, .lib) et les fichiers source (.idl, .h fichiers).

 Les articles de sortie <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput2> peuvent être mis à <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumOutputs> disposition par les méthodes et énumérés avec les méthodes. Lorsque vous souhaitez regrouper les éléments de <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup> sortie, votre projet doit également implémenter l’interface.

 La construction développée `IVsOutputGroup` par la mise en œuvre permet aux projets de regrouper les extrants en fonction de l’utilisation. Par exemple, un DLL peut être regroupé avec sa base de données de programme (PDB).

> [!NOTE]
> Un fichier PDB contient des informations de débogage et il est créé lorsque l’option 'Generate Debug Info' est spécifiée lors de la construction de la .dll ou .exe. Le fichier .pdb est généralement généré uniquement pour la configuration du projet Debug.

 Le projet doit retourner le même nombre de groupes pour chaque configuration qu’il prend en charge, même si le nombre de sorties contenues dans un groupe peut varier d’une configuration à l’autre. Par exemple, le projet Matt’s DLL peut inclure mattd.dll et mattd.pdb dans la configuration Debug, mais seulement inclure matt.dll dans la configuration Retail.

 Les groupes disposent également des mêmes informations d’identification, telles que le nom canonique, le nom d’affichage et les informations de groupe, de la configuration à la configuration au sein d’un projet. Cette cohérence permet au déploiement et à l’emballage de continuer à fonctionner même si les configurations changent.

 Les groupes peuvent également avoir une sortie clé qui permet aux raccourcis d’emballage de pointer vers quelque chose de significatif. N’importe quel groupe peut être vide dans une configuration donnée, donc aucune hypothèse ne doit être faite sur la taille d’un groupe. La taille (nombre de sorties) de chaque groupe dans n’importe quelle configuration peut être différente de la taille d’un autre groupe dans la même configuration. Il peut également être différent de la taille d’un même groupe dans une autre configuration.

 ![Graphique des groupes de sortie](../../extensibility/internals/media/vsoutputgroups.gif "vsOutputGroups (en anglais)") Groupes de production

 L’utilisation principale <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg> de l’interface est de fournir l’accès à la construction, le déploiement et le débogé d’objets de gestion et de permettre aux projets la liberté de regrouper les sorties. Pour plus d’informations sur l’utilisation de cette interface, voir [Project Configuration Object](../../extensibility/internals/project-configuration-object.md).

 Dans le diagramme précédent, Group Built a une sortie clé à travers les configurations (soit bD.exe ou b.exe) de sorte que l’utilisateur peut créer un raccourci à Construit et savoir que le raccourci fonctionnera indépendamment de la configuration déployée. Source de groupe n’a pas de sortie clé, de sorte que l’utilisateur ne peut pas créer un raccourci à elle. Si le groupe Debug Construit a une production clé, mais le groupe de détail construit ne le fait pas, ce serait une implémentation incorrecte. Il s’ensuit donc que si une configuration a un groupe qui ne contient pas de sorties, et, par conséquent, aucun fichier clé, alors d’autres configurations avec ce groupe qui contiennent des sorties ne peuvent pas avoir des fichiers clés. Les éditeurs d’installateurs supposent que les noms canoniques et les noms d’affichage des groupes, ainsi que l’existence d’un fichier clé, ne changent pas en fonction des configurations.

 Notez que si `IVsOutputGroup` un projet a un projet qu’il ne veut pas emballer ou déployer, il suffit de ne pas mettre cette sortie dans un groupe. La sortie peut encore être énumérée normalement <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg.EnumOutputs%2A> en implémentant la méthode qui renvoie toutes les sorties d’une configuration indépendamment du groupement.

 Pour plus d’informations, `IVsOutputGroup` voir la mise en œuvre de l’échantillon du projet personnalisé au [MPF pour les projets](https://github.com/tunnelvisionlabs/MPFProj10).

## <a name="see-also"></a>Voir aussi
- [Gestion des options de configuration](../../extensibility/internals/managing-configuration-options.md)
- [Configuration de projet pour la création](../../extensibility/internals/project-configuration-for-building.md)
- [Objet de configuration de projet](../../extensibility/internals/project-configuration-object.md)
- [Configuration de la solution](../../extensibility/internals/solution-configuration.md)
