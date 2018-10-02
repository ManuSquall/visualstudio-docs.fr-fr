---
title: BscMake, tâche | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vc.task.bscmake
- VC.Project.VCBscMakeTool.PreserveSBR
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (Visual C++), tasks
- BscMake task (MSBuild (Visual C++))
ms.assetid: bb98fc67-cad8-43a7-9598-60df6d734db2
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c3ae418c8448fc2ebe4f5b2af0a8c713458988fb
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47507553"
---
# <a name="bscmake-task"></a>BscMake, tâche
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [BSCMAKE, tâche](https://docs.microsoft.com/visualstudio/msbuild/bscmake-task).  
  
  
IMPORTANT]
>  bscmake n'est plus utilisé par Visual Studio IDE. Depuis Visual Studio 2008, les informations de consultation sont stockées automatiquement dans un fichier .sdf dans le dossier Solution.  
  
 Encapsule l'outil Microsoft Browse Information Maintenance Utility (bscmake.exe).  L'outil bscmake.exe génère un fichier d'informations de consultation (.bsc) à partir des fichiers browser sources (.sbr) qui sont créés lors de la compilation. Utilisez l’**Explorateur d’objets** pour consulter un fichier .bsc. Pour plus d’informations, consultez [Référence BSCMAKE](http://msdn.microsoft.com/library/b97ad994-1355-4809-98db-6abc12c6fb13).  
  
## <a name="parameters"></a>Paramètres  
 Le tableau ci-dessous décrit les paramètres de la tâche **BscMake**. La plupart des paramètres de tâche correspondent à une option de ligne de commande.  
  
|Paramètre|Description|  
|---------------|-----------------|  
|**AdditionalOptions**|Paramètre **String** facultatif.<br /><br /> Liste des options comme indiqué sur la ligne de commande. Exemple : « /*option1* /*option2* /*option#*  ». Utilisez ce paramètre pour spécifier des options qui ne sont pas représentées par un autre paramètre de tâche **BscMake**.<br /><br /> Pour plus d’informations, consultez les options dans [Options BSCMAKE](http://msdn.microsoft.com/library/fa2f1e06-c684-41cf-80dd-6a554835ebd2).|  
|**OutputFile**|Paramètre de **chaîne** facultatif.<br /><br /> Spécifie un nom de fichier qui remplace le nom du fichier de sortie par défaut.<br /><br /> Pour plus d’informations, consultez l’option **/o** dans [Options BSCMAKE](http://msdn.microsoft.com/library/fa2f1e06-c684-41cf-80dd-6a554835ebd2).|  
|**PreserveSBR**|Paramètre **booléen** facultatif.<br /><br /> Si la valeur est `true`, force une génération non incrémentielle. Une génération non incrémentielle complète se produit quand bien même il existe un fichier .bsc, et empêche les fichiers .sbr d'être tronqués.<br /><br /> Pour plus d’informations, consultez l’option **/n** dans [Options BSCMAKE](http://msdn.microsoft.com/library/fa2f1e06-c684-41cf-80dd-6a554835ebd2).|  
|**Sources**|Paramètre **ITaskItem[]** facultatif.<br /><br /> Définit un tableau d’éléments de fichier source MSBuild pouvant être consommés et émis par des tâches.|  
|**SuppressStartupBanner**|Paramètre **booléen** facultatif.<br /><br /> Si la valeur est `true`, empêche l'affichage du message de copyright et de numéro de version quand la tâche démarre.<br /><br /> Pour plus d’informations, consultez l’option **/NOLOGO** dans [Options BSCMAKE](http://msdn.microsoft.com/library/fa2f1e06-c684-41cf-80dd-6a554835ebd2).|  
|**TrackerLogDirectory**|Paramètre **String** facultatif.<br /><br /> Spécifie le répertoire du journal de Tracker.|  
  
## <a name="remarks"></a>Notes  
  
## <a name="see-also"></a>Voir aussi  
 [Task Reference (Informations de référence sur les tâches MSBuild)](../msbuild/msbuild-task-reference.md)



