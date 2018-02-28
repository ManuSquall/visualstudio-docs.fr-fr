---
title: Configuration pour la sortie de projet | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project configurations, output
ms.assetid: a4517f73-45af-4745-9d7f-9fddf887b636
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 4f3927ac9aa9e85be026d2b9a2af1c0c4d956c9f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="project-configuration-for-output"></a>Configuration de projet pour la sortie
Chaque configuration peut prendre en charge un ensemble de processus de génération qui produisent des éléments de sortie tels que les fichiers exécutables ou des ressources. Ces éléments de sortie sont privés à l’utilisateur et peuvent être placées dans des groupes qui lient les types de sortie, tels que des fichiers exécutables (.exe, .dll, .lib) et les fichiers sources (.idl, les fichiers .h).  
  
 Éléments de sortie peuvent être rendues disponibles via le <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput2> méthodes et énumérées avec la <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumOutputs> méthodes. Lorsque vous souhaitez regrouper les éléments de sortie, votre projet doit également implémenter le <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup> interface.  
  
 La construction de développé en implémentant `IVsOutputGroup` permet aux projets de sorties de groupe en fonction de l’utilisation. Par exemple, une DLL peut être regroupée avec sa base de données du programme (PDB).  
  
> [!NOTE]
>  Un fichier PDB contient des informations de débogage et il est créé lorsque l’option « Générer des informations de débogage » est spécifiée lors de la génération du fichier .dll ou .exe. Le fichier .pdb est généralement généré pour la configuration de projet Debug uniquement.  
  
 Le projet doit retourner le même nombre de groupes pour chaque configuration pris en charge, même si le nombre de sorties contenue dans un groupe peut varier à partir de la configuration à la configuration. Par exemple, Matt du projet DLL peut inclure des mattd.dll et mattd.pdb dans la configuration Debug, mais uniquement inclure matt.dll dans la configuration de la vente au détail.  
  
 Les groupes ont également les mêmes informations d’identificateur, tel que le nom complet, nom complet et informations de groupe, de configuration de configuration dans un projet. Cette cohérence permet de déploiement et empaquetage de continuer à fonctionner même si la modification des configurations.  
  
 Groupes peuvent également avoir une génération de clé qui permet des raccourcis d’empaquetage pointer vers un nom significatif. Un groupe peut être vide dans une configuration donnée, donc aucune hypothèse ne doit être effectuées sur la taille d’un groupe. La taille (nombre de sorties) de chaque groupe dans n’importe quelle configuration peut être différente de la taille d’un autre groupe dans la même configuration. Il peut également être différente de la taille du même groupe dans une autre configuration.  
  
 ![Graphique de groupes de sortie](../../extensibility/internals/media/vsoutputgroups.gif "vsOutputGroups")  
Groupes de sortie  
  
 La principale utilisation de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg> interface consiste à fournir un accès pour générer, déployer et déboguer des objets de gestion et permettent aux projets aux sorties de groupe. Pour plus d’informations sur l’utilisation de cette interface, consultez [objet de Configuration de projet](../../extensibility/internals/project-configuration-object.md).  
  
 Dans le diagramme précédent, groupe créé a une clé de sortie entre les configurations (bD.exe ou b.exe), l’utilisateur peut créer un raccourci vers intégré et savez que le raccourci fonctionne indépendamment de la configuration de déploiement. Source de groupe n’a pas une clé de sortie, afin de l’utilisateur ne peut pas créer un raccourci vers celui-ci. Si le groupe de déboguer générée est doté d’une clé, mais le groupe de vente au détail créé pas, qui est une implémentation incorrecte. Elle suit, puis, qui si n’importe quelle configuration comporte un groupe qui ne contient aucuns sortie, et, par conséquent, aucun fichier de clé, puis les autres configurations de groupe qui contiennent des sorties ne peut pas avoir des fichiers de clés. Les éditeurs de programme d’installation supposent que les noms canoniques et les noms d’affichage des groupes, ainsi que l’existence d’un fichier de clé ne changent pas en se basant sur les configurations.  
  
 Notez que si un projet a un `IVsOutputGroup` qu’il ne souhaite pas de package ou de déployer, il ne suffit ne pas placer cette sortie dans un groupe. La sortie peut toujours être énumérée normalement en implémentant la <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg.EnumOutputs%2A> méthode qui retourne toutes les sorties d’une configuration, quelle que soit le regroupement.  
  
 Pour plus d’informations, consultez l’implémentation de `IVsOutputGroup` dans l’exemple de projet personnalisé à [MPF pour les projets](http://mpfproj12.codeplex.com).  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des Options de Configuration](../../extensibility/internals/managing-configuration-options.md)   
 [Configuration de projet pour la génération](../../extensibility/internals/project-configuration-for-building.md)   
 [Objet de Configuration de projet](../../extensibility/internals/project-configuration-object.md)   
 [Configuration de la solution](../../extensibility/internals/solution-configuration.md)