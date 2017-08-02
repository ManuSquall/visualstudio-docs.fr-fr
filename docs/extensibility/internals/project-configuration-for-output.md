---
title: "Configuration de projet pour la sortie | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "configurations de projet, la sortie"
ms.assetid: a4517f73-45af-4745-9d7f-9fddf887b636
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# Configuration de projet pour la sortie
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Chaque configuration peut prendre en charge un ensemble de processus de génération qui produisent des éléments de sortie tels que les fichiers exécutables ou d'une ressource. Ces éléments de sortie sont privés à l'utilisateur et peuvent être placés dans des groupes qui lient les types de sortie, tels que les fichiers exécutables \(.exe, .dll, .lib\) et les fichiers sources \(.idl, fichiers .h\).  
  
 Éléments de sortie peuvent être rendues disponibles via le <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput2> méthodes et énumérées avec le <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumOutputs> méthodes. Lorsque vous souhaitez regrouper les éléments de sortie, votre projet doit également implémenter le <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup> interface.  
  
 La construction de développé en implémentant `IVsOutputGroup` permet aux projets de sorties de groupe en fonction de l'utilisation. Par exemple, une DLL peut être regroupée avec sa base de données du programme \(PDB\).  
  
> [!NOTE]
>  Un fichier PDB contient des informations de débogage et il est créé lorsque l'option « Générer des informations de débogage » est spécifiée lors de la génération du fichier .dll ou .exe. Le fichier .pdb est généralement généré pour la configuration de projet de débogage uniquement.  
  
 Le projet doit retourner le même nombre de groupes pour chaque configuration pris en charge, même si le nombre de sorties contenue dans un groupe peut varier à partir de la configuration de. Par exemple, Matt du projet DLL peut inclure des mattd.dll et mattd.pdb dans la configuration Debug, mais uniquement inclure matt.dll dans la configuration de la vente au détail.  
  
 Les groupes ont également les mêmes informations d'identificateur, telles que le nom complet, nom d'affichage et les informations du groupe, à partir de la configuration de dans un projet. Cette cohérence permet le déploiement et empaquetage de continuer à fonctionner même si la modification des configurations.  
  
 Les groupes peuvent également avoir une génération de clé qui permet de raccourcis de packaging pointer vers quelque chose de significatif. Un groupe peut être vide dans une configuration donnée, donc aucune hypothèse doit être effectuée sur la taille d'un groupe. La taille \(nombre de sorties\) de chaque groupe dans n'importe quelle configuration peut être différente de la taille d'un autre groupe dans la même configuration. Il peut également être différente de la taille du même groupe dans une autre configuration.  
  
 ![Graphique Groupes de sorties](~/extensibility/internals/media/vsoutputgroups.gif "vsOutputGroups")  
Groupes de sortie  
  
 Utilise principalement le <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg> interface consiste à fournir un accès pour générer, déployer et déboguer des objets de gestion et permettent aux projets vers des sorties de groupe. Pour plus d'informations sur l'utilisation de cette interface, consultez la page [Objet de Configuration de projet](../../extensibility/internals/project-configuration-object.md).  
  
 Dans le diagramme précédent, groupe créé a une clé de sortie donc sur les configurations \(bD.exe ou b.exe\) l'utilisateur peut créer un raccourci vers intégré et savez que le raccourci fonctionne indépendamment de la configuration de déploiement. Groupe Source n'a pas une clé de sortie, afin de l'utilisateur ne peut pas créer un raccourci vers celui\-ci. Si le groupe déboguer générée est doté d'une clé, mais le groupe de vente au détail créé pas, qui est une implémentation incorrecte. Il en résulte, puis, que si aucune configuration dispose d'un groupe qui ne contient aucuns sortie, et, en conséquence, aucun fichier de clé, puis les autres configurations de groupe qui ne contiennent pas sorties ne peuvent pas avoir des fichiers de clés. Les éditeurs de programme d'installation supposent que les noms canoniques et les noms d'affichage des groupes, ainsi que l'existence d'un fichier de clé, ne changent pas en se basant sur les configurations.  
  
 Notez que si un projet a un `IVsOutputGroup` qu'il ne souhaite pas empaqueter ou déployer, il suffit ne pas placer cette sortie dans un groupe. La sortie peut toujours être énumérée normalement en implémentant la <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg.EnumOutputs%2A> méthode qui retourne toutes les sorties de configuration indépendamment de regroupement.  
  
 Pour plus d'informations, consultez l'implémentation de `IVsOutputGroup` dans l'exemple de projet personnalisé à [MPF pour les projets](http://mpfproj12.codeplex.com).  
  
## Voir aussi  
 [Gestion des Options de Configuration](../../extensibility/internals/managing-configuration-options.md)   
 [Configuration de projet pour la création](../../extensibility/internals/project-configuration-for-building.md)   
 [Objet de Configuration de projet](../../extensibility/internals/project-configuration-object.md)   
 [Configuration de la solution](../../extensibility/internals/solution-configuration.md)