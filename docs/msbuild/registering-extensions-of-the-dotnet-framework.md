---
title: Inscription des extensions de .NET Framework | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- Add References dialog box, registering extensions of the .NET Framework
- MSBuild, registering extensions of the .NET Framework
- .NET Framework extensions, registering
ms.assetid: deee6f53-ea87-4b88-a120-bea589822e03
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 0017255b67042a7e42b54325b24512a295ebeaf5
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/20/2018
ms.locfileid: "39180150"
---
# <a name="register-extensions-of-the-net-framework"></a>Inscrire des extensions de .NET Framework
Vous pouvez développer un assembly qui étend une version spécifique de .NET Framework. Pour permettre l’affichage de l’assembly dans la boîte de dialogue **Ajouter des références** de Visual Studio, vous devez ajouter le dossier qui le contient dans le Registre système.  
  
 Par exemple, supposons que la société Trey Research ait développé une bibliothèque qui étend .NET Framework 4 et qu’elle souhaite que les assemblys de la bibliothèque s’affichent dans la boîte de dialogue **Ajouter des références** lorsqu’un projet cible .NET Framework 4. Supposons également que les assemblys soient des assemblys 32 bits s’exécutant sur un ordinateur 32 bits ou des assemblys 64 bits s’exécutant sur un ordinateur 64 bits, et qu’ils soient installés dans le dossier *C:\TreyResearch\Extensions4\\*.  
  
 Inscrivez ce dossier à l’aide de cette clé : **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework\v4.0.21006\AssemblyFoldersEx\TreyResearch\\**. Attribuez à la clé cette valeur par défaut : **C:\TreyResearch\Extensions4**.  
  
> [!NOTE]
>  Le numéro de build de la version .NET Framework peut être différent.  
  
 Pour inscrire un assembly 32 bits sur un ordinateur 64 bits, utilisez le nœud Wow6432, par exemple : **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework\v4.0.21006\AssemblyFoldersEx\TreyResearch\\**.  
  
### <a name="see-also"></a>Voir aussi  
 [Intégration Visual Studio](../msbuild/visual-studio-integration-msbuild.md)