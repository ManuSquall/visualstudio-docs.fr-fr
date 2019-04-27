---
title: XDCMake, tâche | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
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
- XDCMake task (MSBuild (Visual C++))
- MSBuild (Visual C++), XDCMake task
ms.assetid: a7de9c64-903a-4a02-85f3-f37672270f25
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0d306ec78087ed53ceca44b15f2e184397217650
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62584021"
---
# <a name="xdcmake-task"></a>XDCMake, tâche
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Encapsule l’outil Documentation XML (xdcmake.exe), qui fusionne des fichiers de commentaire de document XML (.xdc) dans un fichier .xml.  
  
 Un fichier .xdc est créé lorsque vous fournissez des commentaires sur la documentation dans votre code source de Visual C++ et compilez en utilisant l’option de compilateur [/doc](http://msdn.microsoft.com/library/b54f7e2c-f28f-4f46-9ed6-0db09be2cc63). Pour plus d’informations, consultez [Référence XDCMake](http://msdn.microsoft.com/library/14e65747-d000-4343-854b-8393bf01cbac), [Outil Générateur de documents XML, page de propriétés](http://msdn.microsoft.com/library/645912b5-197a-4c36-ba58-64df09444ca0) et l’option de l’aide en ligne de commande (**/ ?**) pour xdcmake.exe.  
  
## <a name="remarks"></a>Remarques  
 Par défaut, l’outil xdcmake.exe prend en charge quelques options de ligne de commande. Des options supplémentaires sont prises en charge lorsque vous spécifiez l’option de ligne de commande **/old**.  
  
## <a name="parameters"></a>Paramètres  
 Le tableau ci-dessous décrit les paramètres de la tâche **XDCMake**.  
  
|Paramètre|Description|  
|---------------|-----------------|  
|**AdditionalDocumentFile**|Paramètre **String[]** facultatif.<br /><br /> Spécifie un ou plusieurs fichiers .xdc supplémentaires à fusionner.<br /><br /> Pour plus d’informations, consultez la description **Fichiers de document supplémentaires** dans [Outil Générateur de documents, page de propriétés](http://msdn.microsoft.com/library/645912b5-197a-4c36-ba58-64df09444ca0). Consultez également les options de ligne de commande **/old** et **/Fs** pour xdcmake.exe.|  
|**AdditionalOptions**|Paramètre **String** facultatif.<br /><br /> Liste des options comme indiqué sur la ligne de commande. Par exemple, «  */option1 /option2 /option#*  ». Utilisez ce paramètre pour spécifier des options qui ne sont pas représentées par un autre paramètre de tâche **XDCMake**.<br /><br /> Pour plus d’informations, consultez [Référence XDCMake](http://msdn.microsoft.com/library/14e65747-d000-4343-854b-8393bf01cbac), [Outil Générateur de documents XML, page de propriétés](http://msdn.microsoft.com/library/645912b5-197a-4c36-ba58-64df09444ca0) et l’aide en ligne de commande (**/ ?**) pour xdcmake.exe.|  
|**DocumentLibraryDependencies**|Paramètre **Boolean** facultatif.<br /><br /> Si `true` et si le projet actuel a une dépendance sur un projet de bibliothèque statique (.lib) dans la solution, les fichiers .xdc pour ce projet de bibliothèque sont inclus dans la sortie de fichier .xml pour le projet actuel.<br /><br /> Pour plus d’informations, consultez la description **Dépendances de bibliothèque de documents** dans [Outil Générateur de documents, page de propriétés](http://msdn.microsoft.com/library/645912b5-197a-4c36-ba58-64df09444ca0).|  
|**OutputFile**|Paramètre **String** facultatif.<br /><br /> Substitue le nom de fichier de sortie par défaut. Le nom par défaut est dérivé du nom du premier fichier .xdc traité.<br /><br /> Pour plus d’informations, consultez l’option **/out:**`filename` dans [Référence XDCMake](http://msdn.microsoft.com/library/14e65747-d000-4343-854b-8393bf01cbac). Consultez également les options de ligne de commande **/old** et **/Fo** pour xdcmake.exe.|  
|**ProjectName**|Paramètre **String** facultatif.<br /><br /> Nom du projet actif.|  
|**SlashOld**|Paramètre **Boolean** facultatif.<br /><br /> Si `true`, active des options xdcmake.exe supplémentaires.<br /><br /> Pour plus d’informations, consultez l’option de ligne de commande **/old** pour xdcmake.exe.|  
|**Sources**|Paramètre `ITaskItem[]` requis.<br /><br /> Définit un tableau d’éléments de fichier source MSBuild pouvant être consommés et émis par des tâches.|  
|**SuppressStartupBanner**|Paramètre **Boolean** facultatif.<br /><br /> Si la valeur est `true`, empêche l'affichage du message de copyright et de numéro de version quand la tâche démarre.<br /><br /> Pour plus d’informations, consultez l’option **/nologo** dans [Référence XDCMake](http://msdn.microsoft.com/library/14e65747-d000-4343-854b-8393bf01cbac).|  
|**TrackerLogDirectory**|Paramètre **String** facultatif.<br /><br /> Spécifie le répertoire du journal de Tracker.|  
  
## <a name="see-also"></a>Voir aussi  
 [Task Reference (Informations de référence sur les tâches MSBuild)](../msbuild/msbuild-task-reference.md)
