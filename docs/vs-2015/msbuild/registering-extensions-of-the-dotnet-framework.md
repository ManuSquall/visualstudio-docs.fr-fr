---
title: Inscription des extensions de .NET Framework | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Add References dialog box, registering extensions of the .NET Framework
- MSBuild, registering extensions of the .NET Framework
- .NET Framework extensions, registering
ms.assetid: deee6f53-ea87-4b88-a120-bea589822e03
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2a2d3e281562be5234e0a70a877a6c169c346995
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47495615"
---
# <a name="registering-extensions-of-the-net-framework"></a>Inscrire des extensions du .NET Framework
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [l’inscription des Extensions du .NET Framework](https://docs.microsoft.com/visualstudio/msbuild/registering-extensions-of-the-dotnet-framework).  
  
  
Vous pouvez développer un assembly qui étend une version spécifique de .NET Framework. Pour permettre l’affichage de l’assembly dans la boîte de dialogue **Ajouter des références** de Visual Studio, vous devez ajouter le dossier qui le contient dans le Registre système.  
  
 Par exemple, supposons que la société Trey Research ait développé une bibliothèque qui étend .NET Framework 4 et qu’elle souhaite que les assemblys de la bibliothèque s’affichent dans la boîte de dialogue **Ajouter des références** lorsqu’un projet cible .NET Framework 4. Supposons également que les assemblys soient des assemblys 32 bits s’exécutant sur un ordinateur 32 bits ou des assemblys 64 bits s’exécutant sur un ordinateur 64 bits, et qu’ils soient installés dans le dossier C:\TreyResearch\Extensions4\.  
  
 Inscrivez ce dossier à l’aide de cette clé : HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework\v4.0.21006\AssemblyFoldersEx\TreyResearch\\. Attribuez à la clé cette valeur par défaut : C:\TreyResearch\Extensions4.  
  
> [!NOTE]
>  Le numéro de build de la version .NET Framework peut être différent.  
  
 Pour inscrire un assembly 32 bits sur un ordinateur 64 bits, utilisez le nœud Wow6432, par exemple : HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework\v4.0.21006\AssemblyFoldersEx\TreyResearch\\.  
  
## <a name="see-also"></a>Voir aussi  
 [Intégration de Visual Studio (MSBuild)](../msbuild/visual-studio-integration-msbuild.md)



