---
title: "Nouveautés de MSBuild 12.0 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9976a6ad-c052-4017-b848-35b5ae4a2f66
caps.latest.revision: 23
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
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
translationtype: Human Translation
ms.sourcegitcommit: 3ba7680d46345f2b49019659c715cfb418933d39
ms.openlocfilehash: d299c4959ddf23a8c249f5577ee03fda99e636f7
ms.lasthandoff: 02/22/2017

---
# <a name="what39s-new-in-msbuild-120"></a>Nouveautés de MSBuild 12.0
MSBuild est désormais installé dans le cadre de Visual Studio et non dans celui de .NET Framework. La version actuelle de MSBuild porte le numéro 12.0. Si vous souhaitez installer MSBuild séparément, téléchargez le package d’installation à partir de [MSBuild Download (Téléchargement de MSBuild)](http://go.microsoft.com/fwlink/?LinkId=309745).  
  
## <a name="changed-path"></a>Chemin d’accès modifié  
 MSBuild est désormais installé directement sous *%ProgramFiles%*, par exemple, dans C:\Program Files\MSBuild\\.  
  
## <a name="changed-properties"></a>Propriétés modifiées  
 Les propriétés MSBuild suivantes sont modifiées à la suite du nouveau numéro de version :  
  
-   `MSBuildToolsVersion` pour cette version des outils porte le numéro 12.0.  
  
-   `MSBuildToolsPath` est maintenant %ProgramFiles%\MSBuild\12.0\bin sur les systèmes d’exploitation 32 bits ou %ProgramFiles%\MSBuild\12.0\bin\amd64 sur les systèmes d’exploitation 64 bits.  
  
-   Les valeurs `ToolsVersion` se trouvent dans HKLM\SOFTWARE\Microsoft\MSBuild\ToolsVersions\12.0 pour les systèmes d’exploitation 32 bits ou HKLM\SOFTWARE\Wow6432Node\Microsoft\MSBuild\ToolsVersions\12.0 pour les systèmes d’exploitation 64 bits.  
  
-   Les propriétés `SDK35ToolsPath` et `SDK40ToolsPath` pointent vers le Kit de développement logiciel (SDK) .NET Framework, qui est fourni avec cette version de Visual Studio (par exemple, 8.1A pour les outils 4.X).  
  
## <a name="new-properties"></a>Nouvelles propriétés  
  
-   `MSBuildFrameworkToolsPath` est une nouvelle propriété pourvue de la valeur %windir%\Microsoft.NET\Framework\v4.0.30319 sur les systèmes d’exploitation 32 bits ou %windir%\Microsoft.NET\Framework64\v4.0.30319 sur les systèmes d’exploitation 64 bits. Elle remplace la propriété `MSBuildToolsPath` et permet de pointer vers les utilitaires et outils .NET Framework.  
  
-   `MSBuildToolsPath` et `MSBuildFrameworkToolsPath` ont des équivalents 32 bits, `MSBuildToolsPath32` et `MSBuildFrameworkToolsPath32`, qui pointent toujours vers l’emplacement 32 bits, quelle que soit la version (32 bits ou 64 bits) MSBuild utilisée.

## <a name="see-also"></a>Voir aussi
[MSBuild](../msbuild/msbuild.md)
