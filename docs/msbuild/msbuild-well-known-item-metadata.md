---
title: Métadonnées d’éléments connus MSBuild | Microsoft Docs
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 284c031d4a76b818992948b2299981b0d650e9e2
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54966593"
---
# <a name="msbuild-well-known-item-metadata"></a>Métadonnées d’éléments connus MSBuild
Le tableau suivant décrit les métadonnées assignées à chaque élément lors de sa création. Dans chaque exemple, la déclaration d’élément suivante a été utilisée pour inclure le fichier *C:\MyProject\Source\Program.cs* dans le projet.  
  
```xml  
<ItemGroup>  
    <MyItem Include="Source\Program.cs" />  
</ItemGroup>  
```  
  
|Métadonnées d’élément|Description|  
|-------------------|-----------------|  
|%(FullPath)|Contient le chemin complet de l’élément. Par exemple :<br /><br /> *C:\MyProject\Source\Program.cs*|  
|%(RootDir)|Contient le répertoire racine de l’élément. Par exemple :<br /><br /> *C:\\*|  
|%(Filename)|Contient le nom de fichier de l’élément, sans l’extension. Par exemple :<br /><br /> *Program*|  
|%(Extension)|Contient l’extension de nom de fichier de l’élément. Par exemple :<br /><br /> *.cs*|  
|%(RelativeDir)|Contient le chemin spécifié dans l’attribut `Include`, jusqu’à la dernière barre oblique inverse (\\). Par exemple :<br /><br /> *Source\\*|  
|%(Directory)|Contient le répertoire de l’élément, sans le répertoire racine. Par exemple :<br /><br /> *MyProject\\Source\\*|  
|%(RecursiveDir)|Si l’attribut `Include` contient le caractère générique \*\*, ces métadonnées spécifient la partie du chemin qui remplace le caractère générique. Pour plus d’informations sur les caractères génériques, consultez [Procédure : Sélectionner des fichiers dans une build](../msbuild/how-to-select-the-files-to-build.md).<br /><br /> Si le dossier *C:\MySolution\MyProject\Source\\* contient le fichier *Program.cs*, et si le fichier projet contient cet élément :<br /><br /> `<ItemGroup>`<br /><br /> `<MyItem Include="C:\**\Program.cs" />`<br /><br /> `</ItemGroup>`<br /><br /> la valeur de `%(MyItem.RecursiveDir)` est *MySolution\MyProject\Source\\*.|  
|%(Identity)|Élément spécifié dans l’attribut `Include`. Par exemple :<br /><br /> *Source\Program.cs*|  
|%(ModifiedTime)|Contient l’horodatage de la dernière modification de l’élément. Par exemple :<br /><br /> `2004-07-01 00:21:31.5073316`|  
|%(CreatedTime)|Contient l’horodatage de création de l’élément. Par exemple :<br /><br /> `2004-06-25 09:26:45.8237425`|  
|%(AccessedTime)|Contient l’horodatage du dernier accès à l’élément.<br /><br /> `2004-08-14 16:52:36.3168743`|  
  
## <a name="see-also"></a>Voir aussi  
 [Éléments](../msbuild/msbuild-items.md)   
 [Traitement par lot MSBuild](../msbuild/msbuild-batching.md)   
 [Informations de référence sur MSBuild](../msbuild/msbuild-reference.md)