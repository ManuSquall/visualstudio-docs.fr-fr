---
title: Tâches MSBuild propres à Visual C++ | Documents Microsoft
ms.custom: ''
ms.date: 06/27/2018
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 1aa3de4738c80018020a7a82ac29631a52f4237d
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/19/2018
ms.locfileid: "39153748"
---
# <a name="msbuild-tasks-specific-to-visual-c"></a>Tâches MSBuild propres à Visual C++
Les tâches fournissent le code exécuté pendant le processus de génération. Quand Visual C++ est installé, les tâches suivantes sont disponibles, en plus de celles qui sont installées avec [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. Pour plus d’informations, voir [Vue d’ensemble de MSBuild (Visual C++)](/cpp/build/msbuild-visual-cpp-overview).  
  
 Outre les paramètres pour chaque tâche, chaque tâche a également les paramètres suivants.  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`Condition`|Paramètre `String` facultatif.<br /><br /> Expression `Boolean` utilisée par le moteur [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] pour déterminer si cette tâche va être exécutée. Pour plus d’informations sur les conditions prises en charge par [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], consultez [Conditions](../msbuild/msbuild-conditions.md).|  
|`ContinueOnError`|Paramètre facultatif. Peut contenir l’une des valeurs suivantes :<br /><br /> -   **WarnAndContinue** ou **true**. En cas d’échec d’une tâche, l’exécution des tâches suivantes de l’élément [Target](../msbuild/target-element-msbuild.md) et de la génération se poursuit, et toutes les erreurs de la tâche sont considérées comme des avertissements.<br />-   **ErrorAndContinue**. En cas d’échec d’une tâche, l’exécution des tâches suivantes de l’élément `Target` et de la génération se poursuit, et toutes les erreurs de la tâche sont considérées comme des erreurs.<br />-   **ErrorAndStop** ou **false** (par défaut). En cas d’échec d’une tâche, les tâches restantes de l’élément `Target` et de la génération ne sont pas exécutées, et tout l’élément `Target` ainsi que la génération sont considérés comme étant en échec.<br /><br /> Les versions de .NET Framework antérieures à 4.5 prenaient en charge uniquement les valeurs `true` et `false`.<br /><br /> Pour plus d’informations, voir [Guide pratique : Ignorer les erreurs dans les tâches](../msbuild/how-to-ignore-errors-in-tasks.md).|  
  
### <a name="related-topics"></a>Rubriques connexes  
  
|Titre|Description|  
|-----------|-----------------|  
|[Tâche BscMake](../msbuild/bscmake-task.md)|Encapsule l’outil Microsoft Browse Information Maintenance Utility (*bscmake.exe*).|  
|[Tâche CL](../msbuild/cl-task.md)|Inclut l’outil Compilateur Visual C++ (*cl.exe*) dans un wrapper.|  
|[Tâche CPPClean](../msbuild/cppclean-task.md)|Supprime les fichiers temporaires créés par MSBuild quand un projet Visual C++ est généré.|  
|[Tâche LIB](../msbuild/lib-task.md)|Inclut l’outil Gestionnaire de bibliothèques 32 bits de Microsoft (*lib.exe*) dans un wrapper.|  
|[Tâche Link](../msbuild/link-task.md)|Inclut l’outil Éditeur de liens Visual C++ (*link.exe*) dans un wrapper.|  
|[Tâche MIDL](../msbuild/midl-task.md)|Inclut l’outil Compilateur MIDL (Microsoft Interface Definition Language) (*midl.exe*) dans un wrapper.|  
|[Tâche MT](../msbuild/mt-task.md)|Inclut l’outil Manifeste de Microsoft (*mt.exe*) dans un wrapper.|  
|[Tâche RC](../msbuild/rc-task.md)|Inclut l’outil Compilateur de ressources Microsoft Windows (*rc.exe*) dans un wrapper.|  
|[Tâche SetEnv](../msbuild/setenv-task.md)|Définit ou supprime la valeur d’une variable d’environnement spécifiée.|  
|[Tâche VCMessage](../msbuild/vcmessage-task.md)|Enregistre les messages d’avertissement et les messages d’erreur lors de la génération. (Non extensible. Usage interne uniquement.)|  
|[Tâche XDCMake](../msbuild/xdcmake-task.md)|Inclut dans un wrapper l’outil Documentation XML (*xdcmake.exe*), qui fusionne des fichiers de commentaires documentation XML (*.xdc*) dans un fichier *.xml*.|  
|[Tâche XSD](../msbuild/xsd-task.md)|Inclut dans un wrapper l’outil Définition de schéma XML (*xsd.exe*), qui génère des fichiers de schéma ou de classe à partir d’une source. *Voir la remarque ci-dessous.*|  
|[Informations de référence sur MSBuild](../msbuild/msbuild-reference.md)|Décrit les éléments du système MSBuild.|  
|[Tâches](../msbuild/msbuild-tasks.md)|Décrit des tâches, qui sont des unités de code pouvant être combinées pour produire une build.|  
|[Écriture de tâches](../msbuild/task-writing.md)|Décrit comment créer une tâche.|

> [!NOTE]
> Dans Visual Studio 2017, *xsd.exe* n’est plus pris en charge par les projets C++. Vous pouvez toujours utiliser les API **Microsoft.VisualC.CppCodeProvider** en ajoutant manuellement *CppCodeProvider.dll* au GAC.