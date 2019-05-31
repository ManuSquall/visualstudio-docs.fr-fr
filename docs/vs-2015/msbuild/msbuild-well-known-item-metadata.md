---
title: Métadonnées d’éléments connus MSBuild | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, item metadata
- MSBuild, well-known item metadata
ms.assetid: b5e791b5-c68f-4978-ad8a-9247d03bb6c0
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1bb2e53102221194dc829df162c44bbf04378b28
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/17/2019
ms.locfileid: "59648937"
---
# <a name="msbuild-well-known-item-metadata"></a>Métadonnées d'éléments connus MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Le tableau suivant décrit les métadonnées assignées à chaque élément lors de sa création. Dans chaque exemple, la déclaration d’élément suivante a été utilisée pour inclure le fichier `C:\MyProject\Source\Program.cs` dans le projet.  
  
```  
<ItemGroup>  
    <MyItem Include="Source\Program.cs" />  
</ItemGroup>  
```  
  
|Métadonnées d’élément|Description|  
|-------------------|-----------------|  
|%(FullPath)|Contient le chemin complet de l’élément. Exemple :<br /><br /> `C:\MyProject\Source\Program.cs`|  
|%(RootDir)|Contient le répertoire racine de l’élément. Exemple :<br /><br /> `C:\`|  
|%(Filename)|Contient le nom de fichier de l’élément, sans l’extension. Exemple :<br /><br /> `Program`|  
|%(Extension)|Contient l’extension de nom de fichier de l’élément. Exemple :<br /><br /> `.cs`|  
|%(RelativeDir)|Contient le chemin spécifié dans l’attribut `Include`, jusqu’à la dernière barre oblique inverse (\\). Exemple :<br /><br /> `Source\`|  
|%(Directory)|Contient le répertoire de l’élément, sans le répertoire racine. Exemple :<br /><br /> `MyProject\Source\`|  
|%(RecursiveDir)|Si l’attribut `Include` contient le caractère générique \*\*, ces métadonnées spécifient la partie du chemin qui remplace le caractère générique. Pour plus d’informations sur les caractères génériques, consultez [Procédure : Sélectionnez les fichiers dans une Build](../msbuild/how-to-select-the-files-to-build.md).<br /><br /> Si le dossier *C:\MySolution\MyProject\Source\\* contient le fichier Program.cs, et si le fichier projet contient cet élément :<br /><br /> `<ItemGroup>`<br /><br /> `<MyItem Include="C:\**\Program.cs" />`<br /><br /> `</ItemGroup>`<br /><br /> la valeur de `%(MyItem.RecursiveDir)` est *MySolution\MyProject\Source\\* .|  
|%(Identity)|Élément spécifié dans l’attribut `Include`. Exemple :<br /><br /> `Source\Program.cs`|  
|%(ModifiedTime)|Contient l’horodatage de la dernière modification de l’élément. Exemple :<br /><br /> `2004-07-01 00:21:31.5073316`|  
|%(CreatedTime)|Contient l’horodatage de création de l’élément. Exemple :<br /><br /> `2004-06-25 09:26:45.8237425`|  
|%(AccessedTime)|Contient l’horodatage du dernier accès à l’élément.<br /><br /> `2004-08-14 16:52:36.3168743`|  
  
## <a name="see-also"></a>Voir aussi  
 [Éléments](../msbuild/msbuild-items.md)   
 [Traitement par lot MSBuild](../msbuild/msbuild-batching.md)   
 [Informations de référence sur MSBuild](../msbuild/msbuild-reference.md)
