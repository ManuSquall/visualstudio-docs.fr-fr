---
title: XDCMake, tâche | Microsoft Docs
description: Découvrez comment MSBuild utilise la tâche XDCMake pour encapsuler l’outil de documentation XML xdcmake.exe, qui fusionne les fichiers de commentaires de document XML dans un fichier. Xml.
ms.custom: SEO-VS-2020
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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 62d1717acee9b8935f176bc10191f044b28a660d
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93047272"
---
# <a name="xdcmake-task"></a>XDCMake (tâche)

Encapsule l’outil de documentation XML ( *xdcmake.exe* ), qui fusionne les fichiers de commentaires de document XML ( *. XDC* ) dans un fichier *. xml* .

 Un fichier *. XDC* est créé lorsque vous fournissez des commentaires de documentation dans votre code source C++ et que vous compilez à l’aide de l’option de compilateur [/doc](/cpp/build/reference/doc-process-documentation-comments-c-cpp) . Pour plus d’informations, consultez [Référence XDCMake](/cpp/build/reference/xdcmake-reference), [Outil Générateur de documents XML, page de propriétés](/cpp/build/reference/xml-document-generator-tool-property-pages) et l’option de l’aide en ligne de commande ( **/ ?** ) pour *xdcmake.exe* .

## <a name="remarks"></a>Remarques

 Par défaut, l’outil *xdcmake.exe* prend en charge quelques options de ligne de commande. Des options supplémentaires sont prises en charge lorsque vous spécifiez l’option de ligne de commande **/old** .

## <a name="parameters"></a>Paramètres

 Le tableau ci-dessous décrit les paramètres de la tâche **XDCMake** .

|Paramètre|Description|
|---------------|-----------------|
|**AdditionalDocumentFile**|Paramètre **String []** facultatif.<br /><br /> Spécifie un ou plusieurs fichiers *.xdc* supplémentaires à fusionner.<br /><br /> Pour plus d’informations, consultez la description **Fichiers de document supplémentaires** dans [Outil Générateur de documents XML, page de propriétés](/cpp/build/reference/xml-document-generator-tool-property-pages). Consultez également les options de ligne de commande **/Old** et **/FS** pour *xdcmake.exe* .|
|**AdditionalOptions**|Paramètre de **chaîne** facultatif.<br /><br /> Liste des options comme indiqué sur la ligne de commande. Par exemple,/ \<option1>  / \<option2>  / \<option#> . Utilisez ce paramètre pour spécifier des options qui ne sont pas représentées par un autre paramètre de tâche **XDCMake** .<br /><br /> Pour plus d’informations, consultez [référence XDCMake](/cpp/build/reference/xdcmake-reference), [outil générateur de documents XML, page de propriétés](/cpp/build/reference/xml-document-generator-tool-property-pages)et aide sur la ligne de commande ( **/ ?** ) pour *xdcmake.exe* .|
|**DocumentLibraryDependencies**|Paramètre **booléen** facultatif.<br /><br /> Si `true` et si le projet actuel a une dépendance sur un projet de bibliothèque statique ( *.lib* ) dans la solution, les fichiers *.xdc* pour ce projet de bibliothèque sont inclus dans la sortie de fichier *.xml* pour le projet actuel.<br /><br /> Pour plus d’informations, consultez la description **Dépendances de bibliothèque de documents** dans [Outil Générateur de documents, page de propriétés](/cpp/build/reference/xml-document-generator-tool-property-pages).|
|**OutputFile**|Paramètre de **chaîne** facultatif.<br /><br /> Substitue le nom de fichier de sortie par défaut. Le nom par défaut est dérivé du nom du premier fichier *.xdc* traité.<br /><br /> Pour plus d’informations, consultez l’option **/out : \<filename>** dans la [référence XDCMake](/cpp/build/reference/xdcmake-reference). Consultez également les options de ligne de commande **/old** et **/Fo** pour *xdcmake.exe* .|
|**Nom du projet**|Paramètre de **chaîne** facultatif.<br /><br /> Nom du projet actif.|
|**SlashOld**|Paramètre **booléen** facultatif.<br /><br /> Si `true`, active des options *xdcmake.exe* supplémentaires.<br /><br /> Pour plus d’informations, consultez l’option de ligne de commande **/old** pour *xdcmake.exe* .|
|**Sources**|Paramètre `ITaskItem[]` requis.<br /><br /> Définit un tableau d’éléments de fichier source MSBuild pouvant être consommés et émis par des tâches.|
|**SuppressStartupBanner**|Paramètre **booléen** facultatif.<br /><br /> Si la valeur est `true`, empêche l'affichage du message de copyright et de numéro de version quand la tâche démarre.<br /><br /> Pour plus d’informations, consultez l’option **/nologo** dans [Référence XDCMake](/cpp/build/reference/xdcmake-reference).|
|**TrackerLogDirectory**|Paramètre de **chaîne** facultatif.<br /><br /> Spécifie le répertoire du journal de Tracker.|

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur les tâches](../msbuild/msbuild-task-reference.md)