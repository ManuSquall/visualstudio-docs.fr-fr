---
title: Tâches MSBuild propres à Visual C++ | Documents Microsoft
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
- MSBuild, tasks specific to Visual C++
ms.assetid: 05410f0c-7356-4692-bc00-20664421c9ff
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 452c3b408ab6471963124e61bc803e99eb6be80d
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65686905"
---
# <a name="msbuild-tasks-specific-to-visual-c"></a>Tâches MSBuild propres à Visual C++
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Les tâches fournissent le code exécuté pendant le processus de génération. Quand Visual C++ est installé, les tâches suivantes sont disponibles, en plus de celles qui sont installées avec [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]. Pour plus d’informations, consultez [Vue d’ensemble de MSBuild (Visual C++)](https://msdn.microsoft.com/library/dd258f6f-ab51-48d9-b274-f7ba911d05ca).  
  
 Outre les paramètres pour chaque tâche, chaque tâche a également les paramètres suivants.  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`Condition`|Paramètre `String` facultatif.<br /><br /> Expression `Boolean` utilisée par le moteur [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] pour déterminer si cette tâche va être exécutée. Pour plus d’informations sur les conditions prises en charge par [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)], consultez [Conditions](../msbuild/msbuild-conditions.md).|  
|`ContinueOnError`|Paramètre facultatif. Peut contenir l’une des valeurs suivantes :<br /><br /> -   **WarnAndContinue** ou **true**. En cas d’échec d’une tâche, l’exécution des tâches suivantes de l’élément [Target](../msbuild/target-element-msbuild.md) et de la génération se poursuit, et toutes les erreurs de la tâche sont considérées comme des avertissements.<br />-   **ErrorAndContinue**. En cas d’échec d’une tâche, l’exécution des tâches suivantes de l’élément `Target` et de la génération se poursuit, et toutes les erreurs de la tâche sont considérées comme des erreurs.<br />-   **ErrorAndStop** ou **false** (par défaut). En cas d’échec d’une tâche, les tâches restantes de l’élément `Target` et de la génération ne sont pas exécutées, et tout l’élément `Target` ainsi que la génération sont considérés comme étant en échec.<br /><br /> Les versions de .NET Framework antérieures à 4.5 prenaient en charge uniquement les valeurs `true` et `false`.<br /><br /> Pour plus d'informations, voir [Procédure : Ignorer les erreurs dans les tâches](../msbuild/how-to-ignore-errors-in-tasks.md).|  
  
## <a name="related-topics"></a>Rubriques connexes  
  
|Titre|Description|  
|-----------|-----------------|  
|[BscMake, tâche](../msbuild/bscmake-task.md)|Encapsule l'outil Microsoft Browse Information Maintenance Utility (bscmake.exe).|  
|[CL, tâche](../msbuild/cl-task.md)|Encapsule l’outil Compilateur Visual C++ (cl.exe).|  
|[CPPClean, tâche](../msbuild/cppclean-task.md)|Supprime les fichiers temporaires créés par MSBuild quand un projet Visual C++ est généré.|  
|[LIB, tâche](../msbuild/lib-task.md)|Encapsule l’outil Gestionnaire de bibliothèques 32 bits de Microsoft (lib.exe).|  
|[Lier, tâche](../msbuild/link-task.md)|Encapsule l’outil Éditeur de liens Visual C++ (link.exe).|  
|[MIDL, tâche](../msbuild/midl-task.md)|Encapsule l’outil Compilateur MIDL (Microsoft Interface Definition Language) (midl.exe).|  
|[MT, tâche](../msbuild/mt-task.md)|Encapsule l’outil Microsoft Manifest (mt.exe).|  
|[RC, tâche](../msbuild/rc-task.md)|Encapsule l’outil Compilateur de ressources Microsoft Windows (rc.exe).|  
|[SetEnv Task](../msbuild/setenv-task.md)|Définit ou supprime la valeur d’une variable d’environnement spécifiée.|  
|[VCMessage, tâche](../msbuild/vcmessage-task.md)|Enregistre les messages d’avertissement et les messages d’erreur lors de la génération.|  
|[XDCMake, tâche](../msbuild/xdcmake-task.md)|Encapsule l’outil Documentation XML (xdcmake.exe), qui fusionne des fichiers de commentaire de document XML (.xdc) dans un fichier .xml.|  
|[XSD, tâche](../msbuild/xsd-task.md)|Encapsule l’outil Définition du schéma XML (xsd.exe), qui génère des fichiers de schéma ou de classe à partir d’une source.|  
|[Informations de référence sur MSBuild](../msbuild/msbuild-reference.md)|Décrit les éléments du système MSBuild.|  
|[Tâches](../msbuild/msbuild-tasks.md)|Décrit des tâches, qui sont des unités de code pouvant être combinées pour produire une build.|  
|[Écriture de tâches](../msbuild/task-writing.md)|Décrit comment créer une tâche.|
