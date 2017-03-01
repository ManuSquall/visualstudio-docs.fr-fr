---
title: "Vue d’ensemble des solutions | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- solutions, about solutions
ms.assetid: 3b21e3a1-170a-4485-941e-6b04b7b27886
caps.latest.revision: 10
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
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 06ca562112b8b6feb711219502e3d10b1cb6f462
ms.lasthandoff: 02/22/2017

---
# <a name="solutions-overview"></a>Présentation des solutions
Une solution est un regroupement d’un ou plusieurs projets qui fonctionnent ensemble pour créer une application. Les informations d’état et de projet se rapportant à la solution sont stockées dans deux fichiers de solution différente. Le fichier solution (.sln) est en mode texte et peuvent être placés sous contrôle de code source et partagé entre les utilisateurs. Le fichier des options (.suo) solution utilisateur est binaire. Par conséquent, le fichier .suo ne peut pas être placé sous contrôle de code source et contient des informations spécifiques à l’utilisateur.  
  
 Un VSPackage peut écrire dans ces deux types de fichier solution. En raison de la nature des fichiers, il existe deux interfaces différentes implémentées pour y écrire. Le <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>interface écrit les informations de texte dans le fichier .sln et <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>interface écrit des flux de données binaires dans le fichier .suo.</xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> </xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>  
  
> [!NOTE]
>  Un projet n’a pas écrit de façon explicite une entrée pour ce dernier dans le fichier solution ; l’environnement qui gère le projet. Par conséquent, sauf si vous souhaitez ajouter du contenu supplémentaire en particulier dans le fichier de solution, il est inutile inscrire votre package VS de cette façon.  
  
 Chaque VSPackage prenant en charge la persistance de la solution utilise trois interfaces, le <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>interface qui est implémentée par l’environnement et appelé par le VSPackage, et `IVsPersistSolutionProps` et `IVsPersistSolutionOpts`, qui sont implémentés par le VSPackage.</xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> Le `IVsPersistSolutionOpts` interface doit uniquement être implémentée si les informations privées doivent être écrits par le VSPackage dans le fichier .suo.  
  
 Lorsqu’une solution est ouverte, le processus suivant a lieu.  
  
1.  L’environnement lit la solution.  
  
2.  Si l’environnement détecte un `CLSID`, il charge le VSPackage correspondant.  
  
3.  Si un VSPackage est chargée, l’environnement appelle `QueryInterface` pour <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>interface, de l’interface qui nécessite le VSPackage.</xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>  
  
    1.  Lors de la lecture d’un fichier .sln, l’environnement appelle `QueryInterface` pour `IVsPersistSolutionProps`.  
  
    2.  Lors de la lecture d’un fichier .suo, l’environnement appelle `QueryInterface` pour `IVsPersistSolutionOpts`.  
  
 Vous trouverez des informations spécifiques relatives à l’utilisation de ces fichiers dans [Solution (. Les fichiers sln)](../../extensibility/internals/solution-dot-sln-file.md) et [Options utilisateur de Solution (. Les fichiers suo)](../../extensibility/internals/solution-user-options-dot-suo-file.md).  
  
> [!NOTE]
>  Si vous souhaitez créer une nouvelle configuration de solution composé de configurations de deux projets et une troisième à exclure de la build, vous devez utiliser l’interface utilisateur des Pages de propriété ou d’automatisation. Vous ne pouvez pas modifier directement les configurations de solution manager et leurs propriétés, mais vous pouvez manipuler le Gestionnaire de génération de solution à l’aide de la `SolutionBuild` classe dans le modèle automation DTE. Pour plus d’informations sur la configuration de solutions, consultez [Configuration de la Solution](../../extensibility/internals/solution-configuration.md).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage></xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts></xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps></xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence></xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>
