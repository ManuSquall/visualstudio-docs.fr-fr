---
title: Configuration pour la sortie de projet | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project configurations, output
ms.assetid: a4517f73-45af-4745-9d7f-9fddf887b636
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a2b3a4e904fa6ca45dc207c4b713577b1e29f840
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58952937"
---
# <a name="project-configuration-for-output"></a>Configuration de projet pour la sortie
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Chaque configuration peut prendre en charge un ensemble de processus de génération qui produisent des éléments de sortie tels que les fichiers exécutables ou des ressources. Ces éléments de sortie sont privés à l’utilisateur et peuvent être placés dans les groupes qui lient les types associés de sortie tels que des fichiers exécutables (.exe, .dll, .lib) et les fichiers sources (.idl, fichiers .h).  
  
 Éléments de sortie peuvent être rendues disponibles via le <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput2> méthodes et énumérée avec le <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumOutputs> méthodes. Lorsque vous souhaitez regrouper les éléments de sortie, votre projet doit également implémenter le <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup> interface.  
  
 La construction de développé en implémentant `IVsOutputGroup` permet aux projets de regrouper les sorties en fonction de l’utilisation. Par exemple, une DLL peut être regroupée avec sa base de données du programme (PDB).  
  
> [!NOTE]
>  Un fichier PDB contient des informations de débogage et il est créé lorsque l’option « Générer des informations de débogage » est spécifiée lors de la génération du fichier .dll ou .exe. Le fichier .pdb est généralement généré pour la configuration de projet de débogage uniquement.  
  
 Le projet doit retourner le même nombre de groupes pour chaque configuration pris en charge, même si le nombre de sorties contenues dans un groupe peut varier à partir d’une configuration à une configuration. Par exemple, Matt du projet DLL peut inclure des mattd.dll et mattd.pdb dans la configuration Debug, mais uniquement inclure matt.dll dans la configuration de la vente au détail.  
  
 Les groupes ont également les mêmes informations d’identificateur, comme le nom canonique, nom d’affichage et informations sur les groupes, à partir d’une configuration à une configuration au sein d’un projet. Cette cohérence permet le déploiement et empaquetage de continuer à fonctionner même si les configurations de modifier.  
  
 Groupes peuvent également avoir une sortie de clé qui permet des raccourcis d’empaquetage pointer vers quelque chose de significatif. N’importe quel groupe peut être vide dans une configuration donnée, donc aucune hypothèse ne doit être effectuée sur la taille d’un groupe. La taille (nombre de sorties) de chaque groupe dans n’importe quelle configuration peut être différente de la taille d’un autre groupe dans la même configuration. Il peut également être différente de la taille du même groupe dans une autre configuration.  
  
 ![Graphique de groupes de sortie](../../extensibility/internals/media/vsoutputgroups.gif "vsOutputGroups")  
Groupes de sortie  
  
 La principale utilisation de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg> interface consiste à fournir un accès pour générer, déployer et déboguer des objets de gestion et permettent aux projets à regrouper les sorties. Pour plus d’informations sur l’utilisation de cette interface, consultez [objet de Configuration de projet](../../extensibility/internals/project-configuration-object.md).  
  
 Dans le diagramme précédent, créé de groupe a une clé donc de sortie dans des configurations (bD.exe ou b.exe) à l’utilisateur peut créer un raccourci vers Built et savoir que le raccourci fonctionnera quel que soit la configuration déployée. Groupe Source n’a pas une clé de sortie, afin de l’utilisateur ne peut pas créer un raccourci vers celui-ci. Si le groupe créé déboguer est doté d’une clé, mais le groupe de vente au détail créé pas, qui est une implémentation incorrecte. Il en résulte, puis, que si aucune configuration dispose d’un groupe qui ne contient aucuns sorties, et, par conséquent, aucun fichier de clé, puis les autres configurations avec ce groupe qui contiennent les sorties ne peut pas avoir des fichiers de clés. Les éditeurs de programme d’installation partons du principe que les noms canoniques et les noms d’affichage des groupes, ainsi que l’existence d’un fichier de clé, ne changent pas en se basant sur les configurations.  
  
 Notez que si un projet a un `IVsOutputGroup` qu’il ne souhaite pas de package ou de déployer, il suffit ne pas placer cette sortie dans un groupe. La sortie peut toujours être énumérée normalement en implémentant la <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg.EnumOutputs%2A> méthode qui retourne toutes les sorties d’une configuration, quel que soit le regroupement.  
  
 Pour plus d’informations, consultez l’implémentation de `IVsOutputGroup` dans l’exemple de projet personnalisé à [MPF pour les projets](http://mpfproj12.codeplex.com).  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des Options de Configuration](../../extensibility/internals/managing-configuration-options.md)   
 [Configuration de projet pour la création](../../extensibility/internals/project-configuration-for-building.md)   
 [Objet de Configuration de projet](../../extensibility/internals/project-configuration-object.md)   
 [Configuration de la solution](../../extensibility/internals/solution-configuration.md)
