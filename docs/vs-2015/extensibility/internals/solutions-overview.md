---
title: Vue d’ensemble de solutions | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- solutions, about solutions
ms.assetid: 3b21e3a1-170a-4485-941e-6b04b7b27886
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7255ed981bd65e364d1028c365aab66a73a76dcb
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49815999"
---
# <a name="solutions-overview"></a>Présentation des solutions
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Une solution est un regroupement d’un ou plusieurs projets qui fonctionnent ensemble pour créer une application. Les informations de projet et d’état relatives à la solution sont stockés dans deux fichiers de solution différent. Le fichier solution (.sln) est en mode texte et peuvent être placés sous contrôle de code source et partagé entre les utilisateurs. Le fichier des options (.suo) solution utilisateur est binaire. Par conséquent, le fichier .suo ne peuvent pas être placé sous contrôle de code source et contient des informations spécifiques à l’utilisateur.  
  
 Un VSPackage peut écrire dans ces deux types de fichier solution. En raison de la nature des fichiers, il existe deux interfaces différentes implémentées pour y écrire. Le <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps> interface écrit les informations de texte dans le fichier .sln et <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> interface écrit des flux de données binaires dans le fichier .suo.  
  
> [!NOTE]
>  Un projet n’a pas écrit de façon explicite une entrée pour lui-même dans le fichier de solution ; l’environnement qui gère le projet. Par conséquent, sauf si vous souhaitez ajouter du contenu supplémentaire spécifiquement pour le fichier de solution, il est inutile inscrire votre VSPackage de cette façon.  
  
 Chaque VSPackage prenant en charge la persistance de solution utilise trois interfaces, le <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> interface, qui est implémenté par l’environnement et appelée par le VSPackage, et `IVsPersistSolutionProps` et `IVsPersistSolutionOpts`, qui sont tous deux implémentés par le VSPackage. Le `IVsPersistSolutionOpts` interface doit uniquement être implémentée si les informations privées doivent être écrits par le VSPackage dans le fichier .suo.  
  
 Lorsqu’une solution est ouverte, le processus suivant a lieu.  
  
1. L’environnement lit la solution.  
  
2. Si l’environnement recherche un `CLSID`, il charge le VSPackage correspondant.  
  
3. Si un VSPackage est chargé, l’environnement appelle `QueryInterface` pour <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> interface, de l’interface qui nécessite le VSPackage.  
  
   1.  Lors de la lecture à partir d’un fichier .sln, l’environnement appelle `QueryInterface` pour `IVsPersistSolutionProps`.  
  
   2.  Lors de la lecture à partir d’un fichier .suo, l’environnement appelle `QueryInterface` pour `IVsPersistSolutionOpts`.  
  
   Vous trouverez des informations spécifiques relatives à l’utilisation de ces fichiers dans [Solution (. Fichier de sln)](../../extensibility/internals/solution-dot-sln-file.md) et [Options utilisateur de Solution (. Fichier suo)](../../extensibility/internals/solution-user-options-dot-suo-file.md).  
  
> [!NOTE]
>  Si vous souhaitez créer une nouvelle configuration de solution comprenant des configurations de deux projets et une troisième à exclure de la build, vous devez utiliser l’interface utilisateur de Pages de propriété ou l’automatisation. Vous ne pouvez pas modifier les configurations de gestionnaire de build de solution et leurs propriétés directement, mais vous pouvez manipuler le Gestionnaire de génération de solution à l’aide de la `SolutionBuild` classe dans le modèle automation DTE. Pour plus d’informations sur la configuration de solutions, consultez [Configuration de la Solution](../../extensibility/internals/solution-configuration.md).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>

