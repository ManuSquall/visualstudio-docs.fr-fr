---
title: "Résolution d’assemblys au moment du design | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: msbuild
ms.assetid: 20dae076-733e-49c1-a2e9-b336757ae21d
caps.latest.revision: "8"
author: kempb
ms.author: kempb
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 3db59c3cb9234231a5a5fe4f881857433ab09479
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="resolving-assemblies-at-design-time"></a>Résolution d'assemblys au moment du design
Quand vous ajoutez une référence à un assembly par l’intermédiaire de l’onglet .NET de la boîte de dialogue Ajouter une référence, la référence pointe vers un assembly de référence intermédiaire, autrement dit un assembly qui contient toutes les informations de type et de signature, mais qui ne contient pas nécessairement de code. L’onglet .NET répertorie les assemblys de référence qui correspondent aux assemblys runtime du .NET Framework. Il répertorie aussi les assemblys de référence qui correspondent aux assemblys runtime dans les dossiers AssemblyFoldersEx inscrits utilisés par des tiers.  
  
## <a name="multi-targeting"></a>Multi-ciblage  
 [!INCLUDE[vs_dev12](../extensibility/includes/vs_dev12_md.md)] vous permet de cibler des versions du .NET Framework qui s’exécutent sur le Common Language Runtime (CLR) version 2.0 ou version 4. Cela inclut les versions .NET Framework 2.0, 3.0, 3.5, 4, 4.5 et 4.5.1, et les versions Silverlight 1.0, 2.0 et 3.0. Si une nouvelle version du .NET Framework basée sur le CLR version 2.0 ou version 4 est publiée, le Framework peut être installé à l’aide d’un pack de ciblage, et il apparaîtra automatiquement en tant que cible dans Visual Studio.  
  
## <a name="how-type-resolution-works"></a>Fonctionnement de la résolution de type  
 Au moment de l’exécution, le CLR résout les types dans l’assembly en recherchant dans le GAC, le répertoire bin et les chemins de détection. Ceci est géré par le chargeur de fusion. Mais comment le chargeur de fusion sait-il ce qu’il doit rechercher ? Cela dépend d’une résolution effectuée au moment du design, quand l’application est générée.  
  
 Pendant la génération, le compilateur résout les types d’applications à l’aide d’assemblys de référence. Dans les versions du .NET Framework 2.0, 3.0, 3.5, 4, 4.5 et 4.5.1, les assemblys de référence sont installés lors de l’installation du .NET Framework.  
  
 Les assemblys de référence sont fournis par le pack de ciblage fourni avec la version correspondante du SDK .NET Framework. Le Framework lui-même fournit uniquement les assemblys runtime. Pour générer des applications, vous devez installer le .NET Framework et le SDK .NET Framework correspondant.  
  
 Quand vous ciblez un .NET Framework spécifique, le système de génération résout tous les types en utilisant les assemblys de référence dans le pack de ciblage. Au moment de l’exécution, le chargeur de fusion résout ces mêmes types aux assemblys runtime, qui se trouvent généralement dans le GAC.  
  
 Si les assemblys de référence ne sont pas disponibles, le système de génération résout les types d’assemblys à l’aide des assemblys runtime. Les assemblys runtime dans le GAC n’étant pas différenciés par des numéros de version mineure, il est possible que la résolution soit effectuée au mauvais assembly. Cela peut se produire par exemple si une nouvelle méthode introduite dans le .NET Framework version 3.5 est référencée alors que vous ciblez la version 3.0. La génération réussira et l’application s’exécutera sur l’ordinateur de build, mais elle échouera lors du déploiement sur un ordinateur sur lequel la version 3.5 n’est pas installée.  
  
 Le pack de ciblage désormais fourni avec le SDK .NET Framework inclut une liste de tous les assemblys runtime dans cette version du Framework, appelée liste de redistribution (redist). Ainsi, il est impossible que le système de génération résolve des types par rapport à une version incorrecte de l’assembly.  
  
## <a name="see-also"></a>Voir aussi  
 [Concepts avancés](../msbuild/msbuild-advanced-concepts.md)