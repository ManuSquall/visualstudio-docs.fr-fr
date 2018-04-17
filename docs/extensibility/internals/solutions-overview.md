---
title: Vue d’ensemble des solutions | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- solutions, about solutions
ms.assetid: 3b21e3a1-170a-4485-941e-6b04b7b27886
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d64175c570c4fbca26bae0aa587b66e04cbee2be
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="solutions-overview"></a>Vue d’ensemble des solutions
Une solution est un regroupement d’un ou plusieurs projets qui travaillent conjointement pour créer une application. Les informations de projet et d’état relatives à la solution sont stockés dans deux fichiers de solution différente. Le fichier solution (.sln) est basée sur le texte et peuvent être placés sous contrôle de code source et partagé entre les utilisateurs. La solution utilisateur option (.suo) fichier est binaire. Par conséquent, le fichier .suo ne peut pas être placé sous contrôle de code source et contient des informations spécifiques à l’utilisateur.  
  
 Un VSPackage peut écrire dans les deux types de fichiers de solution. En raison de la nature des fichiers, il existe deux interfaces différentes implémentées pour écrire dessus. Le <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps> interface écrit les informations de texte dans le fichier .sln et <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> interface écrit des flux de données binaires dans le fichier .suo.  
  
> [!NOTE]
>  Un projet n’a pas écrit de façon explicite une entrée pour lui-même dans le fichier solution ; l’environnement qui gère pour le projet. Par conséquent, sauf si vous souhaitez ajouter du contenu en particulier dans le fichier de solution, il est inutile inscrire votre VSPackage de cette façon.  
  
 Chaque VSPackage prenant en charge la persistance de la solution utilise trois interfaces, les <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> interface, qui est implémentée par l’environnement et appelé par le VSPackage, et `IVsPersistSolutionProps` et `IVsPersistSolutionOpts`, qui sont implémentés par le VSPackage. Le `IVsPersistSolutionOpts` interface doit uniquement être implémentée si des informations privées doivent être écrites par le VSPackage dans le fichier .suo.  
  
 Lorsqu’une solution est ouverte, le processus suivant a lieu.  
  
1.  L’environnement lit la solution.  
  
2.  Si l’environnement détecte un `CLSID`, il charge le VSPackage correspondant.  
  
3.  Si un VSPackage est chargé, l’environnement appelle `QueryInterface` pour <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> interface, pour l’interface qui nécessite que le VSPackage.  
  
    1.  Lors de la lecture à partir d’un fichier .sln, l’environnement appelle `QueryInterface` pour `IVsPersistSolutionProps`.  
  
    2.  Lors de la lecture à partir d’un fichier .suo, l’environnement appelle `QueryInterface` pour `IVsPersistSolutionOpts`.  
  
 Vous trouverez des informations spécifiques relatives à l’utilisation de ces fichiers dans [Solution (. Les fichiers sln)](../../extensibility/internals/solution-dot-sln-file.md) et [Options utilisateur de Solution (. Fichier suo)](../../extensibility/internals/solution-user-options-dot-suo-file.md).  
  
> [!NOTE]
>  Si vous souhaitez créer une nouvelle configuration de solution composé de configurations de deux projets et une troisième à exclure de la build, vous devez utiliser l’interface utilisateur de Pages de propriété ou d’une automation. Vous ne pouvez pas modifier directement les configurations de gestionnaire de build de solution et leurs propriétés, mais vous pouvez manipuler le Gestionnaire de build de solution à l’aide de la `SolutionBuild` classe à partir de DTE dans le modèle automation. Pour plus d’informations sur la configuration de solutions, consultez [Configuration de la Solution](../../extensibility/internals/solution-configuration.md).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>