---
title: XDCMake, tâche | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vc.task.xdcmake
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- XDCMake task (MSBuild (C++))
- MSBuild (C++), XDCMake task
ms.assetid: a7de9c64-903a-4a02-85f3-f37672270f25
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0b1ae0fbbcdb36c13a8c0ee91011f2b7d6fba9f5
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72747164"
---
# <a name="xdcmake-task"></a>XDCMake (tâche)
Inclut dans un wrapper l’outil Documentation XML (*xdcmake.exe*), qui fusionne des fichiers de commentaires documentation XML ( *.xdc*) dans un fichier *.xml*.

 Un fichier *. XDC* est créé lorsque vous fournissez des commentaires de C++ documentation dans votre code source et que vous compilez à l’aide de l’option de compilateur [/doc](/cpp/build/reference/doc-process-documentation-comments-c-cpp) . Pour plus d’informations, consultez [Référence XDCMake](/cpp/build/reference/xdcmake-reference), [Outil Générateur de documents XML, page de propriétés](/cpp/build/reference/xml-document-generator-tool-property-pages) et l’option de l’aide en ligne de commande ( **/ ?** ) pour *xdcmake.exe*.

## <a name="remarks"></a>Notes
 Par défaut, l’outil *xdcmake.exe* prend en charge quelques options de ligne de commande. Des options supplémentaires sont prises en charge lorsque vous spécifiez l’option de ligne de commande **/old**.

## <a name="parameters"></a>Paramètres
 Le tableau ci-dessous décrit les paramètres de la tâche **XDCMake**.

|Paramètre|Description|
|---------------|-----------------|
|**AdditionalDocumentFile**|Paramètre **String[]** facultatif.<br /><br /> Spécifie un ou plusieurs fichiers *.xdc* supplémentaires à fusionner.<br /><br /> Pour plus d’informations, consultez la description **Fichiers de document supplémentaires** dans [Outil Générateur de documents XML, page de propriétés](/cpp/build/reference/xml-document-generator-tool-property-pages). Consultez également les options de ligne de commande **/old** et **/Fs** pour *xdcmake.exe*.|
|**AdditionalOptions**|Paramètre **String** facultatif.<br /><br /> Liste des options comme indiqué sur la ligne de commande. Par exemple, /\<option1> /\<option2> /\<option#>. Utilisez ce paramètre pour spécifier des options qui ne sont pas représentées par un autre paramètre de tâche **XDCMake**.<br /><br /> Pour plus d’informations, consultez [Référence XDCMake](/cpp/build/reference/xdcmake-reference), [Outil Générateur de documents XML, page de propriétés](/cpp/build/reference/xml-document-generator-tool-property-pages) et l’aide en ligne de commande ( **/ ?** ) pour *xdcmake.exe*.|
|**DocumentLibraryDependencies**|Paramètre **Boolean** facultatif.<br /><br /> Si `true` et si le projet actuel a une dépendance sur un projet de bibliothèque statique ( *.lib*) dans la solution, les fichiers *.xdc* pour ce projet de bibliothèque sont inclus dans la sortie de fichier *.xml* pour le projet actuel.<br /><br /> Pour plus d’informations, consultez la description **Dépendances de bibliothèque de documents** dans [Outil Générateur de documents, page de propriétés](/cpp/build/reference/xml-document-generator-tool-property-pages).|
|**OutputFile**|Paramètre **String** facultatif.<br /><br /> Substitue le nom de fichier de sortie par défaut. Le nom par défaut est dérivé du nom du premier fichier *.xdc* traité.<br /><br /> Pour plus d’informations, consultez l’option **/out:\<filename>** dans [Référence XDCMake](/cpp/build/reference/xdcmake-reference). Consultez également les options de ligne de commande **/old** et **/Fo** pour *xdcmake.exe*.|
|**ProjectName**|Paramètre **String** facultatif.<br /><br /> Nom du projet actif.|
|**SlashOld**|Paramètre **Boolean** facultatif.<br /><br /> Si `true`, active des options *xdcmake.exe* supplémentaires.<br /><br /> Pour plus d’informations, consultez l’option de ligne de commande **/old** pour *xdcmake.exe*.|
|**Sources**|Paramètre `ITaskItem[]` requis.<br /><br /> Définit un tableau d’éléments de fichier source MSBuild pouvant être consommés et émis par des tâches.|
|**SuppressStartupBanner**|Paramètre **Boolean** facultatif.<br /><br /> Si la valeur est `true`, empêche l'affichage du message de copyright et de numéro de version quand la tâche démarre.<br /><br /> Pour plus d’informations, consultez l’option **/nologo** dans [Référence XDCMake](/cpp/build/reference/xdcmake-reference).|
|**TrackerLogDirectory**|Paramètre **String** facultatif.<br /><br /> Spécifie le répertoire du journal de Tracker.|

## <a name="see-also"></a>Voir aussi
- [Informations de référence sur les tâches](../msbuild/msbuild-task-reference.md)