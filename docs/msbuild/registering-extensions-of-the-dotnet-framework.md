---
title: Inscription des extensions de .NET Framework | Microsoft Docs
description: Découvrez comment ajouter un dossier contenant un assembly qui étend une version spécifique du .NET Framework au registre système.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Add References dialog box, registering extensions of the .NET Framework
- MSBuild, registering extensions of the .NET Framework
- .NET Framework extensions, registering
ms.assetid: deee6f53-ea87-4b88-a120-bea589822e03
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 61197fcfe84c96eed2c46b662f93a06386bb9c1e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99931840"
---
# <a name="register-extensions-of-the-net-framework"></a>Inscrire des extensions de .NET Framework

Vous pouvez développer un assembly qui étend une version spécifique de .NET Framework. Pour permettre l’affichage de l’assembly dans la boîte de dialogue **Ajouter des références** de Visual Studio, vous devez ajouter le dossier qui le contient dans le Registre système.

 Par exemple, supposons que la société Trey Research ait développé une bibliothèque qui étend .NET Framework 4 et qu’elle souhaite que les assemblys de la bibliothèque s’affichent dans la boîte de dialogue **Ajouter des références** lorsqu’un projet cible .NET Framework 4. Supposons également que les assemblys soient des assemblys 32 bits s’exécutant sur un ordinateur 32 bits ou des assemblys 64 bits s’exécutant sur un ordinateur 64 bits, et qu’ils soient installés dans le dossier *C:\TreyResearch\Extensions4\\*.

 Inscrivez ce dossier à l’aide de cette clé : **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework\v4.0.21006\AssemblyFoldersEx\TreyResearch\\**. Attribuez à la clé cette valeur par défaut : **C:\TreyResearch\Extensions4**.

> [!NOTE]
> Le numéro de build de la version .NET Framework peut être différent.

 Pour inscrire un assembly 32 bits sur un ordinateur 64 bits, utilisez le nœud Wow6432, par exemple : **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework\v4.0.21006\AssemblyFoldersEx\TreyResearch\\**.

### <a name="see-also"></a>Voir aussi

- [Visual Studio, intégration](../msbuild/visual-studio-integration-msbuild.md)
